---
title: "Lucid reboots by itself"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2010-04-09
Bonjour, 

For the past 12 hours my Lucid beta 2 (fully updated) desktop just reboots every so often, 3 times in the past hour.

Is anybody else experiencing this?

Regards

---

### Post by RJARRRPCGP on 2010-04-09
No, I have never encountered an automatic reboot! 

Can a kernel panic even reboot the PC like a Windows NT-based stop error routine can?

The NT kernel (at least Windows 2000 and later) has code to auto reboot if a stop error occurs. I never heard of a reboot, because of a kernel panic, lol.

---

### Post by Uncle Spellbinder on 2010-04-09
Not having that issue here, either. I've never heard of such a thing. Odd.

---

### Post by Yahoé on 2010-04-09
I'm surfing with Firefox, doing some file management, listening to FLAC files with Totem, the music starts looping, then I loose the whole system.... Weird

---

### Post by -humanaut- on 2010-04-09
Mines been running fairly stable since 530ish(Mnt time) this morning.

---

### Post by sports fan Matt on 2010-04-09
What exactly occurs when it reboots? Does it come back to a login screen, black screen?

No issues here as well.

---

### Post by dino99 on 2010-04-09
> **Yahoé said:**
> I'm surfing with Firefox, doing some file management, listening to FLAC files with Totem, the music starts looping, then I loose the whole system.... Weird

is your system overclocked ?
look at bios settings

---

### Post by -humanaut- on 2010-04-09
> **dino99 said:**
> is your system overclocked ?
look at bios settings

Thats a good idea to check. When I had my board overclocked it was a nightmare in Xubuntu

---

### Post by Yahoé on 2010-04-09
Just lost it again.

My system hardware has not changed since new, and it is 12 months old. As mentioned before this all started this am (20:07 here). Will boot to Windows 7 to see if I encounter the same issue there, then it would be hardware related.

---

### Post by mörgæs on 2010-04-09
A few months ago while experimenting with an Nvidia driver on very old hardware I had crash-and-reboots. The machine only ran minutes before rebooting. This has most likely been version 8.10 or 9.04.

Since there has been some trouble reported in the 10.04 forum recently I have not updated my 10.04 machines, and they are still stable.

---

### Post by Yahoé on 2010-04-10
I ran my PC on Windows for the past 6 hours and it never crashed on me.

So I still don't know what's happening...

---

### Post by Yahoé on 2010-04-10
More details.
Experienced the same issue again after 40mn under Lucid Beta 2.

The system does not actually reboots. The screen goes blank (but not in suspend mode), the mouse and keyboard don't work anymore and the music played loops for about 3 seconds. Then the music stops, and the system keeps on running like that. When I hit the reboot key on the chassis then the system stops !!! Again this is not experienced under Windows 7 so hardware does not seem to be the source.

---

### Post by splicerr on 2010-04-10
> **Yahoé said:**
> More details.
Experienced the same issue again after 40mn under Lucid Beta 2.

The system does not actually reboots. The screen goes blank (but not in suspend mode), the mouse and keyboard don't work anymore and the music played loops for about 3 seconds. Then the music stops, and the system keeps on running like that. When I hit the reboot key on the chassis then the system stops !!! Again this is not experienced under Windows 7 so hardware does not seem to be the source.

Well, you haven't told anything about what hardware you are using. Could be some kind of graphic driver related problem.

---

### Post by SevenMachines on 2010-04-10
probably not the problem, but always worth a check, is swap properly available?
$free

---

### Post by Yahoé on 2010-04-10
Hardware is:

AMD Quad-Core 2200 mHz
MB Asus M3N78-EM Bios AMI 0710
ATI Radeon HD 4600 Series Device ID 9490

Something new. when booting, within about 4 seconds of having GDM up, mouse and keyboard stop responding.

Again Windows 7 not affected and I'm no writing this from a USB bootable Lucid 10.4 Beta 2 with no keyboard or mouse issue.

---

### Post by Tompalaz on 2010-04-10
actually, I wouldn't rule out this as a hardware issue.
It might work in Windows, but linux can be more sensitive and the other way around. 

