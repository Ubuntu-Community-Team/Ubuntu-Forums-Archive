---
title: "Installation issues (possible reward)"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by 2girls1cup on 2011-01-09
Hi, I'm having issues while trying to install the latest version of Ubuntu (10.10 at the time of writing). All and any help is greatly appreciated, if it is a complex task then I am even willing to pay someone for their help, as long as it works. Let me just say that firstly it's probably a very simple issue, most likely something I've missed out, so sorry for being a noob. Anyway here goes.

**What I've done so far:**
- Downloaded Ubuntu 10.10 from the official site
- Downloaded UNetbootin from the official site ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))
- Gone through the UNetbootin process to install Ubuntu.

What I done next is restart my computer (running on Windows XP), while it's booting I press F12 to go to the boot menu and choose the UNetbootin option. When I do that, it loads and runs Ubuntu (which is what I'm currently on).

Ubuntu boots, and there's an "Install Ubuntu 10.10" icon on the desktop. When I go through the process of the installer I can get up to the "Allocate drive space" step, but no further. I'll click the "Install Now" button, but get an error message reading "No root file system is defined. Please correct this from the partitioning menu". The problem is however I have literally no options on that screen - no data in the main table (Device/Type/Mount Point/Format?/Size/Used). Also, I only have 1 option in the boot loader field which is "/dev/sda".

Also, if it's of any importance, when booting Ubuntu just after the loading screen (or just before, I can't remember exactly when) the screen is black and displays a message (most of which I've forgotten) something along the lines of "Invalid user id (0)" or "can't find user id (0)" or something. It doesn't seem to matter though as Ubuntu still loads.

**What I want to do overall is to make it so that Ubuntu boots automatically when I first start my computer (instead of Windows). **I'd also like to delete Windows altogether, but the first bit is the most important thing.

Does my post make sense at all to anyone? Again, all help is GREATLY appreciated.

A happy new year to everyone, regards, John.

EDIT: Also, I'm apparently logged in as "LIve session user", if that's of any help.

---

### Post by 2girls1cup on 2011-01-10
No one with any ideas?? :(

---

### Post by garryconn on 2011-01-10
> I'd also like to delete Windows altogether

If that's the case, then why don't you just burn a cd instead of using UNetbootin. If you don't want to burn a cd you can still create a bootable USB and install Ubuntu that way. I'm having trouble understanding the need for UNetbootin?

---

### Post by Bucky Ball on 2011-01-10
And I would try 10.04 LTS as a new user. You may get a smoother ride. 10.10 has issues at the moment so, unless you feel like going through an extremely steep learning curve troubleshooting, 10.04 might be the go until you know the ropes a little better.

Having said that, try a CD as suggested by GarryC if you like. Might make a difference but might wipe Windows as well if you're trying to dual-boot. That is *one* of the problems on some machines with 10.10, and a fairly major one. There's are more.

When you are installing, you need something like this:

/ = root, seems to be what's missing;
/home = your personal data and settings, optional;
/swap = 2Gb, 4Gb for hibernation if you do that.

Try installing again and this time use 'manual partitioning' rather than letting Ubuntu do it, and set these partitions yourself.

Welcome to the forums!

---

### Post by garryconn on 2011-01-10
Also, take some time to read the installation guide. It's very well written. I even printed a copy myself and 3 hole punched the pages and put them in a binder. If you're willing to commit a couple hours of reading, it will honestly save you a couple of days of frustration. 

Here's the link to the installation guide -- [CLICK HERE]("https://help.ubuntu.com/10.04/installation-guide/")

Also with manual partitioning, check out these two pages:

[LIST]
[*][Pre-Partitioning for Multi-Boot Systems]("https://help.ubuntu.com/10.04/installation-guide/i386/non-debian-partitioning.html")
[*][Recommended Partitioning Scheme]("https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html")
[/LIST]

---

### Post by kansasnoob on 2011-01-10
You might also find some of this useful:

[http://ubuntuforums.org/showpost.php?p=10119443&postcount=1](http://ubuntuforums.org/showpost.php?p=10119443&postcount=1)

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

