---
title: "machine freezes at certain (random) moments"
date: 2009-12-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-06
AMD Phenom X3 9450, 3MB, ATI HD3650, Lucid-64(up-to-date).
At certain (random) moments machine freezes: Rhythmbox (it is on almost all the time) plays without interruption, but everything else is solid frozen. Only REISUB helps.
I singled out that it happens most often with FF 3.7 and with some pages with lot of Flash content. But it did happen on pages with no Flash and (I think) it happened with FF 3.6 ... Where (dmesg gets lost after reboot, or not ... ?) to look for a possible clue for this annoying problem ...?
This problem started in the middle of last week. I did not have this same machine frozen for over a year of using Ubuntu ... except when there was some evident problem with boot in testing ...

---

### Post by Gina on 2009-12-06
I too get system occasional crashes when I'm using Firefox. Without Firefox running it's rock solid using Lucid.  I get occasional problems with the system crashing with Firefox in earlier versions too but not as bad.  The 64 bit version is worse than the 32 bit.  I'm running 64bit Lucid ATM.

---

### Post by zika on 2009-12-06
> **Gina said:**
> I too get system occasional crashes when I'm using Firefox. Without Firefox running it's rock solid using Lucid.  I get occasional problems with the system crashing with Firefox in earlier versions too but not as bad.  The 64 bit version is worse than the 32 bit.  I'm running 64bit Lucid ATM.It is not polite to say but I am glad that I'm not the only one and that problem You're having is very similar. I'm trying with refraining of using FF 3.7 and 3.6 and I'm trying to force myself to use FF 3.5 just to locate culprit.
Do You have Ubuntu FireFox Modifications 0.8 enabled ...? I have in Metacity reduced resources and disabled workarounds. Now, I disabled Ubuntu FireFox Modifications to see if that helps.
This probem occurs on 2.6.32-6, 2.6.32-7 and 2.6.32-999 (with or without KMS, no.KMS is default on 2.6.32-999). So, it seems that it is not kernel related ...

---

### Post by autocrosser on 2009-12-06
I've been having randoms also--only when there is high CPU load (which is almost always due to using BOINC)---most times with Firefox 3.6 or 3.7 running. I have not pinned it down yet.......

Have you two looked at logs to find a pattern?

---

### Post by zika on 2009-12-13
I thought the problem solved by itself (by some upgrade), although I've used, mostly, Opera in the meantime, and it did not happen (as far as I can remember) while in 2.6.32-999 kernel. Then I started using 2.6.32-7 and it was OK. I went back to FF and I forgot about the problem. Today, I've installed 2.6.32-8 and problem resurfaced again. Suspiciously enough, that freeze happens mostly while I'm reading the local newspaper site that has lot of flash etc. ... I'll have to find time and will to investigate this more. Back to Opera.

---

### Post by Lyleb on 2009-12-13
Apparently, this isn't a bug or a step backwards. Ubuntu just decided to add the BSD feature to 9.10 that Windows has been so popular for. They just forgot the Blue Screen part.

---

### Post by plun on 2009-12-13
I had this problem with Adobe Flash 10.1
[http://ubuntuforums.org/showthread.php?t=1329328&highlight=flash](http://ubuntuforums.org/showthread.php?t=1329328&highlight=flash)

Went back to the Ubuntu version and freezes was gone...

---

### Post by seeker5528 on 2009-12-15
> **Lyleb said:**
> Apparently, this isn't a bug or a step backwards. Ubuntu just decided to add the BSD feature to 9.10 that Windows has been so popular for. They just forgot the Blue Screen part.

:lolflag:

I'm sure the BSD people are going to love you for mistaking them for a BSOD.:P

Later, Seeker

---

### Post by philinux on 2009-12-15
> **Gina said:**
> I too get system occasional crashes when I'm using Firefox. Without Firefox running it's rock solid using Lucid.  I get occasional problems with the system crashing with Firefox in earlier versions too but not as bad.  The 64 bit version is worse than the 32 bit.  I'm running 64bit Lucid ATM.

I'm getting FF scrolling stopping at random points and at the same time cant do anything in FF until it unfreezes. Lasts about 5 seconds. CPU load normal too. Nothing else going on and bam.

---

### Post by zika on 2010-01-11
There were no freezes lately but they resurfaced today. My main suspect is flash. It, kind of, collides with something.

---

### Post by xebian on 2010-01-11
I have the same problem lately but when I checked outside it was 2 deg F and windchill is at -20.  It must have been due to the occasional gust of cold air.  ;)

