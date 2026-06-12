---
title: "Intel x86 Install"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by ernstlu on 2005-05-22
I just downloaded intel x86 on my computer yesterday, I unzipped it to an emty hard drive. And then tryed to install it from the same one after that. I have 2 hard drives on my computer, both are seriell ata drives. and both are set at cable select. But, the main question is. How do I install ubuntu 5.04? All the files needed are on this hard drive, can't i just run the setup program from the hard drive i want to use ubuntu on?

---

### Post by ola on 2005-05-22
The easiest way is to burn the ISO file to a CD in your current operating system. Put the CD in you computer and start from the CD.

Once you are there the CD will start an installation program that partitions your disks, installs ubuntu, creates user account etc..

Take care though so you dont erease some data on a disk you don't want to!

If you dont want to burn the CD you can order for free from : [http://www.ubuntulinux.org/shipit/link_view](http://www.ubuntulinux.org/shipit/link_view)

---

### Post by apollyonis on 2005-05-22
Have you tried booting off of the hard drive that contains the Ubuntu install? The cable select may have been overlooked somewhere. I'd try to set it to boot off of the hard drive with the unzipped .iso first from BIOS and see what that does. Quite frankly, I don't know if the provided .iso has a hard disk image on it or not and I'm not on my computer so I couldn't tell you. Best way to figure out is to experiment to see if it will boot. If not, you're stuck with the CD install.

---

### Post by ernstlu on 2005-05-23
[QUOTE=ola]The easiest way is to burn the ISO file to a CD in your current operating system. Put the CD in you computer and start from the CD.

Once you are there the CD will start an installation program that partitions your disks, installs ubuntu, creates user account etc..

Take care though so you dont erease some data on a disk you don't want to!

If you dont want to burn the CD you can order for free from : [http://www.ubuntulinux.org/shipit/link_view](http://www.ubuntulinux.org/shipit/link_view)[/QUOTE]
 Hi Ola, I have a hard drive, that I can use, I have 2 hard drives, one that i want to use linux on, and one that I use Windows xp on. Do I have to install windows xp on one of the hard drives before I install linux? And what file system does linux use?

---

### Post by Alexander Kirillov on 2005-05-23
[QUOTE=ernstlu]Hi Ola, I have a hard drive, that I can use, I have 2 hard drives, one that i want to use linux on, and one that I use Windows xp on. Do I have to install windows xp on one of the hard drives before I install linux? And what file system does linux use?[/QUOTE]
You do not need Windows - but if you plan to use both windows and Linux in the future, it is recommended that you install windows first and Linux after that. 

Linux uses so-called ext2 or ext3 filesystem. See here for more info:
[http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/](http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/)

---

### Post by ernstlu on 2005-05-25
[QUOTE=Alexander Kirillov]You do not need Windows - but if you plan to use both windows and Linux in the future, it is recommended that you install windows first and Linux after that. 

Linux uses so-called ext2 or ext3 filesystem. See here for more info:
[http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/](http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/)[/QUOTE]
 Hi, I have one blank hard drive, and it already have the ext3 filesystem on it. All I want to do is to install Linux on it. I have downloaded it from ubuntulinux. And it's a zip file. But how do I install it from my first hard drive over to the 2 one. When the 2 one have the linux filesystem. It's not possible to zip the files over. Is it possible to burn a bootable cd? And if so, how do I do that?

---

### Post by Alexander Kirillov on 2005-05-25
[QUOTE=ernstlu] All I want to do is to install Linux on it. I have downloaded it from ubuntulinux. And it's a zip file. But how do I install it from my first hard drive over to the 2 one. [/QUOTE]

It should not be a zip file. What you should download is cd image file (.iso) - for example, from here [http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso](http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso)
If you have a zip file, it means you downloaded something else. Where exactly did you get it from? 

Then you can burn it to a CD: any CD burning program allows this (under Linux, try K3b or right-click on iso file in Nautilus and select "write to CD").

---

### Post by ernstlu on 2005-05-25
[QUOTE=Alexander Kirillov]It should not be a zip file. What you should download is cd image file (.iso) - for example, from here [http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso](http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso)
If you have a zip file, it means you downloaded something else. Where exactly did you get it from? 

Then you can burn it to a CD: any CD burning program allows this (under Linux, try K3b or right-click on iso file in Nautilus and select "write to CD").[/QUOTE]

Hi Alexander, yes I downloaded it from the internet adress you gave me. And it is zipped. But I dont know how to make a iso file image on a cd. Any ideas? :smile:

---

### Post by DaveyHollingrad on 2005-05-26
[QUOTE=ernstlu]Hi Alexander, yes I downloaded it from the internet adress you gave me. And it is zipped. But I dont know how to make a iso file image on a cd. Any ideas? :smile:[/QUOTE]

I used ISO Recorder to burn the ISO image to a CD. Once you install it, "Copy image to CD" is an option on the context menu.

Here's a link:
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=ernstlu]Hi Alexander, yes I downloaded it from the internet adress you gave me. And it is zipped. But I dont know how to make a iso file image on a cd. Any ideas? :smile:[/QUOTE]
 No, it is not zipped. It is a .iso file, not a .zip file. 

As to burning it to a CD, any CD burning prgram I know has an option of writing an image file to a CD. Which ones do you have installed?

---

### Post by ernstlu on 2005-05-26
Well the file I downloaded was a zip file. And there was no iso image on it! :-)

---

