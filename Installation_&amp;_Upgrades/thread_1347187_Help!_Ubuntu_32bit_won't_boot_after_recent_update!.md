---
title: "Help! Ubuntu 32bit won't boot after recent update!"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by motorhed80 on 2009-12-05
I did a recommended update on 32bit Ubuntu, and now it won't load. It says something about bash, and then it goes to a command prompt. I tried re-installing, and it installed fine, but still shows the same error. Please help!

---

### Post by MelDJ on 2009-12-05
can you boot through recovery mode? 
and try typing gnome-desktop and see what it says

---

### Post by motorhed80 on 2009-12-05
It won't even give me the option of recovery mode, Im going to try typing gnome-desktop

---

### Post by motorhed80 on 2009-12-05
typing gnome-desktop did nothing.

This is what it says

GNU Grub v1.97~beta
[Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]



Im very new to ubuntu, had it running for about 2 weeks and absolutely love it, I just want it back!

---

### Post by MelDJ on 2009-12-05
this is a problem with grub. i am no expert in it. but you could try reinstalling grub with [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by byStanderone on 2009-12-05
...just curious, what exactly did u update to?

---

### Post by motorhed80 on 2009-12-05
A window popped up and said, your system needs to be updated so I did, and here we are now.

---

### Post by orkinson on 2009-12-05
im having the same exact problem. did you restart your machine after installing the update? i chose the restart later option and then ended up just shutting my machine down. when i booted up again i ran a double boot (i have windows too) and chose ubuntu but then it gave me the same message (bash etc.) that you got.

!!!!

---

### Post by byStanderone on 2009-12-06
...ok, here's a thread on these update issue:
[http://ubuntuforums.org/showthread.php?t=1267183](http://ubuntuforums.org/showthread.php?t=1267183)

---

### Post by PJOS13 on 2009-12-06
Hey look at here:[http://ubuntuforums.org/showthread.php?p=8442926#post8442926]("http://ubuntuforums.org/showthread.php?p=8442926#post8442926")

I posted the same problem some days ago, here is how to solve part of it, but now I'm trying to solve the grub problem...

---

### Post by oraso on 2009-12-06
I just ran into this problem today. I used Wubi to install Ubuntu 9.10 on my Aspire One netbook a couple of weeks ago and all was fine until the system notified me there was an update required. Seems like the linux kernel was updated to 2.6.31.16 amongst several other things. After restart I could not boot Ubuntu. I got kicked out into grub. When I exit grub I eventually get a message saying something to the effect that there is no boot disk present. I did read a message on the forums indicating that this can be fixed by booting from a USB, but the posting is from 2006, and grub has changed to grub2. Will the earlier fix still work with grub2? 

I was really enjoying Ubuntu on the netbook so I am hoping this is a straightforward fix for this. 

Cheers.

---

### Post by oraso on 2009-12-06
I happen to have another laptop running Ubuntu 9.1 so I looked at the grub.cfg file (/boot/grub/grub.cfg). Since I knew I had a 2.6.31-14 kernel on my Aspire that wouldn't boot, I copied the following once I got to the grub prompt after the failed Ubuntu boot

insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 6d2f-5568
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
    initrd /boot/initrd.img-2.6.31-14-generic
boot

This got me back into Ubuntu. I then edited the grub.cfg on my Aspire to delete all references to the 2.6.31-16 kernel. My Aspire still will not boot into Ubuntu, and I end up at the grub prompt. What do I change to get the 2.6.31-14 kernel to boot at startup? 

I am not a grub, or anything linux, expert. 

Cheers

---

### Post by oraso on 2009-12-06
Just answered my own previous post. I now have my Aspire back to pre 2.6.31-16 update and booting into Ubuntu. I found the answer in a previous post [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
This is a reasonably detailed description of grub2. Just go to section 7 and follow the instructions. Long story short, just use Synaptic package manager to delete the 2.6.31-16 kernel and then reboot.

---

### Post by bobdotexe on 2009-12-06
> **oraso said:**
> Just answered my own previous post. I now have my Aspire back to pre 2.6.31-16 update and booting into Ubuntu. I found the answer in a previous post [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
This is a reasonably detailed description of grub2. Just go to section 7 and follow the instructions. Long story short, just use Synaptic package manager to delete the 2.6.31-16 kernel and then reboot.
How do you do this in Xubutu?

all I have is add/remove Packages..

I got back in my system, but that only after alot of work+reading:

[http://blogoflinuxnoob.blogspot.com/2009/12/wubi-upgrade-of-death-solved.html](http://blogoflinuxnoob.blogspot.com/2009/12/wubi-upgrade-of-death-solved.html)
once I get this working I'll have to update my log with the details...

---

### Post by oraso on 2009-12-06
> **bobdotexe said:**
> How do you do this in Xubutu?

all I have is add/remove Packages..

I got back in my system, but that only after alot of work+reading:

[http://blogoflinuxnoob.blogspot.com/2009/12/wubi-upgrade-of-death-solved.html](http://blogoflinuxnoob.blogspot.com/2009/12/wubi-upgrade-of-death-solved.html)
once I get this working I'll have to update my log with the details...

I am not familiar with Xubuntu, but I assume the package manager will be able to identify the kernel update that caused the problem. Just search for packages that contain 2.6.31-16. Then completely remove all the packages.

---

### Post by bobdotexe on 2009-12-07
ok, so I found the package mangier, and unstalled the kernel, and the latest grub;
but, it still will not boot normaly, (AND YES, i removed all the packages congaing the version number)

it still shows the latest GRUB version at the  next boot, were I am left at a prompt.
maybe I must update my grub menu list file for grub2.... even tough i unstalled it???

---