Could you test:
1) Memtest, let it run a few times (couple of hours)
2) Try lucid B2 with a live-cd
You could try to post your log here aswell, I'm not good at reading them but someone else might.

---

### Post by fluteflute on 2010-04-10
> The screen goes blank (but not in suspend mode), the mouse and keyboard don't work anymore and the music played loop

This has happened to me three times this morning, since the latest (quite big) batch of updates. 

Hardware: Intel Core 2 6600 and ATI Radeon HD 4350 Series

---

### Post by shindou01 on 2010-04-10
Just finished updating (the huge batch of updates), restarting as soon as my downloads are completed...I'll check back later whether it happens to me or not.....

Edit : I'm fine, no glitch....I'm on a Compaq CQ40-401AU laptop with AMD Turion X2, along with ati radeon 3200hd integrated, and 2 GB of ram, double booting with W7 and Lucid Lynx Beta....maybe the issue is not related to graphics accelerator cards?

---

### Post by fluteflute on 2010-04-10
Just has this crash again :(
Nothing I can see in logs, so I don't think theres any useful information for a bug report

---

### Post by splicerr on 2010-04-10
> **fluteflute said:**
> Just has this crash again :(
Nothing I can see in logs, so I don't think theres any useful information for a bug report

Is this with the proprietary drivers aka fglrx or with the default open source radeon drivers?

---

### Post by fluteflute on 2010-04-10
Yes with proprietary drivers. And I notice "fglrx-modaliases" was updated today.

---

### Post by splicerr on 2010-04-10
Well if you remove them and fall back to the open source drivers and the crashes are gone we know where the problems is. In any case the open source drivers should be good enough for basic dekstop usage including compiz if you want.

---

### Post by fluteflute on 2010-04-10
The difficulty is the randomness of these crashes. They are by no means reproduceable. I will stay on the proprietary driver until I get another crash.

I must have had some reason to enable the proprietary drivers in the first place... but we will see :)

---

### Post by fluteflute on 2010-04-10
Got another crash. But apparently I am using the open source drivers! Didn't realise that... so I'm switching on the proprietary ones to see if it makes a difference.

---

### Post by andrewfn on 2010-04-11
I am getting the same problem (GDM crash and back to logon screen) on two different laptops. Both thinkpads, an X61 and R61. Sometimes I am in firefox, but not always. Sometimes I am not using the computer, but it is just open on a page. My guess it is related to the video driver.

---

### Post by fluteflute on 2010-04-12
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/561373](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/561373)

---

### Post by Yahoé on 2010-04-12
We now know a bug reported has been open and confirmed.

---

### Post by fluteflute on 2010-04-18
Just for anyone interested there is a 2nd bug report now: [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)

---

### Post by jkxx on 2010-04-18
Just to chime in, your problems are probably the result of a graphics driver (see the earlier posts in this thread too).

*The latest Nvidia driver is the first to actually run stable in *Ubuntu for me (8800 GTS gfx). Previously my system would hang every so often because of the Nvidia driver. This still happens even with the latest driver in FreeBSD.

I'm not familiar with the stability of ATI drivers but apparently they aren't very good. For anyone having a similar problem, make sure to post your system specs, especially the graphics card.

Oh and disable any overclocking if you want a stable system.

---

### Post by Yahoé on 2010-04-20
Bonjour,

I keep experiencing these crashes very frequently, 4 times in the past 2 hours. I do not use the proprietary ATI drivers and my Lucid is up to date.
Is there any logs I could check and post to have a better idea of what's happening. RC is just 2 days away, this is anoying.

---

