---
title: "gutsy hd install"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by BUGabundo on 2007-09-13
I'm sorry if this is a duplicated post, but I've been looking for a week with no luck.
i wish to reinstall my laptop with tribe 5, but since beta and gold are a weeks away, I dont want to burn a CD.
my CDRW are of 650MBs, and my 2 DVDRW are scrashed.
So I would like to do what is called an HD install, that allows me to boot (using a modified grub) from the contents of the alternate iso or a bunch of locally downloaded packages.

I've tried the procedure here:
[https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)
but no luck

the contents of the iso are on my /home partition:
```
$ ls /home/gutsy/
-rw-r--r--  1 bugabundo root 239M 2007-09-11 23:09 boot.img
drwxr-sr-x 10 bugabundo root 4.0K 2007-09-11 15:25 disc/
-rw-r--r--  1 bugabundo root  15M 2007-09-11 23:09 initrd
-rw-r--r--  1 bugabundo root 1.7M 2007-09-11 15:30 vmlinuz

```
those were download from the hd media page:
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/)

here are a few tried I made on grub:
```
title		HD instal
root		(hd0,4)
kernel		/gutsy/vmlinux root=e3740d46-69f9-4a4b-8f5c-707d262369a4 ro verbose
initrd		/gutsy/initrd
boot

title		HD instal 2 
root		(hd0,4)
kernel		/gutsy/vmlinux boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd		/gutsy/initrd

title		HD instal 3
root		(hd0,4)
kernel		/gutsy/vmlinux root=/dev/ram ramdisk_size=1048576 rw
initrd		/gutsy/initrd
boot
```

any help appreciated.

---

### Post by logos34 on 2007-09-13
You need to create two new partitions--one big enough to hold the contents of the **live/desktop  iso** (~700 MB) and another for the target root partition.  The alternate cd won't work (tried it), and you need to **mount and copy the contents of the iso** and not simply to iso itself to the holding parition.  

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by BUGabundo on 2007-09-13
are u sure that the desktop is the one?
usually this things are done with the alternate.
So i need a new parttion? danm.
I already did copy the contents of the alternate cd to the folder you can see listed on the ls (called disc)

---

### Post by pxwpxw on 2007-09-13
> **BUGabundo said:**
> are u sure that the desktop is the one?
usually this things are done with the alternate.
So i need a new parttion? danm.
I already did copy the contents of the alternate cd to the folder you can see listed on the ls (called disc)

You can try it the hd-media way with an alternate-install-cd.iso:
It goes very quickly when it works.

Put the hd-media vmlinuz and initrd.gz in your gutsy directory,
but put the gutsy directory in the partition root (could be ext3 or fat32 )
```

/gutsy/vmlinuz
/gutsy/initrd.gz

```

And put the alternate cd iso image file for the same version in the root
**You do not unpack the iso, the installer loop mounts it.** Do not have any other *iso image accessible to confuse it
```

/nameofalternatecd.iso

```
so you have altogether
```

/nameofalternatecd.iso
/gutsy/vmlinuz
/gutsy/initrd.gz

```

Thats all you need, 3 files and grub.

Then assuming that /gutsy and the .iso are in (hd0,4) = hda5 or sda5 - 

in menu.lst:
```

title gutsytest
root (hd0,4)
kernel /gutsy/vmlinuz
initrd /gutsy/initrd.gz
boot

```

or you can do it directly from the grub command line with the same commands except for the title.

Be carefull not to destroy the iso during the install.

---

### Post by logos34 on 2007-09-13
> **pxwpxw said:**
> You can try it the **hd-media** way with an alternate-install-cd.iso:

I stand corrected.  Actually I'm glad I learned that because I thought that was only for the [windows version]("https://help.ubuntu.com/community/Installation/FromWindows") ('CD image approach').  

And now I find this [howto]("http://ubuntuforums.org/showthread.php?t=316093").  Learn something new every day.


you can of course still use the live desktop verison cd in the link I posted--if you do it that way it requires the desktop cd..  But since you have the alternate cd go with pxwpxw's way

---

### Post by pxwpxw on 2007-09-13
**logos34**
I am not sure now whether the OP wanted to do a full install to the hard disk, or to somehow get the live cd copied to the hard disk and run from there - an entirely different  project, so will wait and see.

