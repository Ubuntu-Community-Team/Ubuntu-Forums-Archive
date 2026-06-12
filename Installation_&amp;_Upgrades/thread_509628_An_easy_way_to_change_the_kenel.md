---
title: "An easy way to change the kenel??"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by jedson3 on 2007-07-25
In order to use TMPFS I need to make sure that it is enabled in the kernel. Is there an easy way to make a simple change like this in the kernel?

Jedson

---

### Post by Pumalite on 2007-07-25
In order to add modules or compile the kernel, you need 'build-essential'; that means: you have to have make, automake, autoconf, latest gcc and kernel headers matching your kernel ( sudo uname -r)

---

### Post by jedson3 on 2007-07-25
Do you know of a tutorial that would spell out exactly how to do all that? I downloaded the build-essensal files and am able to get menuconfig to work on a kernel. But I can't find the kernel my os uses on my hard-drive. Is it not possible to just go into the kernel my os uses and make that change, or even locate the kenel on my ubuntu disk and make the change there. 

jedson

---

### Post by Pumalite on 2007-07-25
Terminal: uname -r

---

### Post by jedson3 on 2007-07-25
I have 2.6.20-16-generic. I find a folder listed as linux-headers-2.6.20-16-generic at /usr/scr/ but I don't find a kernel in any of the sub-folders there. Make menuconfig won't work unless I can get it into the same folder with a kernel. When I downloaded linux-2.6.22 just to experiment with, it had a file named "kernel" and I was able to make the needed change with menuconfig. 

jedson

---

### Post by argux on 2007-07-27
Hi, 

The kernel is a file called vmlinuz-2.6.20-16-generic in the /boot folder.

What you see in the folder in /usr/src are the sources to compile a new kernel. 'make menuconfig' is the configuration tool to do this, to configure a new kernel to be compiled. I don't think you need to do this. You only do this if you *know* some strange driver is not compiled in the kernel you're running, andI'd be pretty surprised if tmpfs wasn't in the kernel you're running.

Ubuntu's kernel is very generic, which means it was intended to be used in as many different configurations as possible, so unless you're using some very recent piece of hardware that just came out last month, or a super strange feature nobody uses, you can be pretty sure that what you need is included in the generic kernel (or, at least, in the repositories).

There's also the fact that tmpfs is very important for the system, and probably even required to run any modern linux system, so in this case you can be absolutely sure it's there. No need to recompile or anything. You just need to use it.

If you don't believe me, just type ```
mount
``` on a terminal, and you'll see something similar to this:

```
vim@vimlap:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run [COLOR="Red"]type tmpfs[/COLOR] (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock [COLOR="#ff0000"]type tmpfs[/COLOR] (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev [COLOR="#ff0000"]type tmpfs[/COLOR] (rw,mode=0755)
devshm on /dev/shm [COLOR="#ff0000"]type tmpfs[/COLOR] (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile [COLOR="#ff0000"]type tmpfs[/COLOR] (rw)

```

There you go. If you see that, then you have tmpfs in the kernel and you need nothing more.

---

### Post by jedson3 on 2007-07-27
Argux --

I typed in the Mount command, and it was as you said! Ah, how I wish I had know this before. I love both the concept and the reality of free software, but I am no technician and am always in over my head in technical matters. The info you shared was VERY helpful.  	
	
I went to the page you listed, by the way. I read Spanish with some difficulty, but could follow it well enough to be both impressed and intrigued. You might check out a web page which I write for  < [http://www.politicsofhealth.org/](http://www.politicsofhealth.org/) > and a related one < [http://www.healthwrights.org/](http://www.healthwrights.org/) >. The second one has a strong focus on Mexico which I think you might find interesting. 

Thanks again. 

jedson

---

