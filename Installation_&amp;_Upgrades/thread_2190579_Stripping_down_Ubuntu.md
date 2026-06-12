---
title: "Stripping down Ubuntu"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by kingcobraa on 2013-11-28
Hi,

I recently did a fresh install of Ubuntu 12 on my system  however I cannot help but observe while reading about it that there are a  lot of services and applications that I would not have any use for.

My questions are :

How to know exactly what is installed (services, protocols, applications etc) and the purposes these installations serve.

How to permanently remove all traces of what I feel is not required (without breaking the system) and other unneeded things.

I like to have the bare minimum installed on the system and that also only if I feel it is required.

Hope someone can help me by posting all the commands.

---

### Post by sammiev on 2013-11-28
Download the minimal install ISO and build it from there.

---

### Post by vasa1 on 2013-11-28
Different people have different needs. So your "bare minimum" will differ from mine. Also check out [http://ubuntuforums.org/showthread.php?t=2188868](http://ubuntuforums.org/showthread.php?t=2188868)

---

### Post by CharlesA on 2013-11-28
> **sammiev said:**
> Download the minimal install ISO and build it from there.

This.

Or you could just install Debian. :p

---

### Post by kingcobraa on 2013-11-28
Hi Guys,

Thanks for responding.

hmm... Did some reading on the minimal install of ubuntu, better option...

However I love the Unity desktop environment as not very well versed with terminal as yet and the others are not to my liking.

Is a bare minimum install of Unity possible?

Many thanks.

---

### Post by CharlesA on 2013-11-28
> **kingcobraa said:**
> Hi Guys,

Thanks for responding.

hmm... Did some reading on the minimal install of ubuntu, better option...

However I love the Unity desktop environment as not very well versed with terminal as yet and the others are not to my liking.

Is a bare minimum install of Unity possible?

Many thanks.

You can probably remove the stuff you don't use, but I've never tried it on my 12.04 install with Unity.

---

### Post by ibjsb4 on 2013-11-28
Check this link out.  

[http://packages.ubuntu.com/saucy/ubuntu-desktop](http://packages.ubuntu.com/saucy/ubuntu-desktop)

This is a list of all packages thats installed by default.  Notice all the recommended packages (the ones with the green dot), these packages are not critical to the system but are installed as extras.  By using the mini iso you can install just the necessary packages (the ones with the red dot).  This would take just one command.

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9)

And like CharlesA, I do not run Unity and have not tried this.

---

### Post by kingcobraa on 2013-11-28
Hi oh yeah baby!!!!! I am doing the mini install now. I thought it was stuck for 20 minutes and started typing on this page but then whooosh!!! It has started downloading the updates now. Lets wait and see what happens. Will post as soon as it is completed.

---

### Post by kingcobraa on 2013-11-28
Now it is giving me the message on the screen to choose a disc driver as it has not detected my drive. What driver do i select or what did i do wrong?

---

### Post by Bucky Ball on 2013-11-28
*Thread moved to **Installation & Upgrades**.*

---

### Post by Bashing-om on 2013-11-28
kingcobraal Hi !

I have never encountered that advisory ! ubuntu is real smart about detecting ALL your hardware and devices,
Are you installing with a hard wire 'net connection ? With a descent connection should not take but about 20 minutes for the complete install - good hard ware - .
What is your procedure for installation ? Did you set up partitions before hand ?, set up partitions within the installer ?, allow the installer to utilize the entire disk ?
Did you verify the .iso prior to burning ?
Did you verify the disk integrity ?
Did you "try ubuntu" prior to doing the install ?
Hardware: is your machine's CPU up to snuff ? it does support pae and sse2 capabilities ?

As you can see there may be many variables, once the "core" is installed the fun begins to build the system of your dreams.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by kingcobraa on 2013-11-28
Hi. After your wired net connection question all answers are negative. I don't know what pae means. I am trying to install it on a 32gb sd card doing a minimal install.

Can you tell me what i have to do to get this working?

Been trying to get this done for ths past 6 hours with no luck each time i have to start over and end up back at the same place. Disk not being detected please select fhe correct drivers for your disk.

---

### Post by mörgæs on 2013-11-28
Please post a complete hardware description.

---

### Post by kingcobraa on 2013-11-28
Also i get the thing where it says something about iSCSI server whatever that is. Then i just tinker with it to move forward and get the message no root file system is defined.

I just want a basic ubuntu box with a gui no server no remote etc just a standalone computer.

---

### Post by kingcobraa on 2013-11-28
Running a dell 1012 mini. Ubuntu was installed on the same disk and working very well but i got rid of it due to the bloat on it meaning i wanted to customize it for my own personal taste.

---

### Post by Bashing-om on 2013-11-28
kingcobraa; Hey ,

I am on your side, I too abscribe to the simplicity of a minimal install. -> my Desktop Manager of choice is xfce4, Your choice can be different as there are scores of them available.

Maybe you have chosen to install as a server ????

Do you have a liveDVD on hand ? .. Would be nice to have a means to see what is presently on that hard disk in question, and as well have access to the utility "GParted" . We might want to consider wiping that disk and starting all over ?
As well it is crucial that the .iso file be verified:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Here is a great guide for the process of a minimal install:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

at this point stop:
> 
At the prompt, type these three commands (unfortunately, you won't be able to copy and paste into the fullscreen terminal, so please be careful to type exactly what you see here; be mindful of the spaces and spelling):

and consider what YOU WANT installed.
Run:
```

sudo apt-get update
sudo apt-get upgrade

```
For a desk top you will need xorg and some Desktop Manager (xfce4 in my case) installed:
```

sudo apt-get install xorg
sudo apt-get install xfce4

```
If you install xfce4, start the desktop with terminal command :
```

startxfce4

```
Once more consider carefully what you want installed. Differing applications are built on differing gtk-engines as well as other considerations. These can and do cause minor conflicts and may cause the installation of additional unwanted dependencies.

But for now, all we want is the "core" installed !
Verify that .iso, burn to a CD and boot it to the installer.

And we will work through the rest.
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-11-28
> **kingcobraa said:**
> Also i get the thing where it says something about iSCSI server whatever that is. Then i just tinker with it to move forward and get the message **no root file system is defined**.

This message refers to the partitioning step - it means you didn't select one of the available partitions to mount as the filesystem root (denoted by a / in the table) - you need at least that, other partitions such as a separate /home are optional.

---

### Post by kingcobraa on 2013-11-29
> **steeldriver said:**
> This message refers to the partitioning step - it means you didn't select one of the available partitions to mount as the filesystem root (denoted by a / in the table) - you need at least that, other partitions such as a separate /home are optional.


How do i accomplish part because from a livecd i formatted this card as ext4. But still get the same error meaning the iscsi part. I think the problem lies in correct partitoning? How do i partition the card correctly?

---

### Post by Bucky Ball on 2013-11-29
When you get to the partitioning part of the install you choose 'Manual Partitioning', the last on the list, and create a / and /swap partition on the SD. You should start with free space, no partitions on the SD. 

The partitioning setup is up to you: / and /swap or /, /swap and a separate /home partitoin (in the latter case / only needs to be 20Gb or so, /swap 2Gb and the rest for /home partition).

---

### Post by kingcobraa on 2013-11-29
It gets to detect disk then does not go further. I have booted to expert install now running ash. The root file system is a ram disk. hard disk systems are mounted on /target.

how to do what you suggested on command line.

---

### Post by Bucky Ball on 2013-11-29
? I have no idea what you're doing. Are you not just trying to install from a minimal install ISO on a CD? Booting from the CD?

When you boot from the CD, are you not getting to the installer? What happens exactly when you boot from the minimal install CD? 

Totally confused at this point. :-k

---

### Post by kingcobraa on 2013-11-29
I am able to boot from the cd the problem is it gives me a very long list of drivers to choose as it has not detected my sd card. This prevents me from performing the partitioning step and then completing  the rest of the setup process.

Hope this clarifies.

---

### Post by Bucky Ball on 2013-11-29
Ok. Can I presume the SD is a new one and has not been formatted yet???

If this is the case, boot to Windows and format it as whatever file system you like and see if that is then recognised by the mini install. You can then reformat it during the install process to whatever you need.

---

### Post by kingcobraa on 2013-11-29
Hi. Not new as i was running ubuntu on it until i decided to do the mini install. I don.t have windows however i have access to a live cd that runs ubuntu. Should i use start up disc creator to do the card or do i use the ubuntu disk utility to format the card and in which format mbr/nothing then ext4 etc. I can also create partitions on the target card using the disk utility i think.

---

### Post by Bucky Ball on 2013-11-29
Target card?

Boot from the LiveCD, launch Gparted and format the SD. If you are just attempting to install the minimal install to an SD card that has already been used for Ubuntu, though, I'm not sure why you're having these problems. Have you checked the mini install disk for defects? checksum #?

---

### Post by kingcobraa on 2013-11-29
yes i checked the CD for errors and the MD5sum both are clear.

no i have formatted the disk and it shows as follows: 

partition type: linux(0x83)

Partition flags : -

Type: Ext4 (version 1.0)

this is from disk utility

now from gparted

right click and shows information flags as blank also. should i change the flag type to something like boot in Gparted?

---

### Post by Bucky Ball on 2013-11-29
> **kingcobraa said:**
>  should i change the flag type to something like boot in Gparted?

No. You need to concentrate on why you can't boot the CD and install the mini ISO. What is on the disk at the moment won't matter if you are going to install a fresh mini.

---

### Post by kingcobraa on 2013-11-29
Hi,

I am able to boot the CD from my external cd-drive and the mini.iso CD installer does take me through all the menus for installation on the SD-card. 

However there is a point in the install process where I get a prompt from the installer to select the driver for my card/disk as it has not been able to detect it. This is where the problem lies and I don't know how to get around it. What can we do?

---

### Post by CharlesA on 2013-11-29
I would try installing one of the newer versions of Ubuntu, as I assume you are installing 12.04.

---

### Post by kingcobraa on 2013-11-29
Better to stick to 12.04 as it's an LTS isn't it?

---

### Post by CharlesA on 2013-11-29
> **kingcobraa said:**
> Better to stick to 12.04 as it's an LTS isn't it?

If your hardware isn't working with 12.04, it's pointless to try to stick with it.

If a newer version detects your drive and installs, you can gather more information about what type of drive controller you have.

---

### Post by kingcobraa on 2013-11-29
> **CharlesA said:**
> If your hardware isn't working with 12.04, it's pointless to try to stick with it.

If a newer version detects your drive and installs, you can gather more information about what type of drive controller you have.



Ok... now which version should i install then?

---

### Post by Bucky Ball on 2013-11-29
You are right about wanting to stick with a long support and CharlesA is right about trying a newer version to see if that works (although that doesn't solve why 12.04 is doing this and might not work anyway, but it does rule out or in whether the problem is specific to 12.04). 

My thoughts: Try 13.10, then if it does work it is a one step upgrade to the next long-term support release, 14.04 in April next year. If it doesn't work go back to the drawing board on 12.04 because the release version isn't the problem. This is probably something obscure you nut out with some persistence, but try 13.10 and see if it makes a difference.

---

### Post by kingcobraa on 2013-11-29
Okay I am downloading saucy. Let's see if it works.

---

### Post by kingcobraa on 2013-11-29
Downloaded and tried to install... it still gives the same problem of not being able to detect the disk and asks me to select a disk driver from a very long list of drivers.

In both the installers I have the option to run a shell but the problem is I don't know what to do there.

on the same card that i am trying to install ubuntu mini on now, i had  the full version of ubuntu running on it with no problems only problem being OS bloat.

is there something I can do to the card by using terminal from a working ubuntu live install?

---

### Post by CharlesA on 2013-11-29
Run this when booted off a livecd:

```
sudo lshw
```

---

### Post by kingcobraa on 2013-11-29
Hi with that command i get a long list of things. now what am i supposed to type next?

also with the failed mini install i decided to do a fresh install of ubuntu which went perfect now i am running ubuntu off the same card i tried to install the mini on so nothing wrong with the card.

---

### Post by CharlesA on 2013-11-29
The only thing I can think of is that the mini iso must be missing the drivers for your drive controller.

You can either run with the current setup or paste whatever output you got from the above command.

---

### Post by kingcobraa on 2013-11-29
hi,

thanks for responding. whatever i have removed has been replaced by xxxxxxx. hope we can fix this by mid-noon it is now about 10 am here.


```
*-scsi
          physical id: 2
          bus info: usb@1:8
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: xxxxxxx
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             size: 29GiB (31GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000eb620
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: xxxxxx
                bus info: xxxxxxxxxxxxxxxx
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
                size: 27GiB
                capacity: 27GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-11-30 01:13:53 filesystem=ext4 lastmountpoint=/ modified=2013-11-30 01:36:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-11-30 09:30:05 state=mounted
           *-volume:1
                description: Extended partition
                physical id: xxxxxxxxx
                bus info: xxxxxxxxxxxxxx
                logical name: /dev/sda2
                size: 2035MiB
                capacity: 2035MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: xxxxxxxxxxxx
                   logical name: /dev/sda5
                   capacity: 2035MiB
                   capabilities: nofs
```

---

### Post by CharlesA on 2013-11-29
You have a 32GB disk that you are installing Ubuntu on?

It looks like it is using the normal USB driver, but that shouldn't be a problem.

---

### Post by Bucky Ball on 2013-11-29
> **CharlesA said:**
> 

It looks like it is using the normal USB driver, but that shouldn't be a problem.

That's what I've been thinking. An anomaly. :-k 

@kingcobraa: That has ruled out the problem being specific to 12.04 LTS so feel free to go back to installing that if you want long-term support (13.10 support ends next July). Has nothing to do with it. ;)

---

### Post by kingcobraa on 2013-11-30
So now what can I do? I did a full install of 12.04 with no problems.

The problem is I don't want a full install.

I want the mini.iso installed on my card and since we have identified the problem what can we do to ensure that the mini is installed successfully on the card/disk?

---

### Post by Bucky Ball on 2013-11-30
No idea or we would obviously be telling you. That is what we're trying to work out and at the moment have no clues. Obviously something is missing from the mini iso that is on the regular install disk. :-k

---

### Post by kingcobraa on 2013-11-30
The mini installer does allow me to run shell commands using something that looks and probably operates like terminal hence would't it be possible to run some command that allows me to fix the driver issue?

Additionally the installer gives me the option of installing the drivers from other media as well.

Would doing any of this prove helpful?

---

### Post by Bucky Ball on 2013-11-30
> **kingcobraa said:**
> The mini installer does allow me to run shell commands using something that looks and probably operates like terminal hence would't it be possible to run some command that allows me to fix the driver issue?

Exactly what I've just been looking into.

> **kingcobraa said:**
> Additionally the installer gives me the option of installing the drivers from other media as well.


Install the drivers from the other media then! :-k

Also, if that doesn't work, tell us the *exact* error message you're getting. Write it down if you have to. ;)

---

### Post by kingcobraa on 2013-11-30
Install the drivers from the other media then! :-k

Also, if that doesn't work, tell us the *exact* error message you're getting. Write it down if you have to. ;)[/QUOTE]


