---
title: "nVidia Drivers"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by Prudentissimus on 2005-06-29
Hi,

  What KERNEL SOURCE is nVidia's Graphics/nForce Drivers asking when installing them? Where can I obtain the latest compatible version of this KERNEL SOURCE with Hoary?

-Regards
-Tom

---

### Post by frodon on 2005-06-29
try that to install nvidia drivers and post messages if it doesn't work (but most of the time it will) : [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver)

---

### Post by Prudentissimus on 2005-06-29
[QUOTE=frodon]try that to install nvidia drivers and post messages if it doesn't work (but most of the time it will) : [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver)[/QUOTE]
 I am installing it from the *.deb file I got from NVIDIA.com

Not from web, I have no Internet connection on the linux system.

---

### Post by DarkKnight on 2005-06-29
I downloaded the new nvidia drivers, the Ubuntu kernel source, and tried running it... I still got told I had no kernel source.

When I told it where to find the source, it told me there where no kernel sources there.

I'm using the NVIDIA-Linux-x86-1.0-7664-pkg1.run

---

### Post by Prudentissimus on 2005-06-29
[QUOTE=DarkKnight]I downloaded the new nvidia drivers, the Ubuntu kernel source, and tried running it... I still got told I had no kernel source.

When I told it where to find the source, it told me there where no kernel sources there.

I'm using the NVIDIA-Linux-x86-1.0-7664-pkg1.run[/QUOTE]
 Yea this is BS... I hate this.. glxgears wont work for me either.

---

### Post by trivialpackets on 2005-06-29
[QUOTE=Prudentissimus]Yea this is BS... I hate this.. glxgears wont work for me either.[/QUOTE]
 GLX gears likely won't without 3d rendering, and if it did it would do so poorly.  I am using an HP notebook, I used the steps located on ubuntuguide.org.  It installed fine.  To make it work correctly with the wide screen, it took some other configuring, but it was fine overall using this method.  Have you tried this as these drivers were fine for me.

---

### Post by Prudentissimus on 2005-06-29
[QUOTE=eric.proctor]GLX gears likely won't without 3d rendering, and if it did it would do so poorly.  I am using an HP notebook, I used the steps located on ubuntuguide.org.  It installed fine.  To make it work correctly with the wide screen, it took some other configuring, but it was fine overall using this method.  Have you tried this as these drivers were fine for me.[/QUOTE]
 did you have internet on your linux?

---

### Post by Drain on 2005-06-30
it's pretty difficult to install a lot of software without Internet, on just about any linux system. One of the best things about Ubuntu is that once you've got it configured, a lot of software is available by typing "apt-get install (whatever)", and it downloads it and installs the program, plus any smaller programs that the program might need. 

I've followed the directions here: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
And installed the nvidia drivers on 3 computers in a heartbeat. But if you're going a different route...

It sounds like what you're looking for is the kernel source - if you had internet on this computer, you could just "apt-get install kernel-source-2.6.10" (the default kernel, I believe), and it would download the large 30MB file, and install itself (assuming it doesn't need anything else), and then you could install the nvidia drivers you have that are requesting the kernel sources. It sounds like you'll have to hop on an internet-connected computer, burn a CD with the right .deb files, and then take the CD to your computer, and use "dpkg -i " on the appropriate .deb file you've got. It could get pretty complicated. Good luck.

---

### Post by Prudentissimus on 2005-06-30
[QUOTE=Drain]it's pretty difficult to install a lot of software without Internet, on just about any linux system. One of the best things about Ubuntu is that once you've got it configured, a lot of software is available by typing "apt-get install (whatever)", and it downloads it and installs the program, plus any smaller programs that the program might need. 

I've followed the directions here: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
And installed the nvidia drivers on 3 computers in a heartbeat. But if you're going a different route...

It sounds like what you're looking for is the kernel source - if you had internet on this computer, you could just "apt-get install kernel-source-2.6.10" (the default kernel, I believe), and it would download the large 30MB file, and install itself (assuming it doesn't need anything else), and then you could install the nvidia drivers you have that are requesting the kernel sources. It sounds like you'll have to hop on an internet-connected computer, burn a CD with the right .deb files, and then take the CD to your computer, and use "dpkg -i " on the appropriate .deb file you've got. It could get pretty complicated. Good luck.[/QUOTE]
 Does "Kernel Source" come default with Hoary?

