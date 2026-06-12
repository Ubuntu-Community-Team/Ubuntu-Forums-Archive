---
title: "Installation problems, will not boot"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by jak611930 on 2010-04-27
Hi,
I installed Ubuntu 9.10 today after downloading and booting off the CD.  It worked great and I liked it, so I decided to install it.  I installed it to duel boot with Windows XP Pro.

The install went fine, all the files copied to my computer fine and I got to the prompt to restart my computer.  When I restarted my computer, a boot menu loaded showing me my options, the main two being to boot to Ubuntu or Windows XP.  If I select "Ubuntu, Linux 2.6.31-14-Generic" I get the following message:
Error:  No Such Device: fd2eff29-c536-4ce1-b498-90561d98bedb

If I select the Windows XP option, I get to the first windows loading screen and then I get the blue screen of death and the computer restarts.  I didn't have time to copy any of the information off that screen before it restarted.

If there is a fix for at least the Windows part I'd really appreciate it.  That computer is my main computer and all of my files are on it.  It would be a huge hassle to get all that data off, format it, and re-program it with Win XP.  If there's a fix for Ubuntu also that would be nice, but at this point I don't care too much considering it pretty much just killed my computer.

Computer information:
IBM Thinkpad T40
512 MB ram
40 GB hd(8 GB partition used for Ubuntu)
1.5 Ghz Intel
CD RW/DVD Rom drive
Pretty much all factory for an IBM T40, if you need more info please let me know.

Any help would be appreciated.  Thanks

---

### Post by oldfred on 2010-04-28
Is this a wubi install?

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and/or

Boot Problems:search or no such device
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by jak611930 on 2010-04-28
Thank you, it works great now with no problems.  I was pretty unsure there for a while.  Thanks!  :)

---

