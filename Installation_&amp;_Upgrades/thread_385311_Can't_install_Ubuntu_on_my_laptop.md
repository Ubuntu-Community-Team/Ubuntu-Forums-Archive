---
title: "Can't install Ubuntu on my laptop"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Gothia on 2007-03-15
Hello,

The whole day i have tried to install Ubuntu 6.10 on my laptop (an Acer Travelmate 4600), but i doesn´t work. I´ve came to this step in the installation ([image]("http://www.fm-mobil.se/Ubuntu_install/5.JPG")) and it loads for about 2-3 minutes. But after that the screen goes black and the computer freezes.

I have tried to burn the installation-CD three times with two programs (Nero Burning Rom and Infra Recorder) with different speeds (lowest x1). I have also tried with the "mini-CD".

When i tested the CD i´ve got this result:

[I]Checking integrity, this may take some time
Check finished, 1 checksums failed
Press any key to reboot your system[/I]

Anyone knows what could be wrong?

Thanks in advance!

/Gothia.

---

### Post by zvacet on 2007-03-15
Download it again,besause as it say cheksums are not O.K.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29")

---

### Post by Gothia on 2007-03-16
I've tried to download and burn Ubuntu again, but the screen still goes black. This time i discovered some kind of melody on about 2-3 sec, played about 1 minute *after* the screen goes black.

It looks like the installation works, but i can´t see it.

---

### Post by Gothia on 2007-03-16
Anyone, please..?

Thanks in advance!

---

### Post by floke on 2007-03-16
Look, you need to check the cd before you install from it.
If there are any checksum failures then sling it in the bin.
You might need to download again if you keep getting bad burns.
Burn at the slowest possible speed.
Do not install until the disk is verified.
It took me about 4 burns to get a good one the first time out, so don't worry.

---

### Post by buuntuu! on 2007-03-16
instead of wasting cds you should check the md5sums before burning, there are some xp-applications for doing that out there... just google them

---

### Post by ravis_31 on 2007-03-16
are you able to run the live cd.do you use an ati card.
if yes,i suggest using the alternate cd as ubuntu has some initial setup issues with ati drivers.you can later configure them.

travis

---

### Post by dannyboy79 on 2007-03-16
simply use the "alternate install cd", it's text based. I had to do this on my laptop as well. also, you may have issues with your graphics card, after you're done with the gui installer. read this before you start the install.

This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

---