I have some Kernel 2.6 I think, but still nVidia says cannot find Kernel Source ...

What path is Kernel Source in???

---

### Post by Drain on 2005-07-02
I'm pretty sure it's not installed by default, but that it is somewhere in the Hoary repository - I forget how it's organized - Good luck looking.

---

### Post by Lunde on 2005-07-02
[QUOTE=DarkKnight]I downloaded the new nvidia drivers, the Ubuntu kernel source, and tried running it... I still got told I had no kernel source.

When I told it where to find the source, it told me there where no kernel sources there.

I'm using the NVIDIA-Linux-x86-1.0-7664-pkg1.run[/QUOTE]
 $ sudo apt-get install linux-headers-`uname -r`

---

### Post by Prudentissimus on 2005-07-02
[QUOTE=Lunde]$ sudo apt-get install linux-headers-`uname -r`[/QUOTE]
 I do not have internet to use apt-get.

I have linux-headers 2.6...

---

### Post by Lunde on 2005-07-02
[QUOTE=Prudentissimus]I do not have internet to use apt-get.

I have linux-headers 2.6...[/QUOTE]
 OK, no problem.
**$ uname -r**
The output form this is somthing like 2.6.10-5-686

Open Synaptics and install the packet: 
**linux-headers-2.6.10-5-686 **
Change the numbers with the output of uname -r

---

### Post by Prudentissimus on 2005-07-02
[QUOTE=Lunde]OK, no problem.
**$ uname -r**
The output form this is somthing like 2.6.10-5-686

Open Synaptics and install the packet: 
**linux-headers-2.6.10-5-686 **
Change the numbers with the output of uname -r[/QUOTE]
 but synamptic says it is already installed...

---

### Post by Xian on 2005-07-02
[QUOTE=Prudentissimus]I have some Kernel 2.6 I think, but still nVidia says cannot find Kernel Source ...

What path is Kernel Source in???[/QUOTE]
You have the 2.6 _precompiled_ kernel, but probably not the kernel source.
The path is /urs/src.

You'd want something like the output below.
Notice the tarred linux source file, source folder, and symlink named linux.
```
$ ls /usr/src
linux  linux-patches  linux-source-2.6.10  linux-source-2.6.10.tar.bz2  rpm
```

---

### Post by Prudentissimus on 2005-07-02
[QUOTE=Xian]You have the 2.6 _precompiled_ kernel, but probably not the kernel source.
The path is /urs/src.

You'd want something like the output below.
Notice the tarred linux source file, source folder, and symlink named linux.
```
$ ls /usr/src
linux  linux-patches  linux-source-2.6.10  linux-source-2.6.10.tar.bz2  rpm
```[/QUOTE]
 ```

$ ls /usr/src
nvidia-kernel-source.tar.gz  rpm

```

That is what I have.

---

### Post by Xian on 2005-07-02
[QUOTE=Prudentissimus]```

$ ls /usr/src
nvidia-kernel-source.tar.gz  rpm

```

That is what I have.[/QUOTE]
Yes, that is what I expected.
You will not get the nVidia driver installed without the kernel source pkg.

---

### Post by Lunde on 2005-07-02
[QUOTE=Prudentissimus]```

$ ls /usr/src
nvidia-kernel-source.tar.gz  rpm

```

That is what I have.[/QUOTE]
 Is it the 7664 you are going for?
if so, you need the **build-essential** packet in synaptics and the headers as I described above.

