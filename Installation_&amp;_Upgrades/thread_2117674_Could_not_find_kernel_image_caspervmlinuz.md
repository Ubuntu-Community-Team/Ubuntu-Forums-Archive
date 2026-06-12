---
title: "Could not find kernel image: /casper/vmlinuz"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by oyaji on 2013-02-19
> **garvinrick4 said:**
> 
[QUOTE=Netbook123;9866056]I'm new to Ubuntu and I'm not really experienced in this field. I installed Ubuntu Netbook on my HP Netbook via a pendrive and the installation wen of without a hitch but now whenever I try to boot up Ubuntu through the pendrive it starts and shows the menu and at the bottom says "automatic boot will occur in 5 seconds..." or something to that effect but when the countdown reaches 0 it starts over at five. Ive tried editing some settings and reading through the help stuff but I can't find my problem. And it will say at the bottom of these other bootup menus something like boot: and if i hit enter or wait five seconds it will say below that "could not find kernel image: /casper/vmlinuz" I've tried other boot options and i'm hoping that someone here will know how to help.
 
If you installed to hard drive it should boot without the pendrive installed. If you just want to boot off of the pendrive and it cannot find the linux kernel to boot from, just use startupdisk creator in System/Admin/startup disk creator and install a fresh install to pendrive. 
1. Download .iso file to Desktop
2. Put in flash drive
3. choose your .iso file and your pendrive in startup disk creator (make sure you choose pendrive and not hard drive)
4. Choose to format
5. slide slider over to get 4 gig of persistence.
6. install
Here is url for download.
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)[/QUOTE]
 
 
I have the same problem, so I tried the solution you posted above but to no avail.
 
I've been through my BIOS and tried all options for booting for my USB flash memory pendrive, including setting it to read automatically, as a HDD, and forced to read as a floppy drive, none of which worked. Boot order is correct (checked a number of times on each of several boot attempts) with the name of my pendrive properly displaying in the first boot slot.
 
I have reformatted the pendrive and reinstalled Ubuntu v 12.04.02 several times as well, even going so far as to uncheck the quick format option under Windows 7 for a complete and then even following that with a reformat by ticking the format option box on the installer - all formats done FAT32. I've re-downloaded the ISO file and have repeated all steps, in case the file was corrupted in the first download. I've tried this with 2 USB pendrives: a 4GB (~5 years old) SanDisk as well as an 8GB (~4 years old) generic-brand pendrive, neither of which has seen as many as 2-dozen write events to them over their entire usage history.
 
Sure could use some help - thanks in advance for any assistance you can throw my way.

---

### Post by codemaniac on 2013-02-19
Hello oyaji,

Welcome to Ubuntuforums!!

Your post is now moved to its own thread, in future please try to create new threads for your issues instead of posting on other people's thread.

Also feel free to edit your post and include more details if required. :)

---

### Post by oyaji on 2013-02-19
> **codemaniac said:**
> Hello oyaji,
 
Welcome to Ubuntuforums!!
 
Your post is now moved to its own thread, in future please try to create new threads for your issues instead of posting on other people's thread.
 
Also feel free to edit your post and include more details if required. :)
 
 
 
Umm... ok, and thanks... I guess.
 
In the interest of saving space and fearing to trouble otherwise helpful readers, I first dilligently searched the forums here looking for a similar problem and a solution to it that might apply to my own issue. Having failed in that, I followed ettiquette common to other forums of which I have been a member and instead appended my issue to an identical one rather than demanding attention for my own problem as if it were unique (which, obviously, it ain't) and starting my own thread.
 
I do appreciate the attention, and if there is any further need to ask for help with Ubuntu (which I fervently hope will be unecessary) then I will gladly start my own threads in the future. Meantime I hope some of that attention already garnered here will soon be applied to coming up with a solution to my not being able to boot from a pendrive!
 
It is worthwhile to note that subsequent to my late-night/early morning original post that, out of a pure sense of exasperation, I tried and succeeded in burning a v12.04.02 CD (not a DVD, mind you - a CD) image from the ISO file I downloaded and was using to install to my pendrive - and to my amazement and unbounded joy (contrasting diametrically with my fevered exasperation of last night) the CD will actually boot me into a trial of Ubuntu. (It is also perhaps noteworthy to mention that the boot screen has a purplish background when booting from CD, but when attempting to boot from pendrive the background is black...)
 
If booting and operation at the desktop were at all speedy, I would be satisfied now - but the CD is somewhat slower than pouring frozen molasses. I still want to be able to boot from a pendrive, and hope that the details I have included thus far are somehow helpful in provoking a solution forthcoming from any helpful reader. Thanks again in advance for any help you all can offer me.

---

### Post by oyaji on 2013-02-20
I see this thread is all the way back on page 4 now, so I thought I should bump it back up to the top in hopes of getting some attention...
 
Can anyone help me please?

---

### Post by dino99 on 2013-02-20
installation is made on partition(s) formatted as EXT3/4, not FAT32  ):P

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by oyaji on 2013-02-20
> **dino99 said:**
> installation is made on partition(s) formatted as EXT3/4, not FAT32 ):P
 
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)
 
 
Errrrrm... This makes no sense, as Windows offers no such format option called EXT3/4: options listed are NTFS, FAT, FAT32, and exFAT.
 
Besides that and as I already said earlier, I formatted again with the option *offered by the installer itself*. Are you suggesting that the Ubuntu installer formatted the pendrive in a format impossible for it to install to?
 
Sorry, that sounds nonsensical. The problem **must** lie elsewhere.
 
Thanks for the input though.

---

### Post by div1 on 2013-02-22
same problem here: could not find kernel image /casper/vmlinuz

---

### Post by oyaji on 2013-02-26
Bump to the top again for some attention, please? Problem still unresolved...

---

### Post by omid2s on 2013-02-28
[FONT=arial black]hello friends
Could not find kernel image: /casper/vmlinuz depend on speed of your usb flash.
I had this problem...but I find out this error depend on seed of Usb falsh.
however pen drive linux is correct make bootable.
[/FONT]

---

### Post by presence1960 on 2013-02-28
> **dino99 said:**
> installation is made on partition(s) formatted as EXT3/4, not FAT32  ):P

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

Bootable usbs are formatted as FAT32 not ext3/ext4.

---

### Post by presence1960 on 2013-02-28
What software did you use to create the bootable USB. I always use unetbootin. There is a Linux and a Windows version of unetbootin. 

Did you check the hashes (MD5SUM) of the downloaded iso to make sure the iso is not corrupted?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

