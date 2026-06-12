---
title: "Help Installing"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Pirate742 on 2007-02-13
Hello there, i have been trying / tinkering / searching / everything i can think of to try and get  ubuntu to install on my system. But i have no clue what is going on, maybe i searched for the wrong things, because i really dont know how to search for my problem (pic at the bottom). But every time attempt to run the install it either freezes or something of this nature shows up.

[[IMG]http://img252.imageshack.us/img252/1130/dscf1629largelh6.th.jpg[/IMG]](http://img252.imageshack.us/my.php?image=dscf1629largelh6.jpg)

I tried the alternate cd install as well. It installed correctly, but when the ubuntu splash screen showed up, it froze. Ive tried everything i could find on these forums / google it didnt work. I normally dont like asking for help but, i really would like to experience ubuntu and i cant :(. 
I have no idea why this occurs, but i dont know why i have a hunch it might be my AGP 7800 GS video card.

Thanks

---

### Post by Jussi Kukkonen on 2007-02-13
The kernel crashes... It's probably a hardware compatibility problem, that can be bypassed with proper boot incantations.

The important data on that crash screen is the call trace -- those function name should turn something up in Google... Let's see...

EDIT: I couldn't find anything matching, and I'm signing off for the night now. Regardless of whether you find a solution you should file a bug here: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+filebug](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+filebug) Attach the photo and as much hardware info as you can.

---

### Post by IgnorantGuru on 2007-02-13
I would first try some boot options, such as acpi=off (this cures some kernel problems).

You can test this by pressing e (for edit) at the grub menu, makes the changes, then press b to boot.  These changes won't be saved - you need to edit grub's menu.lst for that.

A google search for 'ubuntu boot acpi off' will give you some references on where and how to add this, such as this discussion...
[http://ubuntuforums.org/showthread.php?t=335347](http://ubuntuforums.org/showthread.php?t=335347)

There is also 'vga=<some number>' which can help - not sure if that will help with a kernel crash though.

I would try a bunch of those options to see if they have any effect.

Your video card appears to be supported.

If you want access to the filesystem (to check logs, edit menu.lst, etc), I suggest burning a copy of SystemRescueCD from  [http://www.sysresccd.org](http://www.sysresccd.org)    This is a barebones linux livecd that will enable you to mount the ubuntu partition and view/edit files.

Here's a thread that may be of interest...
[http://ubuntuforums.org/showthread.php?t=352442](http://ubuntuforums.org/showthread.php?t=352442)

---