For a Howto for doing this check this out:
[http://www.ubuntuforums.org/showthread.php?postid=214636#post214636](http://www.ubuntuforums.org/showthread.php?postid=214636#post214636)

Be ready to role back the driver or back up your system first, there are a lot of known bugs with this driver. Some people are reportng success, so you may be one of the lucky ones.

---

### Post by darkpark on 2005-07-04
mayhaps you're not selecting the correct platform?   if you have an nforce2 (your signature indicates that you do) than you should be using the k7 platform for the kernel headers.  of course, if you installed from a regular CD than it might have went with the i386 kernel.  i used the dvd install which gave me the K7 (amd duron/athlon support)  kernel.

---

### Post by Lunde on 2005-07-04
[QUOTE=darkpark]mayhaps you're not selecting the correct platform?   if you have an nforce2 (your signature indicates that you do) than you should be using the k7 platform for the kernel headers.  of course, if you installed from a regular CD than it might have went with the i386 kernel.  i used the dvd install which gave me the K7 (amd duron/athlon support)  kernel.[/QUOTE]
 It might be better to go for the correct kernel, but make sure to do a system / configuration backup first. There is a lot of people having problems after kernel upgrades in this forum.

Nice howto for a configuration backup here:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=Lunde]It might be better to go for the correct kernel, but make sure to do a system / configuration backup first. There is a lot of people having problems after kernel upgrades in this forum.

Nice howto for a configuration backup here:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)[/QUOTE]
 sigh never knew installing NVIDIA drivers could be such pain

---

### Post by Lunde on 2005-07-04
[QUOTE=Prudentissimus]sigh never knew installing NVIDIA drivers could be such pain[/QUOTE]
 Why not just use the Ubuntu Nvidia Drivers from synaptics? Not much bugs there, and that will be done in about 5min

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=Lunde]Why not just use the Ubuntu Nvidia Drivers from synaptics? Not much bugs there, and that will be done in about 5min[/QUOTE]
 nvidia-glx? or something else??

---

### Post by Lunde on 2005-07-04
[QUOTE=Prudentissimus]nvidia-glx? or something else??[/QUOTE]
 There are some small changes you need to do to enable glx

There's a howto here:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by Lunde on 2005-07-04
Then check your frame rate with:
**$ glxgears**

---

### Post by t2kburl on 2005-07-05
you may try spcifying the kernel path for the nvidia installer ( see its README for exactly how )

my path is /usr/src/linux-headers-2.6.10-5-686/

it may need /usr/src/linux-headers-2.6.10-5-686/include

be sure you remove all nvidia packages and kernel-restricted-modules for your kernel in synaptic prior to running the nvidia installer

and make a backup of your working xorg.conf in case you get the dreaded black screen

---

### Post by codejunkie on 2005-07-05
[QUOTE=Prudentissimus]sigh never knew installing NVIDIA drivers could be such pain[/QUOTE]

you have to have the kernel headers package plus the the build-essential package installed it provides the compilers and such for the nvidia installer to build the kernel module here's the steps from a guide i wrote to install the nvidia driver from scratch hope this helps you out.

find what kernel is listed when you type ```
uname -a
``` at the terminal for example mine displays ```
Linux ubuntu [COLOR=Red]2.6.10-5-k7[/COLOR] #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux
``` what l've listed in red is what to look at so  on mine i need the kernel headers for the k7 kernel. the easiest way to install these is using synaptic click on search and type headers it will list all the header packages avaliable so i install the package linux-headers-k7 these are the ones for my kernel. if you have a different kernel for example 2.6.10-5-386 you will need the package linux-headers-386 etc. you also need the build-essential package installed this provides the basic compilers and stuff used to build the kernel modules. if you can't get X running to use synaptic you can also install the kernel headers and build essential package like this. 
```
sudo apt-get update
sudo apt-get install linux-headers-386 
sudo apt-get install build-essential
```
for this example im using the 2.6.10-5-386 kernel because it's what ubuntu installs by default and the NVIDIA-Linux-x86-1.0-7667-pkg1.run nvidia driver from [www.nvidia.com](www.nvidia.com).

now to install the driver if your already in an x session exit it by hitting
```
ctrl+alt+F1
```
now at the terminal login and type:
```
sudo -s
```
enter you password 
```
telinit 3
```
if your using ubuntu
```
killall gdm
```
if your using kubuntu
```
killall kdm
```
cd to where the nvidia package is installed in this example i've placed it in /home/username/
```
cd /home/username
```
now run the installer with
```
sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```
after the installer has finished completely you need to edit your /etc/X11/xorg.conf
file and tell it to use the nvidia driver with.
```
nano /etc/X11/xorg.conf
```
example: find the line that looks like this
```

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        [COLOR=Red]Driver[/COLOR]          [COLOR=Blue]"vesa"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

```
and replace whatever is listed under the [COLOR=Red]Driver[/COLOR] section with [COLOR=Blue]"nvidia"[/COLOR] save the /etc/X11/xorg.conf file and reboot.

