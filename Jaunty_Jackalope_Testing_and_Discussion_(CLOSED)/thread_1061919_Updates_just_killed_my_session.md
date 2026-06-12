---
title: "Updates just killed my session"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kazade on 2009-02-06
I just ran the latest updates for Jaunty, and now after login I just get dumped at a blank wallpaper :( anyone else experiencing this?

---

### Post by Kazade on 2009-02-06
Hmm... removing my xorg.conf and rebooting seems to have fixed it.. weird.

---

### Post by Kazade on 2009-02-06
It's something to do with the nVidia driver. When I just reenabled the latest one I lost the ability to login :(

Am I the only one seeing this problem?

---

### Post by walmis on 2009-02-06
Compiz broke, if i remove it i can login again.

---

### Post by zenarcher on 2009-02-06
Same here with Kubuntu and Nvidia video.

---

### Post by minisori on 2009-02-06
compiz.real: *** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x0000000003ad4eb0 *** 

Yes is compiz :S

Probably comes from one of these  updates:
> xserver-common (2:1.5.99.902-0ubuntu1) to 2:1.5.99.902-0ubuntu2
xserver-xorg-core (2:1.5.99.902-0ubuntu1) to 2:1.5.99.902-0ubuntu2

---

### Post by taavikko on 2009-02-06
@minisori, those packages are already updated.
2:1.5.99.902-0ubuntu3 is the new version. and in use.

I suggest using main server for upgrades.

---

### Post by minisori on 2009-02-06
> **taavikko said:**
> @minisori, those packages are already updated.
2:1.5.99.902-0ubuntu3 is the new version. and in use.

I suggest using main server for upgrades.

I know, but the problem started in those updates and still remain with the ones you pointed out.

---

### Post by stovenator on 2009-02-06
Happened to me too, with Nvidia glx-180.27-0ubuntu1 .

If I ssh into the box (or ctrl-alt-F1 to a terminal) and kill -9 the PID for compiz-real , the desktop starts up fine.


I tried both 2:1.5.99.902-0ubuntu2 and 2:1.5.99.902-0ubuntu3 . Both updates broke for me.

I will play around with different NVidia drivers.

---

### Post by forumache on 2009-02-06
Same here.

After logon I get my wallpaper and nothing else and
X.org jumps to 70% CPU
compiz.real to 20%

I switch Ctrl-ALT-F1, kill compiz.real, desktop session starts

try to enable Desktop Effects, same problem.

Nvidia. Xorg. Compiz. All updated.

---

### Post by Timon&amp;Pumba on 2009-02-06
Confirmed, switched to metacity temporarily as well...

---

### Post by stovenator on 2009-02-06
Oh, and if it makes any difference, I'm on amd64.

If any developers are looking, I can get a stack trace if you need.

---

### Post by kris kincaid on 2009-02-06
This same thing has happened to me. Can anybody give the command line inputs to bypass compiz and the nvidia driver? Thanks.

---

### Post by stovenator on 2009-02-06
I just hit Ctrl-Alt-F1 , and logged in at a terminal session. At the terminal, I did:

computer1:~$ps ax|grep compiz.real
10094 ?   S   0:19 compiz.real --replace --sm-disable --ignore-desktop-hints ccp
10665 tty1    S+   0:00  grep compiz.real
computer1:~$kill -9 10094

Then I switched back to the Desktop with Ctrl-Alt-F7 . Of course it will happen again on the next reboot.

---

### Post by zenarcher on 2009-02-06
I'm also on the AMD64 bit system.  I'm using my test box, which has the older Nvidia FX5200 video card, as well.

Cheers,
zenarcher

---

### Post by kris kincaid on 2009-02-06
Thanks for the quick reply, that worked for me.

---

### Post by stovenator on 2009-02-06
I attached to compiz-real using gdb to see what was failing:

```
#16 0x0000000000418544 in addScreen ()
No symbol table info available.
#17 0x0000000000411bf8 in addDisplay ()
No symbol table info available.
#18 0x000000000040cf8a in main ()
No symbol table info available.
(gdb) r
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /usr/bin/compiz.real
/usr/bin/compiz.real (core) - Fatal: Couldn't open display
Program exited with code 01.

```

I trimmed out a lot from gdb, but obviously compiz can't figure out what display to attach to (or doesn't have permissions to open the display).

---

### Post by stovenator on 2009-02-06
I filed a bug at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/326366 ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/326366") for anybody wishing to follow this.

---

