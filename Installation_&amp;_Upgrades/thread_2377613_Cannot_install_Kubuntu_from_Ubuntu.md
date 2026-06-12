---
title: "Cannot install Kubuntu from Ubuntu"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by gb6903 on 2017-11-15
My recently installed the new Ubuntu and have had many issues. Therefore, I've been trying to install Kubuntu. However, whenever I burn the ISO onto my USB stick, it boots me into Grub. Where do I go from here?

---

### Post by RobGoss on 2017-11-15
It sounds like your system is trying to boot into the old installation. Are  tapping F-12 when you boot your machine?

On new installations you should not be seeing the Grub menu unless it's not recognizing your USB and trying to boot to the old install like I stated

---

### Post by gb6903 on 2017-11-15
Well I have to hit F9 to boot from the USB otherwise it will go to windows. In Grub when i execute the Return_Normal command it brings me to the new Ubuntu installation page...but when I choose any of the options, it tells me the Kernel must first be loaded...

---

### Post by RobGoss on 2017-11-15
What version of Ubuntu do you have installed? Is this a dual boot in your first post you did not mention you were trying to setup a dual boot

Please try to give as much details as possible about what you're trying to accomplish here, this way we are on the same page. If you are trying to setup a dual boot I would recommend backing up any important **data **before you proceed. Trying to dual boot and not knowing what's involved can be problematic

---

### Post by gb6903 on 2017-11-15
No, I'm not trying to dual-boot. Originally I had Windows 10 Pro installed which came installed on my HP Laptop. I decided to completely wipe the Windows partitions because I wanted a strictly Ubuntu or Kubuntu installation. I do believe that something weird with the partitions happened, because when I power on my PC, it boots me into a sort of Windows recovery mode. From there, I have to go to troubleshoot->change EFI then reboot. When I reboot it then allows me to hit F9 to set me boot up disk. I then choose the Ubuntu installation.

After I installed Ubuntu, things never worked quite as they should. Plus, I prefer the Kubuntu flavour, so I decided to try to completely wipe the Ubuntu installation so I'm strictly left with Kubuntu. But now I'm left with the issue of getting booted into Grub...and I don't know how to install from Grub...I'm familiar with Linux but mostly the GUI, not when it comes to command-line and Grub.

Let me know if there's anything else that can help.

I tried to use UNetBootin to burn the ISO onto my USB stick, but when I install the app then try to launch it, I get the error attached.  And Just FYI, attached is my disk partitions.

---

### Post by vasa1 on 2017-11-16
You can also just use the forum's attachment facility to upload images here. It's the little paper-clip icon *above* the posting text box. If you don't see it, click on Go Advanced *below* the posting text box.

---

### Post by gb6903 on 2017-11-16
Ok, I edited it. Still can't install Kubuntu though :(

---

### Post by RobGoss on 2017-11-16
I would just do a fresh installation of** Kubuntu** if this is your flavor you want then choose to erase the entire disk and install Kubuntu that way you shouldn't have any issues with the partition. I would also use [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) to create your boot media it seems to work well for me

---

### Post by gb6903 on 2017-11-16
I just tried that. When I try to run the program, I get this same error message like always:

Is there a way just to do it from Grub? Or is that going to be really difficult?

I also wanted to mention that the [LINK]("https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") you wrote only has a .EXE installation,

Man, I'd do anything for an official Kubuntu installation DVD right now.

---

### Post by RobGoss on 2017-11-17
What are the specs for this machine including the model, Ram, Graphic card and so on

---

### Post by yancek on 2017-11-17
You can't install any Linux from Grub because Grub is just a bootloader.  You should be able to boot the Kubuntu iso from Grub with a proper entry.  Does your Ubuntu still boot or is that gone also?  If you can boot Ubuntu and you have the Kubuntu iso on it's partition this should work.  I noticed you still have two windows partitions showing in the image you posted including the FAT32 EFI partition? 

If you can still boot Ubuntu, you might try using the 'dd' command to put the Kubuntu iso on the flash drive.

---

### Post by gb6903 on 2017-11-17
> **RobGoss said:**
> What are the specs for this machine including the model, Ram, Graphic card and so on

Attached are my specs.

I tried the same thing with Xubuntu and ran into the same error.

---

