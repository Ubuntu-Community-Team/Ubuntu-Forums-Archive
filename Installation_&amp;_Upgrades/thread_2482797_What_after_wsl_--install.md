---
title: "What after wsl --install"
date: 2023-01-10
forum: Installation &amp; Upgrades
---

### Post by gordon33 on 2023-01-10
I want to do a ubuntu clean install on my new Window 11 hp lap top      

I was able to get "wsl --install" as the instructions I found said.  I hoped to get the ubuntu home page but all I get is the terminal and a small ubuntu icon that only wakes up the terminal. Am I close, can I get the linux ubuntu really working from this windows terminal?

Any recommendation on instructions for clear, simple,and  detailed instructions for an install would be helpful.

I just do not have the patients for Windows .


Gordon33

---

### Post by MAFoElffen on 2023-01-10
WSL 2 basic installation is just Linux Terminal. That is not giving you a fair look at the touch and feel of Ubuntu Desktop.

What Edition of Windows are you running? Windows Professional?

What I am thinking and the way I approached this with my Computer Science students was to give them the whole experience. A way of doing that as an introduction to, is to run it as a Virtual Machine (VM). That way you can explore what it is and how to use it, with full features, without diving in feet first. You can learn where everything is, and test drive it, without anything being crippled. 

If you have Windows Pro, you could turn on Hyper-V as a feature and install Ubuntu as a VM. If Home Edition or Lower, you could install VirtualBox, then install Ubuntu as a VM.

I love Ubuntu in that it is vastly customizable to your own personality and desires. Most software applications are free. There is so much that you can learn and do. I learn by doing (hands on).

A lot of people here, started out that way and fell in love with this OS. Depending how that goes, you could then decide if that is how you want it, or to step further into it by either installing it natively as a Dual-boot alongside Windows, or in place of Windows.

 I have installed Ubuntu Linux as people's daily driver. For most people, as soon as they learn where things are, and what to do, they are at home. Most of them do not know what OS specifics are, nor do they care, as they have the freedom to do what they need to or want to do.

---

### Post by gordon33 on 2023-01-10
Hello MAFoElffen

 I thought that is all I got was Linux Terminal with "wsl --install".  I was hoping for a complete install.

Sadly the new hp lap top came with  Windows 11.  Windows 11 is what came with this hp.

I love Ubuntu and have used it exclusively on 3 or 4 other computers for the last 20 years.

As I only do installs when I get a new computer ever 4 or 5 years I have to learn the install process all over again.  I am all ways happiest once windows is gone.


Any recommendation on instructions for clear, simple,and detailed instructions for an install would be helpful?

---

### Post by MAFoElffen on 2023-01-11
Good to hear that. Ubuntu is my daily driver.

I asked someone to join in that keeps a reference of different brands and models of computers and tips for them as it relates to Ubuntu. He also may have some links to a good tutorial for you. What would help him, it to know what brand and model you have...

If he does, that will save me a lot of typing. If not, I will certainly type up some instructions for you and links to a tutorial I trust. Given that you are an Ubuntu user, I can gear that to your level.

My initial recommends is to plan out what you want to do and look to the long-term use of your computer. In saying that, for a daily driver, you want something that is stable and dependable. Long Term Service (LTS) Releases are released every 4 years and are meant to be Stable. They are meant to be supported for 7 years. (used to be 5 years) Interim releases are meant to be rolling short-term support releases that are in the development cycle between LTS versions. There support is only 8 months. Used to be 6 months.) The current Long term release is Ubuntu 22.04.1 LTS. The .1 being the first point release within that LTS. I test Dev Releases daily, but my daily driver is an LTS release.

I migrate my system releases and plan for maintenance and repair in my installs to promote that. Saying that, I do not do a out-of-the box, canned, whole disk install. Rather, I use "other/custom". Then I can install the system to about 15-20GB... Then I divvy up the rest up the storage for home, data and other slices, etc., based on what it's job is. (And mount those slices back in...) The reason that I keep the OS system to itself (isolated), is that, worst case, it be be reinstalled/replaced quickly, without much affect on my other data and information.

