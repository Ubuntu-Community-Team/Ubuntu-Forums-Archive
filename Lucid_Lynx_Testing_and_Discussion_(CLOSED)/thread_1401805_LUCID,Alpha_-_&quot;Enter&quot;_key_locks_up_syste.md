---
title: "LUCID,Alpha - &quot;Enter&quot; key locks up system."
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jfath on 2010-01-18
I'm running Lucid on two different machines, both with latest updates as of 2010-01-18 including Xorg 1.7.3.902-1ubuntu8.

One system is a full Kubuntu install with a GeForce 9500 GT running nvidia-current drivers.  Everything works great here.

The other system is a 32 bit minimal install running LXDE and using SLiM as the DM.  The graphics hardware is an integrated GeForce 6150.  On this system, I've tried nvidia-current as well as the nv and vesa drivers.  No matter which driver is running, the system boots correctly and will run all programs UNTIL I press the Enter key.  Then, I get an immediate system freeze.  If I login to the system using ssh, I see that xorg is consuming 100% of one of the CPU cores and the following lines were added to Xorg.0.log when the crash occurred:
-----------------------------------------------
Backtrace:
0: /usr/bin/X11/X (xorg_backtrace+0x3b) [0x80e874b]
1: /usr/bin/X11/X (0x8048000+0x61a1d) [0x80a9a1d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x3bd410]
3: /usr/bin/X11/X (0x8048000+0x2a0e0) [0x80720e0]
4: /usr/bin/X11/X (0x8048000+0x1ed4a) [0x8066d4a]
5: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x3d4bd6]
6: /usr/bin/X11/X (0x8048000+0x1e931) [0x8066931]

Caught signal 3 (Quit). Server aborting

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) "Power Button": Close
(II) UnloadModule: "evdev"
(II) "Power Button": Close
(II) UnloadModule: "evdev"
(II) "AT Translated Set 2 keyboard": Close
(II) UnloadModule: "evdev"
(II) "ImExPS/2 Generic Explorer Mouse": Close
(II) UnloadModule: "evdev"
(II) "Macintosh mouse button emulation": Close
(II) UnloadModule: "evdev"
---------------------------------------------------------------------------

