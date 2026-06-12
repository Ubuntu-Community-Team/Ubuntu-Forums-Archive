---
title: "Unable to boot on live USB 16.04"
date: 2016-06-04
forum: Installation &amp; Upgrades
---

### Post by daaxwizeman on 2016-06-04
Hi everybody,

I have a new laptop with UEFI and I am totally new to this.

Sager/Clevo
i7 6700
2 x SSD Micron
GTX 980M

I set the UEFI boot mode in the BIOS, SecureBoot on. I have Win10 already installed.

I checked the mdsum of my ISO Ubuntu image and it is ok.

When I boot on the USB key, the boot grub appeared as required by the UEFI mode.

I set the grub.cfg file as suggested in this thread : [http://ubuntuforums.org/showthread.php?t=2326467](http://ubuntuforums.org/showthread.php?t=2326467)

I see the ubuntu splash screen appearing (the one with the dots) and finally get to a prompt screen saying this :

```
[4.846284] nouveau 0000:01:00.0: gr: failed to load fecs_inst
[6.488001] sd 4:0:0:0: [sdd] No Caching mode page found
[6488018] sd 4:0:0:0: [sdd] Assuming drive cache: write through

BusyBox v1.22.1 (Ubuntu 1:1:22.0-15ubuntu1) built-in shell (ash)
(initramfs) Unable to find a medium containing a live file system
```

I also tried without the modified grub.cfg as stated above and I do see the wallpaper of the 16.04 appearing, I see the mouse cursor, I see the the USB key is read because the led continuously flash, but nothing ever comes.... 

What should I do?

Thanks in advance for the help.

---

### Post by daaxwizeman on 2016-06-04
Hi again,

So I tried something else. I set nomodeset on the boot kernel options and removed the suggestion I told earlier and now I see the wallpaper, the mouse pointer and I get a flashing screen where I can see an ubuntu appcrash reporting (the window is flashing)  that compiz crashed. I was able to click on continue and after that, nothing is happening....

---

### Post by X-RED_Tech on 2016-06-04
If you have nothing else in the desktop from where you can open the settings, then the old trick of right-clicking the desktop, change background... Do not change it unless you want to but install click the top left button and you'll be at the settings panel from which you should choose Software properties, then the additional drivers tab. Wait a moment for it to work and then select and apply the recommended nvidia proprietary driver which must be one of the latest versions in order for that graphics card to work properly.
Reboot and you should have a beautiful desktop.

---

### Post by daaxwizeman on 2016-06-04
Hi X-RED_Tech,

Thanks for helping me out. Indeed, it seems a grphical problem here.... But even if I right click on what seems to be the wallpaper of the desktop, nothng is happening..... Can I install the nvidia driver manually on terminal? I have access to the terminal with ctrl+alt+F1.

---

### Post by X-RED_Tech on 2016-06-04
Never done it that way as nomodeset is usually enough to have a working desktop albeit limited to VESA standard (low resolution, etc.). So, you probably have other issues.
Try this:
```
sudo apt install nvidia-361
```
Which should install nvidia 361.42, the recommended driver for your card. Reboot.

If you still experience issues then a reinstall is in order and if so, this time pay attention to only use the F6 > nomodeset parameter.

---

### Post by oldfred on 2016-06-04
From the terminal you can do this:
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
sudo not required for listing, but is for install.
sudo ubuntu-drivers devices
# or
sudo ubuntu-drivers devices | grep recommended  

If you have a nVidia driver installed you must purge completely before hand or you get conflicts.


 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
If default is what you want:
sudo ubuntu-drivers autoinstall 

If you want or need the very newest kernels you can install this ppa first.
      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa 
# then this will give a different list including newer drivers.
sudo ubuntu-drivers devices

You can also specify version:

 sudo apt-get update && sudo apt-get install nvidia-3xx
# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.
# While you're at it upgrade libvdpau & nvidia-settings

---

### Post by daaxwizeman on 2016-06-04
Ok, I have access to the tty, but what do I enter for the ubuntu login and password it is asking of me?

---

### Post by X-RED_Tech on 2016-06-04
> **daaxwizeman said:**
> Ok, I have access to the tty, but what do I enter for the ubuntu login and password it is asking of me?

Exactly the same as you provided during the installation.

---

### Post by daaxwizeman on 2016-06-04
I didn't get to the installation yet, this graphical problem didn't let me..... I have never been able to get there once....

---

### Post by X-RED_Tech on 2016-06-04
You need nomeset and that alone should give a working desktop. Do not go anywhere else.

---

### Post by daaxwizeman on 2016-06-04
Here is what I set in my boot parameter :

[COLOR=#000000]menuentry "Try Ubuntu without installing" {[/COLOR]
[COLOR=#000000]set gfxpayload=keep[/COLOR]
[COLOR=#000000]linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper nomodeset ---[/COLOR]
[COLOR=#000000]initrd /casper/initrd.lz[/COLOR]
[COLOR=#000000]}

Again, I see the wallpaper, my mouse pointer, and if I right-click on the desktop, nothing appear and if I do the combination of those keys ctrl+alt+del, I have a flashing window of the system monitor that appear. Again, if I access the tty, I cannot login since I can't set login and password..... [/COLOR]

---

### Post by daaxwizeman on 2016-06-04
I am not even installing here, I just want to try it.

Do you think I should try an installation instead of running the live session?

---

### Post by daaxwizeman on 2016-06-04
Hi again, 

So, I decided to test the installation option instead of the live session. It booted really well and I could choose the language, set up my installation partition and such. Because I had no time to finish it up, I chose to quit and guess what ? It sent me right into a working live session. Everything is working!!!

Really bizarre, can't even log in when I chose the "Try ubuntu" but worked when I chose "Install ubuntu".

Si I guess it is ok for now. I will report if something else is going wrong.

Thanks for the help.

---

### Post by oldfred on 2016-06-04
Does your UEFI allow you to set with video you use?
Or can you boot with Intel video, not nVidia?

It is just about impossible to temporarily install nVidia driver to the live installer, but your nVidia will only work with the nVidia driver.
Normally the nomodeset boot parameter works with older nVidia, but some of the newest nVidia cards/chips do not yet work with the open source driver.

With Intel other boot parameter than nomodeset may be required.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions

[/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 



[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

---

