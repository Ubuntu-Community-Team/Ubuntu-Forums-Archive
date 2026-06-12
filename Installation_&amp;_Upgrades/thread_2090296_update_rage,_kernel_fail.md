---
title: "update rage, kernel fail"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by Forbees on 2012-12-01
new round of updates, froze on the install of the new kernel  about 75% through


reboot to a purple screen

tried using boot-repair, told it to purge and install the new kernel - still boot to purple


am i missing something or do i need to start new?


Ubuntu 12.04LTS x64

---

### Post by 2F4U on 2012-12-02
Do you still have older kernel versions available? If yes, you can try to boot into an older kernel:

[http://askubuntu.com/questions/118581/how-do-i-boot-into-an-older-kernel](http://askubuntu.com/questions/118581/how-do-i-boot-into-an-older-kernel)
[http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

---

### Post by Forbees on 2012-12-02
i tried booting to an older kernel, and same thing

now that i used boot-repair to purge and reinstall the kernel, i only have the option for the new one

---

### Post by YannBuntu on 2012-12-02
Hello

> **Forbees said:**
> new round of updates, froze on the install of the new kernel  about 75% through

if i were you, i would use an Ubuntu disk this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
(don't enable the updates during it, so it will reinstall the disk's old kernel)

---

### Post by Forbees on 2012-12-04
thanks

i didn't get the option to do the update and keep my home folder like it shows. but all will be fine. everything important on here is saved to a softRAID-5


reinstalling now, i just need to make sure that i don't mess up rebuilding the RAID :-p

i'm going to attempt to get the new kernel update going before i make any progress at bringing my system back to how i like it. i'd hate to to repeat the same problem.

worst case scenerio i just have to do this again in about an hour.

---

### Post by Forbees on 2012-12-04
yup. the kernel just doesn't work with my system. 

did a reinstall and after the kernel update got the same problem. only this time when i told grub to boot into the older kernel it worked :) so i edited grub to auto boot in the old kernel


now new problem. can't get my raid back up :-/

this problem is solved -  on to my new one

[http://ubuntuforums.org/showthread.php?p=12388562#post12388562](http://ubuntuforums.org/showthread.php?p=12388562#post12388562)

---

### Post by YannBuntu on 2012-12-05
Hello

> **Forbees said:**
> yup. the kernel just doesn't work with my system. 

did a reinstall and after the kernel update got the same problem. only this time when i told grub to boot into the older kernel it worked :) so i edited grub to auto boot in the old kernel

I highly recommend you:
1) test the very last kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/)
2) if the 3.7-rc8 kernel fails too, create a bug report on Launchpad.net (via the 'ubuntu-bug linux' command)

If you don't, you won't be able to use next Ubuntu releases.

---

### Post by Forbees on 2012-12-05
being that i'm running 64bit i want 

linux-image-3.7.0-030700rc8-generic_3.7.0-030700rc8.201212031649_amd64.deb

?

---

### Post by YannBuntu on 2012-12-05
you need :
the _all.deb
and the 3 amd64.deb
packages

---

### Post by lisboa on 2012-12-09
> **Forbees said:**
> yup. the kernel just doesn't work with my system. 

did a reinstall and after the kernel update got the same problem. only this time when i told grub to boot into the older kernel it worked :) so i edited grub to auto boot in the old kernel


now new problem. can't get my raid back up :-/

this problem is solved -  on to my new one

[http://ubuntuforums.org/showthread.php?p=12388562#post12388562](http://ubuntuforums.org/showthread.php?p=12388562#post12388562)

Hello, Forbees! :)

My laptop has the same problem as yours, I deleted the Kernel 3.5.0-19 but I don't know how to edit grub to auto boot in the old kernel.

I have already tried the Grub Customizer 3.0.2. There is no boot options in the folder "Advanced Options for Ubuntu" and I need some suggestions.

Appreciate your help!:)

---

### Post by lisboa on 2012-12-09
> **YannBuntu said:**
> Hello



I highly recommend you:
1) test the very last kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/)
2) if the 3.7-rc8 kernel fails too, create a bug report on Launchpad.net (via the 'ubuntu-bug linux' command)

If you don't, you won't be able to use next Ubuntu releases.

Hello!:P

My laptop is Toshiba Satellite L755D with CPU:AMD A6-3420M and Graphs: ATI Radeon 6520 HD. It has the same purple screen problem as Forbees's when it is running Ubuntu 12.10 Desktop and the kernel is 3.5.0-19.

I'll test the last kernel, too.

If it doesn't work, I'll report the bug and post it here.:(

---

### Post by Forbees on 2012-12-09
let me know if it works for you, i'm currently fighting a raid battle so i'm not quite ready yet to start testing this


but if it works for you i might not put it on the back burner

---

### Post by Forbees on 2012-12-11
> **lisboa said:**
> Hello, Forbees! :)

My laptop has the same problem as yours, I deleted the Kernel 3.5.0-19 but I don't know how to edit grub to auto boot in the old kernel.

I have already tried the Grub Customizer 3.0.2. There is no boot options in the folder "Advanced Options for Ubuntu" and I need some suggestions.

Appreciate your help!:)




sorry i missed your post!
[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Grub Customizer is what i used also - the above link had a helpful thread

essentially in the "General Settings" tab i just selected the kernel. for me it was "entry 3>1(by postition)" when you select the entry it should tell you what kernel

if for some reason that doesn't work try booting into the old kernel and under the same tab in grub customizer select "previously booted entry"

hopefully it works for you

---

