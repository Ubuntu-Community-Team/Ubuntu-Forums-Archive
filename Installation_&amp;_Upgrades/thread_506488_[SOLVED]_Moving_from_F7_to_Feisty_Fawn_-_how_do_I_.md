---
title: "[SOLVED] Moving from F7 to Feisty Fawn - how do I make it as painless as possible"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by WayOutThere on 2007-07-21
New to Ubuntu - been around UNIX/Linux since the dinosaurs were here - that just means that I've learned how to break things in a spectacular way.

Anyway, today I finally got fed up with Fedora 7 - I didn't think I was trying to do anything really special:

Have a nicely working OS : Eclipse 3.3 : Apache Geronimo : Wicket : MySql (and db4o ) : mediaWiki or equivalent (maybe a CMS like Magnolia or OpenCMS) : then rebuild my web pages and start moving the app so that it is webified.

I have two machines but they are going to be done separately. First the older Desktop - Athlon 2GHz, 2.5G ram, 80G hard drive (one partition using Volume Manager), a n1000 compatible network card, Nvidia 5400 video, LG 19" Widescreen monitor.

After doing a bunch of reading, it appears that I can do a Live CD test of Ubuntu. I just want to make sure that I can boot off the disk and test drive without installing anything (oooo - the DVD burn just finished).

Even with all the documentation out there, it seems that there isn't a "How to safely and easily move from Red Hat Fedora 7 to a better Linux" type of document.

I'm all ears for any comments, hints, tips, gotcha's, warnings, black holes, or general do this don't do that.

Kevin

---

### Post by Pumalite on 2007-07-21
With a Live CD you can safely test the OS in Ubuntu. It wont install, neither touch your present installation. You also have a chance to know if Ubuntu likes your hardware. Are you planning on erasing Fedora and installing Ubuntu?

---

### Post by WayOutThere on 2007-07-21
I am planning on erasing Fedora (unless I can get away with not doing that - alas, you know how it is 
after you've been using an OS for a while - you have data littered all over the place :-)

So, yes, I am planning to erase Fedora and install Ubuntu - from everything I've read, Ubuntu sounds like it is a community that cares more than the Fedora users.

---

### Post by Pumalite on 2007-07-21
Good. Welcome to Ubuntu. If you post your specs, I'll tell you what iso to use.

---

### Post by WayOutThere on 2007-07-21
Athlon 2GHz CPU + 2.5Gb RAM
Via Technologies VT82C586A/B/ VT82C686/A/B VT823x/A/C PIPC Bus Master IDE
Floppy dirve (just because I had one sitting around)
AT TranslatedSet 2 Keyboard
Via Technologies VT6102 [Rhine-II] ethernet card
Logitech USB-PS/2 Trackball
Via Technologies VIA VT6420 SATA Raid Controller (No RAID drives)
Via Technologies VT8233/A/8235/8237 AC97 Audio Controller
Via Tecnologies USB 2.0
nVidia NV34 [GeForce FX 5200] Video
DVD-ROM 10x (noname but it seems to work fine)
Philips PC-RW-1208
Maxtor ATA 80Gb Hard Drive (Using LVM with Fedora 7)

---

### Post by Pumalite on 2007-07-21
I'd advice Alternate CD. 256 MB RAM or less> Xubuntu Alternate CD:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

With you video you might run into graphical interface problems. Alternate CD avoids that.

---

### Post by WayOutThere on 2007-07-21
OK - why the version of Ubuntu that uses xfce ? I'm sorta a GNOME fan but am openminded to change - alas, it's one of those - I tried it and it was very painful types of arguments with xfce

Can I take it by your response that there isn't a DVD version that is bootable as a Live CD

I already downloaded the DVD and was thinking that I would just copy all my data to another hard drive
and then take the plunge - but, of course, 'scared' keeps creeping into my thinking - I can't afford for my 
data to be zapped.

---

### Post by WayOutThere on 2007-07-21
I forgot to add - I'm using an HP PhotoSmart C5180 All-in-One printer that is network attached via my 4 port LinkSys router - but that shouldn't matter as it would still use cupsd likely.

---

### Post by Pumalite on 2007-07-21
I don't think there is a 'Live DVD'. Another thing; make sure you backup all your data before install regardless.

---

### Post by louieb on 2007-07-21
With 2.5 GB ram run anything you want.  lol  
Heres two of the best guides I know for installing Ubuntu Linux and dual booting.
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")  Lots of tips about installing and and what to do when when things don't go according to plan.
 [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") Lots of tips here too. Geared more to the Linux noob.

---

### Post by WayOutThere on 2007-07-21
thanks for the site references - they look great - read through a bit already - still backing up data though so it's not time for the plunge.

thanks again.

---

### Post by upchucky on 2007-07-21
there is a dvd that is released with linux magazine, but that flavor is a bit much for u vid card mem size but it will work.

backup u files, do not try to keep anything "Fedora" it will only cause u grief if things do not set up right at the start.

u will be able to get to u files after u have ubuntu up and running. 9provided they are saved on a different partition or drive/ usb key)

read lots, if u dont understand something read more, keep supergrub in mind if u have booting trouble, it can fix any boot trouble.

if u download the iso to cd, it can be booted and will not modify u present installation.

make sure u understand what is meant to edit xorg file for the xserver to run, u need to be abe to do this from text commands to get the gui running, u need to find commands to start and stop xserver to test u xorg file.

these commands are different depending on which flavor u decide to install, gnome uses gdm start, gdm stop command, kde has a different command.

i have a work install on one partition and a experimental install on another partition, i use the dual pane gnome filemanager to compare working files with botched files between the two installs, it also loads up my windows files on a third partiotion when needed.

good luck

---

### Post by WayOutThere on 2007-07-22
just a follow up - the DVD does in fact go live before it installs - an EXTREMELY nice feature.

When I took the plunge, I just booted from the DVD - Ubuntu came up in Gnome with a nice icon to continue the install. After spending some time getting used to the differences between Fedora 7 Gnome menus and Ubuntu menus I was off and installing.

Thanks again Pumalite.

---

### Post by WayOutThere on 2007-07-22
hi upchucky

I didn't try to keep anything "Fedora" - I just backup up all my data

Install went smoothly - video came up just fine - I've even installed the nVidia proprietary drivers - not much difference - the fonts are a little better (antialiasing is smoother) and the screen size is more precise but that's it

the nVidia drivers don't give me the 1440x950 mode that this monitor will do, but then neither did the 
plain drivers.

thanks for the help

---

### Post by Pumalite on 2007-07-22
You are welcome. Enjoy your system.

---

