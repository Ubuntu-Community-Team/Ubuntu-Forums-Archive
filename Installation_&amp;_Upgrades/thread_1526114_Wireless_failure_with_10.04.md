---
title: "Wireless failure with 10.04"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-07-07
First, I know that there has been many, many messages posted on problems with wireless network connections in Ubuntu 10.04. And I have read many of these carefully. However, I still am unable to find a solution to this (and my) problem. Why? Ans. Many of the solutions given assume that you can access the internet (in Ubuntu) by other means than a wireless connection. 
 
More specifically, I am running a dual platform: Windows 7 -- Ubuntu 10.04. I only recentlly installed 10.04 and things seem rather good except for connection to the internet via wireless. My wireless driver is Broadcom Corporation and I am trying to get it to work on a HP Pavilion dv6 Notebook PC. Note, my wireless connection works fine under Windows 7.
 
It seems that many other Ubuntu 10.04 users are having this same problem.
 
Any, suggestions on how this can be fixed would be appreciated greatly. And I will gladly post all methods that work for my system --- hopefully this will help others in the same boat!
 
Also, I would be glad to provide more detailed hardware/software information on my system if needed.
 
Thanks, V

---

### Post by davidmohammed on 2010-07-07
Can I presume your notebook has a ethernet port?  If so, connect your notebook to your router.  Check that internet connectivity is available.  Then goto your administrator - hardware drivers page.

---

### Post by Old_Grey_Wolf on 2010-07-07
I've had the same problem. I have spare Linksys and Netgear USB network adapters for those situations. I can get either the Linksys WUSB54GC or the Netgear WG111 working on most distros. After I am connected, I can get the drivers for the Broadcom installed. I am using the Broadcom STA driver that showed up in "System > Administration > Hardware Drivers".

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> Can I presume your notebook has a ethernet port? If so, connect your notebook to your router. Check that internet connectivity is available. Then goto your administrator - hardware drivers page.
 
Yes, I have an eithernet port; but, not cables or router for connection. I only have a wireless box with no other possible conncections.

---

### Post by davidmohammed on 2010-07-08
The packages you need are from the ubuntu restricted repositories and hence you need a working internet connection i.e. they cannot be distributed with the ubuntu installation CD due to broadcom licensing conditions.

Suggest find a friend that you can connect to their router via the wired connection - or more expensively, buy a wireless router yourself with ethernet ports!

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> The packages you need are from the ubuntu restricted repositories and hence you need a working internet connection i.e. they cannot be distributed with the ubuntu installation CD due to broadcom licensing conditions.
 
Suggest find a friend that you can connect to their router via the wired connection - or more expensively, buy a wireless router yourself with ethernet ports!
 
But I do have a working internet connection (as I stated in my original posting). That is, I can connect (via the same wireless box) in Windows 7. My questions are now.
 
1) What package (file) should I download to my Windows 7 system?
2) Then when I boot to Ubuntu 10.04, how do I install this package in Ubuntu?
 
--Thanks for you help.

---

### Post by davidmohammed on 2010-07-08
ok - in that case - sugggest go [here]("http://packages.ubuntu.com/lucid/b43-fwcutter") and download either the 64 bit or 32bit package depending on which version of the O/S you have installed.

Once you've downloaded - load into ubuntu and double click the deb file.

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> ok - in that case - sugggest go [here]("http://packages.ubuntu.com/lucid/b43-fwcutter") and download either the 64 bit or 32bit package depending on which version of the O/S you have installed.
 
Once you've downloaded - load into ubuntu and double click the deb file.
 
Ok, I went to the link where you suggested and then at the bottom of the page I clicked on the link corresponding to my 32-bit requirement, and this led me to
 
[http://packages.ubuntu.com/lucid/i386/b43-fwcutter/filelist](http://packages.ubuntu.com/lucid/i386/b43-fwcutter/filelist)
 
Here there 8 files.
1) Which one(s) should be downloaded?
2) How should I use them to resolve my problem?
 
Thanks for the help.

---

### Post by davidmohammed on 2010-07-08
click the architecture link not the filelist.

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> click the architecture link not the filelist.
 
Ok, I have done this. I have downloaded the file (using Windows 7). But now, how do I find this file when booted up in Ubuntu 10.04?
 
