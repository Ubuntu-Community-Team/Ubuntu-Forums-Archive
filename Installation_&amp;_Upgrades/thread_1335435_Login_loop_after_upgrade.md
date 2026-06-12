---
title: "Login loop after upgrade"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by cincytee on 2009-11-23
I have Ubuntu installed on a partition of a dual-boot (XP) Dell Optiplex GX110. All was happy. I recently upgraded from 9.04 to 9.10; now I regularly (though not always) have a problem starting up. System loads to login screen fine. I enter password, screen goes dark for a moment, then an off-center splash screen briefly appears. Then terminal readout reports "lockup", then I am sent back to the login screen. Further login attempts repeat this process, generating the further terminal message: "space 65520, wanted 65528". Sometimes the startup jingle starts and gets stuck midway, too. Repeated attempts sometimes lead to successful login. I have run updater a few times and re-installed gdm package; no improvement.

---

### Post by lemming465 on 2009-11-24
Is there any difference between cold (from poweroff) and warm (from reset/reboot) boots?  If one of them works better than the other, stick to the good style.  If the answer is cold boots, look for a BIOS upgrade.

Your symptom sounds like a bug in the X support for your video chip, which given the amount of churn in the intel X video driver, is distressingly likely.  You could try searching for your video chip (find that in the output of *lspci -vv*) on bugs.launchpad.net to see if anyone else has a workaround suggestion, e.g. some kernel boot parameter.  Switching to the VESA driver in your /etc/X11/xorg.conf file might also work, though performance and screen resolution might suffer.  Or reinstall 9.04 if that was more stable (there is no easy downgrade from an upgrade, alas).

---

### Post by cincytee on 2009-12-15
Doesn't seem to matter whether it's warm or cold boot. It sometimes helps to restart after a few login failures, but that's not consistent, either. Over time, I have had time to get the error message in more detail. It's:

[xx.yy][drm:i810_wait_ring] *ERROR* lockup
[xx.yy][drm:i810_wait_ring] *ERROR* space 65520, wanted 65528

The [xx.yy] are a numeric pair which changes with each attempt; the rest remains identical. The norm now is for about a dozen attempts before I can log on. More is not rare. Any ideas?

---

### Post by simple simon on 2009-12-17
I too have this problem.  My history is:

1) clean 9.10 install
2) login with no problems
3) select all updates
4) reboot 
5) fail to login as described in the first post

6) fresh reinstall again
7) system is stable it seems (many logins)
8 ) start to update bit by bit seems ok
9) after all updates reboot
10) back to fail to login as described in the first post

However, if I select failsaife boot option in grub, select continue with normal boot, I can login on the command line and do startx and all is fine.

Is it GDM that is broken?

Simple.

---

### Post by cincytee on 2009-12-22
I am now basically unable to log in at all. I've let this loop run through this loop more than 20 attempts, I've restarted, I've tried failsafe mode. All resulted in no change: login chokes at last second and bounces me back to beginning. The irony that I have to boot into Windows to get a stable system is not lost on me. Further, this glitch does not seem to be unique. Is a fix not in the works?

---

### Post by mgan on 2009-12-22
I'm having this issue as well now after a few weeks of ubuntu and having upgraded my install.

My configuration:

Macbook Pro (most recent model)
Snow Leopard
Vmware Fusion
Ubunutu 9.10

I now have this login loop occurring on every restart of my vmware.  Also, on some successful logins I now have an error message awaiting me about my evolution_alarm_clock.

---

### Post by Psumi on 2009-12-22
Anything can make a login loop happen in 9.10 actually, there is a bug on it on XFCE.org, but it may be related to something other than XFCE.

Some things that may cause it:

-- Resolution Changing
-- Installing GNOME2-Global Menu

---

### Post by &lt;mike&gt; on 2009-12-27
I also have this error after changing screen res for one user. Gnome has stopped working, but xfce still works. Other users also work.

any ideas on how to fix it??

---

### Post by Psumi on 2009-12-27
> **<mike> said:**
> I also have this error after changing screen res for one user. Gnome has stopped working, but xfce still works. Other users also work.

any ideas on how to fix it??

