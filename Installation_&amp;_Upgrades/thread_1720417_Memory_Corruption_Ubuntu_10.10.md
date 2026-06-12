---
title: "Memory Corruption Ubuntu 10.10"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by musdawdaf on 2011-04-03
hey 
I installed almost all distributions of linux ( suse fedora mint lubuntu ubuntu kubuntu).All of these system quickly failed.
Gave an error like Low Memory Corruption at .... this error happens when im trying to boot.I cannot see even the login screen.
after all these Ubuntu 10.10 worked well.Before this I used cable to connect internet, but I didnt connect to internet so it was a just pure Ubuntu 10.10

I tried all test about hibernating suspend or sth else.They all worked good.But after first reboot I couldnt see login screen again.Its just waiting with black screen.When I use ESC before the this black screen I saw that there is a memory corruption error again

But if I login with Recovry Failsafex it worked good.I searched on web and ubuntuforums.org and tried all recommended ways to solve this problem, no one solved this.Pls do not say search that there are many threads in forum.
Also I tried to update kernel it didnt work too.

Here is my system.

Hp Pavillion DV6 3114-et
Intel i5-560M 
4 GB ram
Ati HD 5650 and &#304;ntel HD 

I tried these 

Ubuntu 10.10 x64
Lubuntu 10.10 x86
Kubuntu 10.10 x64

and now Im using Ubuntu 10.10 x64

---

### Post by Quackers on 2011-04-03
Welcome to UF.
Have you tested the ram?

---

### Post by musdawdaf on 2011-04-03
oh finally it finished the test 
both harddisk and ram are ok.no problem
its probably about ubuntu :/
but like I said before, linux work with failsafex mod well.
There may be a problem about the ati5650 drivers

---

### Post by Pumalite on 2011-04-03
A mem test should run 8 HRS minimum

---

### Post by Hedgehog1 on 2011-04-03
> **musdawdaf said:**
> I installed almost all distributions of linux ( suse fedora mint lubuntu ubuntu kubuntu).All of these system quickly failed.
Gave an error like Low Memory Corruption at .... this error happens when im trying to boot.I cannot see even the login screen.
....
But if I login with Recovry Failsafex it worked good...

This memory error may not be from your system RAM, but from your video card's RAM.  If it didn't happen at install, and it's not happening in failsafe, nether of these modes use your video card very hard.

An easy(ish) way to tell is to remove your ATI card and run the PC off the on-board video.  If it works reliably using on-board video,  Your ATI video card has bad RAM in it.


***The Hedge***

:KS

p.s. Becuase non Ubuntu distros also failed (Suse Fedora), I don't belive that this is *"probably about ubuntu"*.  Sorry.

---

### Post by musdawdaf on 2011-04-03
How can I test my graphic card memory?
Any suggestion for this and also RAM.

---

### Post by musdawdaf on 2011-04-03
Ok I finished the test of graphic card memory after 4 hours
No error found.....
Its absolutely about the Linux Ati Driver 
I think i should wait for Ubuntu 11.04.
And also I figured out that this error have been seeing since kernel 2.....idk the exact version.I hope there would be no error about this with new version.

---

### Post by Hedgehog1 on 2011-04-03
> **musdawdaf said:**
> Ok I finished the test of graphic card memory after 4 hours
No error found.....
Its absolutely about the Linux Ati Driver 
I think i should wait for Ubuntu 11.04.
And also I figured out that this error have been seeing since kernel 2.....idk the exact version.I hope there would be no error about this with new version.

Well, I am willing to change sides on this after all your testing. The ATI support after kernal 2.~~.~~~ <tbd> doesn't work with your hardware anymore.

Will you work in failsafe mode in 10.10 for now?  Or go back to 10.04.02 until natty is really ready?

***The Hedge***

:KS

---

### Post by musdawdaf on 2011-04-04
> **Hedgehog1 said:**
> Well, I am willing to change sides on this after all your testing. The ATI support after kernal 2.~~.~~~ <tbd> doesn't work with your hardware anymore.

Will you work in failsafe mode in 10.10 for now?  Or go back to 10.04.02 until natty is really ready?

