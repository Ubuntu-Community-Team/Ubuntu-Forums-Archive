---
title: "Kernel 2.6 question"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by el000 on 2005-04-14
Hi,
I have tried to install Ubuntu Warty and, after the first part of the installation completed, the following message was continuously repeated on screen making it unable to proceed with the post-install configuration:

syslog.err klogd:hub 1-0:1.0: over-current change on port 2

I had the same problem with Mepis with kernel 2.6, but if I choose kernel 2.4, there is no such problem. I was wondering if the problem exists with Ubuntu Hoary and if there is a way to choose kernel 2.4 during installation.
My computer is an old Compaq laptop (Armada 100s).
Processor:AMD K6-III, 533MHZ
128MB RAM  

Thanks!

---

### Post by az on 2005-04-14
[QUOTE=el000]Hi,
I have tried to install Ubuntu Warty and, after the first part of the installation completed, the following message was continuously repeated on screen making it unable to proceed with the post-install configuration:

syslog.err klogd:hub 1-0:1.0: over-current change on port 2

I had the same problem with Mepis with kernel 2.6, but if I choose kernel 2.4, there is no such problem. I was wondering if the problem exists with Ubuntu Hoary and if there is a way to choose kernel 2.4 during installation.
My computer is an old Compaq laptop (Armada 100s).
Processor:AMD K6-III, 533MHZ
128MB RAM  

Thanks![/QUOTE]

You have some usb devices plugged in?  In sounds like a hardware problem (over-current, Yikes!)

Try unplugging it.  I would think the 2.6 kernel is more advanced at deteting these problems than the 2.4 kernel.

Lemme know...

---

### Post by el000 on 2005-04-14
Thanks for your reply
No, there was no usb device plugged in.
Sometime ago I found a post with the same issue (I think it was a bug report; I can't find it anymore). The solution proposed was to follow these steps after the 1st part of the installation:

boot with
init=/bin/bash
and execute the following commands
mount -n -o remount,rw /
echo alias uhci-hcd off > /etc/modprobe.d/local-disable-uhci
sync
reboot -f

If I try this, will I be able to use the usb port or will it be disabled?
Can I choose kernel 2.4 during installation?

Thanks

---

### Post by jsien on 2005-04-14
HI

I have the same h/w and same problem. I also hava nothing plug in (eg. USB, PCMCIA, etc) 

HOw do I use those commands you mentioned? Is it thru GRUB when reboot first time?

TKs
j

---

### Post by el000 on 2005-04-15
[QUOTE=jsien]HI

I have the same h/w and same problem. I also hava nothing plug in (eg. USB, PCMCIA, etc) 

HOw do I use those commands you mentioned? Is it thru GRUB when reboot first time?

TKs
j[/QUOTE]
 As far as I understand you type the first command through GRUB and then you get access to a command line, where yout type the rest of the commands.
But I haven't tried it yet.
If it works would you let me know?

---

### Post by jsien on 2005-04-18
I can't get these commands to work,,,,

I found another link in this forum re same issue saying you can actually ignore those over-current messages, it works just take an hour to finish and at the end you will see a logon screen

---

### Post by jsien on 2005-04-20
Oops,,, I think the commands do work somehow. :---)  I just need to append rw init=/bin/bash to the kernel line, reboot and gain command line and from there execute the other command to disable the  uhci (note I didn't use the mount command guessing it only kicks in the rw)

---

### Post by el000 on 2005-04-27
I have managed to install hoary. However,  didn't use these commands because I don't want to disable my usb port. 
Unlike warty, in hoary no input is needed during the second part of the installation, so, yes, you can ignore the over-current messages. Eventually, you will get  to the gdm login. I think it took about one hour for the whole installation to finish (both steps), but that's the usual time it takes for me (slow pc). 
Everything works fine. The only problem is that if you change to a terminal screen ( I mean doing ctrl+alt+F1) you will get the over-current message again. This makes it difficult to use these terminals because you can't see your input. But, I can live with that.

---

