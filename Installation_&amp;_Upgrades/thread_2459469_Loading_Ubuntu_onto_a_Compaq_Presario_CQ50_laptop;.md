---
title: "Loading Ubuntu onto a Compaq Presario CQ50 laptop; BIOS vs EFI vs UEFI; Noob."
date: 2021-03-19
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2021-03-19
I don't think that laptop will have a motherboard that can use UEFI so there should be no need to worry about that; if I remember the CQ50 was made way back in the early 2000s before UEFI was around and is also possibly a 32bit machine; all of the Ubuntu OSs are now 64bit so you may be unlucky getting anything other than Lubuntu 18.04 to run.
I also think that trying to run Ubuntu on a Pentium 4 laptop will be so frustratingly slow that you will find it almost unusable.
If you look at the Get-Ubuntu webpage, [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) you will see the minimum requirements for Ubuntu are:-

[B][I]Recommended system requirements:
  2 GHz dual core processor or better
  4 GB system memory
  25 GB of free hard drive space[/I][/B]

You would be much better off trying something like Lubuntu, [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) or Xubuntu, [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) both of which require lower computer resources.

What we need to be able to help you more is some better details of the hardware.
I'm not even sure from your post whether or not you got the live system to run from USB/DVD but I suspect not; you also mention Lubuntu several times even though your title is "Ubuntu"

Please clarify as much as possible and if you see error messages make a full note of what you see and read; telling us that you "get a "boot error" message when loading from the USB w/ the ISO image" is no help and we need much more information.
Should you manage to get a live system running on that machine run terminal command ```
inxi -Fzx
``` and post the output back here, using **code tags** please; there's a "How To" in my signature below

---

