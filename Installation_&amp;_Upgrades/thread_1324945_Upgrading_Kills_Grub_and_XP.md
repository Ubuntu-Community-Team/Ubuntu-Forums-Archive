---
title: "Upgrading Kills Grub and XP"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Nohtanhoj on 2009-11-13
Before I decided to upgrade to Ubuntu 9.10, I was running a dual-boot system with Windows XP. I have kind of a "thing" about doing clean installs (and I'm also a total Linux noob), so I thought that I could format the Linux partition, boot into Windows, make my bootable USB then, and all would go well.

I just learned the hard way that what I said is a catastrophe of errors. Since Grub is installed on the Linux partition, I can no longer boot into Windows. To make matters worse, my computer is a netbook that has no CD drive (leaving me with only a bootable USB option). 

My issue is this - does anyone know how to make a bootable USB stick with a Mac (that's my only other accessible computer) ? If so, then I should be able to remedy this problem myself. If not, since I don't have my Windows restore CD's, what should I do?

Sorry to dump such a huge fail onto you guys, but I clearly can't do it myself and don't want to make things worse (if it was possible). The good thing is, I have access to a 9.10 live CD.

---

### Post by lisati on 2009-11-13
Are you able to boot from the Live CD? If so, and you experience no problems with the "Try Ubuntu without installing" option, you should be able to install from there. Just remember to tell the installer to use the largest continuous free space (i.e. the area previously occupied by Ubuntu)

---

### Post by Nohtanhoj on 2009-11-13
What I meant by "I have access to a copy of Live CD," is that I have one in my possession. My current dilemma is that I cannot transfer that CD into a bootable USB because my only other computer is a Mac.

---

### Post by Nohtanhoj on 2009-11-13
Bump - I need to get this fixed....

---

### Post by raymondh on 2009-11-13
This may be a long shot ..... but I think is worth investigating ....

Sun has virtualbox for Mac's.  You could install (make sure you it has USB support) that in your mac and use that to virtualize either Ubuntu or windows.  In virtual mode (whatever OS you decide as guest), you could either burn the liveCD to a thumbdrive or, add unetbootin if you are using windows and make a persistent drive.  

With the thumbdrive, you could access the netbook.

I know this idea sounds far-fetched but It's worth thinking about ;)

---

### Post by darkod on 2009-11-13
Don't know if I can help much since you have no way of creating the bootable ubuntu USB stick, but why is grub on the Linux partition?

Grub goes on the MBR and this situation is exactly why. Formating/deleting the linux partition wouldn't delete grub.

I have no Mac experience and don't know if you can create the USB there. Maybe reading on [www.ubuntu.com](www.ubuntu.com) can help. There is link for creating USB stick it might contain Mac instructions.

And what another poster suggested, use largest continuous space. Why would you want Ubuntu to make the choices for you? People, ALWAYS use manual partitioning. You want to create and have control of your partitions, even if you're not a control freak. :)

---

### Post by darkod on 2009-11-13
Mac instructions on the bottom
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

PS. If you like the desktop look better than UNR, I guess you can use image ISO from desktop 32bit version. Personally I hated UNR and installed desktop 32bit over it 2 days later.

---

### Post by coffeecat on 2009-11-13
That's a difficult situation.

What Mac do you have? Is it an Intel Mac. I believe (but I've never tried it) that you can boot up an Ubuntu live CD on a Mac and use the live desktop session just as you would on a PC. As far as I can see, the app usb-creator that you need comes in the box with 9.10, because it's already installed on my system (System > Administration > USB Startup Disk Creator) and I didn't install it.

That's one way. Or - once you have Ubuntu running live on a Mac, you could create a bootable USB of [SuperGrubDisk]("http://www.supergrubdisk.org/"). [How to SGD USB here]("http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB."). You can use SGD to repair the Windows MBR and get your netbook booting into Windows if you want to go that way.

The only other thing - is there no other computer running Windows and/or Linux (a friend's or relative's perhaps) that you could use?

---

### Post by Nohtanhoj on 2009-11-13
> **darkod said:**
> Don't know if I can help much since you have no way of creating the bootable ubuntu USB stick, but why is grub on the Linux partition?

Grub goes on the MBR and this situation is exactly why. Formating/deleting the linux partition wouldn't delete grub.

I have no Mac experience and don't know if you can create the USB there. Maybe reading on [www.ubuntu.com]("http://www.ubuntu.com") can help. There is link for creating USB stick it might contain Mac instructions.

And what another poster suggested, use largest continuous space. Why would you want Ubuntu to make the choices for you? People, ALWAYS use manual partitioning. You want to create and have control of your partitions, even if you're not a control freak. :)

I will when I can get this working. However, my formatting of the Linux partition has messed Grub up somewhat.... The error I get is Error 22, if that's any help. I am going to a buddy's this weekend and I think I will be able to create the bootable usb there.

EDIT: Just Googled Grub Error 22, it looks like my MBR is messed up. I'll have to get my hands on a Windows XP recovery disk somehow to fix it. However, there's another issue... Can I create a bootable XP drive the same way as I could create a bootable Linux one?

---

### Post by darkod on 2009-11-13
The Mac instruction in post #7 don't help? Or you're no longer after instructions to create the USB stick under Mac.

---

### Post by Nohtanhoj on 2009-11-13
I created the boot disk already with a buddy's copy of Linux (in class). =D

The issue now is fixing the MBR.

Edit/Bump: For the last few days I've been trying to get my computer to boot from the Live USB. Interestingly enough, it doesn't recognize any Live USB that I create. Any ideas, cause I'm fresh out?

---

