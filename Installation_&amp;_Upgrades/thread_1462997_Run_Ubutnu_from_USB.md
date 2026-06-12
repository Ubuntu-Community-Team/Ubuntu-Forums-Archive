---
title: "Run Ubutnu from USB"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by ukbeast on 2010-04-26
Hello I have Windows XP SP3 and was wondering can you install Ubutnu on a USB device and use it?
because netbook has 1 partition and 1 hidden partition,

BTW it is a 8GB.

---

### Post by Megaptera on 2010-04-26
Hi,
Here's a site dedicated to that very topic.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I've used a lot of the guides there with ease.

Enjoy!

---

### Post by ukbeast on 2010-04-26
> **Megaptera said:**
> Hi,
Here's a site dedicated to that very topic.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I've used a lot of the guides there with ease.

Enjoy!

WOW Cheers mate :)

---

### Post by P4man on 2010-04-26
pendrive linux was a great resources when it was needed, but frankly it has become unnecessary for most, as making bootable USB sticks is so easy now.

Just grab unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And make a bootable USB stick for (almost) any linux distro with 2 clicks, from within windows or linux.

---

### Post by Megaptera on 2010-04-26
You're welcome!

---

### Post by P4man on 2010-04-26
May have jumped the gun. If you want to do a full install on to a USB stick or drive, then unetbootin may or may not be the right tool. unetbootin creates a "live cd". That works somewhat different than a traditional install.

advantages of a live session:
- takes very little space thanks to compressed filesystem. 650Mb for ubuntu.
- very little (or even no) writes to your flash drive make sure it lasts long
- you can install from the stick to any PC.
- You can create a writeable virtual filesystem so you can write changes, additional installed apps or documents back to the stick, but not with unetbootin I think.

disadvantages:
- slow boot (decompressing filesystem takes time)
- costs more RAM (not an issue if you have 1+GB)
- not easy to install drivers for video/network

If you do a full install, it will work just like from a HDD, but it will cost you ~ 5 GB and  be advised that a typical USB stick will wear out very quickly when used this way due to extensive writing!

---

### Post by mdscpa on 2010-04-26
I used unetbootin to create a bootable USB key.  When I try to boot, I get a screen that counts down from 10 seconds and then counts down from 10 seconds and so forth.  The PC never boots from the key.  I've tried the key on other laptops with the same result.  Any ideas?  Thanks.

---

### Post by P4man on 2010-04-26
try another USB key. [Verify]("https://help.ubuntu.com/community/HowToMD5SUM") your download that the ISO you used is not corrupted.
 Its also possible its one of those USB keys with U3:
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

If that is the case, the flashdrive emulates a cdrom and loads some custom firmware. You will have to remove u3 using a tool from them (which is irreversible).

---

### Post by Carl Hamlin on 2010-04-26
USB sports a finite number of potential write/erase cycles as a feature of the media. Running linux off a USB key as your main linux installation will result in the key doing the big firework very quickly, potentially resulting in data loss for you as well.

If you're OK with that, boot from CD like you're going to install to the HD, and when it gets to the bit where it's asking what drive to install to, choose your USB key. Ubiquity is just as happy to install to a USB key as a fixed HD.

---

### Post by dabl on 2010-04-26
> **Carl Hamlin said:**
> 

 Running linux off a USB key as your main linux installation will result in the key doing the big firework very quickly, potentially resulting in data loss for you as well.



True, EXCEPT if you make it a "Live CD". 

