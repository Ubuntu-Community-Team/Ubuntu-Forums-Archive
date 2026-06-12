---
title: "Is my notebook anti-linux?!?!"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by mrmiggidude on 2007-10-08
I've tried installing Ubuntu Fesity Fawn a bunch of different ways. First I downloaded the 700 meg image file from their website, burned it. I restarted the my laptop, booted from the CD, got the menus. Clicked install. It made my cd drive go crazy, and froze.

I tried it agian, same thing. Burned it again, same thing.

I downloaded a 4 gig Ubuntu install DVD image. Tried it. Same thing. Reburned it. Same exact thing.

I downloaded UnetBootin installer, that installs via the internet, because I figured there might be something wrong with my drive, or the way I burned them.

And it didn't want to run. Something about a Grub error.

I have a e1705. 1 gig Ram. nVidia 7900 card. 100 gigs with 40 free.

Please help.

---

### Post by 5-HT on 2007-10-08
Shouldn't be a problem with that lappy, and t booted fine into the live environment....
The live/install CDs can be really finicky and I can't stand them myself (nice and flashy but almost always fail for me).
Haven't used unetbootin, but I'm guessing it's just a config thing because it would use ntloader and not grub as the bootloader during the install (if it's vista that could be another story)

I'd suggest giving the 'alternate install cd' a go. Otherwise you could do your partitioning and formatting from the live cd prior to the actuall install (has helped in the past).

If you want to go the unetbootin route...perhaps grub was installed after all to your mbr (unlikely as that would be one of the final steps of the installation but you are getting that grub error when ntloader should be used in your situation).

cheers,

---

### Post by mindtrick on 2007-10-08
I second the alternate cd. It gives you an option to install it without live cd mode. 
Get it here
[http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso)

---

### Post by peterbrewer on 2007-10-08
Did you use a download manager to download iso's as the images can be corrupted quite easily.  Especially if you downloaded them using IE.

---

### Post by mrmiggidude on 2007-10-08
I just used firefox to download them from the site, and I used my torrent client to download the big dvd installer. I'm going to try that alternate iso and see how it goes. It's downloading as I type. So I'll let you know how it goes.

---

### Post by wpshooter on 2007-10-08
Are you burning the image at a slow speed, 4X or less and are you checking the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by mrmiggidude on 2007-10-09
> **wpshooter said:**
> Are you burning the image at a slow speed, 4X or less and are you checking the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

It won't even load to that.

---