With that so far?

---

### Post by Impavidus on 2023-01-11
In case it wasn't clear, wsl gives you an Ubuntu system in a kind of virtual machine, running inside Windows. If you want Windows gone, you need a bare metal install.

---

### Post by oldfred on 2023-01-11
HP is not the most Linux friendly, but with updates & settings changes most do work.

I might keep dual boot as HP does not yet support UEFI update from Linux. Most allow download of an update file and install from within UEFI, but I am not sure that HP even does that. And firmware update for both UEFI & SSD are required sometimes frequently when new virus' are found. 
You can shrink Windows NTFS using Windows tools so only about 30% free in NTFS partition. It needs 30% free to work well. Only use Windows tools to shrink the NTFS partition.

You will need at least 22.04 and maybe 22.10, or even wait for 23.04. Very new systems need latest kernel & drivers.
I have new Dell with 11th Gen Intel & NVMe. I installed 22.04 Kubuntu without issue. I did have to turn off bitlocker & fast startup in Windows. But forgot to make the UEFI settings changes that I have posted many times. And it still worked. It used a new Intel RAID driver, so I did not have to change to AHCI.

What model HP?
Update UEFI, you can check if HP added to fwupdate, but only some commercial  systems seem to be there. Then you can update from Linux.
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

This user posted all the changes he made to get it to work. Issues often common by vendor.
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)

Some general UEFI install info in my signature below.

Ubuntu's install tutorial 
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Boot

---

### Post by gordon33 on 2023-01-11
Thank you for all the help I will get back at it this evening.

---

