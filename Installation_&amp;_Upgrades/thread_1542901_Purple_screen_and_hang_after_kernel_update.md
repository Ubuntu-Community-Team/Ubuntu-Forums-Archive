---
title: "Purple screen and hang after kernel update"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by faflu on 2010-07-31
Hi,

After updating kernel from linux-image-2.6.32-23-generic to linux-image-2.6.32-24-generic, system freezes on boot at purple screen. No mouse cursor available, keyboard unresponsive - only power off. Is it another braking release from Ubuntu or my bad luck? I'm using nvidia and rt73usb modules (to name only those non-typical). I would be glad to provide any information needed to help in resolution of my problem.

---

### Post by dino99 on 2010-07-31
boot by removing splash on boot line: hold "shift" key down at end of bios process if grub menu is hidden

which graphic driver is used ?

---

### Post by tommcd on 2010-07-31
> **faflu said:**
>  I'm using nvidia ...
To say that "*I'm using nvidia*" is a bit vague.

Did you install the nvidia driver from the Ubuntu repositories?
 Or did you install the nvidia driver from nvidia.com?
If you used the driver from nvidia.com, you should know that you need to reinstall the driver whenever there is a kernel update for Ubuntu.

---

### Post by faflu on 2010-08-09
I must admit that I've made this post too quickly. I thought that it's a persisting issue, but the following reboots proved to be successful. Not all of them though. Just sometimes (I hate this word in IT) booting freezes at the point of purple screen. I have checked memory (memtest) and it's ok. I guess it might be related to some disk issues - I will run fsck on them and report back. I also noticed that the system powers off by itself! It never occurred when I was doing anything on the computer but after a long inactivity (a few hours). Any suggestions here?
Regarding nvidia driver - it comes from ubuntu's repository.

---

### Post by tommcd on 2010-08-10
> **faflu said:**
> 
After updating kernel from linux-image-2.6.32-23-generic to linux-image-2.6.32-24-generic, system freezes on boot at purple screen. No mouse cursor available, keyboard unresponsive - only power off.
So when you were using the 2.6.32-23 kernel everything was OK; and this problem started after upgrading to 2.6.32-24? Is that correct??
If so, then try booting the 2.6.32-23 kernel then and see if the problem goes away. It should still be there in the grub menu. (You should always have at least 1 known working kernel to use as a backup in case something like this happens.)
If the problem persists when using 2.6.32-23 kernel, then obviously something else is wrong.
If the problem persists with 2.6.32-23 kernel, try running the live CD for a while and see if the problem develops with the live CD.
> **faflu said:**
> 
I have checked memory (memtest) and it's ok.
How long did you run memtest? You should run it for at least a couple of hours. Some people say you should run memtest overnight before concluding that memory is ok.
> **faflu said:**
> 
I also noticed that the system powers off by itself!
Have you checked your system temps? Have you cleaned the dust out of your system recently? 
You should rule out a hardware problem here.
 Also check the log messages:
/var/log/syslog
/var/log/messages
Is this a desktop or laptop? What are your system specs?? lspci??

---

