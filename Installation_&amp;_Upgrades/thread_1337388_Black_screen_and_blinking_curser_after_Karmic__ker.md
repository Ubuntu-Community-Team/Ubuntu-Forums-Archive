---
title: "Black screen and blinking curser after Karmic  kernel update? Nvidia help inside."
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Shazaam on 2009-11-25
EDIT= This is for those of us that didn't disable the proprietary Nvidia drivers before doing the kernel update. See jimbo99's post to see if that works for you.

Doing this is NOT supported by Ubuntu (Canonical) (Nvidia too) and is probably considered an "ugly hack". If anyone else has a better way please post your info. :)

I run karmic with the proprietary 190.42 Nvidia drivers and did a kernel update yesterday. As usual the update freaked out the Nvidia drivers and left me with a blinking cursor on a black screen. No matter what I did the new kernel refused to boot. After much searching and grub trashing I was able to get the Nvidia drivers re-installed and back to a working system. Here is the procedure that worked for me...

1. Boot to a working (older) kernel.
2. Put the Nvidia driver on the desktop.

The "recovery" kernel line was just as unresponsive on my system as the normal one. To get it to boot I did this-
3. Open nautilus as root-
```
gksudo nautilus
```
go to /etc/X11 and make a copy of xorg.conf (I named mine xorg.confbak) so it will still be there for the other kernels later if you need it again.

4. Delete the original xorg.conf. YOU ABSOLUTELY MUST MAKE A BACKUP OF XORG.CONF FIRST! SEE ABOVE.
5. Reboot to the grub boot screen; highlight the new kernel "recovery" mode entry and press the "e" key to edit it.
6. Remove "quiet" from the end of the line and add vga=771 so it will look similar to this...
```
linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=<snip> ro single  splash vga=771
```
(Ignore the snip, it's just a long uuid. Yours will be different). Doing this (and #4) will allow the new kernel to boot in a low graphics mode. Do NOT hit your "enter" key

7. CTRL+X to boot the new kernel; choose "Drop to command line"; log in.
8. Since we don't have to stop gdm enter-
```
cd ~/Desktop
```
at the prompt and then-
```
sudo sh Nvidia-Linux-x86-190.42-pkg1.run
```
9. You will get a warning-
```
You appear to be running in runlevel 1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficult for `nvidia-installer` to correctly setup the kernel module configuration files.  It is recommended that you quit installation now and switch to runlevel 3 (`telinit 3`) before installing. Quit installation now? (select 'No' to continue installation) Answer: 
```
go ahead and choose "No", then finish the driver install (let it make the kernel module).
10. At the end the installer will ask you if you want it to write (or update) a new xorg.conf. Choose yes as we deleted the old one earlier. This is very important.
11. You will then end up at a prompt (at the bottom of the screen), enter-
```
sudo reboot
```
The new kernel(s) should now boot. Remember, you WILL have to do this every time you install a new kernel. dkms doesn't seem to be able to handle this anymore.

---

### Post by jimbo99 on 2009-11-25
I just edit the /etc/X11/xorg.conf file and change the Option "nvidia" to "nv" before I reboot. Then I load the nvidia driver as usual.

The problem with any fix like this is that it shouldn't be necessary.  This messyness by Canonical is giving Linux a bad name. They need to ensure this stuff works prior to the updates.  I understand the requirement to add the driver for the new kernel.  That's not what I'm talking about, though that should be addressed too.  I'm talking about the looping after the reboot, especially when they give no warning.

---

### Post by Shazaam on 2009-11-25
"I just edit the /etc/X11/xorg.conf file and change the Option "nvidia" to "nv" before I reboot."
That was the first thing I tried. It made no difference but thanks though.

---

### Post by ghostborg on 2009-11-25
Update manager was sitting on my lower panel, updated as normal reboot, all hell broke loose.
My computer gave me a flickering tty> login command line. For some reason I could not get to the grub menu by hitting escape. Tried several times. Finally booted the install disc and edited /etc/X11/xorg.conf. removed everything but the Section device and made the identifier "Default Device" and driver "vesa" .
Rebooted and used Hardware drivers to install.

My system uses a shared ATI 3200HD.

---

### Post by End Us3r on 2009-11-25
This should not occur. You should be able to get back to the desktop at the very least. I had to boot from the 9.10 install CD, then, via terminal, launched Nautilus (gksudo nautilus), backed up and then trashed the xorg.conf file, rebooted, reinstalled the 190.42 and then modified the xorg.conf file to get my dual display settings back.

---

### Post by bigsuccess on 2009-11-27
This happened to me also, I just booted to old kernel and am using that.

Am going to blacklist kernel updates from occurring, I don't have time for troubleshooting every kernel update :|

---

### Post by rsgooch on 2009-11-27
I updated my karmic using the nvidia propritery drivers and it worked fine.  I prefer to download and install the drivers myself.  DKMS should handle the modules update when the kernel is updated.

---

### Post by Arancaytar on 2009-11-27
Thank you, thank you so much. I have exactly the same problem and will now print this thread out, so I can try to fix my system. :)

---

### Post by leprasmurf on 2009-11-30
WTH is going on with Ubuntu lately!?!?!  I upgrade, and it breaks, I fix it to be prompted with another update in a few days....which also breaks it.  My brother updates his laptop, it breaks (with the exact same error that befell my computer).  After I fix it, his wifi stops working...due to another update!  Ubuntu is suppose to be the windows killer, making it just as easy to use, update and install new software.  I'm about to disable all but security updates, and say to hell with new major releases.  I do too much on my computer to have to spend a week upgrading to the new release every six months, and then spend a month working around the bugs.

---

### Post by gardara on 2009-12-06
What worked for me was to boot into an older kernel, then stopping gdm

```
ctlr+alt+f1
```
```
sudo stop gdm
```

then I just removed xorg.conf

```
sudo rm /etc/X11/xorg.conf
```

And booted into the new kernel which auto-generated a new xorg.conf

After I booted into the new kernel I simply re-installed the nvidia driver.


I didn't have any custom configuration to the xorg.conf, if you do this and have some custom settings in the xorg.conf, please remember to take a backup ;)

---

### Post by eGelor on 2010-04-29
Hello everybody,
After update to 2.6.31-20
i got a black scren and my nv crash.
i've tried to change my log and after reboot nvidia-settings don't work.
i did search a lot for about 10 days .
please help.

---

