---
title: "Can't Install Ubuntu!"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Pieman62295 on 2011-06-13
Hey guys. I was wondering if you could help me out here...

I've got a Dell Inspiron 1545 laptop (4 years old, I think.) Running Windows xp 32 bit. I'm trying to dual boot it with ubuntu. I've installed ubuntu on a couple of other computer just fine. This laptop though, has decided it hates linux and I can't get ubuntu to install. I get to the first screen and can boot into ubuntu as a live cd just fine but if I try to install it the screen goes black, a ton of text appears, and then nothing else will happen.

So I tried using a usb stick to install. Same issue. Then I tried downloading mint and could not get past the first screen either. I tried debian, and my computer didn't even boot into the installer, it just booted into Windows...

Help please?

---

### Post by StrayEddy on 2011-06-13
Maybe try something else, like:

- Puppy linux (awesome speed and works out-of-the-box)
- Madbox (i use it on my desktop, works great out-of-the-box)

Maybe your problems are related to your video card, happens a lot

---

### Post by Rubi1200 on 2011-06-13
Hi and welcome to the forums Pieman62295 :)

To help us figure out what might be going on please do the following:

1. post the full specifications for the computer especially RAM and graphics card

2. boot the LiveCD and choose the option to try not install and then run this command:
```
sudo fdisk -lu
```
Post the output here

3. take a screenshot of how GParted sees your drives and partitions and post it here

Thanks.

---

### Post by Pieman62295 on 2011-06-13
Hmm....I don't think my video card or RAM is an issue, as had Ubuntu on it a year ago and it installed fine...

Alright, system specs:


Intel Pentium Dual CPU T3400 @ 2.16GHz processor
3 gig of Ram (DDR2)
32 bit Windows XP Professional w/ Service Pack 3
150 GB hard drive (96 GB free)
Mobile Intel(R) 4 Series Express Chipset video card

I'll get back to you after booting with the Live CD.

EDIT: Oh, look at that. The live CD isn't working at all now.

---

### Post by mastablasta on 2011-06-14
> **Pieman62295 said:**
> Hmm....I don't think my video card or RAM is an issue, as had Ubuntu on it a year ago and it installed fine...
.
 
different ubuntu= different kernel = different graphics card drivers
 
 
you could try to install via alternate CD with text based install.

---

### Post by amberleafguy on 2011-06-14
Hi there have you tried a bios boot by anychance? changing the booting sequence to stop it booting the HDD first? That usually works to force the loading of ubuntu liveCD

If you are using a USB stick which software did you use to load ubuntu on it?

---

### Post by Pieman62295 on 2011-06-14
Yup, I had it set to to look for an os on the usb stick or cd drive first. 

I used LiveUSB Install to put the iso on the pendrive. 

For now I'll take matablasta's idea and try to install via text and see how it turns out. :popcorn:
Thanks for the help guys.

And...it didn't work. hmph.

---

### Post by Pieman62295 on 2011-06-14
Now every time I try to boot ubuntu, it brings me to a busybox prompt and says:

(Initramfs) stdin I/O errormount: mounting /Dev/loop0 on //filesystem.squashfs failed: no such device
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by BBQdave on 2011-06-14
My impression is that the latest Linux kernel changes in 11.04 causes problems with some older dell laptops.  I am running Ubuntu 10.10 on an inspiron 1100 with 1gb of ram, runs beautifully.

I tried running live cd and installing Ubuntu 11.04, and loads of problems on my laptop.  Though it loaded fine on an older sony desktop.

---

### Post by mörgæs on 2011-06-15
Try to create the USB stick with Unetbootin. 

If everything fails with 11.04, it is worth considering to stay with 10.10 or 10.04 for as long as it is supported.

---

### Post by Pieman62295 on 2011-06-16
Tried unetbootin. Didn't work. I've tried booting from a DVD, CD, and live USB on both the new new version of Ubuntu, the LTS version, and Mint. And I keep getting the busybox prompt with the same error message! This is frustrating....

---

### Post by mörgæs on 2011-06-16
This is getting complicated... Before turning to hardware errors, you could try the minimal ISO:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

