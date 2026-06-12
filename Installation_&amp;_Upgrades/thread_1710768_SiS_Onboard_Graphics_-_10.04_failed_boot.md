---
title: "SiS Onboard Graphics - 10.04 failed boot"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by brendanpiater on 2011-03-20
Hi All,

I got an issue trying to upgrade a machine from 8.04 > 10.04. It's running 100% fine with 8.04.

The machine has onboard video and a nVidia AGP card. It should default to the AGP card which works fine under 8.04, but I believe with 10.04 there seems to be an issue with the SiS onboard card messing things up.

Using the LiveCD, I'm unable to get to the install environment. The machine goes through the boot process and hangs after the following error message:

"acer-wmi: no or unsupported WMI interface, unable to load"

Any suggestions how to work around this?

Short of replacing the whole motherboard, I'm stumped after 6 hours...

Cheers
Brendan

---

### Post by JRV on 2011-03-20
Can you disable the SIS graphics in the BIOS?

I followed these instructions to get rid of a problem with SIS graphics a while back.
I booted with a Puppy live CD to make the edit.

Edit this file: /etc/x11/xorg.conf

If the file does not exist copy this:
```

   Section "Device"
     Identifier    "Configured Video Device"
   EndSection

   Section "Monitor"
     Identifier    "Configured Monitor"
   EndSection

   Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
   EndSection

```

Now copy this line:
```

 Driver "vesa"

```
After the Identifier line in the Device section.

Make a backup of the file before editing in case this doesn't work.

Hope this helps.

---

### Post by brendanpiater on 2011-03-20
Thanks for the reply.

Unfortunately the BIOS does not have option to disable the onboard vga chip or choose a default.

I'm keen to test a fresh install on a separate partition before migrating the user. So my end goal is to install via the Ubuntu 10.04 LiveCD and if successfuly upgrade from 8.04 > 10.04 via the normal method. 

However, using VESA like you suggested would mean scaled down resolution and no 3D acceleration for the user, a deal breaker.

Any other thoughts on how to get the LiveCD to run, and I guess the final install?

Cheers
Brendan

---

### Post by davidmohammed on 2011-03-20
if you can install using vesa, then I would  blacklist your SIS graphics kernel module and you should be able to boot using your nvidia card

use instructions [here]("http://wiki.debian.org/KernelModuleBlacklisting") to describe how to blacklist kernel modules

find your sis kernel module by typing

sudo lshw -class display

in the "configuration" part of the output should be the kernel module your SIS graphics is loading.

---

### Post by brendanpiater on 2011-03-22
Just a quick note to say thanks for the suggestion. Will be trying that this evening.

---

### Post by brendanpiater on 2011-03-26
Hi All,

Just a short note to say thank you for your help. 

Unfortunately I was unable to get this machine to boot with newer kernels with various distributions.

So abandoned the machine to it's propriety chip hell. A word of warning, stay away from SiS hardware.

Cheers
Brendan

---

### Post by SteveZsuzska on 2011-06-29
Does your onboard graphics use shared memory? I had a problem after upgrading to 10.04 where I would get to the login screen but no further. After a while it would just come back to the login screen. After some searching I found a post saying that this problem could be resolved by going into the BIOS and increasing the amount of video memory to 64MB and this worked for me. Previously it was 32MB.

---

### Post by brendanpiater on 2011-07-05
Thanks for the reply, but I've sent that machine to the tip a long while ago where all SiS hardware belongs! ;)

---

