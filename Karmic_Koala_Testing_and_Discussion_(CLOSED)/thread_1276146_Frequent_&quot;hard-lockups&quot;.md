---
title: "Frequent &quot;hard-lockups&quot;?"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-09-26
I just wondered if anyone else is experiencing frequent "hard-lockups" requiring a "hard shut down" by pressing the button on the puter? That's my least favorite way to shut down for obvious reasons.

Of course I always try all the Alt > Sys Rq options, including a full REISUB or just B or K, etc.

I've looked for a pattern to this, but it seems to vary greatly. I've had it happen while watching flash videos, using Nautilus just to view or search files, simply browsing the web, etc. It happens no matter how much demand I'm putting on the CPU, memory, SWAP, etc.

So I consider it a "bug" but I have no idea how to file a bug report when I have no commonality to the freeze. I also have no idea what log I might need to pull up after a hard reboot:confused:

The past few days I've really put Jaunty thru the paces on this same machine (multi-boot) and it seems fine. I've even tried things that should cause a crash!

Anyone else experiencing this?

What logs should I look at after a hard lock-up like that? (Please be exact in the command.)

Any help much appreciated:)

---

### Post by qamelian on 2009-09-26
I've seen this too, sometimes while my laptop is sitting completely idle at the desktop. This has happened to me at different points throughout the alphas, sometimes disappearing after a round of updates for days then suddenly coming back. I can't see any pattern on my machine though.

---

### Post by girto on 2009-09-26
Happens here only when mouse is in motion

---

### Post by mafitzpatrick on 2009-09-26
I've had a few of these lately and it turned out to be due to the root partition filling up - presumably because of the sheer number of updates coming through. I've got 8gb assigned to the root partition (I need to increase due to having databases/website development in var but waiting for the Live CD to rejig the partitions) and it runs up to 97% full and then everything goes sad.

An easy way to clear some space:

```
cd /var/cache/apt/archives
sudo rm *.deb
```

...which will delete the cached copies of packages downloaded by apt. Did the trick for me anyway :) Best of luck!

---

### Post by kansasnoob on 2009-09-26
> **girto said:**
> Happens here only when mouse is in motion

Yes! I've thought that!

It can be as simple as navigating to adjust volume or something like a copy-n-paste!

But need more info! There must be a log to look at:confused:

---

### Post by kansasnoob on 2009-09-26
> **mafitzpatrick said:**
> I've had a few of these lately and it turned out to be due to the root partition filling up - presumably because of the sheer number of updates coming through. I've got 8gb assigned to the root partition (I need to increase due to having databases/website development in var but waiting for the Live CD to rejig the partitions) and it runs up to 97% full and then everything goes sad.

An easy way to clear some space:

```
cd /var/cache/apt/archives
sudo rm *.deb
```

...which will delete the cached copies of packages downloaded by apt. Did the trick for me anyway :) Best of luck!

No free space problem here. I'm in Jaunty right now but once I'm back in Karmic I'll post the output of 'df -H'.

In fact I'll look now.

---

### Post by kansasnoob on 2009-09-26
> **qamelian said:**
> I've seen this too, sometimes while my laptop is sitting completely idle at the desktop. This has happened to me at different points throughout the alphas, sometimes disappearing after a round of updates for days then suddenly coming back. I can't see any pattern on my machine though.

I do seem to notice it most often when I'm changing tasks I guess. I notice it most when I try to move the mouse pointer.

Then everything freezes up tight!

I just need to find out how to find the proper log so we can get this filed!

---

### Post by kansasnoob on 2009-09-26
No free space problem:

> lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              6.3G   3.5G   2.5G  59% /
udev                   1.1G   275k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G   103k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   479M   9.8G   5% /home
lance@lance-desktop:~$ 


---

### Post by excogitation on 2009-09-26
I get that as well - only on my P11Z running an Atom Z520 - 
never experienced it with the other Netbook running an Atom N270.

There's plenty of free space on that machine.

Lockups occur mostly when idle for some time.

---

### Post by kansasnoob on 2009-09-26
Well, what I'm ultimately looking for is some way of "logging" these events so we can file a really good bug report.

To me this is a show stopper!

Some people like to complain about default desktop environments or boot-loaders but that's all something that can be changed.

Hard freezes are indicative of serious trouble!

---

### Post by cariboo on 2009-09-27
@mafitzpatrick

You can accomplish the same thing by typing:

```
sudo apt-get clean
```

to me it seems to be less typing. :)

---

### Post by talkingwires on 2009-09-27
I experienced these, too, around Alpha 5, but they went away. They started again last night. I'd been dist-upgrading without rebooting for several days when it hard-locked again. I rebooted to discover that X/GDM was borked *again*. Arg.

---

### Post by ELD on 2009-09-27
I had hard lockups in jaunty which stopped me using it for a long time, nearly all the help i got was "its probably due to your ati card". They have stopped now though haven't seen any at all recently :D, i hope they don't pop up again in Karmic!

---

### Post by nanog on 2009-09-27
> Well, what I'm ultimately looking for is some way of "logging" these events so we can file a really good bug report.

**/var/log** is your friend. 


use tail to find recent activity in larger log files:

```
sudo tail -100 /var/log/kern.log
```

the commands "diff" and "grep" can also be somewhat useful:

```
sudo diff kern.log kern.log.1 > grep error
```

Those who are not gui-phobic can also look at log files in system-->administration-->log file viewer. 


Hard lock ups related to xorg might be logged here:

```
/var/log/Xorg.0.log
```

Hard lock ups related to the kernel might be logged here:

```
/var/log/kern.log
```


GDM and binary bugs:

```
/var/log/syslog
```

---

### Post by excogitation on 2009-09-27
So here are those logs from a recent lockup (at around 14:07).

I don't see the problem though.

---

### Post by VMC on 2009-09-27
> **nanog said:**
> Those who are not gui-phobic can also look at log files in system-->administration-->log file viewer.

