---
title: "Can't upgrade from 16.04 LTS to 18.04.2LTS"
date: 2019-03-07
forum: Installation &amp; Upgrades
---

### Post by newcomer83 on 2019-03-07
Hello everyone,

I've been trying to upgrade my Ubuntu 16.04 to 18.04.2LTS for some months now, but I keep getting the error that some packages couldn't be downloaded and that there was a problem that's most commonly network-related and that I should check my internet connection, which is a weird message, because it happens right after I downloaded package 88 out of 96, so my internet is obviously working (also my browser works as normal, too).

I tried changing servers, but after testing about 5 (including the main one) I've had enough. In the past years update problems kept coming and going, too, so I am assuming that there is a server problem with the upgrade as well. Is there something I can do to get the upgrade to work or is there a major problem I just have to wait out?

I have about 190GB of free space.

Cheers
Alex

---

### Post by newcomer83 on 2019-06-05
I don't understand. Is my problem this rare so that nobody knows how to solve it?
When I use the terminal, right before the error I get 6 of the following errors:
"(appstreamcli:9383): GLib-CRITICAL **: g_strchug: assertion 'string != NULL' failed"
Followed then by two errors that tell me that a signature couldn't be verified due to a missing public key: "NO_PUBKEY D615560BA5C7FF72" (it's the same ID in both cases)

Is there any way for me to get more precise errors to post here?

---

### Post by cruzer001 on 2019-06-05
And sometimes a post will just slip thru the crack :)

Please post the output of:
```
sudo apt -f install
```

---

### Post by Rubi1200 on 2019-06-05
Couple of other things to check as well:

1. make sure you have no PPAs installed and if you do uncheck them via Software Sources >> Other

2. please post the output of ```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by LwIh%*7 on 2019-06-05
Could you have a look at this? [https://askubuntu.com/questions/1031881/dist-upgrade-seems-to-have-created-an-issue](https://askubuntu.com/questions/1031881/dist-upgrade-seems-to-have-created-an-issue) 

It seems a similar issue.

---

### Post by newcomer83 on 2019-06-06
Thanks for all the help! It seems like I had to both purge libappstream3 and remove the launchpad PPA to finally get the update to work!

However, I am facing a bunch of new problems now:
My resolution is super low and I can't go to the system settings, because it won't start. I already found out that they switched from unity to gnome and tried reinstalling gnome, but it didn't work. Starting it from a terminal led to the following error:
```
gnome-control-center: relocation error: /usr/lib/x86_64-linux-gnu/libwebkit2gtk-4.0.so.37: symbol gcry_mpi_ec_decode_point version GCRYPT_1.6 not defined in file libgcrypt.so.20 with link time reference
```

Also my firefox is hiccupping a lot (i.e. freezing for about half a minute whenever I install or uninstall anything in a terminal).

And furthermore, Ubuntu keeps bugging me about failing to ttf-mscorefonts, so when it tries to launch the installation process it wants me to log in as Admin, but when I do that it just does nothing.

I generally research the problems I encounter before posting in a forum, but for some reason researching solutions to Ubuntu 18 related problems has been fruitless each and every time. It's starting to turn into a nightmare. -_-

Should I be worried that my 8 year-old PC might be too old for Ubuntu 18? My graphics card is an Nvidia.. 550 or 560 or something.

---

### Post by Rubi1200 on 2019-06-06
From the terminal:

```
sudo apt install inxi
```

then post the output of

```
inxi -Fzr
```

I have Ubuntu 18.04 running on a laptop that is about 8 or 9 years old. The issues may or may not be graphics related but let's see some specs. from the above command and then we can look further at what is going on.

---

### Post by 1clue on 2019-06-06
This sounds to me a bit like some server in your configs which is defined for you but no longer exists, or is not available for some reason. And the NO_PUBKEY error sounds like you don't have an ssl key for some repository. 

I would check /etc/apt/sources.list and verify that each one has good transfer times for your system. I would also check to make sure you have the keys for any repo you install.

The freezing for half a minute sounds like your DNS server is no longer working, and it takes awhile for the request to timeout before going to the next server in the list.

---

### Post by newcomer83 on 2019-06-07
Okay, so here are the inki infos:

```