I did some searching and did find an ArchLinux bug report that sounds similar at [http://bugs.archlinux.org/task/17472](http://bugs.archlinux.org/task/17472).

I should also note that this system was running without problems until the latest kernel/xorg updates.

I know this should probably be filed as a bug report, but I wanted to post here first to see if anyone else has seen anything similar and whether there are any ideas for work-arounds?

Thanks.

---

### Post by dino99 on 2010-01-18
have seen the Arch bug report started 3 weeks ago, it looks like yours and i'm curious no one with ubuntu fall on this:

better to report on launchpad, as it's a show stopper.

---

### Post by dino99 on 2010-01-18
Maybe you can look at warnings in logs to fight this bug.

Some thinkings:
- can you set custom settings for keyboard
- try to remove/purge xorg, xserver* ; then reinstall them (don't reboot when removed !!!)

---

### Post by jfath on 2010-01-18
Looks like it's related to SLiM (1.3.1-4).  I switched the system to GDM and the problem went away.

---

### Post by Ibidem on 2010-01-18
I can tell it is not just SLiM.  Running IceWM +PCManFM +SLiM+the Intel drivers, I don't
see any issues of the sort (~6 hours uptime right now).
Ibidem

---

### Post by balduin on 2010-02-05
[https://bugs.launchpad.net/xorg-server/+bug/516472](https://bugs.launchpad.net/xorg-server/+bug/516472)

---

### Post by MacUntu on 2010-02-05
> **balduin said:**
> [https://bugs.launchpad.net/xorg-server/+bug/516472](https://bugs.launchpad.net/xorg-server/+bug/516472)

How about [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412) ;)

---

### Post by kaitwospirit on 2010-02-05
I had this earlier today. Definitely not related to SLIM, as I'm not using that at all. But mysteriously, somehow, updates fixed it.

I question nothing.

---

### Post by donniezazen on 2010-02-06
I am still having the same problem. I am also automatically logged off.

---

### Post by ruik on 2010-02-06
Having the same problem here too! :)

---

### Post by infoseeker on 2010-02-06
My Ubuntu and Kubuntu Lucid are now BOTH broken...oh well, they were only testing versions.

---

### Post by BackwardsDown on 2010-02-06
I had the same issue, an 'sudo aptitude remove plymouth' is a good workaround.

---

### Post by phenest on 2010-02-06
> **BackwardsDown said:**
> I had the same issue, an 'sudo aptitude remove plymouth' is a good workaround.

Yep, that's what I did too. No problems since.

---

### Post by EddieRingle on 2010-02-06
Had this problem after updating Plymouth to 0.8.0~-9 via the Update Manager.
Removed the package, rebooted, and the problem disappeared.

---

### Post by tad1073 on 2010-02-06
same problem here but only when I restart.

When I restart my computer I get the freeze, but if I shut it down then reboot it doesn't happen.

Kind of odd if you ask me.

---

### Post by dovernh on 2010-02-08
I just upgraded to 10.04 LTS using update-manager -d.  My desktop is a dell 9100 64bit pc.  Everything is working fine, except when I use the enter button instead of using the mouse to click on any dialog "accept" button.  For example when logging in, I click the user to log in, then enter my password.  If I press enter, the computer locks up.  If I instead click the "login" button, everything is fine.  It's the same with getting updates with update manager.  Is anybody experiencing this problem?

---

### Post by proxess on 2010-02-08
That's the most amazing problem I've ever seen. I've never heard nothing like it and have no idea how to fix it. I'm sorry.

---

### Post by emarkay on 2010-02-08
From the initial login to opening FF and using a message board, the 'ENTER' key freezes everything - power off is the only solution.

I have seen this for a few days, bit now only confirmed that that is the issue.

Anyone elses notice this?  This is a new clean install of Alpha2, updated daily.

This may or may NOT be related to this:
[http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)

---

### Post by rbmorse on 2010-02-08
I did a last ditch attempt to get things going again when that happened to me yesterday.

Reboot into "recovery" mode, then

apt-get update
apt-get dist-upgrade

You'll be asked if you really, really want to do this...check the number of packages to be removed. In my case it was just two,  so I let it go ahead.  System not works as normally as it can at this stage in development.

---

### Post by drs305 on 2010-02-08
> **emarkay said:**
> From the initial login to opening FF and using a message board, the 'ENTER' key freezes everything - power off is the only solution.

I have seen this for a few days, bit now only confirmed that that is the issue.

Anyone elses notice this?  This is a new clean install of Alpha2, updated daily.

This may or may NOT be related to this:
[http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)

I had similar issues. I uninstalled plymouth and the freezes stopped. On my system, it initially manifested itself as you describe but eventually failed even to complete the boot process. You might just try uninstalling plymouth to see if it solves things.

---

### Post by tad1073 on 2010-02-08
[http://ubuntuforums.org/showthread.php?t=1396912](http://ubuntuforums.org/showthread.php?t=1396912)

---

### Post by emarkay on 2010-02-08
> **rbmorse said:**
> I did a last ditch attempt to get things going again when that happened to me yesterday.
Reboot into "recovery" mode, then
apt-get update
apt-get dist-upgrade
You'll be asked if you really, really want to do this...check the number of packages to be removed. In my case it was just two,  so I let it go ahead.  System not works as normally as it can at this stage in development.

I do this frequently, not "dist-upgrade", but "upgrade".  Otherwise, as of an hour ago, it's still locking up.

---

### Post by emarkay on 2010-02-08
> **tad1073 said:**
> [http://ubuntuforums.org/showthread.php?t=1396912](http://ubuntuforums.org/showthread.php?t=1396912)

What does this have to do with anything?  Please elaborate!

---

### Post by saracen on 2010-02-08
ya just uninstall the 'plymouth' package - the problem will disappear after.  Just remember to reinstall it later when they fix the problem.

---

### Post by emarkay on 2010-02-08
> **drs305 said:**
> I had similar issues. I uninstalled plymouth and the freezes stopped. On my system, it initially manifested itself as you describe but eventually failed even to complete the boot process. You might just try uninstalling plymouth to see if it solves things.


I understand that at his stage Plymouth is AFU, but I did not know one could uninstall it - is that something appropriate for Alpha testing?

I can live with the hanging as updates are made (I have Karmic to use for things like reality work) but wonder if this is a bug, or just something in process of development.

---

### Post by phenest on 2010-02-08
Launchpad [bug 516412]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412").

This is a known and common problem. Please use the forums search feature. You will discover several threads about this.

---

### Post by drs305 on 2010-02-08
> **emarkay said:**
> I understand that at his stage Plymouth is AFU, but I did not know one could uninstall it - is that something appropriate for Alpha testing?

I can live with the hanging as updates are made (I have Karmic to use for things like reality work) but wonder if this is a bug, or just something in process of development.

I think your questions are now answered. There is a bug (I added to it a few days ago). You can uninstall plymouth. The most important thing is to get a problem documented via a bug report. 

At least in my case, the only way I was going to be able to continue to test and report was to get the system working again. ;-)

---

### Post by cariboo on 2010-02-08
I had a problem where the system locked up at the login screen after pressing enter. Starting in recovery mode and doing:

```
aptitude safe-upgrade
```

seemed to solve the problem, but on the next reboot, it was back. Doing the upgrade from the recovery console again solved the problem, but on the next boot it locked up again. Removing plymouth solved the problem. 

I run an Nvidia 8400gs in that system.

---

### Post by jppr on 2010-02-08
That problem is gone. I install plymouth back and everything works now fine, i run system nvidia 7600 gs

---

### Post by drs305 on 2010-02-08
> **jppr said:**
> That problem is gone. I install plymouth back and everything works now fine, i run system nvidia 7600 gs

I also have a GS 7600. I reinstalled plymouth and for the first time in a week or so it booted. I restarted the machine and on the second boot I got to the Desktop but then the system froze as soon as I pressed ENTER. Repeated on the next boot.

So for me at least, there is progress. The system now boots, but the freeze still occurs when I press ENTER after booting. I've uninstalled plymouth once again.

---

### Post by plun on 2010-02-08
Yup, started my nVidia 8600 desktop and it froze directly when I pressed enter.....  

Ok with plymouth removed.

---

### Post by cariboo on 2010-02-08
Moved from General Help

---

### Post by hikaricore on 2010-02-08
[http://ubuntuforums.org/showthread.php?t=1401805](http://ubuntuforums.org/showthread.php?t=1401805)

---

### Post by Starks on 2010-02-08
I have an i945gm.

This doesn't happen to me every time I press enter. When it does happen, X restarts.

Why does this happen though?

---

### Post by whinis on 2010-02-08
I have the same problem and i thought the update fixed it but after a wierd xorg restart i realized that xorg ends up crashing and restarting. After the restart the enter key works perfectly.

---

### Post by emarkay on 2010-02-09
Freak me out!  Did someone merge this thread or what?

I prefer the "see this thread..." type of notes - this is sort of like rewriting history.

---

### Post by pvfloripa on 2010-02-09
One question, though:

how can I remove the plymouth package without the need to press the enter key??

Unfortunately when I try to do it using the GUI version of package manager, it also freezes.

Thanks for any hints.

---

### Post by plun on 2010-02-09
> **pvfloripa said:**
> One question, though:

how can I remove the plymouth package without the need to press the enter key??


Boot into rescue mode and uninstalll

```
apt-get remove plymouth
```


EDIT and Ctrl-Alt-Del for reboot

;)

--

---

### Post by MacUntu on 2010-02-10
[COLOR="Red"]**Please help to fix the bug:**[/COLOR]

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412)

---

### Post by saracen on 2010-02-12
Has this been fixed - according to the bug report on launchpad it says "Fix released".  Can anyone confirm that this is no longer an issue?

---

### Post by VMC on 2010-02-12
> **saracen said:**
> Has this been fixed - according to the bug report on launchpad it says "Fix released".  Can anyone confirm that this is no longer an issue?

I never had the "key" freeze issue. Mine is the plain old freeze, right after "fsck" check.

Remember, if you think its fixed you may be under a false assumption. It took me the 4th re-boot for it to freeze!

---

### Post by cariboo on 2010-02-12
It always takes a while after a fix has been released to go through the build farm and then propagate through the repositories. Please be patient.

---

### Post by DToNAToR on 2010-02-13
when booting in normal mode, lucid freezes when I first press Enter in gnome.

A way around this is booting into "recovery mode", asking it to throw me into the root shell and running `service gdm start'

what are my possibilities to debug this? How to force ubuntu to throw me into a good old "screen of death" (in any color you want) instead of leaving me in front of a static picture of my desktop?

---

### Post by Elfy on 2010-02-13
I had this causing this issue = [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412/](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412/)

---

### Post by AlanR8 on 2010-02-13
This happens to me on my newly installed Lucid daily build as of 09-02-10, fully updated.

Boots normally, although not very elegantly, to the log on screen. When I press return to enter my password everything locks up solid.

My workaround is to kill the X session by pressing Alt+SysRq+K. The screen goes black and flickers with random blocks of colour followed by the log on screen reappearing.

This time I can log on as normal.

---

### Post by 23meg on 2010-02-13
Threads merged. Please do a search before starting new threads.

---

### Post by Trespasser on 2010-02-13
I've gotten the same behavior as well. Locks up solid. Have to shut it down via the power button. This is on a Lenovo G530 laptop. Mainly Intel components.

---

### Post by AlanR8 on 2010-02-13
Try my solution in post 45 above. Let me know how you get on

---

### Post by b4rt on 2010-02-13
Hi,

It's been about 2 weeks now, I can't log in to my Lucid box, only on very rare occasions... When the login screen is loading, I can move my mouse around, but at a certain point it just freezes, I can't move my mouse, or use the keyboard to log in. I have used recovery mode to install updates almost every day.

Anyone else noticed this? Is this a known bug? A workaround maybe?

My regards,

Bart G.

---

### Post by Didius Falco on 2010-02-13
I've had the Enter key lock-up, but much more frequently, it just locks up before you even get to the log-in screen - it does still play the little drums sound before locking up.

The only thing I've tried that allows a successful boot-up is to remove plymouth.

I've noticed that most of the posts seem to be from Nvidia users -  my graphics card is an ATI Radeon HD 4870.

---

### Post by Alexandre Putt on 2010-02-13
I had a similar problem with the keyboard and the usb mouse not working after an update, but it was fixed by running apt-get upgrade from the recovery mode.

---

### Post by b4rt on 2010-02-13
Thanks for the reply. Hanging a USB mouse to my laptop doesn't work either... I'm on a Dell Latitude E6500.

---

### Post by Alexandre Putt on 2010-02-13
> **b4rt said:**
> Thanks for the reply. Hanging a USB mouse to my laptop doesn't work either... I'm on a Dell Latitude E6500.

If the keyboard works in the recovery mode and does not work in the login window, then there should be hope for fixing it. In my case I suspect there was a problem with the udev package, but I am not knowledgeable enough to be sure.

Why don't you try playing with apt-get options? Just login with two terminals (switch with alt-f1 / alt-f2 etc.), run in one man apt-get and try to fix the problem by invoking different options. It may be a dependency or configuration problem. As I said, it was fixed in my case by upgrading the system. In your case you may try reinstalling usb related stuff. There is scope for experimenting.

---

### Post by Trespasser on 2010-02-14
> **AlanR8 said:**
> Try my solution in post 45 above. Let me know how you get on

Thanks, dude. The Alt+SysRq+K allows me unfreeze my system and login back to a functioning system. Nice workaround. Beats the heck out of a hard shutdown.

---

### Post by mynimal on 2010-02-14
Same problem here. I get to the login screen, and sometimes I can move around my mouse (and probably type but I haven't had the right reaction time yet) but it promptly stops accepting input. Also, none of the keyboard lights come on indicating it's not even powering the device.

At first I figured it was to do with the removal of HAL since I still had it installed from Karmic, so I removed that. Bootup is crazy fast, but it's still not working.

I can, however, boot into recovery mode and start GDM from there and everything works fine.

---

### Post by b4rt on 2010-02-14
> **mynimal said:**
> Same problem here. I get to the login screen, and sometimes I can move around my mouse (and probably type but I haven't had the right reaction time yet) but it promptly stops accepting input. Also, none of the keyboard lights come on indicating it's not even powering the device.

At first I figured it was to do with the removal of HAL since I still had it installed from Karmic, so I removed that. Bootup is crazy fast, but it's still not working.

I can, however, boot into recovery mode and start GDM from there and everything works fine.

Hmm, booting into recovery and then resume normal boot does not work here, it's stuck...

Ideas?

Greetz,

Bart G.

---

### Post by mynimal on 2010-02-14
> **b4rt said:**
> Hmm, booting into recovery and then resume normal boot does not work here, it's stuck...

Ideas?

Greetz,

Bart G.

What I did was select netboot, and then run gdm from the console there.

---

### Post by b4rt on 2010-02-14
> **mynimal said:**
> What I did was select netboot, and then run gdm from the console there.

Nope, no luck here :(

---

### Post by cariboo on 2010-02-14
Moved from General help. I plan on merging this with the other threads when I have time.

**Edit:** It's now time, merged.

---

### Post by Ibidem on 2010-02-15
> **b4rt said:**
> Nope, no luck here :(

Can't go further or don't have mouse and keyboard?
If you can't get further, you could boot into text mode (cheater's way: edit kernel options in Grub at boot, appending: rw init=/bin/bash) and run startx or gdm...but X might not work, or gdm.

---

### Post by gunnar123 on 2010-02-15
I removed my post. Did not solve issue.

---

### Post by VMC on 2010-02-15
> **gunnar123 said:**
> From what I understand a solution has been posted here?:
[https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.0~-9](https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.0~-9)

I got rid of the issue on my laptop by removing plymouth, then reinstalled from the binary build debs you can access from there.

These are the four .deb files listed under each architecture.
First uninstall plymouth,
I found the safest way to get to a working command prompt once logged into X was to run "Log Out...", then select your username at the login console,
You should see a panel at the bottom of the screen where you find a "Sessions" dropdown menu. Instead of "GNOME", select "xterm" and then log in.
You arrive at a small xterm console and here you can remove plymouth:
sudo apt-get remove plymouth

Then install suitable debs from files you have downloaded
(in my case I need the 64-bit builds):
dpkg -i libplymouth2_0.8.0~-9_amd64.deb
dpkg -i libplymouth-dev_0.8.0~-9_amd64.deb
dpkg -i plymouth_0.8.0~-9_amd64.deb
dpkg -i plymouth-x11_0.8.0~-9_amd64.deb

Then reboot and things should be working, at least did for me.

I get lucid fast boots on an ASUS UL50VT with a Corsair P128 SSD...

The plymouth you removed was it 10?

```
 aptitude show plymouth
Package: plymouth
State: installed
Automatically installed: no
Version: **0.8.0~-10**
```

the one you reference is older "~.9"

---

### Post by gunnar123 on 2010-02-15
Yes my post was all useless. Somehow it all looked ok when I tried it.
Now when I try again, same lockup and as you point out; not an upgrade.
Please ignore, post removed. So seems the fix for now is plymouth removal until sorted out by those concerned.

---

### Post by jrevillini on 2010-03-07
Here's the real question ... exactly how do we report this?  I know there's a bug thread at launchpad, but which logs would have the information we should be posting to the launchpad thread to help them narrow down the cause.  Mine is a little different ... I boot up and I have it auto-login as my account (is that the case for all of you, by the way?), and whatever the first time is that I press ENTER, it crashes gnome and brings me tot he login screen.  So it's almost like ENTER acts like the CTRL+ALT+SysReq combo after the auto-login, but then I just log in and everything is fine until I restart.

---

