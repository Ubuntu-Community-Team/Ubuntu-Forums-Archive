---
title: "Intallation/mounting error"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Fredo_p on 2010-12-03
First time posting, first time user. Still reading the how to manuals.

I recently damaged the HD to my wife's old laptop and ended up buying a new one. So I bought a new HD, claimed the old one for myself and decided to try install Kubuntu 10.10.

I mounted the iso on a CD via PowerISO, installed the new blank HD, and powered up the laptop. I got to the Kubuntu screen, selected start Kubuntu and got this error:

(initramfs) mount: mounting /devloop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I will not be installing any other OS, just Kubuntu. Any ideas?

**Laptop**:
Toshiba Satellite A135-S4427
**HDD**:
 [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822136278&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-"]WD Digital Scorpio Black WD1600EKT 160GB 7200rpm 16MB Cache 2.5" SATA
3.0/Gb/s Internal Notebook hard Drive- Bare Drive[/URL]

---

### Post by Rubi1200 on 2010-12-03
Hi and welcome to the forums :)

You need to burn the image to the CD not just mount it:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Once complete, reboot the computer making sure BIOS is set to boot from the CD/DVD drive and you should be good to go with the installation process.

---

### Post by sikander3786 on 2010-12-03
Welcome :-)

Prior to burning the image to disc, I would recommend to check its integrity first. (it would definitely save you lots of troubles later)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn it as suggested in the link provided by Rubi1200 and remember, burn the image at the lowest possible speed (My CD Drive can burn at 4x :P )

---

### Post by Fredo_p on 2010-12-06
Thanks for the information. It just so happened that a co-worker who convinced me to use Linux said that some laptop users with DVD drives had issues using a CD as the install. He recommended that I try to burn the ISO as a DVD.

Well, I downloaded the DVD version, burned via PowerISO and installed Kubuntu. I did have a hard time trying to understand how to make a partion on a new HD since the guide online showed 10.4 but I was using 10.10. I ended up making the entire drive Kubuntu.

After 189 updates, I am able to use it. Very diffrent from Windows. Lot's to learn and much much guide surfing to do.

---

### Post by Rubi1200 on 2010-12-07
I am glad you got things worked out :)

Yes, it is very different, but it is also an adventure.

Anytime you have questions, feel free to ask here.

Enjoy!

---

### Post by bochi on 2011-01-22
I created the dvd for kubuntu 10.10 and it works on my laptop, but on my desktop I get the "cannot mount dev/loop0 error, so cannot install. 

On my laptop I ran the live cd and cannot get a wireless connection which works out of the box on every other distro I have used. This leads me to conclude that 10.10 sucks big time. Any ideas?

---

