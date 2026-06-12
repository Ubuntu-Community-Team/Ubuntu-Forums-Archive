---
title: "linux-rt"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by gigamico on 2011-07-28
Hi guys,
I'm trying to install the linux-rt package because I've to write a real time application.
Can someone tell me if this is the correct package:
[https://launchpad.net/ubuntu/+source/linux-rt/2.6.31-11.154](https://launchpad.net/ubuntu/+source/linux-rt/2.6.31-11.154)
?

For now I've downloaded the linux-rt_2.6.31.orig.tar.gz file, but I'm not sure that it is the right one.
I've Ubuntu 11, kernel ver. 2.6.38-8-generic.

---

### Post by jerrrys on 2011-07-29
The -preempt and -rt kernels are no longer being developed due to lack  of support.  Focus has instead turned to the -lowlatency and -realtime  kernels, particularly for the the release of Ubuntu 11.04 Natty Narwhal.   The long-term goal is to have -lowlatency in the official Ubuntu  repositories, while maintaining -realtime in a dedicated PPA

[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

---

### Post by gigamico on 2011-07-29
I know that, but I need to install a real time kernel for an university project...

---

### Post by gigamico on 2011-07-29
Anyway, maybe I've found how to install linux rt, but it seems that I don't have enough free space on my ubuntu partition...    I was thinking to delete my old windows xp partition, but before deleting this partition I prefer to ask to you.    My hdd has 3 different ntfs partitions, the first with windows xp, the central which is for storing data and the last one with windows 7 installed.    To install ubuntu I've created a new ext partition of about 4gb from the windows xp partition, since 4gb was the maximum free space available in that partition.    Now, since 4gb are not enough, what I want to do is deleting the whole win xp partition and reinstall again ubuntu in a new partition which includes the space freed by the windows xp partion plus the previous ubuntu partition, so I would have a total of 25GB.    Do you think it is a safe what I intend to do? I would not have problems to boot windows 7.

---

### Post by jerrrys on 2011-07-29
you will create a headache for yourself.  this will mess with your boot.  maybe you be better off just resizing your partitions. either way you go, be sure to have your important files backed up.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

EDIT:  there are a lot of people that believe that windows should be partition only with a windows partition manager.  myself if find this especially true with vista. xp does not seem to have a problem with gparted.  just something to keep in mind

---

### Post by gigamico on 2011-07-30
Made it,
I used paragon partition manager to extend the linux partition over the win xp partition. 

I had to reinstall ubuntu because it didn't boot, probably because I've changed the initial partition point, but once reinstalled it's all fine.  

However linux-rt does not start, I've followed step by step  the guide I've found, but since this guide is for ubuntu 7.10, I'll try to install this older version.

---

### Post by gigamico on 2011-07-30
I've trouble installing ubuntu 7.10 ](*,)

firt of all, when I click on the 'install ubuntu' icon it starts the installation procedure, but when I have to select the partition it shows a blank window... 

I hope I didn't mess up with the partition, but for windows it's all ok, and for ubuntu 11 too
they see all the partitions...

---

### Post by dino99 on 2011-07-30
my way to install it:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

if you can wait a few weeks, next 3.1 kernel will have a -rt version

---

### Post by gigamico on 2011-07-31
@Dino: the problem with ubuntu 7 is that it does not recognize the SATA drives.

This is the guide I have been following:
[http://www.mate.tue.nl/mate/pdfs/10018.pdf](http://www.mate.tue.nl/mate/pdfs/10018.pdf)

Go to the section: Installing a real-time kernel > Manually

If you could take a look at it maybe you can understand why it does not work with ubuntu 11

---

### Post by bluesscream on 2011-07-31
> **jerrrys said:**
> The -preempt and -rt kernels are no longer being developed due to lack  of support.  
[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

have a look at this :D
[http://www.spinics.net/lists/linux-rt-users/msg06759.html](http://www.spinics.net/lists/linux-rt-users/msg06759.html)

---

### Post by bluesscream on 2011-07-31
There is no need to downgrade by installing an obsolete ubuntu version.
There are many howtos around to compile a realtime-kernel yourself, it's quite easy. Or just google for some  debian or ubuntu configured rt-kernel-deb. You can install it with gdebi parallel to your default kernel and select it in grub's bootscreen.
and these 2.6.31 to .33 rt kernels in the ppas should work in all recent ubuntu versions too

---

### Post by gigamico on 2011-08-04
> **bluesscream said:**
> There is no need to downgrade by installing an obsolete ubuntu version.
There are many howtos around to compile a realtime-kernel yourself, it's quite easy. Or just google for some  debian or ubuntu configured rt-kernel-deb. You can install it with gdebi parallel to your default kernel and select it in grub's bootscreen.
and these 2.6.31 to .33 rt kernels in the ppas should work in all recent ubuntu versions too
thanks, :p
but I have no experience in linux so if you could be more precise on what I have to do you could save me a lot of time.

Anyway, now I have installed ubuntu 10.04, because I'm trying to install RTAI, which is similar to linux-rt.

When I extract the rtai-3.8.tar.bz2 file it gives me a raed-only directory 'rtai-3.8'
[http://imageshack.us/photo/my-images/685/screenshoteki.png/](http://imageshack.us/photo/my-images/685/screenshoteki.png/)

but when I try to patch the linux kernel it says it can't find the directory...
what I can do?

---

### Post by jerrrys on 2011-08-04
> **bluesscream said:**
> have a look at this :D
[http://www.spinics.net/lists/linux-rt-users/msg06759.html](http://www.spinics.net/lists/linux-rt-users/msg06759.html)

thanks bluesscream

an email has been sent to the wiki maintainer

---

### Post by gigamico on 2011-08-04
I think I have made it! :)

practically I just downloaded the linux-rt package from here:
[http://old-releases.ubuntu.com/ubuntu/pool/multiverse/l/linux-meta-rt/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/l/linux-meta-rt/)

then I installed it by typing
sudo dpkg -i linux-rt_2.6.31.9.10_i386.deb

but it gived me some dependences errors, so I opened the synaptic manager and fixed the broken package from there.
it has automatically downloaded all the necessary packet, and, after I rebooted, linux-rt was displayed as an option. ^^

---

### Post by gigamico on 2011-08-04
Now I need help for starting to write real time applications...

---

### Post by gigamico on 2011-08-05
I am passed to linux rtai.

I am trying to compile this simple code
```
#include <linux/kernel.h>
#include <linux/module.h>
MODULE_LICENSE("GPL");
int init_module(void) //entry point
{
printk("Hello world!\n"); // printk = scrive in /var/log/messages
return 0;
}
void cleanup_module(void)//exit point
{
printk("Goodbye world!\n");
return;
}
```

it also gives me this makefile
```
EXTRA_CFLAGS += -I/usr/realtime/include -D_IN_RTAI_
obj-m += prog1.o
all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

What I have understood is that I have to compile the hello world file as an object, but I don't know how to use the makefile.

Could someone show me how to do?

---

### Post by bluesscream on 2011-08-05
@gigamico: 

[https://rt.wiki.kernel.org/index.php/HOWTO:_Build_an_RT-application](https://rt.wiki.kernel.org/index.php/HOWTO:_Build_an_RT-application)

this might help, but - hell - I'm no coder ;)

I come from linux audio, there is realtime respectively lowest possible latency functionality a pragmatic request.

For more information about linux realtime google the linux audio or d(igital)a(udio)w(workstation) scene or Thomas Gleixner and his Workgroup who are developing this kernel branch.
I'm sorry that I can't save your time, but I think for enhancement of your programer competency every second of these recherches will be well invested.

---

### Post by gigamico on 2011-08-27
double..

---

### Post by gigamico on 2011-08-27
Hi everyone,
from these 3 weeks I have made a lot of progress, now I have almost all the necessary tools to start to write my real time code, but I moved on RTAI which I found (relatively) easier.

Now I would need that you tell me how to make a script that automatically load these kernel modules instead of doing it manually every time I boot my PC:
```
$ cd /usr/realtime/modules/
$ sudo insmod rtai_hal.ko
$ sudo insmod rtai_sched.ko
$ sudo insmod rtai_shm.ko
$ sudo insmod rtai_math.ko

```I think that it is possibile, like the batch scripts in windows, but I don't know how to do on Linux.
Could you explain me how to do?
Thanks

---

### Post by pastored on 2011-09-14
> Now I would need that you tell me how to make a script that automatically load these kernel modules instead of doing it manually every time I boot my PC...

If you insist on using a script (like a Windows/DOS batch file), you'll use bash scripting. LOTS of tutorials on how to write those as you learn linux.

There's already a special script that's run every time you logon, called rc.local. In ubuntu, you'll find it in /etc. You've already written most of the commands you need, so you just need to put

```

cd /usr/realtime/modules/
sudo insmod rtai_hal.ko
sudo insmod rtai_sched.ko
sudo insmod rtai_shm.ko
sudo insmod rtai_math.ko
```

into your rc.local script.

<sudo gedit/whatever-your-favorite-editor /etc/rc.local> and paste the code you've already written into rc.local.

(That's the LONG way around. You can also just add the list of each module into /etc/modules, and they'll automatically be loaded... but even though that's a better solution than what you asked, it's not technically the answer to the question. So, I've given you both. Good luck!)

---

