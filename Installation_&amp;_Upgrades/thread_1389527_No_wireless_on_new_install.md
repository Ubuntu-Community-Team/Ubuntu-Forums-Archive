---
title: "No wireless on new install"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by DJohansson on 2010-01-24
Hello,
I am completely new to ubuntu, and I am having some installation problems. The systems seems to be running fine, but my wireless network is not working. The laptop have installed this on is a Lenovo 300 N100. 

I have found some instructions online for how to get his to work, but none seems to work. Most of the commands are just giving errors - I guess they were for older versions. I just installed the latest 9.10. 

When I run sudo iwconfig I get this response, which is supposed to be mean that the system at least knows I have a wireless network card?

   [COLOR=Red]wlan0     IEEE 802.11bg  ESSID:""  
              Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
              Tx-Power=0 dBm   
              Retry  long limit:7   RTS thr:off   Fragment thr:off
              Encryption key:off
              Power Management:off
              Link Quality:0  Signal level:0  Noise level:0
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]


Some instructions said I needed to install something called ndiswrapper. The system gave me a command to use for this, but that one didn't work, which seemed very odd... I think I got it installed now though, and when I type in ndiswrapper -l I get the following


 [COLOR=Red]ndiswrapper -l
    
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
    
bcmwl5 : driver installed
    
      device (14E4:4311) present (alternate driver: ssb)[/COLOR]

Doesn't that mean that I have the driver installed? Still, nothing seems to be working. This page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) is telling me to open the network admin tool (system > administration > networking) but I don't even have that alternative in the menu. 

Any suggestions? 

Thanks!

---

### Post by darkod on 2010-01-24
Do you know where the Network Manager icon is? It's one of those icons in the top right bar, next to the time. For wireless it looks like the icon showing the network strength on your mobile, few bars with different height.

Left click that icon and it will show list of available networks, if it can see any (if it's working properly). If you do get your network there, click on it and continue with the setup, to enter your network password, etc.

I don't know whether you tried the above and if that didn't work.

---

### Post by DJohansson on 2010-01-24
Thanks. Yes, I did try this and under Wireless it says 'device not ready. I have right-clicked on this and added the wireless network manually, but that seems to do nothing.

---

### Post by a1gevaldig on 2010-01-24
I also just installed linux 9.10 and it doesnt detect my wireless card

but ehen i run it live from the cd it does work fine

any help? please

---

### Post by mr clark25 on 2010-01-24
> **DJohansson said:**
> Thanks. Yes, I did try this and under Wireless it says 'device not ready. I have right-clicked on this and added the wireless network manually, but that seems to do nothing.


is your card enabled in the bios of your computer?

i had the same problem untill i enabled it in my motherboard's bios.

---

### Post by derekmbarnes on 2010-01-24
Need more information. Open Terminal and run this command:

```
lspci -v | less
```

Look for "Network controller" in the list that comes up and post the details.

---

### Post by DJohansson on 2010-01-25
Yes, I think the card is activated in the BIOS. I had Windows Vista installed on the machine before, and the wireless was working then.

This is what I get when I use the lspci command.

   [COLOR=Red]03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/COLOR]
    [COLOR=Red]        Subsystem: Broadcom Corporation Device 0465[/COLOR]
    [COLOR=Red]        Flags: bus master, fast devsel, latency 0, IRQ 17[/COLOR]
    [COLOR=Red]        Memory at d0000000 (32-bit, non-prefetchable) [size=16K][/COLOR]
    [COLOR=Red]        Capabilities: <access denied>[/COLOR]
    [COLOR=Red]        Kernel driver in use: b43-pci-bridge[/COLOR]
    [COLOR=Red]        Kernel modules: ssb[/COLOR]
  
  
Thanks!

---

### Post by mr clark25 on 2010-01-26
I hear that windows has some odd way around the bios settings. i would check and make sure that it is enabled.

---

### Post by wfamolim on 2010-01-26
Recently I installed Ubuntu 9.10 on my old HP pavilion zv5240us notebook computer. I installed it over the top of Windows XP and intentionally wiped out XP. During the installation, Ubuntu automatically recognized my &#8220;wired&#8221; internet connection. The installation was simple and faultless. I have always been a Windows person but had no problem with the installation of Ubuntu.
 

 Ubuntu did not automatically recognize my D-Link wireless notebook adapter card (DWL-G650M). There are no Linux drivers for it on the D-Link website.
 

 Using the wired connection to my Notebook, I did some internet research (Firefox - Google) and saw references to &#8220;ndiswrapper&#8221; (which meant nothing to me) and for the need to use it with the Windows driver for my wireless card in order to allow Ubuntu to recognize and install the card. I also saw a reference to a Synaptic package manager.
 

 Next I researched the Synaptic manager and learned that it is a Windows-type interface to be used for installing software in Ubuntu. I learned that Synaptic makes it unnecessary to use an application called Terminal where one enters commands that are not, to me, obvious. I decided that I would not waste my retirement (I am 70 years old) by trying to learn how to use Terminal. If Synaptic did not cut it, I would just have to live with a wired Notebook.
 

 I went to the D-Link website and found the support and download page for my wireless adapter. I downloaded the driver package and extracted it within the Ubuntu download folder. Then I made a new &#8220;Wireless&#8221; folder and moved the *.sys and *.inf files for my adapter into that folder.
 

 I found the Synaptic manager in Ubuntu's System &#8211; Administration menu. It was called Synaptic Package Manager. In this manager, I easily located three related items: ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9. I installed them by using the package manager. Somewhere in this process I was asked to identify the *.inf file for my adapter card. I can't remember the details.
 

 My recollection is that I next unplugged my wired connection from the Notebook and then restarted my Notebook.
 

 Then, because I had seen an online wiki explaining the use of &#8220;ping&#8221;, I opened Ubuntu's System &#8211; Administration &#8211; Network Tools, and found a ping sub-menu. I pinged my router. There was a response so I knew that Ubuntu had installed my wireless adapter card. Of course I was overjoyed at this good fortune.
 

 Because of the same online wiki, I knew that I should now try to log in to my wireless network, which I did by using Ubuntu's System &#8211; Preferences &#8211; Network Connections menu. There is a sub-menu called Wireless. I was able to log in, and I checked the box that would make this happen automatically in the future.
 

 Bill (Ubuntu novice)
 January 26, 2010

---

### Post by DJohansson on 2010-01-27
Thanks. I did double-check on the bios setting. I assume this is the 'internal modem' under the advanced settings, and this was set to enabled.

In the OS itself, I have installed ndiswrapper and I can run ndisgtk - Wireless Network Drivers. I went to this page: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4311](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4311) and downloaded the driver that was linked there. I extracted the driver file on a different computer, and brought all the files into ubuntu. There I clicked 'install new driver' in the Wireless Network Drivers, and selected the "bcmwl5.inf" file from the driver directory. When I click 'Install' I get an error saying 'unable to see if hardware is present'. Once I click OK on that I see the bsmwl5 driver in the list and it says 'Hardware present: Yes' below it. There is a button that says Configure Network, but when I click that, all I get is an alert saying 'could not find network configuration tool'. 

Any suggestions?

Thanks!

---

