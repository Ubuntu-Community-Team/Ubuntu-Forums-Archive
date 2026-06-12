---
title: "System Thrashed after Hardy Install"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by oxman on 2008-07-05
Thank you for your attention.

I am on dialup using and AMD_64 X2 opteron with asus MB and 2 gigs ram. NVIDIA 6800gto and Audigy2 Sound Blaster. gnome ubuntu

I was running Dapper_64 on one drive (totally up to date and running smooth) and Gutsy on the other. I did a clean install of Hardy_32 on the Gutsy drive, drove 30 miles to the local ISP and did an update/upgrade of Hardy. My entire system is hosed. Xserver is locking up on both drives and I am unable to install my NVIDIA drivers for either distro.

I am unable to compile the drivers on the Dapper version which I think will fix the problem? It keeps asking for kernal dev in order to compile and shuts down.

The Hardy drive also mounts the Dapper partitions as SDA1 and SDA2 and I think the upgrade hosed some of the packages on the Dapper SDA1???. I had NVIDIA drivers working fine on it until I installed Hardy and attempted to install NVIDIA drivers.

Any help is greatly appreciated.

---

### Post by unutbu on 2008-07-05
I'm sorry to hear of your problem. I find it most surprising that upgrading to Hardy might have messed with the sda1, sda2 (dapper) partitions.

I'm not sure if I can help you, but here are some thoughts:

The command
```
sudo find /  -mmin -60 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' 
```
will show you all the files on your system that have been modified in the last 60 minutes. If you boot into Dapper's Recovery Mode, perhaps you can run this command to see what has changed. Change 60 to whatever is appropriate.

```
sudo find /  -mmin -60 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' > changed-files
```
will save the results to the file changed-files. It may come in handy later.

You may also want to find out what packages have been installed on Dapper and/or Hardy most recently:
```
cat /var/log/dpkg.log | grep install[^e] | tail -n100 
``` will show you the last 100 packages to have been installed.

When you upgraded to Hardy, Hardy may have written a new GRUB menu.lst. Maybe when you think you are booting Dapper, perhaps you are really getting Hardy. It seems possible to me that nothing has changed on your Dapper partitions, and perhaps we just need to figure out how to get it to boot. Do you think that might be the case? It would be helpful if you know where GRUB has been installed, and if you use Dapper's menu.lst or Hardy's menu.lst to boot.

If you think that GRUB is the problem, here are instructions on how to re-install GRUB from a LiveCD (any Ubuntu LiveCD will do).