### Post by psychok9 on 2009-02-06
Same problem here :(

---

### Post by Salane on 2009-02-06
Thanks for the posts I will wait to upgrade for now.

---

### Post by Timon&amp;Pumba on 2009-02-07
Bug report [326344]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344") more specifically describes the cause of the problem. It seems that compiz conflicts with /dev/nvidiactl.
A workaround posted there is:

1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via killall compiz.real -s KILL
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz

---

### Post by plun on 2009-02-07
> **Timon&Pumba said:**
> Bug report [326344]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344") more specifically describes the cause of the problem. It seems that compiz conflicts with /dev/nvidiactl.
A workaround posted there is:

1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via killall compiz.real -s KILL
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz


Thanks !!!!

Works just fine but where is Ctrl-Alt-Backspace....):P

;)

---

### Post by todak on 2009-02-07
If you are using kubuntu with nvidia, start in recovery mode. Go to **xfix** and enter. After xfix does its thing you will be back at the menu to resume normal booting. Resume booting. Log in and go straight to system settings and select **Desktop**. Uncheck **Enable Desktop effects**. Exit System Settings. Go to **Applications> System> Hardware Drivers** and make sure the recommended driver is in use. If not, enable it and reboot (not into recovery mode). You will be able to log in to your desktop. However **DO NOT** re-enable desktop effects (at least until this is fixed) because as soon as you click **Apply** you will be immediately kicked out of your session to the monochrome background desktop with only a cursor and you will have to start the entire process over.

---

### Post by ronacc on 2009-02-07
> **plun said:**
> Thanks !!!!

Works just fine but where is Ctrl-Alt-Backspace....):P

;)

apearently this one fouls up the reading of xorg.conf ? I have the don'tzap option in my xorg but ctrl>alt>bkspc wouldn't work here had to go to term and kill it .

---

### Post by plun on 2009-02-07
> **ronacc said:**
> apearently this one fouls up the reading of xorg.conf ? I have the don'tzap option in my xorg but ctrl>alt>bkspc wouldn't work here had to go to term and kill it .

Yup.... just a "bloody" mess..

GDM > "Options" > restart  hard locks my PC

I uninstalled dkms, nvidia-glx-180 and installed nVidias driver  > recompiled Compiz and its still broken.

Also renamed compiz.real (usr/bin) for avoiding that binay to be a trouble maker, the compiz script cannot find any manageable screens)
 

```
metacity --replace
```

;)

---

### Post by psychok9 on 2009-02-07
Ctrl + alt + backspace is disabled on Jaunty-alpha. I don't remember how activate it, but this forum or google is a friend ;)

---

### Post by psychok9 on 2009-02-07
> **Timon&Pumba said:**
> Bug report [326344]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344") more specifically describes the cause of the problem. It seems that compiz conflicts with /dev/nvidiactl.
A workaround posted there is:

1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via killall compiz.real -s KILL
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz

This workaround is only for a single session?
I started gdm with a simple reconfigured xorg.conf (without effects/nvidia driver).

---

### Post by plun on 2009-02-07
> **psychok9 said:**
> Ctrl + alt + backspace is disabled on Jaunty-alpha. I don't remember how activate it, but this forum or google is a friend ;)

Yup... we knows that..:lolflag:

---

### Post by inportb on 2009-02-07
Heh... if they're gunna pack a buggy X server they might as well throw ctrl+alt+bksp in there too ;)

---

### Post by ubername on 2009-02-07
> **Timon&Pumba said:**
> Bug report [326344]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344") more specifically describes the cause of the problem. It seems that compiz conflicts with /dev/nvidiactl.
A workaround posted there is:

1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via killall compiz.real -s KILL
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz

Thanks, works like a charm. I would have changed step 5 to 'compiz --replace'. but I got there. Thanks again. I wish the Thanks button would come back to these forums.

---

### Post by medeshago on 2009-02-07
This is one of the reason why they shouldn't disable ctrl+alt+backspace.

---

### Post by taavikko on 2009-02-07
> **medeshago said:**
> This is one of the reason why they shouldn't disable ctrl+alt+backspace.

Offtopic->

How on earth does this has something to do with disabling C-A-B.
Killing xserver->restart->whoops, compiz is still running...

Switching to vty isn't that difficult to normal user.
Beginners may have difficulties, but hey, gotta learn it someday ;)

Helps if you know what you're doing with terminal, to rescue b0rked system... GUI isn't always available...

---

### Post by jfernyhough on 2009-02-07
The bug is with Nvidia and Compiz. There is another bug that means when nvidia is enabled CTRL-ALT-F1 gives a warm black screen and no terminal prompt. Hence, no way to easily recover from an xserver bork without the ability to zap.

IMHO, disabling zapping in the final release is probably fine, but for Alphas and the fact that Alphas are used by experienced users disabling zapping is at the least patronising if not counter-productive.

---

