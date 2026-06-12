---
title: "Is it possible to install Good OS besides Ubuntu"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by os56k on 2009-11-30
I have Windows 7 and Windows Vista and Ubuntu 9.04 installed.

I'd like to test [COLOR=Teal][Good OS ]("http://www.thinkgos.com/gos/index.html")[/COLOR], a linux-base OS for cloud computing.

Is it possible to install Good OS besides Ubuntu and Windows ?:KS

---

### Post by slakkie on 2009-11-30
yes.. just like you can install ubuntu next to windows :)

---

### Post by os56k on 2009-11-30
Are you sure ?

Have you tried it practically ?

I'm afraid that I install [Good OS]("http://www.thinkgos.com/gos/index.html") and it removes my current bootloader and i would be able to only boot to gOS.[-o<

---

### Post by jrrader on 2009-11-30
> **os56k said:**
> Are you sure ?

Have you tried it practically ?

I'm afraid that I install [Good OS]("http://www.thinkgos.com/gos/index.html") and it removes my current bootloader and i would be able to only boot to gOS.[-o<

Usually with a linux install you can tell it not to overwrite your boot loader (generally on the page after partition set-up).  I currently have 3 different linux installs on my computer (with windows 7 as well).  I use Ubuntu's grub for booting.

---

### Post by jrrader on 2009-11-30
> **slakkie said:**
> yes.. just like you can install ubuntu next to windows :)
He already has 2 windows and Ubuntu on his computer.  He is looking to add 1 more Linux.

---

### Post by slakkie on 2009-11-30
> **jrrader said:**
> He already has 2 windows and Ubuntu on his computer.  He is looking to add 1 more Linux.

I know, I was making a point :)

It is an Linux OS. I run Debian and Ubuntu next to eachother.

BTW: [http://gosforums.org/viewtopic.php?f=10&t=629](http://gosforums.org/viewtopic.php?f=10&t=629)

I see that gOS uses apt-get, so it is based on Debian (Ubuntuto be more precise, [http://distrowatch.com/table.php?distribution=gos](http://distrowatch.com/table.php?distribution=gos)). There shouldn't be any problem installing it next to Windows/Ubuntu and have Ubuntu control the bootloader. Just install the bootloader of gOS on the partition of the OS itself and it should be working.

---

### Post by os56k on 2009-12-07
Is there a difference between the order of installation  or just installing the GOS bootloader in its own partition is enough ?

---

### Post by joes7 on 2009-12-07
Yes, it is completely possible. May I add that you can always use Virtual Box to create a virtual machine.

---

### Post by lostinxlation on 2009-12-08
The order could make differences. 
I installed Slackware on the sytem Xubuntu was already on, and Slack ripped off the swap space from Ubuntu and Ubuntu lost swap(i was trying to share the swap area).
It all depends on how the new OS is designed.

---

### Post by bcschmerker on 2009-12-08
> **os56k said:**
> I have Windows 7 and Windows Vista and Ubuntu 9.04 installed.

I'd like to test [COLOR=Teal][Good OS ]("http://www.thinkgos.com/gos/index.html")[/COLOR], a linux-base OS for cloud computing.

Is it possible to install Good OS besides Ubuntu and Windows ?:KSI have firsthand experience with [[color=green]g[/color][color=black]OS[/color]® 1.0.1]("http://www.thinkgos.com/"), which, I found out, was directly based on [color=orange]xubuntu[/color]® 7.10 Gutsy Gibbon (LinUX Kernel 2.6.22).  [color=green]g[/color][color=black]OS[/color]® 3.0.1 aphrodite and 3.1.1 are actually based on [color=orange]ubuntu[/color]® 8.04-LTS Hardy Heron (LinUX Kernel 2.6.24), including the GNOME user interface.  However, Good OS LLC uses several unique libraries in [color=green]g[/color][color=black]OS[/color]® that would clash with standard [color=orange]ubuntu[/color]®.  In a way, therefore, [color=green]g[/color][color=black]OS[/color]® may actually be a step backwards compared to the now-in-distribution [color=orange]ubuntu[/color]® 9.10 Karmic Koala.

With two LinUX distros using different steppings of Kernel 2.6, this is a judgment call.

---

