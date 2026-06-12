---
title: "Install kubuntu from another partitiion"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by pssturges on 2007-08-25
Hi,

I am trying to install Kubuntu 7.04 on a laptop that has an inoperative dvd drive. It cannot boot from a usb drive either. The system currently has Windows XP on 1 partition and Ubuntu on another. I want to install Kubuntu over the current Ubuntu installation. I have created another partition and tried to adapt the instructions for 'Preparing Files for USB Memory Stick Booting'. I have successfully gotten the required files on the partition including the Kubuntu Live CD iso.

Problem is I can't get the PC to boot from that partition. I've tried editing grub, but I'm not quite sure what I need to put in. Is there an easier way?

Any help would be much appreciated.

Thanks
Phil

---

### Post by merlinus on 2007-08-25
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

-merlin

---

### Post by wolfger on 2007-08-25
> **pssturges said:**
> I want to install Kubuntu over the current Ubuntu installation. 
Unless you are switching versions as well (i.e. Dapper to Feisty), you can accomplish this just by installing the "kubuntu-desktop" package. After it's installed, log out. On the login screen, go to options and select KDE. You are now using Kubuntu.
I just did this last night on my Feisty box. It's painless.

---

### Post by pssturges on 2007-08-25
Thanks for the info. I'm looking to do a fresh install anyway. My current install is a bit of a mess, having done a fair bit of experimenting with it.

Thanks
Phil

---

### Post by pssturges on 2007-08-25
Anybody else got any ideas?

Thanks
Phil

---

### Post by K.Mandla on 2007-08-26
Is this of any help to you at all?

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

There are also a bunch of ways to install from a Windows partition, but it doesn't sound like that's what you're after.

---

### Post by pxwpxw on 2007-08-26
> **pssturges said:**
> Anybody else got any ideas?

Thanks
Phil

It should work, but there are a few traps.
The easiest way to boot is to get a command line from the grub startup menu
(hit C), find the hd-media installer images then load and boot.

```

grub> find /vmlinuz
 (hd0,1)
 (hd0,5)

grun> root (hd0,5)

grub> find /<TAB>
 Possible files are: vmlinuz initrd.gz sp2 Recycled pagefile.sys ubuntu-6.10-server-i386.iso

grub> kernel /vmlinuz 
grub> initrd /initrd.gz 
grub> boot


```

grub can load vmlinuz initrd.gz from fat32 or linux partiton but not ntfs (xp default).
The iso image can be on ntfs, fat32, linux, possibly on external or usb stick (not tried).

Any proiblems, post
```

 sudo fdisk -l

```
and location of the install images and iso. 

Some more points on this other thread -

[http://ubuntuforums.org/showpost.php?p=3249201&postcount=9](http://ubuntuforums.org/showpost.php?p=3249201&postcount=9)

---

### Post by pssturges on 2007-08-27
> **K.Mandla said:**
> 
There are also a bunch of ways to install from a Windows partition, but it doesn't sound like that's what you're after.

If it'll get the job done easily, that would be great!

pxwpxw, thanks for all the great info. I'll give it a go.

Phil

---