Also look into using the filtering system within that viewer. It can be very helpful when mastered.

---

### Post by girto on 2009-09-27
Despite the mouse and keyboard not responding, we can still ssh into the box.

---

### Post by pedrogfrancisco on 2009-09-27
If your CAPS LOCK light doesn't blink it is either a serious kernel crash or "just" a serious X crash.

I'd like to point you to [a][ project [which] is a set of kernel patches and utilities to allow a copy of the kernel memory to be saved in the event of a kernel panic]("https://wiki.edubuntu.org/KernelTeam/CrashdumpRecipe").

Personally, I haven't got to get it to work but maybe you're luckier than me. My problem was a recurring one, but it worked well enough so the error would get logged, which would be an huge number of lines with:
> Sep 25 13:11:53 HOSTNAME kernel: [  166.776113] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.
Sep 25 13:11:53 HOSTNAME kernel: [  166.780104] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.
Sep 25 13:11:53 HOSTNAME kernel: [  166.784102] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.
Sep 25 13:11:53 HOSTNAME kernel: [  166.788105] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.
Sep 25 13:11:53 HOSTNAME kernel: [  166.792104] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.


Ah, forgot to tell you, in my case the hard lock-ups and kernel panic are triggered by using a WPA-EAP wireless network and.... enabling Bonjour on Pidgin....... Yes, I know, it makes no sense, but I've verified it 3 times now.

Anyway, if you find any similarity, my [bug report is here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/436576").

---

### Post by girto on 2009-09-27
> **pedrogfrancisco said:**
> If your CAPS LOCK light doesn't blink it is either a serious kernel crash or "just" a serious X crash.

In my case, it seems to be an X crash, as the CAPSLOCK light does not change, but I can still ssh into the box.

---

### Post by pedrogfrancisco on 2009-09-27
Then in your case using [Alt+SysRq+R,E,I,S,U,B]("http://fosswire.com/post/2007/9/fix-a-frozen-system-with-the-magic-sysrq-keys/") will probably work, which the original poster said it wouldn't in his case.

[You can also re-enable CTRL+ALT+Backspace]("https://wiki.ubuntu.com/X/Config/DontZap") to check if it responds. Personally, I use the .xinitrc approach:
```
$ cat .xinitrc
setxkbmap -option terminate:ctrl_alt_bksp
```

---

### Post by girto on 2009-09-27
I should have been more explicit:
Pressing CAPSLOCK does not affect the CAPSLOCK LED. In other words, the keyboard is dead.

---

### Post by pedrogfrancisco on 2009-09-27
AFAIK, all keys except the special ones, like [Alt+SysRq+R,E,I,S,U,B]("http://fosswire.com/post/2007/9/fix-a-frozen-system-with-the-magic-sysrq-keys/") and [CTRL+ALT+Backspace]("https://wiki.ubuntu.com/X/Config/DontZap") are handled by the Xorg server. Therefore, if the X crashes, no keys work nor have any effect. But the special ones may have. ALT+SysRq and friends are more probable to work.

---

### Post by W2IBC on 2009-09-27
only hard lockups i get is with firefox + flash.

it seems to be a prob for me that showed up in jaunty. 

can watch like 2 or 3 youtube vids and pow. lockup. also noticed it on Karmic 

im wonder if ether the firefox code or flashplayer code has gotten sloppy?

---

### Post by redrob on 2009-09-27
I'm getting hard lockups too, in a5, a6, and in live CD.
I've looked in the logs, and didn't see anything suspicious.
I've done a ping to the ubuntu machine, and it no longer responds when it locks up.

Will investigate further, but other than going over the logs again, I don't know how to provide any useful info to the developers.

---

### Post by SeePU on 2009-09-27
On my Thinkpad, I get the hard lockup shortly after boot up using the Live CD.  I discovered I can avoid the lockup after disabling Compiz (Fancy effects).

---

### Post by redrob on 2009-09-27
No compiz here.
That was the first thing I checked.

---

### Post by kansasnoob on 2009-09-27
Thanks for all the info. I'll start checking logs the next time I "freeze"!

---

### Post by Longinus00 on 2009-09-28
I consistently get hard lockups after coming back from hibernate. It might not happen right away, but it will happen. If I just use it normally without hibernating+resuming, I have no such problems.

---

### Post by kansasnoob on 2009-09-28
Funny thing. I've been trying to make this thing "lock up" and now can't:lolflag:

No idea why:confused:

I'm going to be brave and try to process some bills (something that'll cost me a little time if it fails) and see what happens.

---

### Post by girto on 2009-09-28
Alt+Sysrq+REISUB did something (switched to a text screen), though it did not always reboot.

Lockups occur when using the Netbook Application Launcher (in UNR) and moving the mouse. However, if the mouse is hovering over another application such as Synaptic, there are no lockups.

---

### Post by sudoer541 on 2009-09-28
could be the intel drivers? 
I have the same problem in 9.04. 
PC suddenly freezes and I have to hard reboot!

---

### Post by kansasnoob on 2009-09-28
Plain Jane Unichrome here. P4M800 - no 3D.

I don't think there's been much change in openchrome drivers since Gutsy. Although auto-detection improved beginning with Intrepid, that is I no longer have to manually edit anything in Xorg.

---

### Post by excogitation on 2009-09-28
Just had another one.
Alt SysRq REISUB isn't working.

I should switch to VESA and see if there are still lockups...

---