I mentioned what the installer makes possible but then solving the problem would be easy since we know now what it is, however very detailed steps would be very useful in this case.

I am willing to try this because even though I attempted to install the mini again then had no choice but to abort it right after doing the full install on the card. Good thing is that I was still able to restart the computer right after and it did not affect my full installation meaning i was able to boot like normal.

---

### Post by Bucky Ball on 2013-11-30
So you have mini installed?

A mini install doesn't just install then it's up and running, you need to install EVERYTHING other than the kernel. All apps, etc. When the computer reboots, are you at a large terminal and connected to the net? That is where you need to put in your apt-get install line, for instance:

```
sudo apt-get install xfce4 synaptics firefox
```

... and whatever else you are going to need/want. Just add them to the end of that line (vlc thunderbird gparted, whatever).

---

### Post by kingcobraa on 2013-11-30
> **Bucky Ball said:**
> So you have mini installed?

A mini install doesn't just install then it's up and running, you need to install EVERYTHING other than the kernel. All apps, etc. When the computer reboots, are you at a large terminal and connected to the net? That is where you need to put in your apt-get install line, for instance:

```
sudo apt-get install xfce4 synaptics firefox
```

... and whatever else you are going to need/want. Just add them to the end of that line (vlc thunderbird gparted, whatever).


