---
title: "[SOLVED] Help!! Apparent Graphics malfunction before and after installation"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by cheatr on 2008-01-13
I have installed Ubuntu like 1 year ago, i liked it a lot, but i wasn't really quite ready to commit to it. So i gave it another go today, but i have encountered a strange problem. When i try installing from the live dvd through the OS like installer, it loads ubuntu, and when it's done, it plays the welcome song and i get a very strange image filled with static, colors, repetitive ubuntu logos(askewed and colorized) and it totally blocks(or not, because i can't really see what's going on because my screen freezes at that strange image). So i figure it's that GUI installation, so i go for the text installation. Works very well, i repartition my disks and it installs. It finishes i finally breathe relaxed, but what do you know, when it reboots into linux i get the same strange screen after the loader.
I haven't deleted linux yet, and i would like some help on fixing it (if possible) or in the worst case scenario at least a way to get it of my system and allow my xp to reboot normally(because i'm afraid of the GRUB loader being erased when i uninstall ubuntu).
A little more detail on the screen if i'm not exact enough, it looks like a television that is receiving through a broken antenna, the image is repetitive, in strange and inappropriate colors, it has static, etc, and it also apparently blocks.
Please help i really like the OS and want to give it another shot at becoming my primary OS.
BTW it's Ubuntu 7.10, and my graphics card is an nVidia 8500GT, i know ati's have a problem with linux.


Edit: I also remember i tried to install 7.04 to make sure something is actually wrong, and it said something along the lines of " Failed to start X server", maybe it has a connection ?

---

### Post by Pumalite on 2008-01-13
You might need to install this driver:
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)

---

### Post by PmDematagoda on 2008-01-13
Boot Ubuntu in Recovery Mode, then execute the following one after each is done:-
```
sudo apt-get install nvidia-glx-new
```
then
```
sudo nvidia-settings --config enable
```
after that, execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as Nvidia and any other options that may be required.

After those commands are done, execute:-
```
reboot
```

---

### Post by cheatr on 2008-01-13
Appreciate the help Dematagoda, but i get an error when it tries to download the driver. I didn't post it because it's way too long to type down and then on the server, but basically it's saying that it can't download from the us ubuntu repository, it says unresolved followed by the address of the repository . any ideeas, is it because i'm not from the us? Pumalite, you don't seem to understand my problem, i can't actually start linux to install things on it. or can i do it from windows?(highly unlikely).

---

### Post by Craigus on 2008-01-13
> i can't actually start linux to install things on it

I think it is starting. If you boot and then do ctrl-alt-F1 you should get to a text terminal. You can log in and work in the command line from there.

Reading through this may help:

[http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/]("http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/")

The tutorial doesn't address your exact situation.

---

### Post by cheatr on 2008-01-13
Nope, turns out it doesn't start at all in the normal mode. So i tried those steps in the recovery mode, still didn't work, gave me " couldn't resolve us.archive.ubuntu.com".

---

### Post by Craigus on 2008-01-13
Boot in recovery mode.

Try to ping something;

```
ping www,google.com
```

IF you have connectivity, open /etc/apt/sources.list :

```
nano /etc/apt/sources.list
```

here's mine (a bit abbreviated):

```
## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Gutsy (Ubuntu 7.10) +++
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse


## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical +++ 
deb http://archive.canonical.com/ubuntu gutsy partner

## +++ Medibuntu +++
deb http://packages.medibuntu.org/ gutsy free non-free



```

What does yours look like ?

Edit: if you change to these, and save the file, does it work then ?

---

### Post by cheatr on 2008-01-14
Mine looks very simmilar, it has a few more sites, like one for security and whatnot, and it had the us servers, so i erased the "us." in front of each line, but it still doesn;t work

And when i try pinging it says unknown host(i tried [www.google.com](www.google.com)). My internet router automatically sets my ip and dns.

---

