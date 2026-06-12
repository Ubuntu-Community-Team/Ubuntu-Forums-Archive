---
title: "Fujitsu-Siemens Amilo L7320: an Ubuntu's problematic installation"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by stilnovo1 on 2014-02-23
Hi, I start this post since I'm an owner of this Laptop, quite popular between 2006 and 2008 in Europe.
Amilo L7320 was sold with Windows XP Home Edition installed over and because of the next end of XP extended support on April 2014, I've decided on the last october 2013 to try if I could install an Ubuntu version on it.

The things have showed a particular complication, so I hope that this post will be useful for all the people (and also for me!) that will want to install Ubuntu, or one of the Ubuntu-flavours on this not-so-old laptop.

I've decided to do a dual boot with XP, since some programs I need run only on that Operative System.
I've made the first trial with Lubuntu 13.10. With the livecd session all the things seemed ok, so I carried on the installation. During the first boot, Grub was ok, but at a certain point the hard disk stopped and the screen remained dark: a freeze of the system. Since the graphic card is a VIA P4M800 Unichrome S3, I have discovered and I have subscribed [this bug]("https://bugs.launchpad.net/bugs/1205643") on Launchpad. Please, if you have this Fujitsu-Siemens Amilo L7320 subscribe too that bug.

I have described the multiple installation trials I've done [in this]("http://ubuntuforums.org/showthread.php?t=2174725&page=16") interesting thread I've subscribed.

From that page onwards I've got from other (super)users newsworthy suggestions and infos on the problems related to this laptop.

At the beginning, I settled with this configuration: Kubuntu 12.04 running Vesa driver. The result was a stable configuration with a poor graphic result: XGA screen resolution instead of a WXGA one (in XP with its VIA driver), faded colours, limited color depth, irregular fonts... for the rest things seemed quite good, but the graphic was a true limit. However, to have a visible desktop on the screen and not a CLI interface, I had to create a xorg.conf file in order to force the loading of the Vesa.

Then, on the mentioned forum, a person suggested to me that the problem could be related to the Enablement Stack or to the CPU's PAE flag, since this laptop has a "Dothan" Celeron M. 

So, I've done many other installation's trials (about 14th...), but the graphic result was always the same: vesa driver forced to be loaded by a xorg.conf file created by me. 

Another problem I've had is that many installation steps required a continous mouse movement or a continouos pressing 'any key' on the keyboard in order to not freeze the installation: if you don't press or move the mouse, the installation stops and it restarts in any moment pressing any key. This behaviour is occurred in every installation, except the ones made by alternate CD (Ubuntu 12.04) and mini iso, where the interface is made only by text.

After all those installation trials, now I have on that Amilo 7320:

- one partition with XP

- one partition with Bodhi Linux 2.4

- one partition with Xubuntu 12.04

Bodhi 2.4 and Xubuntu 12.04 are the only *Ubuntu versions that work with a correct screen resolution, but sometimes they freeze and you need to hold an "any key" to awaken the OS, specialy when you do the system shutdown. 
Indeed the general stability is not so good as I've tested on other computers having the same OSs. 

Did someone have same problems I've had? Do you have solved in a different or better way than mine?

Pull out of the drawer your Amilo 7320 and install Ubuntu on it! I wait for your experience...

---

### Post by Elfy on 2014-02-23
What is the actual support issue you need help with?

---

### Post by stilnovo1 on 2014-02-23
Hi Elfy! 

The behaviour of this computer with both Bodhi Linux and Xubuntu is not very smooth, particularly:
- on shutdown, you need to press an any key to "awake" it since it always freezes or it doesn't close at all;
- during the use, the system blocks for some minutes, then it continues to go (also there pressing some keys or continously moving the mouse)
- Bodhi Linux maybe is a little bit more stable, with less 'freezing' periods, but the problem occurs also there
- Both are the only ones where I was successful to have a right WXGA screen resolution and they don't oblige me to force to use vesa driver: this is nice! However, lshw doesn't give me any driver information (unclaimed display), while from the log of xorg I don't understand if it is finally loaded the openchrome driver or not.

I've used during my installation trials also the 12.04.1 iso(s) of K/X/Ubuntu with the original Enablement Stack. Lubuntu (since 12.04 is no more supported) only 13.10, but I subscribed a bug regarding this issue.

---

### Post by kansasnoob on 2014-03-04
Just curious, have you been creating a SWAP partition?

Also how much disc space are you allowing for your **buntu installs?

---

### Post by stilnovo1 on 2014-03-05
@ kansasnoob: Hi Erick!
- Xubuntu 12.04: 15GB
- Bodhi Linux: 17GB
- XP: 42GB
- SWAP: 1GB (there is only one swap partition for both)

After some days of continuous use with this configuration, I can add the following infos that apply to both Linux OSs I've installed:
- watching a dvd it blocks the video while it continue to play the audio part; the video restarts (as usual I could say) pressing 'an any key' --> I'm obliged to keep a little weight on a key in order to see a video (in any format and with any program - I've tested VLC, Xine, Parole... in Bodhi only VLC and Xine)
- the system often blocks for about two minutes, then it spontaneously restarts; in this case I've seen I can speed up its 'awakening' (guess how?).... pressing an any key!
- this 'often-freezing' behaviour is not present if -just after an installation- I force to load the vesa drivers creating an xorg.conf file... in this case all the Ubuntu 12.04 flavours (Ubuntu included) work witohout freezing but with a lower XGA resolution and with very poor graphic performances
- apparently the Task-manager doesn't show something that could be the responsible for those blocks, nor the 'top' command in the terminal
- the wireless connection goes down during the blocks; in public wi-fi areas I have to reconnect every time
- external speakers don't work with the right configuration: I've to "lie" setting up at least a 4.0 channels surround (but I use a two cheap normal little speakers)

Well, I can say that this is not an Ubuntu-oriented laptop!

---

### Post by sudodus on 2014-03-05
> **stilnovo1 said:**
> ...
Well, I can say that this is not an Ubuntu-oriented laptop!

