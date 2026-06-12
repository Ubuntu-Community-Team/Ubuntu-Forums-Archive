---
title: "/bin/sh: Cant access tty; job control turned off (a solution)"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2007-05-28
Hi.

Today I upgraded my Ubuntu box from kernel 2.6.20-15-generic to 2.6.20-16-generic.
After reboot my system wouldn't start up and I got this message:

```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Build-in shell (ash)
Enter 'help' for a list of build-in commands.

/bin/sh: Cant access tty; job control turned off 
(initramfs)
```

After searching the forums and the net I found different solutions but it's all a mess and I can see people have spendt hours trying to fix this.

In my case the problem was that all my harddrives are called SD* and not HD*. Apparently all devices (of my type) are now known as HD* in the new kernel (at least that's what I conclude). So i opened up my /etc/fstab file and changed all the mappings from SD* to HD*, and rebooted and now it works.

You can probably use the LIVE CD for this. I came into my system by trying to boot in safe-mode, when what appeared to be an infinte loop occured:

```
ACPI: Unable to turn cooling device [df82739] 'on'
```

It said something about "Lost Interrupt" and "dma_timer_expiray" but kept going.

By turning off the power and rebooting it seemed like the system thought something went wrong and gave me a console, by ending that console (CTRL+D) it just keept booting up my system just without any of my harddrives (one can only guess how it found the system drive device).

Here I simply opened a console and wrote sudo /etc/fstab replaced all the SD* with HD*, saved and rebooted.

---

### Post by pyrforos on 2007-05-28
WORKS!!!!!
 U R THE BEST !!!!! keep up the good job!

---

### Post by pyrforos on 2007-05-28
ehm.. a little problem... I had to recompile the kernel for lirc ,and i  now i get the same error... any ideas?:(

EDIT:

 hah? ok i just cant get it.. after two or three reboots it works fine now... Not lirc but i can boot no problem

---

### Post by tbresson on 2007-05-29
Well.. I guess I spoke to soon. I rebooted and now I get the same errors as before.

My /etc/fstab is still pointing at hd* devices, but it just won't start up.

I've decided to go back to the previous kernel (by editing grub).

I've got ATI and now my harddrives seems to disappear, it's an Ubuntu nightmare. Certainly not something I'd choose as an OS if this was my first try at a Linux distro. This is not the first Ubuntu kernel problem in my Ubuntu days.

---

### Post by pyrforos on 2007-05-30
worked for me....

---

### Post by serlex on 2007-05-31
dont get it, how can I edit /etc/fstab if i can not get passed the error message? (ubuntu isnt installed)

---

### Post by tbresson on 2007-06-02
You can edit it with the Live CD. You can mount your disks in the Live CD and change the fstab file there.

---

### Post by AlanQ on 2008-05-06
It happened to me when trying to install 7.04 (same with 7.10).

Take a look here:
[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)

Step 1 on its own worked for me.

---