No mini is not installed the reason is that it did not detect my disk hence no files were installed and I had to abort the installation. I rebooted and it went straight to the normal full/fresh install which i had done just before it... in other words files were unaffected.

---

### Post by Bucky Ball on 2013-11-30
So you have the regular 12.04 installed and when you go through the mini iso install, get to the partitioning section and hit 'manual install' it doesn't recognise the SD card and doesn't see the regular Ubuntu install you have on there or the partitions it created?

---

### Post by mikewhatever on 2013-11-30
You could install the mini ISO on an HDD partition (same size as the card), and then use dd to copy the installation to the SD card. You'll likely need to reinstall GRUB, wich is [easily done]("https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal") from a Live CD/USB.

PS: Going back to the original question, ...why do you think (or rather feel) there is stuff in Ubuntu, you don't want? People can write a lot and very convincingly, but not all is necessarily true. In fact, I'll go as far as to say that much of what's written about Ubuntu on the web is nonsense. ;)
To put it another way, ...what exactly do you require from an Ubuntu instllation?

---

### Post by Bucky Ball on 2013-11-30
> **mikewhatever said:**
> 
PS: Going back to the original question, ...why do you think (or rather feel) there is stuff in Ubuntu, you don't want? People can write a lot and very convincingly, but not all is necessarily true. In fact, I'll go as far as to say that much of what's written about Ubuntu on the web is nonsense. ;)
To put it another way, ...what exactly do you require from an Ubuntu instllation?

