---
title: "problem(s)  after NVIDIA driver upgrade."
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Zeffy on 2008-04-17
I am new to Ubuntu and this is my first machine totally Linux, with no XP dual boot.  So I am a noob, but I am very excited to be XP free!  Though I have a problem, I will explain as best I can.

I had a problem with ubuntu (Gutsy) freezing regularly on my brand new machine, after a little research I found that it was a memory leak in compiz.real due to my NVIDIA driver installed, that could be fixed by installing the latest NVIDIA driver.  That sounded too easy,  so off I went to the NVIDIA website, downloaded the latest driver "NVIDIA-Linux-x86-169.12.pkg1.run" and followed the website instruction exactly.  Heres what happened.  It didn't work!  After a lot of playing (don't ask what I did, I couldn't say what worked) I finally got the driver to work but in doing so.. 

Now I have lost sound, and  the GNOME system monitor shows I only have 1 CPU listed when previously I had 2.  So my machine has no sound and is running at half speed :(

1: Sound.   I get this error "No volume control GStreamer plugins and/or devices found." or in amarok "Audio output unavailable; the device is busy. xine parameters:".  

lspci -v    (shows)[I]

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: a9c00000-afcfffff
        Prefetchable memory behind bridge: 00000000aff00000-00000000efefffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at afefc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: afd00000-afdfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at afefbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at e400 [size=8]
        I/O ports at e080 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d880 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: medium devsel, IRQ 3
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 1806
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ae000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at ac000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at afce0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 267c
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c800 [size=256]
        Memory at afdff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at afdc0000 [disabled] [size=128K]
        Capabilities: <access denied>[/I]

so my sound card is at some level recognized.. but alsactl can not find it.  I have tried uninstalling and reinstalling alsa and anything gstreamer.. No Luck

As for the CPU, cant remember the command, but the output stated I had 1 CPU and reached my limit and that it was going to ignore the other one.

I would appreciate any help!  I am a noob that is probably overlooking something REALLY simple.  But whatever that is, I can not find it!  Thank You


p.s Everything was working perfectly (apart from the memory leak ;) ) before I installed the driver update.  

- - - -   PC Specs - - - - 

Release 7.10 (gutsy)
Kernel Linux 2.6.22-14-386
GNOME 2.20.1

Memory:  1011.5 MB
Processor:  Intel(R) Core(TM)2 Duo CPU  E4500 @ 2.20GHz
Graphics:  GeForce 8500 GT
Sound:  Onboard (ICH7 Family)  High Definition Audio Controller (realtek)

Available disk space  187.4 GB

---

### Post by warp99 on 2008-04-17
First go uninstall the package 'NVIDIA-Linux-x86-169.12.pkg1.run'  
```
sudo ./NVIDIA-Linux-x86-169.12.pkg1.run --uninstall
```
Then run the following:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
```
That will get you back to your original settings. If you disabled the nv modules in the '/etc/default/ linux-restricted-modules-common' file please enable them again.

---

### Post by Zeffy on 2008-04-17
Thanks.. I will go and try this :)

---

### Post by Zeffy on 2008-04-17
Thanks, but unfortunately with all the tweaking I had done to get the NVIDIA driver working this was not enough.  As an update I found this..

[http://prantran.blogspot.com/2008/01/enabling-multicoredual-core-support.html](http://prantran.blogspot.com/2008/01/enabling-multicoredual-core-support.html)

and now I have dual core and sound again! Yayy  But on the downside the NVIDIA driver is NOT working and am now running in low graphics mode.  I can get that working in a second!   But the fix will make the sound and cpu wrong again.  ERRRRRRRRR


It seems that NVIDIA likes the new 386 kernel whilst dual and sound like the older generic one.. so what to do.. whats a n00b to do.. :)

---

### Post by warp99 on 2008-04-17
> **Zeffy said:**
> Thanks, but unfortunately with all the tweaking I had done to get the NVIDIA driver working this was not enough.  As an update I found this..

[http://prantran.blogspot.com/2008/01/enabling-multicoredual-core-support.html](http://prantran.blogspot.com/2008/01/enabling-multicoredual-core-support.html)

and now I have dual core and sound again! Yayy  But on the downside the NVIDIA driver is NOT working and am now running in low graphics mode.  I can get that working in a second!   But the fix will make the sound and cpu wrong again.  ERRRRRRRRR


It seems that NVIDIA likes the new 386 kernel whilst dual and sound like the older generic one.. so what to do.. whats a n00b to do.. :)

If you run this command again:

```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
```
It will loads the restricted modules for your running kernel. See all of the drivers, including the restricted modules, are compiled against a running kernel. The reason your drivers are not working is that you have the modules for the 386 kernel and since you changed kernels you need the correct ones. Once you do that just issue the following:
```
sudo dpkg-reconfigure xserver-xorg
```
and choose nvidia as your driver. Issue a 'sudo reboot' and all should be well.

---

### Post by Zeffy on 2008-04-18
Thanks, I get what you mean, but unfortunately i cant seem to uninstall the NEW nvidia driver that is causing all the headaches. (well headaches if I want sound and to run as a dual not single core!) It is not showing in synaptic, the command on this thread to uninstall does not work for me, and I have to "untick" it from my "restricted drivers manager" to get the computer to work.. I have tried re-installing the glk-new and glk versions, but I am guessing because the other one is newer they are being ignored..

So I have this great new graphics card and my computer is basically running in low res mode :(

I seem to be going round in circles :P   I hate being a nOOb and knowing nothing, but I also know I have to start somewhere!  Its both fun and VERY VERY frustrating trying to sort things out!

---

### Post by warp99 on 2008-04-18
Don't go into Synaptic and uninstall the driver. Open a terminal and issue the following string I gave you:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
```
the string will determine the dependencies and install the proper modules for you. Then run the following:
```
sudo dpkg-reconfigure xserver-xorg
```
and choose 'nvidia' as your driver.

