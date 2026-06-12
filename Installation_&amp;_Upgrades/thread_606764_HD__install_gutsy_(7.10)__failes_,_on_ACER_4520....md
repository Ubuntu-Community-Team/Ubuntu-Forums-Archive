---
title: "HD  install gutsy (7.10)  failes , on ACER 4520..."
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by dhruv001 on 2007-11-08
I am kind of stuck with issues with the HD(SATA)  install of  7.10 desktop (Kernel  2.6.22-14-generic,  ) on my new ACER 4520, from the LIVE CD install. 

It fails with an ALERT! /dev/disk/by-uuid<uuid here> does not exist. Dropping to a shell!
( and nothing much can be done from the shell here)
 
I am not familiar with unix, but, what appears to be happening is that my Hard Drive is not being recogonized/loaded at all, even though i had no problems mounting it after boot from LIVE CD

I have been on this for the past few days with no luck. googling has not been of any help and none of the suggestions/instructions seemed to work for me. So, in brief, 

     -. 7.10 (desktop) LIVE CD boot works without any issues ( in safe graphics mode)
             - Network detected and working without issues (from livecd)
             - HD boot fails with ALERT mentioned above
              Looks like Hard Disk not detected  , and unable to mount from busybox prompt. ls /dev/s* shows nothing from this prompt.
               - grub/menu.lst contains the correct UUID of the HD ( which i checked using LIVE CD)
               - there was no etc/fstab , but i created one with the UUID's (  not sure if this makes sense, as the HD is not being mounted at all)

    - Installed 6.06 (desktop) on my HD and was able to login without any issues.
               - but  network card not detected. This seemed to be due to an older version of forcedeth (.56), which was not binding to the interface. 
               - tried to update forcedeth (using forcedeth.ko from 7.10 live cd ) and on reboot, dmesg showed that forcedeth did not start clean, which indicated that my kernel (re) build was not properly done.  So i have given up on this.

    - Now downloading 7.04(desktop), and hoping that this will work without any issues. 

I am not sure where to go from here. Hardware specs of my acer ->[http://priceguru.in/archives/features/895/4]("http://priceguru.in/archives/features/895/4")

Hoping someone can help me out here.

---

### Post by dhruv001 on 2007-11-09
Ah Finally ! 

I am posting this from the successfull install of Fiesty., on my ACER 4520 . Faced lots of issues here as well, but was  able to get it working .. Just for the record, in case it might be of help to someone else, here is what needed to be done....

- Initially, after the first successfull boot from HD, in safe graphics mode, all further HD boots failed, with an "invalid MAC address "
           - Reinstalled from LIVE CD, and did NOT perform any software updates. To be more specific, did not upgrade to the latest linux kernel

-after trouble free HD boot in safe graphics mode, performed the following, to get the GeForce 7000M working, with the proper resolution
     - updated pci.ids from [http://pciids.sourceforge.net/pci.ids]("http://pciids.sourceforge.net/pci.ids"). Not sure if this need, but this certainly helped lspci recognize my vga card. 
      -  downloaded the latest installation package from [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html]("http://www.nvidia.com/object/linux_display_amd64_100.14.19.html")

    - Uninstalled nvdia-glx, nvidia-glx-new using synaptics 
    - updated /etc/modprob.d/lrm-video , to comment out all lines that referenced Nvidia
   -stopped GDM, and ran the package downloaded from the nvidia website, and followed instructions as given in the README file (available in the nvidia link)
  - edited my /etc/X11/xorg.conf to correct the PCI bus id, and resolution to 1280x800
   - REBOOT.. this is important, as i was not able to get it working by stop/start of GDM.. the reboot fixed it.

and here i am ..my first experience with linux.. and the journey appears to have just begun :)

---

### Post by ajoey707 on 2007-12-13
Hai 
Can you explain detail for installation or how to fix this problem cause laptop acer 4520 can't running using ubuntu 7.10 but if i install using linux Open Suse this laptop running well. 
Oh the error " initramfs" bla..bla..bla 
Please help me or you can ..
Thanks

---

### Post by mittaldeepak01 on 2008-01-05
> **dhruv001 said:**
> Ah Finally ! 

- Initially, after the first successfull boot from HD, in safe graphics mode, all further HD boots failed, with an "invalid MAC address "


Hi Dhruv, How did you manage to boot successfully from your HD. I have been trying for more than 2 days, without any luck. 

I will really appreciate if you could throw some pointers. 

Regards,

-Deepak Mittal

---

### Post by cdinz on 2008-01-11
> **mittaldeepak01 said:**
> Hi Dhruv, How did you manage to boot successfully from your HD. I have been trying for more than 2 days, without any luck. 

I will really appreciate if you could throw some pointers. 

Regards,

-Deepak Mittal

Hey Deepak... chk this out: [http://ubuntuforums.org/showpost.php?p=4030097&postcount=10](http://ubuntuforums.org/showpost.php?p=4030097&postcount=10)

---

