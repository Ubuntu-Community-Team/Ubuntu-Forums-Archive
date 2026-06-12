---
title: "how does driversupport work in Bumblebee?"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Askel on 2012-11-21
Hello

I installed Bumblebee a while ago. I tried glxspheres and optirun glxspheres to see the difference. And difference it was.

But how does it work with the drivers? When I installed it the additional drivers under systemsettings disappeared. Is that how it should be? Does Bumblebee use own drivers?

I also wonder how to start games with optirun. For example I have Oil-Rush, Bastion and Amnesia. None of these can be started using optirun. Firefox on the other hand works great with optirun.

Also I wonder how well the Bumblebee actually work with Nvidia Quadro K2000M. The displayport stopped working after I installed it. When I removed it (while following the instructions) the grafics was all messed up, with displayport still not working and really bad resolution. I had to reinstall Bumblebee to get good resolution again. Unfortunately the displayport is still not active. :(

---

### Post by 2F4U on 2012-11-21
You may wish to read through the FAQ:

[https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)

> **How it works?**

  The Bumblebee server disables the discrete video card if no client is detected (if power management is enabled which is the default setting). This is done by keeping track of programs that request Bumblebee to run themselves on the discrete nvidia card. On such requests, a X server is started which makes use of the nvidia card. Because the frames cannot directly be displayed on the display due to the Optimus design, [VirtualGL]("http://en.wikipedia.org/wiki/VirtualGL") is used to copy frames to the visible display which runs on the integrated Intel GPU.


> **How to know if my graphics card is supported?**

  Bumblebee has two parts: power management and the ability to run programs using the discrete card. The first feature is supported with [bbswitch]("https://github.com/Bumblebee-Project/Bumblebee/wiki/bbswitch") which should be able to support all Optimus models. The ability to use the nvidia card depends on the driver: [open-source nouveau]("http://nouveau.freedesktop.org/wiki/FeatureMatrix") and [proprietary nvidia]("http://www.nvnews.net/vbulletin/showthread.php?t=122606").


---

### Post by Askel on 2012-11-21
Thanks for the quick reply.
I've read it, but not quite understood it. 

"Because the frames cannot directly be displayed on the display due to the Optimus design, [VirtualGL]("http://en.wikipedia.org/wiki/VirtualGL") is used to copy frames to the visible display which runs on the integrated Intel GPU. 			 		"

This I did not understand.

I've been reading about [bbswitch]("https://github.com/Bumblebee-Project/Bumblebee/wiki/bbswitch"). Is that installed and activated by default? Because that's how I understood it.
I've checked the Bumblebee.conf file and from what I can gather Bumblebee uses the Nvidia-current driver. But how come this doesn't come up under additional drivers? Is it because Ubuntu doesn't need additional drivers because they are run through Bumblebee? What difference does it make if Bumblebee uses the proprietary driver or Nouveau?

Is there any configuration I need to do after the install?

> **2F4U said:**
> You may wish to read through the FAQ:

[https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)

---

