---
title: "Atheros Support in Intrepid"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tim183 on 2008-10-04
Will the much promised Atheros support finally arrive before the release of 8.10? As of beta I still have no support for my wireless card (the infamous ar5007eg) . I'm using a very common HP laptop so the fact that wireless networking doesnt work is just a ridiculous situation. I'm a 64-bit user and have never been able to get the wireless card to work in  gutsy or hady despite months and months of trying every available combination of configurations, howto's and long nights on irc channels. I have filed endless bug reports and followed mailing lists of all kinds

for me, these need to be the kinds of challenges that intrepid should meet if Mark Shuttleworth's comments about ubiquitous connectivity are to be met. Isn't such a feature as wireless connectivity much more important for the average user than which wallpaper, theme or sound scheme is better?
For me features like that are the deal breaker, not astheatics, which can easily be configured by the end user.

I hate to say it, but if intrepid fails me I am going back to windows.:(

---

### Post by inportb on 2008-10-04
I've the same chipset (also running the 64-bit kernel) and ath5k has never worked well for me. I simply blacklisted it and went back to MadWifi.

You can't use the stock MadWifi, but it's not so difficult to build your own. Please refer to my blog post: [http://www.inportb.com/2008/07/27/madwifi-support-for-ar5007-ar2425-with-injection-aircrack/](http://www.inportb.com/2008/07/27/madwifi-support-for-ar5007-ar2425-with-injection-aircrack/) (you can skip the aircrack part if you don't need it, but it works). For Intrepid, you also have to blacklist ath5k, or it would get in the way.

The AR5007EG has always worked for me; sometimes one just has to settle for workarounds. In this case, it's really not so bad. Originally I used ndiswrapper, then I switched to a native 32-bit only hack when it became available, and finally this one which is the best so far. If I can get it working, so can you; don't give up!

I hope this helps ;p

---

### Post by Sef on 2008-10-04
> Will the much promised Atheros support finally arrive before the release of 8.10?

If you want to download it yourself, click [here]("http://sourceforge.net/projects/madwifi/").

---

### Post by Nullack on 2008-10-04
> **tim183 said:**
> I hate to say it, but if intrepid fails me I am going back to windows.:(

Unlike some other software projects, what FOSS offers you is the ability to get involved and made a difference. You don't have to be a developer to do so. There's ways with tests, bugs and other areas in which non developers can contribute.

---

### Post by tensop on 2008-10-05
the kernels ath5k_pci drivers are working for me on ar5007eg, however it only connects at 6mbps :)

Switching over to madwifi drivers(make,make install) works better


1. Download ath_pci drivers from madwifi(madwifi drivers)
2. sudo make
3. sudo make install
4. sudo rmmod ath5k
5. sudo modprobe ath_pci

---

### Post by tim183 on 2008-10-05
Nullack, I am completely aware of this fact, that is why I have assisted by filing bug reports, contributing to these forums and others. My knowledge of the OS isnt the greatest, but as an end user I do as much as I can. I think turning all my friends and family over to ubuntu has been the best I have done.

I will give the howto on inports blog a run after my updates finish this afternoon, fingers crossed!!!

I don' see why there needs to be these workarounds though, the ar5007eg is a fairly common chip.

---

### Post by blakamin on 2008-10-05
I have the same chip and it works fine for me...

---

### Post by tim183 on 2008-10-05
did you have to do anything to get it to work? I dont even have wireless as an option in network manager

---

### Post by jbernardo on 2008-10-05
On my Aspire One I went back to the madwifi drivers, as the kernel included ones (ath5k) would give a hard lock if there were more than one AP on range with the same SSID.

---

### Post by inportb on 2008-10-05
> **tim183 said:**
> did you have to do anything to get it to work? I dont even have wireless as an option in network manager

The ath5k driver was able to scan for access points, but was not able to connect to any of them, for me. So yes, I had a wlan0 device.

It's interesting that you should not see the option at all. Make sure you've got the wifi device turned on? :) Or check ifconfig/iwconfig instead.

---

### Post by Perpetual on 2008-10-05
Mandriva is the only distribution I have found lately that supports my Atheros 5007 out of the box.

---

### Post by maestrobwh1 on 2008-10-17
I tried to do this and I get

$# make
Makefile.inc:96: scripts/get_arch.mk: No such file or directory
Makefile.inc:100: ath_hal/ah_target.inc: No such file or directory
Makefile.inc:161: *** TARGET  is invalid, valid targets are: .  Stop.

So what am I doing wrong?

I have kernel headers and source installed.


> **tensop said:**
> the kernels ath5k_pci drivers are working for me on ar5007eg, however it only connects at 6mbps :)

