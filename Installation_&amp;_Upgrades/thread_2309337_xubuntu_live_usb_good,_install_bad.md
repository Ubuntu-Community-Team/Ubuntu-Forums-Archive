---
title: "xubuntu live usb good, install bad"
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by ibexslam on 2016-01-09
I'm attempting to help a colleague get started with linux. He's getting a little tired of paying for the privilege of being a prisoner in a walled garden. He has a spare older W7 machine and we're trying to put xubuntu 14.04 on it. The live usb I made works fine on his machine when we boot from that. But when we install it to his hard drive (we've tried twice), the screen is slightly the wrong size (enough to push the icon for the menu off the screen), the wifi is not working, and the mouse is dead. All of these things are totally fine when booting from the flash drive. (The machine also won't boot into windows now, but I'll handle that as a separate issue.)

All of this weirdness is making my colleague uncomfortable with the open source scene...more trouble than it's worth. I need to get him past all this so he can finally revel in the glory of the penguin. 

Any advice, friends, on how to make this install work the way it should?

Thanks,
I.

---

### Post by ajgreeny on 2016-01-09
To be able to help you we need you to help us with a lot more information about the hardware, particularly the graphic card and wifi adapter.

A good start will be for you, or your colleague, to boot the live system again and from that open a terminal and run command ```
lspci
``` then post the output you get back here using code-tags (see my signature below for a "how-to")

---

### Post by ibexslam on 2016-01-12
Hi, aj,

Here's that output:

```

xubuntu@xubuntu:~$  lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

```

Regards,
I.

---

### Post by ubfan1 on 2016-01-12
I don't even see a wifi adapter, so maybe post the USB devices with:
lsusb
The video looks like just Intel, which should work out of the box, so maybe there are adjustments on the monitor (desktop?, external monitor on a laptop?) for picture size and position which can fix things.
Is the mouse a USB device or an older PS2?  
Any additional information will help us figure out the problem.

---

### Post by ibexslam on 2016-01-13
Hi, here's that info:

```

xubuntu@xubuntu:~$ lsusb
Bus 001 Device 003: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It's a PS2 mouse. Don't know about monitor adjustments, but I do know that no adjusting is necessary when booting off the flash drive.

Thanks!

I.

---

### Post by ubfan1 on 2016-01-14
Try 
sudo update-initramfs -u
That might fix the problem, but also look at [http://askubuntu.com/questions/202988/how-to-use-a-ps-2-mouse](http://askubuntu.com/questions/202988/how-to-use-a-ps-2-mouse) and
[http://ubuntuforums.org/showthread.php?t=2047900](http://ubuntuforums.org/showthread.php?t=2047900)

Another possibility is to use a PS2 to USB adapter -- I am using an old PS2 keyboard and the USB adapter works just fine.

---

### Post by ibexslam on 2016-01-14
Hi, folks, 

I admit that I'm a little confused. I don't understand how, if there's a problem with a PS2 mouse, the mouse is totally fine when booting from a flash drive. 

ubfan, your suggestion to try sudo update-initramfs -u...at what point, if you don't mind my asking? After installing to the hard drive? We're not able to interact with the system in any way after installation.

We'll try a different mouse, see what happens.

Any other ideas?

I.

---

### Post by ibexslam on 2016-01-14
Hi, folks, 

I admit that I'm a little confused. I don't understand how, if there's a problem with a PS2 mouse, the mouse is totally fine when booting from a flash drive. 

ubfan, your suggestion to try sudo update-initramfs -u...at what point, if you don't mind my asking? After installing to the hard drive? We're not able to interact with the system in any way after installation.

We'll try a different mouse, see what happens.

Any other ideas?

I.

---

### Post by ubfan1 on 2016-01-14
I thought you could get to a low resolution desktop on the install.  If the keyboard works, switch to a virtual terminal (crt-alt-f2), login, and run the command.  The problem is probably a driver for the mouse which is present in the live-media but not the install.  The links had also suggested just copying the initrd off the install media to the hard disk location, replacing the one there (initrd.img-3.13.0-7xx-generic).  Are using a pae kernel?  Again the links seemd to indicate that might be the point of confusion for the kernel not picking up the right driver.  Again from the virtual term, list the modules (lsmod | sort )  and see what drivers are present (any with ps2 in their name?)  Try and insert one like pcips2 or ps2mult with modprobe (sudo modprobe pcips2 ).

---

### Post by ibexslam on 2016-02-21
Hi, folks,

I'm not hands-on with the computer in question, so I've been passing the suggestions on to my colleague who is new to all of this. The last one caused him to say "*&^%$#@! Put my Windows® back!" He can't follow any of that, and I can only understand about one eighth of it. I've been mystified about the fact that xubuntu is fine from the live USB drive, and useless when installed. But I saw something the other day on Slashdot that gave me an inkling. 

"Installed 3.13.36, which caused the server to boot with no network. No problem, right? Wrong! This kernel also rendered the mouse and keyboard inoperable! My only way back was to boot from a LiveUSB, chroot the server and install an older kernel 3.13.28. The hour-ish of downtime was a huge pain in my" etc.
[http://news.slashdot.org/story/16/02/18/2226254/ubuntu-14044-lts-officially-released#comments](http://news.slashdot.org/story/16/02/18/2226254/ubuntu-14044-lts-officially-released#comments)

No network, no mouse, no keyboard...sounds familiar. Hmm. At this point, I'm thinking, to get things going without too much inscrutable fiddling, I might either wait until the new LTS release comes out in April (actually, I'd wait an additional month for things to stabilize--been there before) and start over, or go with another distro, probably Mint, and see how that works. 

However, if a knowledgeable guru (unlike me) can suggest something fairly straightforward such as "just type this kernally thing into the terminal and you'll be good to go," I'd like to give that a shot. I'm going to have about 10 minutes of hands-on time with the machine this week. Any ideas about this? I'd really like to get past this.

Thanks, folks.

I.

---

### Post by mörgæs on 2016-02-23
> **ibexslam said:**
> 
At this point, I'm thinking, to get things going without too much inscrutable fiddling, I might either wait until the new LTS release comes out in April (actually, I'd wait an additional month for things to stabilize--been there before) and start over, or go with another distro, probably Mint, and see how that works. 


I suggest that you install 15.10. One of the best buntus ever with regards to hardware support.

---

### Post by ibexslam on 2016-02-23
Hi, mörgæs,

I appreciate the advice. Unfortunately, that one is only supported for a few more months. I prefer to stick with LTS releases--particularly for a new user, such as in this case.

I.

---

### Post by mörgæs on 2016-02-23
Five months to be exact. 

I don't understand why people cling to a buggy 14.04 when three development (that is, bug-reducing) cycles have passed since then. Ok, your choice.

---

### Post by Geoffrey_Arndt on 2016-02-23
>   Add a "normal" (usb) mouse and that problem's fixed.
>   Adjust the monitor settings to get the alignment right . . . or try display settings in the xubuntu system settings, problem has nothing to do with kernel(s)
>   Just install the wireless driver via "additional drivers" (use search if you can't find the program in Xubuntu).    Or install a plug & play usb wireless adapter dongle (Panda Ultra Wifi 150 b/g/n . . . $10. on Amazon - - - plug it in . . . . problem fixed)

By the way, Ubuntu 15.10 is excellent - - - upgrading from that to the next LTS is a no-brainer.

---

