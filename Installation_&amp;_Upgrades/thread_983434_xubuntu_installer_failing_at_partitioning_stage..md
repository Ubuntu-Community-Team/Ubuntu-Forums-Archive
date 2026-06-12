---
title: "xubuntu installer failing at partitioning stage."
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by stan potts on 2008-11-15
Hello. This is my first post, so feel free to kick me if I make a mistake.

Anyway, I am trying to install Xubuntu 8.10 over my Ubuntu installation, in the hope that it will make the old dinosaur a bit more responsive.

Specs: PIII 500Mhz
256MB RAM
20GB hdd, 3GB second hdd normally used as a net share.

At the partitioning stage, as soon as it tries to do any work on the drives, the installer crashes to the live CD desktop, and the crash reporter appears.

On the other hand, it detected my wireless card, so once I get it installed, no more messing about with ndiswrapper!

Should I try the alternate install cd, or is there a solution that will work with the Live CD?

I have only been using Linux for the past 6 months or so (thank you Asus), so there may be something obvious I have forgotten to do.

Thanks

---

### Post by Partyboi2 on 2008-11-16
Because you already have ubuntu installed there is another option and that is to remove the ubuntu-desktop and replace it with xubuntu-desktop. See [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by stan potts on 2008-11-16
Ah. Well, I am not sure if I can get to my Ubuntu installation, as the only thing the installer HAS done is delete my swap partition, which I think is essential for me.

Are there any benefits to swapping it from ubuntu to xubuntu in that way? There is no data that needs preserving on that computer.

The programs that crashed were: ubiquity, install.ph

Thanks

---

### Post by Partyboi2 on 2008-11-16
> Are there any benefits to swapping it from ubuntu to xubuntu in that way? This way you don't have to reinstall and worry about the partitioning problem. If you have only deleted your swap you should be able from the ubuntu live cd go to Partition Editor (System>Admin>Partition Editor) and create the /swap partition that has been deleted.

---

### Post by stan potts on 2008-11-16
Whoops - It has done something to GRUB.

When I try to start up, I get this:

Grub loading, please wait...
Error 2

So it looks like installing is the only option.

---

### Post by stan potts on 2008-11-16
And more problems. I downloaded the alternate install disk, and burnt it to CD-RW. When it starts verifying packages to install, it tells me that 'dhcp-common' is corrupt, and it cannot be retrieved. The installer then cancels, and I am left with the alternate install options menu.

The only problem I can see here is that there has been corruption somewhere along the line. It cannot be downloading - I used a torrent file, and the burn was at 12x, so there cannot be much of a problem there.

So that leaves me with the media or the drive itself that is causing the install to fail. I cannot do a network install, because it only has a wirless card, and I can't do a USB install, because it cannnot boot from USB drives (and it has usb 1, so would take forever).

---

### Post by lifestream on 2008-11-16
Mmmm how about... I just came upon this the other day:

If you have a small partition as a share, you could save the ISO there, and install Ubuntu from hard drive. Ofcourse, you will have to partition and format prior to installing. 

MMmmm I'm searching for the guide I read a while back, if I find it, I will post here.

---

### Post by stan potts on 2008-11-16
Not sure how I would do that, you would have to guide me.

Something else interesting - I ran an integrity check on the CD, and no errors were found.

Tried installing again. This time it was udev that was corrupt. It also 'failed while configuring base packages'. It finally gave up when it failed to install 'busybox-initramfs'.

---

### Post by stan potts on 2008-11-16
Fixed it. I pulled a DVD drive out of another computer and tried that. This has worked!

The installation has been perfect, and the only problem I have seen so far has been that my slave 3GB hard disk was not added to fstab automatically. But that's not hard to fix. And the computer is handling a lot better compared to chugging along with Ubuntu.

Thanks

---

### Post by lifestream on 2008-11-17
(I tried to post this earlier, and got never ending database errors, so I gave up and went to bed. I'm posting it anyway in case someone else needs this help. Glad you were able to get another drive!)

[http://linuxbasement.com/content/installing-ubuntu-or-other-distributuin-without-burning-a-cd](http://linuxbasement.com/content/installing-ubuntu-or-other-distributuin-without-burning-a-cd)
Read it through, and ask questions here, if you got any :-D

Yeah, if you used a torrent, it checks for integrity, so it should be fine.

Here's some ideas:
   * Are you posting on the forums from the liveCD? Another OS on your computer?
   * Boot from CD and run *fsck* on a terminal. Type *fsck --help *for more options. If your harddrive is /dev/hda, do * fsck /dev/hda*.
   * Use gParted on the live CD to make the partitions as you wish. 
   * Download the ubuntu ISO to your net share partition
   * Follow the instructions on the link I posted.

Again, make sure to ask here if you don't understand something on the guide!

---

### Post by lifestream on 2008-11-17
(I tried to post this earlier, and got never ending database errors, so I gave up and went to bed. I'm posting it anyway in case someone else needs this help. Glad you were able to get another drive!)

[http://linuxbasement.com/content/installing-ubuntu-or-other-distributuin-without-burning-a-cd](http://linuxbasement.com/content/installing-ubuntu-or-other-distributuin-without-burning-a-cd)
Read it through, and ask questions here, if you got any :-D

Yeah, if you used a torrent, it checks for integrity, so it should be fine.

Here's some ideas:
   * Are you posting on the forums from the liveCD? Another OS on your computer?
   * Boot from CD and run *fsck* on a terminal. Type *fsck --help *for more options. If your harddrive is /dev/hda, do * fsck /dev/hda*.
   * Use gParted on the live CD to make the partitions as you wish. 
   * Download the ubuntu ISO to your net share partition
   * Follow the instructions on the link I posted.

Again, make sure to ask here if you don't understand something on the guide!

---

