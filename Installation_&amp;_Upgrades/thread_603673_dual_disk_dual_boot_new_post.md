---
title: "dual disk dual boot new post"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by george56 on 2007-11-05
My previous post was about how to correct the dual disk 
master = xp
slave = ubuntu 7.10)

getting grub error 2

now I have xp and am reinstalling gutsy on drive 2.

Problem is that I mistakenly installed grub on xp drive and won't boot.

If I install gutsy on 2nd drive will grub correct itself at the end of the install?

---

### Post by Herman on 2007-11-05
Hello again george56,
Please don't start a new post about the same problem, because anyone who wants to understand your problem will need to read all the way through your [other  thread]("http://ubuntuforums.org/showthread.php?t=603510") again to try to understand what's wrong before they'll be able to give your the right help. Otherwise they'll be wasting their time trying to guess. :)

To answer your question, if you are using the 'Alternate CD', you can install GRUB to any location you like. The default will be the MBR in the first hard drive, which in your case will the the hard drive you have Windows in.
If you don't want to do that, then say 'No' when it's time to install GRUB, so you can choose to install GRUB somewhere else, or install LiLo if you want. 

Here's my link explaining how to install a bootloader in Ubuntu with the 'Alternate CD if you don't like the default suggestion, [Installing a Boot Loader for Ubuntu]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").

You can try re-installing, but I bet you'll still have exactly the same problem again as you had the first time you installed, but you can try it, you might be lucky. Sometimes software can be installed and be corrupted somehow during installation, I have even helped some one once who had no GRUB at all! :)

If that doesn';t work and your hardware is okay, I think you should tryinstalling GRUB to the first sector of your Ubuntu partition and then try GAG Boot Manager instead.
[GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")  GAG Boot Manager, a Windows and Linux booting alternative, 

**GAG's HomePage: **[GAG Boot Manager]("http://gag.sourceforge.net/")

I am sure GAG will be a lot easier for you than GRUB, especailly if your not too comfortabl;e with Linux commands yet. GAG is the 'Graphical Boot Manager', so it's a lot simpler to set up.

GAG will probably not work either if you still have a hardware problem though, or it might if you are lucky.

Regards, Herman :)

---

