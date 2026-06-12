---
title: "When will ubuntu Lucid 10.04 support Intel GMA500 &quot;Poulsbo&quot; video hardware?"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by spooter on 2010-04-13
When will ubuntu Lucid 10.04 support Intel GMA500 "Poulsbo" video hardware?

I always like moving to the lastest release when available but as my netbook uses Intel GMA500 video i'm stuck until support is added.

Any ideas?

---

### Post by m0dcm on 2010-04-14
> **spooter said:**
> When will ubuntu Lucid 10.04 support Intel GMA500 "Poulsbo" video hardware?

I always like moving to the lastest release when available but as my netbook uses Intel GMA500 video i'm stuck until support is added.

Any ideas?

Erm, from what I've read Canonical aren't going to support us Netbook users with the Intel GMA500 Chipsets! It seems that we're left with 2 options, either find another distro that will support Netbooks, or go back to Windows, the latter one I won't be doing.
What I cannot understand is that Jolicloud actually has GMA500 support straight out the box, and video accelleration is there too, but Canonical just want seem to be more bothered about where the buttons are going and other Graphics Cards eg Nvidia and ATI!

Come on Canonical, put the Poulsbo support into Lucid Lynx, so we Netbook owners with the very under rated GMA500 chipset can use the new release!!!

---

### Post by PatrickVogeli on 2010-04-14
don't blame Cannonical for Intel's fault!

Currently the GMA500 driver is a mess, it is buggy as hell and lacks support from both the vendors (starting with intel) and the manufacturer (PowerVR I think).

It's not that Canonical doesn't support netbooks, since they do. But having a GMA500 graphics netbook.. you just bought the wrong thing for running linux in it.

---

### Post by m0dcm on 2010-04-14
> **PatrickVogeli said:**
> don't blame Cannonical for Intel's fault!

Currently the GMA500 driver is a mess, it is buggy as hell and lacks support from both the vendors (starting with intel) and the manufacturer (PowerVR I think).

It's not that Canonical doesn't support netbooks, since they do. But having a GMA500 graphics netbook.. you just bought the wrong thing for running linux in it.

But why is it that Jolicloud has the GMA500 working? What are they doing on the Ubuntu backbone that Canonical aren't??
I'll be keeping 9.10 on my Acer Aspire One ZA3 till April 2011, then it's either Linux or nowt!
Intel are passing the buck onto the Distributors saying that it's up to them to sort it out, I know as I wrote something on the Intel Forums and got a not so nice comment back.

---

### Post by PatrickVogeli on 2010-04-14
ubuntu is focused to very wide range of machines and aims to be high quality software. That means that it can't add certain drivers because they not mature or it won't do some dirty hacks because.. they're dirty. It may well be that, in order to include the poulsbo driver, they'd need to stick with an older X Server and/or kernel or whatever.. that may be fine for gma500 users but not for the rest.

Jolycloud is, basically, only targeted to netbook users, so it's ok for them to do stuff to make the gma500, since a large amount of netbooks use that.

---

### Post by mikewhatever on 2010-04-14
> **m0dcm said:**
> But why is it that Jolicloud has the GMA500 working? What are they doing on the Ubuntu backbone that Canonical aren't??
I'll be keeping 9.10 on my Acer Aspire One ZA3 till April 2011, then it's either Linux or nowt!
Intel are passing the buck onto the Distributors saying that it's up to them to sort it out, I know as I wrote something on the Intel Forums and got a not so nice comment back.

Jolicloud is not Lucid Lynx. OK?
Ubuntu does work with gma500 (Hardy, Intrepid, Jaunty, Karmic).
The major difference is that Lucid has xserver version 1.7.x, whereas Jolicloud has 1.6.x. Now, Lucid devs could have said, "Let's keep an older version of xserver just for those with gma500 for ever", but, I guess, the show must go on. Much has been written about it, and you may want to use Google and read a bit before posting, but, in a nut shell, Intel refuses to support its hardware on Linux by not updating the driver to work with newer xservers. At the moment, I don't know of any distro that supports gma500 and xserver 1.7.x. Silly as it is, you just through stones into the wrong yard.

---

