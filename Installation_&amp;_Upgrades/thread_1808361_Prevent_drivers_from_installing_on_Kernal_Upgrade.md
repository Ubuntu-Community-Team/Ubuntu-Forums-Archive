---
title: "Prevent drivers from installing on Kernal Upgrade"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by twignation on 2011-07-20
Hello,

I had a quick look around to see if anyone has already asked this, and I couldn't find a solution/question. 

I have a GByte GA-P67A-UD4 (Version B3) and 1GB XFX HD6870: 
The driver for the network card on the motherboard is RTL8111E, and requires the r8168 - which I get from the [realtek website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")  

The driver for my graphics card I get direct from the [Ati website]("http://support.amd.com/us/gpudownload/Pages/index.aspx"), and works very well thank you very much.

However, every time I get a Kernel upgrade, the drivers for both of these are changed; the network card gets set to the repo driver (r8169) - and I have never found out what the graphics card gets set to, as my X-session just goes blank on re-install, and I just put back my Ati driver through the safe-session thing.

Is there anyway of repressing the driver updates?

Am I asking in the wrong place/going about this wrong?

Cheers

---

### Post by Grenage on 2011-07-20
I think what you want to do can be achieved by writing a short script which installs the drivers, then moving that script to */etc/kernel/postinst.d/*.  That script should then run post-install, or when a new kernel has been installed.

I've not done it before, so hopefully someone who has will chime in.

---

