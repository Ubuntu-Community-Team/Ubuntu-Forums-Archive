---
title: "Flash Player 10.1 is out!"
date: 2009-11-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shakaran on 2009-11-17
For the moment only .tar.gz

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Bugtracker:
[https://bugs.adobe.com/flashplayer/](https://bugs.adobe.com/flashplayer/)

Someone have a .deb? when it would be on repos?

---

### Post by Merk42 on 2009-11-17
This, so far, is 32-bit only I see.

---

### Post by kostkon on 2009-11-17
Nice! Also, Adobe Air 2 beta is available, if anyone's interested. There is a deb for it.

Anyway, from the release notes:
> To deliver on a high level of consistency and move onto mobile platforms with limited memory and processing resources, Flash Player 10.1 leverages hardware acceleration of graphics and video and many other performance improvements, such as rendering, scripting, memory utilization, start-up time, battery and CPU optimizations.
I wonder if that means that it will also have better performance in Linux.

---

### Post by Schendje on 2009-11-17
> **kostkon said:**
> Nice! Also, Adobe Air 2 beta is available, if anyone's interested. There is a deb for it.

Anyway, from the release notes:

I wonder if that means that it will also have better performance in Linux.
If I'm not mistaken, I read somewhere the hardware acceleration was only for Windows, not Linux or OS X. :(

---

### Post by slakkie on 2009-11-17
It didn't hit the repo's:

```

apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 10.0.32.18-1karmic2
  Candidate: 10.0.32.18-1karmic2
  Version table:
 *** 10.0.32.18-1karmic2 0
        990 http://archive.canonical.com lucid/partner Packages
        500 http://archive.canonical.com karmic/partner Packages
        100 /var/lib/dpkg/status

```

---

### Post by xebian on 2009-11-17
64-bit is not out yet.  Hopefully in a few days?  :(

---

### Post by shakaran on 2009-11-17
> **kostkon said:**
> 
I wonder if that means that it will also have better performance in Linux.

I hope. My firefox hogging the CPU with wordpress blogs with the plugin WP-Cumulus.

---

### Post by hikaricore on 2009-11-17
Lets just hope it's an improvement for once..

---

### Post by Eclipse. on 2009-11-17
Its only a prerelease, it might not even hit the repos at all.Easy enough to install manually anyway. :)

---

### Post by SevenMachines on 2009-11-17
i think i remember something from adobe mentioning that 10.1 on amd64 wouldnt be a simultaneous release with the other versions. i'd love to be proved wrong but i'm not holding my breath here

---

### Post by zika on 2009-11-17
> **shakaran said:**
> For the moment only .tar.gz

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Bugtracker:
[https://bugs.adobe.com/flashplayer/](https://bugs.adobe.com/flashplayer/)

Someone have a .deb? when it would be on repos?You do not need a .deb. Just open [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p1_linux_111709.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p1_linux_111709.tar.gz) with file-roller, extract libflashplayer.so in ~/.mozilla/plugins (make a back-up for the file from previous version, if You have one) and ... that's it. I think it's only 32-bit version. If You're not satisfied, revert back to file from previous version that You did make back-up of.

---

### Post by bluelamp999 on 2009-11-17
> **zika said:**
> You do not need a .deb. Just open [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p1_linux_111709.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p1_linux_111709.tar.gz) with file-roller, extract libflashplayer.so in ~/.mozilla/plugins (make a back-up for the file from previous version, if You have one) and ... that's it. I think it's only 32-bit version. If You're not satisfied, revert back to file from previous version that You did make back-up of.

I don't have a ~/.mozilla/plugins folder?

I do have 2 libflashplayer.so files, one at */usr/lib/flashplugin-installer/* and one in */usr/share/ubufox/plugins/*

Any idea how to install in this case?

Thanks

---

### Post by zika on 2009-11-17
> **bluelamp999 said:**
> I don't have a ~/.mozilla/plugins folder?

I do have 2 libflashplayer.so files, one at */usr/lib/flashplugin-installer/* and one in */usr/share/ubufox/plugins/*

Any idea how to install in this case?

Thanks
1. If You were to install flash-plug-in "my way" You are free to make that folder, not using sudo, simply with **mkdir ~/.mozilla/plugins**. But please investigate more before You adopt "my way" ...
2. I'm not sure enough to give advice in Your case. I do not know how they were installed.
3. Environment that works for me (FF 3.5, 3.6, 3.7 on Lucid): ```
~$ ls /home/zika/.mozilla/plugins/ -l
total 9340
-rwxrwxrwx 1 zika zika 9560488 2009-07-18 06:04 libflashplayer.so
lrwxrwxrwx 1 zika zika      50 2009-11-17 18:22 libnpjp2.so -> .../jre1.6.0_18/lib/amd64/libnpjp2.so
```

---

### Post by paul_in_london on 2009-11-17
This is what I did after downloading the .tar.gz:

```
cd /usr/lib/adobe-flashplugin/
sudo cp libflashplayer.so libflashplayer.so.original
sudo mv  /home/paul/Downloads/flashplayer10_1_p1_linux_111709.tar.gz .
sudo tar xzvf flashplayer10_1_p1_linux_111709.tar.gz
cd install_flash_player_10_linux/
./flashplayer-installer
sudo cp libflashplayer.so ../

```

HTH

---

### Post by zika on 2009-11-17
There is a reason why I insist in not using system's folders for plugins. It is simple: security. Placing all plugins in local folder with only user's permissions is a good thing to do. Just my .01$.

---

### Post by cariboo on 2009-11-17
The only problem with putting plugins in your home folder, is if you have other users on the system, you'll have to install the plugin in each of their home folders too. Putting the plugin in /usr/lib/mozilla/plugins allows the plugin to be used system wide.

---

### Post by zika on 2009-11-17
> **cariboo907 said:**
> The only problem with putting plugins in your home folder, is if you have other users on the system, you'll have to install the plugin in each of their home folders too. Putting the plugin in /usr/lib/mozilla/plugins allows the plugin to be used system wide.I know that and I wanted to mention that but for the sake of brevity of my post I left it out. Even with that point taken, I wote for putting plugin in home folder. Not to mention the case when You have separate /home partition ... As I said, just my .01$. "Install" is a big word here when the whole "installation" is just a copying of a single file ...

---

### Post by nortexoid on 2009-11-17
So is anyone noticing substantial improvements in flash playback performance? I'm waiting around for "definitive" benchmarks.

---

### Post by bluelamp999 on 2009-11-17
No matter where I put the the file, my installed flash plugin version is still 10.0.r32???

I give up...

---

### Post by Ric_NYC on 2009-11-17
> **nortexoid said:**
> So is anyone noticing substantial improvements in flash playback performance? I'm waiting around for "definitive" benchmarks.




I noticed no difference... Still freezing, choppy images.

Is this a lost cause?

---

### Post by blur xc on 2009-11-17
> **Ric_NYC said:**
> I noticed no difference... Still freezing, choppy images.

Is this a lost cause?

Out of curiosity, on what websites are you experiencing freezing, choppy images?  And also, what hardware are you running?

Thanks,
BM

---

### Post by Ric_NYC on 2009-11-17
> **blur xc said:**
> Out of curiosity, on what websites are you experiencing freezing, choppy images?  And also, what hardware are you running?

Thanks,
BM


Youtube.
ATI Radeon Xpress 1200.

---

### Post by blur xc on 2009-11-17
I've got a nvidia card and I can view full screen hd youtube videos and a host of other sites very smoothly.  They area bit high on the cpu usage, but smooth, nonetheless...  

So, would it be more accurate to say that your video card driver is the problem, not flash?  How can flash make your video card and driver play better w/ Ubuntu (or linux, in general)?

BM

---

### Post by Seventh Reign on 2009-11-17
Adobe already stated that the improvements to the Linux version would be minimal if not non-existent.

---

### Post by Merk42 on 2009-11-17
> **Seventh Reign said:**
> Adobe already stated that the improvements to the Linux version would be minimal if not non-existent.

OOoh let's hope they're "not non-existent"

---

### Post by waffletten on 2009-11-17
Sorry for posting to the lynx forum, I couldn't find a thread for Karmic. I have been reading forums for a long time, but I am a first time poster.
 
Bummed to hear that no improvement from other users. I have dual boot revo 3600 (atom 330/NVIDIA ion) and there was a noticeable difference in Windows 7 performance when watching you tube and surfing flash heavy web sites. I was hoping that there would be some improvement for my ubuntu 9.10 OS on the same machine.
 
Anyone tried this out on a comparable system (NVIDIA ion) in Karmic? I am hesitant to change if there is no improvement with other users.

---

### Post by lovinglinux on 2009-11-17
No improvement here.

---

### Post by baizon on 2009-11-18
> **lovinglinux said:**
> No improvement here.

Damn you Adobe :(

---

### Post by 23meg on 2009-11-18
> **waffletten said:**
> 
Anyone tried this out on a comparable system (NVIDIA ion) in Karmic? I am hesitant to change if there is no improvement with other users.

After some brief testing, I noted a slight imporvement with Firefox on Atom 330 + Ion, but it may not be correct to attribute it to the Flash plugin itself. With Epiphany, Vimeo HD videos play perfectly.

Can others reproduce this Flash performance gap between Epiphany (WebKit) and Firefox, and does anyone know the reason? I see the same behavior on a 8800GT, with older versions of the Flash plugin as well.

---

### Post by philinux on 2009-11-18
Waiting for the 64 bit version to test drive. However regarding current performance I get much smoother full screen flash if I switch the cpu governor to conservative or performance rather than the default ondemand.

nVidia 8600GT.

---

### Post by psyke83 on 2009-11-18
> **waffletten said:**
> Sorry for posting to the lynx forum, I couldn't find a thread for Karmic. I have been reading forums for a long time, but I am a first time poster.
 
Bummed to hear that no improvement from other users. I have dual boot revo 3600 (atom 330/NVIDIA ion) and there was a noticeable difference in Windows 7 performance when watching you tube and surfing flash heavy web sites. I was hoping that there would be some improvement for my ubuntu 9.10 OS on the same machine.
 
Anyone tried this out on a comparable system (NVIDIA ion) in Karmic? I am hesitant to change if there is no improvement with other users.

Off-topic, but on Windows you need the latest beta driver from NVIDIA (195.55). From: [http://www.nvidia.com/object/win7_winvista_32bit_195.55.html](http://www.nvidia.com/object/win7_winvista_32bit_195.55.html)

> # Adds GPU-acceleration for smoother online HD videos with the new Adobe Flash 10.1 beta. Learn more here.

Perhaps the next Linux driver will add GPU acceleration support as well?

---

### Post by baizon on 2009-11-18
There is a nice test. It seems that ATi drivers have some problems with the new flash :(

[http://www.anandtech.com/video/showdoc.aspx?i=3678&p=1]("http://www.anandtech.com/video/showdoc.aspx?i=3678&p=1")

---

### Post by waffletten on 2009-11-18
Off-topic on windows: I had the 186.18 (WHQL) NVIDIA driver installed before I installed the flash 10.1 beta and the performance increase was incredible! This morning I installed NVIDIA driver 191.07 (WHQL) and the performance decreased? Then I installed the 195.55 (beta) and performance increased to the level I observed with 186.18 driver / flash 10.1. Weird.
 
Back to linux: On another topic, the NVIDIA linux beta driver 190.42 did make a big difference in performance for my R3600 Revo (atom 330/NVIDIA ion) under ubuntu 9.10. I followed the guide here:
 
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)
 
Thanks for all the feedback!!
 
PS I see a synopsis with some more tests (anandtech included) here: [http://www.liliputing.com/2009/11/adobe-flash-player-10-1-tested-extensively-hd-flash-video-is-about-to-explode.html](http://www.liliputing.com/2009/11/adobe-flash-player-10-1-tested-extensively-hd-flash-video-is-about-to-explode.html)

---

### Post by executor on 2009-11-18
under ubuntu 9.10 her ,i have dual atom 330, intel gpu, and now i can watch in hd on youtube, but not in fullscreen, so it is some improvement.
did use the 10.0-32 before, that did not work at all on youtube hd.

---

### Post by blur xc on 2009-11-18
> **baizon said:**
> Damn you Adobe :(

You say, "Damn you Adobe", but Adobe is actually working on software for Linux.  What's ATI doing?  

I say thank you Adobe, for putting an effort into the 1% of computer users running Linux.  Damn you ATI for doing nothing...

BM

---

### Post by 23meg on 2009-11-18
> **executor said:**
> under ubuntu 9.10 her ,i have dual atom 330, intel gpu, and now i can watch in hd on youtube, but not in fullscreen, so it is some improvement.
did use the 10.0-32 before, that did not work at all on youtube hd.

To update my previous comment: Strangely, HD videos stutter in the first few plays, but after a plays they get close to smooth, or completely smooth (depending on the browser as well).

I'm tired of experimenting with various Flash plugins on different hardware, so I switched to the surefire solution: [a Greasemonkey script]("http://userscripts.org/scripts/show/34765") that loads the embedded video source in gecko-mediaplayer.

---

### Post by rajeev1204 on 2009-11-18
> **Schendje said:**
> If I'm not mistaken, I read somewhere the hardware acceleration was only for Windows, not Linux or OS X. :(

Correct.

---

### Post by lovinglinux on 2009-11-18
> **blur xc said:**
> You say, "Damn you Adobe", but Adobe is actually working on software for Linux.  What's ATI doing?  

I say thank you Adobe, for putting an effort into the 1% of computer users running Linux.  Damn you ATI for doing nothing...

BM

IMO, there is a big difference. You don't have to buy an ATI card if you don't want to, but flash is everywhere and there is nothing you can do about it.

I have started a new thread and poll about this: [http://ubuntuforums.org/showthread.php?t=1330866](http://ubuntuforums.org/showthread.php?t=1330866)

---

### Post by blur xc on 2009-11-18
> **lovinglinux said:**
> IMO, there is a big difference. You don't have to buy an ATI card if you don't want to, but flash is everywhere and there is nothing you can do about it.

I have started a new thread and poll about this: [http://ubuntuforums.org/showthread.php?t=1330866](http://ubuntuforums.org/showthread.php?t=1330866)

I know, flash is everywhere.  I have a nvidia card, and flash performance is great.  Full screen youtube videos play smoothly, and online flash based games work 100% great, I'd say even a touch better than my win xp machine.

BM

---

### Post by psyke83 on 2009-11-22
> **23meg said:**
> After some brief testing, I noted a slight imporvement with Firefox on Atom 330 + Ion, but it may not be correct to attribute it to the Flash plugin itself. With Epiphany, Vimeo HD videos play perfectly.

Can others reproduce this Flash performance gap between Epiphany (WebKit) and Firefox, and does anyone know the reason? I see the same behavior on a 8800GT, with older versions of the Flash plugin as well.

Try disabling the apparmor profile for Firefox. I assume the same instructions for Karmic [should work]("http://www.ubuntu.com/getubuntu/releasenotes/910overview#AppArmor").

I'm not using Lucid, but I can confirm that disabling the apparmor profile seems to improve Flash performance in Firefox (equal to Epiphany) and eliminates flicker on embedded Youtube videos.

---

### Post by sdowney717 on 2009-11-22
from that article, linux is not ready yet
:frown:
> Huge Improvements under OS X

The release notes for the Flash 10.1 preview say the following about cross-platform hardware accelerated H.264 decoding support:

    In Flash Player 10.1, H.264 hardware acceleration is not supported under Linux and Mac OS. Linux currently lacks a developed standard API that supports H.264 hardware video decoding, and Mac OS X does not expose access to the required APIs. We will continue to evaluate adding the feature to Linux and Mac OS in future releases.

Ouch. Linux isn’t ready and Apple isn’t open enough. That’s not to say that there aren’t major performance gains to be had.

---

### Post by sdowney717 on 2009-11-22
i can say that i can watch full screen hulu vids with my nvidia card 8600 perfectly on my core 2 duo e6550 overclocked to 3.4ghz and asus p5qc motherboard.
so what is lacking in software is made up by hardware. my other system single core with an mx4000 nvidia still drops frames at hulu.

---

### Post by sdowney717 on 2009-11-22
the installer for me does not work, i had to manually copy the file
first do a search for libflashplayer.so

then copy the new libflashplayer.so over the old one in usr/lib/flashplugin-installer folder.
the link in ubufox is automatically updated

---

### Post by Locke_99GS on 2009-11-22
I've been using 10.1 on Karmic 32bit for a few days now, (nVidia 9500gt, 185.18.36) and have made a couple observations. I know that supposedly they did not add much for *Linux specific* optimisations. 

Pros: 
Full screen flash playback is smooth and flawless, even HQ.
Flash controls function and are smooth.
Flawless (properly synced) audio.

Cons:
Roughly 20% of the time, moving away from a flash page (even to another) will crash Firefox 3.5 after playing a flash video.

Previously, Flash 10.0.32.18 from the repo's was 100% stable for me, but fullscreen flash was jittery.

---

### Post by victorche on 2009-11-23
> **philinux said:**
> Waiting for the 64 bit version to test drive. However regarding current performance I get much smoother full screen flash if I switch the cpu governor to conservative or performance rather than the default ondemand.

nVidia 8600GT.

Am I wrong or there is already a 64 bit version of flash?

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by Merk42 on 2009-11-23
> **victorche said:**
> Am I wrong or there is already a 64 bit version of flash?

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

That's 10.0, not 10.1

---

### Post by victorche on 2009-11-23
> **Merk42 said:**
> That's 10.0, not 10.1

Oh, sorry then... my mistake :oops:

---

### Post by sdowney717 on 2009-11-24
> Cons:
Roughly 20% of the time, moving away from a flash page (even to another) will crash Firefox 3.5 after playing a flash video.

yes it is worse than that for me. I was just viewing a flash on the bbc site and it makes firefox crash everytime i click another video after running one video.
Also, the flash screen flickers when moving the scroll bar and the picture on the flash screen turns tan.

This is definitely not going to work yet, so dont bother trying it.

---

### Post by alexfish on 2009-11-24
got flash player 10  runs reasonable on usb broardband
  so can't say if this is a problem
   
    vlc runs no problem / had tweak pulse from pulseaudio device chooser / and vlc 
   
     
   possibly the the best debug can be done with vlc

   may give clues   so sticking with 10

---

### Post by alexfish on 2009-11-24
hear is a screen shot 
   
 please don't scream it's not flash
    
  I am only looking for a solve because the two may have the same problem

added link of screen shot / iplayer and flash 10

[http://ubuntuforums.org/showthread.php?t=1326072&page=3](http://ubuntuforums.org/showthread.php?t=1326072&page=3)

---

### Post by 23meg on 2009-11-27
> **psyke83 said:**
> Try disabling the apparmor profile for Firefox. I assume the same instructions for Karmic [should work]("http://www.ubuntu.com/getubuntu/releasenotes/910overview#AppArmor").

I'm not using Lucid, but I can confirm that disabling the apparmor profile seems to improve Flash performance in Firefox (equal to Epiphany) and eliminates flicker on embedded Youtube videos.

The AppArmor profile for Firefox is disabled by default in Karmic.

---

### Post by psyke83 on 2009-11-28
> **23meg said:**
> The AppArmor profile for Firefox is disabled by default in Karmic.

I'm aware of that - one of the first steps I took after installation was to enable the profile manually, using the instructions outlined in the release notes.

Flash 10 has a [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/451146") in which hardware acceleration (needed to be force-enabled for non-NVIDIA cards) will cause a segmentation fault. With the standalone Flash player, the segmentation fault occurs. Within Firefox, there is no segmentation fault with the AppArmor profile enabled; with the AppArmor profile disabled, the segmentation fault occurs.

Additionally, embedded videos will flicker when the AppArmor profile is enabled, and do not flicker when the profile is disabled.

My conclusion: AppArmor interferes with or prohibits OpenGL/DRI in the Flash plugin. That may explain why Flash is slower in Firefox than in Empathy, and I also suspect the flickering on embedded videos is related to this problem.

Does Lucid's Firefox ship with its AppArmor profile enabled by default? That's worth investigating, IMHO.

---

### Post by nickleus on 2009-11-30
> **victorche said:**
> Am I wrong or there is already a 64 bit version of flash?

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
thanks victorche, i updated the [ubuntu amd64 firefox plugins documentation]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins")
it was previously pointing to a page with only 32 bit versions.
[]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins")

---

### Post by alexfish on 2009-11-30
did this post yesterday RE:BBC iplayer 

 : noted the version
 working from live cd
for @sillysod
Hi
just done a run with bbci player with the live cd every thing went well 
until found out I have insufficient band width / done tests through the bbc i player

mobile broadband + bad weather / internet speed / 

worth checking on wireless connections as well

although I have everything working at home 


added extract




may be for somepeople who have problems with iplayer / firefox the above might be the best option, there are threads about this

have you noted what @ myklmar has posted

looked in repos and showed flash player 10.0.32.18-1

added
Since Ubuntu 9.10 (Karmic), AppArmor ships with a profile for Firefox which is disabled by default. 
 You can enable it using the following command: 
 sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5

---

### Post by alexfish on 2009-11-30
Just received this post

RE: Flash player 10

dansar99
5 Cups of Ubuntu

 
Join Date: Jun 2009
Location: Lavergne,TN USA
Beans: 32
Ubuntu 9.10 Karmic Koala
Re: streaming radio buffers every few minutes
This is the response I got from ENTERCOM.

ur customer support team personnel has replied to your support request 

Thanks for your email,

The Linux OS is not officially supported at the moment. Try uninstalling and 
reinstalling the Flash Media player component from the latest build available 
for your Linux distribution.

Regards,
Streamtheworld Support


We hope this response has sufficiently answered your questions. If not, please 
do not send another email. Instead, reply to this email or login to your account 
for a complete archive of all your support request and responses.
__________________
HP Pavilion 750n 1.6 ghz RAM 1g

---

### Post by peterbuldge on 2009-12-23
video is heavily distorted with this

---