Interesting but off-topic. The OP is after a minimal install and can't get it working on the SD. 

I would give the DD option a shot though, failing anything else working, because I'm unsure why this is not working if a regular 12.04 can be installed but the min iso can't. All I can think of is the SD is missing drivers for the SD card where as the desktop 12.04 ISO is not.

---

### Post by mikewhatever on 2013-11-30
> **Bucky Ball said:**
> Interesting but off-topic. The OP is after a minimal install and can't get it working on the SD. 
Well, as the title indicates, the OP wasn't originally after a minimal install, but rather after some down-trimming. Given the minimal ISO installation on an SD card is a no-go, perhaps the OP would like to go back and explore the original idea. I have some experience with that, and could help.
> 
I would give the DD option a shot though, failing anything else working, because I'm unsure why this is not working if a regular 12.04 can be installed but the min iso can't. All I can think of is the SD is missing drivers for the SD card where as the desktop 12.04 ISO is not.
You are probably right. The mini ISO likely doesn't have all the drivers that the full kernel on a live CD has. Perhaps the [Alternate ISO]("http://old-releases.ubuntu.com/releases/xubuntu/releases/precise/release/xubuntu-12.04.2-alternate-i386.iso") could help. There is an option to install the command line system there.

---

### Post by kingcobraa on 2013-11-30
where scsi is concerned. i again tried to do the installation and each time with 12.04 it takes me about 1 hour to get to the drive detection and selection screen. I was able to successfully reach the partition manager this time which I was not able to do in previous attempts but there was 1 problem.

