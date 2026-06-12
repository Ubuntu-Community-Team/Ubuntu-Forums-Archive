---
title: "lucid lynx [PPC?]"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anurse on 2010-03-25
Hi!

Any experiences with the lucid lynx beta on PPC?

Andrew

---

### Post by jim_24601 on 2010-03-26
I'm running it on my PowerBook now. I've not had any major problems that I can't work round.

The X.org Radeon drivers do not always play nicely with the kernel modesetting support enabled in the newer kernels. I had to disable KMS to get accelerated rendering.

I'm using cryptswap, and my swap isn't activated automatically at startup (I get the dreaded "Waiting for ... [sm]" message, and then X boots without it.) I can mount it manually, but still this isn't too pleasant if I don't realise I'm running swapless until the system starts thrashing.

Oh yes, and I had to download and rip the firmware for the AirPort Extreme (what a dumb name!) before the wireless LAN would work. Caused a bit of hassle with the live CD; when I came to install for real I was ready for it and had all the files on flash disc ready to go :)

Apart from that, everything worked out of the box. I've only just switched the PowerBook over to Linux, so I can't compare with other versions. The battery life isn't great, but I've not made any serious attempt to cut down on power usage other than disabling bluetooth. I'm also doing CPU-churning development work.

And you know what, I much prefer it to OSX. And I don't get the uncomfortable feeling that I'm using my computer on Apple's sufferance. I've still got a Tiger partition, but I don't know if I'm ever going to boot into it again.

---

### Post by anurse on 2010-03-26
Thanks for the information. It sounds pretty straight forward. Can I ask if you installed off CD or upgraded via the update manager/synaptic? 

I agree re Airport Extreme and the "feel" of Linux v OS X. 

Best
Andrew

---

### Post by mccashin on 2010-03-26
Last two days I can't get update-manager -d past retrieving initial install package on
my powerbook (PPC Karmic) or on Virtualbox (OS X) running 9.10 as well.

Both act as if the network times out retrieving the packages.

Could there be bandwidth problems with the repositories?

Installed 10.04 CD under Vbox OS X no problem.

---

### Post by Wiebelhaus on 2010-03-26
Yep , Doesn't feel like a beta at all other than the occasional minor bug.

---

### Post by nixscripter on 2010-03-27
> **jim_24601 said:**
> I'm using cryptswap, and my swap isn't activated automatically at startup (I get the dreaded "Waiting for ... [sm]" message, and then X boots without it.) I can mount it manually, but still this isn't too pleasant if I don't realise I'm running swapless until the system starts thrashing.

Just curious: did you set the key to **/dev/urandom** or **/dev/ramdom**? The latter will tend to cause long hangs (this is the voice of experience). ;-)

---

### Post by jim_24601 on 2010-03-29
> **Wiebelhaus said:**
> Yep , Doesn't feel like a beta at all other than the occasional minor bug.

So what you're saying is, it feels *exactly* like a beta :)

> **nixscripter said:**
> Just curious: did you set the key to /dev/urandom or /dev/ramdom? The latter will tend to cause long hangs (this is the voice of experience).

Er, no. I let the installer set it up. It's configured in crypttab as
```
cryptswap1  /dev/hda5  /dev/urandom  swap,cipher=aes-cbc-essiv:sha256
```

Oh, and to the OP, I remembered something else that's quite important. The upgrade killed my keyboard under X; I had to remove the mouseemu package to get it working again. See [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/513932"). Removing mouseemu hasn't caused any problems that I noticed.

---

### Post by JoeMac42 on 2010-04-10
I tried the Beta 1 Live CD on a G4 with an nvidia geforce 6600 video card.  The live CD booted successfully but all of the colors were inverted.  I ran into this when I installed Jaunty (from the alternate-install cd) but I was able to correct it after the install by editing xorg.conf.  I tried 9.10 but was never able to get the video working, so I reverted back to 9.04 Jaunty.  I would be interested in hearing about experiences with Lucid on PPC using nvidia AGP video cards now that Lucid has switched from NV to Nouveau for nvidia video support.

---

### Post by oubiwann on 2010-04-15
Wow, let me tell you about issues!

1) The first set of problems I ran into came as a result of having to install (and boot) off of a firewire drive (large chunks of the internal drive are dead). The installer does not set up the device entry properly in yaboot.conf. It took a while to uncover that issue, though.

2) The second major problem I had was with suspend and resume. Works *great* when running from the LiveCD. Completely fails when running off the hard drive.

3) After rebooting because of issue #2, my network interfaces are no longer recognized. I can't get ethernet or wireless.

I'm frustrated, but still hacking on it...

**Update**: For issue #3, it looks like I got bit by this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289584](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289584)

---

### Post by DougieFresh4U on 2010-04-15
I tried Lucid on my iMac G3.
I had to use an external screen as it would only present me with 'black' screen upon boot, but I heard all the 'bells and whistles' of the desktop loading, which is why I tried external monitor.
Then every time I clicked something, machine would 'lock' up and take forever to open. So I went back to Karmic.
That was using a 4/5/2010 daily download.
Will try again soon.

---

