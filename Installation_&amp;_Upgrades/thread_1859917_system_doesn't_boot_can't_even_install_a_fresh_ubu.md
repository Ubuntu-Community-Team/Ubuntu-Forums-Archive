---
title: "system doesn't boot can't even install a fresh ubuntu"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by vikashiiitdm on 2011-10-14
hiii all,

i had a ubuntu 11.04 with gnome -3 installed in it. last night i put it on upgrade , when it started installing the upgrade i locked my system and went to sleep , but an idiot shut down my system after some time. I'm not sure whether the upgrade was successful or not , all  i know is that my system is not booting up nor even with the previous linux versions. not also in recovery modes! 

i am unable to install a fresh ubuntu over my pxe server . it shows a screen with a purple wallpaper, my mouse works , but i don't get anything else. i have an nvidia  graphical card on my laptop. everything else is also decent enough. please help my out . 

thank you

---

### Post by oldfred on 2011-10-14
You mention recovery mode, so you are booting with grub and get menu?

With nVidia I have always had to add nomodeset on first boot. I noticed that Oneiric new install installed the 173 version nVidia not the current which seemed wrong, so I changed it. Not sure about upgrades.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by vikashiiitdm on 2011-10-14
i am using pxe boot , not getting any other options ! :( what to do!

---

### Post by oldfred on 2011-10-14
I know nothing about pxe boot.

Try running this from a liveCD if you can, so we can see what is were. Not sure if it even works with a pxe boot:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by MAFoElffen on 2011-10-14
> **vikashiiitdm said:**
> i am using pxe boot , not getting any other options ! :( what to do!
Since you are asking these questions and trying to reinstall from external sources, I am assuming that it didn't finish your upgrade and that your system does not boot?  (That was not clear/you left that open)  Please clarify.

Why are you installing PXE?  Do you not have the ability to use a LiveCD or LiveUSB to boot off or to use it as diagnostics tool?  Do you not have a CD or DVD drive or USB port with BIOS that supports booting from them? That is what I assume when people do an externally connected install that takes extra effort to setup and do...  Tell me if that assumption is wrong.

If you try to boot your PC, do you get a Grub Menu?  If the installation borked before the end, there is a possibility that the Grub menu is still intact and that you could boot a previous kernel into tty text console mode to restart/continue your upgrade... thereby fixing your install.

If you can answer the above questions, that may give us an idea of where you are with that and direction in resolving your issue...

---

### Post by vikashiiitdm on 2011-10-15
> **MAFoElffen said:**
> Since you are asking these questions and trying to reinstall from external sources, I am assuming that it didn't finish your upgrade and that your system does not boot?  (That was not clear/you left that open)  Please clarify.

Why are you installing PXE?  Do you not have the ability to use a LiveCD or LiveUSB to boot off or to use it as diagnostics tool?  Do you not have a CD or DVD drive or USB port with BIOS that supports booting from them? That is what I assume when people do an externally connected install that takes extra effort to setup and do...  Tell me if that assumption is wrong.

If you try to boot your PC, do you get a Grub Menu?  If the installation borked before the end, there is a possibility that the Grub menu is still intact and that you could boot a previous kernel into tty text console mode to restart/continue your upgrade... thereby fixing your install.

If you can answer the above questions, that may give us an idea of where you are with that and direction in resolving your issue...

i am not trying to install a pxe server , i already have one up an running in my local network, yes i have usbBOOT option but would prefer a pxe boot cause several other systems in my network also are having same machine and same problems. Regarding the grub menu, yes i do get it and option to boot into previous linux versions , but none of them give me a command line or anything, they all freeze after a point. thanks for your response.

---

### Post by MAFoElffen on 2011-10-15
> **vikashiiitdm said:**
> i am not trying to install a pxe server , i already have one up an running in my local network, yes i have usbBOOT option but would prefer a pxe boot cause several other systems in my network also are having same machine and same problems. Regarding the grub menu, yes i do get it and option to boot into previous linux versions , but none of them give me a command line or anything, they all freeze after a point. thanks for your response.
Offhand, I know of 2 (of many) options that will work for that.  Both methods will get you booted (I'm giving both in case one doesn't work for you.)  Both then branch into the 3rd set of instructions, to install your video driver, clean up and fix the interrupted upgrade and finish the distribution upgrade.:

A. First Method, (easiest) From Grub Menu

1. At boot, hold down or press repeatedly the shift key. That should bring up the Grub Menu.
2. At Grub menu, Press "e".  That will put you into an edit mode on that grub menu item.
3. Arrow down to the line starting with "linux". That is the kernel boot line.
4. Arrow right until after the boot options "quiet splash".
5. Insert the kernel boot option "nomodeset" before the option "vt.handoff=7"
6. Press <cntrl><x> to boot with that option.

Once it boots, go to System Settings > Additional Drivers...  Install your driver.


B. Second method from LiveCD (or LiveUSB as it may), if the first doesn't work:

1. Boot from a LiveCD.  First page is black with a keyboard/person icon (input). Press Escape.
2. That will get you to a VGA looking keyboard selection screen. Press <esc> or <enter>. Both will end up as a US keyboard.
3. Then you should be at the Advanced Installation Menu.
4. At that menu, press <F6>. That will bring up dropdown Boot Options Menu.
5. Arrow down to where is says "nomodeset". Press your spacebar to select.
6. Press escape to exit the dropdown, it will keep the selection(s).
7. Select "Try" from the menu.
8. When booted from the Live-CD. Open a terminal session.
9. Find your installed Linux partition, e.g. /dev/sda5 (where you've installed Ubuntu ... the "/" or root mount partition)
```

sudo mount /dev/sda5 /mnt

```3. If you have a dedicated boot partition: sudo mount /dev/sda3 /mnt/boot
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" Oneiric, see chnageroot man page for details

10. Now in your desktop, go to System Settings > Additional Drivers and install your driver. (I don't know your specific Video Card model or I would have given you the CLI commands to install it...)


C. Both methods above of booting, getting to your install, installing the video driver, then branch to this--> where you fix and finish your update:

From there, open a terminal session (<cntrl><alt><t>).
```
[FONT=monospace]
[/FONT]sudo apt-get update  
sudo apt-get clean 
sudo apt-get -f  
sudo apt-get dist-upgrade

``` - Right before that last cli command, you "could" probably exit and do your automagic install from your pxe server, but you are already there...  The point is, you "need" to get your graphics driver installed and working, and the install got hosed on "this single" machine. It is no longer a "generic" install that is covered with your generic PXE install script.

Since "how" graphics is handled now in 11.04 and later (actually in upstream Linux itself), now I'm getting curious about how PXE Server installs are going to handle differences in client GPU's.  They are no longer handled as generic graphics as they where in 9.04 and previous.  11.04 and later is getting real particular about that.  The installer doesn't probe and adjust to that well <> its still a manual affair (installing proprietary drivers for prorietary GPUs) in that respect.

---

### Post by vikashiiitdm on 2011-10-15
> **MAFoElffen said:**
> Offhand, I know of 2 (of many) options that will work for that.  Both methods will get you booted (I'm giving both in case one doesn't work for you.)  Both then branch into the 3rd set of instructions, to install your video driver, clean up and fix the interrupted upgrade and finish the distribution upgrade.:

A. First Method, (easiest) From Grub Menu

1. At boot, hold down or press repeatedly the shift key. That should bring up the Grub Menu.
2. At Grub menu, Press "e".  That will put you into an edit mode on that grub menu item.
3. Arrow down to the line starting with "linux". That is the kernel boot line.
4. Arrow right until after the boot options "quiet splash".
5. Insert the kernel boot option "nomodeset" before the option "vt.handoff=7"
6. Press <cntrl><x> to boot with that option.

Once it boots, go to System Settings > Additional Drivers...  Install your driver.


B. Second method from LiveCD (or LiveUSB as it may), if the first doesn't work:

1. Boot from a LiveCD.  First page is black with a keyboard/person icon (input). Press Escape.
2. That will get you to a VGA looking keyboard selection screen. Press <esc> or <enter>. Both will end up as a US keyboard.
3. Then you should be at the Advanced Installation Menu.
4. At that menu, press <F6>. That will bring up dropdown Boot Options Menu.
5. Arrow down to where is says "nomodeset". Press your spacebar to select.
6. Press escape to exit the dropdown, it will keep the selection(s).
7. Select "Try" from the menu.
8. When booted from the Live-CD. Open a terminal session.
9. Find your installed Linux partition, e.g. /dev/sda5 (where you've installed Ubuntu ... the "/" or root mount partition)
```

sudo mount /dev/sda5 /mnt

```3. If you have a dedicated boot partition: sudo mount /dev/sda3 /mnt/boot
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" Oneiric, see chnageroot man page for details

10. Now in your desktop, go to System Settings > Additional Drivers and install your driver. (I don't know your specific Video Card or I would have given you the CLI commands to install it...)


C. Both methods above of booting, getting to your install, installing the video driver, then branch to this--> where you fix and finish your update:

From there, open a terminal session (<cntrl><alt><t>).
```
[FONT=monospace]
[/FONT]sudo apt-get update  
sudo apt-get clean 
sudo apt-get -f  
sudo apt-get dist-upgrade

```

thank you it worked!

---

### Post by vikashiiitdm on 2011-10-15
Dear all, 

thanks for all your valuable comments and suggestions .  the problem was with my nvidia card , doing a nomodeset during the boot solved the issue! the way to solve the problem in pxe boot is to press the tab to edit pxe boot options and remove video=normal and add nomodeset in place of it!  :D

---

### Post by MAFoElffen on 2011-10-15
> **vikashiiitdm said:**
> Dear all, 

thanks for all your valuable comments and suggestions .  the problem was with my nvidia card , doing a nomodeset during the boot solved the issue! the way to solve the problem in pxe boot is to press the tab to edit pxe boot options and remove video=normal and add nomodeset in place of it!  :D
Good deal! Please mark this thread as solved.

---

