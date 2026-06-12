---
title: "Suspend hangs for 30 to 40 seconds before going to sleep"
date: 2020-05-19
forum: Installation &amp; Upgrades
---

### Post by naughtmcnoone on 2020-05-19
I just spent the weekend upgrading my lap top from v14. to v20.04.

I did a fresh install, after backing up my /home and re-partitioning the drive.

I also completely deleted the dual boot with Win10.  I found that I never use that system anymore.  My one Windows program I need is run in a virtual machine.

Boots fine, everything works.  Have reinstalled all the software I use.  I restored my backup.  I am happy with the system . . .  except . . . .

When I put the system in suspend mode, it hangs for about 30 to 40 seconds before it goes to sleep.  It never did that with the older version of Xubuntu.

I did some digging and tweaking.  I found that if I "log out" before I suspend, then it goes to sleep almost instantly.  So it had to do with something that started after I logged in.

I used "Session and Startup" to disable all my start services on log in, but it had no effect.  I rebooted and still got the same hang time.  I re-enabled the services and started looking elsewhere.

Here is an extract from the log file:

[I][SIZE=1][114250.960519] mce: [Firmware Bug]: cpu 1, failed to setup threshold interrupt for bank 4, block 1 (MSRC0000408=0xc008000001000000)
[114257.054884] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
[114257.054907] [drm;atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E89A (len 498, WS 0, PS 4) @ oxE8DB
[117457.375048] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu[/SIZE][/I]

This, and very similar entries, loop several times when the system is put into suspend.  

A search brought me to Launchpad which had a bug report that predated my v14 install!

I ran "apt-get upgrade" and it upgraded some of my system, but the hang time still persists.

This led me to believe that my problem was with the Radeon video driver.  When I went to "Additional Drivers", there were none listed, and after a search it said that no drivers were available.

Here is the output for  sudo lshw -c video

[I][SIZE=1] *-display                 
       description: VGA compatible controller
       product: RS880M [Mobility Radeon HD 4225/4250]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:9000(size=256) memory:d0100000-d010ffff memory:d0000000-d00fffff memory:c0000-dffff[/SIZE][/I]

I downloaded the ATI drivers from their website for  ATI Mobility Radeon HD4250 and ran the install script.
Here is the result:

[I][SIZE=1]error: Detected X Server version 'XServer _64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:86_64:lib32:XServer _64a:none:5.4.0-31-generic: )
Installation will not proceed.[/SIZE][/I]

Has anyone else had this issue, and if so, did you find a fix?

Cheers!

Naught

---

