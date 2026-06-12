---
title: "Dual windows 10 and Linux boot. Can't boot into Linux after install"
date: 2021-03-01
forum: Installation &amp; Upgrades
---

### Post by kennedya27 on 2021-03-01
I installed Ubuntu alongside Windows 10 without any errors during the process, however I cannot boot into Ubuntu. I am using an HP laptop (windows 10) with UEFI. I've turned bitlocker off, disabled secure boot but still no luck. I ran a live session of Ubuntu from my USB to run the boot repair tool and generated the following report:

[http://paste.ubuntu.com/p/9ZfQKYNHqb/](http://paste.ubuntu.com/p/9ZfQKYNHqb/)

I am brand new to Linux, so I'm positive I screwed something up along the way, and would appreciate any help resolving. Thank you!

---

### Post by oldfred on 2021-03-01
Are you able to go into UEFI one time boot menu (same place as you booted live installer) and boot ubuntu entry?

Grub only boots working Windows, so make sure you have a Windows repair/recovery flash drive and good backups.

But many with HP have updated UEFI and changed boot order in UEFI settings. HP does not remember changes with efibootmgr that grub uses to set boot order. See line 49 in report or:
sudo efibootmgr -v

Do you have drives still set for Intel RST, not AHCI?
If so you need to add AHCI drivers into Windows and then change UEFI settings for drives.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

---

### Post by kennedya27 on 2021-03-01
I do not know what one time boot menu is. I have changed my boot order to boot from the USB first (which is how I can get into the live session), but there is not an option to boot into Ubuntu (my understanding is that should be an option under the BIOS boot order section). I can also go directly into boot menu (f9) and find where Ubuntu is located, but when clicking on that option it complains that it's not a valid option.

I've been reading up on Intel RST as a possible issue, so I'll keep looking at that. To change the drives from Intel RST to AHCI, is that a necessity? And does that typically require modifying or reinstalling the windows side?

---

### Post by CelticWarrior on 2021-03-02
F9 is the one time boot menu (it doesn't change the set boot order except for that one time, on demand).
F10 should open the UEFI settings. The actual boot order should be set at the Boot menu.

---

### Post by tea for one on 2021-03-02
[COLOR="#0000FF"]Line 31 - 33[/COLOR]  Only one OS detected Ubuntu 20.04.2

That seems odd if you have Windows 10 also.
Can you boot into Windows 10?

---

### Post by oldfred on 2021-03-02
It used to be that you could not see drive at all with RST.
But it looks now like it tries to see it:
> nvme1n1     isw_raid_member 

---

### Post by tea for one on 2021-03-02
[COLOR="#0000FF"]Line 107[/COLOR] INTEL HBRPEKNX0202AHO Intel Optane

As mentioned by **oldfred**, you should enable AHCI in the UEFI settings and also disable Windows applications which manage Intel Optane memory & storage.

---

### Post by kennedya27 on 2021-03-02
I see, very help. Here's a fun question: How do I enable AHCI?

I've been researching this for a while, and understand that I need to do so through the bios. However, my HP Envy laptop only gives me access to some sort of minimal BIOS where only a few settings are present (basically change the boot order). I've never seen anything quite like it. I've been trying to get into the "advanced bios", no idea if that's even the right term, but nothing. I called HP tech support and they evaded the question and told me to contact their premium services which is a fun way to find out I'm never buying an HP product again.

So, does anyone know how to access the advanced bios settings on my HP Envy 15t laptop?

---

### Post by tea for one on 2021-03-02
Post no. 4 has the answer [COLOR="#0000FF"]F10 should open the UEFI settings[/COLOR]

---

### Post by kennedya27 on 2021-03-02
Correct, f10 opens the UEFI settings, but there it's a very minimal settings list. There's some sort of extra lock HP has setup and I do not know how to get around it.

This may be beyond the scope of this thread, but this has pointed me in the right direction. Thank you all!

---