---

### Post by BUGabundo on 2007-09-21
> **pxwpxw said:**
> **logos34**
I am not sure now whether the OP wanted to do a full install to the hard disk, or to somehow get the live cd copied to the hard disk and run from there - an entirely different  project, so will wait and see.

I want to do a full install.
either from using running the LiveCD on the disk, or any other way.
I've finally manage to go with your steps, but only after I found that one of the gz was corrupt.
it seems that the alternate cd iso that I downloaded was also with some prob on the framebuffer.
during install the screen would start to flicker. it never happened to me before, and didnt happened with a previous CD.
Now I'm trying to use this same method to boot hte netboot, but it doesnt find my netcard.
bummer.

---

### Post by logos34 on 2007-09-21
So the problem with cdrom install is basically you have only 650MB size CD-RWs and ubuntu won't fit?

Because about the only other thing I can suggest is you try the server version (~490MB) and then install the ubuntu-desktop or kubuntu-desktop metapackage, which will give you the full gui environment.

 ubuntu-7.04-server-i386.iso             15-Apr-2007 10:59  492M  Server install CD for PC (Intel x86) computers (standard download)

---

### Post by BUGabundo on 2007-09-21
I want gutsy 7.10, not feisty 7.04.
also the iso are even bigger then the 700MiBs
[http://cdimages.ubuntu.com/daily/current/](http://cdimages.ubuntu.com/daily/current/)


still no luck in trying to but the network boot via disk.

why do they make this so hard? lol

---

### Post by jnorthr on 2007-09-21
You may get some further ideas here: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and here [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)

---

### Post by BUGabundo on 2007-09-21
> **jnorthr said:**
> You may get some further ideas here: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and here [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)

those wont help no more. what I'm rtying to do doesnt come there.
I finally manage to get the last iso, check it md5, update the hd media install kernel, and when I selected the Ubuntu Desktop and SSH Server packages, i got my screen filled with (not so) funny colors. they seem like small flags.

10:35 pm and I havent ate yet, and cant this che@t to work.
i'll mail laptoptesting and devel-discuss

---

### Post by pxwpxw on 2007-09-22
**BUGabundo**

I am not sure what stage you got to, but I would try to do the install in 2 stages- First a minimal command line console install, no desktop, no extras, finish and restart, just to establish the basics are ok.
Then do the desktop install and extra packages, to help you isolate the problem.

---

### Post by BUGabundo on 2007-09-22
> **pxwpxw said:**
> **BUGabundo**

I am not sure what stage you got to, but I would try to do the install in 2 stages- First a minimal command line console install, no desktop, no extras, finish and restart, just to establish the basics are ok.
Then do the desktop install and extra packages, to help you isolate the problem.

the base system install quite nice. its only after i select the SSH Server and Ubuntu Desktop

---

### Post by BUGabundo on 2007-09-22
[IMG]http://fileland.bugabundo.net/Linux/screen.JPG[/IMG]

my laptop screen during install

---

### Post by pxwpxw on 2007-09-23
Looks like a text screen gone wrong. Does it get stuck there? does it seem to scroll?

So the hd-media install is getting the installer up and base system installed, then a problem with ubunu desktop or SSH server.. 
I cant recall the installer options - if you are selecting the Ubuntu Desktop as an option from the installer menu, then when the garbling starts you could try switching to console 3 or 4 or 5 - one of them shows instsllation progress (alt-F3 or control-alt-F3 ).

However my suggestion meaant that you should not select Ubuntu-desktop as an installer option, if offered, but install later after a restart  (sudo apt-get ubuntu-desktop). Maybe thats what you did.

Some systems have xwindow problems that need fixing in xorg.conf or graphics drivers, but usually  only comes when xwindows starts up.

Cant really suggest anything else.

---

### Post by justask on 2007-09-23
Check the grub kernel options.
If you have a set a vga mode for the framebuffer display, delete it and try again

---

### Post by michalw on 2007-09-23
I have run to exactly the same problem when installing Gutsy from CD, I avoided it by selecting specific VGA (1024x768x32) mode from CD boot screen by pressing F4. You can try it, maybe it helps.

---

