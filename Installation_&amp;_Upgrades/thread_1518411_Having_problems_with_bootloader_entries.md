---
title: "Having problems with bootloader entries"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Shelton2142 on 2010-06-26
I started experimenting with Wubi installs of Ubuntu late last year and decided I enjoyed the system, but still wasn't quite ready to make a permanent install. After that, I decided to test out Unetbootin for an alternate method. I uninstalled the Wubi version, then tested out Unetbootin, but I found it not to my liking. After removing the Unetbootin files, I found that my computer still opened up the boot menu even though I didn't have any OS besides XP installed. It has stayed like this for several months.

Now I have permanently installed 10.04 with a disk. While installing, the computer could not set up the boot menu entry by running from the disk, so I had to use the direct installer that came with the DVD.

I now have something of an odd problem. When I start my computer, it goes directly to a new bootloader that I think is native to Linux rather than the old bootloader I had seen before. In this bootloader, Windows XP is now at the bottom of the list, which it was not before. If I select to boot into XP, I get a second bootloader menu, the old one that I had used originally. In this menu, I still see XP, Unetbootin, and now the newest Ubuntu installation.

I need to find out how to get rid of these double boot menus, as well as clear unetbootin from the list because I assumed it doesn't exist anymore. I also need to rearrange the entries, because My dad also uses this computer and is not bothered by my Ubuntu experiments as long as he can just leave the computer alone and it goes straight to XP when he turns it on. Because XP is no longer the first entry in the first list, it goes to Ubuntu if he does nothing, and he isn't an extremely computer-savvy person so he doesn't like the added hassle of having to go through 2 menus to get the OS he wants.

---

### Post by darkod on 2010-06-26
The windows bootloader showing XP and unetbootin has nothing to do with ubuntu, you are aware of that. You should have fixed that first before proceeding with ubuntu install. Get your XP install cd and try to repair the boot process with instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

NOTE: First try to repair only with the /fixboot command. If you also need to use the /fixmbr that will delete grub2 from the MBR. Don't reinstall ubuntu just to get it back, you can just reinstall grub2, if it comes to that.

Try this and it should get rid of the second menu you are seeing. We will discuss rearranging the grub2 menu after that.

---

### Post by oldfred on 2010-06-26
With wubi, you get the windows boot and wubi adds and entry and a delay so the windows boot will show. It is in boot.ini in XP and BCD in Vista/7. Then wubi shows a typical grub menu to continue booting.

With a full install you get the grub menu first, then windows boots and normally you do not see anything as it has no choices. You need to uninstall your wubi from windows and remove the wubi boot entry from the windows boot loader.

You can set grub to default to the windows boot.

the quick and easy to make a default boot:
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