I agree, but as long as you enjoy tweaking it ... :-)

---

### Post by stilnovo1 on 2014-03-05
@sudodus: yes, you are right! But also consider how many Amilo 7320 are sleeping in some drawers or are running XP.... they are only waiting to 'eat' L/Xubuntu!!

---

### Post by Elfy on 2014-03-05
Please keep this thread on topic as a support thread or I will move it to a chat area.

---

### Post by stilnovo1 on 2014-03-05
ops, excuse me! Is it useful what I wrote about the first periods of use?

---

### Post by kansasnoob on 2014-03-05
> **Elfy said:**
> Please keep this thread on topic as a support thread or I will move it to a chat area.

Please don't [-o<

I met Andrea here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

And I'm the one that convinced her to approach this at the forums, I've just been slow responding because I've had a lot on my plate with Trusty testing, and now I'm down with a stomach bug :(

It is a valid support request, I'll recap what I know ASAP and get down to basics when I'm physically able.

---

### Post by Elfy on 2014-03-05
I've not got an issue with it being here, but 

It needs to be about issues and fixes :)

---

### Post by kansasnoob on 2014-03-05
> **Elfy said:**
> I've not got an issue with it being here, but 

It needs to be about issues and fixes :)

It seems like mostly an X issue. I'm going to request some basic info soon, but right now I'm wearing out the floor between the puter and the bathroom :(

BTW I think English is not Andrea's first language so what seems like a long drawn out explanation is actually an effort to be respected.

It boils down to broken graphics and frequent freezes.

---

### Post by stilnovo1 on 2014-03-06
Yes, as you have properly noticed, english is not my first language.... I try to give more details only because I'd like to be precise (or I attempt it!).... so excuse me if sometimes I'm too much loquacious! Effectively I've asked in another thread a suggestion on where to post this issue, since I'm a callow on this forum...
Good healing!
Ask me every info you need...

---

### Post by kansasnoob on 2014-03-06
Thanks for being patient, I've had a rough 48 hours. That said let's start off by eliminating any guess work :)