Switching over to madwifi drivers(make,make install) works better


1. Download ath_pci drivers from madwifi(madwifi drivers)
2. sudo make
3. sudo make install
4. sudo rmmod ath5k
5. sudo modprobe ath_pci

---

### Post by Perpetual on 2008-10-17
> **maestrobwh1 said:**
> I tried to do this and I get

$# make
Makefile.inc:96: scripts/get_arch.mk: No such file or directory
Makefile.inc:100: ath_hal/ah_target.inc: No such file or directory
Makefile.inc:161: *** TARGET  is invalid, valid targets are: .  Stop.

So what am I doing wrong?

I have kernel headers and source installed.

Have you tried following [this]("http://ubuntuforums.org/showthread.php?t=792158")?  Worked perfect for me.

---

### Post by wwusnobrdr on 2008-10-17
Yeah I have the 5007 Chipset and the wireless did not work when I first booted up.  I had to disable the restricted drivers, restarted it and it worked.  Seems counter-intuitive and may confuse the average user.  I do like the madwifi drivers better, although I have just been using these for a couple days.  I tried bridging my wireless connection and it worked for about a minute then I lost my connection and could not authenticate with my AP.  Overall it does seem that the network manager has improved but I will have to get some more experience to see if that is really the case.  I know that wireless drivers has been a tough subject and I applaud developers for making progress.

---

### Post by maestrobwh1 on 2008-10-20
Perpetual>

Thanks!  Worked as far as installing... now lets see if my connection doesn't eventually crap out like it was doing.

---

### Post by forcecore on 2008-10-21
> **maestrobwh1 said:**
> Perpetual>

Thanks!  Worked as far as installing... now lets see if my connection doesn't eventually crap out like it was doing.

i hope that with final release my esprimo v5535 wifi can work out of box without ndiswrapper.

---

### Post by maestrobwh1 on 2008-10-21
It does not disconnect, it just stops communicating.  Manually installing the driver "helped" but rather than crap out, it seems quite a bit slower.

---

### Post by bodycoach2 on 2008-10-21
> **tensop said:**
> the kernels ath5k_pci drivers are working for me on ar5007eg, however it only connects at 6mbps :)

I noticed that too (6mbps). But, when I check at random, I notice speeds all over the place: 1mbps, 5mbps, 36mbps, 48mbps, and 54mbps. 

I wonder the atheros chipset driver is now altering speed and power for battery saving purposes.

---

### Post by hdhrnova on 2008-10-21
> **bodycoach2 said:**
> I noticed that too (6mbps). But, when I check at random, I notice speeds all over the place: 1mbps, 5mbps, 36mbps, 48mbps, and 54mbps. 

I wonder the atheros chipset driver is now altering speed and power for battery saving purposes.

its bug.  workaround.  lock it at 24M using iwconfig.

---

### Post by maestrobwh1 on 2008-10-21
Perpetual --> do you have no/few issues at this time, now that you compiled and installed madwifi?  I still have issues.

[EDIT]: I opened /etc/network/interfaces and removed everything there except
auto lo
iface lo inet loopback 

My Intrepid was an upgrade... so I assume there will be more issues than from a fresh install. 

Then, oddly, as much as I had better luck with WICD, I installed knetworkmanager instead (I am using the Kubuntu flavor of 8.10) and I seem to have a better connection BUT still

Three things can happen when I boot:
[B]
1) I have wireless for my entire session
2) I have wireless for a few moments or even longer but it is horribly slow, it looks like it is connected but there is no real communication going on: there is no way to get it working even using command line tools - reboot and hope.
3) I have what looks to be a connection I can use, but it won't connect.  Rebooting doesn't seem to solve this problem unless I unplug my router and plug it in again, but I get issue 2[/B]

I am considering
1) blacklisting ath_pci and ath_hal and installing ndiswrapper and win driver
2) Putting my broadcom card back in after removing it sometime last year, then using ndis
3) perhaps more simply, restoring my Hardy image back to the drive