### Post by cheatr on 2008-01-14
Any other ideas? at least give me some tips on how to install the drivers if i download them previously from XP and put them on a thumb drive.(i can't remember the commands in recovery mode to mount the flash and everything). And are the drivers on the nvidia site good?

---

### Post by Craigus on 2008-01-14
I'll have a look around for answers to your question, but I think really what you need to do is to get the 'net connectivity issue sorted. If you can't ping, then apt will not be able to fetch packages either.

Once you can connect, you will be able to get the drivers from the repos.

Edit: Can you ping anything on your local network ?

Are you connecting via an ethernet cable ?

---

### Post by Pumalite on 2008-01-14
Get wired to the Internet.

---

### Post by cheatr on 2008-01-14
Ok, i've figured that out, but since my internet connection sets itself up automatically i can't see what more i could do to it.(and yes it is on ethernet but i have no other computers on the network)

---

### Post by Partyboi2 on 2008-01-15
Could you connect to the internet without the router to start with while you get the  system up and running?

---

### Post by cheatr on 2008-01-15
The router is the one i have from my ISP, which gives automatically assigns my ip and dns addresses, so i can't directly connect to the internet. But again i ask isn't there any way to get the files on to a flash drive from windows, and install it in the recovery mode?

---

### Post by Partyboi2 on 2008-01-15
Yes you can download the package from 
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new) But you may need to download some other packages it depends on to get it installed. 
then you need to mount your flash drive via the terminal
[http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html)

On a side note have you tried to reconfigure xserver and selected the "vesa" driver which hopefully should give you are working desktop while you sort out your problem.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cheatr on 2008-01-15
I couldn't get my flash mounted, can't figure out why, but i managed to install the nvidia-glx-new from the ubuntu dvd, and it still doesn't work.

---

### Post by Omnios on 2008-01-15
Re: strange lines
K this sounds like a xserver problem and I had this problem before and solved it by lowering the  the frequency a bit.

---

### Post by Pumalite on 2008-01-15
nvidia-glx-new doesn't work with your card. Check the driver I suggested.

---

### Post by cheatr on 2008-01-16
Thank you for the idea Pumalite. But keep in mind i am new and i remember nothing on using terminal commands. I need to know this, on what kind of removable media should i put that driver, and how do i execute it once i am able to access it from the recovery mode? Please help cause i would really like to see that orange screen again...

---

### Post by PmDematagoda on 2008-01-16
A flash drive would suffice.

When you plug the flash drive into the PC, post the result of:-
```
cat /etc/mtab
```

---

### Post by cheatr on 2008-01-16
I can't paste the result from recovery mode....or can I? If not tell me what to look for in the result at leas. But i can't believe it's that complicated to install something from a removable flash drive....

---

### Post by PmDematagoda on 2008-01-16
Just give the entries that have the word "dev" in them. So that would mean lines like:-
```
/dev/sda1 /media/home
```

---

### Post by cheatr on 2008-01-17
This is what i get. Only the ones with dev:

```
dev/sda3/ext3 rw,errors=remount -ro 00
udev/dev/shm tmpfs rw 00
devpts /dev/pts devpts rw,gid=5, mode 620 00
```

---

### Post by PmDematagoda on 2008-01-17
Ok, now for this next command I will need the full output. The command is:-
```
sudo fdisk -l
```

With that we can figure out how to mount your USB drive.

---

### Post by cheatr on 2008-01-17
I did the command. I assume you're interested only in the values that relate to my flash usb, the ones that relate to my HDD are not here. They are:

```
Disk /dev/sdb:2032MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units=cylinders of 4032*512=206384 bytes
Disk identifier: 0x00000000

Device Boot  Start  End  Blocks        Id  System
/dev/sdb1        1     984  1983619   6     FAT16
```


If you need the others too, tell me.(i can't see why you would, so i didn't take the time to write them down.)

---

### Post by PmDematagoda on 2008-01-17
Create a new directory using:-
```
sudo mkdir /media/flash
```

Then mount the drive using:-
```
sudo mount -t vfat /dev/sdb1 /media/flash -o rw
```

