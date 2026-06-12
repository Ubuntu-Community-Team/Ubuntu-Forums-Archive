---
title: "ACPI issue"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by Unknown201 on 2010-10-22
When Ever I try to install Ubuntu I must disable ACPI, I have Toshiba C650
The thing is how can I disable it so I can access Ubuntu,
it refuses to run, how to disable it before running ubuntu?!

to make it more clear: 
> 	 Re: Satellite C650-14W - Does Linux work on it? 
Posted: 04-Sep-2010 18:31     in response to: giltosh	  	
 		Reply
Yes, you can install Ubuntu on the C650, but ACPI is not yet supported so it must be disabled in order to boot. This can be accomplished by pressing the shift key while booting to obtain a boot menu. You might have to hit the escape key to get a second menu (I can't remember), then you select Linux and hit F6 which opens a menu, select acpi=off and the installation disk will boot.

To avoid following this procedure at each boot, grub2 must be reconfigured. Modify the line in the file /etc/default/grub from:
GRUB_CMDLINE_LINUX=""
fo
GRUB_CMDLINE_LINUX="acpi=off"
or
GRUB_CMDLINE_LINUX="ht"

Then do:
$ sudo update-grub

Ubuntu will work but without ACPI, your computer will run down it's battery faster than it would with ACPI. This bug has been reported and hopefully will get fixed. 

Ian
Source: [http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=54715&tstart=0](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=54715&tstart=0)

I must do what he said but I can't since I can't boot up the system, anyone can help?!
Thanks in advance :)

---

### Post by lechien73 on 2010-10-22
How far do you get when you try to install Ubuntu?

If you get to purple screen with the image at the bottom of a keyboard and a person in a circle, then press Escape here.

At the next menu, highlight "Install Ubuntu", and then press F6.

From the next menu, choose "acpi=off".

---

### Post by Unknown201 on 2010-10-22
I was able to fully install but not boot after restarting when instillation is done.

---

### Post by The Cog on 2010-10-22
So how do you get on following the instructions in that post you linked to? Do you get the GRUB boot menu if you hold shift sown while booting?

---

### Post by Unknown201 on 2010-10-26
> **The Cog said:**
> So how do you get on following the instructions in that post you linked to? Do you get the GRUB boot menu if you hold shift sown while booting?

Thanks I was able to work it out after I found a thread on this forum telling how to do it.

---

### Post by elton1984 on 2010-11-01
Can you give me the thread link? i facing same problem.....
Thanks!

---

### Post by Bucky Ball on 2010-11-01
> **elton1984 said:**
> Can you give me the thread link? i facing same problem.....
Thanks!

Here, here! Link please. I just bought a Toshiba Satellite Pro L510 only to find their seemingly Linux friendly approach online was skin deep and Ubuntu is almost impossible to run on it. But I have not given up yet. 

Tip: I discovered the 2.6.35.* kernel runs on some of these problematic machines. Just figuring how to go about getting that together. I guess when that kernel is available as ISO might be as easy as installing from it and following the 'ESC' + F6 instructions in a previous post. Might try that with my 10.10 CD. Tried everything from 8.04 - 10.10. Finally the 10.04 alternate installed but when I choose Ubuntu kernel in the grub menu it takes me to a login prompt. Doesn't seem to have installed anything; no desktop, nothing. /X11 empty.

So, lets keep working on this. Thanks for making it so tricky Toshiba. Or is it the i* series processors?

* Wondering if one could download and install, in the right order, from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.1-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35.1-maverick/")

... then run the 'ESC' + F6 trick.

** This works for me and controls the fan. Running VERY cool now:

```
acpi=copy_dsdt
```Make it permanent by editing /etc/default/grub. Make this line (if there, if not add it):
```
 GRUB_CMDLINE_LINUX=""
```... look like this:

```
 GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```Worked for me. Wireless still totally erratically swinging between 50-100% though. Hopefully this will be fixed in a future update or I stumble on a fix in the, hopefully, near future.

---

