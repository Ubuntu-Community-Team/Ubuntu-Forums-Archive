---
title: "ubuntu partitioning questions"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2007-05-06
I have a few questions on the partition side of ubuntu that i want to get clear.

I have an asus g1 laptop thats going to boot ubuntu alone.  nothing else, but the vbox or whatever it's called that boots up OS within linux.  specs:
2.0  ghz duo core T7200
2 gbs of ddr2 ram
160 gbs sata 5400

im going to partition my hard again for ubuntu, and i need some advise on how to do it.
4 gbs swap
10 gbs/root
145 gbs /home
75 mbs /boot (maybe, is it even needed?  would it do anything for me?)

anything else you guys would like to add?  with ya advice, i wanna do the reformat tonight and getting all my updates going and such.  maybe even a little diablo 2 :)  (yes i still play that game. hahah)

thanks guys.




P.S.  Need more specs?

Intel Core 2 Duo 2.00GHz T7200 667MHz FSB 4MB L2 Cache

15.4" "Glare Type" WSXGA+ w/ Asus Splendid Video Technology

2GB DDR2 667 Dual Channel (2 Dimms)

160GB 5400RPM SATA

8x DVD Super Multi w/ Lightscribe

NVIDIA GeForce Go 7700 512MB

1 x Type I/II PC Card Slot

Gaming bag and Mouse

Gaming feature- ASUS Direct Messenger

Gaming feature - ASUS Direct Flash

Intel 945PM Chipset

RJ11 56K Modem

10/100/1000Mbps LAN

802.11a/b/g Wireless LAN

Bluetooth v2.0 +EDR

4 USB's

1 IEEE 1394

1 x S-Video TV-out, 1 x DVI, 1x VGA

3 Audio Ports

Integrated Sound card

Front/Side Internal Speakers

Vertical Scrolling Touchpad

4-in-1Card Reader

1.3MP Camera

8-cell lithium ion

Approx 3 hours Battery Life

6.84 lbs.

