---
title: "Speakers issue"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2014-11-30
Dear Ubuntu community,

Few days ago I bought a new set o speakers and they were working fine.
[[img]http://s14.postimg.org/8i58n6iyl/DSC_0009.jpg[/img]](http://postimg.org/image/8i58n6iyl/)

Today I have reinstalled my Ubuntu and ONLY LEFT speaker works on Ubuntu.
Everything is fine on Windows 7, but some strange things happen here:/
I cannot see 2.1 option in Sound Settings, which I think I was able to see before.
[[img]http://s3.postimg.org/yndbllwn3/Screenshot_from_2014_11_30_16_10_14.jpg[/img]](http://postimg.org/image/yndbllwn3/)
[[img]http://s13.postimg.org/khwd4wqwz/DSC_0010.jpg[/img]](http://postimg.org/image/khwd4wqwz/)
I can choose any of the above options and it is either left only clear, left only with cracks or silence.

My sound card is Sound Blaster Creative PCI Audigy SE 7.1
Headphones work fine on both Ubuntu and Win 7.

Help please!:)

---

### Post by jet-san on 2014-12-03
Don't really know where to start...
Should I try to remove and reinstall sound card drivers?
Or maybe that ALSA...
Not sure how does it work on Ubuntu.

---

### Post by jet-san on 2014-12-10
Anyone...?

---

### Post by jet-san on 2015-09-09
Guys,

I have just downgraded my Ubuntu from 14 to 13, because of this speaker issue:/
Speakers (both) work normally on Windows 7 as well as Ubuntu 13.04, but on Ubuntu 14.04 only left speaker works (right one is somehow muted).
I have different speakers now (Bose Companion 2 Series III), but the issue is exactly the same.
Anyone can advise something, because nothing is working on 13.04 now...

Thanks,
Damian

---

### Post by jet-san on 2015-09-14
I have installed Ubuntu 15.04 and I have the same issue.
Left speaker is working fine, right one is muted, same as on Ubuntu 14.04.
However speakers are working normally on Windows 7 and Ubuntu 13.04...

Help!!!;(
Damian

P.S.
My PC:
[TABLE]
[TR]
[TD]PC Case:[/TD]
[TD]Gigabyte GZ-X6 Black[/TD]
[/TR]
[TR]
[TD]Case Fan:[/TD]
[TD]1 x Standard Fan[/TD]
[/TR]
[TR]
[TD]Power Supply:[/TD]
[TD]Coolermaster 460W Dual 12V Rail[/TD]
[/TR]
[TR]
[TD]Processor:[/TD]
[TD]Intel Core 2 Duo E8600[/TD]
[/TR]
[TR]
[TD]Heatsink & CPU Fan:[/TD]
[TD]Standard Heatsink & CPU Fan[/TD]
[/TR]
[TR]
[TD]Motherboard:[/TD]
[TD]Asrock G31M-S[/TD]
[/TR]
[TR]
[TD]Memory:[/TD]
[TD]8GB (2 X 4GB) Kingston PC6400 800Mhz DDR2[/TD]
[/TR]
[TR]
[TD]PCI-E Graphics:[/TD]
[TD]Asus GeForce GTX 750 Ti 2GB GDDR5[/TD]
[/TR]
[TR]
[TD]PhysX Card:[/TD]
[TD]Not Included[/TD]
[/TR]
[TR]
[TD]Sound Card:[/TD]
[TD]Creative PCI Audigy SE 7.1[/TD]
[/TR]
[TR]
[TD]Primary Hard Drive:[/TD]
[TD]SAMSUNG SSD 850 EVO 500GB 500G SATA III[/TD]
[/TR]
[TR]
[TD][FONT=arial]Secondary Hard Drive:[/FONT][/TD]
[TD]500GB 7200rpm SATA II[/TD]
[/TR]
[TR]
[TD]Main Optical Drive:[/TD]
[TD]22x Dual Layer DVD +/- Rewriter[/TD]
[/TR]
[TR]
[TD]Network Adapter:[/TD]
[TD]Integrated 10/100[/TD]
[/TR]
[TR]
[TD]Front USB Ports:[/TD]
[TD]2 Front USB Ports[/TD]
[/TR]
[TR]
[TD]Back USB Ports:[/TD]
[TD]4 Back USB Ports[/TD]
[/TR]
[TR]
[TD]TFT Monitor:[/TD]
[TD]AOC I2757FM 27 inch Widescreen IPS LED[/TD]
[/TR]
[TR]
[TD]Monitor Cable:[/TD]
[TD]HDMI to HDMI[/TD]
[/TR]
[TR]
[TD]Speakers:[/TD]
[TD]Bose Companion 2 Series III[/TD]
[/TR]
[/TABLE]

---

### Post by jet-san on 2015-09-14
Finally, after long months on Win7 I can come back to Ubuntu - my friend solved it!!!

Terminal => alsamixer => increase gains for right speaker:)

---

