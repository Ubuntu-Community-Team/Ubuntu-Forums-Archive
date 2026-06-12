---
title: "xorg-nvidia conflict after update, simple solution please"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by whatrucrazy on 2006-11-23
so after updating the other day i find that x will not start at all. great.
i'm running dapper 6.06
according to the terminal it's due to a conflict between the versions of the nvidia driver and the xserver version.
now the problem is that almost all of the responses on the site are for edgy, or say to do different things - some of which i tried and seemed not to work (like downgrading my version of nvidia glx driver to 1.0.8762

my stopgap solution was to edit xorg.conf to boot to the nv driver, but i'm not sure i'd like this to stay that way, so...

can anyone provide a clear and simple solution to this upgrade issue, for myself and others. hopefully one that is universal for each release. 

thanks very much!!

---

### Post by Jimmey on 2006-11-23
You might want to check that you've got the right drivers installed.

I found that my card under Dapper worked with the nvidia-glx-legacy drivers installed. When I updated to Edgy, it worked under the plain nvidia-glx. If your card is getting a bit old, it wouldn't harm to try the legacy drivers.

---

### Post by MJN on 2006-11-23
Check out Alberto's guide for installing Nvidia drivers - he's the proverbial 'daddy' when it comes to this.

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

Mathew

---

### Post by whatrucrazy on 2006-12-03
OK, so i guess i wasn't that clear about the issue.

it seems that the problem is with a recently released upgrade, i'm assuming to the nvidia driver. the problem seems to be (according to the terminal error message):

 a mismatch between the nvidia kernel module version (1.0-8776)
and the X module version(1.0-8762)

ie - the nvidia kernel 8776 is later than the x module 8762.

so considering that everything worked fine on my box until i used the updater, i'm thinking that its the nvidia driver. Now i have downgraded my nvidia driver to version 1.0-8762 (sudo apt-get install nvidia-glx=1.0.8762+2.6.15.11-1), but my system is still not working and i have had to keep the xorg.conf configured to rung the nv driver.

so what's the go? it would seem weird that this update is a small scale issue if i'm right... 

will there be a new x server version released? or does this perhaps have something to do with the fact that i'm using the k7 kernel, or running dapper?

just to be sure my specs are:

amd XP2000, 1.75GHz
512MB RAM
Nvidia GForce 4 MX 420
Dapper, K7 Kernel
using both gnome and KDE 

please help, no open GL means no cube. can't live without a bit of FPS!!!

---

### Post by Jimmey on 2006-12-04
Make sure the right kernel modules are installed. Do this by:
> sudo apt-get install linux-restricted-modules-$(uname -r)
Then
> sudo apt-get update; sudo apt-get upgrade
Then
> sudo apt-get --purge remove nvidia-glx; sudo apt-get install nvidia-glx

Try that?

---

### Post by mattyj on 2006-12-09
I have the same problem, did you find a solution?

---

### Post by whatrucrazy on 2006-12-11
ok: so the solution i have found that works (for me) is to downgrade the kernel i'm running to 

2.6.15-26-386

and all the related drivers and modules too.

so for me this involved:
1- editing /etc/X11/xorg.conf and changing the line stating which driver to load back to nvidia (from 'nv', which had been the workaround)

2- booting to the old kernel from grub (2.6.15-26-386), and making sure that it all runs fine, as the kernel after this 2.6.15-27-386 did not run fine, nor did the k7 which was what i was using.

3- now i'm not sure if these steps are necessary, but it worked for me. use synaptic to remove the kernels/headers that were on the system newer than the one i wanted to boot from permanently. this effectively removed them from grub and reset everything to the kernel i wanted. perhaps there is a better way, but i don't know.

4- reinstall the restricted modules for that kernel:

sudo apt-get install linux-restricted-modules-$(uname -r)

5- install the nvidia-glx drivers:

sudo apt-get install nvidia-glx 

and done.


if this install process doesn't work, try the one discussed a few entries earlier, and run the update or purge. if it still doen't work, go back and edit you xorg back to 'nv' and wait a bit for a better soultion...

given all of this though, i'm not going to be upgrading my kernel or x-server for a while!

good luck

---

