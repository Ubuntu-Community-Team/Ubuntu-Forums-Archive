---
title: "Graphics failure on boot of 9.10 CD"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Computersleuth2 on 2009-12-02
I attempted to boot from the Ubuntu 9.10 install CD. During the boot, the boot sequence went through language setup and then displayed a white-on-black Ubuntu graphic while the CD was loading.

Then I observed a sequence of test patters with a square block superimposed on the patterns.  Inside the square block was this statement:

"Not Optimum Mode - - 

Recommended Mode:  

        1280x1024 60 Hz

        ------------
        |                           |
        |            ?          |
        |                           |
        ------------
(Please note that above is a square with a '?' in the middle.  The display feature of this site apparently filters out those spaces it considers to be extraneous.)

The test patterns were removed and the square block with text proceeded to traverse my screen in a diagonal fashion. All keys are locked up, the CD will not manually eject, and the traveling graphic continues to display - seemingly in perpetuity.

I am running an NVidia onboard graphics adapter, with an ASUS motherboard. My current OS is a dual boot Linux Mint 6 and Windows Server 2003 - these are on separate hard drives. I normally run Linux Mint 6 on this machine; and it appears to run really good - except for issues with some of the internet video streams.

I am guessing . . . that a possible fix is to interrupt the boot process and manually set the correct screen resolution. However, I do not have specific knowledge to do this; nor do I know if this is even possible.

Any help that you can provide will be greatly appreciated.

- Dave

---

### Post by efflandt on 2009-12-02
It is not the site that eats up extra spaces, it is standard html (any number of spaces, tabs, etc, are all considered one whitespace).  If you want fixed font, highlight the text and use the **#** at top of message window to mark it as code, or you can enter smart code tags manually with the word **code** surrounded by square brackets [ ] and ending with **/code** in square brackets.  For example:

```
|     |
|  ?  |
|     |
```I cannot help you with your specific nVidia problem.  But I did have experience with something similar when I tried to activate the nVidia driver in an earlier Ubuntu version and it totally blacked out X, probably because it was modules for an older kernel version that had been updated.  Fortunately I knew how to get into the console and was able to purge that package.

If you can somehow get into a console [try Crtl-Alt-F2 (or other Fn < F7) if X blacks out], see if you can get the output related to your video from **sudo lspci -v**.  Maybe someone else would be familiar with that specific nVidia device.

---

### Post by Computersleuth2 on 2009-12-02
> **efflandt said:**
> It is not the site that eats up extra spaces, it is standard html (any number of spaces, tabs, etc, are all considered one whitespace).  If you want fixed font, highlight the text and use the **#** at top of message window to mark it as code, or you can enter smart code tags manually with the word **code** surrounded by square brackets [ ] and ending with **/code** in square brackets.  For example:

```
|     |
|  ?  |
|     |
```I cannot help you with your specific nVidia problem.  But I did have experience with something similar when I tried to activate the nVidia driver in an earlier Ubuntu version and it totally blacked out X, probably because it was modules for an older kernel version that had been updated.  Fortunately I knew how to get into the console and was able to purge that package.

If you can somehow get into a console [try Crtl-Alt-F2 (or other Fn < F7) if X blacks out], see if you can get the output related to your video from **sudo lspci -v**.  Maybe someone else would be familiar with that specific nVidia device.

Thanks for your reply.  I am thinking that at the point in the boot process where it fails, the video driver in use will be the standard X video driver; rather than an Nvidia driver.  Further, the boot process should be (I believe) pulling the standard video driver off of the CD, rather than attempting to use any currently installed driver.

Am I missing something here?

---

### Post by renato.vitolo on 2009-12-03
I had exactly the same problem. I kind of solved it by reconfiguring gdm.
Of course, to do this you need a working root shell, don't you?

Try this: when the GRUB menu appears, edit the 'kernel' line by pressing 'e'
scrolling down and 'e' again (also see  here for more info:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[http://forum.soft32.com/linux/gentoo-Interrupting-boot-sequence-ftopict321907.html](http://forum.soft32.com/linux/gentoo-Interrupting-boot-sequence-ftopict321907.html))

Remove everything at the end of that line from the 'ro' onwards and add 'rw init=/bin/bash' instead. Then press 'Enter' and 'b' to boot. This should give you a shell.

From there, do 'dpkg-reconfigure gdm' and select gdm again, then exit and reboot.

In my case, this was not enough. On top of that I had to boot using previous versions of the kernel and fiddle around a lot. I am now using gdm-2.20 (legacy) and the thing works by miracle and I am too scared to touch it again.

This seems to be a weird conflict between the various login managers (gdm, kdm, xdm, I too have them all installed), which seems to leave the X system not working even after rebooting, for some reason which I was unable to identify. In certain cases, the DRM system was not found and X started in a very slow and CPU-consuming fashion. The problem persisted across a few reboots. Then I rebooted with another kernel and the problem was gone. And so on...

I have an AMD 64 system with an Intel VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). Kernel is
2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
but I have used other versions in the process like  Ubuntu 9.10, kernel 2.6.27-14-generic, Ubuntu 9.10, kernel 2.6.31-14-generic etc.

This is the first time that Ubuntu lets me down and it's not a pleasant one.

Good luck!

---

### Post by renato.vitolo on 2009-12-03
Excuse me, I have posted to the wrong post!

---

### Post by Computersleuth2 on 2009-12-10
> **renato.vitolo said:**
> I had exactly the same problem. I kind of solved it by reconfiguring gdm.
Of course, to do this you need a working root shell, don't you?

Try this: when the GRUB menu appears, edit the 'kernel' line by pressing 'e'
scrolling down and 'e' again (also see  here for more info:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[http://forum.soft32.com/linux/gentoo-Interrupting-boot-sequence-ftopict321907.html](http://forum.soft32.com/linux/gentoo-Interrupting-boot-sequence-ftopict321907.html))

Remove everything at the end of that line from the 'ro' onwards and add 'rw init=/bin/bash' instead. Then press 'Enter' and 'b' to boot. This should give you a shell.

From there, do 'dpkg-reconfigure gdm' and select gdm again, then exit and reboot.

In my case, this was not enough. On top of that I had to boot using previous versions of the kernel and fiddle around a lot. I am now using gdm-2.20 (legacy) and the thing works by miracle and I am too scared to touch it again.

This seems to be a weird conflict between the various login managers (gdm, kdm, xdm, I too have them all installed), which seems to leave the X system not working even after rebooting, for some reason which I was unable to identify. In certain cases, the DRM system was not found and X started in a very slow and CPU-consuming fashion. The problem persisted across a few reboots. Then I rebooted with another kernel and the problem was gone. And so on...

I have an AMD 64 system with an Intel VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). Kernel is
2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
but I have used other versions in the process like  Ubuntu 9.10, kernel 2.6.27-14-generic, Ubuntu 9.10, kernel 2.6.31-14-generic etc.

This is the first time that Ubuntu lets me down and it's not a pleasant one.

Good luck!

Thanks.  I will give this a shot as soon as I get some free time.

- Dave

---

