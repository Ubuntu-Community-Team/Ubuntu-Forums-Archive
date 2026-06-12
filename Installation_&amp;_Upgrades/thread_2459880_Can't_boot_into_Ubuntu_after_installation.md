---
title: "Can't boot into Ubuntu after installation"
date: 2021-03-28
forum: Installation &amp; Upgrades
---

### Post by mrpresident2020 on 2021-03-28
In the last week, I reinstalled Ubuntu about 6 times. The reason is because I'm trying to install Tensorflow and make it run using Cuda.

Every time I install Ubuntu, it goes like this:

1) I install the OS
2) Right after I boot it for the first time, it tells me that some programs need to be updated, and I click on Update.
3) After it finishes updating, it shows the message: "your programs are up to date"

The problem happened last time I installed it. in step 3 above, instead of showing the message "your programs are up to date", it showed "your computer needs to restart to finish installing the updates". But when I restart it, it never boots. It gets stuck in a screen with a blinking cursor (blinking underscore).
Even after I install the whole thing again, the same thing happens. I can't install Ubuntu anymore in this computer, for some reason.

I think this problem has something to do with the last thing I tried in order to install Tensorflow. I installed Anaconda and used it to install Cuda and Tensorflow. The problem started to happen after that.
Maybe it did something to Grub that messed things up. I don't know.

How should I fix this?

Some information about my computer:
- It's a Dell with Nvidia GPU.
- Dual boot with Windows 10.

---

### Post by oldfred on 2021-03-28
Have you updated Dell's UEFI? And if SSD, SSD firmware?
Are you installing nVidia driver as part of the install? And only install from Ubuntu repository.

Do not know cuda or tensorflow, but you need to make sure system if fully running correctly before adding apps.

Reboot after update is not unusual if a new kernel or drivers are installed.

---

### Post by CatKiller on 2021-03-28
> **mrpresident2020 said:**
> But when I restart it, it never boots. It gets stuck in a screen with a blinking cursor (blinking underscore).

That's classic *Nvidia driver not installed properly* behaviour.

A lot more information about what you did and didn't do would be useful if you want help. In particular your 3-step process to failure doesn't detail the *installing random stuff* step that you allude to elsewhere. 

You haven't said if you're using Secure Boot. Drivers from the main Ubuntu repository are signed and will work fine either way. Drivers from the PPA aren't signed, so you need to sign them yourself if you want to use Secure Boot. Drivers installed with the .run file from Nvidia's website aren't meant for end users and will break on every kernel upgrade: don't use that. The drivers from Nvidia's CUDA repository don't come with all the stuff for normal desktop usage, so they're best avoided, too; they're also not signed.

In your other thread that you never went back to you were planning on adding Nvidia's CUDA repository and installing the CUDA toolkit but not the driver, getting your driver from the Ubuntu repositories or the PPA. That's really straightforward, once you've managed to navigate Nvidia's site to get the details of their repository.

---

### Post by mrpresident2020 on 2021-03-29
This problem (blinking cursor) happens even when I install nvidia drivers with the Ubuntu repositories. For example: when I install Ubuntu, it installs the nvidia-driver-460 during Ubuntu installation. It works fine. However, if I install any of the nvidia-drivers (even the same 460) afterwards using the Ubuntu repositories, this problem happens. I seems that the OS does something during Ubuntu installation that it doesn't do during the drivers installations afterwards. My guess is that Anaconda installed some driver and caused this problem again.

Another thing that I'm confused is that when you reinstall Ubuntu, it should overwrite everything in the disc. So why doesn't this problem go away with a fresh install? Is there some information that remains untouched even when I reinstall the whole OS?

---

### Post by oldfred on 2021-03-29
A full reinstall with formatting will erase all old data. If you do not tick the format box any files not part of normal install will remain. But that should not include nVidia drivers.

But if your install of new nVidia driver without totally purging old driver creates conflicts which then prevent nVidia driver from working correctly.

---

### Post by CatKiller on 2021-03-29
> **mrpresident2020 said:**
> This problem (blinking cursor) happens even when I install nvidia drivers with the Ubuntu repositories. For example: when I install Ubuntu, it installs the nvidia-driver-460 during Ubuntu installation. It works fine. However, if I install any of the nvidia-drivers (even the same 460) afterwards using the Ubuntu repositories, this problem happens. I seems that the OS does something during Ubuntu installation that it doesn't do during the drivers installations afterwards.

When you're installing fresh, there isn't already an Nvidia driver. If you've already got one branch of the Nvidia driver installed it interferes with the installation of a different branch of the Nvidia driver.

Because it's proprietary, it has to reimplement a bunch of stuff that open source stuff gets "for free," and they aren't very careful with their library versions to do that. When upgrading from the command line you can see the driver freaking out about the libraries it's trying to install already being there, and it ends up using the wrong versions of the libraries for the version of the driver.

If you remove an existing Nvidia driver branch before you install a new one, it's fine. ```
sudo apt-get purge nvidia*
``` should do it. 

For the blinking cursor issue - which can happen if you've got conflicts, and can happen on some hardware if you don't have any Nvidia driver at all - you can temporarily use the *nomodeset* boot parameter to get to a limited graphical environment. From there you can fix up your driver issue.

---