***The Hedge***

:KS

Nope,I have already a Win 7 license, so I ll use Win7 till 11.04.Im not sure that will work with 10.04.But I have to find a distribution which works with ati because of my Operating Systems course.My professor advise me to use 8.04 and its absolutely ridiculous :D
But here is the another solution:
This computer has two graphic cards ati 5650 and  intel HD
By removing Ati it should work probably.Its not a big deal because im using mostly LUBUNTU.I ll try it and write here the result soon.

---

### Post by Dutch70 on 2011-04-04
If you have a partition on your hdd already, you may want to consider going ahead and installing 11.04. You obviously wouldn't be depending on it, and it's scheduled to be released in a few weeks now. 

I've found the stability to be fairly good lately, but remember that if you do install it. It's not easy to get help with, there is a section here for Natty testing & development. Support questions placed here will be moved there.

You'd just be reporting any bugs you find to help out with the development, while also getting used to it.

---

### Post by musdawdaf on 2011-04-04
> **Dutch70 said:**
> If you have a partition on your hdd already, you may want to consider going ahead and installing 11.04. You obviously wouldn't be depending on it, and it's scheduled to be released in a few weeks now. 

I've found the stability to be fairly good lately, but remember that if you do install it. It's not easy to get help with, there is a section here for Natty testing & development. Support questions placed here will be moved there.

You'd just be reporting any bugs you find to help out with the development, while also getting used to it.
Ohh finally Im not going to wait for 11.04.
Its all about Linux Ati Drivers
I couldnt wait without doing sth and I installed Ubuntu 10.10 again
First reboot was OK again I didnt install any Ati driver when I checked the graphic card with
$ lspci
I saw that its still Ati.I rebooted and fail...
Again rebooted in failsafex mode and just installed intel HD graphic card driver.
$ sudo add-apt-repository ppa:glasen/intel-driver 
$ sudo apt-get update && sudo apt-get upgrade
I looked at graphic card it was Intel HD
There is a VGA Ati below and I should better get rid of this :D
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```And rebooted 
Booom.Its working well now.I reboot over 15 times to try it will give an error but it didnt.

But I still want to test 11.04..

---

### Post by Hedgehog1 on 2011-04-04
> **musdawdaf said:**
> Ohh finally Im not going to wait for 11.04.
Its all about Linux Ati Drivers
I couldnt wait without doing sth and I installed Ubuntu 10.10 again
First reboot was OK again I didnt install any Ati driver when I checked the graphic card with
$ lspci
I saw that its still Ati.I rebooted and fail...
Again rebooted in failsafex mode and just installed intel HD graphic card driver.
$ sudo add-apt-repository ppa:glasen/intel-driver 
$ sudo apt-get update && sudo apt-get upgrade
I looked at graphic card it was Intel HD
...
And rebooted 
Booom.Its working well now.I reboot over 15 times to try it will give an error but it didnt.

But I still want to test 11.04..

[SIZE="4"]EXCELLENT!!![/SIZE]

**Thanks for sharing the solution.**  To be clear - the install had mis-identified your Intel video as ATI video and loaded the wrong driver? I want to be sure I understand it before I have some other poor soul testing memory (when it isn't really needed).

***The 'curious' Hedge***

:KS

---

### Post by Dutch70 on 2011-04-05
Nice work! 

If you want to test 11.04, It's best to do it with...
a) virtualbox
b) usb stick
c) a small partition on your hdd.

Good luck

---

### Post by musdawdaf on 2011-04-05
> **Hedgehog1 said:**
> [SIZE=4]EXCELLENT!!![/SIZE]

**Thanks for sharing the solution.**  To be clear - the install had mis-identified your Intel video as ATI video and loaded the wrong driver? I want to be sure I understand it before I have some other poor soul testing memory (when it isn't really needed).

***The 'curious' Hedge***

:KS

At first Ubuntu doesnt care that I have a Intel HD and just try to use Ati.By applying this now I can see there is a Intel HD card and it starts to use this but still it was asking about loading Ati driver and I closed it. Now just using Intel HD and work pretty well.

---