Note, I have gone to **Places** and looked at all of the folders:
 
Home Folder
Desktop
Documents
Music
Pictures
Videos
Downloads
Computer
SYSTEM
HP_TOOLS
Network
 
but could not find any files that I have in Windows 7.

---

### Post by davidmohammed on 2010-07-08
Can I suggest the easiest way would be to download and save to a memory stick.  When you boot into ubuntu then you can read directly from the memory stick.

I'm assuming from your question that you haven't mounted your Windows 7 hard-drive from ubuntu?

Don't know how to do this myself since I've only ever done this with Windows XP.  For WinXP i downloaded a package called ntfs-config.

---

### Post by virsto on 2010-07-08
> **virsto said:**
> Ok, I have done this. I have downloaded the file (using Windows 7). But now, how do I find this file when booted up in Ubuntu 10.04?
 
Note, I have gone to **Places** and looked at all of the folders:
 
Home Folder
Desktop
Documents
Music
Pictures
Videos
Downloads
Computer
SYSTEM
HP_TOOLS
Network
 
but could not find any files that I have in Windows 7.
 
Oops! I found the folder:
 Places->File System->host->Users->Virgil->Downloads
 
I then tried to install (double clicking on the *.deb file). I first tried the i386 file which was for the wrong architecture (I am running a 64-bit Windows 7 but a 32-bit Ubuntu because it does not like my CPU that I am using). I then tried the am64 file and this failed to install also. The following is from a terminal window when trying to install from the am64 *.deb file:
 
...
```
 
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess installed post-installation script returned error exit status 4
Processing triggers for man-db ...
Error were encountered while processing
 b43-fwcutter

```

---

### Post by davidmohammed on 2010-07-08
... as I feared - the deb file needs to find more information from that website - its not all self contained.

I'm sure you can hack this - but to be honest, I would advise you to find a router/friend's router that has ethernet ports.

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> ... as I feared - the deb file needs to find more information from that website - its not all self contained.
 
I'm sure you can hack this - but to be honest, I would advise you to find a router/friend's router that has ethernet ports.
 
Well, thanks for you confidence in my hacking ability; but, I actually have no idea how to "hack" this.
 
This reminds me of a "catch-22" situation --- To get your wirless working you need to connect to the network; but, you can not connect to the network because your wireless is not working!
 
Surely, there is a way around this --- if only someone could provide some more suggestions then perhaps we could together converge to a solution.;)

---

### Post by virsto on 2010-07-08
> **davidmohammed said:**
> ... as I feared - the deb file needs to find more information from that website - its not all self contained.
 
I'm sure you can hack this - but to be honest, I would advise you to find a router/friend's router that has ethernet ports.
 
I did download the DVD file for Ubuntu. Do you believe that this could be used to fix the problem?

---

### Post by pmenefee on 2010-07-08
Not to throw a negative comment at you, but after you get as frustrated with 10.4 as I got, then get the 9.04 cd and use it.  9.04 wireless works.

---

### Post by davidmohammed on 2010-07-08
> **pmenefee said:**
> Not to throw a negative comment at you, but after you get as frustrated with 10.4 as I got, then get the 9.04 cd and use it.  9.04 wireless works.

I doubt 9.04 came with broadcom drivers.

Here is a quote from the [linux wireless website]("http://linuxwireless.org/en/users/Drivers/b43")

> The Broadcom wireless chip needs software, called "firmware", that runs on the wireless chip itself during operation. This firmware is copyrighted by Broadcom and must be extracted from Broadcom's proprietary drivers. To get such firmware on your system, you must download the driver from a legal distribution point, as noted below. Then you must extract the firmware from that Broadcom driver by using b43-fwcutter (or bcm43xx-fwcutter) and install it in the special directory for firmware - usually /lib/firmware. Please note that the firmware from the binary drivers is copyrighted by Broadcom Corporation and must not be redistributed.

Some distributions have special methods for installing the firmware. In general these consist of a special command entered at a terminal. Because the proprietary driver containing the firmware cannot be included in the distribution, you will need a working connection to the Internet. 

... in summary you need a working internet connection to get their driver and firmware to install!

---

