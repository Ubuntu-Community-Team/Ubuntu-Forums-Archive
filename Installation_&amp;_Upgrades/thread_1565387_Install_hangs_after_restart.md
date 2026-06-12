---
title: "Install hangs after restart"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by tedv on 2010-08-31
Hi,
I'm installing 10.04 on a PC with Windows XP Home. All is fine until i get to the splash with "The installation will finish soon. We hope you enjoy Ubuntu". 

Above the stubborn progress bar that reads 0% it says "Formatting swap space in partition #1 of /host/ubuntu/disks/swap.disk..." 

Is is a permission problem or what? :confused:

---

### Post by andrewthomas on 2010-08-31
**[SIZE=1]Ubuntu 10.04 “Lucid” Blank Screen at Startup : Workaround[/SIZE]**



[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by tedv on 2010-09-01
Thanks for that but it's not a blank screen. The screen is very colourful and Ubuntuey. The installation almost completes, Firefox even pops up when i click a link in the splash screen. It just fails to do the swap file thing.

The swap file at host/ubuntu/disks/swap.disk is 256mb in size so formatting it is not a big deal. I'm wondering if Anti Virus is to blame.

---

### Post by tedv on 2010-09-01
I cured this by uninstalling Ubuntu in Add/Remove Programs. I Defragged the hard disk with Windows Utility and then defragged the free space with Defraggler ([www.piriform.com]("http://www.piriform.com")).

The Wubi install then went ahead perfectly.
:D

---