---

### Post by zika on 2010-01-11
> **xebian said:**
> I have the same problem lately but when I checked outside it was 2 deg F and windchill is at -20.  It must have been due to the occasional gust of cold air.  ;)Just keep the good spirit and even this too shall pass...

---

### Post by VMC on 2010-01-11
It would be great if you could get conky or top being run on top of all windows and when it freezes you can then single out the offending app.

---

### Post by zika on 2010-01-11
> **VMC said:**
> It would be great if you could get conky or top being run on top of all windows and when it freezes you can then single out the offending app.I thought of that but, too much other stuff to do to keep the track. I'll do that...
(Using 64-bit, 2.6.32-10 for several days, 2.6.33-999 (daily), FF 3.5, 3.6, 3.7, Chrome (daily-testing))

---

### Post by phillw on 2010-01-11
Is any one getting this in 32 bit ?

I'm still running FF 3.5.7 -- I think I'll stay put for the time being.

I'm still on  > Linux piglet 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:43:20 UTC 2009 i686 GNU/Linux

Hmm, just seen that 2.6.32.10.10 is in Synaptics Package Manager ... I'll pop it on later. Don't recall being offered it in Update Manager, but not too sure is Update Mananger offers kernel updates.

I'll give it a go later - I have usually got about 10+ tabs open in FF and watch both flash from the bbc news web site & you-tube, both run with no glitches.

Phill.

---

### Post by nanog on 2010-01-12
still getting intermittent freezes in 2.6.32-10-generic.
no associated log messages in kern.log, syslog and Xorg.0.log. TTY broked and netbook has no sys rq. 

Stumpified.

---

### Post by ranch hand on 2010-01-12
I get freezes on occasion but they all seem to be related to FF.  Do you have these more often when running a lot of tabs or several FF windows open?

---

### Post by zika on 2010-01-19
I (kind of) am getting the feeling that the problem is related to KMS+FF. If I disable KMS I can endure the whole day without a freeze. If I go into KMS I'm (almost) always ending that session in freeze. (Almost) always there is FF in equation. Music (Rhythmbox, most often) plays, but machine is frozen. If I'm fast enough Ctrl-AltSq-B is enough. It does not depend on kernel (2.6.32-9(rarely used lately, just for test), 2.6.32-10, 2.6.33-999)...

---

### Post by errigalmarten on 2010-01-21
I've been having the same issues. Looking back, it seems that any time my machine locks up, I've been using Firefox. At first I thought maybe the newer Kernal just wasn't playing nice with my hardware or something. But, I never had this issue until recently. I ran 8.10 for about a year, and no problems. When I wiped my machine because XP was bugging out on me, I went to 9.04. Ran fine for a while, and then after some updates, my machine would just lock up at random, the screen going blank and all of my system fans revving up.

Tried going back to 8.10 after 9.10 had the same issue, and after I got some updates, it began having the same problems. Not sure what the problem is, but I'm hoping it gets figured out. I suspect Firefox. I think I'll try my hand at Opera for a while and see how that goes.

Also, the issue doesn't show itself on my clunky old laptop, my Evo D500, or on my girlfriend's laptop. Though today she got some updates and now her machine gets hung up, saying it's having trouble finding her SATA controller.. Probably not related, but the only thing that got updated was Firefox as far as I know.

---

### Post by zika on 2010-01-21
I'll make the test today. I'll refrain from using FF, leave KMS on in 2.6.32-11, I've changed all options pointing to FF, in order not to forget that I'm not to use it, and we'll see. If it doesn't freeze, then it is FF. I'll use Chromium-browser 4.0.303.0 (36724) Ubuntu...

