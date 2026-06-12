---
title: "intel graphics installer : the following packages have unmet depedencies"
date: 2017-08-21
forum: Installation &amp; Upgrades
---

### Post by someoe on 2017-08-21
The information :

-ubuntu 16.04 LTS 
-Memory : 3.8 GiB 
-Processor : Pentium(R) Dual-Core CPU E5700 @ 3.00GHz × 2 
-Graphics : Intel® G41 
-Graphics card information : [https://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/g41-chipset-brief.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/g41-chipset-brief.pdf)
-OS type : 64-bit
-OpenGL version string: 2.1 Mesa 17.1.2
-Motherboard information : [https://www.gigabyte.com/Motherboard/GA-G41MT-S2PT-rev-11#ov](https://www.gigabyte.com/Motherboard/GA-G41MT-S2PT-rev-11#ov)
-Kernel : 4.12.0-041200-lowlatency
-sudo apt-get update output (i know, there's alot of problems) :
```
Hit:1 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease
Hit:2 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Hit:3 [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease                             
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Ign:5 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Ign:6 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring InRelease                   
Hit:7 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Hit:8 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Hit:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring Release                     
Hit:10 [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) xenial InRelease     
Hit:11 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease             
Hit:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                    
Hit:14 [http://ppa.launchpad.net/obsproject/obs-studio/ubuntu](http://ppa.launchpad.net/obsproject/obs-studio/ubuntu) xenial InRelease  
Hit:15 [http://download.mono-project.com/repo/ubuntu](http://download.mono-project.com/repo/ubuntu) xenial InRelease           
Hit:16 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) xenial InRelease          
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Hit:18 [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) xenial InRelease       
Hit:19 [http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu](http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu) xenial InRelease 
Hit:20 [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial InRelease  
Hit:21 [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial InRelease  
Hit:22 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease       
Hit:25 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease          
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main Sources [88.3 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [346 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [324 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [147 kB]
Fetched 1,212 kB in 14s (82.0 kB/s)                                            
Reading package lists... Done
W: Target Packages (restricted/binary-amd64/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-i386/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-all/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en_US) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (partner/binary-amd64/Packages) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple  times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple  times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: [https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:](https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:) Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weak digest algorithm (SHA1)
W: Target Packages (restricted/binary-amd64/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-i386/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-all/Packages) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en_US) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:8
W: Target Packages (partner/binary-amd64/Packages) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple  times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple  times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:41 and  /etc/apt/sources.list.d/xenial-partner.list:4
```


The Problem :

i wanted to install intel graphics to update my driver, the download link : [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0) then selected ([Graphics Installer 1.4.0 for Ubuntu* 15.10, 64-bit]("https://download.01.org/gfx/ubuntu/15.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.4.0-0intel1_amd64.deb"))

when i open it i write my password then click on begin then click on install and wait until it ends, but this two windows appears :

[URL="https://ibb.co/hzqyhQ"]https://ibb.co/hzqyhQ
[/URL]
then this window :

[URL="https://ibb.co/kvvENQ"]https://ibb.co/kvvENQ
[/URL]

---

### Post by vocx on 2017-08-21
> **someoe said:**
> The information :

-ubuntu 16.04 LTS 
-Memory : 3.8 GiB 
-Processor : Pentium(R) Dual-Core CPU E5700 @ 3.00GHz × 2 
-Graphics : Intel® G41 
-Graphics card information : [https://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/g41-chipset-brief.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/g41-chipset-brief.pdf)
-OS type : 64-bit
-OpenGL version string: 2.1 Mesa 17.1.2
-Motherboard information : [https://www.gigabyte.com/Motherboard/GA-G41MT-S2PT-rev-11#ov](https://www.gigabyte.com/Motherboard/GA-G41MT-S2PT-rev-11#ov)
-Kernel : 4.12.0-041200-lowlatency
-sudo apt-get update output (i know, there's alot of problems) :


First of all, please edit your post. Whenever you post the terminal output in this forum, you should use "CODE" tags. This keeps the terminal output intact and with a monospace font.
```

Hit:1 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease
Hit:2 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Hit:3 [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease                             
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Ign:5 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Ign:6 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring InRelease                   
Hit:7 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Hit:8 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Hit:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring Release                     
Hit:10 [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) xenial InRelease     
Hit:11 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease             
Hit:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                    
Hit:14 [http://ppa.launchpad.net/obsproject/obs-studio/ubuntu](http://ppa.launchpad.net/obsproject/obs-studio/ubuntu) xenial InRelease  
Hit:15 [http://download.mono-project.com/repo/ubuntu](http://download.mono-project.com/repo/ubuntu) xenial InRelease           
Hit:16 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) xenial InRelease          
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Hit:18 [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) xenial InRelease       
Hit:19 [http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu](http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu) xenial InRelease 
Hit:20 [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial InRelease  
Hit:21 [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial InRelease  
Hit:22 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease       
Hit:25 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease          
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main Sources [88.3 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [346 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [324 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [147 kB]

```

> 
The Problem :

i wanted to install intel graphics to update my driver, the download link : [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0) then selected ([Graphics Installer 1.4.0 for Ubuntu* 15.10, 64-bit]("https://download.01.org/gfx/ubuntu/15.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.4.0-0intel1_amd64.deb"))

when i open it i write my password then click on begin then click on install and wait until it ends, but this two windows appears :

[URL="https://ibb.co/hzqyhQ"]https://ibb.co/hzqyhQ
[/URL]
then this window :

[URL="https://ibb.co/kvvENQ"]https://ibb.co/kvvENQ
[/URL]

I see several problems with your computer. First, why do you want to upgrade your video drivers? The Intel integrated video drivers normally come with the kernel so you don't need to install them. Do you experience a particular problem that is presumably corrected with newer drivers? Check your device with "lshw -c video".
```

*-display               
       description: VGA compatible controller
       product: **Broadwell-U Integrated Graphics**
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: **driver=i915** latency=0
       resources: irq:46 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:4000(size=64)

```
The i915 driver used by Intel chipsets normally comes with the kernel, so you don't need to install it.

You apparently are using a 4.12 kernel. Why? This is already a very new kernel. The standard kernel for 16.04 was 4.4. If you use the hardware enablement (HWE) stack you should get 4.10. Maybe you are using the HWE "edge" that gives you an even newer kernel, maybe 4.11 and 4.12. Do you really need such a new kernel? I imagine the 4.12 version already includes the latests Intel drivers. Despite this, you still want the newest of the newest? Why?

The link you provide seems to be for an Intel driver for Ubuntu 15.10 which is an old and unsupported version of Ubuntu. You should not install anything from this version in your current 16.04 system.

Another issue that I notice, that is probably not related to this, is that you have many strange repositories, old repositories I'd say, referencing "raring", and "precise". These Ubuntu versions should no longer be supported, so I'd advice you to remove the repositories referencing them. Also, the messages about "configured multiple times" are strange.
```
Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list.d/xenial-partner.list:4
```
This gives me the impression you have repeated repositories. You should clean all this clutter.

So, as you can see, I'm a bit confused by the state of your system. I'd like you to clarify why your system is in the state it is, so we could better assess what you want to do, or if you really need to upgrade your drivers or not.

---

### Post by someoe on 2017-08-21
i need to update my graphics driver because of this, an another question by me (read carefully) : [https://forum.unity3d.com/threads/graphics-problem-in-games-made-with-unity.488544/](https://forum.unity3d.com/threads/graphics-problem-in-games-made-with-unity.488544/)

thanks,

---

### Post by QIII on 2017-08-21
Hello!

Please use code tags when posting terminal commands and their output.  This maintains the formatting and makes your posts easier to read.

To use code tags:

1.  Click the # button above the text box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