### Post by pmenefee on 2010-07-09
David, all I'm saying is that you can work and toil to make 10.04 wireless work, or you can just go back to 9.04....turn it on and it works.  I don't know why...drivers, kernel, etc.  I'm not a techie.  I'd rather have it work than play with it trying to make it work.  This suggestion came from other threads on this board.  I tried it and the same machine hooks up nicely to my home network, and 10.04 simply will not.  I hope they fix it.

I'm running 10.04 at the office connected by cable.

---

### Post by davidmohammed on 2010-07-09
> **pmenefee said:**
> David, all I'm saying is that you can work and toil to make 10.04 wireless work, or you can just go back to 9.04....turn it on and it works.  I don't know why...drivers, kernel, etc.  I'm not a techie.  I'd rather have it work than play with it trying to make it work.  This suggestion came from other threads on this board.  I tried it and the same machine hooks up nicely to my home network, and 10.04 simply will not.  I hope they fix it.

I'm running 10.04 at the office connected by cable.

virsto - suggest you give pmenefee's idea a try - download the desktop image and run it as a live CD (i.e. try without installing) - see if you can "turn it on and it works"

---

### Post by virsto on 2010-07-11
> **davidmohammed said:**
> The packages you need are from the ubuntu restricted repositories and hence you need a working internet connection i.e. they cannot be distributed with the ubuntu installation CD due to broadcom licensing conditions.
 
Suggest find a friend that you can connect to their router via the wired connection - or more expensively, buy a wireless router yourself with ethernet ports!
 
Ok David,
I am still trying to fix the wireless problem --- I have not given up yet. :)
 
The current state of things:
1) I purchased an internet cable and was able to make and good internet connection in Ubuntu 10.04 --- this took a while but finally succeeded. (I have attached an image showing the settings for the cable internet connection).
 
2) I then successfully installed the recommended file:
 
b43-fwcutter_012-1build1_amd64.deb
 
3) I then tried to connect to my wireless router --- still no connection! It seems that I am unable to activate the wireless hardware!
 
I have attached images for some the setting attempted for the wireless. Please take a look at them and make any suggestions that you have for solving this problem.

---

### Post by virsto on 2010-07-11
Images did not get attached --- why??

---

### Post by davidmohammed on 2010-07-12
OK - step by step,
  

Connect via your wired connection - make sure you have a good internet connection.

When you go to administration - hardware drivers, do you have any restricted drivers offered to you?  I hope you see one or two drivers, a broadcom STA and/or a b43 cutter. 

Is either of them "activated" - from memory there should be a green light against one of them - hopefully the b43 cutter.

Next, click on your network manager - you should see your wireless network being offered to you - do you?

If you don't, then I guess the correct firmware for your wireless card has not been found. If so, goto administration - synaptic manager.  Search for "firmware" - it should display two wireless firmware packages.  Install both of these.  Reboot.  Check your network manager again.  You should now hopefully see your wireless network being offered to you.

---

### Post by virsto on 2010-07-16
Finally a solution --- thanks to David's perseverance on this irritating problem. First, it is important to note that I am running Ubuntu 10.04 (64-bit) in dual-boot mode.
The solution (specific to my system) is as follows:

1) Download (in Windows) the following file (see previous postings on this file):

    b43-fwcutter_012-1build1_amd64.deb

 I then saved this file in a USB memory stick.

2) Boot-up Ubuntu 10.04 and copy this file from the memory stick to the desktop

3) Install it (double-click on the file).

4) Execute --- System -> Administration -> Hardware Drivers

    and then activate the driver corresponding to the downloaded file

THIS LAST STEP IS IMPORTANT!

And that's it!
Thanks again for the help.
Have a good day ;)

---

### Post by digitalcitizenx on 2010-07-16
> **virsto said:**
> 
 
but could not find any files that I have in Windows 7.

:-s

---

### Post by agan on 2010-07-16
If you have a problem with wireless u need to go by steps

need to check following command outputs
                     iwconfig
                     ifconfig wlan0/ath0 down
                     ifconfig wlan0/ath0 up
                     iwlist scan waln0
                     lspci -C network

                then check ur firware of card vs linux kernel. U need network manager running to see the wireless network status. main issues are with the firmware of wirlesscard and kernel. You can download the firmware and copy to the firware folder and reboot.

if no success post the outputs of above commands

                                     success

---

