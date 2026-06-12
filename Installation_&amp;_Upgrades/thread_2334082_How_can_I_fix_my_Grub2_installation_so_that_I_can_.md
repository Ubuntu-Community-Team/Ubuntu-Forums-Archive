---
title: "How can I fix my Grub2 installation so that I can boot?"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by cfogelberg2 on 2016-08-16
**QUESTION:**
How can I fix my Grub2 installation so that I can boot? Is there anything obvious in [http://paste.ubuntu.com/23060616/](http://paste.ubuntu.com/23060616/) that suggests the problem?

**SITUATION:**
I am trying to install Ubuntu 14.04.04 from a "live CD" USB flash drive to a Dell Inspiron 14z but it is failing to install Grub correctly so I can not boot the laptop. Ubuntu 14.04 was previously installed to the laptop and I do not want to wipe the home drive partition so I am using the "Something else" installation type option to manually configure the mounting and partitions

Disk configuration:

[LIST]
[*]/dev/sda - a 500gb hard drive
[LIST]
[*]/dev/sda1 - is ~60gb fat32 - I haven't touched this, I think it's Dell's "restore Windows" partition
[*]/dev/sda2 - is ~450gb for home /home, I am NOT reformatting this partition
[/LIST]

[*]/dev/sdb - a 32gb SSD
[LIST]
[*]/dev/sdb1 - is 24gb / partition, I am reformatting this one
[*]/dev/sdb2 - is 1mb bios_grub (I'm not sure why it has higher device number, it comes before others on this disk)
[*]/dev/sdb3 - is 8gb swap
[*]The device for the boot loader set to /dev/sdb
[/LIST]
[/LIST]

After the install reports success I reboot the laptop, but this shows me the "grub restore" prompt. When I use the "live CD" USB flash drive, I can see the /dev/sdb2 partition and it appears to have all the files that it should so I think that the problem is just with Grub.

**WHAT I'VE TRIED SO FAR:**
[LIST]
[*]boot-repair from my "live CD" USB - fails because the USB was booted via legacy not UEFI, I have a boot-repair ISO downloading and I'll try to install that on another thumb drive as a UEFI  boot USB drive (haven't had a chance to do this yet)
[*]installing Ubuntu with different devices or partitions for the boot loader (these have all failed on install, reporting that it cannot install the boot loader to that location)
[/LIST]

The boot loader paste bin is here:
[http://paste.ubuntu.com/23060616/](http://paste.ubuntu.com/23060616/)


**HOW THIS HAPPENED:**
Previously I had been able to view local SWF files in Chrome, however this had stopped working (assumption: in some automatic Chrome update).

I attempted the instructions here: [http://superuser.com/a/783451](http://superuser.com/a/783451), which involved editing /usr/share/mime/packages/freedesktop.org.xml and sudo update-mime-database /usr/share/mime, but those seemed to corrupt the XWindows or Gnome drivers and I was unable to login to Gnome (although I could still login to a terminal).

Unable to fix it I thought "oh well, a reinstall can't be too hard..."

---

### Post by Bucky Ball on 2016-08-16
Welcome. Have you set your BIOS to boot from sdb, the second hard drive and not the first? That is where the grub is.

The root of your problem, though, is that the original was an EFI install and you have booted the current install disk/USB in legacy mode and installed in legacy. Not sure what the exact mix up is. Check the bottom of your bootinfo output for more detail on that. Try booting the upgrade disk/USB in UEFI, not legacy.

I had a similar situation to this as far as the machine not booting from sdb and ended up switching the SSD with the HDD, making the SSD sda. Some machines have issues booting from anything but sda. I did end up tricking the machine to boot from sdb with a grub on each drive, but it was clunky so I swapped them over and no issues.

You might want to try again making sure you are doing it in EFI this time. With /home in Something Else, mark 'Use' but NOT format. You can use the existing /swap also if there is one. ;)

(I know you made a good backup of /home before doing any of this though. ;))

---

### Post by cfogelberg2 on 2016-08-16
Thanks for your help here, ultimately I have solved the issue by removing all partitions from sdb (swap, / and biosgrub) and installing again fresh using the 14.04.04 live USB.

Unfortunately I couldn't figure out how to get the boot-repair USB to boot in UEFI mode and I was cautious about futzing too much with my BIOS, especially since everything had worked with its current configuration previously.

Thanks again for your help :)

---

### Post by cfogelberg2 on 2016-08-16
Additional notes for future reference / in case someone searches:
[LIST]
[*]I was going to modify these instructions for DVD UEFI booting to use with USB: [http://www.dell.com/support/article/us/en/04/SLN142679/en](http://www.dell.com/support/article/us/en/04/SLN142679/en)
[*]Idle speculation: Sometime back in the life of 14.04.04 I realised it wasn't using the swap drive, part of the fix for this was changing fstab to use UUID's instead of /dev paths - probably completely unrelated but I wondered
[/LIST]

---

