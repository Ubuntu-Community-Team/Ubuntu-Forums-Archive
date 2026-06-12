---
title: "Installing Ubuntu and keeping older OS running"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by pat_togo on 2005-07-02
Hi All,
I have just installed Ubuntu and can't access my other drives (should be Ubuntu on C, WIndows on D, my files on E etc.). Is there a way to have both OS and a choice when booting?
Otherwise if I have to redo the installation of both OS, in which order should I do it, and to what should I pay attention to in order to enable dual booting and access to all drives no matter the OS in use.
Thanks.
Patrick

---

### Post by ulisse on 2005-07-02
Normally Ubuntu detects if you have other OS on your machine and create a voice in the Grub menu.
At boot time, you should see something like:

Grub loading, press ESC to enter menu...

for some seconds, then the system boots with the default OS.
If you want the menu to show by default, you have to edit /boot/grub/menu.lst and put a # in front of the word "hiddenmenu".

If your windows OS isn't in the grub menu.lst, you have to add it manually.
A paragraph to boot windows could look like this:

Title Wndows
rootnoverify (hd0,1)
chainloader +1
boot

where hd0 stands for the primary HD and the 1 after the comma is the number of the partition where windows lies, in this case the second.
Also if windows lies on another disk, the "slave" one I.E., you probably have to map the hard drives in this way:

Title windows
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
boot

the comment lines in menu.lst should explain better what you have to do.

---

### Post by pat_togo on 2005-07-03
Hi,
From where to edit the "grub" (what is it anyway I am completely new to this)?
I remember having some problems during the installation about that "grub" I skipped it maybe this is where the problem is coming from?
I will try my chance again, thanks.
Patrick

---

### Post by ulisse on 2005-07-03
the file you have to edit is "menu.lst" and it is located under /boot/grub/, you need root privileges to edit it.
Open a terminal and type in:

sudo gedit /boot/grub/menu.lst

For further information, read this: [URL=http://ubuntuguide.org/#addwindowsentrygrubmenu]http://ubuntuguide.org/#addwindowsentrygrubmenu
[/URL]

---