[http://kubuntuforums.net/forums/index.php?topic=3106368.msg224305#msg224305](http://kubuntuforums.net/forums/index.php?topic=3106368.msg224305#msg224305)

Put Linux in a 800MB second partition, leaving the first partition as FAT32 for general data.  Then the Linux will run in "read only" mode, as you won't be installing software or saving anything on the Linux partition.  Windows will not see that second partition.

---

### Post by Herman on 2010-04-26
> USB sports a finite number of potential write/erase cycles as a feature of the media. Running linux off a USB key as your main linux installation will result in the key doing the big firework very quickly, potentially resulting in data loss for you as well.Surely you exagerate.
I have installed regular Ubuntu installations in flash memory sticks and I haven't run into any problems yet. 
The only way to know for sure is to test to destruction, but I have been running Ubuntu in my EeePC with a 4 GB SSD drive for quite  a long time now without any problem.
ASUS says it's guaranteed for at least two years no matter how we use it. I have the swap file in it and all. No problems so far and often I let it go 24/7.
I have other USB flash memory installations and I have not lost a flash memory drive yet.
I have a growing pile of failed hard disk drives though.
My newest flash memory drive is an OCZ Vertex SSD drive and it boots Lucid Lynx in 4.19 seconds and is guaranteed for life.
I think flash memory has a bad reputation from the past which is undeserved nowadays. :)

---

### Post by P4man on 2010-04-26
SSD drive != usb stick

---

### Post by bunny rabbit on 2010-04-26
> **P4man said:**
> SSD drive != usb stick
I think that's what he meant :) His' is still good even though it's used a lot.

By the way: thumbdrives hardly cost anything anymore and all data can be backed up online [(_ubuntuone_)]("https://one.ubuntu.com/").
Coincidentally the last couple of days I've been walking around with one of those "corporate handout" 1 Gigabyte thumbdrives that I had put UNR on. Installing it on my mums eeepc for example, went fast and was a breeze! The Ubuntu people have taken very good care of all this IMHO. Great stuff!

All the best,

---

### Post by P4man on 2010-04-27
> **bunny rabbit said:**
> I think that's what he meant :) His' is still good even though it's used a lot.

Im not sure if he is making the distinction, but SSD drives have buffer memory and a controller that will minimize wear of the flash memory by spreading write cycles over different cells for each, that dramatically increases the lifetime of them if you are doing a lot of writes, and the larger your drive, the longer it will last. USB sticks arent that smart, and for instance ext4 journaling will keep hammering the same cells on your stick and these will wear out quickly. Ive killed usb sticks in a matter of months doing regular installs on them (and even using them rather sporadically). 

Maybe newer sticks are better at this and its true they are cheap as chips nowadays, but its definitely worth pointing out.

---

### Post by bunny rabbit on 2010-04-27
That's interesting. I agree.

---