### Post by MAFoElffen on 2023-01-11
To confirm, 'oldfred' is who is who I asked to join in. When he mentioned HP ZBook and posted the link to the thread, take note of this post in particular:
[https://ubuntuforums.org/showthread.php?t=2482555&p=14125216#post14125216](https://ubuntuforums.org/showthread.php?t=2482555&p=14125216#post14125216)

We are both patiently waiting to hear which model HP Laptop you have...

I am still Certified as an HP, Dell and Lenovo On-Site Warranty Service Tech... Even though I am now working as something else. HP's Dev-One Line is a Pre-Order Linux Pre-Installed Laptop with an Ubuntu derivative OS... But not all their Laptops are 100% Linux Friendly. One of my go to tools for diagnostics, besides an HP Tools USB, was my Ubuntu Live-USB with persistence.

I am a big fan of Dual Booting Ubuntu alongside Windows 11. About half my machines "here" are dual-boot, with Ubuntu as the main OS, and either Windows or MAC OSx as a secondary presence. It's not that I use the other OS'es a lot at home, but if I need to use them, for say, updating the BIOS, Machine specific diagnostics utilities, and such, it is there. ...and some businesses require that people have Windows or MAC to communicate with them (their utilities). I also do Dev testing and support work for Windows Server and VMware.

One thing I would do early on, is to contact HP Support and have them send you the HP / Windows OS USB key to your Laptop. It is free from them (to ship directly to you). If you ever have to reinstall Windows to your Laptop, the License DRM is locked to the chips in your specific motherboard. If your ever need your motherboard replaced, someone like me needed to come and rebrand the new motherboard with the existing motherboard's information, so that the Windows License carries over. That HP Windows USB Key then loads the OS, with the original HP Apps, and automatically is Activated with the old / existing Windows License. Dell and Lenovo are similar in how they do that.

Waiting for your input before going on...

To do an install alongside Windows, there is some prep work required inside Windows and in the BIOS.

---

### Post by gordon33 on 2023-01-11
Hello Old Fred and MAFoElffen

The lap top is a HP 15-dw4047nr.  

What I am struggling with is making a boot-able flash stick.  I have been able to get the download of Ubuntu-22.04-desktop-amd64 on my new lap top.

I will be using this lap top to stream videos, save family photos, and do some office work.  Such as, Spread sheets and letters.

I did explain to the HP tech when picking a lap top I would be using Linux.

---

### Post by oldfred on 2023-01-11
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most find this works, but also Rufus or etcher. Some just find one works better than the other. 
Also with HP, some find one port works better. And many UEFI now require a UEFI setting to enable USB booting like full USB support or similar setting.
Howto help USB boot drives - sudodus
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

The link above was another HP 15, so issues should be similar. 
Vendors use same UEFI with slight modifications depending on system, so issues are almost always the same across many similar models.

---

### Post by gordon33 on 2023-01-11
It looks as if [https://ubuntu.com/tutorials/install...top#1-overview](https://ubuntu.com/tutorials/install...top#1-overview) has given me enough information as the new lap top has booted in ubuntu and is asking me questions such as language, passwords, and just told me I need to restart the computer.

It did seem I had to figure out what selections to make with etcher.  but I guessed right.

Thank you for all the help.

---

### Post by gordon33 on 2023-01-11
I the instructions from  [https://ubuntu.com/tutorials/install...top#1-overview](https://ubuntu.com/tutorials/install...top#1-overview)  were enough  for me to get ubuntu 22.04 downloaded to my new computer.    I am missing the wifi when i go to settings i get wired and cable unpluged.  I need to know how to get the wifi option

---

### Post by gordon33 on 2023-01-11
From the upper right the pull down menu does not include wi-fi disconnected.

I have been able to connect to the web with a Ethernet cable.

---

### Post by MAFoElffen on 2023-01-11
Please post the output of:
```

sudo lshw -c network | grep 'product: \|driver='

```

---

### Post by gordon33 on 2023-01-12
gordon@gordon-HP-Laptop-15-dw4xxx:~$ sudo lshw -c network | grep 'product: \|driver='
[sudo] password for gordon: 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-57-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       product: Realtek Semiconductor Co., Ltd.
gordon@gordon-HP-Laptop-15-dw4xxx:~$ ^C

---

### Post by MAFoElffen on 2023-01-12
I don't see any wireless card... That laptop has a Realtek RTL8822CE 802.11a/b/g/n/ac (2x2) Wi-Fi® and Bluetooth® 5 wireless card[11,12,13]... That should show up with that query...

Is it turned off in the BIOS?

EDIT: If you go back to the last post, please edit it, go to advanced edit, highlight the terminal output, and press the "#" icon, to wrap the ouput with CODE Tags...

---

### Post by MAFoElffen on 2023-01-12
Is it turned off in the BIOS? Does it show up with HP TOOLs (HP's Diagnostics Utility...) A copy of the diagnostics is in the UEFI BIOS... Loaded into ROM.
[https://support.hp.com/us-en/help/hp-pc-hardware-diagnostics](https://support.hp.com/us-en/help/hp-pc-hardware-diagnostics)

---

### Post by gordon33 on 2023-01-12
The wi-fi worked with the old windows 11

From Bios

I clicked return to default settings in the bios.  and keyed in the 4 digit code + return.  They had a scan square and I clicked on it with my phone then scrolling I clicked on 'wireless'.  that said My "Wireless Module not supported (70X).  "
The system has detected a wireless module installed in the system that is not supported and has been disabled.
Their was a list
702 Failure to detect or connect a wireless access point
703 WWAN Module
704 Bluetooth Module
705 GPS module

Remove the new wireless module and replace with the original module

In Activites I typed Wi-Fi and a box showed up with the following:    "No wi-fi adapter found  Make sure you have a WI-FI adapter and it is plugged and turned on.

---

### Post by MAFoElffen on 2023-01-12
Report that to HP Support. If you bought that from a Certified HP Dealer, take it there.

As an On-site tech, they would have me pop the back off and reseat the module to see if it comes back up, or to replace it...

They send the part overnight shipping.

---

### Post by gordon33 on 2023-01-12
It is a mail order from the HP web site.  I will see what they say.

---

### Post by gordon33 on 2023-01-28
Hello  MAFoElffen 

I took the lap Top to one of the places that HP listed.  The geek said I needed to find a driver that would work with Ubuntu 22.04.  And they left it to me.  if they are correct how do I go about finding a driver for:
Ubuntu 22.04
HP lap top HP 15-dw4047nr.
Wifi card Realtek RTL8822CE 802.11a/b/g/n/ac (2x2) Wi-Fi® and Bluetooth® 5 wireless card[11,12,13]...

---

### Post by MAFoElffen on 2023-01-28
Here--> [https://askubuntu.com/questions/1407357/rtl8821ce-driver-not-working-on-ubuntu-22-04](https://askubuntu.com/questions/1407357/rtl8821ce-driver-not-working-on-ubuntu-22-04)

---

### Post by gordon33 on 2023-01-28
Hello MAFoElffen 

Thank you I will do some searching.

---

### Post by MAFoElffen on 2023-01-28
My curiosity is that HP's own Diagnostics program showed that it didn't even find the Wireless Card, and threw an error with a bar code stating so... 'lspci' and 'lshw' didn't show it as there. Right?

Did that change?

---

### Post by monkeybrain20122 on 2023-01-28
I am now typing from a HP pro book 440 G7, Ubuntu 22.04 works out of the box without a hitch including WIfi. My friend had exactly the same laptop but he complained his Wifi didn't work with Ubuntu. It turned out it was because he locked the BIOs, once he unlocked it wifi worked without issue.

The wifi card is the same as yours

```
$lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 15
       serial: b0:5c:da:40:5e:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:f1204000-f1204fff memory:f1200000-f1203fff
  *-network
       [B]description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 70:66:55:b0:fd:a5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.15.0-58-generic firmware=N/A ip=192.168.2.44 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:141 ioport:3000(size=256) memory:f1100000-f110ffff[/B]
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

You can boot from a Ubuntu live usb first and choose "try Ubuntu" to see if the hardware works (you may need to change the boot order in BIOS first so that it boots from usb) Or better, if you have a spare external hard drive, you can install Ubuntu in the external drive (tutorial available on these forums by C.S. Cameron) and boot from the external disk so you can have the full Ubuntu experience without installing into your main hard disk.

You shouldn't just take the word of the geek from hp on face value, I think sometimes they just tell you "no" because they are not paid to help you to install different OS on their products. When I started off with Ubuntu years ago I had an Samsung labtop with Windows 7 preinstalled. I asked Samsung tech support if Ubuntu would work they told me it wouldn't because of hardware incompatibility so I just left it at that. Meanwhile I was playing with a very old hand me down Dell laptop where Ubuntu 10.04 worked except for the Wifi so I used a dongle. But the Wifi didn't work in Windows XP either so it wasn't Ubuntu's problem.

I was thinking it was a real shame that I couldn't use Ubuntu on the Samsung laptop. One day I had the idea of just trying it out even though tech support said it wouldn't work. At that time I was more confident after playing with the Dell for a while. I thought I might be able to work around the problems. 

So I booted from the Ubuntu live usb (Ubuntu 10.10) and to my surprise, everything worked!! The only doubt was the Nvidia driver which I couldn't test on a live usb. So I made a dual boot and installed the driver (at that time I didn't know I could install Ubuntu on an external hard drive and it was a lot easier to make a dual boot with Windows 7 than with later Windows) Everything just worked! The samsung tech support guy apparently didn't know what he was talking about!. I spent more and more time on the Ubuntu partition and only logged into Windows for house keeping. Finally I made up my mind to wipe Windows and let Ubuntu take over the whole hard disk. I never looked back since. :)

---

### Post by gordon33 on 2023-01-29
results for sudo lshw -c network | grep 'product: \|driver=' for both my HP lap tops.

Wifi works on **Old ** HP lap top

gordon@gordon-HP-Laptop-15-daxxx:~$ sudo lshw -c network | grep 'product: \|driver='
[sudo] password for gordon: 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       product: RTL8723DE 802.11b/g/n PCIe Adapter
       configuration: broadcast=yes driver=rtw_8723de driverversion=5.15.0-58-generic firmware=N/A ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11



Wifi not working on **New** HP lap Top

gordon@gordon-HP-Laptop-15-dw4xxx:~$ sudo lshw -c network | grep 'product: \|driver='
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       product: Realtek Semiconductor Co., Ltd.


Am I correct both my lap tops have the same hardware for wifi?

---

### Post by MAFoElffen on 2023-01-29
Yes, buit......The second one is seeing the Ethernet, but not the WiFi in the results... Post
```

sudo lshw -c network

```
of both...

---

### Post by gordon33 on 2023-01-29
gordon@gordon-HP-Laptop-15-dw4xxx:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: 5c:60:ba:ee:e5:c8
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:50904000-50904fff memory:50900000-50903fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:50800000-508fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by gordon33 on 2023-01-29
My Bios list Bios information as Vendor Isyde Revision F.56.
Searching the web for turning on wifi in bios I find:

2  Navigate to the Security menu.
3  Choose Device Security.
4  Verify that &#8220;Wireless Network Button&#8221; is set to enable. &#8230;
5  Exit the bios from the File menu, Choose Save Changes and Exit.

So I get to step 2 and can not find  Device Security.
In the bios Security my options are: Administrator Password [clear],  Power-On Password [clear] ,   TPM Device [Available],  TPM State [Enabled], Clear TPM [No],   and  Restore Security settings to Factory Defaults.

---

### Post by MAFoElffen on 2023-01-30
I see it now...
> *-network UNCLAIMED
Post #28 is the same conditions corrected by the link in Post  #22... From what I found. Did you try that?

---

### Post by gordon33 on 2023-01-30
Hello MAFoElffen 

Thank you for all your help.

I started following the link in post # 22 after "2 Answers"  command     sudo dkms remove rtl8188fu/1.0 --all           results       dkms: command not found.  Command dkms status it said I had to install dkms.  So I  did that. and got failed to fetch.

It looked as if the information before  2 Answer was for locating the problem.  Or should I have started at the very beginning?

---

### Post by MAFoElffen on 2023-01-30
There were 3 answers that helped: At Update #1, Answer #3 and answer #0...

---

### Post by gordon33 on 2023-01-30
Will work on this tomorrow

---

### Post by gordon33 on 2023-02-01
Hello  MAFoElffen

I did not have any luck following the link in post # 22.  

I did a google search of  *-network UNCLAIMED and found several sites listed.  The 2 sights that I looked at talked about a missing driver.  So far I have been confused as the post I have looked at list a different manufacture's wifi card.  I will be searching for a driver for my wifi card.   (Realtek Semiconductor Co., Ltd.  RTL8723DE 802.11b/g/n PCIe )

One thing that puzzles me is 2 computers same type wifi card same ubuntu 22.04.  One wifi works the other does not work.

---

### Post by MAFoElffen on 2023-02-01
I found this: [https://fostips.com/realtek-wifi-drivers-ubuntu-linux-mint/](https://fostips.com/realtek-wifi-drivers-ubuntu-linux-mint/)

---

### Post by gordon33 on 2023-02-07
unable to get wifi working with  [https://fostips.com/realtek-wifi-dri...tu-linux-mint/](https://fostips.com/realtek-wifi-dri...tu-linux-mint/)

Did not find a match with the one shown in my lap top

$lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.

---

### Post by MAFoElffen on 2023-02-07
It does not make sense that both your laptops have the same wifi card, and that this one goes unrecognized... IDK

Maybe start a new thread in The Networking Section on it not being recognized???

---

### Post by gordon33 on 2023-02-08
Hello MAFoElffen 

I will make another post in a few days


gordon33

---

