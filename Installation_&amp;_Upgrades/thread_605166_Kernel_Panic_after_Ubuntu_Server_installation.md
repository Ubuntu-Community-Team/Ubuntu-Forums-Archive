---
title: "Kernel Panic after Ubuntu Server installation"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by anwar007 on 2007-11-06
I tried to install ubuntu server distro on a parallels virtual machine and it completed successfully.  But, after restart, it displayed: 

       **Kernel panic:  CPU too old for this kernel.**

I don't think it is reporting right because the rig where i'm installing has the following:
      AMD Athlon 64x2 4000+ (Dual Core 2.1 GHz)
      1 GB DDR2 memory
      ATI Radeon HD2600 Pro video card

I just don't know which have a bug here, ubuntu or paralells. Nevertheless, I hope somebody could provide me some work around link or instructions.

---

### Post by lyneux on 2007-11-07
Hi,

I just had the same problem installing ubuntu server 7.10 using parallels on my MacBook. I'm going to retry the installation using OS Version = 'Other Linux kernel 2.6' as some reports on other forums seemed to suggest this would solve the problem.

Lyneux

---

### Post by frippz on 2007-11-07
Just an FYI: I used Other Linux kernel 2.6 and got the same error (I actually found this thread while looking for a solution :D).

edit: I saw a solution for 7.04 that involved installing a vanilla kernel (if I remember correctly) right before rebooting from the install. Will be looking into it.

---

### Post by night0wl on 2007-11-08
> **frippz said:**
> Just an FYI: I used Other Linux kernel 2.6 and got the same error (I actually found this thread while looking for a solution :D).

edit: I saw a solution for 7.04 that involved installing a vanilla kernel (if I remember correctly) right before rebooting from the install. Will be looking into it.


Get the same error...were you able to figure something out?  I cant even figure out how to get to the bios in parallel's to change the boot order to go to the cd and enter rescue mode.

---

### Post by night0wl on 2007-11-08
Figured this out!  

First - boot order in Parallels is easy....user error on my part not knowing this:

In the "General" tab of VM options in Parallels, select Boot Order to be CD first

Start up the VM and boot off the server cd.  Select Rescue...and follow general directions here:

[http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/](http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/)

Good luck!

---

### Post by frippz on 2007-11-09
> **night0wl said:**
> Get the same error...were you able to figure something out?  I cant even figure out how to get to the bios in parallel's to change the boot order to go to the cd and enter rescue mode.

Sorry for being slow to reply. What you need to do is replace the server kernel with a vanilla one, just like I mentioned. [_These instructions_](http://paul.annesley.cc/articles/2007/05/01/ubuntu-704-feisty-server-parallels-cdromkernel-workaround) are for Feisty (7.04), but works for Gutsy (7.10) as well, with a few modifications.

For example, I never changed the OS type to "Solaris", I stuck with "Other Linux kernel 2.6" without any problems. Do not follow the instructions blindly. The version of the kernel is not the same in Gutsy, so be flexible there (this goes for the removal of the server kernel). Check what version you've got installed (can't remember which one right now).

Good luck!

[i]Pasting the URL again in plain text for good measure:
[http://paul.annesley.cc/articles/2007/05/01/ubuntu-704-feisty-server-parallels-cdromkernel-workaround](http://paul.annesley.cc/articles/2007/05/01/ubuntu-704-feisty-server-parallels-cdromkernel-workaround)[/i]

edit: Must be too early in the morning for me. I didn't see that you had replied to your own thread. However, the link I provided might prove useful to someone else. :D

Don't forget to mark the topic as resolved. ;)

---

### Post by RikardSvenningsen on 2007-11-30
As suggested. 
This did the trick for me

[http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/](http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/)

---