---

### Post by MacUntu on 2010-01-21
Had a freeze today (+ 100% load according to the fan noise), maybe caused/triggered by Chromium (PPA) on Facebook (Café World, don't laugh!). I turned on SSH and am now waiting for it to happen again.

---

### Post by Tompalaz on 2010-01-21
I'm affected by this as well.
For me it doesn't seem to be associated with Firefox. My machine can freeze at true random moment, like today, I used ls -l and my machine just died.

Have a fairly powerful machine, its a MacBook 5,1 gen. 
> tomas@macbook:~$ uname -r
2.6.32-11-generic


---

### Post by dino99 on 2010-01-21
i'm fighting against sound driver detection since one week now, they freeze my apps or system or froze memory.

Htop give me some info as logs don't talk about this problem:
- high cpu activity with pulseaudio, so i kill it when needed
- gnome-setting-daemon often heavily use cpu too

Seems that an alsa/pulseaudio problem.

---

### Post by zika on 2010-01-27
Yesterday my machine froze just while I was playing with screensaver,  trying some of them, mostly the simplest ones. At that moment, that was the only process of mine that was active. Not using sound, not using FF... at that particular moment. Not using KMS at that boot. Kernel at that moment was: 2.6.33-999

---

### Post by dino99 on 2010-01-27
theses problems was solved to me after using "bleachbit" as root (apps --> system --> bleachbit as root). Be carefull to use it.

---

### Post by zika on 2010-02-02
Funny thing. Today 2.6.33-999, for the first time in weeks, is with KMS by default. I, happily went my way, working, and puff, freeze came out of nowhere. Yes, there was Flash content in FF3.6... So, definitely, KMS is in the equation of freeze. I was not using KMS for days and did not have a freeze once. There is a problem when KMS is with Flash plugin (64-bit alpha)... There is a thing I might (very reluctantly) try, and that is 32-bit Flash plugin and KMS. But, that will introduce so many 32-bit libraries that I'm, probably, not going to do that... Back to "nomodeset" ... The only thing that spoils my "equation" is experience with screensaver explained above...
Any ideas, experiences, hints...?
@dino99 I do not plan to erase history and similar stuff... Sorry... In that case I'd rather reinstall... Even if I would've decided to reinstall, I suspect I would have the same problem...

---

### Post by zika on 2010-02-02
I've bit the bullet. Removed libflashplayer.so and installed flashplugin-installer with the bunch of 32-bit libraries. Of cource, once I've done that, I've put newer version (10.1 prerelease) in /usr/lib/flashplugin-installer/ so at least I'm up-to-date. We'll see, if machine freezes with this contraption then the problem is elsewhere... Runing on KMS with 32-bit flash-plugin...

---

### Post by teresaejunior on 2010-02-02
I understand you have reported not too high cpu usage, but this used to happen to my machine always because the fans were blocked. 

Try in the terminal to see sensors temperatures displayed in °C:

```
grep [0-9]* /proc/acpi/thermal_zone/*/temperature
```

---

### Post by zika on 2010-02-02
> **teresaejunior said:**
> I understand you have reported not too high cpu usage, but this used to happen to my machine always because the fans were blocked. 

Try in the terminal to see sensors temperatures displayed in °C:

```
grep [0-9]* /proc/acpi/thermal_zone/*/temperature
```I do not think that is the case in my case... Machine works without a glitch if it is booted without KMS and if it is booted with KMS, if no Flash is loaded. I thought about HW but it worksfor days without KMS+Flash no matter if it is 2.6.32 or 2.6.33 etc. Now, it survived kind of record time with KSM and Flash... So, there might be a point in not using 64-bit-alpha-plugin... We'll see... Time will tell.

---

### Post by kevron2020 on 2010-02-02
I have been having the same issues for awhile now, with FF and Chromium...  Chromium doesn't do it as often, but still does it.  Gonna try opera and see if it does it then.  I am a Linux n00b and I love it, except for the browsers freezing.  Its getting so bad I'm about to pay for Win7.

---

### Post by kevron2020 on 2010-02-02
Freezes in Opera also.  

  When typing msg's on a forum where there is no flash It'll freeze for about 20 seconds.  

Opera video in YouTube seems to freeze more than in FF or Chromium.  However the audio never stops.  FF  video freezes audio continues for about 20 Seconds then Freezes completely for about 15 seconds. Then Resumes, same with Chromium.

---

### Post by zika on 2010-02-03
For now system looks more like Linux, stable, resiliant. With KMS. I've changed some settings for Flash and I can watch 2hour video from Stanford University without freezing the system. It crashed browser twice but that's it. File in /tmp grew to 200+M and everything is OK. Looks as if I found the culprit: 64-bitFlash aplha plugin. I'll investigate more as soon I get some more spare time... Flash 10.1 looks promising... I wonder when we are going to get real 64-bit Flash plugin... In beta, at least...

**Update:** Since today's version of 2.6.33-999 is buggy and I had to go to 2.6.32-12 to fix that, I stayed in it, and, so far, it is OK too. It seems I've found the reason for freeze. Fingers crossed...

---

### Post by gfarmerfr on 2010-02-03
Hi everyone,

I've also some random freeze not related to FF. I've notice that these problem appears just after the last plymouth update. So after removing plymouth all works just fine. Hopes this help you guys. Can anyone test removing plymouth and confirm it's a plymouth related bug ?

---

### Post by darco on 2010-02-04
I just booted into Lucid and went straight to a terminal,soon as I hit the up arrow to bring up the last command, the entire system froze up. Had to hard boot, tried it again, and exact same thing happened. I reinstalled from backup (feb 1) and all is fine. I was in the system for a good 10 mins before I decided to run a safe-upgrade. 
New updates installed, rebooted and the exact same thing, froze up immediately after trying to bring up the last command in a terminal. I was in the system for less than 1 minute,

---

### Post by sirdilznik on 2010-02-04
> **gfarmerfr said:**
> Hi everyone,

I've also some random freeze not related to FF. I've notice that these problem appears just after the last plymouth update. So after removing plymouth all works just fine. Hopes this help you guys. Can anyone test removing plymouth and confirm it's a plymouth related bug ?

I had a similar problem that started since the last time I updated a day or two ago.  My system would freeze completely and require a hard reboot any time I pressed the "Enter" key anywhere (while in an app or just on the desktop) in any WM I tried (FVWM or e17).  Removing plymouth solved the problem.

I am running the "EVIL" :roll: nvidia binary blob which I installed manually.  This occurred with both 195.30 and 195.36.03.  As a curiosity after a further update installed a new version of xorg-server and put me in that weird state that sometimes happens where the kernel driver still works but the libs are no longer functional due to the xorg update and you get a functional desktop but no glx the freeze was gone.  Pressing "Enter" worked just fine but of course no glx meant no 3D games.  So I reinstalled the nvidia binary blob, libs and all, and the freeze returned.  

Again, removing plymouth did the trick.  Now pressing whatever on the keyboard works fine, with no freeze, and I have glx for games. :D

Edit:  ~$ uname -a
Linux PhenomII 2.6.32-12-generic #16-Ubuntu SMP Thu Jan 28 07:47:05 UTC 2010 x86_64 GNU/Linux

AMD Phenom II 940 x4 nVIDIA GTX260

---

### Post by zika on 2010-02-05
I've reinstalled yesterday, keeping my personal settings, history, bookmarks, shortcuts, etc., even without having separate /home partition.That is a good news. I've reinstalled because my machine became very unstable and nearly unusable, especially after grub upgrade. That was with 20100130 image. It worked very nice with that build. The moment I did upgrade it all started again. It is just a matter of minutes when it is going to crash. Yes, I've uninstalled plymouth... That helped a bit. I never had such unstable machine... Even with W$... Now I'm in 2.6.33-99-20100204... I'm keeping my fingers crossed to finish this message... We'll see. This is my 3. or 4. reinstall due to the problems with machine in several years.

---

### Post by Sephoroth on 2010-02-06
> **sirdilznik said:**
> I had a similar problem that started since the last time I updated a day or two ago.  My system would freeze completely and require a hard reboot any time I pressed the "Enter" key anywhere (while in an app or just on the desktop) in any WM I tried (FVWM or e17).  Removing plymouth solved the problem.

I am running the "EVIL" :roll: nvidia binary blob which I installed manually.  This occurred with both 195.30 and 195.36.03.  As a curiosity after a further update installed a new version of xorg-server and put me in that weird state that sometimes happens where the kernel driver still works but the libs are no longer functional due to the xorg update and you get a functional desktop but no glx the freeze was gone.  Pressing "Enter" worked just fine but of course no glx meant no 3D games.  So I reinstalled the nvidia binary blob, libs and all, and the freeze returned.  

Again, removing plymouth did the trick.  Now pressing whatever on the keyboard works fine, with no freeze, and I have glx for games. :D


Thanks.  That fixed my issue (same as yours) on a 9400M G w/ 195.30.

---

### Post by pickarooney on 2010-02-07
I'm having the exact problem described by phillinux and kevron2020. I don't know what KMS or plymouth are but I don't think I have them installed. This is a fresh Karmic install (had no such problem in Jaunty) and Firefox seems to be at the root of the problem - CPU usage regularly hits the high 90s. I've disabled java to no avail and am testing plugins one by one.

---

### Post by kevron2020 on 2010-02-08
Mine stopped freezing with one of the latest updates, Still freezes for a few seconds while watching video's online, but not randomly with or without a web browser open.

---

### Post by zika on 2010-02-08
> **pickarooney said:**
> I'm having the exact problem described by phillinux and kevron2020. I don't know what KMS or plymouth are but I don't think I have them installed. This is a fresh Karmic install (had no such problem in Jaunty) and Firefox seems to be at the root of the problem - CPU usage regularly hits the high 90s. I've disabled java to no avail and am testing plugins one by one.KMS is not a package. It is a mode. If You do not have nomodeset in Your kernel line in GRUB, You are, most probably, in KMS. I am unable to make my machine 100% freeze-free if I choose KMS. With UMS it works for hours without a freeze. Removing Plymout helped KMS a lot, so it can endure for several hours, sometimes, without a freeze. But, also, it can freeze in a minute... With or without the FF.

---

### Post by moviemaniac on 2010-02-13
I am also experiencing random freezing on my machine but I haven't been able to see a pattern yet. I've seen the machine freeze seconds to minutes after shutting down a machine in Virtualbox to logging out of KDE or when pasting text in my web browser (Opera). I'm on 64bit with opensource ATI drivers and KMS enabled. When the machine freezes - it happens 2-4 times a week - it doesn't come back and I have to shut it down with the power switch lacking a reset button.

---

### Post by zika on 2010-03-05
I was just inclined to write that freezes stopped and that I can use KMS, machine worked for two days, from morning until midnight without freeze, and, yesterday evening and today freezes are back. They do not happen without KMS, machine could run for weeks. So, it is not the result of plymouth or drivers... I, even, disabled dynclks for ATI and... no change, KMS is the common factor in all freezes. Flash or not, it doesn't matter...

---

### Post by kansasnoob on 2010-03-05
I just began to experience freezes again yesterday. Both times the only open app. was Firefox and I was typing (both times in these forum reply boxes).

Anyway the cursor completely disappears and I seem to have no mouse function, keyboard mostly fails. X refuses to restart (or kill), can't toggle to a TTY, but Alt + SysReq + REISUB does work.

Anyway I filed a bug report If someone should experience the same freezes:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/532807](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/532807)

