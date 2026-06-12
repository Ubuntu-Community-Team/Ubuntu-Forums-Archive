---
title: "Another installation problem"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by chet8625 on 2016-03-16
Compaq CQ2014PC
3GB
AMD E-300 processor
160GB available disk space

Hope this isn't too confusing. And forgive me as I'm noit a techie...

Father's hard drive died in this PC. Decided to install Ubuntu for him. I had installed version 10xxxxxx on another PC and liked it so figured he could work with it.

Downloaded a UUI and version 14xxxxx. Put a new drive into his PC and tried to install on a clean hard drive. Got as far as installing a"grub" and it hung. Tried this three times and same result.

Still had my version 10xxx so loaded that on the PC with no problem, except no updates or maintenance or upgrade path with that version so decided to try version 14xxxx again.

Go to install it from my USB drive and get a message ending with:

[121.704726]---[end kernal panic - not syncing: VFS: unable to mount root fs on unknown block (2,0)

I tried the "try it before you install" and got the following:

---compression error
System halted

Bottom line is that I'd like to install version 14xxxxx so my father can get support and maintenance. It's running fine now (typing this under version 10xxxxx).

Any suggestions?

---

### Post by v3.xx on 2016-03-17
Times have changed and it seems you got left behind.  10x is end of life and no longer supported.  14x has a new desktop called Unity.  It is resource demanding and my first thought is its too much for your dad's computer.  I run Mate which is a clone of the old 10x system.  Maybe it would be a better choice.

---

### Post by mastablasta on 2016-03-17
> **chet8625 said:**
> 
Go to install it from my USB drive and get a message ending with:

[121.704726]---[end kernal panic - not syncing: VFS: unable to mount root fs on unknown block (2,0)

I tried the "try it before you install" and got the following:



the image you are working with is a "bad download".

re-download the image. after it is downloaded check the md5sum: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
or use torrent for download in which case the image will be checked while it is downloaded.

after creating the USB drive, do the test again. if test fails, then the method of recording image to USB is flawed. a couple of USB image creators are: Pendrive Linux, unetbootin, yumi, USB startup disk creator, LinuxLiveUSB (windows only), mkusb (works on Ubuntu, created by forum member). sometimes the program handles the creation in a bad was. using a different program solves it.

edit: e-300 should do fine with unity. though using a lighter interface will bring more speed. Ubuntu Mate is the one that looks like the old 10.x version. other light options - Xubuntu, Lubuntu, LXLE...
e-300 is currentl ysupported by AMD drivers. this will no longer be the case starting with 16.04 when only opensoruce drivers will be available (20-30 % worse than AMD drivers). Good news - 14.04 is supported until 2019. there is no soltion yet what they will do with newer 14.04 version and drivers (14.04.[COLOR=#FF0000]**5**[/COLOR] and on). on the other hand if you install 14.04.[COLOR=#FF0000]**1**[/COLOR] then you are "safe" until 2019.

---

### Post by chet8625 on 2016-03-17
I'll download a new ISO. Question... should I download the 32-bit or 64-bit version? The 64-bit version was what hung up. the 32-bit wouldn't even start to install.

---

### Post by v3.xx on 2016-03-17
You have 3G of ram.  No matter which flavor you go with, I would say 64bit.

---

### Post by chet8625 on 2016-03-17
Thanks. Started download before leaving for work and will go through steps above when I get home tonight.

---

### Post by v3.xx on 2016-03-17
More about drivers

[http://ubuntuforums.org/showthread.php?t=2316215&p=13454247#post13454247](http://ubuntuforums.org/showthread.php?t=2316215&p=13454247#post13454247)

Good luck :)

---

### Post by justen_m on 2016-03-17
re: resources: I am running 32-bit 16.04 on a much less capable system (1.5GB RAM, 1.6GHz single core Intel Atom CPU) and it works fine, albeit very slow.
re: 32 vs 64: With just 3GB of RAM, why would you recommend 64-bit over 32? Personally, I would go 64-bit just so it was the same OS as my other systems. The Intel Atom on my netbook is only 32-bit, so I don't have an option on that ancient machine.

In any case, it does sound like a bad download. I'd recommend you download a new ISO and make a new USB boot stick.

---

### Post by v3.xx on 2016-03-17
> **justen_m said:**
> With just 3GB of RAM, why would you recommend 64-bit over 32?

Mileage will vary, but also works with less.  My 2G system:

> Desktop:  MATE 1.12.1  Distro:  Ubuntu 16.04 xenial
Kernel:  4.4.0-13-generic x86_64 (64 bit)
Dual core Intel Xeon X5650
Memory:  377.2/2000.4MB

---

### Post by chet8625 on 2016-03-17
so I ran MD5SUM on a new download and it checked out fine.

Since I wasn't sure how to run it on the USB drive (what the terminal command would be) I tried again to "try before installing" and got:

symbol 'grub_crypto_hash' not found

tried installing and got nothing.

can you give me the command line to check the USB?

Also, I initially had a problem with the UUI before loading version 10xxx from the CD... could that be an issue?

---

### Post by v3.xx on 2016-03-17
Again it sounds like a bad download, but it checksum, so we know thats good.

Could you burn a dvd?

[This tutorial]("https://ubuntu-mate.community/t/ubuntu-beginners-guide-complete-how-to-install-and-run-first-update/955") is general use and may be some help in the install process.

I have found installing by flash drive to be hit and miss.  I have had my best luck with unetbootin.

No other ideas at the moment.

---

### Post by chet8625 on 2016-03-18
I'll pick up a DVD this weekend and give it a try. Thanks

---

### Post by chet8625 on 2016-03-19
Update:

Probably skipped a most obvious step... taking the flash drive and trying to install or try Ubuntu on my own machine. It couldn't so I assume the flash drive doesn't work (or the imaging didn't work). So I went out and got a DVD.

Burned the DVD (version 14xxx LTS) and rebooted. It looked like it was going to work. Started going through all the steps but now the install has stopped at:

Running "grub-install/dev/sda"...

(This is where the original flash drive install hung up)

Now what???

Edit: I restarted and booted to the "try before you install" and it seemed to work just fine (given my limited browsing around Ubuntu). Restarted without the DVD in and got a message "No boot disk has been detected or the disk has failed" (telling me the install never was finished?)

FINAL EDIT!!!: Tried to boot again and it worked. I thing the only difference was I checked the "download updates" when it was being installed.

Everything seems to be working. Thanks for all the help.

---

### Post by v3.xx on 2016-03-19
I guess you have one finicky computer, but you got it working, good show.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Enjoy ):P

---

