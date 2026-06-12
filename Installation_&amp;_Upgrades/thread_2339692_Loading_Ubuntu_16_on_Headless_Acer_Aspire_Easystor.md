---
title: "Loading Ubuntu 16 on Headless Acer Aspire Easystore H340 Homeserver"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by entry on 2016-10-11
My old H340 boot disk died so I tried to put the newest Ubuntu LTS server on it.   Because it is headless I put a new drive in a separate PC, loaded and formatted Ubuntu, configured ssh then moved the disk back to the H340 and tried to boot.   I could not get the box to recognize the network card because the old card was not automatically detected and with the new Ethernet device labelling scheme I couldn't figure out how to manually add it.

After searching several forums on H340, Headless, New network config and boot logging I found the following worked so I wanted to share it here.  It may be useful for others setting up a headless server box with the new networking approach (apparently since 14):

1) Turn on journaling persistence by creating[COLOR=#ff0000] /var/log/journal[/COLOR]
apparently journaling is automatic now by default but if the directory does not exist it is overwritten every boot and not persistent.

2) Take the drive to the headless server, boot and wait a few minutes before powering down

3) Put the drive back in the first machine and boot.  Read the boot log with[COLOR=#ff0000] journalctl -b#[/COLOR] (# is 2 in my case) and look for the new name of the eth0 device where it reports in the log attempts to map devices

4) edit [COLOR=#ff0000]/etc/network/interfaces [/COLOR]and make sure to add a new pair of auto and iface command lines to refer to the new device name on the H340

for me eth0 was now enp9s0 so I added the following: 

[COLOR=#ff0000]auto enp9s0
iface enp9s0 inet dhcp[/COLOR]


By adding the new pair I can still move the drive back to the new higher speed PC for the major updates and configuration work.

5) Shutdown, move the drive back to the H340 and reboot.   The network card should be discovered and configured this time.

Some other posts show how to make the machine a static address instead of dhcp if you need it.   I just reserved the address in the router.

The approach seems benign but if I've done something risky for the system please let me know before I get too carried away with the complete setup.  

Thanks.

---

