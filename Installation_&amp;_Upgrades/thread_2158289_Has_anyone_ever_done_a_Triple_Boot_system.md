---
title: "Has anyone ever done a Triple Boot system?"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-28
We hear all the time about folks doing a Double Boot system with Windows/Linux or OS X and Linux so, has anyone ever done a Triple Boot set up with all Linux?  If you had the hard drive space it seems you could cut it up into three partitions and install a different version of Linux on each one so you could boot to one of three different Op Systems. I just wonder how far you could go with something like this. With a 1TB hard drive you could cut it up into 10 partitions of 100GB each and have 10 Op Systems to boot to.  Would that be a possible or is there a limit to how many partitions you can create and how many Op Systems you can run?

---

### Post by oldfred on 2013-06-28
I originally had two 160GB drives with Windows on one & Ubuntu on the other. Then I got a new 640GB drive which seems huge. I created two data partitions of 100GB each for Linux & Windows (NTFS) and still had 440GB left. I created a 25GB / (root) partition and left the rest unformatted in the extended partition. Since that was 3 or 4 years ago I have added 25GB / partitions for each new install and only now have gotten to the point where I may need to houseclean out some of the obsolete installs. I have to turn os-prober off on a new install as it takes forever and shows too many installs many which I do not want to normally boot.

The limit is more that it is difficult to keep track of all the systems and which grub is in charge & the default boot. I have to run bootinfoscript regularly or Boot_repair to kept track. And it is best to manually modify grub to only add one simple boot entry per install. You can have an unlimited number of logical partitions.

Also better to have shared data partition, so each system can have the same data without issues of sharing /home and user settings.

If using only Linux, never Windows on a drive, I now suggest gpt partitioning. The main advantage is all partitions are primary and you do not have the primary, extended and logical partition planning issues. But with gpt you have a standard limit of 128 partitions.