---

### Post by zika on 2010-03-05
In my case(s) only reset button helped... I've +1-ed bug report...

---

### Post by Saghaulor on 2010-03-17
I'm having random crashes as well. There doesn't seem to be a pattern, and I don't use Firefox.

I'll try disabling KMS.

---

### Post by zika on 2010-03-17
I think I've located the source of the problem, at least on my machine: xorg-edgers. If I ppa-purge to "official" Lucid set of packages offered also on xorg-edgers, crashes disappear, with KMS turned on. As soon as I upgrade to xorg-edgers set of packages, crash is imminent...

Update: No, I've got crash several minutes ago in KMS with "official"  set of packages that are, also, at xorg-edgers. So ball is not in their  court... Back to UMS and xorg-edgers... Still hunting... Crashes and  not-working-shutdown makes this Lucid testing experience a bit  tainted...

---

### Post by dino99 on 2010-03-18
i think you might look at :

[https://bugs.launchpad.net/firefox/+bug/401823](https://bugs.launchpad.net/firefox/+bug/401823)  post 85

this is with KMS with no ppa and nvidia 195.36 installed

---

### Post by zika on 2010-03-18
I see what You mean. I do get a lot of > (firefox-bin:4587): Gdk-WARNING **: XID collision, trouble aheadin .xsession-errors. Good point! I'll see what I can do...
Ditch FF 3.6, or Adobe flash plugin, use Gnash...?

---

### Post by Saghaulor on 2010-03-18
> **zika said:**
> I think I've located the source of the problem, at least on my machine: xorg-edgers. If I ppa-purge to "official" Lucid set of packages offered also on xorg-edgers, crashes disappear, with KMS turned on. As soon as I upgrade to xorg-edgers set of packages, crash is imminent...

Update: No, I've got crash several minutes ago in KMS with "official"  set of packages that are, also, at xorg-edgers. So ball is not in their  court... Back to UMS and xorg-edgers... Still hunting... Crashes and  not-working-shutdown makes this Lucid testing experience a bit  tainted...

How do I turn off KMS?

---

### Post by zika on 2010-03-18
> **Saghaulor said:**
> How do I turn off KMS?Put "nomodeset" in kernel line in GRUB...
When GRUB appears, navigate to kernel You want to use (unless it is a default one), press "E", navigate to the end of line with "quiet splash" > linux	/boot/vmlinuz-2.6.34-999-generic root=UUID=... ro quiet splash nomodesetand add "nomodeset", press Ctrl-X and ... If You want to make it permanent, open ```
gksu gedit /etc/default/grub
``` and change ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```then```
sudo update-grub
```...

---

### Post by zika on 2010-03-18
> **dino99 said:**
> i think you might look at :

[https://bugs.launchpad.net/firefox/+bug/401823](https://bugs.launchpad.net/firefox/+bug/401823)  post 85

this is with KMS with no ppa and nvidia 195.36 installedThank You very much for a first good advice regarding this, a bit, annoying problem with Lucid... I tried Gnash but it doesn't work with sites I visit often. I'll try to stick with AdobeFlashPlugin but refrain of using F3.6 and use Chromium and Opera instead, to see if crashes occur... Great help!
Opera doesn't generate that warning and collision, but Chromium does, at least did one or two, not hundreds as FF does...

---

### Post by Saghaulor on 2010-03-18
> **zika said:**
> Put "nomodeset" in kernel line in GRUB...
When GRUB appears, navigate to kernel You want to use (unless it is a default one), press "E", navigate to the end of line with "quiet splash" and add "nomodeset", press Ctrl-X and ... If You want to make it permanent, open ```
gksu gedit /etc/default/grub
``` and change ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```then```
sudo update-grub
```...

Thank you.

Btw, I don't use Firefox anymore, I've been using Chrome. Perhaps Chrome has been my culprit behind the crashes as well, well that and the KMS.

---

### Post by zika on 2010-03-18
> **Saghaulor said:**
> Thank you.

Btw, I don't use Firefox anymore, I've been using Chrome. Perhaps Chrome has been my culprit behind the crashes as well, well that and the KMS.From what I can see, the only safe browser, now, I can use is Opera... (10.20)... Cromium, also, produces these warnings. I've tried using Gnash or SWF, but they, simply, do not work what I need them to do... So, I'm now, stuck with Opera, KMS and Adobe 64-alpha-plugin... I do not think that downgrading to 32-bit Adobe plugin would change anything, so, I will not try that... With Opera, at least from my moderate experience, You're safe in KMS. We'll see...
Thank You dino99, again!

Update: Unfortunately there is no safe browser:```
(operapluginwrapper-native:5582): Gdk-WARNING **: XID collision, trouble ahead
```...
Current preliminary conclusion: It is Flash-plugin-alpha-64-bit...

Update: I've installed, after so many months of relying on 64-bit plugin, official flashplugin-nonfree (10.0 r45)... It doesn't produce those warnings. I'm, still, unable to figure how to install 10.1 version of that plugin...

---

### Post by sirkeith on 2010-03-18
I get the occasional freeze as well but it is a lot less than when I ran Firefox. I don't know what the problem is but it is related to wireless.

If I freeze, I pop out my wireless card and the freeze releases.

The further from the router I am, the more often the freezes.

keith

---

### Post by zika on 2010-03-18
Despite all my efforts, I'm still not convinced what is the reason of crashes. I've reinstalled 64-bit plugin at took asylum in UMS, for now... It, just now, crashed even though there were no warnings in .xsession-errors... Beats me...

Update: I give up. I'll live with UMS and hundreds of warnings, which, for now, knock on wood, three times, do not crash UMS... I need stable machine and I need flash-plugin, so...

---

### Post by Saghaulor on 2010-03-23
I never ended up doing the KMS kill, but I haven't really had an issue since these last couple rounds of updates.

Resolved? Let's hope so. Now if I could just get this dang sound issue fixed.

---

### Post by zika on 2010-03-23
I do not see it as resolved, yet...
Like non-existant power-off on shutdown that bugs me, also... But that is less problematic, I do not loose any work by having to use power-switch. Random crush cost me some unsaved work, already...

---

### Post by Saghaulor on 2010-03-29
> **zika said:**
> I do not see it as resolved, yet...
Like non-existant power-off on shutdown that bugs me, also... But that is less problematic, I do not loose any work by having to use power-switch. Random crush cost me some unsaved work, already...

It was pretty stable for a few days, then the other night, crash city.

So I retract that statement.

---

### Post by moviemaniac on 2010-03-29
2.6.34-rc2 with KMS enabled has been working great for me the past 24 hours. I jsut hope the issues are gone in the newer mainline kernels - I suspect the problems to derive from Ubuntu devs backporting lots of DRM- and related code from -33 to -32.

---

### Post by zika on 2010-03-29
> **Saghaulor said:**
> It was pretty stable for a few days, then the other night, crash city.

So I retract that statement.It is not a nice thing to say, but I'm glad I'm not alone in this...

---

### Post by moviemaniac on 2010-04-04
Well, I've been using my machine excessively over the last week with KMS on the 2.6.34-rc* series and I haven't encountered a single crash or freeze when before the machine would freeze at least once a day with KMS and Ubuntu's -32 kernel series. So I think it's safe to say it's definitely a kernel (DRM) issue coming from the whole backporting stuff from mainline -33. So if you want to use KMS and your machine freezes randomly I'd very much recommend you to switch to mainline -33 or even better the -34-rc* series (unless you're on a production machine which has to run absolutely stable 24/7).

---

### Post by zika on 2010-04-04
> **moviemaniac said:**
> Well, I've been using my machine excessively over the last week with KMS on the 2.6.34-rc* series and I haven't encountered a single crash or freeze when before the machine would freeze at least once a day with KMS and Ubuntu's -32 kernel series. So I think it's safe to say it's definitely a kernel (DRM) issue coming from the whole backporting stuff from mainline -33. So if you want to use KMS and your machine freezes randomly I'd very much recommend you to switch to mainline -33 or even better the -34-rc* series (unless you're on a production machine which has to run absolutely stable 24/7).Freezes and crashes are gone  for couple of days now, even here... Because of the holidays and not spending the whole day in using my computer, I was not brave enough to mark this [solved]. We'll see in next several days... I'm in KMS for 3-4 days now without retreating to UMS even once...

---

### Post by penguinv on 2010-04-04
Hi, It's cold in here cause this system FREEZES. Or did yesterday. Not yet last night and today.

I've been working with #ubuntu on this one for over 2 weeks and my / our conclusions are:

    NOTHING.


[SIZE="2"][FONT="Comic Sans MS"][INDENT]So let me include it here, as completely as I can, as documentation, for the record, for the community, in hopes of help.[/INDENT][/FONT][/SIZE]

What's this about UBUNTU FREEZES. What does that mean?

[INDENT]Nothing happens, 
the mouse cursor is visible and flashes
the mouse makes no actions. 
the keyboard makes no actions 
there are no lishts flashing or otherwise on the skeyboard
the sequence cntl-SysRq then REISUB does nothing.[/INDENT]

What do I do?  POWERCYCLE.

What is it related to?  FLASH.
In what programs: Firefox (even without addons), Chrome.
Does anything help?:
  after restart the browser opens. I close it, then reopen.
That helps. Once it got so bad that as soon as I opened the browser and started a hulu file in a second it would freeze, ie lock up.

Does it ever happen if I dont use a browser: No.

Is there any triggering that I can tell? is there any consistency? NO. Except Flash has been used but maybe some time ago but always since the browser has been open.


MY SYSTEM IS:
Ubuntu 9.04 upgraded to Ubuntu 9.10 and I still have grub (not grub2). AMD 32 bit. AGP/PCI, nothing there but a modem card, dont use). 
The internet is ethernet from cable.
I ran the grub memtest to completion with no errors.

Have I got anything special added to the regular Ubuntu? 
xchat2, non-free (Medibuntu, then the pastes recommended by Old_Gray_Wolf in the forums here). I have skype but dont use it.
I see Sun Java and Ubuntu One on the list. I see Wine too, from long ago, dont use.


DOES ANYTHING ELSE GO WRONG?
The igoogle page doesnt/_didnt_ work right in either browser. Going to a test page tells me that javascript is indeed installed. FF used to complain about that. I quit using that page. Looked today and it's better, no complaint. Now they have improved and all the corner gizmos show and only the target weekly ad looks wrong A square at upper left shows and the rest is blank.

Jon Stewart didn't work (went black) then on another day later, it did. (Was fun while it lasted.) Then it froze. 

TED was black. I havent tried it recently. How quickly I accept my limitations. No-to-self, wrong strategy.



AND I still say "Where's my flying bunnies?"

---

### Post by Dauthi4 on 2010-04-15
I've got the exact same problem !

Did you find a solution ?

---

### Post by moviemaniac on 2010-04-15
Well, I can only repeat what I've said: I'm on the .34-kernel for over 2 weeks now (currently running -rc4) and I haven't experienced one single crash since - even with excessive use of flash in the browser and video-playback (which triggered the crashes previously on .32 for me too). I'm just wondering: Has a bugreport been filed for this problem - if not, please do so - I can't as there's no way I'll go back to the crashing standard kernels supplied by Ubuntu ;)

---

### Post by zika on 2010-04-15
It seems that the problem is gone, even at my place... Now, I'm waiting for solution of no-sut-down...

---

### Post by Dauthi4 on 2010-04-15
Well,

Following your advice I've just installed 2.6.34rc2. First it seemed ok but after an intensive use of Flash, it hanged.

---

### Post by moviemaniac on 2010-04-15
That's very odd. Which card are you using? I'm on an ATI 2600XT - it could be the problem's not gone throughout all the different cards and their KMS support. As I already mentioned: Please do file a bugreport and tag it as release-critical.

---

### Post by Dauthi4 on 2010-04-15
I'm using this card 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
```

For which package should I open a bugreport ? xorg-video-intel ?

---

### Post by moviemaniac on 2010-04-15
Since a kernel-upgrade fixed it for me on ati I'd suggest filing it against the kernel and maybe also against the xorg-video-intel package just to be sure.

---

### Post by Saghaulor on 2010-04-15
I'm still crashing constantly.

I did a fresh install of Beta2, as I was worried that all the packages updates since Alpha1 might have been part of my problem. 

Apparently it's not the problem. I believe that Flash is related to the crash.

Edit:
I believe the problem to be a combination of the Intel video driver, Compiz, and Flash.

---

