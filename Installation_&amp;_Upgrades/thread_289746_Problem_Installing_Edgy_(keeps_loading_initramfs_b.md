---
title: "Problem Installing Edgy (keeps loading initramfs busybox)"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Progressive on 2006-10-31
Does anyone know why my live CD for Kubuntu Edgy amd64 wont boot up half the time and the other half of the times it loads something called busybox and displays a command line interface with the word initramfs?

---

### Post by vixenk on 2006-10-31
It may be related to this bug...
[https://launchpad.net/distros/ubuntu/+bug/67487/](https://launchpad.net/distros/ubuntu/+bug/67487/)

---

### Post by Progressive on 2006-10-31
maybe, i dont know... most of them couldn't even get to the console... mine boots to busybox. Much like this person [http://www.linuxquestions.org/questions/showthread.php?t=462877](http://www.linuxquestions.org/questions/showthread.php?t=462877)

I am actually in edgy because I upgraded from dapper... but i had some problems so I want to clean install. My problems are that Akregator crashes and i can't get Beryl to work.

If you can help me with the akregator problem i guess i wont even need to reinstall... I miss RSS

---

### Post by vixenk on 2006-10-31
In my attempts to get Edgy to work, I got the busybox a few times as well. It actually wasn't until I tried downloading and burning Edgy to disc for the 3rd time that I got it to work. I got the blinking cursor/lock ups during my attempts as well, which is part of the reason why I suspect they're all related. Perhaps a large number of people are obtaining fouled up downloads? I don't know. I checked each download against the MD5 checksum and verified the data on the discs got burned correctly and they all came out ok. It's strange.

So far, the most I can suggest is that you redownload and reburn the disc, or try installing the alternate non-live cd.

---

### Post by RichJacot on 2006-11-12
I'm am now getting the same thing:

[FONT="System"][SIZE="2"]Busybox v1.1.3(Devian 1:1.3-2ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't tty; job control turned off
(initramfs)

#[/SIZE][/FONT]

I have been trying to do a fresh install of edgy and encrypt root, swap and home.  I have done at least 8 or 10 different full installs with the single cd I downloaded.  IT WAS WORKING, at least for a few installs.  At this point I have even downloaded the alt cd and I get the same result after installing from that.

I think it has something to do with the partitioning.  The reason I think so is because...  If I let the installer erase the whole disk and let it do the partitioning piece, after the install it boots-up fine.](*,)   Needless to say the default partitioning setup is not what I need. 

I'm open to suggestions, anyone?

---

### Post by rshel on 2006-11-12
HI,

This is probably way too simple of an answer for your problem, but it fixed mine.  I kept getting the same message this morning.  Turns out it was one of two things: 1. my son had left a windows video game cd in the cd drive (probably not the cause, but I removed it and for the sake of full disclosure I thought I should mention it) 2. I paused grub during the boot process and found that it was trying to boot an earlier version of ubuntu rather than the latest kernel.  After I selected the most recent upgraded kernel, no problems.  Like I said, pretty simplistic (sort of like checking to see the power cable) but that was the problem for me.

---

### Post by dunkgreen on 2007-10-18
> **rshel said:**
> HI,

This is probably way too simple of an answer for your problem, but it fixed mine.  I kept getting the same message this morning.  Turns out it was one of two things: 1. my son had left a windows video game cd in the cd drive (probably not the cause, but I removed it and for the sake of full disclosure I thought I should mention it) 2. I paused grub during the boot process and found that it was trying to boot an earlier version of ubuntu rather than the latest kernel.  After I selected the most recent upgraded kernel, no problems.  Like I said, pretty simplistic (sort of like checking to see the power cable) but that was the problem for me.

The latter problem was the same as mine.  As soon as I chose the -16 from GRUB I was able to boot.  Thanks!

---

### Post by erv2 on 2007-10-18
> The latter problem was the same as mine. As soon as I chose the -16 from GRUB I was able to boot. Thanks!

hi, i am having the same problem, how to "choose -16 from GRUB"? i am new to ubutu, now i think i'd be a good time to try.

there are 6 options on the boot menu, where do i do the thing you did?

thanks.

---

### Post by RavUn on 2007-12-22
Could anyone tell me how to do what rshel did?

I've been getting the busybox / (initramfs) message when trying to install.

I tried adding root=/dev/cdrom under the boot options (F6) as mentioned in a different thread but it did nothing.  I currently have 6.06 server installed on the PC and I want to install 7.10 desktop instead...

---

