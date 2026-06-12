---
title: "Can't log in ??"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stereo_steve on 2008-10-27
Hi everyone,

Just thought I'd share a problem i'm having with Intrepid and maybe some of you can give me some advice. Perhaps you are experiencing the same problem?

I have Ubuntu installed on an external USB 2.5" disk and i swap it between my work pc and my laptop. My laptop is a HP compaq nc6400 which has an Intel Graphics Media Accelerator 950. I have been using this laptop with Ubuntu since Feisty.

My problem is that my laptop gets to the login screen and everything looks fine. I login and the screen looks like something from a commodore 64 loading screen. Sometimes it falls back to the login prompt but most of the time it fails.

+ I have booted failsafe mode. Selected Fix X - no luck
+ I have uninstalled compiz - No luck
+ I have run dpkg-reconfigure xorg-xserver - no luck

I also see that I can no longer configure xorg. Or am i missing something? Its been like this for a week now and I figured that the problem would fix itself with updates. I'm up to date now and its still not working.

Any suggestions guys?

Thanks,
Steve

---

### Post by ajgreeny on 2008-10-27
If I remember correctly, you can only boot an external disk install of ubuntu on the computer which you used to install it.  This is because the hardware will be different and such things as the fstab file will not be compatible with other machines.  There is a way to do the external disk operating system, but I think this just means that you have the equivalent of a live CD but on a hard drive instead.

Have a look at [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/) for more info on the background to this type of install.

---

### Post by stereo_steve on 2008-10-27
Thanks for the response ajgreeny but I've been carrying Ubuntu around on my drive since Gutsy with no problems before. I always change the boot order in the bios and everything works fine.

It makes my job so much easier because I hot desk in work and it means I get to bring my "computer" around with me wherever I go!

Just can't get the display right with Intrepid. I was hoping someone here could point me towards some log files or give me some trouble shooting advice?

---