### Post by kansasnoob on 2009-09-28
I've been trying like the devil to "freeze" mine again and can't. Sort of makes me want to hang my head in shame since I started this tread:(

And I haven't seen any updates that I would have thought would effect this. Maybe I'm a dunce:confused:

---

### Post by kansasnoob on 2009-09-28
BTW the "hard lockups" or "freezes" I was talking about rendered everything dead!

No response through keyboard or mouse, no lights on the keyboard, but my CPU temp monitor indicated ZERO usage of the CPU.

---

### Post by merlyn on 2009-09-28
I recently installed the latest Karmic build, and all current updates.

I've also been experiencing "hard lockups" where Alt SysReq REISUB and Ctrl Alt Bksp are ineffective.

The only solution is to do a hard reboot.  

It's a little disappointing to say the least as I've just decided to give *buntu another look after the Jaunty lockup debacle that led me to move to another distro.

Just as well this in on my test box, and I've got a stable system to work with.

/sigh and I'd been hearing good things about Karmic also.

Also an unrelated 'problem' is that there is no Grub screen or Usplash on boot.

I'm impressed with the boot times.

But come on *buntu devs these kind of show stoppers so late in the development cycle.

Thank heavens for true Debian, that's all I can say.

---

### Post by VMC on 2009-09-28
> **kansasnoob said:**
> BTW the "hard lockups" or "freezes" I was talking about rendered everything dead!

No response through keyboard or mouse, no lights on the keyboard, but my CPU temp monitor indicated ZERO usage of the CPU.

When mine locked up just like you discribed, I looked at two files in my home dir for some insight, namely ~/.xsessions-errors and .xessions-errors.old.

---

### Post by orawax on 2009-09-30
I just today installed Karmic Daily build from Alternate cd, with the filesystem encrypted. The system becomes totally unresponsive when logging in - "hard-locked" as it was said. Ctrl-Alt-REISUB doesn't work.

[See temporary patch at the bottom]

During first login, the gnome-panel loaded before the system hung. Since then it hangs already before the panel gets to load. Also the ubuntu-tune was crackling in the first login, and since then there has been no login sound.

I checked various logs but can't tell what could be the problem.

/var/log/syslog

```
Sep 30 19:04:03 leviathan console-kit-daemon[1080]: WARNING: Couldn't read /proc/1073/environ: Failed to open file '/proc/1073/environ': No such file or directory
...
Sep 30 19:04:07 leviathan gnome-session[1330]: WARNING: Could not launch application 'polkit-gnome-authentication-agent-1.desktop': Unable to start application: Failed to execute child process "/usr/libexec/polkit-gnome-authentication-agent-1" (No such file or directory)
...
Sep 30 19:04:07 leviathan rtkit-daemon[1387]: Failed to make ourselves RT: Invalid argument
(...several times the same...)
Sep 30 19:04:14 leviathan pulseaudio[1385]: ratelimit.c: 3 events suppressed
Sep 30 19:04:15 leviathan wpa_supplicant[1154]: CTRL-EVENT-SCAN-RESULTS
(...four times...)
Sep 30 19:04:30 leviathan rtkit-daemon[1387]: Failed to make ourselves RT: Invalid argument
(...repeats several times...)
Sep 30 19:04:36 leviathan pulseaudio[1707]: ratelimit.c: 5 events suppressed
Sep 30 19:04:36 leviathan wpa_supplicant[1154]: CTRL-EVENT-SCAN-RESULTS 
Sep 30 19:04:41 leviathan wpa_supplicant[1154]: CTRL-EVENT-SCAN-RESULTS 
Sep 30 19:04:43 leviathan pulseaudio[1707]: ratelimit.c: 1 events suppressed
Sep 30 19:04:46 leviathan wpa_supplicant[1154]: CTRL-EVENT-SCAN-RESULTS 
Sep 30 19:04:48 leviathan wpa_supplicant[1154]: CTRL-EVENT-SCAN-RESULTS 
```

/var/log/messages doesn't show any errors apart from the three pulseaudio messages also in syslog (above)
/var/log/kern.log -no errors

The Machine is IBM ThinkPad T41.

Sound: Intel 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97
Video: ATI Radeon RV250 [Mobility FireGL 9000]
Ethernet: Intel 82540EP Gigabit (Mobile)
Wireless: Intel PRO/Wireless LAN 2100 3B Mini PCI

**Temporary patch:**

I guessed the ATI Radeon might be at least part of the problem, so I logged into the shell from login screen (Ctrl-Alt-F1) and created an xorg configuration file

```
sudo nano /etc/X11/xorg.conf
```

First I put there my old xorg.conf from Jaunty, but with that compiz was reeeeally slow. Then I found [this great xorg.conf](http://ubuntuforums.org/showpost.php?p=7804812&postcount=2), which seems to work perfectly.

Now login succeeds and compiz works, no hard-lock.

EDIT:
Nothgin in ~/.xsessions-errors or .xessions-errors.old

---

### Post by Anubis on 2009-09-30
:lolflag:EVERY release there are hoards of screamers accusing Ubuntu of "hard locking" their systems. The only times I EVER have had such issues is when faulty hardware was present. Faulty BIOS in my XFX nvidia 680i which had to be flashed to a BIOS for the same chipset/board from another manufacturer(EVGA). Faulty hard drive was the culprit another time. This last time I just installed KK alpha6 on two boxes. Koala on my mythtv build is solid. I installed from usb flash drive flawlessly. It runs like a champ. On a c2d 6600 with 2gs base Kingston ram ddr2 pc5300, basically slow ram. Brand new Asus basic board, with brand new WD sata drive. Just recently I had issues with my main machine. That was due to adding 4 more gigs of ram and my ram timings were too tight. Then I could not install from cd or usb stick, UNTIL I changed my dvd drive. After putting in a new dvd drive I was able to install KK on my c2q with 8gb OCZ ram no issues at all. 

No lockups, no freezes no slow downs. My phoronix linux-system benchmarks blow my 9.04 install out of the water.

All this to say check your hardware. Anytime someone here or the IRC channels suggested it may be my hardware I took it as an easy dismissal of my problems. Once I keep at it instead of looking for someone to blame, I found that indeed it was my hardware.

Check your hardware.:popcorn:

---

### Post by kansasnoob on 2009-09-30
Well, I've changed no hardware or drivers.

The "hard-lockups" seem to have stopped!

I watch the updates closely and I see no apparent reason, I think however they stopped after the recent "ubuntu-desktop" updates.

Makes no sense to me but I'm happy!

---

### Post by stinger30au on 2009-09-30
what amazes me is that every release before the new version is ready people run out and try it and whinge when it doesnt not work when it is stated very clearly at the ubuntu web site it is in development stages and not ready for install but ready for testing only

---

### Post by redrob on 2009-09-30
I did an upgrade of a6 on Monday, and the lockups disappeared.
It's all working nicely.:P

I did notice some extremely weird behaviour just before lockup...

Firstly, I could always cause a lockup by launching Firefox.
Secondly I always got the following in the syslog when the lockup occured:

```
Sep 28 02:07:39 X hp[2378]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 28 02:07:40 X python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 28 02:09:42 X anacron[2052]: Job `cron.daily' started
Sep 28 02:09:42 X anacron[2406]: Updated timestamp for job `cron.daily' to 2009-09-28

```

What's really bizarre is that I don't have any printers attached, and as far as I'm aware,  hp[2378] is connected to running an hp printer.
Also why on earth would cron.daily only run as soon as Firefox is started?

I supect it was a bug with udev, maybe connecting something to the wrong device?

The only thing that disappoints me about this alpha experience is that I can't find a checklist to debug this kind of problem.
Beyond the Alt+SysRq+R,E,I,S,U,B there seems to be nothing to move this kind of bug forwards.

---

### Post by merlyn on 2009-09-30
> **Anubis said:**
> EVERY release there are hoards of screamers accusing Ubuntu of "hard locking" their systems.

I can assure you that it is not a hardware problem with my system.

The only times that I have **ever** experienced such problems with *buntu was after dist-upgrading to from 8:10 to 9:04 **after** the final release date, and also with a subsequent fresh install.

Hence my move to straight Debian (Sid)

This after running "stable" *buntu since the Warty Warthog release, and various development releases also.

In addition to that I have the same problems with the current karmic release with all updates on my **test** drive.

Debian Sid continues to runs faultlessly on the **same** system, installed on my **main** drive.

It's amazing just how quickly people disregard the problems encountered by others if they haven't experienced the same.

Don't you think it possible, with the number of people experiencing similar problems that their is substance to their statements?

---

### Post by ELD on 2009-10-01
What annoys me is that i get told it is my ATi card, yet any other operating system i throw at it works without a hitch, Win XP included and we all know how old it is now, surely Ubuntu should be able to do a better job being much more up-to-date.

I am hoping Karmic stops the freezing for me or i will have to jump ship.

---

### Post by orawax on 2009-10-01
> **Anubis said:**
> EVERY release there are hoards of screamers accusing Ubuntu of "hard locking" their systems. ... No lockups, no freezes no slow downs. My phoronix linux-system benchmarks blow my 9.04 install out of the water. All this to say check your hardware

Good for you. I've installed the beta of both Jaunty and Intrepid on this same hardware. Always there's been problems with the ATI RV250, but this is the first time it locks up like this. And could you point out the posts where you find screaming?

> **stinger30au said:**
> what amazes me is that every release before the new version is ready people run out and try it and whinge when it doesnt not work when it is stated very clearly at the ubuntu web site it is in development stages and not ready for install but ready for testing only

I thought this forum is here just for that purpose - for ppl to share their experiences and problems. I can't find much whining in this tread, apart from those who whine when ppl dare to report problems with the version still under development. I for one installed Karmic alpha fully aware that it's not yet ready. Even though I'm no developer, I wanted to help for my part by reporting any problems at this point. This kind of feedback ('screaming', 'whining') is not very encouraging. Rather you could tell how to file a bug, how to find out what to report etc...

EDIT: Perhaps the problem are these broad and false generalizations - "*every* time", "*hoards* of screamers", "*nobody's* screaming or whining". Ill communication... Better stick to the fact than generalize.

> **SeePU said:**
> On my Thinkpad, I get the hard lockup shortly after boot up using the Live CD.  I discovered I can avoid the lockup after disabling Compiz (Fancy effects).

I installed Karmic succesfully on ThinkPad T41 from the [_Alternate install cd (Daily build)_](http://cdimage.ubuntu.com/daily/current). Before logging in I had to create an xorg.conf file to make ATI driver work (see my previous post).

---

### Post by Anubis on 2009-10-01
> **merlyn said:**
> I can assure you that it is not a hardware problem with my system.

The only times that I have **ever** experienced such problems with *buntu was after dist-upgrading to from 8:10 to 9:04 **after** the final release date, and also with a subsequent fresh install.

Hence my move to straight Debian (Sid)

This after running "stable" *buntu since the Warty Warthog release, and various development releases also.

In addition to that I have the same problems with the current karmic release with all updates on my **test** drive.

Debian Sid continues to runs faultlessly on the **same** system, installed on my **main** drive.

It's amazing just how quickly people disregard the problems encountered by others if they haven't experienced the same.

Don't you think it possible, with the number of people experiencing similar problems that their is substance to their statements?
You know very well I discounted nothing. I gave my experiences and shared the degree of confidence I had it was not my hardware too, but it was. I merely suggested people NOT rush to dismiss that it MAY be their hardware and or setup.

---

### Post by fela on 2009-10-01
I got lockups once when I compiled a kernel with voluntary preemption and an 1000HZ timer on Ubuntu 8.10 (or 9.04, can't remember).

I think it's almost certainly a kernel bug, as it would probably have to be to cause such a serious lock up.
[B]
@@@@@@ DO DO DO NOT NOT NOT RUN WHAT FOLLOWS !!! @@@@@[/B]
(To the mods: if you see this as inappropriate, please remove it instead of giving me a warning :) )

but anyway, an easy way to lock up a Linux system running bash, if you haven't checked your thread-per-user limits:

```
:(){ :|:& };:
```

It's a beautiful and nasty piece of code. _Don't run it._

It's called a fork bomb and it creates endless threads that do absolutely nothing, but take up all the CPU time leaving nothing for anything else, effectively locking up the system. It's a form of denial of service attack.

Just a thought but if you're connected to the internet and you get random lockups, there's a very slim chance that someone has hacked into your computer and is running this out of spite. Although this is extremely unlikely.

---

### Post by Anubis on 2009-10-01
> **orawax said:**
>  And could you point out the posts where you find screaming?


To what end?:popcorn:

---

### Post by Hated On Mostly on 2009-10-02
When Jaunty was released and people complained about lockups and crashes, people laughed and said it was the user's fault as well.

Turned out the stable kernels for Jaunty had some critical data corruption bugs which were eventually fixed but too late for a lot of people. Not to mention the fixes have not been released for Jaunty, just corrected for Karmic kernels.

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/330824)

Also seem to be some other bugs in Jaunty causing lockups if you go through the very long thread.

Given all of the confirmed bugs in Karmic that cause high CPU usage or instability (ex: xorg using 100% CPU unless you logout and login), freezing should be taken more seriously and not brushed off.

---

### Post by SeePU on 2009-10-02
Well, being brushed off and ignored is basically what the problem starts with.  

You have users here who mock, criticize, jeer or otherwise scoff at those who criticize or report these lock-ups, freezes, crashes, call it what you will.  If these users, which seem to be numerous, are so indifferent and ignorant about these issues, then what convinces you that the Developers will give a hoot?

I filed a bug about the lockup and it still isn't responded to.  I guess they don't care about owners of older hardware.

The release is yet not even a month away and I haven't noticed hardly any changes or replies to the bugs.

The bugs are one thing but the attitude is another.

The degree of importance seems low so I'll probably end up installing Debian on my Thinkpad T41.  At least, there are alternatives. Debian and the offshoots have options for getting close to bleeding edge so one is not losing anything if they want up-to-date.

---

### Post by SeePU on 2009-10-02
> **orawax said:**
> 
I installed Karmic succesfully on ThinkPad T41 from the [_Alternate install cd (Daily build)_](http://cdimage.ubuntu.com/daily/current). Before logging in I had to create an xorg.conf file to make ATI driver work (see my previous post).
Well, it shoudl work automatically as you have no choice but to use the open source driver.   

Maybe the xorg.conf file can be tweaked.

The thing is, effects must be turned off or the entire system will lock up soon.  Not that I need effects but it's a pretty major problem, I think.

---

### Post by excogitation on 2009-10-02
> **SeePU said:**
> 
I guess they don't care about owners of older hardware.
Not only old hardware is affected. I'm on an Atom Z520.
The only other machine I had lockups previously was a brand new Atom N330 box (which isn't my computer so I didn't investigate).

I haven't had any lockups in quite a while - but I'm not really using Ubuntu that much on the affected machine - guess why ;-)

> **SeePU said:**
> 
The bugs are one thing but the attitude is another.

...at least, there are alternatives...

/signed

---

### Post by adamhalliwell on 2009-10-02
Mine locked up completely when I was coming back from suspend and the network manager was connecting. Like some of the others, I was moving my mouse when it happened. I'm running a fresh install of beta. I've never experienced any hard lockups on this hardware from Dapper to Jaunty.

---

### Post by RavenHollow on 2009-10-05
Have also been experiencing random lockups here with capslock and numlock blinking.  It has happened a number of times but recently I got  an actual crash report after reboot!  So naturally I submitted to launchpad assuming it would help and perhaps an answer would come.

Well as you can see by looking at [https://bugs.launchpad.net/ubuntu/+bug/440291](https://bugs.launchpad.net/ubuntu/+bug/440291), the title bar has been changed to "Bug # 440291 is not in Ubuntu".  What the heck does that mean?  If someone expended effort to figure out that it is NOT in Ubuntu, then how much extra work would be involved to say something like "take a look here"?  

Having spent hours searching and reading and finding some suggestions about kernel parameters, video or wireless drivers, testing hardware, etc. there is still no definitive "fix".  Eventually I will figure this out, but I just don't get the arrogance and rudeness shown by these so-called "experts" who most likely could provide some guidance. 

By slim chance is there anyone out there with enough decency to offer some specific suggestions on what to do about these lockups?

Best, -- Jake
Karmic updated this morning
Dell Inspiron 1720, Core 2 Duo T-7500, 4GB, GeForce 8600M GT, BCM4401-B0, BCM4311

---

### Post by olskar on 2009-10-05
I had troubles with this in Jaunty. And so did other people. So many people that the thread I created about the issue now has 69 pages and around 700 posts.

I most certainly hope this is fixed in Karmic. This was a showstopper, stopping hundreds of people from using Jaunty.


 [http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by Hated On Mostly on 2009-10-05
It is definitely annoying to have an unstable system and have the problem completely ignored. 8.04 (Hardy Heron) and 8.10 (Intrepid Ibex) were stable for me. 9.04 (Jaunty Jackalope) was a disaster for me and I didn't even experience as bad a problem as most others.

I haven't tested Karmic Koala until now. I am using the alternate CD daily build (2009.10.04) and thankfully I it has been stable and fast so far. Still have more testing to do, but it looks like I am getting lucky this time around. When Ubuntu works properly it is the best. When it doesn't it is the worst. Seems like there is no middle ground for it.

As far as other distributions to try I would give the new openSUSE milestone release a try. I tried it out and it was great. openSUSE has really made a lot of progress. Whole disk encryption, faster I suspect due to Beagle being disabled by default, easy to use and configure, easy package and application management.

The only reason I bothered to try out Karmic Koala is because there is a DEB package available for SABnzbd which I use. Sure I could install it manually in openSUSE but I prefer packages. I want to use my computer to get things done quickly, not to tweak and play with settings, updates, and constantly fixing problems. Fedora 11 was nice as well, 12 should be great when it comes out although I would not recommend using the alpha version. Too bad those distributions use RPM. 

[http://news.opensuse.org/2009/10/01/opensuse-11-2-milestone-8-released/](http://news.opensuse.org/2009/10/01/opensuse-11-2-milestone-8-released/)
[http://software.opensuse.org/developer](http://software.opensuse.org/developer)

I don't like Debian because you have to manually install/setup everything like firmware, drivers, etc. Somebody should come out with a version of Debian that isn't Ubuntu, that comes with the non-free stuff and has everything setup and ready to use like every other major distribution. Oh and it must offer whole disk encryption. Seems like every Debian based distribution out there is really based off of Ubuntu (and thus has Ubuntu specific bugs) or doesn't offer whole disk encryption.


The only other suggestion to try to stop the crashing is maybe check out this thread:

[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Modifying the DSDT file has relieved some people of problems and bugs with Ubuntu. Unfortunately for this freezing problem I don't think it will work. The problem seems to be very Ubuntu specific. It is worth a shot though.

---

### Post by pedrogfrancisco on 2009-10-05
I believe the easiest way to fix our problems is to get [KernelTeam/CrashdumpRecipe]("https://wiki.edubuntu.org/KernelTeam/CrashdumpRecipe") working.

Once it is working, we'll have a precise dump which will helpfully allow the devs to see clearly where the problem is.

Unfortunately, I can't [get it to work]("http://ubuntuforums.org/showthread.php?t=1283276"). You may have better luck than me, though.


Because honestly, we *can* crash our systems easily. We *can't* pinpoint the exact causes. Therefore, I believe the best thing we *can* do is get that thing working and submit the kernel dump to Ubuntu devs.

---

### Post by userid on 2009-10-18
Super annoying, I've been on ubuntu for years now, sometimes I got a less stable ride when upgrading early.. karmic is a catastrophe, constant lockups. I don't know how to bugtrace/report this either, although the symptoms are as described above. As this coincides 100% with my move from 810 to 910 (clean install of course, encrypted home, ati radeon) it must be due to karmic..

---

### Post by BigSilly on 2009-10-18
This is worrying. It's something I saw with Intrepid, but not on Jaunty, so I'm hoping it doesn't rear its ugly head in the final Karmic. I do remember though, doing a second fresh install of Intrepid seemed to clear up the issue. I don't know if that would be any use here though.

---

### Post by RdFltErr on 2009-10-18
> **kansasnoob said:**
> I just wondered if anyone else is experiencing frequent "hard-lockups" requiring a "hard shut down" by pressing the button on the puter? That's my least favorite way to shut down for obvious reasons.

Of course I always try all the Alt > Sys Rq options, including a full REISUB or just B or K, etc.

I've looked for a pattern to this, but it seems to vary greatly. I've had it happen while watching flash videos, using Nautilus just to view or search files, simply browsing the web, etc. It happens no matter how much demand I'm putting on the CPU, memory, SWAP, etc.

So I consider it a "bug" but I have no idea how to file a bug report when I have no commonality to the freeze. I also have no idea what log I might need to pull up after a hard reboot:confused:

The past few days I've really put Jaunty thru the paces on this same machine (multi-boot) and it seems fine. I've even tried things that should cause a crash!

Anyone else experiencing this?

What logs should I look at after a hard lock-up like that? (Please be exact in the command.)

Any help much appreciated:)


I am having this exact problem also. I concur that I thought it was when the mouse was moved, but I've also experienced the lockup when the computer simply goes to sleep and I come back later to use it. Hard locked up frozen - no caps lock toggling works, no magic keystrokes get me out. Have to hold power button for 5 seconds to shutdown.

Can't find ANYTHING suspicious in the logs. I also did a FULL re-install via the 9.10 ISO and ran for a few days without issue. Then I did an apt-get upgrade and the behavior started happening again.

Would love some help here. I see no pattern...

---

### Post by userid on 2009-10-21
Still going on.. hoping it will be fixed upon every single update.. Has anyone seen a relevant bug report as of yet? [This one]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014") looks like it may be relevant.. Provided you have an ecrypt-encrypted home dir..

---

### Post by stans on 2009-10-23
I've filed a bug report as my pointer locks up - but not the system.

It is indeed a show stopper. Cannot proceed with plans for applications.

I am NOT whining, and DO realize this is a development environment. However, I will have a problem with my hardware being accused as I ran Jaunty from a different hard drive with the same lockups... and then ran OpenSolaris from that same drive with no lockups. This of course exonerates the motherboard if I am not mistaken. Yes, I did open a bug report.

---

### Post by qamelian on 2009-10-23
I gave up and switched to the rt kernel for Ubuntu Studio several days ago and haven't had a single lockup since.

---

### Post by userid on 2009-10-23
Sounds good ;) How do I install the RT kernel?#

Edit: Ehem! Synaptic does it.. Will report back

---

### Post by merlyn on 2009-10-24
> **qamelian said:**
> I gave up and switched to the rt kernel for Ubuntu Studio several days ago and haven't had a single lockup since.

Outstanding, I'll give this a go.

What pray tell are the kernel team up to I wonder.

Jaunty was plagued by hard locks after it went gold as 8:04 and now this.

Yes, yes "it's a beta" (tm), I get it. :roll: 8:04 however was not.

Thankfully I don't use Ubuntu as my main OS anymore, just dip my toe in the water from time to time to see how things are going.

It's Debian SID for me now, has been since the aforementioned 8:04 problems.

---

### Post by userid on 2009-10-24
That didn't help..

---

### Post by tghe-retford on 2009-10-24
I've just recently been getting hard lockups since reinstalling Kubuntu. This looks to be the cause from the kernel log:
```
Oct 24 11:43:08 TGHE kernel: [ 2089.413240] general protection fault: 0000 [#1] SMP 
Oct 24 11:43:08 TGHE kernel: [ 2089.413246] last sysfs file: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-5/1-5:1.0/uevent
Oct 24 11:43:08 TGHE kernel: [ 2089.413249] CPU 0 
Oct 24 11:43:08 TGHE kernel: [ 2089.413251] Modules linked in: binfmt_misc snd_hda_codec_realtek dvb_pll cx22702 cx88_dvb cx88_vp3054_i2c videobuf_dvb dvb_core snd_hda_intel cx8800 cx8802 snd_hda_codec cx88xx ir_common i2c_algo_bit snd_hwdep v4l2_common videodev snd_pcm iptable_filter v4l1_compat snd_timer ppdev lp ip_tables snd v4l2_compat_ioctl32 psmouse tveeprom soundcore videobuf_dma_sg parport_pc snd_page_alloc btcx_risc videobuf_core i2c_nforce2 parport x_tables serio_raw nvidia(P) asus_atk0110 joydev hid_microsoft usbhid usb_storage ohci1394 ieee1394 forcedeth
Oct 24 11:43:08 TGHE kernel: [ 2089.413284] Pid: 1300, comm: Xorg Tainted: P           2.6.31-14-generic #48-Ubuntu System Product Name
Oct 24 11:43:08 TGHE kernel: [ 2089.413286] RIP: 0010:[<ffffffffa02a8daa>]  [<ffffffffa02a8daa>] _nv013815rm+0x95/0x507 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.413501] RSP: 0018:ffff88007c88bd08  EFLAGS: 00010297
Oct 24 11:43:08 TGHE kernel: [ 2089.413503] RAX: 0000000000000001 RBX: 0000000000000003 RCX: 0000000000000003
Oct 24 11:43:08 TGHE kernel: [ 2089.413505] RDX: 0000000000000004 RSI: ffff880075dd0000 RDI: ffff8800774c4000
Oct 24 11:43:08 TGHE kernel: [ 2089.413507] RBP: ffff880077f6aca0 R08: ffff880077f6acec R09: ffff880075dd0000
Oct 24 11:43:08 TGHE kernel: [ 2089.413509] R10: 0000000000000060 R11: 0000000000000000 R12: ffff8800774c4000
Oct 24 11:43:08 TGHE kernel: [ 2089.413511] R13: ffff880075dd0000 R14: 0000000000000001 R15: ffff88003794b000
Oct 24 11:43:08 TGHE kernel: [ 2089.413513] FS:  00007ff6f94d06f0(0000) GS:ffff8800019f4000(0000) knlGS:0000000000000000
Oct 24 11:43:08 TGHE kernel: [ 2089.413515] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 24 11:43:08 TGHE kernel: [ 2089.413517] CR2: 00000000027fe000 CR3: 0000000075c9f000 CR4: 00000000000006f0
Oct 24 11:43:08 TGHE kernel: [ 2089.413519] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 24 11:43:08 TGHE kernel: [ 2089.413521] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 24 11:43:08 TGHE kernel: [ 2089.413524] Process Xorg (pid: 1300, threadinfo ffff88007c88a000, task ffff88007b25ad60)
Oct 24 11:43:08 TGHE kernel: [ 2089.413525] Stack:
Oct 24 11:43:08 TGHE kernel: [ 2089.413526]  ffff88007c4a4bd0 0000000000000003 0000000000000003 ffff88007a6c2000
Oct 24 11:43:08 TGHE kernel: [ 2089.413530] <0> ffff8800774c4000 ffffffffa0284a8b ffff880075dd0000 0000000000000001
Oct 24 11:43:08 TGHE kernel: [ 2089.413534] <0> 0000000000000001 0000000000000000 ffff8800774c4000 ffffffffa0418c3a
Oct 24 11:43:08 TGHE kernel: [ 2089.413538] Call Trace:
Oct 24 11:43:08 TGHE kernel: [ 2089.413663]  [<ffffffffa0284a8b>] ? _nv013814rm+0xd4b/0x1189 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.413790]  [<ffffffffa0418c3a>] ? _nv003848rm+0x3dc/0x45d [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.413915]  [<ffffffffa040d29b>] ? _nv007315rm+0x81/0xbb [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414039]  [<ffffffffa040d25e>] ? _nv007315rm+0x44/0xbb [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414153]  [<ffffffffa02174f5>] ? _nv003829rm+0x305/0x5e9 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414279]  [<ffffffffa04994d5>] ? rm_ioctl+0x2f/0x67 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414381]  [<ffffffffa057bcac>] ? nv_kern_ioctl+0x13c/0x450 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414482]  [<ffffffffa057bffc>] ? nv_kern_unlocked_ioctl+0x1c/0x20 [nvidia]
Oct 24 11:43:08 TGHE kernel: [ 2089.414486]  [<ffffffff8112ddfd>] ? vfs_ioctl+0x1d/0xa0
Oct 24 11:43:08 TGHE kernel: [ 2089.414489]  [<ffffffff8112e429>] ? do_vfs_ioctl+0x79/0x370
```
As I suspected, Xorg is causing it (explains why the mouse, keyboard and graphics froze whilst the sound continued to work).

EDIT: This may be the relevant bug report, but has reported to affect their AMD proprietary driver, whilst I use the latest NVidia proprietary driver: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/436326](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/436326)

---

### Post by stans on 2009-10-24
My kernel log doesn't show anything useful at all. The xorg log neither.

---

### Post by tghe-retford on 2009-10-24
> **stans said:**
> My kernel log doesn't show anything useful at all. The xorg log neither.
In terms of what I found, does this show anything? If not, your issue isn't related to mine.
```
grep "general protection fault" /var/log/kern.log
```

---

### Post by stans on 2009-10-24
No - nothing found. Just locked up again. Here's the last few lines. I wonder now if logging stopped earlier... doesn't seem reasonable to not see any entries for 45 minutes.

Oct 24 04:31:48 stan-desktop kernel: [   58.631382]   groups: 1 0
Oct 24 04:31:48 stan-desktop kernel: [   58.631387]   domain 1: span 0-1 level MC
Oct 24 04:31:48 stan-desktop kernel: [   58.631389]    groups: 0-1 (__cpu_power = 20 4 8 )
Oct 24 05:15:54 stan-desktop kernel: [ 2704.394546] __ratelimit: 3 callbacks suppressed
Oct 24 05:15:54 stan-desktop kernel: [ 2704.394553] npviewer.bin[2486]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000fffd7b1c error 14
Oct 24 05:45:42 stan-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Oct 24 05:45:42 stan-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset

---

### Post by TimT on 2009-10-24
Can I just add a me-too here ? 
Possibly relevant data:
Hardware ASUS F3Tc, Nvidia geforce go 7300, driver 185.18.36, 2Gigs
Funny thing is, with me the lockup is repeatable: always happens on the first bootup in the day, at a random time in the hour after boot. 
Usually happens when I'm scrolling round in firefox.

I've always suspected the video drivers..

---

### Post by TimT on 2009-10-25
Just had another one.

- Plugging in an USB stick did not help
- Alt-SysRQ: I forgot the proper key-sequence, I'll make a note later :redface:

- The linux-crashdump package didn't do anything either..

---

### Post by userid on 2009-10-25
I think the crashdump package i meant to help you produce crash data for the developers... ;)

I tend to think it's something to do with the usb system, as the last message in the log is always something related to USB, and it often happens whilst plugging in/removing a USB disk.

I'm on radeon open source drivers. Changing to the RT kernel did not help..

---

### Post by jandante on 2009-10-25
I also have those hard freezes.

I can minimize them by using cpufreq-selector by doing:

sudo cprufreq-selector -c 0 -g conservative

this is setting cpu 0 to the governator conservative.

If you have more then one cpu you do it again but 1 in stead of 0.

This really minimizes the lock-ups for me.

---

### Post by merlyn on 2009-10-25
Has there been and "official" response to this problem, or any developers posts?

This is horribly reminiscent of the "hard-lockup" problem that occured when 8:04 went gold.

Granted Karmic isn't 'gold' yet but at this stage in the release cycle for some many folks encountering this 'show stopper' it doesn't bode well for the release of 8:10.

---

### Post by userid on 2009-10-25
> **jandante said:**
> I also have those hard freezes.

I can minimize them by using cpufreq-selector by doing:

sudo cprufreq-selector -c 0 -g conservative

this is setting cpu 0 to the governator conservative.

If you have more then one cpu you do it again but 1 in stead of 0.

This really minimizes the lock-ups for me.

This would limit the frequency of changes; I have had the lockup occuring with cpufreq set to a fixed frequency (i.e. zero changes).

---

### Post by TimT on 2009-10-26
> **userid said:**
> I think the crashdump package i meant to help you produce crash data for the developers... ;)



Yes, I understood that.. ;-)
What I meant to say is that the crashdump package did not log any errors.

Just a thought: this is an AMD processor, 
On every start up, I get 
powernowd-k8 : ph2 null fid transition 0x8 
displayed on the terminal

Trying startup/shutdown/startup now, since things are usually OK on the second startup.

---

### Post by anselm on 2009-10-26
I'm having hard lockups, also no pattern to why, I've been blaming it on my intel Video.

---

### Post by girto on 2009-10-26
I tested 2 different boxes with Intel CPU and graphics with karmic RC Netbook Remix.

1st box freezes (no mouse motion, Alt+SysReq+REISUB almost works) just when i move the mouse. With the UNR Application Launcher disabled, the freeze would occur just when i click on the menu on the top panel.

2nd box froze after a while, but the mouse could still be moved.

I updated the 1st box and tested with the UNR Application Launcher disabled. No more freezing.

I hope this is on the way to be solved.

---

### Post by NRDNick on 2009-10-26
I realize that the OP is not using an NVidia GPU, however for anyone else here that is, and is encountering issues with freezing and artifacts on screen, check out the workaround from this thread [http://ubuntuforums.org/showthread.php?t=1247300&page=3]("http://ubuntuforums.org/showthread.php?t=1247300&page=3") It has seems to have cleared up a few issues for me, one of which was a freezing/unresponsive desktop. The workaround disables the nvidia GPU scaling known as Powermizer. Just an idea.

---

### Post by thecityofgold2006 on 2009-10-26
Karmic installed for about 3 hours now and 2 hard lockups already.

Amd64 version with Nivdia 185. I'm also getting a 'your system encountered a serious kernel problem' crash report repeatedly (high priority on launchpad already). not sure if it's related. 

And this thing launches when?!?!

---

### Post by userid on 2009-10-26
I'm fairly sure it only occurs whilst I'm moving the mouse around.. Couldn't find an input-related bug though..

---

### Post by Piscium on 2009-10-26
I have an old PC: Pentium 4, 2 GBytes RAM, 965 Intel graphics.

I tried twice to install Ubuntu Alpha 4 and failed both times. Gave up on it.

When Alpha 5 came out I tried it. I managed to install it successfully, but every time I loged in I had lockups, similar to what other people described in this thread: I saw the Gnome desktop, did things, and then the mouse and keyboard stopped working and the screen stopped updating. This happened between 45 seconds to 10 minutes after the Gnome desktop appeared. I then needed to press the power button to power off the computer. This happened I think five times so I gave up on Alpha 5 too.

As I don't have much time for testing Ubuntu, I have not tried any other release since, will wait for the official 9.04.

The sad thing is that I don't know what caused the issue. I have very little experience with Linux so it is difficult to diagnose the problem. I did look at the system log once and things seemed more or less normal.

António

---

