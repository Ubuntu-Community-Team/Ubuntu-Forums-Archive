---
title: "problems with new install"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by wfk on 2012-03-07
I have 2 problems:
1 - Ijust installed ubuntu 11.10 on a laptop from an USB stick.
The system starts up ok but I can not see my main "C" drive. The system shows only the USB stick.

How can I make the "C" drive visible?

2 - I want to transfer the ubuntu install from the USB stick to the main drive and kick the windows environment out.

How can I do this?

Thanks - wfk

---

### Post by grahammechanical on 2012-03-07
You are confusing me.

If you have done this

>  installed ubuntu 11.10 on a laptop from an USB stick.

Then you have already installed from the USB drive to the main drive.

Open the file manager and you will see in the left hand panel the heading Devices. Your C: drive is there but it is called File system and it will have the same size as your Windows drive.

We do things differently in Linux. We do not call anything C: or D: etc. They are called partitions. And if a partition is formatted it is called a file system.

Check this link and scroll down to Install It - and click Show Me How.

[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

Regards.

---

### Post by wfk on 2012-03-07
Thanks for the reply.

I do see devices and I see USB, CD and floppy, that's it. I just downloaded VLC player, the system put it on the USB stick. I do file search for doc files on the windows device / partition - nothing is returned. Perhaps, I should reinstall directly to the windows drive / device.

I am completely new with the linux world :confused: sorry for the stupid questions ....:(

---

### Post by wfk on 2012-03-07
I installed ubuntu on the USB stick, it is running of the stick.

---

### Post by bogan on 2012-03-08
Hi!, **wfk**,

What happens if you boot your laptop with the USB removed.?

If the Bios is set to boot from USB by default first priority, it will not boot to your Ubuntu installation as long as the USB is plugged in.

Does Windows still boot?

Do you get a Menu titled Grub?

OR is it one with the choices to try Ubuntu or to Install it?

EDIT: If you are running from Ubuntu on the USB the Windows partitions will not be found in 'Search' until they are mounted, which they will be if you Click on them in the file manager Window.

Chao!** bogan.**

---

