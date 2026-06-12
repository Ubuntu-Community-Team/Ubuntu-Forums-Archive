---
title: "Please critique installation setup"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by binjured on 2006-06-08
Greetings!  I am a soon-to-be new Ubuntu user and I want to have my installation setup critiqued by the community before going ahead.  

Version: Alternate AMD64.  
My question regarding this is: yes I do have an AMD64 chip, but is Linux like Windows in that 64bit apps/drivers != 32bit apps/drivers?  Also (tangent) are dual-core AMD64 chips supported yet (planned upgrade)?

1) I will be dual-booting Windows XP Pro, for the sole purpose of gaming.
2) I have two hard drives: 1 80gb and 1 250gb, both SATA.  I plan to partition like this:
hdd0 (250gb): 
 a) Linux partition of probably around 50gb (do you think this will be sufficient?)
 b) Swap of 500mb (standard, right? is more better?)
 c) FAT32 of ~199gb: storage & backup (general files, possibly used for both linux/windows... can i backup linux to a mounted FAT32 drive using the built-in backup functionality I've heard about?)
hdd1 (80gb): NTFS: Windows XP Pro

Unfortunately, the Wiki only covers dual booting when using a single hdd.  Am I to assume GRUB will require no special setup to let me choose between linux and windows at boot when using two separate hard drives?

Also, I know writes aren't *really* supported on NTFS (I don't know what I'm going to do about my web-server as it is windows and using NTFS, I guess I will need to switch it to Linux as well which I don't really want to do right now), so is FAT32 the only solution for compatability between linux/windows?

Hopefully this was clear enough and not too tangent-filled ;)

Thanks!

---

### Post by nanotube on 2006-06-08
[QUOTE=binjured]Greetings!  I am a soon-to-be new Ubuntu user and I want to have my installation setup critiqued by the community before going ahead.  

Version: Alternate AMD64.  
My question regarding this is: yes I do have an AMD64 chip, but is Linux like Windows in that 64bit apps/drivers != 32bit apps/drivers?  Also (tangent) are dual-core AMD64 chips supported yet (planned upgrade)?
[/quote]
i'd recommend you go with 32bit ubuntu, since as you suspect, drivers and things like flash are still quite problematic for 64bit. so if you don't feel like screwing around with that stuff to get it to work, just use 32bit.

> 
1) I will be dual-booting Windows XP Pro, for the sole purpose of gaming.
2) I have two hard drives: 1 80gb and 1 250gb, both SATA.  I plan to partition like this:
hdd0 (250gb): 
 a) Linux partition of probably around 50gb (do you think this will be sufficient?)
 b) Swap of 500mb (standard, right? is more better?)
 c) FAT32 of ~199gb: storage & backup (general files, possibly used for both linux/windows... can i backup linux to a mounted FAT32 drive using the built-in backup functionality I've heard about?)
hdd1 (80gb): NTFS: Windows XP Pro

read this excellent guide about planning your partitions:
[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

(btw, yes, i'd say 500megs is generally plenty for a swap, especially if you have a lot of ram.)

> 
Unfortunately, the Wiki only covers dual booting when using a single hdd.  Am I to assume GRUB will require no special setup to let me choose between linux and windows at boot when using two separate hard drives?

yes, grub should handle that just fine.

> 
Also, I know writes aren't *really* supported on NTFS (I don't know what I'm going to do about my web-server as it is windows and using NTFS, I guess I will need to switch it to Linux as well which I don't really want to do right now), so is FAT32 the only solution for compatability between linux/windows?

there is a driver for windows that can read/write ext2/ext3. that seems like a better option for sharing files between win and lin. it is also mentioned on that partitioning guide i linked you to.

> 
Hopefully this was clear enough and not too tangent-filled ;)

Thanks!
clear enough. :) always good to ask before screwing around with things ;)

---

### Post by binjured on 2006-06-08
Thank you for the quick and thorough reply, nanotube!  After reading the guide you supplied and another I found (after reading at the bottom "if you have a 200gb hdd create as many partitions as you can") I have come up with the following:
```

/           200mb
swap        2gb (currently 1gb ram, later 2gb)
/usr        5gb 
/boot 	    50mb
/tmp 	    2gb
/var 	    5gb
/usr/local  5gb
/home 	   ~230gb

```
Since I don't really understand where most files go in Linux I basically just took the numbers from the guide I found and padded them a bit.  I'd rather be over space than under obviously!  My other consideration is the /home partition -- can I make backups of this partition *to* it without causing any crazy problems?

Thanks again!

---

### Post by markh on 2006-06-08
I'd probably have something like a 1Gb /swap, and just have the 50Gb for the Linux / partition - that's usually more than enough. I doubt I'd make so many partitons, since my personal opinion is that it doesn't really help and just confuses things. Apart from that your setup looks fine :)

---

### Post by nanotube on 2006-06-08
[QUOTE=binjured]Thank you for the quick and thorough reply, nanotube!  After reading the guide you supplied and another I found (after reading at the bottom "if you have a 200gb hdd create as many partitions as you can") I have come up with the following:
```

/           200mb
swap        2gb (currently 1gb ram, later 2gb)
/usr        5gb 
/boot 	    50mb
/tmp 	    2gb
/var 	    5gb
/usr/local  5gb
/home 	   ~230gb

```
Since I don't really understand where most files go in Linux I basically just took the numbers from the guide I found and padded them a bit.  I'd rather be over space than under obviously!  My other consideration is the /home partition -- can I make backups of this partition *to* it without causing any crazy problems?

Thanks again![/QUOTE]
2gb swap is really overkill - it will never be used by the system, and will just be wasted space. i'd reduce it to 1gb. (but if you feel happier with 2gb, there is nothing wrong with it, it's just not useful)

then, i'd merge /usr and /usr/local into one 10g /usr partition. there is no reason to split up those. 

next, 50mb for /boot and 200mb for / is too little. my /boot right now, for example, uses 22megs (i have a few kernels installed). so 50mb is "ok" but kinda close. also, if you do some things as root, you might end up with some files in /root, which is part of / in your setup. all the stuff in /etc, also part of /, takes up 38m for me. so i'd give 100m for /boot, and 1g for / (steal that 1g from swap :) ).

everything else looks ok.

on a desktop system there really is not that much call for creating so many separate partitions, but it doesn't hurt, and you learn something in the process. :)

to learn about what all the directories mean in detail, you can read this link: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

in brief, /usr is where software gets installed, /home is where users' personal files and docs get stored, /var is for system logs and such (would also store email, if you run a mail server).

as to backing up your /home... i am not sure what you mean. you are saying you want to back it up to itself? as it, make a copy of /home to the free space on /home? yes, i suppose you could do that. but you know, offline backups are better - if your hd blows up, it will take everything with it. 

good luck, and have fun ;)

---