After that, enter the flash using:-
```
cd /media/flash
```
and post the result of:-
```
ls
```

---

### Post by cheatr on 2008-01-17
Thank you man. It lists all my files that are on the drive. I hope i'll get to install the driver today(i got it from the nvidia website), and i'll post back with the results.

Edit: So i tried installing the driver from nvidia, but when it starts it says I am running in runlevel 1 instead of 3, and it tells me to use level 3. I ignored that and went on, after that it said that there is no matching precompiled kernel interface for my kernel, and asks if i want it to get it from the web, but of course i can't connect to the internet. Any ideas?

---

### Post by Craigus on 2008-01-17
Seriously, you need to fix the internet issue. The other problems should then go away.

Post the output of```
ifconfig
```

---

### Post by Pumalite on 2008-01-17
And:
lshw -C network

---

### Post by cheatr on 2008-01-18
For lshw -C network, i got a bunch of data about my ethernet board (eth0), and strangely at the beginning it says ```
*-network DISABLED
```

For ifconfig i got:
```
Link Encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
UP LOOPBACK RUNNING MTU:16436 METRIC:1
RX packets:0 errors:0 dropped:0 overrun:0 frame:0
Tx packets:0 errors:0 dropped:0 overrun:0 carrier:0 collision:0 txqueuelen:0
RX bytes:0 (0.0b) TX bytes:0 (0.0b)
```

---

### Post by Pumalite on 2008-01-18
Post:
ip addr

---

### Post by cheatr on 2008-01-18
This is what i get:

```
1: lo : <LOOPBACK, UP, 1000> mtu 16436 qdisk noqueue
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
2:eth0: <BROADCAST/MULTICAST> mtu 1500 qdisk poop glen 100
link/ether 00:19:66:48:e5:f8 brd ff:ff:ff:ff:ff:ff
```

---

### Post by Pumalite on 2008-01-18
> **cheatr said:**
> Ok, i've figured that out, but since my internet connection sets itself up automatically i can't see what more i could do to it.(and yes it is on ethernet but i have no other computers on the network)

If you have DSL with a Winmodem; put a router in the middle providing you with DHCP

---

### Post by cheatr on 2008-01-18
I have a router with DHCP provided by my ISP, it gives my adress automatically

---

### Post by Craigus on 2008-01-18
Are the link lights up on the router and the lan connection on the PC ?

---

### Post by cheatr on 2008-01-19
Good idea to check that but unfortunately they're all on, so the problem isn't with my router....

---

### Post by cheatr on 2008-01-19
I am trying knoppix to see if that works..... i'll post back soon with the results.

Edit: So the Knoppix live cd works perfectly, but it visibly struggles with the graphic user interface, it first tries to use the X window manager, fails badly and the ngoes to Server Xorg which works for my computer. My internet problems are still here, it can't automatically configure the DHCP..... Does this mean anything related to Ubuntu?

---

### Post by cheatr on 2008-01-20
Please anybody, i need help with this, firstly if i can fix my display issue without configuring my internet i am a happy man, if i have to reconfigure my net to make it work please help me with that, but just give me an idea, cause i'm getting really desperate...

---

### Post by Pumalite on 2008-01-20
Wrong post.

---

### Post by cheatr on 2008-01-20
Say what?

---

### Post by Craigus on 2008-01-20
Does this machine dual boot by any chance, and have internet connectivity when running windows ?

---

### Post by cheatr on 2008-01-21
Yes it does dual boot, it boots in windows xp and ubuntu 7.10, out of which only windows works with full functionality(including internet connectivity), ubuntu works only in CLI in recovery mode without internet connectivity...

---

### Post by cheatr on 2008-01-22
Ok it's finally fixed, and surprisingly enough it was fixed using something from another thread which was already posted on this thread. For some reason it did not work the first time, but this time it did:). Ok what i did was i reconfigured the xserver and chose the nvidia drivers. It works now, a big thank you to PmDematoga and everybody else.

---