### Post by Swan_DB on 2021-03-19
> [COLOR=#000000]I'm not even sure from your post whether or not you got the live system to run from USB/DVD but I suspect not; you also mention Lubuntu several times even though your title is "Ubuntu"[/COLOR]

You are correct, title should say "Lubuntu", not Ubuntu.  I am trying to install Lubuntu.  And I am not sure what "live" means, I did get to a point of setting up the OS configuration, stuff like network, language, keyboard config, timezone, etc., etc.,, but I don't know if that is "live" system, or not.  Is "live" system meaning it's reading from the USB and it's not actually installed yet?  If so, then I did get it to start to run the "live" system, but install failed; I *think* it may have failed due to I couldn't set up the network properly, so maybe it couldn't access the internet for files needed, but I also think the files needed for install should be included and a internet connection/network set-up shouldn't be needed, so it likely failed for another reason (see "alternative Lubuntu version vs Desktop Lubuntu version, idk...?). 


> [COLOR=#000000]if I remember the CQ50 was made way back in the early 2000s before UEFI was around and is also possibly a 32bit machine; all of the Ubuntu OSs are now 64bit so you may be unlucky getting anything other than Lubuntu 18.04 to run.[/COLOR]

yes, laptop is from 2008 but it's x86_64, and *says* it can run 32 bit or 64 bit; from what I've read, I should use the 64 bit OS.


I've just used```
[FONT=Verdana]sudo dd if=/dev/zero of=/dev/sdc bs=1k count=4096[/FONT]
``` 
(from link here: [https://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive](https://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive) )
in an attempt to wipe the 4GB USB clean, so I can start over with the Desktop version of 18.04.5 Bionic Beaver LTS (LXDE)

to clear the USB stick, I'm looking at installing the Desktop version of Lubuntu ISO (instead of the alternative version, whatever that is, from link above -> 18.04.5 Bionic Beaver LTS (LXDE) Desktop download- 64 bit.

> [COLOR=#000000]Should you manage to get a live system running on that machine run terminal command[/COLOR]```
[COLOR=#000000]inxi -Fzx[/COLOR]
```The laptop still has Ubuntu 20.04 on it, so it does work, I can run commands on it, but like you said, "Ubuntu isn't the right distro for a 2GB system with a 1 core CPU", lol.

I will run ```
[COLOR=#000000][FONT=&amp]inxi -Fzx[/FONT][/COLOR]
``` in a few minutes, will edit this comment when I get the output.

[COLOR=#000000][SIZE=5]**EDIT:**[/SIZE][/COLOR]
```
[COLOR=#000000]inxi -Fzx[/COLOR]
```
returns "command not found", so I tried to install via ```
sudo apt install inxi
``` and I can't get it to install, I tried sudo apt-get update sudo apt update --fix-missing sudo apt install inxi --fix-missing, and I can't get it to install. There are about 5 "failure to fetch [http://.](http://.)... " and 1 "Some index files failed to download. They have been ignored or old ones used instead".

Any other commands, or what info are you looking to get?  I can probably find it via another method/command?

Edit 2: Also, I did wipe the USB stick, and have not formatted it yet, should I format and partition it a certain way, like FAT and/or EXT4, and try to download the Desktop version of 18.04.5 onto it, and give it another attempt at installing it onto the the laptop?
I'll wait a bit and see what the replies, if any, say, thank you

---

### Post by yancek on 2021-03-19
EFI and UEFI are the same thing, see the link below.  Lots of sites  explaining it such as below.  If your computer is from 2009, highly  unlikely to be UEFI compatible.

[https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)

Best to focus on one question per thread, pick the one which is most  important.  In your last post, you are trying to install software (inxi)  apparently from the 'live' Lubuntu.  You can't do that without a  working internet connection.

You don't need an internet connection to install Lubuntu/Ubuntu or any  other Linux.  The 'live' systems are meant to allow potential users to  test the system and also to install it to an actual hard drive.  A  'live' system can be modified as you indicate in one of your posts,  setting up network configuration, etc.  Since a 'live' system is read  only by design, all these configurations will be lost on reboot, if you  accidentally shut down the computer or have a power outage while using  it.  No point in making these configuration changes on a 'live' system  other than to test.

In your last post, you indicate that you were able to boot and use the  'live' but that the install failed.  What you need to post are the  details as to what exactly happened.  The computer froze, you got an  error message (what exactly it was).

The boot error and operating system not found messages are generally  because a user did not create the bootable usb correctly or has selected  the wrong device in the BIOS.

The age of your computer would indicate that it is not UEFI compatible  and you should ignore anything related to UEFI.  You can easily check  this by going into your BIOS on boot and looking for anything EFI/UEFI,  particularlly in the Boot Options section.

---

### Post by Swan_DB on 2021-03-19
Edit: With USB stick not plugged in.

```
lsblk
``` returns
> 
loop0
...
...
loop9 - all loop types - mount point for all is: /snap/......

sda -> (160GB internal HDD)
--sda1 - size is 512M - mount point is: /boot/efi
--sda2 - size is 1k - mount is empy
--sda5 - size is 146.1G - mount point is: /
--sda6 - size is 2.5G - mount point is empty
sr0 -> size is 1024M, and type is rom, mount point is empty
 

---

### Post by mikewhatever on 2021-03-19
I think the output of <lscpu> would be interesting for the CPU info.

There is no need to format or partition the USB, as it is wiped clean  anyway when the ISO file gets written.

---

### Post by Swan_DB on 2021-03-19
> [COLOR=#000000]In your last post, you are trying to install software (inxi) apparently from the 'live' Lubuntu.[/COLOR] No, I tried installing (inxi) from Ubuntu 20.04, currently installed on the laptop still, it has internet connection.  I did not try to install (inxi) while running Lubuntu/while trying to install Lubuntu (it never installed, and didn't give the option to "try" or "install", just an old looking graphical interface with "Install" and a couple other options that made little sense to me. I did get to a point where I could press 9 and enter a root command line interface, I assume to change boot settings among other things, but I was scared I'd break something).

> [COLOR=#000000]You don't need an internet connection to install Lubuntu/Ubuntu or any other Linux. The 'live' systems are meant to allow potential users to test the system and also to install it to an actual hard drive. A 'live' system can be modified as you indicate in one of your posts, setting up network configuration, etc. Since a 'live' system is read only by design, all these configurations will be lost on reboot, if you accidentally shut down the computer or have a power outage while using it. No point in making these configuration changes on a 'live' system other than to test.[/COLOR]
 This clarifies what a live boot is, thank you : )

> [COLOR=#000000]The boot error and operating system not found messages are generally because a user did not create the bootable usb correctly or has selected the wrong device in the BIOS.[/COLOR]I think I created the bootable USB wrong.

> [COLOR=#000000]The age of your computer would indicate that it is not UEFI compatible and you should ignore anything related to UEFI. You can easily check this by going into your BIOS on boot and looking for anything EFI/UEFI, particularlly in the Boot Options section[/COLOR][COLOR=#000000] 
The laptop shows "sda1 as mounted at /boot/efi"  ?  which is confusing me, but I think my issue is I messed up the bootable USB.  I'm going to try to redo it in a little while and see what happens.

[/COLOR]Thanks for all the input, it is appreciated : )

---

### Post by Swan_DB on 2021-03-19
Well, just realized the laptop's wifi wasn't working, not sure if it's the JB weld, or I crossed the wires when putting the wifi card back in...  between that, and realizing (inxi) wouldn't install because of it..  having a 1 core cpu with no mouse, so I have to keep swapping my mouse from my desktop and back and forth to keep typing this. I quit, at least for now.

 Thanks for trying guys.

---

### Post by Swan_DB on 2021-03-19
Unhooked wifi connectors, re-connected them (on the Compaq Presario laptop) and got the internet connection working;
Downloaded (inxi);
Ran```
inxi -Fzx  
System:
  Kernel: 5.8.0-45-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Hewlett-Packard 
  product: Compaq Presario CQ50 Notebook PC v: F.32 serial: <filter> 
  Mobo: Wistron model: 360B v: 09.48 serial: <filter> BIOS: Hewlett-Packard 
  v: F.32 date: 11/20/2008 
Battery:
  ID-1: BAT0 charge: 0% condition: 47.5/47.5 Wh (100%) 
  model: LGC-LGC EV06047 status: Unknown 
CPU:
  Topology: Single Core model: Intel 585 bits: 64 type: MCP arch: Core Merom 
  rev: D L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 4322 
  Speed: 2161 MHz min/max: N/A Core speed (MHz): 1: 2161 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics 
  vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: vesa unloaded: fbdev,modesetting 
  resolution: 1280x800~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 20.2.6 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.8.0-45-generic 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet 
  vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus ID: 01:00.0 
  IF: enp1s0 state: down mac: <filter> 
  Device-2: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter 
  vendor: Hewlett-Packard AR5BXB63 802.11bg Mini PCIe NIC driver: ath5k 
  v: kernel port: 3000 bus ID: 02:00.0 
  IF: wls1 state: up mac: <filter> 
Drives:
  Local Storage: total: 149.05 GiB used: 8.74 GiB (5.9%) 
  ID-1: /dev/sda vendor: Western Digital model: WD1600BEVT-60ZCT1 
  size: 149.05 GiB temp: 41 C 
Partition:
  ID-1: / size: 142.76 GiB used: 8.74 GiB (6.1%) fs: ext4 dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 52.0 C mobo: 50.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 193 Uptime: 2h 39m Memory: 1.87 GiB used: 700.7 MiB (36.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  inxi: 3.0.38 

```
Ran```
lscpu
``` and it returned : ```
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   36 bits physical, 48 bits virtual
CPU(s):                          1
On-line CPU(s) list:             0
Thread(s) per core:              1
Core(s) per socket:              1
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           15
Model name:                      Genuine Intel(R) CPU             585  @ 2.16GHz
Stepping:                        13
CPU MHz:                         2161.251
BogoMIPS:                        4322.50
L1d cache:                       32 KiB
L1i cache:                       32 KiB
L2 cache:                        1 MiB
NUMA node0 CPU(s):               0
Vulnerability Itlb multihit:     KVM: Mitigation: VMX unsupported
Vulnerability L1tf:              Mitigation; PTE Inversion
Vulnerability Mds:               Vulnerable: Clear CPU buffers attempted, no microcode; SMT disabled
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Vulnerable
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, STIBP disabled, RSB filling
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr s
                                 se sse2 tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni 
                                 dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm pti dtherm


```

I'm still thinking my issue is the bootable USB I made, I made it wrong.
I am about to try to install again 18.04.5 Desktop 64 bit bionical beaver LTS from a freshly partitioned USB, I think I may still have done it wrong because
the only real difference this time is I'm using the "Desktop" version of 18.04.5 instead of the "Alternative" version from the Lubuntu download site.

What I did was download the ISO into ~/Downloads, then I copied it to the USB stick (sdc --> sdc1; with mount at : /media/[COLOR=#0000cd]username[/COLOR]/8fc4cfc9-1d94-4d21-bd94-4c015blahblahblah

So : ```
ls /media/[COLOR=#0000cd]username[/COLOR]
```shows I have 2 things : > [COLOR=#000080]8fc4cfc9-1d94-4d21-bd94-4c015blahblahblah[/COLOR]  lubuntu-18.04.5-desktop-amd.iso

Will report back when the install fails/succeeds.

---

### Post by CatKiller on 2021-03-19
> **Swan_DB said:**
> I think I may still have done it wrong because
the only real difference this time is I'm using the "Desktop" version of 18.04.5 instead of the "Alternative" version from the Lubuntu download site.

The default install image boots into a fully-functional Linux environment, which is what makes it "live" from which you can install or not. The alternative image is just the install scripts without the live environment.

And yes, you did it wrong. After the process you should have a whole bunch of files on your USB stick rather than just the one file. It's possible to get the files from the filesystem image with dd, but I've found [Etcher](https://www.balena.io/etcher/) to be painless.

---

### Post by Swan_DB on 2021-03-19
USB boot attempt has been at a black screen with a blinking underscore cursor now for 20+ minutes, I suspect the boot-able USB is wrong again.

I got Ubuntu 20.04 onto the laptop using Rufus.exe which I *think* converts the ISO file into a...  something?  a working boot-able disk?

But Rufus.exe wouldn't open on my PC because I *think* it's an exe file meant for windows?  I don't know.

My next attempt might be to find a way to convert the ISO file into a boot-able format that works for my laptop.

Or look into GRUB2 and boot loaders, that might be interesting :guitar:

---

### Post by CatKiller on 2021-03-19
> **Swan_DB said:**
> I *think* BIOS is older and being...  deprecated slowly/replaced by UEFI, is this correct?

It already happened, a long time ago, and it was quick. But because BIOS was so ancient and limited, it's trivial to emulate. That emulation is what the Legacy/Compatibility Support Module setting in your UEFI does. *EFI* was the brief Intel-only replacement for BIOS, before it became standardised as UEFI, but the name lingers in some dark corners.

---

### Post by CatKiller on 2021-03-19
> **Swan_DB said:**
> But Rufus.exe wouldn't open on my PC because I *think* it's an exe file meant for windows?  I don't know.


Rufus is Windows-only, yes. There are any number of Linux-native tools for creating a bootable USB stick from an image, including Etcher that I suggested earlier.

---

### Post by Swan_DB on 2021-03-19
Any idea why the ISO file doesn't "just work".  I started into this thinking I could put the ISO file onto a USB stick, then just "plug and play".

Was I wrong, and just missed the part where people converted the ISO file into a different format?

---

### Post by CatKiller on 2021-03-19
> **Swan_DB said:**
> Any idea why the ISO file doesn't "just work".  I started into this thinking I could put the ISO file onto a USB stick, then just "plug and play".

Was I wrong, and just missed the part where people converted the ISO file into a different format?

You were wrong in that you thought you could just put the file on a USB and have it work: your UEFI doesn't have the ability to read arbitrary .iso files.

You're also wrong in thinking that the file needs to be "converted" into a different "format." The .iso file is the *image* of a bootable filesystem, for convenience of distribution. You're taking the filesystem from that image, so that you have a filesystem rather than an image of a filesystem, and putting it onto a USB stick. Your UEFI can read a bootable filesystem from a USB stick (or DVD, or CD-ROM back in the day, which is where the process came from).

[This](https://en.wikipedia.org/wiki/ISO_9660) is the filesystem, and why it has the ISO suffix, if you're interested.

---

### Post by Swan_DB on 2021-03-19
[SOLVED]

Rufus was an exe file.  [Etcher]("https://www.etcher.net/") for the win.  ISO file to boot-able USB stick in less than 5 minutes, an the Lubuntu 18.04.5 booted right up on the Compaq Presario CQ50.  

Thanks to everyone.  Cat Killer, you devil you, lol.  Really appreciate the help.

EDIT:  Hello from Lubuntu 18.04.5 (Bionic Beaver), using a 2008 Compaq Presario CQ50.  Etcher for-the-win when needing a boot-able USB drive, Thanks again to everyone here.  My 1 core laptop is usable now!  Internet is quick too : )

---

### Post by ajgreeny on 2021-03-19
I was tempted to leave your text in the post above unchanged but decided to edit out the poor language and change to default font.
Please do not use huge fonts as you did there in normal posting.
I do understand how frustrated you were when posting earlier but please use normal fonts and do not make use of half-hidden obscenities; this is a family friendly and posts such as yours at #9 and in this one which I have now edited.
Such posts are unwelcome and normally removed from public view.

As we have now established that the machine does have a 64 bit capability you would be advised to use a different version of OS and not Lubuntu 18.04 which regrettably for you loses support next month. I originally mentioned Lubuntu 18.04 in my first post as that was the only *buntu OS that retained a 32 bit OS; that has now lost support and all of the Ubuntu family is now 64bit only.
Luckily it looks as if you should be able to use either Xubuntu or Lubuntu 20.04 on that machine and whilst not fast I suspect, it should manage to run both OSs at a usable, if pedestrian speed.

---

### Post by Swan_DB on 2021-03-19
> **CatKiller said:**
> You were wrong in that you thought you could just put the file on a USB and have it work: your UEFI doesn't have the ability to read arbitrary .iso files.

You're also wrong in thinking that the file needs to be "converted" into a different "format." The .iso file is the *image* of a bootable filesystem, for convenience of distribution. You're taking the filesystem from that image, so that you have a filesystem rather than an image of a filesystem, and putting it onto a USB stick. Your UEFI can read a bootable filesystem from a USB stick (or DVD, or CD-ROM back in the day, which is where the process came from).

[This]("https://en.wikipedia.org/wiki/ISO_9660") is the filesystem, and why it has the ISO suffix, if you're interested.


I must have missed this, and the other comment about Etcher, I don't get any notifications so I just go into the thread and try to pick up where I left off.

Anyways, you're the best, CatKiller, that is exactly what I needed to know about the ISO file, or rather file system.  I haven't read into it too far yet, but it seems strange that it's still being used, I would guess for backwards compatibility reasons, but I'll read the wiki on it.

Can you recommend where I can go next?  Should I learn about GRUB2? Or boot loaders? Or is there some foundational stuff you can point me in the direction of to get a understanding of a lower level than the ISO and boot-able USB drives?  If not, no worries, thanks again : )

---

### Post by CatKiller on 2021-03-19
> **Swan_DB said:**
> Can you recommend where I can go next?

Just keep using your computer for computer-type things. If something comes up that piques your interest, or is particularly troublesome, you can read up about whatever it is or ask here about it. Things that are interesting or useful for one person wouldn't necessarily be so for anyone else.

So, for example, today I'm finding signed distance fields really interesting; I doubt many other people do. Tomorrow I'm sure I'll find something else really interesting. Very occasionally, an acquired titbit can help someone on the Ubuntu forums :)

---

### Post by yancek on 2021-03-19
>  What I did was download the ISO into ~/Downloads, then I copied it to the USB stick (sdc --> sdc1

That is possible if you know enough about Grub to create a proper menuentry on your installed Ubuntu.  From your posts, I would think it's not worth getting into.  Using software such as Etcher, Rufus and a number of other programs will correctly create a bootable usb.  You indicate that the Rufus you used had an .exe extension.  That would only work if you were trying to create the bootable usb from a windows operating system, were you?  If you are trying to create a bootable usb from Linux/Ubuntu you need the Linux version of the software you use.  Also, if you are doing it from Linux/Ubuntu, you can simply use the dd command to create a bootable usb as the iso files are hybrid.  There are numerous sites explaining this and you should be able to get examples/instructions by simply doing a Search on these forums:  Create bootable iso with dd.r

---

### Post by Swan_DB on 2021-03-19
> [COLOR=#000000]That is possible if you know enough about Grub to create a proper menuentry on your installed Ubuntu. [/COLOR] I actually started down that path, lol.  I found a guide while out, on my iPhone, then when I got home to do it, I couldn't find the guide as I forgot the keywords I used in the search.  All I remember was it was on askubuntu.com, a guy laid out how to add a menuentry into the grub.config.  I think I might try it anyways, as I'll be swapping OS's soon again as 18.04 is not being supported much longer.

---

