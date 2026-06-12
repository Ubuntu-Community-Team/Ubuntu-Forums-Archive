---
title: "Natty install, will only boot once after install"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2011-04-28
I've installed 11.04 64bit several times, and here's what happens. On install and reboot, seems to work fine. Then on 2nd boot, 2 things:

1) grub has changed, the count-down counter is gone.
2) will not boot in normal mode, I have to boot in reduced graphics mode, and even then only boots about 50% of the time, and then hangs on shut down.

Help! I'm running 10.10, and it's got problems on my new laptop too, and was hoping 11.04 would get me where I need to be. I do NOT want to go back to windows.

Some more info:
Dell Vostro 3550, with Intel i3, and Radeon discrete graphics.
3GB DRAM

---

### Post by mörgæs on 2011-04-28
How does the 32 bit version work?

---

### Post by aeronutt on 2011-04-28
Good question. Just loaded the 32b version. :)
Nearly same problem. Booted fine after initial load. It did reboot ok 2-3 times (and at grub, had the count down counter). But on 3rd or so boot, count down time gone, and hung during boot process.

Very odd, what could be changing grub w/o manually changing grub files and running update???  Obviously, something else wrong too.


I get the feeling this all has something to do with having 2 graphics processors, and integrated one and a discrete one. But I thought I was ok as long as I didn't try to load the radeon fglrx proprietary driver.  Could that be the problem....2 graphics?  Anyway I can fix that?

---

### Post by stormelf on 2011-04-28
I am having a similar problem.

Black screen on every other boot.

After doing Ctrl+Alt+Del on the black screen it seems to boots normally again the next time.

I can not remember having this problem during Alpha 3.

I suspect it was introduced during beta1 or beta2.

Annoying bug.

Dell laptop with 64bit.

---

### Post by aeronutt on 2011-04-28
> **stormelf said:**
> I am having a similar problem.

Black screen on every other boot.

After doing Ctrl+Alt+Del on the black screen it seems to boots normally again the next time.

I can not remember having this problem during Alpha 3.

I suspect it was introduced during beta1 or beta2.

Annoying bug.

Dell laptop with 64bit.

Interesting. I've been seeing this problem since trying beta2 (didn't try Natty prior to that).

Do you have dual graphics? Which processor do you have?

Update, the only way I can get out of the blank screen is to power off.
Also, even if I run update-grub (after booting in low graphics mode), when I reboot, the grub screen does not have the countdown counter. Very screwed up.

---

### Post by aeronutt on 2011-04-28
Found this web site:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Turned OFF radeon graphics by changing line in /etc/default/grub to :
GRUB_CMDLINE_LINUX_DEFAULT=radeon.modeset=0


Have now booted 5 times no problems. (Although boots slower).
Who know if I'm using the integrated Intel graphics. Need to figure that out. I don't like this solution though, $100 worth of graphics acceleration unusable unless I boot into windows.

---

### Post by mörgæs on 2011-04-29
It seems like a bug worth reporting in Launchpad.

---

### Post by aeronutt on 2011-04-29
> **mörgæs said:**
> It seems like a bug worth reporting in Launchpad.

Will do that. 

FYI, I've started a separate thread on my graphics problem:
[http://ubuntuforums.org/showthread.php?p=10738107#post10738107](http://ubuntuforums.org/showthread.php?p=10738107#post10738107)

---

### Post by doorunrun on 2011-04-29
I'm having a similar problem on Natty 64-bit server running on VMware (as you know, no GUI).

I found the other console logons (alt-F1, F2, F3...) are working but going back to the primary, alt-F7, the system seems to be hung.
I though it might be a VWware Tools issue, but removing them does not solve the problem.

Anybody else notice this?

---