### Post by Herman on 2010-04-27
Well if you take a look at the illustration in the following URL, [http://www.extremetech.com/article2/0,2845,2329594,00.asp](http://www.extremetech.com/article2/0,2845,2329594,00.asp),  you can see the flash memory chips in a solid state drive.
The first picture in this URL, [http://en.wikipedia.org/wiki/Flash_memory](http://en.wikipedia.org/wiki/Flash_memory), shows that the flash memory inside a USB thumb drive are much the same as the ones inside an SSD, and the thumb drive also has a controller chip.

I think that all flash memory thumb drives nowadays would have some kind of a controller, with wear levelling. I would think that almost all flash memory sticks now would have some form of wear levelling, but there may still be a few available without it.

The web page in this URL, [http://www.testfreaks.com/blog/review/usb-flash-memory/usb-flash-drive-comparison-21-tested-and-compared/](http://www.testfreaks.com/blog/review/usb-flash-memory/usb-flash-drive-comparison-21-tested-and-compared/) shows the test results of 21  flash memory sticks tested for various qualities. Although the first chart shows a 'Combined Index and Endurance Factor' which is only calculated and may not be real, it is interesting to note that the difference indicated here between the best USB flash memory drives and the worst is a factor of more than 20x.

The only real testing I can find for flash memory drives running Linux operating systems in them based on actual real-life testing is this one, [http://www.nslu2-linux.org/wiki/Info/FlashDriveLifespanSurvey](http://www.nslu2-linux.org/wiki/Info/FlashDriveLifespanSurvey) started back in 2005/06, (when USB thumb drives most people could afford were quite small, by the look of things).  Assuming participants in the survey remembered to come back and post their results when their flash memory sticks died, it looks like only two out of fifteen have failed so far.

In my own personal experience, I must be extremely lucky, because I have not yet experienced a failure in a USB flash memory stick yet and I do use flash memory sticks quite a lot.  My EeePC is on almost all the time and travels with me almost everywhere I go, I'll be sad some day when it wears out, but by then I expect it will be obsolete and I'll want a newer one anyway.

---

### Post by P4man on 2010-04-27
Herman, you might be right. Certainly looks like better quality thumbdrives have improved dramatically. I just saw this pdf from corsair which is rather interesting:

[http://www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf](http://www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf) 

A quote:
> Will my Corsair USB Flash drive last
more than 10 years?
Yes. All Corsair flash drives are built with memory
components that can handle AT LEAST 10,000 write
cycles; typically they will handle an order of
magnitude more than this. So, this means that in
order to exhaust the drive in ten years, one would
have to write to EVERY BLOCK in the device about
2.7 times per day, every single day. We simply can’t
conceive of such a usage scenario; this would mean
that on a fairly typical 8 GByte drive, one would need
to write over 21 GBytes of data to it every day for ten
years! USB flash drives simply are not used in this
way.


But the interesting part is how they implement wear leveling.

Now Im not sure the dirt cheap thumbdrives you can buy anywhere will be as sophisticated, but maybe I should let go of my fear of killing thumbdrives. Its just that I have so many gone bad on me over the years  (admittedly, not very new ones, and most of them cheap 128 Mb - 1 GB models) that I always thought floppy disks looked rather reliable in comparison.

---

### Post by acarlstein on 2010-04-28
I created a live usb with Ubuntu 9.10

I can store information and changes in it

I am trying to modify the installation menu.

I am compiling different versions of the kernel and I want to have a way to choose them.

update-grub is not working as it should.

Any ideas?

---

### Post by Herman on 2010-04-28
> I just saw this pdf from corsair which is rather interesting:
[http://www.corsair.com/_faq/FAQ_flas...r_leveling.pdf]("http://www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf")  
Yes, impressive eh?

The [OCZ ATV Turbo]("http://www.ocztechnology.com/products/flash_drives/ocz_atv_turbo_usb_2_0_flash_drive") USB flash drives come with a lifetime warranty, and they don't mind if we install Ubuntu in them.

---

### Post by Herman on 2010-04-28
> I created a live usb with Ubuntu 9.10
I can store information and changes in it
I am trying to modify the installation menu.
I am compiling different versions of the kernel and I want to have a way  to choose them.
update-grub is not working as it should.
Any ideas?I don't think I understand you since the Live CD or 'Persistence' type of USB installation which has the Ubuntu Installer in it boots with syslinux, not GRUB.
If you have the regular Ubuntu installation, except in a USB flash memory stick instead of a hard disk drive then that boots with GRUB or whatever boot loader you installed, but it won't have an installer in it. 
I'm confused. :confused:

---

### Post by Richbuntu on 2010-04-28
> **P4man said:**
> advantages of a live session:
- You can create a writeable virtual filesystem so you can write changes, additional installed apps or documents back to the stick, but not with unetbootin I think.


If I can't use unetbootin for creating a writeable virtual filesystem, which software can I use for that and how? :confused:

---

### Post by P4man on 2010-04-28
ubuntu has a tool built in to make a live usb stick with persistence file (read/writable partition on the stick to save your stuff). I wonder if it runs from a regular live stick lol. find out, its in system > administrion >live disk creator.

If that doesnt work, then pendrivelinux has a ton of howto's ad they have a windows tool. Havent tried it, but look here:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by P4man on 2010-04-28
BTW, if you want to do a full install to USB stick, so you can do updates, boot fast, and well, do anything like a normal install, then just install it to the usb stick. Boot from a live stick (or cd), and use that to install to another stick, just like you would to a harddrive. Does require 4+ GB and Id say realistically, an 8GB stick.

---

### Post by Richbuntu on 2010-05-10
Thanks it worked. 
But I decided to install Ubuntu on my computer, it's easier to use like that and it's faster :)

---