### Post by 3vi1 on 2009-02-07
> **jfernyhough said:**
> The bug is with Nvidia and Compiz.

I don't see how that's possible, since I see the same problem using KWin (locks up if desktop effects are enabled).

Also, I had already rebooted 2 or 3 days back to the new 180.27 nVida drivers + Compiz, and it was working fine.

---

### Post by jfernyhough on 2009-02-07
OK fine the bug's not just nvidia+Compiz. It's nvidia+xserver. But my point still stands. ;)

---

### Post by 3vi1 on 2009-02-07
> **jfernyhough said:**
> OK fine the bug's not just nvidia+Compiz. It's nvidia+xserver. But my point still stands. ;)

Fair enough.  :P

Hopefully they get this fixed soon.  I loves me some desktop effects.  Hehe.

---

### Post by TerminX on 2009-02-08
Seems like an X issue, downgrading X to 1.5.99.902-0ubuntu1 fixed the problem for me.

---

### Post by 0x656b694d on 2009-02-08
stovenator, that was because you had not passed the correct arguments to compiz, like the display number. i guess.

Compiz eats 100% cpu, but not exit with an error.

---

### Post by Kevbert on 2009-02-08
Even without compiz, the error may occur with the Nvidia drivers. If you hit Ctrl-Alt-F1, log-in at the prompt and run
```
top
```
you may find kwin and xorg take up 100% of your processes.

---

### Post by Streeterer on 2009-02-08
This killed my session as well. How might I downgrade the xserver to 1.5.99.902-0ubuntu1?

---

### Post by Perpetual on 2009-02-08
I really wish that desktop effects were not enabled automatically.  That annoys me greatly.

---

### Post by cariboo on 2009-02-08
I uninstalled any mention of nvidia using sysnaptic, then moved xorg,conf to xorg.conf.bak, used the dontzap applet, just in case and rebooted my system.

It started with that minimal xorg.conf file, I played with it for an hour or two and nothing went wrong, so I enabled the Nvidia driver using System-->Administration-->Hardware Drivers, I used Ctrl-Alt-Backsapce to restart the server.

I did this yesterday afternoon and have rebooted several times just to check. I'm using 180.27 and compiz with no lock ups, other ill affects.

Jim

---

### Post by minisori on 2009-02-08
> **Streeterer said:**
> This killed my session as well. How might I downgrade the xserver to 1.5.99.902-0ubuntu1?


Look at the first post in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344)

---

### Post by lusephur on 2009-02-09
follow the link above in minisori's post
download the deb file for your system, it's either ix86 or amd64
open a console, navigate to where you downloaded the file Desktop or home

type 
> sudo dpkg -i packagename.deb

reboot 

and you should be sorted

alternatively instead of downloading, you might find the deb in var/cache/apt/archives

hope this helps as much as this thread helped me when i was trying to find out what was causing my issues last friday.

---

### Post by lusephur on 2009-02-09
also you might want to lock the ubuntu1 version of xserver-xorg-core for a while till a newer bugfixed version is released

---

### Post by lusephur on 2009-02-09
edit, double post, sorry.
moderators, please remove this

---

### Post by kde4-core-user on 2009-02-09
> **lusephur said:**
> also you might want to lock the ubuntu1 version of xserver-xorg-core for a while till a newer bugfixed version is released

There is no need to downgrade or lock. All you have to do is 'disable direct rendering' before activating the effects. It work for kwin & compiz.

>> This bug was fixed in the package xorg-server - 2:1.5.99.902-0ubuntu5 <<

I hope this will fix the issue completely, but by now only ubuntu4 is in repository.

---

### Post by stovenator on 2009-02-09
2:1.5.99.902-0ubuntu5 is built and should show up in the repositories sometime tonight. This build should fix the issue - I'm hoping :-)

---

### Post by minisori on 2009-02-09
Yes, it's fixed :D

---

### Post by Streeterer on 2009-02-09
I am actually still having trouble, Ubuntu still starts in low-graphics mode, even with the IgnoreABI flag on.

---

### Post by todak on 2009-02-09
Still not fixed on my system running kubuntu with nvidia FX5200. I have to revert to the older version of xorg or disable effects.

---

### Post by ugkbunb on 2009-02-10
fixed with version ubuntu5 in the repos

---

### Post by plun on 2009-02-10
> **todak said:**
> Still not fixed on my system running kubuntu with nvidia FX5200. I have to revert to the older version of xorg or disable effects.

Yup, still broken also for me

```
plun@plun:~/compiz$ compiz --replace
compiz (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
compiz (core) - Fatal: No manageable screens found on display :0.0

```

EDIT Solved.... drivers mess.... 180.27 and 29

---

