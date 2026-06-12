---
title: "Mouse not working in Hyper-V"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by birdus on 2010-01-23
I'm brand new to Ubuntu (or any flavor of Unix/Linux, for that matter). I installed it (9.10) into a VM in Hyper-V with aplomb. However, the mouse isn't working, so I'm getting good at using the keyboard shortcuts right off the bat. :)

Anyhoo, I'd like to get the mouse working. I downloaded Hyper-V for Linux 1.0 (integration components), but I can't seem to get it installed. I attach to the ISO from my VM and the CD shows up in Ubuntu, but then what? I tried running the setup.pl file, but nothing seemed to happen and my mouse still isn't working.

Simple instructions (keyboard-oriented) would be greatly appreciated!

Thanks,
Jay

---

### Post by rogue_0111 on 2010-01-23
Try [virtualbox]("http://www.virtualbox.org/") instead. Open Source baby.

Here's a how to video also:

[http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows](http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows)

---

### Post by birdus on 2010-01-24
Anyone have an answer to this question?

---

### Post by matthew.mattoon on 2010-05-29
Hi Birdus,

I have written an article describing the different components of Ubuntu Integration on Hyper-V.  This article has much more simplified instructions.

Now it sounds to me like the mouse is not working for you at all?  If that is the case it is probably due to you using RDP from your workstation to another workstation or the server, then from their using SCVMM or Hyper-V Manager to connect to the VM.  This will NOT work for mouse.  If you use your workstation to connect to the VM directly via SCVMM or Hyper-V Manager it will work just fine.  It is simply the problem with the RDP connection losing control of the mouse (this happens on Windows guests with no ICs as well).

[http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx)

-matt

---

### Post by Victor Miasnikov on 2011-02-24
> **matthew.mattoon said:**
> 
Now it sounds to me like the mouse is not working for you at all? If that is the case it is probably due to you using RDP from your workstation to another . . . server, then from their using SCVMM or Hyper-V Manager to connect to the VM. This will NOT work for mouse. If you use your workstation to connect to the VM directly via SCVMM or Hyper-V Manager it will work just fine. It is simply the problem with the RDP connection losing control of the mouse (this happens on Windows guests with no ICs as well).
 
Mini How-To about _practically_ method for worked mouse in Linux guest:
 
Linux on Hyper-V How-To FIX &#8220;Mouse not captured in Remote Desktop session&#8221;
[http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/](http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/)
==
. . .
Without Satori, mouse work in Linux Guest if connect to it from Windows _directly_
. . .
==

---

### Post by Victor Miasnikov on 2012-03-13
Satori come back =} Ctrl-Alt Left -- God Bay!  read ( in creation time order):
[http://vvm.blog.tut.by/category/linux/](http://vvm.blog.tut.by/category/linux/)
[http://www.simweb.ch/blog/2011/12/experimental-hyper-v-branch/](http://www.simweb.ch/blog/2011/12/experimental-hyper-v-branch/)
[http://www.simweb.ch/blog/2011/10/state-of-linux-on-hyper-v/](http://www.simweb.ch/blog/2011/10/state-of-linux-on-hyper-v/)

---

