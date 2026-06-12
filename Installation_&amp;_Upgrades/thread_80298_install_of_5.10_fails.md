---
title: "install of 5.10 fails"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by j69ds on 2005-10-21
My first attempt at this os... I got version 5.10 downloaded and put onto a cd.
boot up and start the setup, all is well untill about halfway the base install it fails saying the the debootstrap has failed and it exits with an error 1.
I have tried reburning the cd, also using a different cd rom drive. in all cases I come up on the same error. Also I have disabled power management from the bios, since when it hangs the cd drive is not responding to the open button but this did not have any effect at all. In all I must have a tried a dozen times all with same result.
the pc I am installing onto is a pc clone with a amd processor 1.4 Ghz, with 512 Mb ram hd is just a mere 20 gig.
any idears to resolving this problem are very welcome....

Frans Jr.

---

### Post by Emerzen on 2005-10-21
A couple of thoughts:

Your system is more than adequate to run Ubuntu

Did you try the LiveCD before the install?  

What architecture did you download (should be the x86 iso's, not PPC)?

Debootstrap error is usually the result of a bad iso, not necessarily a bad burn-> I would download the LiveCD (I prefer bittorrent for it's data integrity) -> run LiveCD and download install CD from there -> burn iso using k3b in LiveCD which will automatically check the md5sum before burn

---

### Post by j69ds on 2005-10-22
Ok thanks for reply,

I have the live cd, it is what drew me to get the full version for install 
(this brings up another question though when I run live cd I do not see my hard drives? or am I looking in wrong place? )
yes it is the x86 version for pc

However I will go with your suggestion to redownload the iso and reburn it.

I will let you know how this  works out..

---

### Post by j69ds on 2005-10-22
Allright, I did download again and reburn to cd. the install went smoothly, now got a ubuntu box on the desk... now I got to learn how to use it... LOL
Thanks for the advice it worked...

Frans Jr

---

### Post by Tim0123 on 2005-10-22
I'm having the same problem with the base system and I thought the image was bad so I downloaded the iso image again and I'm still gettting the error. Where do you download your image from.

---

### Post by Emerzen on 2005-10-22
I always use the Bittorrent download.  What software are you using to burn?  Are you getting the exact same debootstrap error?

---

### Post by taygan on 2005-10-23
check the md5sum, check if dma is enabled on your cdrom (hdparm). search the archives for "debootstrap"

good luck.

---

### Post by Chasehead on 2006-05-07
I had the same problem until I used a regular CD-R instead of a CD-RW. After that, worked great....until a part in the installation where I have to start all over again because of a time zone glitch...of all the abuse my computer is taking to get ubuntu on it, you wouldnt think configuring my time zone would crash it?! Well, that's another story.

---

