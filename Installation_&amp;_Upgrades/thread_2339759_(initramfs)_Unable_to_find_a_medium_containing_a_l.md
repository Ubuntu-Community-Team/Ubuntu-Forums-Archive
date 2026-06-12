---
title: "(initramfs) Unable to find a medium containing a live file system."
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by srinivaschandrakanth on 2016-10-12
Hi Guys,

I was facing some issue in loading my Ubuntu 14.04LTS in Dell Inspiron edition, any pointers are highly appriciated.

ISSUE: 
When I start my Laptop ubuntu screen loads up and abruptly a error comes as below:

```
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system.



```Googled this and found out that this is something related to mounting problem or something like that.
I have my important documents in the machine. Need someone experts advise so that I can take a backup copy and re-install my ubuntu.

my Laptop details are :
[https://www.ubuntu.com/certification/hardware/201408-15437/](https://www.ubuntu.com/certification/hardware/201408-15437/)

Or else please help a way forward to resolve this.

Thanks,
Srini

I saw this same error with lot of people which was not answered since long back, I really appreciate if an IT Pro can pitch in and help me.

Point to add is that I got this PC installed with ubuntu in it via manufacturer

---

### Post by oldfred on 2016-10-12
Have you tried to press enter?
Many report it just then boots.

Some have reported that it really is just that drive is slow coming up to speed. I do not understand that, but some have used a boot parameter to slow process. If that works, you can experiment with how long of a delay, but I would think it really is something else.

 BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash) Enter 'help' for a list of built-in commands.
(initramfs)
type exit and it may load.
May need to add boot parameter for drive to come up to speed.
 GRUB_CMDLINE_LINUX="rootdelay=90" 

If it does boot post this:

 systemd-analyze blame
systemd-analyze critical-chain

---

### Post by srinivaschandrakanth on 2016-10-12
thanks for the quick reply and helping me out.
When I press enter it says nothing and when I press exit it gave me some error as in pictures below.
 
[https://s14.postimg.org/m95nisk41/image.jpg](https://s14.postimg.org/m95nisk41/image.jpg)

So help me in understanding how to proceed now.

---

### Post by yancek on 2016-10-12
> 
Point to add is that I got this PC installed with ubuntu in it via manufacturer 		

Is this what happened the first time you booted the pre-installed Ubuntu?  If not, what changes were made.
The messages you see indicate a lot of directories/files do not exist which indicates a major problem.  I also see references to 'casper' which is a directory on a Live DVD or flash drive and not an installed system.

---

### Post by oldfred on 2016-10-12
Is this the live installer?
If so I might check that download was correct.
       [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What model Dell Inspiron?
Old BIOS or new UEFI?
What processor & video card/chip?

---