This is now very old and uses grub legacy, but shows some of the planning required.
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by TNFrank on 2013-06-28
Wow, 145 Op Systems, that's just crazy.  I'm currently only running Ubuntu 12.04  and only have a 60GB hard drive. I'd like to run Black Box Linux but don't know if I want to partition and install or just get another computer to install it on.  I'm really a "Keep it simple" kind of guy but just thought it'd be cool to have one Op Sys for play, one for work(if I can go back to school and learn some IT/PenTesting stuff, I think that'd be a very cool job to have.) and maybe a third for just messing around with so 3 would probably be my limit.  I'm so tempted to partition my drive and cut off maybe 20GB to install BBL but I don't know how hard it'd be to remove it if I ran into problems with not having enough drive space for my main 12.04 install.

---

### Post by deadflowr on 2013-06-28
I multi boot five systems.
Precise
raring
saucy 
and kubuntu precise.
They are divided between two hard drives.

And on a third hard drive, I have Windows XP, sitting lonely.(Twas the original hard drive, and because of it's lack of use, is actually in tip-top shape)
I kept XP around for some reason, which now I forget. And will keep it around, because I still forget.

My only problem with multi-booting is giving each one a moment of love, more than I actually do.
So Kubuntu and raring don't get the attentions that saucy or precise might get.
I also tend to keep an empty partition for other distros.
But have become more inclined to run those in a virtual environment, if possible.

---

### Post by ubfan1 on 2013-06-28
Or install qemu-kvm and play around with the OSes in a virtual machine.
> Create a sparse (smaller until filled) 6G disk image:
   qemu-img create myvirt.img -f qcow2 6G
Install an iso into the disk image:
   kvm -m 750 -cdrom /usr/local/vm/precise/precise-desktop-i386.iso -boot d precise.img
Run the image (in a window):
  kvm -m 750 precise.img

---

### Post by Bashing-om on 2013-06-28
@TNFrank; Hi !

I also presently triple boot (did have 4, ->10.04 is gone now)... as others advise ,,,workie great but a real hassle to keep up with updates and keeping grub satisfied. Customizing grub's boot menu is a big help !
13.04/xfce4/Google-Chrome/elinks/gedit == work
12.04 ubuntu == play and my ole standby
12.04 lubuntu == experimental stuff

My installs on are 2 hard drives with a third hard drive shared as a data disk. I maintain a "disposable" data partition on the primary install disk.

[INDENT][INDENT]If I keep learning, one of these days I might get smart[/INDENT][/INDENT]

---

### Post by Lars Noodén on 2013-06-28
I did triple boot OS X, Ubuntu, OpenBSD for a while.  It's doable with rEFIt but there might be another way.  At the time, Grub could not find the OS X partition so rEFIt was needed for that.

---

### Post by Cheesemill on 2013-06-28
I've got a triple boot at the moment. Arch, Kali and Saucy.

---

### Post by Buntu Bunny on 2013-06-28
So with a triple boot, Grub doesn't automatically detect all three?

---

### Post by oldfred on 2013-06-28
Grub2's os-prober almost always finds other installs. There are a few exceptions and in some cases with non-standard partitioning or formatting you have to mount the partition so grub includes the extra driver.

I have to turn os-prober off as it finds too much. I manually add the few I want with simplified partition boot entries and can manually edit those to boot another old install if needed. See info on partition boot style grub entries in 40_custom.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by TNFrank on 2013-06-28
> **deadflowr said:**
> 
I kept XP around for some reason, which now I forget. And will keep it around, because I still forget.


Probably to show people in the future what a crappy Op System looked like .LOL:D

It almost sounds easier to just do an install for something like Black Box onto a USB stick and not actually put it onto the hard drive. Of course if I can sell an air rifle that I have and pick up an HP nc6230 that I found the point will be somewhat moot since I can use the that laptop for a "take around" and it'll have BBL on it and then I can just keep 12.04 on my nc8230 for home use.

---

### Post by C.S.Cameron on 2013-06-28
My office computer has Ubuntu, XP and Win 7 64.
(I need AutoCAD and SolidWorks and with large files I need the ram of a 64 bit system).

---

### Post by JDorfler on 2013-06-29
Hmmm, I did it a long time ago.  However, it was more of a pain than it was a help.  I did Ubuntu, Fedora, and Win Vista at the time.  I spent most of my time in Ubuntu.  
I see above someone has Ubuntu Precise and Kubuntu Precise in a seperate boot.  Just out of curiousity why didn't you just install kubuntu-desktop whilst in Ubuntu.  I have, currently on the same install Xubuntu, Ubuntu, and Ubuntu Gnome.  You just boot into Ubuntu from grub, then when you reach our log-in screen, you just chose the session you wish.  I'm just curious for this reasoning for seperate boot partitions.

---

### Post by deadflowr on 2013-06-29
> **JDorfler said:**
> Hmmm, I did it a long time ago.  However, it was more of a pain than it was a help.  I did Ubuntu, Fedora, and Win Vista at the time.  I spent most of my time in Ubuntu.  
I see above someone has Ubuntu Precise and Kubuntu Precise in a seperate boot.  Just out of curiousity why didn't you just install kubuntu-desktop whilst in Ubuntu.  I have, currently on the same install Xubuntu, Ubuntu, and Ubuntu Gnome.  You just boot into Ubuntu from grub, then when you reach our log-in screen, you just chose the session you wish.  I'm just curious for this reasoning for seperate boot partitions.

Because I like to run Kubuntu as vanilla as possible.
Pure Kubuntu without any gnome/ubuntu/unity packages installed.

Sure I could install a desktop metapackage and be done with it.
But there something to running an OS as close to the defaults, that strikes me.

On a different setup,  I have a lot of different desktops, including gnome-shell/classic,kde,xfce/xubuntu/awesome,cairo-dock,lxde,lubuntu,icewm,fluxbox,openbox,and couple others which I tend to forget.

And so I know how to switch a desktop.

---

### Post by magog45 on 2013-06-29
Many years ago I triple booted windoze 98, Caldera Linux and BeOS using the BeOS boot manager and it worked quite good till I finally went all Linux on my daily use Computer.

---

### Post by Ridgerunrbunny on 2013-07-05
I have 3 hard drives, OS's include Ubuntu, Windows XP, a nd Mac. I did have ubuntu and mac on the T byte but recently changed to having it on a 250 G. Windows is on a 120 g drive. Grub will recognize all three. The only problem with loading more than one linux OS is that the last one installed only recognizes itself.  Not with ubuntu though, the grub in it will triple boot all three.

---