### Post by BrokeMahPC on 2010-04-20
It's the open source ATI driver that does not work well with your HD card - activate the proprietary FGLRX driver
I posted some info on that for someone else here at post #6:
[http://ubuntuforums.org/showthread.php?t=1433254](http://ubuntuforums.org/showthread.php?t=1433254)

I read somewhere that using the open source driver would fix the ugly plymouth - I tried it for 24 hours and experienced overheating and crashes exactly as you describe. Since then I've read a few threads and guides, which state that for the newer cards we must use FGLRX.
I have an ATI Radeon HD4670 - no problems with FGLRX apart from ugly Plymouth.

(PS next time you crash it might be best to shutdown the system properly if possible. Try Alt F1 (F2-F8 as well) to get to a tty console and try 
```
sudo reboot
```
```
sudo halt
```
```
sudo shutdown -h now
```

you may have to login with user name then password.)

---

### Post by Yahoé on 2010-04-20
Bryce Harrington, the Ubuntu Xorg Maintainer would like the users experiencing this to download to 1:6.12.192-2ubuntu2 to see if that version is stable.
Could anyone guide me into doint just that.

Thanks.

---

### Post by BrokeMahPC on 2010-04-20
Are you sure that's recent info?
We are already up to 1:6.13.0-1ubuntu5 - check your version in Synaptic Package Manager. 
type: xserver-xorg-video-ati in the quick search window
Have you updated?

It's still not stable for me - did you try the proprietary driver? I know many have issues with non-free software but it might be best to use it till a fix is found. No good cooking your hardware waiting for them to fix this?

---

### Post by Yahoé on 2010-04-20
Bug #565790

[Bryce  Harrington]("https://launchpad.net/%7Ebryceharrington")             wrote             3 hours ago:                                                             [  #14]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790/comments/14")                                                        If it is correct that this regression  started April 10th, that roughly coincides to when we brought in the  6.13.0 version of -ati.
 It would be helpful of those of you able to reproduce this problem  could downgrade to version 1:6.12.192-2ubuntu2 and verify the issue goes  away.  If it does not go away, then the bug is not likely to be in  xserver-xorg-video-ati.  After that, the next thing to check  would be to boot an earlier kernel from before April 10th and see if  that makes the issue go away.
 In either case, I think this bug report should be sent upstream, as  the changes we've added to ubuntu are almost entirely cherrypicks from  upstream, so this is probably relevant to them.


[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)



So yes this is very recent info. and the Bryce is the Ubuntu Xorg maintainer.


I'm still not sure how to downgrade my Xserver to a previous version. Still requiring help please.

---

### Post by wkulecz on 2010-04-21
Had one this morning.  10.04Beta1 with frequent aptitude update; aptitude safe-upgrade done.  Most recent this morning which said I was current.

System was idle and I was not looking at it, I only knew it happened because I heard the login sound after the spontaneous shutdown (or crash to reboot) and reboot happened.

No clue here that can help.  All I can do is dual boot into 8.04 or 6.06 and see if its perhaps a hardware problem, the power supply died on this box a month ago or so, I guess it could be infant mortality on its replacement.

Edit:
I'm using Nvidia proprietary drivers, which other than this random crash to reboot issue and annoyingly slow DNS resolution, seem to otherwise work very well.

---

### Post by wkulecz on 2010-04-21
> **wkulecz said:**
> Had one this morning.  10.04Beta1 with frequent aptitude update; aptitude safe-upgrade done.  Most recent this morning which said I was current.

System was idle and I was not looking at it, I only knew it happened because I heard the login sound after the spontaneous shutdown (or crash to reboot) and reboot happened.

No clue here that can help.  All I can do is dual boot into 8.04 or 6.06 and see if its perhaps a hardware problem, the power supply died on this box a month ago or so, I guess it could be infant mortality on its replacement.

Edit:
I'm using Nvidia proprietary drivers, which other than this random crash to reboot issue and annoyingly slow DNS resolution, seem to otherwise work very well.

Edit2:
I've rebooted into 8.04, if it crashes I'll follow-up, but I suspect it won't.  I can leave it running until Friday afternoon which will be longer than 10.04Beta has gone without a spontaneous crash/reboot.

---

### Post by wkulecz on 2010-04-23
Follow up.

Ran Ubuntu 8.04 on this box for over two days with no crash, so unlikely to be a hardware issue.

Booted back into Lucid to send this, will catch up on updates and see if things improve, but I'm going on vacation tomorrow and won't be back until after 10.04 is released.

---

### Post by NoVista on 2010-04-23
Had issue like yours, was caused by glx being version 1.4, using the open source driver.
They just regressed back to GLX version 1.2.
And now I am completely stable.

---

