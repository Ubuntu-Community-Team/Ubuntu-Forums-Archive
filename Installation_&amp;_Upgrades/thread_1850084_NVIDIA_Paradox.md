---
title: "NVIDIA Paradox"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by xtjacob on 2011-09-25
I recently saw that kernel version 3.0 has come out so I decided to compile it. Everything works, and now I want to install the accelerated graphics driver for my video card. However when I try to install the driver it tells me that I cannot install the driver because nouveau is active. So I decided to put it in blacklist. Now when I boot up all I get is a black screen, and the only way I can see anything is to remove nouveau from the blacklist. Is there anyway I can install this driver? My graphics card is an NVIDIA GEforce 9100M G.

---

### Post by MG&amp;TL on 2011-09-25
Could you compile the kernel without the 3d support? Then you could manage with (Vesa?) graphics until you install the nvidia ones.

I followed this guide as a I-can-do-this, but it might work in your case. Be sure you've backed up everything though.

[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

But there's various problems with custom kernels, mostly from human error. Be CAREFUL. I hope this is a test machine/partition.

---

### Post by MAFoElffen on 2011-09-25
> **xtjacob said:**
> I recently saw that kernel version 3.0 has come out so I decided to compile it. Everything works, and now I want to install the accelerated graphics driver for my video card. However when I try to install the driver it tells me that I cannot install the driver because nouveau is active. So I decided to put it in blacklist. Now when I boot up all I get is a black screen, and the only way I can see anything is to remove nouveau from the blacklist. Is there anyway I can install this driver? My graphics card is an NVIDIA GEforce 9100M G.
refer to this post...
  			#[**306**]("http://ubuntuforums.org/showpost.php?p=10924650&postcount=306")

Hope those instructions help.

---

### Post by xtjacob on 2011-09-25
I'll give that a try soon. Also where can I find nouveau when I'm compiling the kernel to disable it? I looked under device drives->graphics, but I couldn't find it...

---

### Post by MG&amp;TL on 2011-09-25
I dunno. You could join the Linux Kernel Mailing List,and ask there, but I'm told that it will cause your inbox to explode and that the social skills exhibited aren't the best. Tell me if it's fun in there. :)

---

### Post by xtjacob on 2011-09-25
Haha, how do you sign up?

---

### Post by MAFoElffen on 2011-09-25
> **xtjacob said:**
> I'll give that a try soon. Also where can I find nouveau when I'm compiling the kernel to disable it? I looked under device drives->graphics, but I couldn't find it...
I guess a little explanation might help... You compiled kernel 3.0.x.  As you can surmise, the linux kernel numbering schema has changed.  Packages that require binaries or source to be compiled look at the linux kernel numbering schema to ensure they are being compiled for a certain linux kernel version (therefore the numbering schema check.) Previous checks were for kernels previous to 2.4, 2.4 to previous to 2.6 and then 2.6.  Linux kernel 3.0 is essentially kernel 2.6 with a different "name." An administrative thing with eyes at the future.

So current packages (like up to and including those for 11.04) will error out when it see's "3.0" in version, until you add the approved fix from kernel.org that the instructions in the first part of that post explains.  (If you don't, your build log will reveal an error saying that the current kernel is is being compiled under is invalid or not supported.) Ubuntu 11.10 already includes this fix, as it is being released with that kernel version.

This affects "more" packages and binary installs than just nvidia drivers... when you are running linux kernel 3.0.x with Natty or earlier.

You could use nouveau just by changing the driver in xorg.conf to nouveau and adding a nomodeset in the kernel bootline-- or just ensure thre is no xorg.conf and use a nomodeset in your kernel boot line.  Those would get you graphics until you work things out.  Anther would be to use the Ubuntu opensource Nouveau Experimental 3D Driver for NVidia which works with kernel 3.0.  That driver is in the Meerkat, Natty and Oneiric repo's.

---

### Post by xtjacob on 2011-09-25
Well it's not really a naming problem right now. I can't get to any command line or anything when I try to boot up the computer, because as it seems 3.0 requires nouveau to be used else all I get is a black screen. However, will the problem be solved if DKMS doesn't fail when I'm install the kernel?

---

### Post by MAFoElffen on 2011-09-25
> **xtjacob said:**
> Well it's not really a naming problem right now. I can't get to any command line or anything when I try to boot up the computer, because as it seems 3.0 requires nouveau to be used else all I get is a black screen. However, will the problem be solved if DKMS doesn't fail when I'm install the kernel?
Yes, the fix adds 3.0 to the range when if looks for the version number.

Can you get to the Grub boot menu?  If you can, edit the linux boot line boot options from "quiet splash" and replace with "verbose text".  That will get you to TTY Text Console were you can edit files from vi(?)  (I have emacs installed, because I've been using that for 25 years...)

Can you boot from rescue mode?  If not in the Grub Menu, the kernel boot option for that would be "rescue".

You could also boot under a previous kernel or from a LiveCD to make your editing changes... :)

---

### Post by xtjacob on 2011-09-25
I got it to work without following that guide you put. I removed the gfx line in grub, took off vga=, quiet, and splash, then replaced it with verbose and text. After it booted up, I ran NVIDIA-xxx.run and it installed the driver. Then I rebooted and it worked! Thanks!

---

