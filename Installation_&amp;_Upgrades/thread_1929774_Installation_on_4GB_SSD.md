---
title: "Installation on 4GB SSD?"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by therock003 on 2012-02-22
Hello, i jut tried installing the 11.10 32bit Ubuntu system on a netbook i got with 4GB SSD drive inserted, and it prompted me with an error of needing more than 4.4GB free to continue with the installation.

Is there any way to trim the installation by ripping unnecessary files?

---

### Post by roelforg on 2012-02-22
Use ubuntu server and add your own gui;
it's not easy though.
EDIT: Referring to configuring the whole sys to work together.

---

### Post by snowpine on 2012-02-22
15gb is the minimum recommendation for Ubuntu. 

With only 4gb I recommend an ultra-light distro like SliTaz or TinyCore.

---

### Post by therock003 on 2012-02-22
But i have installed ubuntu in the past and it fit. What has changed that it needs more than 4GB? I dont need to do heavy work, i just need to run simple applications but i would prefer ubuntu from other distros...

---

### Post by snowpine on 2012-02-22
Ubuntu is a very full-featured distro (some might even call it "bloated").

If you want to create your own Minimal Ubuntu here is a guide: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

SliTaz is a 30mb download and uses maybe 200mb hard drive space, that is why I recommended it.

---

### Post by therock003 on 2012-02-22
Thank You for that. I will give it a try and if it fails for what i want to do, maybe i could try siitaz or whatever alternative there may be.

BTW do you know if i can use the same method i used with a full ubuntu image in order to launch the installation from a usb drive instead of burning iso to a cd?

Since my netbook doesnt have a drive, i use the universal usb installer to mount the iso into a bootable thumbdrive. I hope this works with the minimal iso as well.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by snowpine on 2012-02-22
I don't know anything about "universal usb installer." I have always used Ubuntu's own usb-creator with good results.

---

### Post by therock003 on 2012-02-22
I see. AFAIK though this can only run while you're in Ubuntu.

---

### Post by snowpine on 2012-02-22
I'm not much of a Windows user; sorry I can't help you there...

---

### Post by snowpine on 2012-02-22
Also I hope this is not too obvious, but nobody has mentioned it yet: Don't let the installer make a swap partition for you. If you only have 4gb then you don't want to waste space on swap!

---

### Post by therock003 on 2012-02-22
> **snowpine said:**
> Also I hope this is not too obvious, but nobody has mentioned it yet: Don't let the installer make a swap partition for you. If you only have 4gb then you don't want to waste space on swap!

I dont know how to handle this information. I guess it just create one on its own, like on this picture on the tutorial.

[IMG]http://www.psychocats.net/ubuntu/images/minimallucid17.png[/IMG]

It prompts as part1 for ext4 and part5 for swap. Was there any way i could have avoided that?

