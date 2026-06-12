---
title: "[SOLVED] Uninstall Ubuntu"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by chirripo on 2008-07-16
My main OS is WinXp. I installed Ubuntu with no problems from the cd on to a NTFS partition I created on an external USB connected hard drive. Now I want to uninstall Ubuntu. I reformatted the partition and used the WINXP cd to run fixmbr. No matter how many times I run it, I still get the dual boot option.  Can anyone help me with this?

Thanks

---

### Post by killernat on 2008-07-16
there is a file you can edit i think its in the comp prefrences win key + print screen im sry i cant remember exactly where bur i came upon it a while agoe when playing with prefrences

---

### Post by Rocket2DMn on 2008-07-17
If you are using Vista, see here - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You will probably want both /FixBoot and /FixMbr

---

### Post by chirripo on 2008-07-17
Thanks for the replies. I am using XP so the Vista link won't help.
I was reading somewhere that when you run fixmbr using the xp disk, one should see a confirmation that the changes have taken place. After I hit return all I get is a prompt. This is very frustrating.

---

### Post by Pumalite on 2008-07-17
Have you tried?:
FIXMBR>FIXBOOT

---

### Post by Rocket2DMn on 2008-07-17
I believe the Super Grub Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) - allows you to restore windows to the MBR as well.  You may want to give that a try if running fixmbr from the recovery console doesn't work from the windows disc.

---

### Post by chirripo on 2008-07-17
Just tried that and no luck. I also went into BIOS and made sure that boot sector was not protected. I'll try supergrub next.  I also downloaded mbrfix.exe and that didn't help.

---

### Post by chirripo on 2008-07-17
Just tried Supergrub and that didn't fix the problem. I get the message that a new MBR has been written but when i reboot I am still presented with the Ubuntu option. It's more of an annoyance than anything else but I don't feel comfortable having something on my machine I can't control /remove.

---

### Post by Rocket2DMn on 2008-07-18
That's a little strange.  In your BIOS, is your boot order set to look at the USB drive before the internal drive?  If so, you should set it so that the internet drive is ahead of the USB devices in the device boot order.

---

### Post by chirripo on 2008-07-18
Actually, the external USB drive isn't attached at all so the system should see it.

My BIOS startup settings are"

1. Floppy
2. CD/DVD
3. Hard drive
4 Nvidia Boot Agent.

---

### Post by Rocket2DMn on 2008-07-18
OK, clearly GRUB is somewhere on the system if you can actually select from it.  Did you install with Wubi?

---

### Post by chirripo on 2008-07-19
No, I didn't use Wubi. I went to the Ubuntu webpage, downloaded the Ubuntu 8.04 LTS Desktop Edition - Supported to 2011 and burned it to a disk.

With XP booted, I loaded the cd and from the GUI chose Install Ubuntu within Windows. I chose the D: drive which was on the external USB hardrive and went from there.

Thanks for your help.

---

### Post by Rocket2DMn on 2008-07-19
OK, installing from within windows means you are using Wubi, which is officially supported now and available on the LiveCD.  I've never tried this approach to installing Ubuntu, but you should check out this link here for uninstalling - [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by chirripo on 2008-07-19
Success! You beat me to it by about 15 minutes. I was on track to modifying the boot.ini, but I didn't know to remove the mbr files in C:

I can't thank you enough for taking the time to help me out. You've been great.

---

