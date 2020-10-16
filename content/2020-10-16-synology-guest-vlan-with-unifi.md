+++
title="Synology Guest VLAN with UniFi"
date=2020-10-16T00:00:00-00:00
[taxonomies]
tags = ["Networking", "Ubiquiti", "Synology", "UniFi"]
+++

TL;DR: Tag the guest network as VLAN **1733** in the UniFi Controller.

I had the Synology RT2600ac for a few years and it was time to upgrade the Wi-fi at my work. I used the RT2600ac and bought a new UniFi nanoHD AP. Both are excellent products but making the guest network work properly took more time than I had anticipated. <!-- more --> The Synology device does not officially support VLANs (yet) on their LAN. But they have [Documented the VLAN used by their guest network](https://www.synology.com/en-global/knowledgebase/SRM/tutorial/Mesh_System/How_do_I_set_up_Wi_Fi_system_with_managed_switch) (Finding this took me too long then I'm willing to admit, hence this blog post) The VLAN for the guest network is **1733**. I first found it mentioned on the [Synology Forum](https://community.synology.com/enu/forum/2/post/127186) Thanks @rustyduck!

## Let's Fix it
I assume that you already have the networks configured with subnets on the RT2600ac Router and UniFi Controller e.g. `10.1.0.0/16` for your staff and `10.2.0.0/16` guests.

In my case, I have an unmanaged switch connected to the Synology Router and I have the UniFi NanoHD AP connected to that.

In the UniFi Controller Settings open your Wi-Fi network (`Settings > Wi-Fi > Wi-Fi Networks > [Wi-Fi Network] > Advanced Settings`) and for your guest network enable `Use a VLAN` and set the VLAN ID to `1733`.

You can also set the VLAN ID in` Networks > Local Networks > [Network] > General`

![unifi-guest-vlan.png](/images/unifi-guest-vlan.png)

Just re-provision your UniFi devices and the comparability issue with the Guest network should be fixed!