### Post by gb6903 on 2017-11-17
> **yancek said:**
> You can't install any Linux from Grub because Grub is just a bootloader.  You should be able to boot the Kubuntu iso from Grub with a proper entry.  Does your Ubuntu still boot or is that gone also?  If you can boot Ubuntu and you have the Kubuntu iso on it's partition this should work.  I noticed you still have two windows partitions showing in the image you posted including the FAT32 EFI partition? 

If you can still boot Ubuntu, you might try using the 'dd' command to put the Kubuntu iso on the flash drive.

Gotcha. Yes I'm currently using the Ubuntu install.The Kubuntu ISO is on an external hard drive. And it's burned to a USB stick as well.

---

### Post by vasa1 on 2017-11-17
If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system). After that, run```
inxi -Fxzc0
```and post the output here. The output may help people guide you better.

PS: edit out your user name please!

---

### Post by gb6903 on 2017-11-18
> **vasa1 said:**
> If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system). After that, run```
inxi -Fxzc0
```and post the output here. The output may help people guide you better.

PS: edit out your user name please!
I tried both ways. Below are the outputs: 

Like I was saying...something is gooofy with my Ubuntu installation, :([ATTACH=CONFIG]277564[/ATTACH][ATTACH=CONFIG]277565[/ATTACH][ATTACH=CONFIG]277566[/ATTACH]

---

### Post by vasa1 on 2017-11-18
First, run exactly```
sudo apt-get install inxi
```
After that's goes through successfully,
run```
inxi -Fxz
```Keep a space between inxi and -Fxz.

If that runs, properly, copy the terminal output and paste that here.

---

### Post by gb6903 on 2017-11-18
```
****r-HP-250-G6-Notebook-PC:~$ sudo apt-get install inxi
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi
****-HP-250-G6-Notebook-PC:~$ inxi -Fxz
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi
*****r-HP-250-G6-Notebook-PC:~$ ^C
*****r-HP-250-G6-Notebook-PC:~$ sudo apt install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi
******-HP-250-G6-Notebook-PC:~$ 


```
Asterisks added for reason,

---

### Post by vasa1 on 2017-11-18
Have you run ```
sudo apt-get update
```recently?
And
```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by gb6903 on 2017-11-18
> **vasa1 said:**
> Have you run ```
sudo apt-get update
```recently?
And
```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

```
****r-HP-250-G6-Notebook-PC:~$ inxi -Fxz
System:    Host: *****-HP-250-G6-Notebook-PC Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.24-0ubuntu1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: HP product: HP 250 G6 Notebook PC v: Type1ProductConfigId serial: N/A
           Mobo: HP model: 832A v: 23.40 serial: N/A
           UEFI: Insyde v: F.24 date: 09/25/2017
Battery    BAT1: charge: 16.5 Wh 54.0% condition: 30.6/31.1 Wh (99%)
           model: Hewlett-Packard PABAS0241231 status: Discharging
CPU:       Dual core Intel Core i5-7200U (-HT-MCP-) 
           arch: Kaby Lake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10848
           clock speeds: max: 3100 MHz 1: 2700 MHz 2: 2700 MHz 3: 2700 MHz
           4: 2700 MHz
Graphics:  Card: Intel HD Graphics 620 bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1366x768@59.80hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           IF: eno1 state: down mac: <filter>
           Card-2: Intel Device 24fb driver: iwlwifi bus-ID: 02:00.0
           IF: wlo1 state: up speed: N/A duplex: N/A mac: <filter>
Drives:    HDD Total Size: 1752.6GB (28.4% used)
           ID-1: /dev/sda model: SanDisk_SD8SN8U size: 128.0GB temp: 36C
           ID-2: /dev/sdc model: Name n/a size: 500.1GB temp: 0C
           ID-3: USB /dev/sdd model: External_USB_3.0 size: 1000.2GB temp: 0C
           ID-4: USB /dev/sdb model: Ultra size: 124.2GB temp: 0C
Partition: ID-1: / size: 31G used: 9.6G (34%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.5C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 266 Uptime: 15:23 Memory: 4164.0/7897.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37 


```
Aha! Good stuff, my friend.

---

### Post by gb6903 on 2017-11-18
But can you tell me why I get these errors when I try to run certain apps like UNetBootin? [ATTACH=CONFIG]277568[/ATTACH][ATTACH=CONFIG]277569[/ATTACH]

---

### Post by gb6903 on 2017-11-18
Honestly, I think what I may do is just reinstall Windows, then create the Kubuntu boot disk from there. I also think I need to use GParted to get rid of some of those miscellaneous partitions,

---

