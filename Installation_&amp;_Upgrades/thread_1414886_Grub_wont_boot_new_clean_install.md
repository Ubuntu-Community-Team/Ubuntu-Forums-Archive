---
title: "Grub wont boot new clean install"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Rt4rd on 2010-02-24
A friend of mine asked me to install ubuntu on his system as he finally got enough of all the flaws and problems in his vista. I said no problems ill have ubuntu up and running in no time!

Well this is 2 days later and still nothing, he's computer refuses to boot from cd, i been changing the boot sequence allot but no indications of it wanting to boot the cd at all, whatever i try. So i made a bootable ubuntu usb-stick, doesnt work everytime i boot but sometimes... i get the load-up-screen, select install ubuntu, go ahead with the install, everything goes like clockwork. "restart is needed" sure, i restart it. grub says something like cant boot, or nothing to boot on hdd.. and thats that. ive reinstalled it several times (10+), trying ext2,ext3,ext4, partitioning it diffrently, ive tried it all. i even took out the scsi hdd, and tried an old ide-drive i had, gave me the exact same error.. 

i dont have all the specs but ill write what i know:
GA-ma78gm-s2h gigabyte motherboard
AMD Quad 3ghz
4 gb ddr
500 gb scsi

i hope someone has an idea, any idea is welcome!:|

---

### Post by darkod on 2010-02-24
> **Rt4rd said:**
>  he's computer refuses to boot from cd, i been changing the boot sequence allot but no indications of it wanting to boot the cd at all, whatever i try. So i made a bootable ubuntu usb-stick, doesnt work everytime i boot but sometimes...

It seems there are issues booting anything on that computer. I can only speculate but it's no surprise if ubuntu can't boot if there are booting issues.

I suggest loading BIOS optimized defaults unless the user has some special settings that are not easy to reproduce.

You have to get to a stage where you can boot the cd, the usb, easily. I guess ubuntu will work right away from the hdd after that (new reinstall might be needed).

---

### Post by Rt4rd on 2010-02-24
yeah i think youre right, BIOS is the problem.. i dont think he has been messing around with bios but returning to default is worth a try.

Thing is that when he had vista running on the box i also tried installing linux from within vista, but the vista (wich whas in pretty bad shape) wouldnt run the install program from the live cd at all, i tried with the notebook remix version and it worked up until 40ish % of the install, where it halted. but when booting after that i got the grub screen enabling me to choose vista or ubuntu.. after that i made an usb stick, and did a clean install and thats when grub started doing what i described in my first post, and i did not mess around with BIOS from the time it had dualbooting going and not finding any os to boot.  

thanks for the reply darkod

---

### Post by darkod on 2010-02-24
If you can boot from cd or usb into the ubuntu live desktop, you could follow these instructions and post the content of the results file. It might explain few things. Or not. :)
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

