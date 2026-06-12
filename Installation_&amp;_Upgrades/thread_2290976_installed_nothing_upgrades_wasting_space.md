---
title: "installed nothing upgrades wasting space?"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by Sandgoose on 2015-08-17
my laptop has the following setup

16gb SSD
128GB USB

I partitioned the following

SSD 15GB /
SSD 1gb swap

USB 128GB fat32

the only program I have installed was VLC

the only programs I use are transmission/firefox and vlc and I have transmission writing anything it downloads to USB, firefox is set to only cache so much.

I manually run a script to download and build the kernel drivers every time theres an update because my hardware isn't officially supported (all this is one in /tmp)

it has got to the point where I don't have enough room to rebuild the kernel without it failing (99% usage), so I deleted a bunch of the old kernels and it it working but Im still over 90% usage that can't be correct? looking for a solution...

thinking a reinstall would help but Id be back to square one eventually and running out of space.

1/any suggestions on how I can reclaim or free up a lot of space because 15gb for an os seems a lot? (considering the installation media is 800mb image)

2/should I go to a smaller/lighter distro considering the limited programs I use?

3/should I look into reinstalling and splitting the distro between the ssd and the flash also how would I go about doing that? is it possible to move without reinstalling, can any issues arrise from being installed (partially or fully) on usb ?

thanks

---

### Post by v3.xx on 2015-08-17
Have you tried to free up any space with the autoremove command?
```
sudo apt-get autoremove
```
also could try
```
sudo apt-get autoclean
```
And check usage with
```
df -h
```

---

### Post by Sandgoose on 2015-08-17
thanks that cleared up 1% but im curious what is consuming the rest, I have the live image installed on usb that runs fine and its only a 2gb flash drive wondering what's eating the other 9gb?

---

### Post by howefield on 2015-08-17
Did you run the command ?

```
df -h
```

---

### Post by v3.xx on 2015-08-17
You could also look for large files.

[https://help.ubuntu.com/community/RecoverLostDiskSpace#find_.28Find.29](https://help.ubuntu.com/community/RecoverLostDiskSpace#find_.28Find.29)

---

### Post by Sandgoose on 2015-08-17
"Did you run the command ?"
yep. before and after, it tells me ubuntu is using 11G and from before/after I freed up 1% with the apt commands

largest folders are lib and usr both weighing in over 4 gig each, there dosn't seem to be any single large files that I can see

---

### Post by grahammechanical on 2015-08-17
The size of the installation media is irrelevant. Before the installation begins the installer asks us to check that there is suffient disk space available and the install sets a minimum size of about 6 - 8 GB. So, the 800MB of the install media contains compressed files. Do you have large data files? and are they stored on the 15GB partition?

There is nothing stopping you removing applications that you will never use such as games. Libreoffice Impress is included by default. Do you use presentation files? If not remove Impress. I am giving you an example of how to create space. VLC may be the only appplication that you have installed but where do you keep the audio and visual files that you are using VLC to play? Those kinds of files can take up a lot of space.

Regards

---

### Post by flocculant on 2015-08-17
> Libreoffice Impress is included by default. This is Xubuntu. The only LO stuff we seed are Calc and Writer as drop ins for Abiword and Gnumeric.

The issue here is for sure either a ~/ one or post-install installations. 

>  VLC may be the only appplication that you have installed but where do you keep the audio and visual files that you are using VLC to play? This is probably more likely :)

~/Music or ~/Videos

time will tell when the OP gets back with some real data about folder sizes.

> lib and usr both weighing in over 4 gig each,

lib on a massively mucked about with dev version of Xubuntu gives me 545Mb - so ~4GB is not normal.

at OP

run 

```
sudo find /lib -name '*' -size +500M
```

Give us the whole terminal output.

IF nothing else it will sort out if /lib is really massive.

---

### Post by Sandgoose on 2015-08-17
"his is probably more likely :smile:

~/Music or ~/Videos"

all the videos on the device are installed on the fat32 flash drive

"Give us the whole terminal output."
output is empty

---

### Post by Sandgoose on 2015-08-17
oh ... /lib/modules has a copy of modules for every single kernel version that has been installed

down to 61% usage, libs down to 358mb, anyway to automate this process ? anything else I should look into deleting ? I see no reason why it should need to automatically archive that much junk :S

---

