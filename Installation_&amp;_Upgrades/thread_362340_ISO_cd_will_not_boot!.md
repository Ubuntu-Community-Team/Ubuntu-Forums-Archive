---
title: "ISO cd will not boot!"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by j00ford on 2007-02-15
Hi,

Just starting out here...I have copied the iso image on a cd and am trying to install. I select the boot from cd option during startup and for some reason it still boots from the hard drive and loads xp. I have a Lenovo 3000 N100 laptop where I have formated the hard disk and have multiple partitions. Any ideas how I can get the system to boot from the cd and proceed with the install?

Thanks for your help 

-J

---

### Post by louis_nichols on 2007-02-15
Did you check the ISO image before writing it? I mean, the MD5 sum. It might be that the ISO was corrupted during download. Or it might be that there was an error when burning the CD, in which case you'd have to simply burn another one.

Of course, it is possible it's because of the laptop. Can you boot toher CDs?

---

### Post by j00ford on 2007-02-15
no...i had tried to boot this other cd (gparted) to partition the hard disk...and that won't boot either...i will check the md5 sum and burn to another cd and try again..i also think, like u said it might be something specific to the make of the laptop...i must be missing something there....any Lenovo experts out here????

thanks for replying... :)

---

### Post by the.phantom on 2007-02-15
was the qtparted cd a bootable disk?
where did you d/l it from?

can you (in XP) put a bootable cd in the drive and will it boot up?
if not i would guess you need to check your BIOS settings and have it boot CD first , then hard drive

---

### Post by j00ford on 2007-02-16
yes...i tried setting the bios to boot from cd...still wont work...i am pretty sure that the laptop boots from the cd (i tried a windows cd to check).

---

### Post by j00ford on 2007-02-16
I finally got all the files on a thumb drive and my laptop finally boots from the USB drive.....However I get an error saying Operating system not found ----Any suggestions??

Thanks - J

---

### Post by Snowbat on 2007-02-16
Operating System not found means it failed to boot!

Going back to the CD writing for a minute, did you write the ISO file to CD as an image (eg. File/Burn Image in Nero)?  Simply copying the ISO file to CD will not give you the desired results, nor will extracting the contents and burning those.

The same is true for USB drives actually and may well be the source of your problems.

---

### Post by lil_niles on 2007-09-02
just to rule out the cd being the problem, make sure you are specifically selecting the option to burn a cd FROM an image file (.iso) and make SURE that the burn speed is x4 and the CD is the right size. it is imperative that the CD be burnt at x4 speed! i just did an install of ubuntu and got all kinds of crazy errors because i burnt my cd too fast.  hope that helps!

---

### Post by justinpcletus on 2008-01-15
I've got the same problem, but I've tried to boot the same CD on another system and it worked fine.

It seems to be only my Lenovo 3000 N100 that fails.  It used to boot from CDs just fine.  That's how I got Ubuntu on it in the first place.  However, now when I try to boot from a CD, it boots from the hard drive no matter what the BIOS settings are.  I even disabled booting from the HDD altogether...  Still boots the Ubuntu installation on the HDD!

---

