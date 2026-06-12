---
title: "No sound in Warty in MS Virtual PC 2004"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by vaskark on 2004-10-24
Hi, I just installed Warty in MS Virtual PC 2004. Everything works great except I have no sound, even though I did have it when I used the warty live cd (?????). When I click on the Volume applet properties the list is blank, and when I try to open the Volume Control I get this error message:

Sorry, no mixer elements and/or devices found

Just wondering if anyone can help me. Thanks!

-- vaskark

---

### Post by hoosfoos on 2004-10-24
I believe, but I'm not sure on this, that virtual pc only supports sound with Microsoft OS's.  I have a number of linux distros on my virtual pc install and haven't ever had sound working.

---

### Post by RichNRockville on 2004-10-24
[QUOTE=hoosfoos]I believe, but I'm not sure on this, that virtual pc only supports sound with Microsoft OS's.  I have a number of linux distros on my virtual pc install and haven't ever had sound working.[/QUOTE]


Interesting, I wonder why Ubuntu does not support the Sound blaster 16, I guess because VPC  emulates a 16bit card.?  I also use VPC and even DOS 6.22 works with
the sound.

---

### Post by hoosfoos on 2004-10-24
This was taken directly from Microsoft's Virtual PC 2004 web site.
[http://support.microsoft.com/default.aspx?kbid=824513&product=vpcwin](http://support.microsoft.com/default.aspx?kbid=824513&product=vpcwin)

       Disable sound servers if you use X
If you use X, you may have to disable any running sound servers. For example, if you use the KDE desktop, disable the arts sound server.
	Manually configure sound
You may have to manually configure the sound functionality in your Linux guest PC. To do this, use the sndconfig command. Virtual PC installs a Sound Blaster 16 sound card with the following settings:
I|O port: 220
IRQ: 5
DMA 1: 1
DMA 2: 5
MPU: 330  

So I guess it might be possible, I guess I've never had luck with the gui tools in fedora, Suse, and slax.

---

### Post by vaskark on 2004-10-27
Thanks for all the help, guys. I tried 'sndconfig' but it isn't on my system. What synaptic package is it apart of?

---

