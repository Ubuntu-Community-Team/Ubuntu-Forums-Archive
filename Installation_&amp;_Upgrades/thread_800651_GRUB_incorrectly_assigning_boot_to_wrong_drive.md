---
title: "GRUB incorrectly assigning boot to wrong drive"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by masonfoley on 2008-05-20
This bug appears to be describing my issue exactly:  [https://bugs.launchpad.net/grub/+bug/8497](https://bugs.launchpad.net/grub/+bug/8497)

Is it possible for this same problem manifesting itself for people that have PCI-based card controllers?  My mobo does not have SATA so I'm using 2 Samsung SATA 150s hooked into a Promise SATA150 II TX2 controller card.  What I'm seeing described here, I've been dealing with this for almost 10 straight hours in attempting to do a clean install of a system that previously enjoyed Feisty.  Only difference I can't resolve as that the BIOS is not aware of the Promise based drives, the controller card is post BIOS with it's own BIOS and is one of the last events in the POST sequence.

The whole discussion thread seems to revolve around the installer grabbing an array list of drives from the BIOS and that ordering being different after reboot.

I can't install Ubuntu or Kubuntu at this time as GRUB can't find the menul.lst file since it's pointing to the wrong drive.

I'm beginning to lose faith in Kubuntu/Ubuntu's progress.  This "bug" has been around for almost 2 years (I only encountered it now as I was attempting to free my system of XP completely and do a clean install).  Seems like a [whole lot of talking]("https://wiki.ubuntu.com/GrubDiskMapSanity") and not much as to how they are actually going to resolve it.

UPDATE:  Only temporary but I disconnected power to the Samsung drives and reinstalled.  The system is up and running but I'm praying that this is a temporary solution.  I suspect as soon as I plug those guys back in, the hard-drive list is going to be out-of-whack again.

---

### Post by Gio-van-I on 2008-05-20
Don't use hope yet. I've installed ubuntu on almost every crappy system I could find. And only problem I ever had was with a PS3.
Still my knowledge is pretty limited, but I'll give it a go.

The first thing that comes in mind is using UUID instead of standard drive notations.
Have you tried this yet? And what where the outcomes?

The problem is know how to set UUID in menu.lst, but I don't have any idea how to get grub looking for menu.lst by an UUID...
Hopefully someone else can shed more light on this.

---

### Post by masonfoley on 2008-05-20
Nah...I'm gonna keep the faith.  This isn't my primary system so it's not THAT critical.

Part of the hours spent on this was trying to "undo" an Ubunto distro that I installed yesterday from scratch.  I ran into the problem right away there but I managed to boot the system with [SuperGrub's LiveCD]("http://supergrub.forjamari.linex.org/") and manually edited (hd0,0) to (hd0,2) and booted into  Ubuntu.  From there, installed the QGRUBEditor package and made the change permanent.  I then went to install MythBuntu by using the "use complete drive" option and I believe I may have "unchecked" the install Grub option from the advanced dialog on the last installation wizard page.  Not happy with the MythBuntu package, I went back to Kubuntu and installed it.  I believe that time I tried to point the GRUB option from the installation wizard to hd2.  That started a long series of install and wipe sequences where I tried to fool GRUB to go to the right drive.  None of those attempts worked and interestingly enough, when I used SuperGrub to try and boot, the old Ubuntu menu.lst kept showing up.  No reference to the new Kubuntu list.  

On a couple of attempts, I tried in vain to mount these drives in a LiveCD setting and get access to /boot/grub but mounting the two Samsung drives, no matter the file system, would not mount with it's original file structure intact.  Kept showing up with a "Lost+Found" directory that I didn't have access to.  (tried ext3 and ext2, no go).  And QGRUBEditor wouldn't run in a LiveCD system.  (I could download it fine but it had an assertion failure a couple of seconds after I would launch...obviously not the environment is was intended to run in)  :)

And there are several other things I tried based on countless Google and forum searches/browsing.

So I guess my question is, if the system gets in this state with GRUB installed to the wrong drive, is there a way edit the menu.lst and get it installed to another drive's MBR and cleanly remove it from the wrong drive?

---

### Post by masonfoley on 2008-05-20
I read your post a bit more carefully and my questions are, is there a way to probe the hard drives to get their UUIDs?  And from there, can the menu.lst and device.map files be edited such that it refers to these IDs?  And if so, what does a menu.lst look like when it is utilizing these IDs?

My thinking is, if I attach my drives back to the system, it will get thrown back into this state and I won't have a means to edit menu.lst.  The only way I know how at the current time is to use QGRUBEditor, but that's only available when booted into a working system.  Can the menu.lst be edited from a >grub command prompt?

---