---

### Post by Prudentissimus on 2005-07-05
[QUOTE=codejunkie]you have to have the kernel headers package plus the the build-essential package installed it provides the compilers and such for the nvidia installer to build the kernel module here's the steps from a guide i wrote to install the nvidia driver from scratch hope this helps you out.

find what kernel is listed when you type ```
uname -a
``` at the terminal for example mine displays ```
Linux ubuntu [COLOR=Red]2.6.10-5-k7[/COLOR] #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux
``` what l've listed in red is what to look at so  on mine i need the kernel headers for the k7 kernel. the easiest way to install these is using synaptic click on search and type headers it will list all the header packages avaliable so i install the package linux-headers-k7 these are the ones for my kernel. if you have a different kernel for example 2.6.10-5-386 you will need the package linux-headers-386 etc. you also need the build-essential package installed this provides the basic compilers and stuff used to build the kernel modules. if you can't get X running to use synaptic you can also install the kernel headers and build essential package like this. 
```
sudo apt-get update
sudo apt-get install linux-headers-386 
sudo apt-get install build-essential
```
for this example im using the 2.6.10-5-386 kernel because it's what ubuntu installs by default and the NVIDIA-Linux-x86-1.0-7667-pkg1.run nvidia driver from [www.nvidia.com](www.nvidia.com).

now to install the driver if your already in an x session exit it by hitting
```
ctrl+alt+F1
```
now at the terminal login and type:
```
sudo -s
```
enter you password 
```
telinit 3
```
if your using ubuntu
```
killall gdm
```
if your using kubuntu
```
killall kdm
```
cd to where the nvidia package is installed in this example i've placed it in /home/username/
```
cd /home/username
```
now run the installer with
```
sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```
after the installer has finished completely you need to edit your /etc/X11/xorg.conf
file and tell it to use the nvidia driver with.
```
nano /etc/X11/xorg.conf
```
example: find the line that looks like this
```

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        [COLOR=Red]Driver[/COLOR]          [COLOR=Blue]"vesa"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

```
and replace whatever is listed under the [COLOR=Red]Driver[/COLOR] section with [COLOR=Blue]"nvidia"[/COLOR] save the /etc/X11/xorg.conf file and reboot.[/QUOTE]
 Thanks, finally for such a complete guide.

I'm gonna give it a try.

Also, how different are these steps from those of installing the NFORCE2 Drivers?

Do I need to install NFORCE2 drivers? Would there be dramatic changes in performances?

Where can I get "Disk Defragmenter" for Linux?

---

### Post by codejunkie on 2005-07-06
[QUOTE=Prudentissimus]Thanks, finally for such a complete guide.

I'm gonna give it a try.

Also, how different are these steps from those of installing the NFORCE2 Drivers?

Do I need to install NFORCE2 drivers? Would there be dramatic changes in performances?

Where can I get "Disk Defragmenter" for Linux?[/QUOTE]

well i don't know for sure because i have never used the NFORCE2 drivers but i would assume that if nvidia uses the same installer type for them then yes it should be the same about installing the kernel headers and build-essential packages,but configureing them i don't know for sure because i don't have an nforce2 chipset also you might need to read the instructions on nvidia's web site and see what the module is called for the NFORCE2 drivers how to load it and see if you have to remove any other modules that conflict with the nforce2 drivers but as i said earlier i have never used them so i don't know.
               as for the defragmenter for linux i don't think you need one because linux doesn't fragment the harddrive like windows. im not saying there isn't a program do that because i think i ran across one about 2 years ago when i was using suse but i didn't bother to use it and i ran suse for almost 2 years on this computer with no problems, like apps that used to run fast taking 10 minutes to load like you get in windows when you haven't defraged in a while. i've noticed with linux stuff just runs one way, if it's slow it's slow, like open office and if its fast, its fast like abiword, hope this helps, but if you really need that app to defrag let me know and i'll try digging through some of my old suse bookmarks and find it for you.

---

### Post by Snipersnest on 2005-07-08
Isn't there something I need to put in my init.d file or something??  

The driver brakes everytime I reboot and I have to modprobe nvidia before I can startx. Its not a big deal, but gets old.

---