[http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

---

### Post by oxman on 2008-07-05
Thank you very much for your reply. It is greatly appreciated.

Dapper:

I'm gaining ground. :) I have installed the headers for Dapper and have attempted to compile the Nvidia drivers. X still refuses to load on boot. I've managed to get to a prompt on the Dapper_64 and I am looking at the xorg.conf to make sure everything is as it should be. Not sure what I am looking for???

I do notice that my Modules section doesn't show to load nvidia drivers just glx???

Hardy:

I did the update on the system last Wednesday and I have been wrestling around in there with it since so I'm not sure if that would help but I will look.

I am certain it is not a Grub problem since uname -r gives me what kernal I am using. Hardy is 32 bit and Dapper is 64.

When I drop to a prompt in Hardy before my desktop freezes I am shown the curser after a message concerning running a local boot script???? Would that be a grub problem?  I am accessing the prompt by xterm then sudo /etc/init.d/gdm stop  ???

I hope this doesn't sound too confusing.

---

### Post by unutbu on 2008-07-05
Ok, let's work on getting Dapper fixed since (1) it seems a little less mysterious and (2) I think you'll feel a lot more comfortable when you get your main system working again.

Please post your /etc/X11/xorg.conf

Also 
```

lsmod | grep nvidia
```

might help to show if the nvidia driver has been successfully inserted into the kernel.
The output should look something like

```
% lsmod | grep nvidia
nvidia               6221648  24 
i2c_core               26112  3 it87,i2c_isa,nvidia
agpgart                35016  2 nvidia,intel_agp

```
If lsmod does not show your nvidia driver installed, please post a link to the tar.gz for the driver you have installed, and a description of what commands you have issued (e.g. ./configure, make, sudo make install...)

Finally, please post
```
lspci -nn
```
as this will show not only the name of your card (which we already know to be nvidia GeForce 6800 GTO) but also the hardware id [xxxx:xxxx]. This number might be useful for google searches.

There is a thread 
[http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313)
where people post how they got their nvidia cards working, and there are a bunch of reports for 6800's , but none that I found for 6800 GTO. I'm hoping if I search by hardware id something might come up...

---

### Post by oxman on 2008-07-05
These are my results. I wasn't expecting the long string but post it to you here:

```

lsmod | grep nvidia

nvidia   4572640 0


lspci -nn

0000:00:00.0 0580: 10de:005e
0000:00:01.0 0601: 10de:0050
0000:00:01.1 0c05: 10de:0052
0000:00:02.0 0c03: 10de:005a
0000:00:02.1 0c03: 10de:005b
0000:00:06.0 0101: 10de:0053
0000:00:07.0 0101: 10de:0054
0000:00:08.0 0101: 10de:0055
0000:00:09.0 0604: 10de:005c
0000:00:0a.0 0680: 10de:0057
0000:00:0b.0 0604: 10de:005d
0000:00:0c.0 0604: 10de:005d
0000:00:0d.0 0604: 10de:005d
0000:00:0e.0 0604: 10de:005d
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:01:00.0 0300: 10de:0291
0000:05:07.0 0401: 1102:0004
0000:05:07.1 0980: 1102:7003
0000:05:07.2 0c00: 1102:4001
0000:05:0c.0 0200: 11ab:4320

```

---

### Post by unutbu on 2008-07-05
Your lspci -nn looks different than mine. (No words!)
Please post

```
lspci -nnvv
```

Attached is a sample xorg.conf which works for an 6800 XT video card. Perhaps it, or something similar will work for you too.

(I'm not sure about the
```

	Option		"AddARGBGLXVisuals"	"True"
```

line. You might want to comment that line out to begin with. Also, change the Modeline so the top choice matches the capabilities of your monitor.)

PS. Could it be that you have a 
GeForce 7900 GT/GTO? (See [http://pci-ids.ucw.cz/iii/?i=10de0291](http://pci-ids.ucw.cz/iii/?i=10de0291))

---

### Post by oxman on 2008-07-06
When I do lspci -nnvv there is a huge verbose display far to large for me to read.

My mistake. You are correct it is a 7900gto

This is the driver I downloaded and installed from the Nvidia site: Latest Version: [173.14.09]("http://www.nvidia.com/object/linux_display_amd64_173.14.09.html")

I will have to take up the project again tomorrow after work. It is late here and the sun rises early. Plus my old brain is fried 
:)

Again let me express my gratitude. If you get a brainstorm feel free. I'll check back here in the A.M .

Blessings upon you.

---

### Post by unutbu on 2008-07-06
It appears that it is best to remove any old NVIDIA drivers before trying to install new ones.
See
[http://ubuntuforums.org/showpost.php?p=5246486&postcount=450](http://ubuntuforums.org/showpost.php?p=5246486&postcount=450)

I think the spirit of gwillem's post is correct, but his boxed command may be wrong. Boot Dapper in recovery mode, then try

```

ls -l /lib/modules/`uname -r`/kernel/drivers/video/nvidia*  # To take a look at what you're moving, if anything
mv /lib/modules/`uname -r`/kernel/drivers/video/nvidia* /root
```
instead.

Then run ```

cd /path/to/NVIDIA-Linux-x86_64-173.14.09-pkg2.run  
sudo ./NVIDIA-Linux-x86_64-173.14.09-pkg2.run
```
to install the new driver.

I think you can then try to restart the X server with
```

sudo /etc/init.d/gdm start
```

If it works, wait a week and then you can remove the old nvidia drivers that you had moved to /root.

---

### Post by oxman on 2008-07-07
Thank you unutbu but no joy.

Here's the installer message:
```

Utility "runlevel" failed to run

Installer forced to guess the X library path '/usr/lib/' and the X module path '/usr/lib/xorg/modules'

If x fails to find the nvidia driver module please install 'pkg-config' utility and the x.org sdk/development package for your distribution and reinstall the driver.

```

---

### Post by unutbu on 2008-07-07
oxman, I really feel for your situation and wish that I could help. However, I'm also concerned that I might tell you something which is wrong (or more wrong than I have already been). 

I've been searching and found a description of how to install the NVIDIA driver here:
aktiwers [http://ubuntuforums.org/showpost.php?p=4105735&postcount=4](http://ubuntuforums.org/showpost.php?p=4105735&postcount=4)
and here:
cresho [http://ubuntuforums.org/showpost.php?p=5317396&postcount=10](http://ubuntuforums.org/showpost.php?p=5317396&postcount=10)

but I'm afraid to tell you what to do for fear I might be leading you on a wild goose chase.

I hope this message will bump this thread and bring some fresh eyes to the problem. Best wishes, and good luck.

---

### Post by oxman on 2008-07-07
Thanks again sir. Your efforts have appreciated.

I finally caved and reinstalled Hardy. I have a functioning work space at least (I was getting way behind)

But I will continue to restore my once wonderfully functionind Dapper. 

Just for the record. My Hardy install mounts /sda1 and /sda2 when it boots (allows me to access files on that drive easily). I have never had any problem with that set up before. 

Again, my gratitude sir.

---

