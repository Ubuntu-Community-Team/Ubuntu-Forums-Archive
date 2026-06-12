---
title: "Fresh Feisty install, and get xorg errors with various others after multiple install."
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by feeman_4_life on 2007-08-08
I just formatted today (my XP was messing up yet again), and wanted to install Feisty Fawn.  I've done it before several times on an older box and it went well.  My mom is using one my installs on my old box.  I've installed this once before on this box.

Anyway, I digress.

---------------------------

So today I wanted to dual boot, so I installed XP first, partitioned, and then popped in the Ubuntu CD and then let Ubuntu do its thing......

Okay, Ubuntu is installed.... awesome.  I get a "failed to load X Server."

I try the sudo dpkg-reconfigure xserver-xorg thing, and it said the X server wasn't even installed!!  

I look at my CD, it was a little scratched so well... I'll just download a fresh copy burn it and do it again.

I install it again with the fresh copy (i got the x86 version), but this time, same deal, the x server thing doesn't work.  So I reboot it..... I only see a blank screen...  Big and black, with a blinking type thing in the top left hand corner.  Nothing else.

"Um..... K", I thought to myself.  So I erased yet again, and installed it again, and this time I get some checking hard drive thing saying I haven't checked it in 3xxxx days.  That is 5 digits.

This is getting a little ridiculous.  So I formatted that once again, and I even loaded up 6.10, with the intent of just upgradiing it to Feisty.  I got one of those errors I listed above!!!!!!!!!!!!!!!! ARGH!

I really want to use Ubuntu to try to set up mythtv and try to figure out how to use my plextor convertx px-m204u so I can convert some old family VHS's.  But this is crazy, I can't get anything to work. AT ALL. 

Not once did I see the normal login screen.

I ended up just using XP for now....  What am I doing wrong guys?  I am completely stumped.


The computer specs are:

4600+ Amd Athlon 64 X2 Dual Core @ 2.4ghz
120gb Western Digital IDE drive (set at master w/ slave).
320gb  Seagate Barracuda SATA.
400gb Seagate Barracuda SATA.
Corsair Value Select PC2-5300 1gb x2
NVidia GeForce 7600 GT
Asus M2N-E SLI ATX AM2 Nforce 500 SLI 2PCI-E16 2PCI SATA2 Sound GBLAN 1394 Motherboard

Thank you for any help, I appreciate it!

---

### Post by ifeldt on 2007-08-08
I'm thinking this may be a hardware problem, as you say your Windows XP install was acting up as well.

Can you give some details on that? How was it acting up? Does it consistently do crazy things after each install?

[LIST=1]
[*]I would try booting from the Ubuntu install disk and running a RAM test.
[*]Pick one of the CDs and do a media check to make sure it is burning correctly.
[*]Replace your CD burner with a different one and reburn and try the install again.
[*]Replace the IDE cable that the CD burner is on.
[*]Replace the IDE cable the install HD is on.
[*]Try installing to a different HD.
[/LIST]


How does the live CD act? Try browsing the internet, running OpenOffice, etc.

This is just a general list of things I would try in troubleshooting a machine with the same problems you are having, post back how things went and I will try to help you more.

---

### Post by feeman_4_life on 2007-08-12
I actually think my Harddrive has bad sectors or something, because I just installed it (dual boot) onto one of my new Sata harddrives, and it works perfectly........

The drive was about 3-4 years old anyway.

Thanks for the help!

---