I did not know which one of these to select for my card hence just selected the last one (scsi_debug). It came back with the size of 8MB and I just moved forward then the partition manager gave me the message that the partition size is too small, I tried to exit and see if a re-detection is possible but it was not hence I aborted the installation, rebooted with the same card and now have come back to report my findings.

Which one of these is the correct one??

scsi_transport_sas

scsi_transport_fc

scsi_tgt

scsi_dh_rdac

scsi_dh_hp_sw

scsi_dh_alua

scsi_debug

---

### Post by Bucky Ball on 2013-11-30
So you are getting to the screen in my attachment, choosing 'manual', the last selection, and this is the selection of partitions you are getting?

scsi_transport_sas

scsi_transport_fc

scsi_tgt

scsi_dh_rdac

scsi_dh_hp_sw

scsi_dh_alua

scsi_debug

---

### Post by kingcobraa on 2013-11-30
no.

it first does the disc detection, then tells me it cannot find the driver and to select from a list of maybe 50 different types of disc drivers but since mine appears to sit in as a scsi as per the checks and post i made a few hours ago, then I selected through only those that were related to scsi, i selected the debug one and then if i remember correctly it took me to a screen similar to the one you have posted only that i chose guided-use entire disk however it only displayed the disc size as 8MB, once i selected that it gave me an error on the next screen saying that my disc size is too small to hold the install files. i had no choice but to abort the installation.

---

### Post by vasa1 on 2013-11-30
> **mikewhatever said:**
> Well, as the title indicates, the OP wasn't originally after a minimal install, but rather after some **down-trimming**. Given the minimal ISO installation on an SD card is a no-go, perhaps the OP would like to go back and explore the original idea. **I have some experience with that, and could help**.
...
If you write up a tutorial on that I'd certainly read it :)

---

### Post by kingcobraa on 2013-12-01
Hi, I was very busy yesterday hence was not able to post anything.

An idea that may solve the problem.

When a hard disc is not being detected by the installer then it signifies that the disk is not mounted at the time of starting the installation or at the required time during the installation.

The key is that I can execute a shell or something like that from within the installer.

What can be done to make the installer recognise and then MOUNT the disc so that the mini can proceed with the installation like normal?

---

### Post by Bucky Ball on 2013-12-01
The disk will be /dev/sda*, where * is a number, say sda5. You could try:

```
sudo mount /dev/sda*
```

... replacing sda* with the correct details. Don't think this is the problem, but give it a go anyway. ;)

