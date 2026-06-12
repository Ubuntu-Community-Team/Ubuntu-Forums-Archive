---
title: "Error booting from any Live CD or USB"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by mohamed.ramzy on 2010-10-28
Hello ,
i have laptop Toshiba Satellite A500 with Intel i5 processor and Intel Graphics Media Accelerator HD ,
i am having this problem when booting from any live CD or USB 
when i choose "run from USB or Live CD " or even "install Ubuntu..."
i got large list of error lines (as i think) and after that , no response until i manually switch laptop off.
attached two photos and a small video that i could took as it is very quick .
please help me
thanks

---

### Post by mohamed.ramzy on 2010-10-31
is there any help please ??

---

### Post by oldfred on 2010-10-31
It is usually the last lines that are the problem. You are just seeing the boot process, line by line as it loads drivers and modules.

Often the issue lately has been video. Have you tried f6 on first screen and try some options. 

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

If not the video then you need to capture the last messages to see what is not loading.

---

### Post by mohamed.ramzy on 2010-10-31
> **oldfred said:**
> It is usually the last lines that are the problem. You are just seeing the boot process, line by line as it loads drivers and modules.

Often the issue lately has been video. Have you tried f6 on first screen and try some options. 

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

If not the video then you need to capture the last messages to see what is not loading.
1st , yes i got at first the blank screen problem and  i have tried some options with Ubuntu 9.10 and after i could boot and install it , no drivers were recognized (video , wireless , .. ) except sound . 
2nd , my Intel video driver is not old i think , so do you think this option (i915.modeset) will help as i remember that i tried this but the same problem.

---

### Post by oldfred on 2010-10-31
Did you try the generic drivers also?

Other workarounds, May apply to Maverick also:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

May apply to Maverick also:
Lucid 10.04 KMS advanced settings:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

---

### Post by mohamed.ramzy on 2010-11-01
I could resolve my problem through these steps :
1- using this link [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
and instead of adding one option of the listed ones , i added "apci=off" which enables me to boot through ubuntu .

2- i could install ubuntu 10.10 normally , enabling it to download files while installing .

3- after installation , i faced the same screen when booting again , so i had to update grub file /etc/default/grub  using "sudo gedit /etc/default/grub" 
and added the options i choose above at the line 
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" changing it (in my case) to "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash apci=off"

4- update grub config file using "sudo update-grub".


[]("http://www.*****************/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html")

---