System:    Host: alexander Kernel: 4.15.0-51-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-970A-UD3 v: x.x serial: N/A
           BIOS: Award v: F1 date: 05/17/2011
CPU:       Quad core AMD Athlon II X4 640 (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 3000 MHz 1: 3000 MHz
           2: 1800 MHz 3: 800 MHz
           4: 1800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 7.0, 128 bits)
           version: 3.3 Mesa 18.2.8
Audio:     Card-1 NVIDIA GF116 High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Card-3 Logitech Webcam C270
           driver: USB Audio
           Sound: ALSA v: k4.15.0-51-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: eth0 state: up speed: 1000 Mbps duplex: full
           mac: <filter>
           Card-2: Ralink RT3062 Wireless 802.11n 2T/2R
           driver: rt2800pci
           IF: wlan0 state: down
           mac: <filter>
Drives:    HDD Total Size: 2000.4GB (2.7% used)
           ID-1: /dev/sda model: ST2000DL003 size: 2000.4GB
           
Partition: ID-1: / size: 205G used: 11G (6%)
           fs: ext4 dev: /dev/sda7
           ID-2: /boot size: 1.9G used: 160M (9%)
           fs: ext4 dev: /dev/sda1
           ID-3: /home size: 780G used: 33G (5%)
           fs: ext4 dev: /dev/sda8
           ID-4: swap-1 size: 8.91GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda9
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 27.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://archive.ubuntu.com/ubuntu bionic main restricted
           deb-src http://archive.ubuntu.com/ubuntu bionic main restricted
           deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted
           deb-src http://archive.ubuntu.com/ubuntu bionic-updates main restricted
           deb http://archive.ubuntu.com/ubuntu bionic universe
           deb-src http://archive.ubuntu.com/ubuntu bionic universe
           deb http://archive.ubuntu.com/ubuntu bionic-updates universe
           deb-src http://archive.ubuntu.com/ubuntu bionic-updates universe
           deb http://archive.ubuntu.com/ubuntu bionic multiverse
           deb-src http://archive.ubuntu.com/ubuntu bionic multiverse
           deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse
           deb-src http://archive.ubuntu.com/ubuntu bionic-updates multiverse
           deb http://security.ubuntu.com/ubuntu/ bionic-security restricted universe main multiverse
Info:      Processes: 283 Uptime: 3 min Memory: 1736.7/7974.5MB
           Client: Shell (bash) inxi: 2.3.56 
```

> 
I would check /etc/apt/sources.list and verify that each one has good  transfer times for your system. I would also check to make sure you have  the keys for any repo you install.
I'm not sure how to do that. I download all my updates from the main server, because my closest server (German) has failed often in the past couple of months.

And I just got the info again that "ttf-mscorefonts-installer" wishes to download additional information, but fails. And when I try to "Run this action now", it wants me to type in my password, but then it doesn't do anything further.

---

### Post by cruzer001 on 2019-06-07
> And I just got the info again that "ttf-mscorefonts-installer" wishes to download additional information, but fails. And when I try to "Run this action now", it wants me to type in my password, but then it doesn't do anything further. 
Try running this in terminal.
```
sudo apt install ttf-mscorefonts-installer
```
To accept the license press the ***Tab*** key until the 'O.k.' is highlighted and then ***Return***.

---

### Post by newcomer83 on 2019-06-07
Hm... Ubuntu told me mscorefonts were already up-to-date. Weird.

edit: I just figured out that if I changed the graphics card's driver from the "xserver-xorg-video-nouveau" one to the proprietary one (nvidia-driver-390) I can have my Full-HD resolution back! This was the main reason why I was frustrated that the system settings aren't working. Settings still aren't launching, but at least I can use my Ubuntu without getting a headache any longer. 640x480 is terrible if web page designs are made for bigger resolutions. Menu bars, cookie notices and stuff can be quite annoying on low-res.

---

### Post by cruzer001 on 2019-06-07
Excellent!

Don't forget to mark this thread solved if your good with the results.

---

### Post by newcomer83 on 2019-06-07
I will mark it as solved after the System Settings work again and after the ttf-mscorefonts-installer doesn't appear any longer. ;-)

Though technically they're not the initial topic. If you want I can put them into another thread or two.

---

