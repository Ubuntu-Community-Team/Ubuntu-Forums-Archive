---
title: "attempting to install on laptop from usb stick"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by wog on 2013-04-26
I have Ubuntu on the usb stick. I plugged it in and booted the laptop from the usb stick. I went through the menu and chose Install Ubuntu. All is good so far.

Then I get: 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

I also get:
(initramfs) Unable to find a medium containing a live file system

Okay, this sort of makes sense, since the hdd has no OS, and I'm either expecting Ubuntu to install like normal or demand I make partitioning decisions. The problem is, I've never seen BusyBox before, I'm only an intermediate Ubuntu user (this may be the wrong place for this thread, I don't know), and I only barely remember how to use the mount command. Thankfully I also have a working Ubuntu machine so I can get at the man files.

Shouldn't Ubuntu have fired up gparted and partitoned the drive? Or am I missing something?

---

### Post by ibjsb4 on 2013-04-26
Yes, the live cd will partition the drive.  Have you tried to run ubuntu without installing?

---

### Post by wog on 2013-04-26
> **ibjsb4 said:**
> Yes, the live cd will partition the drive.  Have you tried to run ubuntu without installing?

Yes. After the menu option I get:
(initramfs) Unable to find a medium containing a live file system

Does this make any sense to you?

---

### Post by ibjsb4 on 2013-04-26
I took a look around and found a mountain of posts on this and just about as many (suggested) solutions.  The one that caught my eye is changing  SATA controller type from AHCI to IDE in BIOS.  But like I say, there are many suggested solutions.  Another was "checksum".

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unable+to+find+a+medium+containing+a+live+file+system&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unable+to+find+a+medium+containing+a+live+file+system&sa=Search&cof=FORID:9)
[https://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+a+medium+containing+a+live+file+system&ie=utf-8&oe=utf-8#client=ubuntu&hs=DTs&channel=fs&q=unable+to+find+a+medium+containing+a+live+file+system+ubuntu&revid=526828250&sa=X&ei=Kv56UfDGLLH9iQL8s4CYDw&ved=0CIIBENUCKAE&bav=on.2,or.r_qf.&bvm=bv.45645796,d.cGE&fp=f6891b0e0614ef8a&biw=1143&bih=674](https://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+a+medium+containing+a+live+file+system&ie=utf-8&oe=utf-8#client=ubuntu&hs=DTs&channel=fs&q=unable+to+find+a+medium+containing+a+live+file+system+ubuntu&revid=526828250&sa=X&ei=Kv56UfDGLLH9iQL8s4CYDw&ved=0CIIBENUCKAE&bav=on.2,or.r_qf.&bvm=bv.45645796,d.cGE&fp=f6891b0e0614ef8a&biw=1143&bih=674)

I think trying another source would also be a good idea.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

