---
title: "GRUB error"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by drlog on 2007-02-12
```

```I have a AMD Athlon 2600+ 2.13 Ghz processor from my HP Pavilion 525c.  Awhile ago the hard drive went out so I bought a new 250GB one.  Unfortunately the BIOS of the motherboard can only read like 32gb I guess.  

So when I try and install Ubuntu I try and make sure the partition is setup at the beginning, even though it sees the whole 250gb.  But when it all sets up and I restart it always says GRUB loading error 18 or sometimes 17.  

So I can't get Ubuntu to run at all, any help is GREATLY appreciated, I just wasted an entire day trying to get this taken care of

---

### Post by Herman on 2007-02-12
Hello drlog, 
When that happened to me I had to go buy another hard disk that was less than 33 GB. It was in a small computer with a laptop hard drive. I tried and tried too, so I know how you feel.  There were no jumper settings for jumpering it off from 40GB to 30 GB, due to the fact that it was a laptop hard drive I think.
The regular sized (physically) hard drives for desktop PCs sometimes have jumper settings for jumpering the hard drive off to 30 GB, but even those would be getting rare these days, I'm not sure, I doubt if a 250GB hard disk would be likely to be able to be jumpered all the way down to 30.

                        Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                         2.11 GB or 4095 cylinder limit
                         3.26 GB or 6322 cylinder limit
                         4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                         8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                         33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                         137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
                        
You can probably check the date of your computer's BIOS by going into 'setup' by pressing the appropriate key during the early stages of booting.
                         
                        You could check at your motherboard manufacturer's website, (find it with google), to see if there is a newer update for your machine's BIOS available. If so, you can download it and try 'flashing the BIOS'.  That has been reported to have solved similar problems for some people. You never know, it would be worth a try.

Otherwise, a nice big hard disk like that is always a useful thing to have, I would keep it and get an external USB hard drive case for it and use it as an external drive for storing all my data. Sadly, you might have to do the same as I had to do and buy another hard drive that is small enough for your BIOS. (Keep your 250 GB one though). I'm sorry to have to say that, but I hope it's better than no answer at all.
Regards, Herman

---

### Post by rumli on 2007-02-14
In the GRUB menu on startup, try selecting the Ubuntu option with Recovery mode.

Once you get to a command line, backup your /boot/grub/menu.lst as follows:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Then edit your /boot/grub/menu.lst as follows:
```
sudo nano /boot/grub/menu.lst
```
and then comment out or remove the "savedefault" line from the main ubuntu entry.  The main ubuntu entry should then look something like:
```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
boot

```
Reboot and choose the regular Ubuntu option in the GRUB menu.

---