1.) Get into a tty terminal by pressing CRTL+ALT+F1.

2.) Login to the terminal. (It will ask you for your username/password. THE CURSOR WILL NOT MOVE WHEN YOU TYPE YOUR PASSWORD, THIS IS NORMAL.)

4.) sudo stop gdm (or sudo /etc/init.d/gdm stop)

3.) sudo apt-get purge gdm

4.) sudo apt-get install wdm

5.) sudo reboot now

When you startup, you will see a really ugly looking login screen. However, since normal users can't fix the issue with gdm, and the developers don't seem to care one bit about it, this is the only workaround for us.

---

### Post by resisthegemony on 2010-01-03
My original problem was this: I logged in, the system would accept the password...and then proceed to bring me back to the log in screen. I tried the previous fix to no avail, so I booted from my first hard disk using the Ubuntu installation CD. Now everything is working perfectly (I restarted to check), but I'm stuck with the ugly login screen. Aesthetics aren't all that important now that my computer works--but is there a way to get back to the original login screen or bypass it altogether? 

If it's probably better to leave it, I'll probably stick with that. I'm more curious as to why my 9.10 would have such a problematic login...any suggestions? :-/

---

### Post by &lt;mike&gt; on 2010-01-04
i fixed my problem by undoing my screen res change (manually editing the monitors.xml file in ~/.gnome2/ and ~/.config/). Damn, i am stuck at 1600 x 1200, 60Hz... good for me, but my wife is constantly squinting...

---

### Post by Bean Street on 2010-01-05
Hey this might help:   I installed 9.10 got stuck in this time loop, and searched widely for rescue.  Thank you all very, very much.

My config is: Snow Leopard; VMware Fusion 3.0.1, Ubuntu 9.1.0 (Karmic)

I was stuck due to my changing the monitor resolution, but I got in through GNOME failsafe (took two tries), and then set my res.  First I scaled down to 1024x768, still looped.  Then I tried the stock resolution of 800x600.  Now no resize occurs during login, and now no loop.  And since Fusion can still go to Full Screen mode, it works ok.
Pretty fair guess that the trouble is happening during/etc the re-size

CIAO

---

### Post by danielpalos on 2010-01-05
Request for opinions.

I make a motion that the login requirement should be not be installed by default in order to better meet the intent of the public domain; but set so that it can easily be installed if that functionality is required in the appropriate menu panel.

---

### Post by sirlancalot on 2010-01-15
:KS> **Psumi said:**
> 1.) Get into a tty terminal by pressing CRTL+ALT+F1.
 
2.) Login to the terminal. (It will ask you for your username/password. THE CURSOR WILL NOT MOVE WHEN YOU TYPE YOUR PASSWORD, THIS IS NORMAL.)
 
4.) sudo stop gdm (or sudo /etc/init.d/gdm stop)
 
3.) sudo apt-get purge gdm
 
4.) sudo apt-get install wdm
 
5.) sudo reboot now
 
When you startup, you will see a really ugly looking login screen. However, since normal users can't fix the issue with gdm, and the developers don't seem to care one bit about it, this is the only workaround for us.
 
I am a Ubuntu newbie and am very grateful for Psumi's post and the rest the info shared in this forum. These steps worked like a charm for me. The login loop happened to me after performing my first batch of updates in update manager for Xubuntu 9.1 and then restarting.  I don't know if the Gnome2-Global menu was listed as one of the initial updates.

---

### Post by cincytee on 2010-04-08
Imperfect solution, reported in a not-at-all timely fashion: I finally got logged in and, on a hunch based on other threads, returned my screen resolution to its default setting. I haven't had a problem since ... except of course that I can barely read a good chunk of on-screen text.

---

### Post by Psumi on 2010-04-08
> **cincytee said:**
> Imperfect solution, reported in a not-at-all timely fashion: I finally got logged in and, on a hunch based on other threads, returned my screen resolution to its default setting. I haven't had a problem since ... except of course that I can barely read a good chunk of on-screen text.

In lucid, there will be a better looking *DM, called slim that can replace what I chose to give people (wdm.)

If you're on lucid, and still have the issue, use slim instead, it's much better looking.

---

