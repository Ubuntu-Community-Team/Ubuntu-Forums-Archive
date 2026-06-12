---
title: "Enable Nvidia restricted driver for Custom LiveCD"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by mburris on 2007-06-30
Let me give you guys a little history on my situation here so you can better understand what/why i want this.

I am building a LiveCD (liveUSB actually, but close enough) for my parents and grandparents. Want it does is basically allow them full use of Ubuntu without them worrying about messing anything up. I am using a non-writable configuration here... ie not persistent USB, so that if they have a problem, they restart the PC, and their PC is good as new.

I have been reading everything I could find that was even remotely related to LiveCD / LiveUSB / SquashFS / Casper customization. Until this point there has been (or at least I have been able to find) enough documentation to figure out almost everything I needed. Here's what I am able to do now:

(at first I did try using UCK - ubuntu customization kit and reconstructor, but I found them limiting me, and I was able to learn (and do) a lot more by doing all the steps manually)
- Mount the SquashFS of a LiveCD
- Copy the squashed filesystem to a folder for customization
- Chroot into the extracted squashFS to make changes (ie install / remove / command line changes / and now, even run GUI application in the chroot'ed environment
- customize all aspects of the GUI including uSplash startup and shutdown animations
- re-compress (mksquashfs) the customized live filesystem
- package it all back up in an ISO or USB stick and boot to it
(keep in mind 3 weeks ago, when I started this project I was strictly a Windows guy and had really never even booted Linux of any kind) quick study i guess...

Now one of the last things I would like to do is add proprietary Nvidia video driver support to my rofs (read only file system). Why? couple reasons: 1. I want them to be visually comforted by the GUI, beryl will do that. 2. I would like to make the menu as easy to use as possible and I have set my sights on a graphic rich OSX like dock that requires beryl like 3D effects.

I read somewhere (i believe it was on the Linux-mint or mint-Linux forum) that someone was able to disable the hooks in Casper that allowed the restricted modules required to automatically support the Nvidia video driver. There was no other information he provided in that or any other post I could find.

Can someone point me in the direction of some documentation or give me a little hint as to how I can allow the Nvidia proprietary drive to automatically work in a LiveCD / USB system? I'm not afraid to get dirty doing this... lord knows I already have.

---

### Post by Silvestre on 2007-06-30
> **mburris said:**
> Let me give you guys a little history on my situation here so you can better understand what/why i want this.

I am building a LiveCD (liveUSB actually, but close enough) for my parents and grandparents. Want it does is basically allow them full use of Ubuntu without them worrying about messing anything up. I am using a non-writable configuration here... ie not persistent USB, so that if they have a problem, they restart the PC, and their PC is good as new.

I have been reading everything I could find that was even remotely related to LiveCD / LiveUSB / SquashFS / Casper customization. Until this point there has been (or at least I have been able to find) enough documentation to figure out almost everything I needed. Here's what I am able to do now:

(at first I did try using UCK - ubuntu customization kit and reconstructor, but I found them limiting me, and I was able to learn (and do) a lot more by doing all the steps manually)
- Mount the SquashFS of a LiveCD
- Copy the squashed filesystem to a folder for customization
- Chroot into the extracted squashFS to make changes (ie install / remove / command line changes / and now, even run GUI application in the chroot'ed environment
- customize all aspects of the GUI including uSplash startup and shutdown animations
- re-compress (mksquashfs) the customized live filesystem
- package it all back up in an ISO or USB stick and boot to it
(keep in mind 3 weeks ago, when I started this project I was strictly a Windows guy and had really never even booted Linux of any kind) quick study i guess...

Now one of the last things I would like to do is add proprietary Nvidia video driver support to my rofs (read only file system). Why? couple reasons: 1. I want them to be visually comforted by the GUI, beryl will do that. 2. I would like to make the menu as easy to use as possible and I have set my sights on a graphic rich OSX like dock that requires beryl like 3D effects.

I read somewhere (i believe it was on the Linux-mint or mint-Linux forum) that someone was able to disable the hooks in Casper that allowed the restricted modules required to automatically support the Nvidia video driver. There was no other information he provided in that or any other post I could find.

Can someone point me in the direction of some documentation or give me a little hint as to how I can allow the Nvidia proprietary drive to automatically work in a LiveCD / USB system? I'm not afraid to get dirty doing this... lord knows I already have.

For running a propietary nvidia-Driver you need first to uninstall:

-nvidia-common-kernel
-linux-restricted-modules

Then:

You need the kernel headers or kernel source of your actually kernel

Further you must to deny the start of the "nv" driver in:

/etc/default/linux-restricted-modules-common

```
DISABLED_MODULES="nv"
```

When you have made all this things then it will run. You ask, how you can integrated that on CD running a Windows??? a Linux ??? machine
I don't know but you have what you need for running a propietary driver. Don't forget to uninstall all the nvidia-things that you have installed before otherwise you won't have success.

---

### Post by mburris on 2007-06-30
I don't know if we are talking about the same thing.

I am building a custom LiveCD that will only be ran on one type of hardware ( a specific motherboard, video card, etc etc)  

**I want to recompile the Live CD to use and start the propritary nvidia video driver.  I want the driver to start automatically everytime the system is booted.  **

Installing the driver is not a problem...  I can do that when i'm chroot'ed into the filesystem that will become the LiveCD system.  The problem is that Casper seems to be rejecting configurations I make to X and using its own.

Here is the process as I understand it, and if i'm wrong please correct me:

syslinux/isolinux ---> initd.gz ----> casper -----> real kernel -----> live system

---

### Post by mburris on 2007-07-01
I am writing this from my LiveUSB stick running Ubuntu 7.04 with full nvidia proprietary video support enabled at boot.  mmm beryl looks even better when it works from the LiveCD

How did it do it?  Actually, quite simply. (haha)

(this is not a step by step guide.. I am not going to write one.. this is a basic account of exactly how i got this to work.. using this walkthrough, some common sense, and a little research, any one can do this... here we go

I started out by making a normal bootable LiveUSB stick
([following these instructions but use feisty fawn as the source iso instead of Edgy]("http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/"))

Then I performed basically normal 7.04 installation onto a hard drive.  (only difference was during the hard drive partitioning step I chose "manually" and did not use a swap partition.

Then I rebooted and started using the new installation... 
(note: it is KEY to not install any of the available system updates... the kernel must remain at the original version installed by the CD -mine was 2.26.20.15-generic)
then I installed the restricted nvidia driver using [ENVY]("http://www.albertomilone.com/nvidia_scripts1.html") then I restarted.

After the restart its time to install any cool 3D stuff you want like Beryl and Kiba Dock.

Now would be a good time to make any other modifications to your system you want to become a perminent part of the liveCD.  I installed things like Java, Flash, and multimedia codecs.  I also made changes to the theme, wallpaper and icon scheme.

Now that I have all the changes I'd like to make to the system, and i have rebooted a few times, and cleaned the trash bin and made sure all the other temporary crap was gone, its time to build the Live file system. -- In order to do this, we need to boot the PC to a LiveCD so we can work with the hard drive's file system while it is 'offline'.

Once the PC is booted with the standard live CD, install mksquashfs tools from the terminal.  Go to Places > Computer and double click on your hard drive's icon to mount it.  Then I would bring up nautilus as root by typing "sudo nautilus" at the terminal prompt.  Then browse to the mount location of the hard drive's files... for me its "/media/disk" (after double clicking on filesystem).  Here i create a folder called "toBeSquashed" and i move all the files from the "/media/disk/" folder in to it.  then I use another terminal window to make a squash file system out of the files i moved into the folder i created called toBeSquashed by issuing the terminal command: "sudo su" enter... then "cd /media/disk" enter... then "mksquashfs toBeSquashed filesystem.squashfs" enter

This will create a 700 ~ 900MB file called "filesystem.squashfs" in the root of your hard drive.  This file will be the file system used in the bootable CD or USB stick.  At  this point I will move all the files that i moved into the toBeSquashed folder back to the root of the hard drive.

Now i reboot the PC back into the ubuntu installed on the hard drive.  

I copy the filesystem.squashfs file that we created while in LiveCD to the /casper folder on the USB stick we created in step 1. (replace the existing file)  

Now here is where the magic comes in... take the initrd.gz file from the root of the USB stick, and [extract it to a temporary working folder]("http://www.extremetech.com/article2/0,1697,2132842,00.asp")

It will extract all the files that make up the pre-os loading process... we need to delete a single file from the folder, %extracted%/scripts/casper-bottom/  ..the file name is something like 20xconfig ... it is the part of the initrd casper configuration that automatically creates a new xorg.conf file thereby over writing the xorg.conf file that has been already setup to work with the Nvidia drivers... we dont want that file to be overwritten!!!

Once that file has been removed, recompress the files using the information found in the link above.  Place the resulting initrd.gz file in the root of the USB stick overwriting the existing one.

now boot to your USB stick and enjoy.

---

### Post by lifeempowered.com on 2007-07-04
> **mburris said:**
> Let me give you guys a little history on my situation here so you can better understand what/why i want this.

I am building a LiveCD (liveUSB actually, but close enough) for my parents and grandparents. Want it does is basically allow them full use of Ubuntu without them worrying about messing anything up. I am using a non-writable configuration here... ie not persistent USB, so that if they have a problem, they restart the PC, and their PC is good as new.

I have been reading everything I could find that was even remotely related to LiveCD / LiveUSB / SquashFS / Casper customization. Until this point there has been (or at least I have been able to find) enough documentation to figure out almost everything I needed. Here's what I am able to do now:

(at first I did try using UCK - ubuntu customization kit and reconstructor, but I found them limiting me, and I was able to learn (and do) a lot more by doing all the steps manually)
- Mount the SquashFS of a LiveCD
- Copy the squashed filesystem to a folder for customization
- Chroot into the extracted squashFS to make changes (ie install / remove / command line changes / and now, even run GUI application in the chroot'ed environment
- customize all aspects of the GUI including uSplash startup and shutdown animations
- re-compress (mksquashfs) the customized live filesystem
- package it all back up in an ISO or USB stick and boot to it
(keep in mind 3 weeks ago, when I started this project I was strictly a Windows guy and had really never even booted Linux of any kind) quick study i guess...

Now one of the last things I would like to do is add proprietary Nvidia video driver support to my rofs (read only file system). Why? couple reasons: 1. I want them to be visually comforted by the GUI, beryl will do that. 2. I would like to make the menu as easy to use as possible and I have set my sights on a graphic rich OSX like dock that requires beryl like 3D effects.

I read somewhere (i believe it was on the Linux-mint or mint-Linux forum) that someone was able to disable the hooks in Casper that allowed the restricted modules required to automatically support the Nvidia video driver. There was no other information he provided in that or any other post I could find.

Can someone point me in the direction of some documentation or give me a little hint as to how I can allow the Nvidia proprietary drive to automatically work in a LiveCD / USB system? I'm not afraid to get dirty doing this... lord knows I already have.

Hi, I'd like to get your steps if you don't mind, on how you did the above?  I'd like to duplicate it for an ATI driver.  Thanks!

---

### Post by mburris on 2007-07-04
> **lifeempowered.com said:**
> Hi, I'd like to get your steps if you don't mind, on how you did the above?  I'd like to duplicate it for an ATI driver.  Thanks!

John... This was very funny... I had read your blog note on your littleUbuntuGuild page the other day, and just left you a comment with a link to this thread... Then i came here and saw your comment.  

I dont have time at the moment right now to fully document what I did, but I would be more than happy to help you out... i mean it was *your* guide that allowed me to install ATI graphics on my e1505 a month ago when i took ubuntu for my first test run...

Start out by actually installing the OS on a hard drive.  You will need to keep the kernel at 2.6.20.15 so DO NOT apply those updates. Install your ATI drivers and any other customizations you want and then get back to me here.

- Matt Burris
[www.360mbits.com](www.360mbits.com)

---

### Post by lifeempowered.com on 2007-07-04
Ah, I see you registered at my blog, cool.  I have a few VMs I'm using so I'll install a fresh Ubuntu on one as you say.  Thanks.

John

---

### Post by mburris on 2007-07-04
> **lifeempowered.com said:**
> I have a few VMs I'm using so I'll install a fresh Ubuntu on one as you say.


Does your Ubuntu installation on the VM recognize your ATI card and prompt to install the restricted drivers?  If no.. then you will need to do an actual installation maybe using a temporary hard drive on a PC that has an ATI video card.

---

### Post by jseligma on 2007-12-02
Hi mburris, 
I really like the idea behind your method. If I could get it to work, I can see that it would be a very flexible appraoch to customising Ubuntu on a USB drive. Unfortunately, I can't quite get it to work with Gutsy. Have you tried this?  I've found that simply removing 20xconfig from initrd doesn't work. My nVidia graphics card isn't recognised, and I'm asked to put in the settings manually (and after that, the boot hangs). 

The rest of the installation appears to be okay. If I  don't remove 20xconfig then the copied (and altered) filesystem boots nicely, but without the restricted drivers of course.

---

