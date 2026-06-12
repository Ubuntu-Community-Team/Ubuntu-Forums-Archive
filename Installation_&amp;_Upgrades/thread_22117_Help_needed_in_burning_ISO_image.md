---
title: "Help needed in burning ISO image"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by jsradley on 2005-03-25
I have Hoary installed and running from the Linux Magazine March issue. Don't know what version, but I think it's earlier than the Preview release.

I have downloaded the Preview version for the AMD64 ISO, and am trying to burn it to a CDRW.

1. First I try Nautilus, after installing the CD Creator.
Nowhere can I find an option to ensure I get a image, but I try, and you guessed it I get a CD with the ISO file.

2. Next I try cdrecord. This appears to be an unofficial modification.
cdrecord -scanbus reports an error can't find /dev/pg*
Is this a bug in the distribution I have??
What could I do to fix it?

3. Next I try K3B.So I install that.
K3B reports no cdrdao, I get the rpm and use alien to install. OK, great.
Why is K3B in the Ubuntu distrubtion if it is missing a package?
This is a much more sophisicated package, rather like Nero.
BUT, you gussed it I cannot find any option to burn an image, so I;ve got another copy of the ISO file.

It CAN'T be this complicated to burn an image using Linux.
PLEASE can someone tell me where I am going wrong?

Thanks
John

---

### Post by Buffalo Soldier on 2005-03-25
[list=a]
[*] Insert blank CD into your CDRW.
[*] Open up Nautilus and browse to where you've downloaded the ISO file.
[*] Right click on the ISO file.
[*] Click "Write to Disc..."
[/list]

---

### Post by LongTooth on 2005-03-26
Gnomebaker is even a better choice. Do a search with Synaptic. If nothing available via apt-get cruse over to the Gnomebaker site  [http://gnomebaker.sourceforge.net/](http://gnomebaker.sourceforge.net/)  . They have instructions. I use it and find it great. Never had any luck with K3B.

---

### Post by pieter hollenberg on 2005-03-27
I downloaded gnomebaker and tried to install with apt-get

apt-get install gnomebaker........

but it didnit work 

how did you install it ?

---

### Post by clb137 on 2005-03-27
HI,

Go to the site and download the*.deb.tar.gz file, then using file manager unpack it you should have a file, gnomebaker_0.3-1ubuntu1_i386.deb or something like that.

Using terminal just put in the following 

sudo dpkg -i gnomebaker_0.3-1ubuntu1_i386.deb 

Hope that helps

Clinton

---

### Post by LongTooth on 2005-03-27
clb137's instructions, or rather Gnomebaker's instructions, are what worked for me.

Don't forget to first remove you apt-get version. Might have problems if you don't.

---

### Post by pieter hollenberg on 2005-03-28
dpkg -i gnomebaker gave a error " missing package cdda2wav" 

so I apt-get cdda2wav

and then it worked

thanx

---