If you would, please post the output of these commands:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
lspci | grep Audio
```

```
lspci | grep Ethernet
```

```
free -m
```

If my assumptions have been correct I think I may be able to help you because I maintain over 20 machines with this hardware:

> VIA C7 CPU @ 1500MHz
VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
VIA VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
1GB DDR2 RAM

It's very flaky though!

Flash video performance is terrible, and due to the presence of "flash" ads on the net Firefox will appear to freeze unless you use Adblock Plus. And the P4M800 will NOT play full screen flash at all.

I haven't tried VLC, Totem, or Mplayer recently on that hardware but I doubt DVD's would play well with that graphics chip.

Installation can also be problematic! I always start from the advanced boot menu and choose "install" after being sure to check disc for defects!

I guess we should also know if you're using an optical drive to install or a USB drive?

I'd guess that some of your "any key" freezes are due to a screensaver wanting to activate when no resources are available.

---

### Post by stilnovo1 on 2014-03-07
Hi! 

Below the results:


cat /proc/cpuinfo | head -10

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor         1.70GHz
stepping    : 8
microcode    : 0x20
cpu MHz        : 1695.687
cache size    : 1024 KB
fdiv_bug    : no




lspci | grep VGA

lspci | grep VGA[COLOR=#222222][FONT=Verdana]01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)[/FONT][/COLOR]


lspci | grep Audio

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


lspci | grep Ethernet

00:06.0 Ethernet controller: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)


free -m

             total       used       free     shared    buffers     cached
Mem:           937        804        132          0         15        606
-/+ buffers/cache:        181        755
Swap:         1425          0       1425


Maybe it's important for the last result, but since I have had problems to load Xubuntu this evening, those datas come from Bodhi.

---

### Post by kansasnoob on 2014-03-07
> **stilnovo1 said:**
> Hi! 

Below the results:


cat /proc/cpuinfo | head -10

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor         1.70GHz
stepping    : 8
microcode    : 0x20
cpu MHz        : 1695.687
cache size    : 1024 KB
fdiv_bug    : no




lspci | grep VGA

lspci | grep VGA[COLOR=#222222][FONT=Verdana]01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)[/FONT][/COLOR]


lspci | grep Audio

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


lspci | grep Ethernet

00:06.0 Ethernet controller: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)


free -m

             total       used       free     shared    buffers     cached
Mem:           937        804        132          0         15        606
-/+ buffers/cache:        181        755
Swap:         1425          0       1425


Maybe it's important for the last result, but since I have had problems to load Xubuntu this evening, those datas come from Bodhi.

Thank you :)

Give me a bit of time to search for problems specific to the  Intel Celeron M 1.70GHz CPU.

Regarding the wireless I'm beyond clueless because wireless support where I live is horrible and I seldom work on laptops.

But we have identical graphics chips so I should be able to help troubleshoot some of the graphics issues, it will however be slightly time consuming because I'll have to perform some test installs.

Thanks for your patience.

---

### Post by kansasnoob on 2014-03-07
@ sudodus,

Are you still following this thread?

---

### Post by mörgæs on 2014-03-07
> **kansasnoob said:**
> 
Give me a bit of time to search for problems specific to the  Intel Celeron M 1.70GHz CPU.


I can't imagine any. 
All 32 bit ISO's should run, but not fast. Lubuntu or Bodhi are good choices.

---

### Post by kansasnoob on 2014-03-07
> **mörgæs said:**
> I can't imagine any. 
All 32 bit ISO's should run, but not fast. Lubuntu or Bodhi are good choices.

I also thought Lubuntu would be the best fit, but Saucy is a total no-go because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

I'm almost tempted to recommend trying Trusty, but I want to do some additional testing before doing so.

I've never tried Bodhi so maybe it's time to have a look ;)

---

### Post by sudodus on 2014-03-08
> **kansasnoob said:**
> @ sudodus,

Are you still following this thread?

Yes :-)

*Edit*: The following command will print pae (highlighted), if there is a PAE flag. Independent of that, there is probably PAE capability.

```
grep --color pae /proc/cpuinfo
```

The Trusty daily build is fixed now for Pentium M and Celeron M. See the end of this bug report

[URL="https://bugs.launchpad.net/bugs/930447"]https://bugs.launchpad.net/bugs/930447
[/URL]
You can also check for the front side bus (FSB) speed, if 533 MHz, there is probably a PAE flag

```
sudo dmidecode|grep Clock
```

My Pentium M 1.7 GHz has 'only' 400 MHz FSB.

[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

-o-[I]

Stilnovo[/I], I think that *kansasnoob*'s ***PreciseGnomeClassicTweaks*** according to this link

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

works well in many old computers, and it might be easier to install with low RAM using the One Button Installer according to

[URL="https://help.ubuntu.com/community/OBI"]https://help.ubuntu.com/community/OBI

[/URL]because you need not pass a stage in the installation with the default desktop environment which might not work. In this case I recommend the tarball without OEM

[SIZE=3][FONT=courier new]**GnomeClassic1204.tar.xz**[/FONT][/SIZE]

---

### Post by kansasnoob on 2014-03-08
> **sudodus said:**
> Yes :-)

*Edit*: The following command will print pae (highlighted), if there is a PAE flag. Independent of that, there is probably PAE capability.

```
grep --color pae /proc/cpuinfo
```

The Trusty daily build is fixed now for Pentium M and Celeron M. See the end of this bug report

[URL="https://bugs.launchpad.net/bugs/930447"]https://bugs.launchpad.net/bugs/930447
[/URL]
You can also check for the front side bus (FSB) speed, if 533 MHz, there is probably a PAE flag

```
sudo dmidecode|grep Clock
```

My Pentium M 1.7 GHz has 'only' 400 MHz FSB.

[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

-o-[I]

Stilnovo[/I], I think that *kansasnoob*'s ***PreciseGnomeClassicTweaks*** according to this link

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

works well in many old computers, and it might be easier to install with low RAM using the One Button Installer according to

[URL="https://help.ubuntu.com/community/OBI"]https://help.ubuntu.com/community/OBI

[/URL]because you need not pass a stage in the installation with the default desktop environment which might not work. In this case I recommend the tarball without OEM

[SIZE=3][FONT=courier new]**GnomeClassic1204.tar.xz**[/FONT][/SIZE]

The OBI doesn't work in multi-boots though does it?

Andrea does want to keep Win XP to run some windows only software :)

---

### Post by mörgæs on 2014-03-08
The important part is that we have a 6.13.8 Celeron M, which belongs to the Dothan family. Only the Banias lack the PAE flag. 

Whoa, I hardly believe what I saw. Is the PAE bug fixed for 14.04? I'll go and test right away.

---

### Post by sudodus on 2014-03-08
Yes, the current version can do it at the advanced OBI level :-)

He should edit the partitions with gparted. With the labels obi-root and obi-swap, the OBI will find those partitions automatically (at the advanced level).

---

### Post by stilnovo1 on 2014-03-09
Hi to Everybody!

Yes, I've the pae flag:


grep --color pae /proc/cpuinfo

flags        : fpu vme de pse tsc msr [COLOR=#ff0000]**pae**[/COLOR] mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts


I discovered this when I read the sudodus's guide about installation with fake-pae... 


well/1, the second command:

sudo dmidecode|grep Clock

External Clock: 100 MHz

(uh, it's very low - isn't it?)

Well/2, I've read the tutorials about installation with OBI, but I evidently am a blockhead!!
I think to have understood this method in theory, where it seems very clear but when you pass to the action it becomes... (how can I say....)... yes: less clear!  :D

This evening I've discovered another little problem: if I don't turn on the wi-fi before Grub, I will not be able to load neither Bodhi nor Xubuntu.... I've tried this several times, and I've seen that it always happens: after the Grub screen, I choose the OS but after this the loading stops near immediately. Maybe this has nothing to do with this thread, but when in doubt... I prefer to write it down!

---

### Post by sudodus on 2014-03-09
> **stilnovo1 said:**
> Hi to Everybody!

Yes, I've the pae flag:


grep --color pae /proc/cpuinfo

flags        : fpu vme de pse tsc msr [COLOR=#ff0000]**pae**[/COLOR] mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts

Good - it makes it easier for you :-)
> 
I discovered this when I read the sudodus's guide about installation with fake-pae... 

well/1, the second command:

sudo dmidecode|grep Clock

External Clock: 100 MHz

(uh, it's very low - isn't it?)

Yes, but it might be 'doing more per clock cycle' compared older systems with higher frequency.

Well/2, I've read the tutorials about installation with OBI, but I evidently am a blockhead!!
I think to have understood this method in theory, where it seems very clear but when you pass to the action it becomes... (how can I say....)... yes: less clear!  :D

I can guide you through the installation with the OBI, if you wish. But if you are happy with Bodhi or Xubuntu (and can rememeber to turn on the wi-fi before Grub), you won't need it.
> 
This evening I've discovered another little problem: if I don't turn on the wi-fi before Grub, I will not be able to load neither Bodhi nor Xubuntu.... I've tried this several times, and I've seen that it always happens: after the Grub screen, I choose the OS but after this the loading stops near immediately. Maybe this has nothing to do with this thread, but when in doubt... I prefer to write it down!

You might be able to black-list some driver. I don't know the details how to find which one, but I know many other people around here know.

---

### Post by kansasnoob on 2014-03-10
I've been playing with Ubuntu Trusty using the GNOME Flashback w/metacity session the past couple of days on my VIA P4M800 box and the performance is pretty good. I notice that it now uses llvmpipe:

[ATTACH=CONFIG]251011[/ATTACH]

But it's still in development :guitar:

If you wanted to give it a try we should probably discuss that here:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

---

### Post by stilnovo1 on 2014-03-10
Hi to Everybody!

First of all, I still haven't done yet a thing: thanks for the help! 
(even if we will not be successful!!) :D

Well, I would be interested in a new installation via OBI, at the very least I will have learnt something new...

At this time, Bodhi in this laptop is more stable than Xubuntu, but also Bodhi freezes and I've just discovered another strangeness in both the OSs: the clock remains back.

The backup battery is new and ntp service is running (sudo service ntp status), but after a while the watch stops...

So, the actual situation is not so good, therefore if you say that OBi is not so hard to apply, I can try: all my personal datas are in XP partition!!

Maybe this could be interesting also for many other people that could feel this passage not so easy...

Or, in alternative, we could wait for Lubuntu 14.04....

Please, tell me what you think!

(this would be the 21th installation on this poor laptop ](*,))

---

### Post by gajdipajti on 2014-03-11
Hello, I am a Fujitsu Siemens Amilo L7320 user too.
Here are my findings regarding this problem:
[LIST]
[*]only working Ubuntu version is 10.04 with kernel 2.6.32. But here you must write your own xorg.conf to correct the resolution.
[*]From kernel 2.5.35 the timer problem exists (2.6.34 is ok).
[*]The problem also exists on Fedora.
[/LIST]

---

### Post by stilnovo1 on 2014-03-11
Hi Gajdipajti! Have you tried also the last version of Bodhi or other newer Ubuntu's ones?

---

### Post by mörgæs on 2014-03-11
> **stilnovo1 said:**
> 
Or, in alternative, we could wait for Lubuntu 14.04.

Please, tell me what you think!


I think you should try 14.04 now.

---

### Post by kansasnoob on 2014-03-11
> **mörgæs said:**
> I think you should try 14.04 now.

I think Andrea prefers Lubuntu and I've not yet seen an announcement regarding whether Lubuntu will go for LTS status in Trusty.

I blew up my Ubuntu Trusty + flashback w/metacity just by changing the resolution so I'm looking at other options regarding VIA P4M800 graphics and it really does look rather glum :(

---

### Post by mörgæs on 2014-03-12
Trying 14.04 could be done in a live boot. We don't need a full install.

I have: 
[http://www.linuxadvocates.com/2013/10/lubuntu-1404-goes-lts.html](http://www.linuxadvocates.com/2013/10/lubuntu-1404-goes-lts.html)

---

### Post by kansasnoob on 2014-03-12
> **mörgæs said:**
> Trying 14.04 could be done in a live boot. We don't need a full install.

I have: 
[http://www.linuxadvocates.com/2013/10/lubuntu-1404-goes-lts.html](http://www.linuxadvocates.com/2013/10/lubuntu-1404-goes-lts.html)

That's great news :D

I'm going to try the daily on my VIA P4M800 box today.

---

### Post by kansasnoob on 2014-03-12
I tried the Lubuntu 14.04 daily image from here:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64423/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64423/downloads)

And I think it's definitely worth a try.

I did however encounter one problem that I'll have to try and figure out, actually this also effected Ubuntu Trusty flashback w/metacity;

The default resolution is 1366x768 on my 18.5 LCD display but I prefer 1280x720. When I change to my desired resolution I get only a blank screen :(

But I'd think if the default resolution for your display is correct this may be worth a try.

I'll have to ask some questions in Ubuntu +1 about this new Gallium via llvmpipe driver because I'm a real dummy when it comes to Xorg :redface:

**Edit:** I started a thread here to learn how to deal with that blank screen thing after changing resolutions:

[http://ubuntuforums.org/showthread.php?t=2210695](http://ubuntuforums.org/showthread.php?t=2210695)

---

### Post by sudodus on 2014-03-12
> **stilnovo1 said:**
> Hi to Everybody!

First of all, I still haven't done yet a thing: thanks for the help! 
(even if we will not be successful!!) :D

Well, I would be interested in a new installation via OBI, at the very least I will have learnt something new...

At this time, Bodhi in this laptop is more stable than Xubuntu, but also Bodhi freezes and I've just discovered another strangeness in both the OSs: the clock remains back.

The backup battery is new and ntp service is running (sudo service ntp status), but after a while the watch stops...

So, the actual situation is not so good, therefore if you say that OBi is not so hard to apply, I can try: all my personal datas are in XP partition!!

Maybe this could be interesting also for many other people that could feel this passage not so easy...

Or, in alternative, we could wait for Lubuntu 14.04....

Please, tell me what you think!

(this would be the 21th installation on this poor laptop ](*,))

Yes, we can try. I think the best thing would be that you start by reading the documents at the following web sites
[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV")

[General description file]("http://ubuntuone.com/7fhghK1KFNmNuTqjVVV1IH")

[README file]("http://ubuntuone.com/4Py84gLbZrk8z12ZzSb8SW"),

and then we can agree on some date/time when we can chat, which gives faster feed-back (and progress).

---

### Post by kansasnoob on 2014-03-12
> **sudodus said:**
> Yes, we can try. I think the best thing would be that you start by reading the documents at the following web sites
[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV")

[General description file]("http://ubuntuone.com/7fhghK1KFNmNuTqjVVV1IH")

[README file]("http://ubuntuone.com/4Py84gLbZrk8z12ZzSb8SW"),

and then we can agree on some date/time when we can chat, which gives faster feed-back (and progress).

Sorry but I don't like it!

In fact I wish Lubuntu would drop the alternate images.

I get the feeling sometimes that we're trying to be Puppy, but Puppy does that well enough on there own:

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by sudodus on 2014-03-13
> **kansasnoob said:**
> Sorry but I don't like it!

In fact I wish Lubuntu would drop the alternate images.

I get the feeling sometimes that we're trying to be Puppy, but Puppy does that well enough on there own:

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

This way (with the OBI) it is possible to install 'your' Precise Gnome Classic Tweaks without needing the horsepower for Unity, because you need not install standard Ubuntu. This way I have installed Precise Gnome Classic Tweaks in an old Compaq with Pentium II at 400 MHz and 128 MB RAM. It did not run happily, but when I increased RAM to 192 MB, it was possible to run. Now that is a limit case, but it should work fairly well in *stilnovo1*'s computer.

So I think the OBI offers a possibility to install systems, that will work, but might get stuck during the installation, if you go along the conventional road (the desktop installer).

-o-

I agree that Puppy and other ultra-light-weight distros are good alternatives when there is not enough horsepower or memory for 'Precise Gnome Classic Tweaks', but those are rather primitive, and a last resort.

@*stilnovo1 *

As you see there are different ideas about what would work best for you. *kansasnoob* and *mörgæs* have suggested other alternatives. Both of them have more experience than I in general and *kansasnoob* particularly about your kind of graphics card, so I can fully understand if you listen to their advice ...

---

### Post by stilnovo1 on 2014-03-13
Hi to All!

Well, I know myself: I'm curious and I like to learn.

Actually:

- we still don't have the final Lubuntu 14.04 version but the iso testing images --> so, the installation would be temporary, today

- for me, OBI would be an experiment from which to learn something new, although I don't find this way so easy for the skills I have now

- the two installed Ubuntu's based OSs don't work both very well, so in any case I will substitute them with... Win 7?... just kidding!! :lolflag:

- jokes aside, I'd like to shift them with Lubuntu 14.04 (LTS!!)

So:

- I hope to download and install in this week end the Lubuntu iso testing images from the link provided by **kansanoob: **[http://iso.qa.ubuntu.com/qatracker/m...4423/downloads]("http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64423/downloads") --> in this case I will overwrite Xubuntu and, at the moment, I will keep the more stable Bodhi Linux for pragmatic reasons

- I will read the links provided by **sudodus **regarding OBI --> really, I've already read the texts of those links, I hope to better understand their content now, after having learnt more things thanks to you all!

Yes, it is useless to deny it: if it will work, it would have more appeal for me the 'traditional' installation... anyway now I want at least to understand the OBI method.

I have installed Xubuntu 12.04 starting from alternate iso, so without a working DE... I've also tried the mini-iso image, which is also DE-less... so the DE hasn't interfered during the installation, am I right?

OK, ready for the 21st installation. Next stop: Lubuntu 14.04 testing iso!

---

### Post by kansasnoob on 2014-03-13
>  we still don't have the final Lubuntu 14.04 version but the iso testing images --> so, the installation would be temporary, today

Unless the OS breaks you should be able to just keep applying updates and end up with the final ;)

There was one time that the release notes mentioned the need to edit one file manually so it's always a good idea to read the release announcement and release notes.

When you're ready to install be sure to check the installation media for defects, then try the live session just to see if it seems to work, but on lower resource machines I always reboot and choose install from initial boot menu - this just seems to work better for me :D

---

### Post by sudodus on 2014-03-14
> **stilnovo1 said:**
> Hi to All!

Well, I know myself: I'm curious and I like to learn.

Actually:

- we still don't have the final Lubuntu 14.04 version but the iso testing images --> so, the installation would be temporary, today

- for me, OBI would be an experiment from which to learn something new, although I don't find this way so easy for the skills I have now
...
- I hope to download and install in this week end the Lubuntu iso testing images from the link provided by **kansanoob: **[http://iso.qa.ubuntu.com/qatracker/m...4423/downloads]("http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64423/downloads") --> in this case I will overwrite Xubuntu and, at the moment, I will keep the more stable Bodhi Linux for pragmatic reasons

- I will read the links provided by **sudodus **regarding OBI --> really, I've already read the texts of those links, I hope to better understand their content now, after having learnt more things thanks to you all!
...

Good luck with Lubuntu Trusty, and if you want to try the OBI afterwards, just let me know :-)

-o-

Right now I'm building a lighter Lubuntu Core Trusty system from the mini.iso. If it works well, I'll upload it for installation via the OBI.

---

### Post by stilnovo1 on 2014-03-14
only to advise that the actual link to download daily live iso build for Lubuntu 14.04 is [http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64601/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64601/downloads)

I'm downloading now... tomorrow or on sunday I will try to install it!

---

### Post by kansasnoob on 2014-03-14
> **stilnovo1 said:**
> only to advise that the actual link to download daily live iso build for Lubuntu 14.04 is [http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64601/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/64601/downloads)

I'm downloading now... tomorrow or on sunday I will try to install it!

Cool :D

Just a few reminders:

#1: Be sure and check the md5sum of your download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

#2: Even though you've checked the md5sum be sure to run Check disc for defects:

[http://pix.toile-libre.org/upload/original/1354180067.png](http://pix.toile-libre.org/upload/original/1354180067.png)

Sometimes laptops have old, tired, and dirty optical drives so it may me better to use a live USB if possible ;)

#3: After that check shows no errors try the live DE - if the live DE fails there is probably little chance that the installed version will work :(

#4: Do NOT start the installation from the live DE! Please reboot and choose install from the main boot menu - it uses much lower resources!

#5: Do NOT choose to auto-login during installation! Lubuntu offers more than one session so if the default DE does not boot it will be much easier for you to choose a different session if desired :)

#6: Remember that you're now using a release that's still in development so post questions here:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

#7: Feel free to send me a PM!

---

### Post by stilnovo1 on 2014-03-16
nooooooooooooooo!!!!

Excuse me, but my installation has already ended!!! Sic, livecd gives me an alternated red-blue stripes screen without the pointer.....

Yes, it doesn't freeze but it's impossible to use it....

---

### Post by kansasnoob on 2014-03-16
> **stilnovo1 said:**
> nooooooooooooooo!!!!

Excuse me, but my installation has already ended!!! Sic, livecd gives me an alternated red-blue stripes screen without the pointer.....

Yes, it doesn't freeze but it's impossible to use it....

Were you able to use the live DE at all?

---

### Post by stilnovo1 on 2014-03-16
Hi Erick! 
The live DE works, but the pointer doesn't appear and the screen has those alternated blue and red stripes... so, without a visible pointer, you have to go -how can I say- in a "blindfold way"... so, also the installation would be not so easy. It's not freezed, if you move with tab key you can choose some options, and also the screen resolution it would be ok, but....

---

### Post by stilnovo1 on 2014-03-16
Update: there is a very very lilliputian point (it seems about a single pixel!!): this is the pointer!!!
Only Sherlock Holmes could have found it!!!
sic!!

---

### Post by kansasnoob on 2014-03-16
I just checked the 20140315 Lubuntu i386 image and it's borked!

Running "Check disc for defects" returns "1 error found" even though the md5sum passed.

Did you run the "Check disc for defects"?

---

### Post by slooksterpsv on 2014-03-16
I've read most the information in this thread, and I have a few questions regarding your attempts with 12.04 LTS

1. I was reading about the display issue here and how to create an xorg file with the necessary information for color depth and resolutions - [http://www.linlap.com/fujitsu_amilo_l7320gw](http://www.linlap.com/fujitsu_amilo_l7320gw) - were these the same ones you tried?

2. Did you attempt to boot the system with acpi=off or it may be noacpi? I'm wondering if the power management could be an issue there.

3. You can also try ndiswrapper to install the S3 graphics in Linux. It basically is a wrapper that takes the windows driver (you have to provide it) and uses it to wrap around the graphics.

4. BIOS Updates - have you applied any BIOS updates to the system?

---

### Post by stilnovo1 on 2014-03-16
@kansasnoob: Yes, I've checked right now after your suggest: no errors found (I've hoped for a moment about this!)

@slooksterpsv:
1. Yes, those are the ones I've tried. If you do some googling, you can find other two similar variants. The result has always been a fail to load openchrome and a loading of vesa (I've read this from the log file of xorg) with a limited XGA screen resolution instead of a correct WXGA...

2. no, I didn't find any suggestion in the forums about this so I didn't try it

3. In another (Lubuntu 13.10) installation on another pc I had to use ndiswrapper for the modem, so I've already "met" it!! Could it slow down graphic performances?

4. In Fujitsu-Siemens web-site there is a nice system to check for updates. I've checked until two years ago

I remeber that this problem was present also during installation of:

Ubuntu 12.04
Kubuntu 12.04

(I've done some installation trials...)

---

### Post by stilnovo1 on 2014-03-16
just tried Xubuntu 14.04 daily build: same defect....

---

### Post by kansasnoob on 2014-03-16
> **stilnovo1 said:**
> just tried Xubuntu 14.04 daily build: same defect....

Yes, Ubuntu itself is borked right now, but I'm surprised you're passing the "Check disc for defects" because I'm NOT!

Development releases are always "hit or miss" when it comes to daily images but I also wonder why you had trouble with Ubuntu 12.04 and Xubuntu 12.04. Maybe if you're using a DVD drive you should try a live USB?

I'm particularly concerned because you show the discs passing while I show them failing, and I've even checked using testdrive + virtualbox so I know it's not a burn issue.

---

### Post by stilnovo1 on 2014-03-16
Hi! During my countless installations, I've tried both dvd and usb... I've done the check with my pendrive, that's what I've used today...

Also the check made with Xubuntu says 'ok'.

Well, Ubuntu-misteries!!!

But is there an Openchrome or a Lubuntu developer that could help us?

---

### Post by kansasnoob on 2014-03-16
> **stilnovo1 said:**
> Hi! During my countless installations, I've tried both dvd and usb... I've done the check with my pendrive, that's what I've used today...

Also the check made with Xubuntu says 'ok'.

Well, Ubuntu-misteries!!!

But is there an Openchrome or a Lubuntu developer that could help us?

The devs very seldom frequent the forums :(

But I suspect it's something specific to that laptop because we have identical graphics chips:

> Mine:  1:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
Yours: 1:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)

I'm out of ideas :redface:

---

### Post by kansasnoob on 2014-03-16
> **gajdipajti said:**
> Hello, I am a Fujitsu Siemens Amilo L7320 user too.
Here are my findings regarding this problem:
[LIST]
[*]only working Ubuntu version is 10.04 with kernel 2.6.32. But here you must write your own xorg.conf to correct the resolution.
[*]From kernel 2.5.35 the timer problem exists (2.6.34 is ok).
[*]The problem also exists on Fedora.
[/LIST]

I wanted to just bump this ahead as a reminder.

Of course using 10.04 isn't really a viable option :(

---

### Post by stilnovo1 on 2014-03-17
Thanks kansansnoob anyway! Now it's something like a challenge, although I'm near hopeless....

Also from the gajdipajti's post we can deduce that there is something strange with Amilo L7320.... I see that this thread has received a quite high number of visits (by the way: I've seen that the number of views' counter of this thread is the same from some days, it seems no more updated), so maybe there are out there several persons with this problem. The hardware of this Amilo 7320 is not so bad, with XP I can do a "normal" use of it (youtube, websurfing, working issues, some games etc.), but even with Bodhi the general result is poor... in my naivety I thought that all these posts in this forum could be an occasion, a source for developers... at this time I even am not able to begin an installation with both Xubuntu 14.04 nor Lubuntu 14.04 (yes, daily buillds but...)

:-(

---

### Post by sudodus on 2014-03-17
At this point, maybe you feel like trying to install kansasnoob's Precise Gnome Classic Tweaks with the OBI?

Edit: See posts #20 and #35.

---

### Post by stilnovo1 on 2014-03-17
@ sudodus: yes, you are right: at this point I have to try this way you suggested.
In the next days I will read the links you provided to me; I hope this will be useful also for all the users that are reading this thread (dear readers, please: appreciate our efforts!!)
:-)

---

### Post by stilnovo1 on 2014-03-19
Hi to All!

@sudodus: I've begun to read the documents about OBI, and I would have some questions:

- my graphic chipset has a bug (described by kansasnoob) in Lubuntu 13.10, so I cannot use it: have you already set up a compressed file from a recent Lubuntu Trusty daily build?

- why does my system should work after an installation via OBI, since it doesn't work with a live DE session? The loaded drivers are the same, aren't they?

Thanks in advance!

P.S.: @this-thread-readers: does anybody have already tested OBI method on a Fujitsu Amilo 7320?

---

### Post by sudodus on 2014-03-19
> **stilnovo1 said:**
> Hi to All!

@sudodus: I've begun to read the documents about OBI, and I would have some questions:

- my graphic chipset has a bug (described by kansasnoob) in Lubuntu 13.10, so I cannot use it: have you already set up a compressed from a recent Lubuntu Trusty daily build?

I suggest that you try ***Precise Gnome Classic Tweaks***, the version without OEM, which is Ubuntu 12.04 LTS tweaked, and I think *kansasnoob* manages to run your kind of systems with that version and flavour of Ubuntu. The advantage for old computers and computers that might not work with standard Ubuntu is that this system will by-pass the standard installation and you will have an installed and tweaked system 'at once'.

There is also a system based on ***Lubuntu Core Trusty beta 1***, that you can try. It might or might not work ... worth trying, but I think chances for success are smaller than with *Precise Gnome Classic Tweaks**.*** See this link (about testing the ***9w*** installer, post #88, #89 and the following posts)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

*Edit*: But 9w cannot create systems with dual booting within the same drive. You can install a portable system into a USB pendrive and test it in computer that can boot from USB.

> 
- why does my system should work after an installation via OBI, since it doesn't work with a live DE session? The loaded drivers are the same, aren't they?

Thanks in advance!

P.S.: @this-thread-readers: does anybody has already tested OBi on a Fujitsu Amilo 7320?

I don't think any flavour of 13.10 will work for you, in this case it does not help with the OBI. The drivers are the same as in the DE.

---

### Post by stilnovo1 on 2014-03-19
Thanks sudodus!!

Well, since it (the "nice" Amilo!) can boot from USB, I could buy a 8gb pendrive since I have several external hard disks but they are full of backups and if I'm right this kind of installation destroys the datas on them... am I right?

Excuse me, I have not been (Pangolin) precise!! The live DE that doesn't work (red and blue stripes) is the Lubuntu Trusty daily build that I've mentioned in post #43... the 13.10 live DE session works very well... telling the truth, all the live DE sessions I've tried (Lubuntu 13.10; Xubuntu 12.04; Ubuntu 12.04; Kubuntu 12.04) work well, the problems are during (freezings) and above all after the installation... 

For these reasons I've tried also the alternative iso versions, Ubuntu's 12.04 mini-iso included!

It's a hard world!!

---

### Post by sudodus on 2014-03-19
The One Button Installer can create dual boot (and multiple boot) if you wish. But the 9w installer cannot.

Anyway, in both cases it can be nice to try systems running in a USB pendrive. If you want a fast system, I suggest that you read the following links. Notice that I have not found any really fast 8 GB pendrive, while there are several reasonable fast 16 GB and 32 GB pendrives.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by stilnovo1 on 2014-03-30
Hi to Everybody!

This week I'll buy a 16GB USB pendrive since there is a strong discount in a famous store (9,90&#8364;).

But now I have also a good news for all the Amilo L7320 owners: now I'm running from a week a stable version of Lubuntu 14.04!! 

Good graphics, high speed, no freezes etc, although it has been not so smooth to install it... the installation presented several problems, and the only thing that doesn't work very well is Grub (the new version), that freezes and you have to manage it a little when you turn on the pc.... but once you have passed it, Lubuntu 14.04 gives a powerful higher gear to this problematic computer...

It can even play Youtube videos as it has never been before!! All the things have been very smooth until now, I'll continue to use it in order to confirm this very (but very) good feeling!

In the next days, with more time, I will deepen this point and anyway I will test OBI....

---

### Post by stilnovo1 on 2014-04-02
Well, now I describe how I've installed Lubuntu 14.04 on Amilo L7320.

First of all, after having (obviously) downloaded the daily builds, I've used an USB pendrive to install it (with Unetbootin).

Here there is the first problem: the pointer during the installation is only a little point that you have to "search for" on the screen; you will see a bad graphic made by alternated red and blue stripes. Do not let that demoralize you!! The difficult thing is to identify where is the pointer  in order to advance during the installation, but if you look in the screen with a lot of attention, you can identify it. Once you can manage this (you will see a little brighter point: that is the pointer!!), you can do the installation without other particular problems.

Ok, when you have finished this part, you are ready for rebooting. If you have (like me) other OSs installed (in my case: Windows XP + Bodhi Linux + Xubuntu 12.04 + Lubuntu 14.04), you will see the Grub menu: it will seem freezed, but if you keep the arrow keys pressed, the menu "will come to life": be fast to choose your choice, otherwise it will block itself.... but in this case just press (for a while) and the menu will become available again.

At this point, go to edit the loading option of Lubuntu (pressing the letter 'e' on Lubuntu 14.04, in my case the first option on Grub): here you need to insert 'nomodeset' as described here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Follow the guide to set permanently this, it's not so difficult: I'm a beginner and I did it!

Once passed also this point, Lubuntu 14.04 will be loaded and - surprise!! - all will be ok: no more strange things, no more freezes, only a normal, fast and -above all - working system! Your Amilo L7320 has never been so fast (and furious) like now!!

Yesterday "System Updates" has stopped to work (I've started a bug on Launchpad), but you can update via terminal with the usual 'sudo apt-get upgrade' etc. and in this way it will work without any problem.

Since the Amilo's screen is quite good, also in comparison with newer computers, I've used it to see some DVDs and Youtube's videos: this computer has never been so good!

I suppose that the OBI method should permit to avoid the problematic part of installation, so be patient and I'll try also this way...

---

### Post by sudodus on 2014-04-02
Great work :KS

You are no longer a beginner :-)

---

### Post by kansasnoob on 2014-04-02
> **sudodus said:**
> Great work :KS

You are no longer a beginner :-)

+1 :guitar:

---

### Post by stilnovo1 on 2014-04-02
Thank you sudodus and kansanoob!! But I'm still too slow and not so efficient...

Today I've bought the USB pendrive: 16GB from TDK at 9,90&#8364; (in speciale offer): it's not so bad, isn't it?

So, I'm (almost) ready also for the OBI experience!!

---

### Post by kansasnoob on 2014-04-02
> **stilnovo1 said:**
> Thank you sudodus and kansanoob!! But I'm still too slow and not so efficient...

Today I've bought the USB pendrive: 16GB from TDK at 9,90€ (in speciale offer): it's not so bad, isn't it?

So, I'm (almost) ready also for the OBI experience!!

Slow and inefficient describes me to a T :lolflag:

If I don't do at least ten stupid things every day it means I'm sleeping in :redface:

You're doing great =d>

---

### Post by sudodus on 2014-04-02
> **stilnovo1 said:**
> Thank you sudodus and kansanoob!! But I'm still too slow and not so efficient...

Today I've bought the USB pendrive: 16GB from TDK at 9,90€ (in speciale offer): it's not so bad, isn't it?

So, I'm (almost) ready also for the OBI experience!!

I hope it's good, but I have no own experience of TDK pendrives.

---

### Post by stilnovo1 on 2014-04-10
@sudodus: right this evening I've read (better: studied) again the documents about OBI you linked... the possibility to bring with you your (very) personal operating system is really fascinating, but I don't find it so easy to proceed...
If I have correctly understood, once I've got my USB pendrive (done!), I have to choose the compressed tarball file. 
I would have chosen: LubuntuTrusty-oem-feb12.tar.xz
What do you think? What does "feb12" mean?
I've also thought that it would be very nice to give to my colleagues a USB pendrive with their personal OS that they can load in every computer, at home and at office: since Lubuntu 14.04 seems to work fine (apart a bug that I've inserted in Launchpad regarding System Updates) on Amilo, I could propose it as OS to use not only on this laptop but thanks to a simple 16GB USB pendrive everywhere: am I wrong?
So, in your opinion, do you think is that a good idea (Lubuntu Trusty)?
If so, and if I'm right, I have to:
- download the mentioned tarball (LubuntuTrusty-oem-feb12.tar.xz)
- to mount the USB pendrive
- to format it (ext4? ntfs?)
- to create the main and the swap partition
- ok, now the doubts are increasing... help!!

---

### Post by sudodus on 2014-04-11
> **stilnovo1 said:**
> @sudodus: right this evening I've read (better: studied) again the documents about OBI you linked... the possibility to bring with you your (very) personal operating system is really fascinating, but I don't find it so easy to proceed...
If I have correctly understood, once I've got my USB pendrive (done!), I have to choose the compressed tarball file. 
I would have chosen: LubuntuTrusty-oem-feb12.tar.xz
What do you think? What does "feb12" mean?

It was created from an installed system that was updated/upgraded to the 'daily updated status' of february 12.
> 
I've also thought that it would be very nice to give to my colleagues a USB pendrive with their personal OS that they can load in every computer, at home and at office: since Lubuntu 14.04 seems to work fine (apart a bug that I've inserted in Launchpad regarding System Updates) on Amilo, I could propose it as OS to use not only on this laptop but thanks to a simple 16GB USB pendrive everywhere: am I wrong?
It is possible for most computers.

But in some special cases a general system with the free drivers will not work with the graphics or the wifi, so a proprietary driver is necessary. This can often be done after booting with the boot option nomodeset and installing the proprietary driver for that particular hardware.

And computers with UEFI instead of old style BIOS will not run 32-bit operating systems unless you switch off UEFI.
> 
So, in your opinion, do you think is that a good idea (Lubuntu Trusty)?
If so, and if I'm right, I have to:
- download the mentioned tarball (LubuntuTrusty-oem-feb12.tar.xz)
Yes, it is worth trying.

If you have problems, wait until I have made a tarball with the final released (and maybe also debugged) version 14.04 LTS. It is a question of one or two weeks (I think and hope).> 
- to mount the USB pendrive
- to format it (ext4? ntfs?)
- to create the main and the swap partition
- ok, now the doubts are increasing... help!!

You need two drives:

1. The One Button Installer should be installed into one USB pendrive

2.  The target system LubuntuTrusty-oem-feb12 should be installed by the  One Button Installer into another drive, which can be an internal drive  or a USB drive.

-o-

It is enough to plug in the USB pendrive. It will be formatted automatically, so it is a waste of time to format it before the installation. It is easiest to run at the basic OBI level, if you want to use the whole drive (in this case the whole USB pendrive).

You can create the main and swap partition with gparted, if you are not happy with the default partitioning. In that case, run at the advanced OBI level. This is also how to make dual boot or multi boot systems.

---

### Post by stilnovo1 on 2014-04-12
@sudodus: but you didn't say that you and amjjawad are like Hollywood stars!! I've found a 35 minutes video on Youtube where you and Ali explain OBI.... tomorrow I will watch it!

---

### Post by stilnovo1 on 2014-04-12
excuse me, the link: [https://www.youtube.com/watch?v=s2BYU0_3mUY](https://www.youtube.com/watch?v=s2BYU0_3mUY)

---

### Post by sudodus on 2014-04-12
That video is 'general talk' about what we are doing.

I think you need more details, and you can get it via discussions here, or if this gives too slow feedback, maybe via chatting (I can use skype-chat or google-chat). I think it is better with a written chat, because many things need to be exact, which they are when written (instead of spoken).

---

### Post by stilnovo1 on 2014-05-11
Hi to Everybody!

Now it's some time I'm using Lubuntu 14.04 on this laptop: things are ok and I strongly suggest to follow the procedures described in this thread. 

You will have a fast problems-free modern laptop, it's not difficult!

---