---

### Post by Zeffy on 2008-04-18
Thanks guys for all your help.  I have not fixed this problem totally.  But I am at a point where I am happy (for now).  As I have sound, a dual core (running as a dual core) and I have my screen set at 1280 X 1024 as opposed to 640 X 480 on my 19" monitor!!  Though I have not got the restricted driver working and will loose a lot of graphics card functionality.    But I will give it a rest for a while :)

For those who have a similar issue with screen resolution when you run dkpg-reconfigure xserver-xorg, you need to know your monitors exact HF and VF ranges.  Going the simple or even medium option doesn't cut it.  Go advanced and input the exact figures manually :)  Thats the only thing that worked for me..   I will be happy if I never see another warning about running in low res mode!

Thanks again..

---

### Post by Czar on 2008-04-19
> **warp99 said:**
> Don't go into Synaptic and uninstall the driver. Open a terminal and issue the following string I gave you:

```

sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-restricted-modules-2.6.22-14-generic is not possible, it cannot be downloaded.
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.

```

What's going on?  Did the upgrade to 8.04 remove the restricted-modules source?

```

The following packages will be REINSTALLED:
  linux-restricted-modules-2.6.22-14-generic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the linux-restricted-modules-2.6.22-14-generic package. This might mean you need to manually fix this package.

```

---

### Post by nacho32 on 2008-04-19
I tryed and here s what I got

now I have 800 x 600 lol
jeff@jeff-desktop:~$ sudo apt-get install --reinstall linux-restricted-modules-$(jeff -r) nvidia-glx
bash: jeff: command not found
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-restricted-modules is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3853kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 126640 files and directories currently installed.)
Preparing to replace nvidia-glx 1:96.43.05+2.6.24.12-16.34 (using .../nvidia-glx_1%3a96.43.05+2.6.24.12-16.34_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up nvidia-glx (1:96.43.05+2.6.24.12-16.34) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jeff@jeff-desktop:~$

---

### Post by Czar on 2008-04-19
> **nacho32 said:**
> I tryed and here s what I got

now I have 800 x 600 lol
jeff@jeff-desktop:~$ sudo apt-get install --reinstall linux-restricted-modules-$(jeff -r) 

lol.  ;-)

leave it as uname, not your name.  (uname - prints system information)

---

### Post by nacho32 on 2008-04-19
ok i did that 

does that mean the driver is installed? I have driver on desktop but don't no how to install it

jeff@jeff-desktop:~$ sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
Suggested packages:
  avm-fritz-firmware-2.6.24-16
