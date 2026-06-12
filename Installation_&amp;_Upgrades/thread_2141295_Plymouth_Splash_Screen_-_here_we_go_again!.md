---
title: "Plymouth Splash Screen - here we go again!"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2013-05-02
I have a Nvidia GEForce 7300LE GPU and done a clean install of Ubuntu Studio 13.04 64bit version. Installation was completed without any issues except for the Plymouth screen not being displayed. When I did the Ubuntu Studio 12.04 install I had the same problem but was able to fix it with setting Framebuffer=yes in /etc/initramfs-tools/conf.d/splash but this time that did not work.

Tried various other solutions such as setting xforcevesa nomodeset video=vesafb:mode_option=1280x1024-16 from grub command line without success. 

Any hints will be greatly appreciated.

SEE BELOW FOR FURTHER INFO....

---

### Post by gdesilva on 2013-05-02
The solution in my case was to put vga=794 in the grub command line - (and of course, run update-grub).

I think there is an issue with vga=795 which is 1280x1024-24 and hence vga=794 (1280x1024-16 bit) was used. Hope this will be of use to someone.

---

### Post by MAFoElffen on 2013-05-02
Whatever you do, do it in /etc/default/grub...

Just a note:
I've been the known as the Linux graphics layer go-to guy since v11.04... but I can tell you that since v12.10, there's now another wrench thrown in there "somewhere" that I hanen't figured out yet.  The settings in /etc/default/grub work all good and fine from a cold boot, but on a reboot, it's anyone's guess what happens.

I still have a test box here that on reboot or shutdown, from the shutdown plymouth splash on, the session looks like it goes from 1920x1080 to 640x480. If on a reboot, it stays in that mode through the BIOS POST messages (Grub Menu is fine.) and the next plymouth boot splash. And nothing I've done changes that (so far)... Except for a shutdown and cold boot.

---

### Post by gdesilva on 2013-05-03
> **MAFoElffen said:**
> Whatever you do, do it in /etc/default/grub...

Thanks. Yes, I did modify /etc/default/grub and ran update-grub.

> **MAFoElffen said:**
> 
Just a note:
I've been the known as the Linux graphics layer go-to guy since v11.04... but I can tell you that since v12.10, there's now another wrench thrown in there "somewhere" that I hanen't figured out yet.  The settings in /etc/default/grub work all good and fine from a cold boot, but on a reboot, it's anyone's guess what happens.

I still have a test box here that on reboot or shutdown, from the shutdown plymouth splash on, the session looks like it goes from 1920x1080 to 640x480. If on a reboot, it stays in that mode through the BIOS POST messages (Grub Menu is fine.) and the next plymouth boot splash. And nothing I've done changes that (so far)... Except for a shutdown and cold boot.

Now that is very interesting.....I am running Ubuntu Studio 12.04LTS(32-bit) and just trialling out 13.04(64-bit) as a dual boot. I noted similar problem to what you are describing here....after running 13.04 when I boot 12.04 graphics resolution went crazy and I had to boot 12.04 with vga=794 option to get it back to normal. I thought this may be due to the fact that I am trying to run 64-bit and 32-bit OSes on the same machine and in fact I am in the process of downloading 32-bit 13.04 to establish this fact. I will let you know whether my problem is related to what you have described...thanks for alerting about this.

---

### Post by gdesilva on 2013-05-05
Installed the 32-bit version and I had the problem of 13.04 affecting the video settings of my 12.04 installation. This is how I fixed it - but not sure whether all the steps are needed or not.

1. echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
2. in /etc/default/grub  -> GFXMODE=1280x1024 (my screen resolution)
3. in /etc/grub.d/00_header -> after set gfxmode={GRUB_GFXMODE} command insert 
    set gfxpayload=keep
4. Save files and run update-grub

Note: vga=794 in grub command line can be saved in /etc/default/grub but it does not appear to get picked up in the grub menu (when editing the entry by pressing 'e' - most likely because this option is deprecated in grub2.

---

