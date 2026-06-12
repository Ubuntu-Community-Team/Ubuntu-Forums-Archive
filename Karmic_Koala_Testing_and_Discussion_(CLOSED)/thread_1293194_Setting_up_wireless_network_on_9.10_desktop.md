---
title: "Setting up wireless network on 9.10 desktop"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by RyanfromtheShire on 2009-10-16
I just installed 9.10 desktop on my lenovo ideapad s10e and I'm trying to set up a wireless network. For some reason I can't install ndiswrapper, but I think the drivers have already been installed anyways.

I have entered all the information correctly, but it won't let me hit "apply":

[http://img131.imageshack.us/img131/7204/screenshotvu.png](http://img131.imageshack.us/img131/7204/screenshotvu.png)

[http://img148.imageshack.us/img148/9136/screenshot1zn.png](http://img148.imageshack.us/img148/9136/screenshot1zn.png)

Any ideas on what is wrong?

---

### Post by Sef on 2009-10-16
moved.

---

### Post by forumache on 2009-10-17
> **RyanfromtheShire said:**
> I just installed 9.10 desktop on my lenovo ideapad s10e and I'm trying to set up a wireless network. For some reason I can't install ndiswrapper, but I think the drivers have already been installed anyways.

I have entered all the information correctly, but it won't let me hit "apply":

[http://img131.imageshack.us/img131/7204/screenshotvu.png](http://img131.imageshack.us/img131/7204/screenshotvu.png)

[http://img148.imageshack.us/img148/9136/screenshot1zn.png](http://img148.imageshack.us/img148/9136/screenshot1zn.png)

Any ideas on what is wrong?

Maybe you don't need ndiswrapper if your wireless card is supported directly.

If your SSID is broadcasted, the only thing left to do is right click on the NetworkManager, see if you see your SSID there (and maybe others detected around), click on it, it will ask for password, enter it, done.

No need to install anything. If it doesn't work it will help if you provide the model of your wireless card (lspci or lsusb output, depends if it is internal or usb connected).

---

### Post by Mike_IronFist on 2009-10-17
Just an FYI, if you can detect wireless networks and connect to them with your wireless card right now, you don't need ndis wrapper.

---

### Post by RyanfromtheShire on 2009-10-17
Yeah the wireless networks aren't showing up when I right click on the network icon, so I tried manually setting it up. I thought it should automatically detect the networks around me. So maybe the wireless card isn't installed?

I believe my network card is a Wireless Broadcom BCM4312. I run a hardware test, and it detects the card, but doesn't detect my wifi. The only way I can connect is by plugging my computer in directly. Any ideas?

also, when I tried to install ndiswrapper, I get this issue:

```

ryan@Darla:~$ sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

```

---

### Post by forumache on 2009-10-19
> **RyanfromtheShire said:**
> Yeah the wireless networks aren't showing up when I right click on the network icon, so I tried manually setting it up. I thought it should automatically detect the networks around me. So maybe the wireless card isn't installed?

I believe my network card is a Wireless Broadcom BCM4312. I run a hardware test, and it detects the card, but doesn't detect my wifi. The only way I can connect is by plugging my computer in directly. Any ideas?


when you right click you don't see the networks. if your wireless is detected you get: Enable Wireless Connection checkbox.

If your card is supported, you click (this mean *left* click) in order to get the list of the wireless networks around.

To be sure of the model of your wireless card, please run lspci and/or lsusb and put the output here.

You can also run dmesg and see if something related with your wireless card appears in the text displayed.

---

### Post by fjosh on 2009-10-19
I believe the 4312 is supported under bcmwl-kernel-source

---

### Post by RyanfromtheShire on 2009-10-19
Yeah I'm not getting the wireless network options when I right or left click.

Anyways, here is my lspci:

> 
ryan@Darla:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)



@fjosh: what exactly is bcmwl-kernel-source?

---

### Post by fjosh on 2009-10-19
Search synaptic package manager for bcmwl-kernel-source

system > administration > synaptic package manager

or from terminal > sudo apt-get install bcmwl-kernel-source

It should be installed by default so maybe try reinstalling it.

---

### Post by forumache on 2009-10-20
Your last line from lspci output shows that you indeed have a bcm4312 as you suspected.

If you search on Ubuntu forums on bcm4312 you'll see this thread: [http://ubuntuforums.org/showthread.php?t=1056446]("http://ubuntuforums.org/showthread.php?t=1056446")

I read it but it seems a little bit difficult to understand. You might want to try something simpler first: boot from the CD you installed Ubuntu from. Choose "Try Ubuntu without modifing my harddisk" (or something like that). It will boot and run completely from the CD, without touching your HDD. See if here you have wireless (it is known to happen, everything work perfectly with LiveCD, but not after you install).

Also you might want to post the output from lsmod command, which will show the list of kernel modules that are loaded. Maybe the one for your wireless card is not loaded or it conflicts with other one (it seems that there are two: b43 and wl)

---

### Post by RyanfromtheShire on 2009-10-20
> **fjosh said:**
> Search synaptic package manager for bcmwl-kernel-source

system > administration > synaptic package manager

or from terminal > sudo apt-get install bcmwl-kernel-source

It should be installed by default so maybe try reinstalling it.

This worked! Thanks! I also realized that I wasn't able to access the repositories because I hadn't checked them in the synaptic package manager. DUH.

Anyways, thanks everyone for your help.

---