[http://forum.notebookreview.com/showthread.php?t=91603](http://forum.notebookreview.com/showthread.php?t=91603)

---

### Post by zmike1 on 2007-05-06
From what little I can tell, you don't need that much swap.

One alternative to consider is simply to let the installer make comfortable use out of whatever free space you have available.  If you're only putting ubuntu on the machine, going with the defaults goes very well.  
Have fun.

---

### Post by quark_77 on 2007-05-06
Hi Sugi,

I have 1GB DDR RAM and 1GB swap space - it's never used by linux to my knowledge so I'm not sure if you need 4GB Swap space... hell, with that size hard disk why not?! My boot partition currently takes up 53.5MB - you don't need a separate boot partition as such, although it can be useful. Mine is 500MB in size which is excessive... Anyway, if you don't specify a /boot partition it'll be created as a sub directory on the root partition. 10GB should be fine for root unless you plan to install a lot of software.

As for how to go about doing this - there is a step in the Ubuntu install (livecd and alternate) that asks how would you like to partition disks - select manually edit the partition table. Then, it's fairly self explanatory. Destroy partitions you don't want, create ones you do, set their formats, mount points etc and click next.

Hope this helps, I agree Diablo II IS a good game. Never tried it under wine, windows still lurks on my laptop...

Quark_77

---

### Post by Sugi on 2007-05-06
where is all my games going to go on my partition?  /home or / dir???

what about primary or logical types of partions???

sorry for my english, it's not native to me

---

### Post by quark_77 on 2007-05-06
Your games will go wherever you set wine up to run them, so probably under home as they'll be installed on /home/username/.wine/drive_c/....... unless you choose to install your wine programs outside the /home tree, in which case /. All your linux programs go on /.

As for logical vs primary - you only need one primary partition and this can be any of them, I presume /boot is the most logical. there can be up to four primary partitions, then, you create a logical partition. This is just more empty space in which you create other partitions. Then create your partitions within this logical partition e.g. / /home or whatever.

Your English seems perfectly good to me!

Quark_77

---

### Post by ajgreeny on 2007-05-06
Just let ubuntu do it all as default and you will end up with two partitions, / as root and another (possibly within an extended partition) as swap.  With 2GB of ram you will never need 4 GB of swap, so stick with whatever ubuntu gives you as it installs and all should be OK.  As others have said you can do whatever you want in linux with the partitions, but to be honest, it is simplest to let the system take care of all that by itself and then get on and enjoy it.

---

### Post by Sugi on 2007-05-06
what about future reformats, i've overheard once, that if you make /home within another partition, it would be save and used in the next reformat.  so that means, like you delete / dir and install ubuntu again.  when it comes back up, all the stuff on your /home partition is saved.  right?  thats something maunal i want to config.

---

### Post by quark_77 on 2007-05-06
> **Sugi said:**
> what about future reformats, i've overheard once, that if you make /home within another partition, it would be save and used in the next reformat.  so that means, like you delete / dir and install ubuntu again.  when it comes back up, all the stuff on your /home partition is saved.  right?  thats something maunal i want to config.

That's possible. When you install Ubuntu again, you will see your previous partitions in the partitioning table. You can delete all the others, resize them or whatever, but if you leave the one with /home intact then you can set its mount point to /home again and it will be used as your /home, complete with all your old data.

Enjoy!

Quark_77

---

### Post by Sugi on 2007-05-06
> 
As for logical vs primary - you only need one primary partition and this can be any of them, I presume /boot is the most logical. there can be up to four primary partitions, then, you create a logical partition. This is just more empty space in which you create other partitions. Then create your partitions within this logical partition e.g. / /home or whatever.

now im just confused on the primary and logical partition.  would it be more like this???


primary / 
logical /home
either /swap
logical /boot

---

### Post by Sugi on 2007-05-06
bamp.   should / dir be ext3?  because im having problems with the reformat.  it gives me some error. installing ubuntu.



primary / dir 10 gbs ext3
primary swap 768 mbs
primary /home 149 gbs ext3

What should i do?

---

### Post by quark_77 on 2007-05-06
/ dir should be ext3 if you have no separate boot partition as grub won't like it otherwise.

Sorry, my error above, there are "primary" and "extended" partitions. In the "extended" partition you can put as many logical partitions as you like, although you can only have 4 primary ones. As for which one to make primary, if you don't have a separate boot I'd go for root (/) as this seems the most obvious choice.

So, you could do as you said above:
> primary / dir 10 gbs ext3
primary swap 768 mbs
primary /home 149 gbs ext3

or

> primary / dir 10 gbs ext3
logical swap 768 mbs
logical /home 149 gbs ext3

Apologies,

Quark_77

---

### Post by Sugi on 2007-05-06
what about this error i get trying to install ubuntu???  it says something about "creation of sda installion has failed"  what should i do about this???

thanks for the primary and logical answer.

---

### Post by Sugi on 2007-05-06
something i've notice when it comes to partitions, if the ubuntu install can't read how much of the hard drive is being used, it can't format it.  why is it?  my friend had the same problem, and we couldn't do anything about it.  what should i do?


IE:
partition 1 "/" New: 10001 GBS EXT3 Primary               Used: 33 MBS
partition 2 New:  768 MBS SWAP Primary               Used: 0 MBS
partition 3 "/home" New: 149512 EXT3 Primary                Used: unkown

In partition 3: it says next to used: unknown, how should i fix this??  how can i fix this?

---

### Post by quark_77 on 2007-05-07
If you can't format it using the setup program then you can try gparted. Go to System > Administration > Gnome Partition Editor on the live CD. This will examine your drives and show you the setup. If the filesystem type is "unknown" it will show up as a black region - if you right click on it you should be able to format it using the format to command.

Gparted does have a tendancy to auto-mount filesystems - I don't know why this is and I think for an unknown filesystem it shouldn't matter but if it does you can right click the desktop icons and unmount the volumes.

Once you've formatted the partition with gparted then you should be able to go back into setup and complete the install.

Hope this helps,
Quark_77

---

### Post by Sugi on 2007-05-07
tryed all the options for making a new partion.  I even let ubuntu do it's work the way they wanted to.  it worked, but i didn't like it.  so i tryed doing another format, and for some reason it worked.    I'm up and running now.  So, im happy.  Thanks everyone.

P.S.  Now, I got new problems to deal with.  yea ^_,^

---

