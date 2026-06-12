---
title: "Installing Ubuntu from USB Stick"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by nickhopkins07 on 2010-02-13
Hi Guys, 
 
I am the true definition of a 'noob'. i've bought an Acer Revo computer, mainly to run squeezecentre and plug into my AV amp. From reading a few bits, I get the impression I'm gunna be able to do much more with this little system if I install Ubuntu on it rather then keeping the pre-loaded Linpus Linux.
 
My biggest stumbling block so far is how to actually get Ubuntu onto the system, from what i can work out I need to use the USB Startup disk creator, but im guessing thats from within a computer thats already running ubuntu? Which i dont have, so once I've d/l ubuntu, how do i go about using Vista (wash my mouth out i know!) to put it on USB so it boots up into the Ubuntu installer?
 
Thanks

---

### Post by ironclaw on 2010-02-13
You can use [UNetbootin]("http://unetbootin.sourceforge.net/") to create a live USB from the ISO within Windows.

---

### Post by lenoirrichelieu on 2010-02-13
I don't know if I get it right. You have a new computer. You have a whatever operating system on it. You want Ubuntu.
 
If so why don't you d/l Ubuntu CD image, burn it on a disc, boot from it and install it?
 
Or if you want USB image  you should check if your computer knows to boot from USB. Probably you have to press a key (most use F12 during boot) for choose where to boot from. There you can select the USB drive.

---

### Post by LoloftheRings on 2010-02-13
Well.. you could burn an Ubuntu iso to a disk, boot from the disk on your vista computer (don't worry, it won't affect your computer at all) and use the usb creator.

Don't you have a CD drive in your Acer?

---

### Post by ironclaw on 2010-02-13
> **LoloftheRings said:**
> Well.. you could burn an Ubuntu iso to a disk, boot from the disk on your vista computer (don't worry, it won't affect your computer at all) and use the usb creator.

Don't you have a CD drive in your Acer?
I'm quite sure the Acer Revo is a nettop and does not have a CD drive. It should be able to boot from a live USB, since that's the only way another OS can be installed.

---

### Post by nickhopkins07 on 2010-02-13
Yeah indeed the Acer Revo has no optical drive, so booting from USB is my only option. Thanks for the tips guys, I'll give them a go and see how I get on!
 
Thanks:D

---

### Post by StevieRG on 2010-02-27
I've recently installed 9.10 on an Acer Revo 3600. The Linux OS it comes with is pretty inadequate if you want to do anything at all 'PC' like, so you'll probably want to install something else instead. The Revo has no optical drive but can boot from USB. This is how I installed 9.10 using USB:

I already have a Ubuntu PC, so used this to prepare the installation USB stick. To create a bootable USB stick from an existing Ubuntu PC:
Download Ubuntu 9.10 from the Ubuntu website and save to eg. Desktop. I used full as opposed to the netbook version as I have a big monitor plugged into the Revo, and the Revo can handle the full version anyway.

Get a 2 gig USB stick. I actually used a 2 gig SD card plugged into an SD to USB adapter which works fine.
Use the utility System > Administration > USB Startup Disk Creator   to copy the downloaded (.iso) file to the USB.

From now on the procedure is the same (regardless of whether you prepared your USB stick using Linux or Windows):

Switch on the Revo and stop the boot with the Delete key.
In Advanced Settings of the BIOS config, change the first boot device to be "USB".
Also – and importantly – disable "RevoBoot"!
Put the USB stick into the Revo.
Save the settings and exit the BIOS setup.
The system will now boot Ubuntu from the USB stick and invite you to install. Just follow the installation instructions. When it asks about disk useage, the easy option is to just say 'use all available space'.
After installing, shut down the Revo, and remove the USB stick.
Switch on again and stop the boot with the Delete key.
Change the first boot device back to HDD.
Save the settings and exit the BIOS setup.

Upon switchon you should now boot happily into Ubuntu.

Now – and importantly – by default you wont be using the proper Nvidia display drivers. Everything will look OK as it is, but theres a massive difference when using the proper drivers. XBMC runs shockingly slowly without the correct drivers (updates the screen about once every 5 seconds).

To enable the Nvidia drivers:
Use the menu item System > Administration > Hardware Drivers. It probably says no current proprietary drivers being used – but you want them! Click to enable the Nvidia drivers and they will be downloaded and installed. Then just reboot and the display will come to life.

Hope this is useful to someone.

---

### Post by tdlucas on 2010-02-27
Hi,

I pretty much did the same yesterday and now have 9.10 set up on my Revo.

I noted however that the NVIDIA drivers that are downloaded and installed are ver 185 whereas on the NVIDIA website they say the latest version is 190.53.

Should I update to this version (I'm unable to set the resolution when connecting to my TV via HDMI and this could maybe fix the problem) and if so, can someone talk me through how to install the update?

Cheers

---

### Post by bbala2020 on 2010-02-28
I've a netbook with no optical drive. When i try to use the usb-creator.exe, it says python26.dll not found :(

---

### Post by acreech on 2010-03-02
I am having trouble setting up a USB drive to install edubuntu 9.04 from. I used the above instructions to try and put the .iso onto a 2 GB SD Card and I also attempted a 1 GB USB Drive. 


I have attached the screen shot of the error that I get.

---

### Post by StevieRG on 2010-03-02
I did an install with full Ubuntu 9.10 pretty painlessly by preparing an SD card through a USB-SD bridge adapter from an existing PC that was running (at that time) 9.04. Did you download the .ISO image and use the startup disk creator under System>Admin?
 
I still have the SD that I used, and looking at it contains 857meg of files for 9.10, with a first level structure like this, I'm not sure whether with your distro it would be the same though:
.dsk   (a directory)
.Trash-1000   (a directory)
casper   (a directory)
dists   (a directory)
install   (a directory)
pics   (a directory)
pool   (a directory)
pressed   (a directory)
syslinux   (a directory)
autorun.inf
casper-rw
md5sum.txt
README.diskdefines
syslinux.cfg
wubi.exe

---

### Post by tpkaznowski on 2011-01-17
Hi GUys, 

I have just bought a Revo 3700 with linpus already installed... I want to install ubuntu. I have created a USB boot disk with ubuntu on it. I have been searching the web for ages and have found several posts relating to the difficulties with the BIOS in these machines. I have tried several different things - I have turned Quick and quiet boot off - I have turned Usb to primary boot option and I have Made sure that the USB is recognised as a HDD rather than AUTO. When I boot up it goes to the screen "press escape to boot" and when i press it, the machine boots into linpus again.....

I am getting very frustrated.... Can anyone help?

Taz

---