BTW i just booted. What's this? This is not ubuntu? Where's firefox and the rest of the interface, i cant make anything out of this :(

[IMG]http://www.psychocats.net/ubuntu/images/minimallucid39.png[/IMG]

---

### Post by darkod on 2012-02-22
Use the manual method and create only a single ext4 partition with mount point /.

As far as I know the auto methods always create root + swap.

Also you have you considered lubuntu? I believe that is the light version of ubuntu.

---

### Post by therock003 on 2012-02-22
I just tried to install an application in .deb format and it prompted me to "choose application". Isn't there a default program that allows you to install software using this method?

Also how can i add universe sources to the synaptics, with this minimal installation?

---

### Post by snowpine on 2012-02-22
I recommend choosing Manual Partitioning and installing to a single / (root) partition formatted as ext4.

Rather than describe every step and risk making an error (since I am not an Ubuntu user) I'll point you toward  this documentation: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by snowpine on 2012-02-22
> **therock003 said:**
> I just tried to install an application in .deb format and it prompted me to "choose application". Isn't there a default program that allows you to install software using this method?

Also how can i add universe sources to the synaptics, with this minimal installation?

Generally speaking you should install using the Software Center, Synaptic Package Manager, or terminal commands such as "apt-get" or "aptitude."

If you want to install unsupported 3rd party .deb files (at your own risk) then you can use the GUI application **gdebi** or the terminal command:

```
sudo dpkg -i whatever.deb
```

What is the name of the application you are trying to install?

---

### Post by therock003 on 2012-02-22
> **snowpine said:**
> Generally speaking you should install using the Software Center, Synaptic Package Manager, or terminal commands such as "apt-get" or "aptitude."

If you want to install unsupported 3rd party .deb files (at your own risk) then you can use the GUI application **gdebi** or the terminal command:

```
sudo dpkg -i whatever.deb
```
[B]
What is the name of the application you are trying to install?[/B]

Its sixemugui found here

[http://gimx.fr/download/gimx-ubuntu-32bits.html](http://gimx.fr/download/gimx-ubuntu-32bits.html)

---

### Post by snowpine on 2012-02-22
And did my instructions help you to install it? :)

---

### Post by therock003 on 2012-02-23
Good Morning. I just tried it, but couldn't get it to install because some dependencies were missing due to the fact that i don't know how to add the universe repo packages. IS there a command line to do it, cause with this minimal installation i cant find the synpatics manager gui?

---

### Post by sudodus on 2012-02-23
Try Lubuntu, the light-weight flavour of Ubuntu!

See the following thread by *amjjawad*
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1872303_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

---

### Post by therock003 on 2012-02-24
Is there any way to install unity now that i got the installation running? It's not practical the way it shows... I need something light yet user-friendly. I'm a novice linux user :(

---

### Post by sudodus on 2012-02-24
> **therock003 said:**
> Is there any way to install unity now that i got the installation running? It's not practical the way it shows... I need something light yet user-friendly. I'm a novice linux user :(
I don't know what you have running but

1. Lubuntu is light and user friendly, it uses LXDE. You can install this desktop environment with the command
```
sudo apt-get install lxde
``` but I would recommend the installation by amjjawad (see my previous post)

2. Unity 2D is lighter than standard Unity.

---

### Post by snowpine on 2012-02-24
> **therock003 said:**
> Is there any way to install unity now that i got the installation running? It's not practical the way it shows... I need something light yet user-friendly. I'm a novice linux user :(

I'm not 100% sure but I think you can simply:

```
sudo apt-get install unity
```

:)

---

### Post by therock003 on 2012-03-07
I'm thinking of dual booting an old laptop i have instead. So i will add ubuntu alongseide with the already installed Vista.

My _main questions_ are the following.

-On the new partition i will create should i leave it as NTFS (I HEAR Ubuntu handles it just fine) OR TURN IT TO EXT3/EXT4?

-Also will i need to create a swap partition or should i leave this one out?

> **sudodus said:**
> **I don't know what you have running** but

1. Lubuntu is light and user friendly, it uses LXDE. You can install this desktop environment with the command
```
sudo apt-get install lxde
``` but I would recommend the installation by amjjawad (see my previous post)

2. Unity 2D is lighter than standard Unity.


I have the minimal ubuntu followed from the guide here.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I dont want lubuntu or anything else. I want ubuntu. But the least Ubuntu edition that looks like ubuntu but doesnt have all the heavy stuff. The guide here results into a very strict interface OS.

> **snowpine said:**
> I'm not 100% sure but I think you can simply:

```
sudo apt-get install unity
```

:)


Thanks. I'll try that hoping that it works.

---

### Post by LinuxFan999 on 2012-03-07
> **therock003 said:**
> I'm thinking of dual booting an old laptop i have instead. So i will add ubuntu alongseide with the already installed Vista.

My _main questions_ are the following.

-On the new partition i will create should i leave it as NTFS (I HEAR Ubuntu handles it just fine) OR TURN IT TO EXT3/EXT4?

-Also will i need to create a swap partition or should i leave this one out?




I have the minimal ubuntu followed from the guide here.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I dont want lubuntu or anything else. I want ubuntu. But the least Ubuntu edition that looks like ubuntu but doesnt have all the heavy stuff. The guide here results into a very strict interface OS.




Thanks. I'll try that hoping that it works.
You should format the Ubuntu partition as ext4.
It would be a good idea to make a swap partition.

---

### Post by therock003 on 2012-03-07
> **LinuxFan999 said:**
> You should format the Ubuntu partition as ext4.
It would be a good idea to make a swap partition.

I used to hear about ext4 being buggy and ext3 being stable. Has the definitely been fixed? I want to make sure i wont encounter any issues.

Also whats the use of swap partition? I dont have much space available so i dont want to waste any, unless i really need the swap partition. Does it help with memory management?

---

### Post by snowpine on 2012-03-07
> **therock003 said:**
> I used to hear about ext4 being buggy and ext3 being stable. Has the definitely been fixed? I want to make sure i wont encounter any issues.

Also whats the use of swap partition? I dont have much space available so i dont want to waste any, unless i really need the swap partition. Does it help with memory management?

ext4 is the default recommendation of Ubuntu for a couple of years now.

Swap is like "virtual memory" in case you run low on RAM. Since your SSD is so small, I recommend **not** creating swap, and changing your work habits so that you don't fill up your RAM (for example open 1 or 2 apps at a time instead of a dozen or more).

---

### Post by C.S.Cameron on 2012-03-07
you can use usb-creator to do a persistent install on a 4GB drive, this uses 0.75 GB for the file system and leaves 3.25 GB for persistence.

---

### Post by therock003 on 2012-03-07
> **snowpine said:**
> ext4 is the default recommendation of Ubuntu for a couple of years now.

Swap is like "virtual memory" in case you run low on RAM. Since your SSD is so small, I recommend **not** creating swap, and changing your work habits so that you don't fill up your RAM (for example open 1 or 2 apps at a time instead of a dozen or more).

OK so ext4 it is. Swap partition is the pagefile equivalent for linux? If I create one will it make a great difference considering i only have 2GB of RAM?

> **C.S.Cameron said:**
> you can use usb-creator to do a persistent install on a 4GB drive, this uses 0.75 GB for the file system and leaves 3.25 GB for persistence.

How do you mean? What's _persistence_? Is there some guide to do what you're suggesting?

---

### Post by sudodus on 2012-03-07
> **therock003 said:**
> OK so ext4 it is. Swap partition is the pagefile equivalent for linux? If I create one will it make a great difference considering i only have 2GB of RAM?



How do you mean? What's _persistence_? Is there some guide to do what you're suggesting?

It is a way to change the live session from being volatile (disappearing at poweroff or reboot, because the file system is on a ramdrive) to persistent, because the written data are saved in a file system inside a casper-rw file or partition. See
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

---

### Post by C.S.Cameron on 2012-03-07
> **therock003 said:**
> 
How do you mean? What's _persistence_? Is there some guide to do what you're suggesting?

Boot Live USB.
Run gparted, format 4GB drive as FAT32.
Run Startup Disk Creator.
Select 4GB drive as Disk to use
Use maximum Stored in reserved extra space

If Startup Disk Creator does not see the 4GB drive, copy the iso to the drive and try MultiBootUSB:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by therock003 on 2012-03-07
> **sudodus said:**
> It is a way to change the live session from being volatile (disappearing at poweroff or reboot, because the file system is on a ramdrive) to persistent, because the written data are saved in a file system inside a casper-rw file or partition. See
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

This way though i would always need the CD, plus it takes loader to boot on the OS using LIVE and it requires even greater RAM... Right? :(

---

### Post by sudodus on 2012-03-08
> **therock003 said:**
> This way though i would always need the CD, plus it takes loader to boot on the OS using LIVE and it requires even greater RAM... Right? :(

1. Normally, you make a USB boot drive persistent, a CD is read-only.

2. The loader is on the USB drive too (and you should have the proper boot order, so when the computer finds a USB drive, it boots from it.

3. It is always good to have a lot of RAM, but not necessary.
--
But the most stable system is an installed one, installed to an internal HDD or SSD, single, dual or multi-boot.

---

