---
title: "B43legacy problem, are drivers not available in 2020?"
date: 2020-03-30
forum: Installation &amp; Upgrades
---

### Post by paulgwog on 2020-03-30
Hi! Very new to Ubuntu, trying it to fix a bsod on an old laptop. Since I didn't know what I was doing, I tried several versions of Ubuntu...14LTE, 12, and finally 10.04.4 worked for me so I'm going with it (for now).
I have the well known issue of WiFi not working...needing B43legacy driver but the links on other posts are dead (they return a 404 message when I run the commands in the posts). I can't connect to the "b43" link ([http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)) on any computer, it seems to not exist anymore? Should I be trying a different version of Ubuntu? Is there someone who has the b43 driver (and 'firmware - b43legacy installer')for 10.04.4? 
I have an old Dell Inspiron 8600 Pentium M D800 1.7GHz with 40GB and 512MB RAM Broadcom BCM4306 (rev3) [14e4:4320} ; Ethernet works for the most part, I guess (but can't connect to 'broadcom . com' because of a 'ssl_error_no_cypher_overlap' error...which is a different issue?). I may also need to setup the wireless connection from scratch...nothing was ever set up on this laptop. I tried to use similar settings from another laptop but I'm not sure it's 100% correct.
Can anyone with experience help with this old b43 issue? I've read dozens of webpages, trying to learn about Ubuntu in general and also this b43 issue. I've tried following a few posts, the sudo-whatevers run, but my results show a lot of '404' responses...the websites seem to be dead? I'd like to 'play' with my new Ubuntu but I'd like a good internet connection so I'm not tethered by the Ethernet cable.
Thanks!
PaulG! -new to Ubuntu (Ubunt-noob? lol), I can follow directions but I can't read code (well...maybe a little BASIC.lol).

---

### Post by ubfan1 on 2020-03-30
According to [https://wireless.wiki.kernel.org/en/users/drivers/b43](https://wireless.wiki.kernel.org/en/users/drivers/b43) your 4320 hardware takes the b43 driver, not the b43legacy.  This driver has been working for ages and is included in the standard installations.  What exactly does not work from a fresh install of 18.04 or 19.10, the only suppored releases at this point?

---

### Post by tea for one on 2020-03-31
> **paulgwog said:**
>  I tried several versions of Ubuntu...14LTE, 12, and finally 10.04.4 worked for me so I'm going with it (for now).

Ubuntu 10.04 reached **end of life** in April 2015. You will be very frustrated if you continue to try and use it.

> **paulgwog said:**
> I have an old Dell Inspiron 8600 Pentium M D800 1.7GHz with 40GB and 512MB RAM Broadcom BCM4306 (rev3) [14e4:4320} 

512MB RAM will only be suitable for a lightweight version of Ubuntu such as Lubuntu [https://lubuntu.me/](https://lubuntu.me/)

There are other Linux distros that are also suitable for older hardware.

---

### Post by paulgwog on 2020-03-31
Thanks. I thought I read somewhere that my old laptop wouldn't run anything newer, so that's why I kept stepping backwards through the versions...14, then 12, then 10...and that provided a useable laptop so I figured that was the version to go with. I never tried a newer version...thought it would be too much for that old Dell.
I installed it by making a USB drive on another computer and stuck that into the old Dell, turned it on, made it boot from the USB and whatever I put on the USB (10.04.4) installed itself and my bsod was gone. I thought the problem was a failing harddrive (from reading posts on the bsod issue)...I'm just glad the laptop works! :)
I'm new to the whole Ubuntu thing, I've heard of it for years, but don't really know much about it...I learned there are several 'buntu's' but I have no idea what the differences are. Figured I'd just wing it and do what I've read that worked for others with the same laptop...hence the 10.04 and b43legacy. Thanks for providing the link...I see it listed (I kept looking up the b43xx number...I didn't see the '06' model (I think the lists I've seen stopped at 4320?).

I'll look at the lbuntu link you posted and see what distro makes sense to me, but if you have a specific distro you recommend, I'll try that. 

Thanks again!

---

### Post by DuckHook on 2020-03-31
Welcome to the forums, paulgwog.

For an overview of what flavours there are and what they are all about, please read the link in my sig: The Best 'buntu Flavour.

As for using 10.04, I'm going to go one step further than those who have already chimed in and tell you that you simply should not be using it. You are resurrecting a zombie. There have been thousands of security holes found since it died, so using it is just begging for trouble.

---

### Post by DuckHook on 2020-03-31
Your laptop is, indeed, very old. It's an unfortunate reality that any decent OS that you would put on it&#8212;at a minimum, one that is at least safe&#8212;is going to struggle on such old machinery. Perhaps you would be better off with another distro altogether: [Puppy]("http://puppylinux.com/") comes to mind. Another candidate that might work is [Bunsenlabs]("https://www.bunsenlabs.org/index.html"). Or [Slitaz]("http://www.slitaz.org/en/"). These are distros designed for really old HW or severely limited resources. The big plus in going for such alternate distros is that they are all current, supported and therefore safe.

---

### Post by paulgwog on 2020-03-31
Thanks. OK, I'll get to reading your link right now. :) I guess I didn't realize how old 10.04 was...I'll install something else as soon as I can.
Thanks again everyone!

---

### Post by paulgwog on 2020-03-31
Yes, it's a dinosaur, for sure! :) I know the laptop will be slow (at best) but that'll be fine with me. I intend on using it for my other hobby...model railroading. I'll use it for programming locomotives with Digital Command Control (DCC) using the program 'Java Model Railroad Interface' (JMRI) and I'll possibly take the laptop with me to train shows to be the 'brains' of a layout...throwing turnouts, calculating routes and signal aspects, maybe showing a video or play a DVD for the public to view. Nothing too intensive for this old gal (I hope). :) Some people are getting into battery powered locomotives, which require a WiFi signal for control...which I')m hoping this laptop can handle. I won't be on the internet too much, which is why I don't really care about the WiFi issue (it's a 'would be nice to have'...not a 'I gotta have it!' type of thing).

I've done my reading (thanks for the link, and for writing them) and am currently downloading the 18.04.4 ISO to a USB drive. (30mins left on the download). Do you think that's a good version? I'll try 19 and 20 if 18 doesn't work...again, I'm figuring an older version will be better on an old system?

OK...12 mins left on the download...time for a cup of coffee to help me through this install (it's 9:30p here). :)

Thanks again for all the help. :)
p.s. I'd like to read up on the Ubuntu language a bit. Can you recommend a beginner document where I can learn about 'sudo' and 'apt' and stuff like that? I don't want to program...just trying to better understand what all the commands I've been typing (or...copy/pasting) into the terminal. :)

---

### Post by ubfan1 on 2020-03-31
New to Ubuntu:
- read the Ubuntu Manual, it's very informative: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Click on the "download Button" to download the latest PDF version.
- The online help [https://help.ubuntu.com/](https://help.ubuntu.com/)
- Command line help: [http://www.tuxfiles.org/linuxhelp/linuxfiles.html](http://www.tuxfiles.org/linuxhelp/linuxfiles.html)
  and the manual pages for help on commands e.g.: man ls
  or the similar info pages:  info ls
Relax and fun:
[http://planet.ubuntu.com/](http://planet.ubuntu.com/) and Full Circle Magazine [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by paulgwog on 2020-04-01
Thank you for those links...I'll check them out soon.
So, I installed lubuntu 18.04 (Bionic Beaver) by downloading it on another computer, then used Rufus 3.9 to install it onto a 4GB USB drive, then put the USB drive in the old laptop and booted from there (using F12 during bootup). During the install, I had to use 'forcepae' before and after the '---' to get it to work. A bit farther into the install, an error popped up..."b43-open/code5.fw" not found, then the instructions to get it from wireless.kernel.org. I'll try to deal with that later. Continuing with the install, I chose 'normal installation' and checked the boxes for 'download updates while installing' and 'install third-party software'; I hoped these might download and install the b43 drivers (but it didn't seem to?). I selected 'Erase disk and install Lubuntu', so I started off with a 'blank slate'.
A window popped up about a 'System program problem detected'...and I clicked on 'Report'. Then a window popped up showing 'Package operation Failed'...I clicked OK. The install finished and I restarted and for the most part, it works. There is a 3-10 second delay from me clicking on something and seeing anything happen, but I guess that's normal for an old laptop (but I think 10.04 seemed to respond quicker?).
I have some Ethernet connectivity, but some sites come back as 'server not found'. No idea what that's all about. A small window did pop up, said something along the lines of: Network service discovery disabled Your current network has a .local domain...not recommended and incompatible with Avahi network service discovery. The service has been disabled.
I configured a new WiFi connection, put in the SSID and password, but still no WiFi (which didn't surprise me).

I'm guessing I'm going to have to try and download and install the b43 driver? It's a propriety driver, right? Do I have to get it from the Broadcom website? I'll read up on it some more, but I'm done for the night...I'll tackle it tomorrow. I just wanted to document my progress (for others who may read this in the future (Hi future people!), and let you know progress is being made. 
Thanks for all the info and help! :)

---

### Post by webaake on 2020-04-01
Here are some more tips for the B43: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

As already said, the command line (terminal) is a very useful tool for installing stuff and looking for errors. Using commands form the terminal, instead of GUI:s, often gives you more feedback from the process and more powerful alternatives.

By the way, your use case with running model trains seems very interesting! Later on you could start a thread about that.

Good Luck!

---

### Post by DuckHook on 2020-04-01
It's getting late where I am, so some short answers:
> **paulgwog said:**
> &#8230;I'd like to read up on the Ubuntu language a bit. Can you recommend a beginner document where I can learn about 'sudo' and 'apt' and stuff like that? I don't want to program...just trying to better understand what all the commands I've been typing (or...copy/pasting) into the terminal. :)
To learn the command line, please use the link in my sig: A Great CLI Guide.

To learn more about Linux in general, follow the link in my sig: Resources for Newcomers.

[https://linuxjourney.com](https://linuxjourney.com) is an awesome resource specifically geared for newbies.
> **paulgwog said:**
> &#8230;I'm guessing I'm going to have to try and download and install the b43 driver?
Yes.
> It's a propriety driver, right?
Partially. It is largely community based FOSS but with a proprietary binary blob.
> Do I have to get it from the Broadcom website?
No. Do not get it from anywhere except the Ubuntu repos. As a general rule, in Linux, one NEVER downloads unknown stuff from outside the repos unless one is a Linux uber-wizard. For general users, only use the repos. Always. **Follow the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")**.

:!: CAUTION :!:
> *As ubfan1 has already told you, your BCM4306 (rev3) [14e4:4320} chipset does **NOT** use the legacy driver. It uses plain b43. Repeat, **NOT** b43 legacy. Use plain b43.*

It's easy to get distracted through conflicting advice and too much information. Stay focused and follow the instructions I linked you to.

---

### Post by tea for one on 2020-04-01
> **paulgwog said:**
> 

I'll look at the lbuntu link you posted and see what distro makes sense to me, but if you have a specific distro you recommend, I'll try that. 

Thanks again!

You could consider Peppermint OS [https://peppermintos.com/](https://peppermintos.com/)

They offer both 32 bit and 64 bit ISO images and the website indicates that it will run with 512 MB RAM. [https://peppermintos.com/guide/downloading/](https://peppermintos.com/guide/downloading/)

---

### Post by paulgwog on 2020-04-01
I'm familiar with the 'WiFiDocs/Driver/bcm43xx' page...spent a whole day clicking through all the links and trying to comprehend all the info. That page is where I was having trouble.
Under the 'Drivers available in Ubuntu', b43 driver (open source) instructions say there are two parts, the firmware installer and the b43 package. Following the firmware download link, I click on the Bionic Beaver section, then I see three files under the 'Downloads' section (a ...dsc, ...tar.bz2 and  ...tar.xz). Do I need to Save Link As... for all three of those files right to my USB drive? I mean, I already saved all three to my USB drive...just wondering if I need all three. :) No problem saving those files, but when I go back to the instruction page and click on the 'b43' link, I immediately get a big "Not Found...requested URL not found on this server", page. That's why I was originally asking if the drivers are still available in 2020...I couldn't find any other links to a 'b43' Ubuntu (and/or?) Lbuntu driver.
Reading closer, I see the legacy driver seems to be for a Rev02 and I have the Rev03...I get it now. :)

So, any idea about the b43 link? Or am I totally overlooking something simple?
Thanks guys! I'm learning a lot...probably won't retain much of it, but next time I come across this problem, it won't seem so alien to me. :)

---

### Post by DuckHook on 2020-04-01
I suspect you are making things needlessly complicated.

Firstly, you must have internet access by attaching a physical ethernet cable from your router to your laptop.

Then, it's easy. Here are the relevant sections from those instructions, quoted directly from that webpage:
> Open a Terminal and if you haven't already done so, update your package list:

```
sudo apt-get update
```

If you have a b43 card use the command

```
sudo apt-get install firmware-b43-installer
```

Then:

> 
If you wish to permanently use the open source drivers then remove the bcmwl-kernel-source package:

```
sudo apt-get purge bcmwl-kernel-source
```

Ensure that the driver/modules you wish to use are not blacklisted in any of the other files in /etc/modprobe.d 

It's that simple.

---

### Post by ubfan1 on 2020-04-01
You only need the [b43-fwcutter_019-3.debian.tar.xz]("https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/b43-fwcutter/1:019-3/b43-fwcutter_019-3.debian.tar.xz") file -- that's the latest.  There are two sources for the b43 firmware: 1) the Windows drivers (which the b43-fwcutter extracts for you) and 2)the b43-open firmware.  either one should work.  The b43-fwcutter program (may be included on an old ISO)  may be run on a Windows driver (from a Windows install) it you have it around.  The files are:
$ ls b43
a0g0bsinitvals4.fw  a0g0initvals9.fw     a0g1initvals5.fw     b0g0bsinitvals9.fw  lp0bsinitvals13.fw  lp0initvals15.fw    pcm5.fw     ucode4.fw
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals9.fw     b0g0initvals13.fw   lp0bsinitvals14.fw  n0absinitvals11.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals9.fw  a0g1bsinitvals5.fw   b0g0bsinitvals13.fw  b0g0initvals4.fw    lp0bsinitvals15.fw  n0bsinitvals11.fw   ucode13.fw  ucode9.fw
a0g0initvals4.fw    a0g1bsinitvals9.fw   b0g0bsinitvals4.fw   b0g0initvals5.fw    lp0initvals13.fw    n0initvals11.fw     ucode14.fw
a0g0initvals5.fw    a0g1initvals13.fw    b0g0bsinitvals5.fw   b0g0initvals9.fw    lp0initvals14.fw    pcm4.fw             ucode15.fw

$ ls b43-open
b0g0bsinitvals5.fw  b0g0initvals5.fw  ucode5.fw

So just adding the b43 and/or the b43-open directories to the /lib/firmware should allow the b43 open driver (in the Ubuntu distribution) to load them and work.

Things changed drasticaly over time, so there's a lot of old/inapplicable info out there.  The b43-open firmware is still available at netweb.ing.unibs.it/~openfwwf/firmware/b43_v4.6.tar.gz I think, but if the b43-fwcutter-installer works, you don't need it.  Save the firmware on a USB and you'll never have to do the download/extract again, it does not change for new kernel releases.

---

### Post by paulgwog on 2020-04-01
lol, making things[COLOR=#000000] needlessly complicated...yup, sounds like me (I'm more of an engineer (CAD) than a programmer). :D
[/COLOR]Ok, I ran '[COLOR=#000000][FONT=&quot]sudo apt-get update' and got this:
[/FONT][/COLOR]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


paulg@paulg-Latitude-D800:~$ sudo apt-get update
[sudo] password for paulg: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Hit:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic InRelease                     
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 DEP-11 Metadata [38.5 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons [41.4 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 DEP-11 Metadata [42.1 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [16.4 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [111 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 DEP-11 Metadata [2,464 B]
Get:11 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [662 kB]
Get:12 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main i386 DEP-11 Metadata [307 kB]
Get:13 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
Get:14 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [140 kB]
Get:15 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1,012 kB]
Get:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 DEP-11 Metadata [273 kB]
Get:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [210 kB]
Get:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [483 kB]
Get:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 DEP-11 Metadata [2,468 B]
Get:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 DEP-11 Metadata [7,980 B]
Fetched 3,676 kB in 7s (536 kB/s)                                              
Reading package lists... Error!
E: Read error - read (5: Input/output error)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
paulg@paulg-Latitude-D800:~$ 

It says the file is corrupted? Well, from past experience, sometimes its ok to ignore the error for now and press on, so I ran: '[COLOR=#000000][FONT=&quot]sudo apt-get install firmware-b43-installer' and got this:
[/FONT][/COLOR]paulg@paulg-Latitude-D800:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  efibootmgr libfwup1
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 27.7 kB of archives.
After this operation, 103 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main i386 b43-fwcutter i386 1:019-3 [23.7 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/multiverse i386 firmware-b43-installer all 1:019-3 [3,950 B]
Fetched 27.7 kB in 1s (32.8 kB/s)            
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 153939 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-3_i386.deb ...
Unpacking b43-fwcutter (1:019-3) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-3_all.deb ...
Unpacking firmware-b43-installer (1:019-3) ...
Setting up b43-fwcutter (1:019-3) ...
Setting up firmware-b43-installer (1:019-3) ...
No chroot environment found. Starting normal installation
--2020-04-01 12:25:20--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.30.178
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.30.178|:80](www.lwfinger.com)|173.254.30.178|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-tar]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;


broadcom-wl-5.100.1 100%[===================>]  12.89M   202KB/s    in 70s     


2020-04-01 12:26:31 (188 KB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]


Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
paulg@paulg-Latitude-D800:~$ 

This is where, last time (with 10.04?), I got a bunch of '404' errors...it looked like it couldn't find what it was looking for, but this time it looks a lot better (way less errors)...you are right, it was That easy! :)

Does this look like it worked well enough? I didn't do the remove the 'kernel-source' step yet...don't know if it's working well enough to remove things (but I'd like to remove it, eventually). :)
I unplugged the Ethernet and I seem to have some connectivity but when I try to get to 'Google.com', I get 'Hmm. We're having trouble finding that site.'. I guess that means it's working...it's just not configured (on my end) yet?
Thanks again!

---

### Post by ubfan1 on 2020-04-01
Reboot and run dmesg | grep -i firm to ensure the firmware gets loaded.  Then you should be able to connect to your wifi access point.

---

### Post by paulgwog on 2020-04-01
Thanks for all your patience. :)
Ok, UBfan1, I rebooted, ran the '[COLOR=#000000]dmesg | grep -i firm' and got back this:
[46.068911] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

No errors, so I guess it worked? Disconnected the Ethernet cable, clicked on the 'Web Browser' button on the lower left of the screen and the Firefox window opens and seems to load fine. When I type anything in the Google search, or click on any link, it comes back "Hmm. We're having trouble...".

How do I set up a wireless connection? I click on the icon on the lower right and created a new wifi connection...put in my SSID and password (I checked it twice), but still get the Hmm... page.
Can you help me with this or is there a link to instructions on how to do this? I'm only familiar with Windows, I don't know where to look in Lubuntu...it seems like everything has a different name so I have to click on things to see what they do (which is why I asked for the beginner-style documentation). :)
When I plug in the Ethernet, click on the Web Browser button, and click on a link (in this case YouTube), it opens (somewhat slowly...but it opens). Current network has a .local domain ... Avahi network service discovery network disabled (...or something similar to that). I kinda hoped when the WiFi was turned on, it would do a self-configure type of thing. That reminds me...somewhere I read I might need to toggle the wireless on (like Alt+F7, or some kind of keyboard shortcut like that?). Since the Firefox homepage opens with WiFi, I'm guessing it's not that; just wanted to rule out something simple.

Also (might be unrelated), on the lower right (next to the connection icon?) is an exclamation mark; when I click on it, a small window pops up saying "A problem occurred when checking for the update.". Task cannot be monitored or controlled The connection to the daemon was lost. Most likely the background daemon crashed. When I click on Details...It seems that the daemon died. ...I have no idea what several of those things are. :)

Occasionally, I'll get this window too:
System program problem detected. Do you want to report? ...I click on Report problem and the window goes away (but I don't know if it did anything; I'm assuming it sent the report). Is that a 'normal' Lubuntu thing or is it something I need to address? (I frequently accept any errors and warnings when I'm on a Windows machine...I don't know if this is typical for Lubuntu.
Thanks![/COLOR]

---

### Post by ubfan1 on 2020-04-01
I guess the dmesg output is OK, at least there was no complaint about missing firmware.... It's been several eyars since I had a machine with the Broadcom chips, and don't use Lubuntu, so may not have the best advice on it, but see [https://help.ubuntu.com/lts/ubuntu-help/net-wireless-troubleshooting.html.en](https://help.ubuntu.com/lts/ubuntu-help/net-wireless-troubleshooting.html.en) for some starting points.  If the wireless-tools package is not installed, install it.  It may be there by default -- looking for the iwconfig and iwlist programs.  When you click on the icon, do you get a list of nearby access points?  Run rfkill list in a terminal to ensure the wireless is seen, and not hard or soft blocked.  Hardblocked is some switch or keyboard toggle, or no driver.  Softblocked  some config error.  Running sudo iwlist scan in a terminal should give a list too. When you can successfully see (your) access point(s), click on yours.  If yous has a hidden ESSID, maybe you'll have to select connect to hidden...  and type in your ESSID name.  Select the type of encryption WEP or WPA2, then the password.  If you can see "edit connections" in some menu, edit your connection and from that, I disable IPV6.  These settings are also available from a gear icon (settings) next to your access point when in a list.  I think dhcp will be automatic, so you should be getting an ip address -- run ip a and see if you get an inet line under your wireless with an ip address .  iwconfig will tell you how good your connection is to the ap, and which channel is in use.  ping 8.8.8.8 to see you you can reach the internet.  If ping works, try a firewfox connection .

---

### Post by happyytilton on 2020-04-01
> **paulgwog said:**
>  
I have an old Dell Inspiron 8600 Pentium M D800 1.7GHz with 40GB and 512MB RAM Broadcom BCM4306

I had a 2004 Dell 8600 with same specs, except a 60GB HDD. I upped the RAM to 2GB, and is the best thing I ever did to it.
Two 1GB sticks was cheap through Amazon, so you might want to give that option some thought. RAM has easy access on an 8600.

But to the problem at hand...
I had the same issues as you, on a Dell E1705 w/Broadcom BCM4306, and I was the dog chasing it's tail, until coming to this forum.
Here's the link to that thread, as there may be something helpful therein.
[URL="https://ubuntuforums.org/showthread.php?t=2225781"]https://ubuntuforums.org/showthread.php?t=2225781
[/URL]
BTW....
I'm a retired RR Condr.

---

### Post by paulgwog on 2020-04-02
Happyytilton, thanks for the link...I read through it quickly and some things may apply...I'll keep them in mind for the future. A conductor, huh? What railroad? I model the C&O in the late 60's (which is a little before my time), around the Detroit area, in HO scale. I'm always looking for more realistic ways to operate my layout (which are made up of Free-Mo modules...but I digress, until this Lubuntu issue is solved. :)

Ubfan1, I looked at the Wireless troubleshooter link you gave and have on small issue. On the second page (?), #4 "[COLOR=#333333][FONT=Ubuntu]Click the system status area on the top bar and...", I don't have a top bar, so I can't check if the wireless is on, or if Airplane Mode is off. I went ahead and did the next step ([/FONT][/COLOR][COLOR=#333333][FONT=monospace]nmcli device) and got this:

[/FONT][/COLOR]```
paulg@paulg-Latitude-D800:~$ nmcli device
DEVICE  TYPE          STATE        CONNECTION 
enp2s0  ethernet   unavailable            --         
wlan0    wifi          unavailable            --         
lo          loopback   unmanaged           --        
``` 

I did unplug the Ethernet (per the instructions) so I'm not surprised by that, but the wireless is unavailable.
Moving on to the next page of the troubleshooter, I did the '[COLOR=#333333][FONT=monospace]lshw -C network' and got this:

[/FONT][/COLOR]```
paulg@paulg-Latitude-D800:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0               
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 01
       serial: 00:0f:1f:21:db:0f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Inc. and subsidiaries
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f2:60:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=5.3.0-45-generic firmware=666.2 latency=32 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:5 memory:fafec000-fafedfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

It seems the device was properly detected, so I did the next step, "[COLOR=#333333][FONT=monospace]lspci", and got this:

[/FONT][/COLOR]```
paulg@paulg-Latitude-D800:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510/7610 CardBus Bridge (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410/7510/7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Inc. and subsidiaries BCM4306 802.11b/g Wireless LAN Controller (rev 03)
paulg@paulg-Latitude-D800:~$ 
```

Next step is the Device Drivers Step. Since I already got the driver, there is nothing helpful here; I've read about the '[COLOR=#333333][FONT=Ubuntu]NDISwrapper', but not sure if it applies to me, so I didn't follow that link...and that's the end of that page; I don't see anything else to try here.
[/FONT][/COLOR]



Something must be wrong with permissions, the configuration, or something like that (?) because when I click on the Web Browser button on the lower left (I'm on 18.04), the Firefox window opens, but anything typed into the search bar (even the links on that page) comes back "Hmm. We're having trouble finding that site.", page. That's with the Ethernet disconnected (but it's weird that the page loads with seemingly up to date links/pictures...but everything leads to the 'Hmm' page.

One thing listed on that 'Hmm' page asks if I'm behind a firewall and to check to see if Firefox has permission to access the Web. In Windows, I know how to find the firewall settings...but I have no idea where to find the Firewall in Lubuntu. 

When I plug the Ethernet cable in, everything seems to work fine. I can click and search to whatever I want...so my router is working. I'm using an AT&T U-Verse Gateway...in case there are issues with this specific combination (I doubt it, but sometimes certain components just don't work well with each other)...and I don't have any issues on any of my other devices.

What am I doing wrong? My brain is kinda jello now, trying to read all the 'buntu info (Thanks a lot DuckHook! lol), but I can't seem to see an equivalent of 'network settings' in Windows, where I can run a troubleshooter (not that they usually help), or change settings (airplane mode, for example). I've heard people say Ubuntu is more text based, and Windows is more graphical (hence the 'windows' name), and I've read about the ability to put different interfaces on Ubuntu (some resemble Windows more, right?), but I don't want to customize this basic install until everything works...kind of like, I've got to get the car running before I put a custom paint job on it :). I don't mind typing commands into the terminal, but I don't know what to type.

DuckHook, thanks for the info...really! It's (slowly) helping me understand and I really appreciate the knowledge I'm gaining (even if for a short while.lol).

Now...back to the 'books'. I'll probably research my issue some more, maybe watch a Ubuntu video online to get a better handle on this OS. Having a working computer that I can follow along with is much more helpful than just watching a video on it while I drink a cup of coffee and stare at the TV.

Thanks guys...I'm still working on the Dell-osaur laptop, but might get busy with other stuff (it's finally going to be above 50 tomorrow, so yard work...yeah).

---

### Post by happyytilton on 2020-04-02
> **paulgwog said:**
> A conductor, huh? What railroad?
SCL in Wildwood, Fl from 1971-1986, 1986 Amtrak, from JAX to Florence, SC and Hamlet, NC until retired in 2009, 38yrs!

Glad that thread was an informative read for you. That Broadcom b43/b44 wireless driver ordeal aged me 5yrs in the time frame of that thread!

---

### Post by paulgwog on 2020-04-07
Well, I've been reading a lot...DuckHook, fiy, the tux link, for 'command line help' (from post #9) is broken...just wanted to make you aware. :)
Thanks for all your help, My original problem was solved by installing the Bionic Beaver version. Everything seems to be working (except the wifi...which is probably on my end).
Thanks again for all the help and support. I'm considering this "Solved". :)
Weather is getting nice and my list of projects is getting longer so I'll work on my old laptop later.
Thanks again...I can't say it enough...this forum is a great place to learn!
:)

---

### Post by CelticWarrior on 2020-04-07
You have the correct driver installed but the WiFi is still DISABLED. That means, in a UEFI system, that you need to disable Secure Boot in UEFI ("BIOS") settings and/or enable the WiFi there if disabled. Nothing else is wrong.

---

### Post by ubfan1 on 2020-04-07
To repeat, did you ever try rfkill list to ensure you are not hardblocked?  That might be a tiny switch somewhere on the case which turns off wifi. The hardblock switch may also be a function key toggle, check those and see what's there (if anything).

---

