---
title: "lubuntu Version 19.04 Login problems"
date: 2019-09-06
forum: Installation &amp; Upgrades
---

### Post by ews2k on 2019-09-06
Hi all,

I have an old (but hardly used) HP Compaq Mini110 32-bit Notebook PC that was running WinXP. XP has more than reached end of life so I browsed the Internet for a light Linux OS that should be compatible with this PC.

I downloaded and installed the latest 32-bit version of lubuntu Version 19.04 via a USB stick, and all went well - initially. When trying to boot up into lubunto, I enter my log in name which the PC accepts, but it refuses to accept my password, the cursor does not even move across the screen when I type in my pass word.

What are my options? I have tried running a repair but still no luck. Is there any way I can boot into lubuntu and remove/edit my login details?

Thanks in advance,

Eric

---

### Post by guiverc on 2019-09-06
Lubuntu 19.04 x86/32bit ISOs stopped being produced dec-2018 and were in early-alpha stage and never actually released.  The only Lubuntu 19.04 that has been released was amd64 (64-bit); if you want to check view [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

As a result, I'm wondering what you really downloaded (and from where? as the official Lubuntu site doesn't offer and has never offered a x86/32bit 19.04).  I don't know about non-Ubuntu/non-Lubuntu sites (but know of their existence).

Do you have 19.04?  or do you have something else other than Lubuntu?

The last Lubuntu release in x86/32bit was Lubuntu 18.10, but it's now EOL (*end-of-life*) - 32bit users were advised to stick with Lubuntu 18.04 LTS (2018-April release with 3 years of support) which is supported until 2021-April as 18.10->19.04 upgrades were officially unsupported (possible yes, but unsupported). 

Myself - I'd be checking what you're actually running.   Also if you're unsure of where to download a flavor, stick to finding out the official site by going to ubuntu.com (ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)) and follow links from there; and don't ask google.com as it often favors unofficial sites (*of which there are many, including non-english*) that are not related at all with Ubuntu or Lubuntu team.

*fyi: I do have a Lubuntu 19.04 x86 system here (a test system) so maybe able to help, but believe you'll find yours is something different.*

---

### Post by ews2k on 2019-09-06
Thank you for your reply.

I downloaded the 32-bit version of what I thought was version 19.04 here:

[https://lubuntu.net/downloads/](https://lubuntu.net/downloads/)

"Alternative Previous  Image" just under the blurb on the 64-bit download. I just assumed it was a 19.04 release, but it obviously is not as the filename refers to 18.04.

How would I go about uninstalling this, is it at all possible? I kept the WinXP OS on it until I was happy with lubuntu but my networking capabilities have also been compromised since the lubuntu install.

-Eric

---

### Post by oldfred on 2019-09-06
When you type password into system, cursor does not move or show anything. 
You have to blind type correct password.
So are you sure you are typing in the same password you created when you installed system?
If I have shift key on, it usually tells me, but not sure if Lubuntu also does that or not.

---

### Post by ews2k on 2019-09-06
Yep, I typed in the correct password, no reaction and after timeout it simply requests log-in details again.

Short of reformatting the hard drive, I would like to remove the OS completely and try again, unless there is a way of bypassing the log-in screen.


-Eric

---

### Post by oldfred on 2019-09-06
If you press & hold shift key from BIOS screen until grub menu appears you may be able to go into recovery mode.

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by guiverc on 2019-09-07
Please note *lubuntu.net* is **not** a Ubuntu or **Lubuntu** site, so I would definitely suggest you md5sum/sha256sum the ISO you used with the what the official site suggests it should be before you trust it (or what you installed from it).  It may be a valid ISO or it may not be - so you should ensure it is.  (you got it from a '*fan*' site)

I provided the official site, or suggested using ubuntu.com and following that links to stick to official Ubuntu/Ubuntu-flavor sites.  You don't need to uninstall it, just install over it if you don't want it anymore.

If it turns out the sha/md5 checksums are valid, you can probably trust it, but I'd suggest you do this before you worry about problems with your install, as you're not starting with an *official Lubuntu image* that came from either Ubuntu or Lubuntu.

Checksums can be found at [http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)

---

### Post by ews2k on 2019-09-07
My bad, I thought it was an official site :(

I will attend to this on Monday, the machine is at work. Thank you to all for the good advice.

-Eric

---

### Post by ews2k on 2019-09-10
No joy with whatever I tried, so having worked with Linux Mint in the distant past, I downloaded and installed it. The installation worked perfectly, except for the Broadcom BEM4312 wireless adaptor. Try as I might, none of the drivers I found on the internet would work. So I will probably look for another suitable version of Linux and try that although I might still end up with a wi-fi adaptor problem.


-Eric

---

### Post by mörgæs on 2019-09-10
Since you at least have something running please copy **sudo lshw -sanitize > lshw.txt** and paste it to the command line, run it and post lshw.txt in CODE tags. It will tell us all about the hardware.

---

### Post by GhX6GZMB on 2019-09-10
The official Lubuntu download site is here:
[https://lubuntu.me/](https://lubuntu.me/)

Make a new DVD/USB install image from there.
Your PC is 64-bit capable, and in my experience the install is painless, but takes up to an hour.

---

### Post by ews2k on 2019-09-11
> **mörgæs said:**
> Since you at least have something running please copy **sudo lshw -sanitize > lshw.txt** and paste it to the command line, run it and post lshw.txt in CODE tags. It will tell us all about the hardware.


Running **sudo lshw -sanitize > lshw.txt** in Terminal mode gives me:

PCI (sysfs)   (which then disappears, followed by:)
USB              (which also then disappears)

I'm not sure what you mean by this:
 post lshw.txt in CODE tags ?

If I type lshw.txt then the command is not recognised.

As you can see, I'm totally a newbie at Linux.




-Eric

---

### Post by ews2k on 2019-09-11
What does happen now is that at least the WiFi Adaptor is recognised under Network Connections and I can switch it on. It still does not connect however, even when the correct credentials are entered.

I downloaded so many Broadcom BEN 4312 (bcmw-kernel-source) yesterday I have no idea which one worked.


-Eric

---

### Post by ews2k on 2019-09-11
> **ml9104 said:**
> The official Lubuntu download site is here:
[https://lubuntu.me/](https://lubuntu.me/)

Make a new DVD/USB install image from there.
Your PC is 64-bit capable, and in my experience the install is painless, but takes up to an hour.

Thanks, busy downloading the 32-bit 1804 and will see what happens.

I also found this link, seems the CPU is 64-bit capable, but not the notebook.
[https://askubuntu.com/questions/786119/installing-64-bit-ubuntu-on-hp-mini-110]("https://askubuntu.com/questions/786119/installing-64-bit-ubuntu-on-hp-mini-110")


Eric

---

### Post by Dev'olution on 2019-09-11
Have you tried downloading the server version of Ubuntu and then adding packages manually bit by bit... 

e.g, first the lubuntu desktop, then the wireless drivers?

---

### Post by ews2k on 2019-09-11
I booted the notebook from the USB drive using this lubuntu version: lubuntu-18.04.3-desktop-i386

Again no wireless, then I checked for a new driver using Hardware Drivers. Again, it stated that the bcmwl driver installed is not working and should be disabled. However, in LinuxMint, the driver appears to work as it shows up under Network Connection, so I might hopefully be halfway there. Seems the problem might be the WPA setting, from what I read on an earlier post made in this group.

---

### Post by mörgæs on 2019-09-11
> **ews2k said:**
> 
I'm not sure what you mean by this:
 post lshw.txt in CODE tags ?


It's a file stored in your /home directory. Please post the contents of this file in CODE tags.

---

### Post by ews2k on 2019-09-12
Is this what you're after?

---

 *-network DISABLED
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:26:5e:0a:b4:04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=b43 driverversion=4.15.0-54-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:feafc000-feafffff

---

### Post by ews2k on 2019-09-12
OK, I really have no idea what I did, the Compaq showed the driver was enabled but the wi-fi kept on showing disconnected in the wi-fi settings tab.

Flaffing around with my befuddled mind did something correctly and I am proudly sending this message via my wi-fi enabled Compac Mini 110 Notebook Computer.

I still do not comprehend half of what was discussed here but this is the reason why I am going with Linux - to learn.

Many thanks to all who provided valuable assistance :)


-Eric

---

### Post by mörgæs on 2019-09-12
Good, please mark the thread 'solved'.

---

### Post by oldfred on 2019-09-12
Other threads on Mini 110

[https://ubuntuforums.org/showthread.php?t=2326940](https://ubuntuforums.org/showthread.php?t=2326940)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2F_Compaq_Mini_100c.2F110c](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2F_Compaq_Mini_100c.2F110c)
[https://forums.linuxmint.com/viewtopic.php?t=197286](https://forums.linuxmint.com/viewtopic.php?t=197286)

---