### Post by m0dcm on 2010-04-15
> **mikewhatever said:**
> Jolicloud is not Lucid Lynx. OK?
Ubuntu does work with gma500 (Hardy, Intrepid, Jaunty, Karmic).
The major difference is that Lucid has xserver version 1.7.x, whereas Jolicloud has 1.6.x. Now, Lucid devs could have said, "Let's keep an older version of xserver just for those with gma500 for ever", but, I guess, the show must go on. Much has been written about it, and you may want to use Google and read a bit before posting, but, in a nut shell, Intel refuses to support its hardware on Linux by not updating the driver to work with newer xservers. At the moment, I don't know of any distro that supports gma500 and xserver 1.7.x. Silly as it is, you just through stones into the wrong yard.

So basically, the IEGD driver Intel have released is a no no? and after April 2011 Netbooks that run the Intel GMA500 chipset are basically no good?
So disabled users like myself, who cannot afford new PC's, have got to go back to Windows?
Sorry for my rantings, I used to be a IT Support Tech, and love to use the latest Operating Systems, and I had this Netbook for Christmas, thanks to my inlaws, and till January I was a brainwashed Billy "Bob" Gates user, till I was told about Linux, and I've never looked back, till I learnt about the GMA500. I've got it running ok under Ubuntu 9.10, but I just cannot get it to run fullscreen video's.
This will be my last post on this issue, and I'll think hard about putting Windows back on this Netbook, and no more Linux for me.....

---

### Post by mastablasta on 2010-04-15
Windows has longer support periods than Linux (XP until 2014 i think). In fact some are so long that by the time you get to the end the computer is probably obsolete anyway... (for example XP will have 13 years of support, while 98 had 8 years support). 
and even then it could be possible to get various drivers and backwards compatibility. so not all is bad in Windows.

---

### Post by cgriffith on 2010-04-15
@[m0dcm]("http://ubuntuforums.org/member.php?u=1054054")

I really get pissed when I see blind comments like the ones you have made come across the wires.  "Well Jollicloud is working, why can't Ubuntu".  This shows that you really have no idea what your talking about.  Maybe you should a little more research before throwing out a blanket statement like that.

The reason why Jollicloud works is because it uses xserver 1.6.  The reason why Lucid does not work (yet all previous version do) with the psb drivers is because it uses xserver 1.7.  So yes Jollicloud works, but what is it gonna do when Lucid comes out(in case you were not smart enough to figure it out, Jollicloud is based off of Ubuntu).  What you really need to do is focus your frustration at intel and ask them to provide updates to the psb or iegd drivers.

On a separate note, 9.10 works perfectly for HD video (except using flashplayer).  Do some research on the work that many very talented people in this community have done for you.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by snowpine on 2010-04-15
The current Ubuntu Long Term Support release, 8.04 Hardy Heron, works with GMA500 and will be fully supported by Canonical through April 2011. I am cautiously optimistic that a solution to the "Poulsbo Conundrum" will be found by then. :) Also remember that Lucid is still in Beta; don't judge it until it is actually released. If Canonical doesn't officially support it, maybe the community will come up with a good workaround (like they always have in the past). ;)

Ubuntu is a fast-moving distribution with an emphasis on the latest desktop features (like Xorg). It would be unfair to expect Canonical to hold back this important feature to cover for Intel's mistake. There are many Linux distributions with an emphasis on stability that will be supporting older Xorg versions for quite some time (Red Hat, CentOS, Debian, etc.) if Ubuntu is too "bleeding edge" for your taste.

---

### Post by mikewhatever on 2010-04-15
So far, community members have been very helpful in figuring out how to make gma500 work on post Hardy Heron versions of Ubuntu.
[Someone claims]("http://www.nanoant.com/linux/compiling-kernel-iegd-10x-module-for-any-linux-distribution/comment-page-2"), that IEGD can be made work too.

---

### Post by Anfanglir on 2010-04-17
> **snowpine said:**
> The current Ubuntu Long Term Support release, 8.04 Hardy Heron, works with GMA500 