**My desktop and my other laptop use the atheros chipset with madwifi in Hardy and I have none of these issues.**

Original post:

I was hopeful after a manual install of madwifi.  I set my device at 11M and it does remain a bit more stable.  It still craps out even after the manual installing of the latest madwifi.  

This is a real downer... it is the ONLY issue I have with 8.10 so far.   

Using the Kubuntu version and KDE 4.1 looks beautiful and seems faster and less "clunky" than previous kde versions.  I know that sounds like overkill, but the interface looks awesome.

---

### Post by piotrwoj on 2008-10-22
latest ath5k and ath9k!!! source code from [wireless.kernel.org]("http://wireless.kernel.org/en/users/Download") work as virtual-AP, and monitor mode (kismet, airodump-ng) :)))
[drzwi ]("http://www.domar.biz.pl/")[zewnetrzne ]("http://www.drzwi-gerda.pl/")[wejsciowe]("http://www.drzwi-warszawa.pl/")

---

### Post by maestrobwh1 on 2008-10-22
Using compiled madwifi (as per this post); I found more of my "quirk."  

ath0 is brought up automatically, but not not always wifi0 so that is why I cannot connect [sometimes this is the reason].

When I went to the command line and did 
**ifconfig**

I got interfaces lo, ath0 and eth0, so after pulling my hair out wondering whey I cannot connect sometimes no matter what I did (knetworkmanager, any command line network tools); when trying again today from command line, I remembered always seeing wifi0 any time with ath0 and I DID NOT see it.

I had this epiphany and did

sudo ifconfig wifi0 up

Boom... I can connect.

***So why is wifi0 not initializing along with ath0 at times?***

[B]FIX: If you have trouble with reconnection and when you do ifconfig you have my issue of wifi0 being present from boot but not suspend, open /usr/lib/pm-utils/sleep.d/10NetworkManager

thaw|resume) 
  ifconfig wifi0 up  <-- 
  resume_nm

add that line assuming this is the virtual device (for you as it is for me) that madwifi creates along with ath0.

You don't need to add ath0 if that seems to show up after resume.

NM reconnects Wifi every time - so far for me anyway.[/B]

---

### Post by forcecore on 2008-10-24
esprimo v5535 atheros wifi still do not work in rc so i still use ndiswrapper gui from 8.10 cd.

---

### Post by plun on 2008-10-24
I am rather confused over this and I am helping a user within my country with this.....

Atheros ath5k is blocked in latest kernel which now is available
> 
linux (2.6.27-7.14) intrepid; urgency=low

  [ Tim Gardner ]

  * **Disable ath5k in 2.6.27**
    - LP: #288148

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009253.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009253.html)




According to this bug report linux-backports-module should be enough

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284354)

and especially this message from Colin Watson

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284354/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284354/comments/21)

> **The outcome of discussion on #ubuntu-release today appears to be as follows:**

* We will remove ath5k from the kernel configuration for 8.10 to avoid the race. (This upload needs to happen today, and involve as few other changes as possible.)
* We will include linux-backports-modules on the CD so that people can install it without a network connection if they need to.
* We will add a release notes item to state that newer Atheros devices may not work, and that Atheros devices in general may or may not work with WPA; this item will include instructions on installing linux-backports-modules from the CD as a workaround.




But in the end...

> 

linux-restricted-modules needs to ship:
/etc/pm/config.d/madwifi

with the following line:
SUSPEND_MODULES="ath_pci"

this will make sure the module gets properly unloaded in suspend/resume cycles which doesnt happen by default and thus results in a broke wlan connection after a resume.



:confused::confused::confused:

---

### Post by gcday on 2008-10-24
Did an update this morning and it killed the wifi again. ARGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGG.

---

### Post by Dreamer Zero on 2008-10-24
reinstalling the driver got my wireless back.

---

### Post by thor2002ro on 2008-10-24
in terminal:

sudo apt-get install linux-backports-modules-intrepid

shutdown and back on

gets everything up again :popcorn:

---

### Post by sanone on 2008-10-25
Well it doesn't work here :(
Some more info on this particular case can be found here: [http://ubuntuforums.org/showthread.php?t=958686](http://ubuntuforums.org/showthread.php?t=958686)

---

### Post by voltaire99 on 2008-10-29
Sidux Ourea 64 supports the card perfectly, as far as I can see, via ath5k.

---