The following NEW packages will be installed:
  linux-restricted-modules-2.6.24-16-386
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 18.0MB/21.9MB of archives.
After this operation, 47.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted linux-restricted-modules-2.6.24-16-386 2.6.24.12-16.34 [18.0MB]
Fetched 18.0MB in 2min24s (125kB/s)                                       
Selecting previously deselected package linux-restricted-modules-2.6.24-16-386.
(Reading database ... 126640 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.24-16-386 (from .../linux-restricted-modules-2.6.24-16-386_2.6.24.12-16.34_i386.deb) ...
Preparing to replace nvidia-glx 1:96.43.05+2.6.24.12-16.34 (using .../nvidia-glx_1%3a96.43.05+2.6.24.12-16.34_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up linux-restricted-modules-2.6.24-16-386 (2.6.24.12-16.34) ...

Setting up nvidia-glx (1:96.43.05+2.6.24.12-16.34) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jeff@jeff-desktop:~$

---

### Post by Zeffy on 2008-04-20
I am still using 7.1 not 8.04 as I will wait till the most stable is released, I am just not that competent yet :)  The crux of my problem is the latest NVIDIA driver wont work on the kernel version I am running for sound and dual core capabilities.  I cant remove the latest restricted nvidia, as whatever I do, it is still on the list.  So I cant just "rollback" to the previous restricted driver. (that had issues anyway-hence why I was upgrdaing!).. so catch 22 all around.   I am dissapointed, but so far my only issue is that I can't use the pretty visual effects that are part the Gutsy release (those that caused the NVIDA memory leak in the first place!).  So am not terribly dissapointed.  But we will see when I play around a bit more.

I know I am a n00b but surely I am not the only one with issues?  Hopefully the latest kernel release will satisfy both requirements!

---

### Post by Spartan.II.117 on 2008-04-20
you should try envy (program to manage restricted graphics modules) it is in the repos.

---

### Post by warp99 on 2008-04-23
> **Czar said:**
> ```

The following packages will be REINSTALLED:
  linux-restricted-modules-2.6.22-14-generic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the linux-restricted-modules-2.6.22-14-generic package. This might mean you need to manually fix this package.

```

No your booting under the 7.10 kernel, not the kernel for Hardy which is 2.6.24-16-generic. So your trying to reinstall a package that is not available. You need to boot to the hardy kernel then run the commands again.

---

### Post by warp99 on 2008-04-23
> **nacho32 said:**
> ok i did that 

does that mean the driver is installed? I have driver on desktop but don't no how to install it

jeff@jeff-desktop:~$ sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
Suggested packages:
  avm-fritz-firmware-2.6.24-16
The following NEW packages will be installed:
  linux-restricted-modules-2.6.24-16-386
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 18.0MB/21.9MB of archives.
After this operation, 47.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted linux-restricted-modules-2.6.24-16-386 2.6.24.12-16.34 [18.0MB]
Fetched 18.0MB in 2min24s (125kB/s)                                       
Selecting previously deselected package linux-restricted-modules-2.6.24-16-386.
(Reading database ... 126640 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.24-16-386 (from .../linux-restricted-modules-2.6.24-16-386_2.6.24.12-16.34_i386.deb) ...
Preparing to replace nvidia-glx 1:96.43.05+2.6.24.12-16.34 (using .../nvidia-glx_1%3a96.43.05+2.6.24.12-16.34_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up linux-restricted-modules-2.6.24-16-386 (2.6.24.12-16.34) ...

Setting up nvidia-glx (1:96.43.05+2.6.24.12-16.34) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jeff@jeff-desktop:~$

Yes you have the new drivers installed. If you enable nvidia in the restricted drivers manager they should work. If not open a terminal and issue the following:
```
gksudo nvidia-settings
```
if nvidia-settings is not installed then:
```
sudo apt-get install nvidia-settings
```
you may have to enable the universe repositories to install. Now you can use nvidia-settings to make yourself a new xorg.conf that will support you video card by using the "X Server Display Configuration" and saving the file as "/etc/X11/xorg.conf" then reload the desktop (crtl+alt+backspace).

---

### Post by warp99 on 2008-04-23
> **Zeffy said:**
>  Though I have not got the restricted driver working and will loose a lot of graphics card functionality.    But I will give it a rest for a while :)

When you ran 'sudo dpkg-reconfigure xserver-xorg' if you choose nvidia as your driver then you're running the restricted modules even if the restricted drivers manager says that you're not.

---

### Post by Czar on 2008-04-23
> **warp99 said:**
> No your booting under the 7.10 kernel, not the kernel for Hardy which is 2.6.24-16-generic. So your trying to reinstall a package that is not available. You need to boot to the hardy kernel then run the commands again.

Your right.. something got messed up with I upgraded my hard-drive and.. long story short the kop option (/boot/grub/menu.list) needed updated and now I'm in the proper kernel.

---