---

### Post by kingcobraa on 2013-12-01
hi it did not work.

it gave me some fstab message

when i tried to get into it then it gave me the permission denied error.

now do you remember that when we used to make floppy boot disks for windows, we had to copy over a lot of files to make sure the system would detect the floppy disk and then boot etc.

I think it is the same where the installer does everything in RAM like detecting the disc etc, once the disc is detected only then does the base system install on the disk.

Can we do something similar on a formatted disc?

*Key* we need to verify if this will work before we attempt  to format the disc and the installer bit because it takes 1 hour to get to the point where it tries to detect the disk.

---

### Post by steeldriver on 2013-12-01
Are you sure it's SCSI drivers that are involved? I had a play with my Thinkpad and it looks like the SD card / subsystem has its own modules

```

$ lsmod | grep sdhci
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
$ 
$ modinfo sdhci
filename:       /lib/modules/3.2.0-56-generic-pae/kernel/drivers/mmc/host/sdhci.ko
license:        GPL
description:    Secure Digital Host Controller Interface core driver
author:         Pierre Ossman <pierre@ossman.eu>
srcversion:     8D9FD806174D04BE764F9D9
depends:        
intree:         Y
vermagic:       3.2.0-56-generic-pae SMP mod_unload modversions 686 
parm:           debug_quirks:Force certain quirks. (uint)
parm:           debug_quirks2:Force certain other quirks. (uint)
$ 

```

For me, it appears (via udev I think) as /dev/**mmcblk0**

```

$ sudo parted /dev/mmcblk0 print
Model: SD SU32G (sd/mmc)
Disk /dev/mmcblk0: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  31.9GB  31.9GB  primary  fat32        lba

```

Are sdhci / sdhci_pci in the long list of drivers it asks you to choose from? if so maybe that's what you should try - or if you can get to a shell prompt,

```
modprobe -v sdhci
```

---

### Post by kingcobraa on 2013-12-01
Are sdhci / sdhci_pci in the long list of drivers it asks you to choose from? if so maybe that's what you should try - or if you can get to a shell prompt,

```
modprobe -v sdhci
```[/QUOTE]

Hi, no this specific set of drivers that you mention above are not in the list. I provided the names of the drivers in the list a few posts back.

Is there a list of commands that I can try in shell prompt that would help to identify the required information and a command that will help me to download the driver for the card from the minimal iso shell prompt itself.?

---

### Post by kingcobraa on 2013-12-01
Yesterday I was doing some tinkering and then in shell prompt it gave the message that my card is listed as sg0.

Also  what happened yesterday is that I downloaded netbootin downloaded the  net install for pangolin, put the set-up files on my card, restarted the  machine wtith no optical drive connected, it booted from the card and  went through the installer took about 1 hour to download the updates,  when i got to the detect disk part i selected buslogic just to see what  would happen and still it did not work.
Now when i insert the card to  boot it boots to the netbootin prompt and gives the option to proceed  with various components of the install but the part to select the disks  is not there now... 

The thing is that yesterday the machine  booted from files on the card BUT it did not install the disc drivers  automatically and gave me the the scsi option of which I just selected  the buslogic option.

Possibly a manual install of the correct drivers is required.

Is  there some way that I can download and burn on a disc ALL the possible  scsi drivers that exist and then transfer them from CD to the card using  the "Ash prompt" and then let the installer detect and install the  correct drivers automatically?

Also I plugged in the card into  the card slot and I am able to view the folders/files on the card, maybe  it is possible to do some editing/manipulation of the files but don't  know how to do this.

---

### Post by kingcobraa on 2013-12-02
I tried to install using the alternate CD and you will not believe it but even the alternate CD has a driver problem.

Only choice is to install Ubuntu desktop edition and strip it down naked without breaking the system.

Are  there willing people that can help the die hard Ubuntu fans like myself  to strip down Ubuntu desktop edition just so that we have no software  or services installed on it except for the most basic OS boot files and  OS services, OS dependencies, the basic unity desktop environment,  firefox, chrome, synaptic, Gdebi and UFW.

We only need synaptic and gdebi just in case.

I think this way of dealing with Ubuntu will be more successful and most rewarding.

I  have installed mostly this mini and the alternate CD and the clean  install so many times anyone would get frustrated and run to another OS  variant but I am not angry or annoyed, I just feel like I was rewarded a  body of knowledge and have started to develop a new hobby. ;)

You guys with me?

---