Really? I know that Dell released a modified 8.04 that was preinstalled on dells with GMA500, but that release is not available for other brands. My experience is that the regular (Canonical's) 8.04 LTS do not work well with GMA500. Later versions (9.04 annd 9.10) mostly work after some tweaking.

/ Anfanglir

---

### Post by snowpine on 2010-04-17
> **Anfanglir said:**
> Really? I know that Dell released a modified 8.04 that was preinstalled on dells with GMA500, but that release is not available for other brands. My experience is that the regular (Canonical's) 8.04 LTS do not work well with GMA500. Later versions (9.04 annd 9.10) mostly work after some tweaking.

/ Anfanglir

My mistake; I do not have GMA500 personally and was repeating something I read elsewhere. :)

---

### Post by descendent87 on 2010-04-17
Theres a bug report [here](https://bugs.launchpad.net/ubuntu/+bug/553898)
At the moment you can either go back to an older version of ubuntu or use mandriva 2010 or 2010.1 (currently in beta) which both support GMA500 out the box

---

### Post by Anfanglir on 2010-04-18
> **descendent87 said:**
> At the moment you can either go back to an older version of ubuntu or use mandriva 2010 or 2010.1 (currently in beta) which both support GMA500 out the box

I tried Mandriva 2010 for a while, it is true that GMA500 is supported on install, however, once you update mandriva you loose video support and is stuck at a command line. 

Found out how to solve this ([http://forum.mandriva.com/viewtopic.php?p=792054#792054](http://forum.mandriva.com/viewtopic.php?p=792054#792054)), but as the same issue will appear on every kernel update it is something of a showstopper. Also suspend/resume do not work. Maybe these issues will be solved in 2010.1 but I'm not betting on it.

/ Anfanglir

---

### Post by lucazade on 2010-04-18
xserver downgrade to run intel IEGD drivers:

[http://silicone.homelinux.org/2010/04/11/building-xserver-1-6-for-xorg-7-5/](http://silicone.homelinux.org/2010/04/11/building-xserver-1-6-for-xorg-7-5/)

haven't tried yet.

---

### Post by Eclipse. on 2010-04-19
I really feel sorry for people on GMA500 but there is really nothing that can be done. GMA500 wasn't made by Intel, instead they got another company to make it for them, PowerVR. Since this chip is different from every other Intel product the usual Intel drivers don't work, we need the drivers from PowerVR. 

Every time we upgrade Xorg, we need an update for the driver.Sometimes this can be an issue for Nvidia users at the start of development cycles before they push out a new driver, however since Nvidia actively supports Linux we normally get an update long before the final release. With GMA500 its a different story and have no idea when a new driver will be made available. Until that point there is nothing anybody can do apart from downgrade Xorg, or use an old release.

---

### Post by lucazade on 2010-04-19
> **Eclipse. said:**
> I really feel sorry for people on GMA500 but there is really nothing that can be done.
Not true...
Intel will port IEGD to xserver 1.7/1.8 because of Meego

---

### Post by mikewhatever on 2010-04-19
> **Eclipse. said:**
> I really feel sorry for people on GMA500 but there is really nothing that can be done. GMA500 wasn't made by Intel, instead they got another company to make it for them, PowerVR....

Nothing can be done?! Where do you get these ideas? Can you explain why the latest gma500 driver for W7 is dated 16 March 2010.

---

### Post by Eclipse. on 2010-04-19
> **lucazade said:**
> Not true...
Intel will port IEGD to xserver 1.7/1.8 because of Meego

Well currently speaking.

> 
Nothing can be done?! Where do you get these ideas? Can you explain why  the latest gma500 driver for W7 is dated 16 March 2010.     
Windows is actively maintained where as on Linux its not.What people are basically asking the equivalent of is for Microsoft to make drivers for Windows.It just doesnt work that way.

See here for more information, [http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ)

---

### Post by brauliobo on 2010-04-19
maybe we should protest more!!

The intel community forums is a good place.
[http://community.edc.intel.com](http://community.edc.intel.com)
iegd linux search:
[http://community.edc.intel.com/t5/forums/searchpage/tab/message?q=iegd+linux#message-list](http://community.edc.intel.com/t5/forums/searchpage/tab/message?q=iegd+linux#message-list)

people is already claming support on newer linux:
[http://community.edc.intel.com/t5/Software-Tools-Discussions/Fedora-12-Support-in-IEGD/m-p/2143](http://community.edc.intel.com/t5/Software-Tools-Discussions/Fedora-12-Support-in-IEGD/m-p/2143)

Intel Poulsbo (GMA500) Dissatisfaction Group
[http://www.facebook.com/home.php?#!/group.php?gid=62711517402&ref=ts](http://www.facebook.com/home.php?#!/group.php?gid=62711517402&ref=ts)

---

### Post by Leed on 2010-04-20
In general I don't care if there ever will be a proper driver for my gma500, I don't mind if I have to install some Backports and reconfigure some settings after each upgrade, I don't even care if I have somehow manipulate a windows driver to get the psb running in lucid. 

It doesn't have to be out of the box, it doesn't have to be official, It can be dirty code just as before. I would just really appreciate some solution for the psb problem. Since I got Lucid on my T91 I simply love it, but that little extra of having any crappy form of the driver working would simply make my day.

---

### Post by Artemis3 on 2010-04-20
Because its proprietary and undocumented hardware, you have to complain the hardware manufacturer (Intel/PowerVR) for it. IMO this video chip should be avoided like the plague.

---

### Post by Leed on 2010-04-22
I think everybody looking for a solution is aware of the proprietary driver problem that PowerVR has caused.

It's just, as a Linux user I believe nothing is impossible. I mean there is some windows driver, why can't we somehow port it to linux, just as we used to with the windows wireless drivers in the old days. Doesn't have to be perfect, just a temporary solution.

---

### Post by beastrace91 on 2010-04-23
> **Leed said:**
> I think everybody looking for a solution is aware of the proprietary driver problem that PowerVR has caused.

It's just, as a Linux user I believe nothing is impossible. I mean there is some windows driver, why can't we somehow port it to linux, just as we used to with the windows wireless drivers in the old days. Doesn't have to be perfect, just a temporary solution.

Yep. Personally I don't even need 3D support, I just want my 1024x600 resolution :-/

~Jeff

---

### Post by Ibidem on 2010-04-24
> **beastrace91 said:**
> Yep. Personally I don't even need 3D support, I just want my 1024x600 resolution :-/

~Jeff
If the resolution is all you want, I accidentally found out that 915resolution has been ported to grub2...
Not using the GMA500 myself, I haven't needed or used it, but Ubuntu ships that (/boot/grub/915resolution.mod).  
If you know how to use 915resolution, you're halfway there; add the line "insmod 915resolution" and the appropriate command before the "linux ..." line.
Arch and Gentoo forums have some decent guides on it.

---

### Post by tsip4 on 2010-04-24
Without having tested lucid yet I believe 915resolution hack wont make it work. From what I have read the poulsbo chipset cannot support any gui because xserver 1.7.0 is incompatible with old poulsbo drivers.

---

### Post by descendent87 on 2010-04-24
It can support GUI's but just slowly and usually at the wrong resolution

---

### Post by Anfanglir on 2010-04-26
I have given up hoping for a resolution of the poulsbo-mess for Lucid, and have just ordered a copy of Win7 for my Fujitsu u820. I really need to have graphic accelleration and suspend/resume working without hitches. Switching hardware is not an option for me since no other UMPC offers the same small-size/convertible-format/touchscreen/GPS as the Fujitsu u820.

I'm sticking with Ubuntu on my other notebook (Toshiba Libretto U100) and on the desktops.

:\ Anfanglir

---

### Post by lucazade on 2010-04-26
"The wonderful Olivier Blin of Mandriva has come through with his patches for making the psb video driver for Poulsbo (GMA 500) chipsets work on newer versions of X.org. He reports success – including 3D – with X server 1.7."

[http://www.happyassassin.net/2010/04/26/poulsbo-packages-for-f12-f13-may-be-incoming/](http://www.happyassassin.net/2010/04/26/poulsbo-packages-for-f12-f13-may-be-incoming/)

Keep fingers crossed!

---

### Post by Anfanglir on 2010-04-26
Hey that's good news! Guess I'll be keeping a Linux partition on the u820 after all.

EDIT: here's a link to Blino's blog post on the topic:
[http://blino.org/blog/mandriva/poulsbo-xserver1.7.html](http://blino.org/blog/mandriva/poulsbo-xserver1.7.html)
Apparently the fixed drivers are already available in Mandriva Cooker, may try it the coming days :p
END EDIT

/ Anfanglir

---

### Post by Eclipse. on 2010-04-26
Awesome news :) Expect to see ppa's soon then.

---

### Post by lucazade on 2010-04-27
[Xorg PSB patched by Blino and packaged by me (DEB)]("http://dl.dropbox.com/u/1338581/Gma500/deb/xserver-xorg-video-psb_0.31.0-0ubuntu2%7E1004_i386.deb")

Haven't tried it yet.. let me know if ok!

```
wget http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh && sh ./poulsbo_lucid.sh
```

---

### Post by Anfanglir on 2010-04-27
Hi,
tried running the script on a live usb-stick install of Lucid. For the most part the script seemed to execute OK but it gave me an error at the end, something about wmlinuz - may be related to that it is a live install.

On restart I get a error message and is left with low graphic mode, running dpkg reconfigure psb-kernel-source do not resolve the issue.

/ Anfanglir

---

### Post by lucazade on 2010-04-27
> **Anfanglir said:**
> Hi,
tried running the script on a live usb-stick install of Lucid. For the most part the script seemed to execute OK but it gave me an error at the end, something about wmlinuz - may be related to that it is a live install.

On restart I get a error message and is left with low graphic mode, running dpkg reconfigure psb-kernel-source do not resolve the issue.

/ Anfanglir

You should try it on a phisical installation of lucid (not live usb) because the kernel module should be compiled and started at reboot.

I'll test my self as soon as i get back my netbook.

---

### Post by Anfanglir on 2010-04-27
Yea I guess. I was considering waiting for the official release of Lucid on the 29 before switching from Karmic to Lucid, but I might as well upgrade to the Release Candidate to test this. Need to backup some files first though.

/ A

---

### Post by jr3us on 2010-04-27
I did an install on an acer 751h, however i didn't pay enough attention to the need to use acer as an argument to the install shell.

long story short, i tried to patch around it, but it was of no use as when it now boots, it wont leave the mode where it is showing the 5 dots during initial boot screen. 

any special instructions to uninstall what i have done, and retry

regards

---

### Post by last1 on 2010-04-27
Hi, I went ahead and tried to install it on a fresh install of the lucid rc. So I ran the script..went well except for this:
setting up mplayer-skins (3)...
[: 89: unexpected operator

Anyway after that it generates the initramfs and quits, I wasn't sure at first if that error messed it up but I think so or maybe it's something else.. Either way, when I reboot I get to an X screen telling me it's running in low graphics mode, it doesn't know the devices, hardware etc and asking me what to do. I told it to reconfigure for my hardware, then rebooted, since I didn't know what else to try..it didn't work. I then told it to use a generic configuration, rebooted, that got me booted into the system with no errors, but using the installed mplayer gives me an error about loading shared libraries, can't find liblzo2.so.2 and flash doesn't seem to be present though the wiki page about the previous script mentions that it installs flash..

So..I dunno. Did it fail, or did I just leave something out?

---

### Post by Jackyboy86 on 2010-04-27
Ubuntuforums, I love you.
I love you more than chocolate, flowers and dildos.

*prances and upgrades to 10.04 on mini 10*

---

### Post by jr3us on 2010-04-27
last1,

if you dont have an aspire 751h, then the error is of no consequence based on looking at the shell.

---

### Post by last1 on 2010-04-27
Ah ok. Then I guess maybe something else needs tweaking before the script will work right, here I was hoping I could be a little more helpful as to what that something might be but I guess not.

---

### Post by markybob on 2010-04-27
> **last1 said:**
> Hi, I went ahead and tried to install it on a fresh install of the lucid rc. So I ran the script..went well except for this:
setting up mplayer-skins (3)...
[: 89: unexpected operator

Anyway after that it generates the initramfs and quits, I wasn't sure at first if that error messed it up but I think so or maybe it's something else.. Either way, when I reboot I get to an X screen telling me it's running in low graphics mode, it doesn't know the devices, hardware etc and asking me what to do. I told it to reconfigure for my hardware, then rebooted, since I didn't know what else to try..it didn't work. I then told it to use a generic configuration, rebooted, that got me booted into the system with no errors, but using the installed mplayer gives me an error about loading shared libraries, can't find liblzo2.so.2 and flash doesn't seem to be present though the wiki page about the previous script mentions that it installs flash..

So..I dunno. Did it fail, or did I just leave something out?

run it with bash, not sh, and you won't get that error.  "bash poulsbo_lucid.sh" instead of "sh poulsbo_lucid.sh"

---

### Post by lucazade on 2010-04-27
other poulsbo thread to follow:
[http://ubuntuforums.org/showthread.php?t=1229345&page=45&highlight=gma500](http://ubuntuforums.org/showthread.php?t=1229345&page=45&highlight=gma500)

---

### Post by Leed on 2010-04-28
That's great news Lucazade, hope that thing will do the trick

---

