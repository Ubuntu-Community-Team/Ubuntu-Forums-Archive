---
title: "SLOW network, startup, apps in Edgy"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by msfisher on 2007-04-07
Since my earlier thread in Absolute Beginner seems to have fallen by the wayside with little to show for it, I figured I&#8217;d start a new one here.  Please note that I&#8217;m only a beginner to Ubuntu.  I have some experience (see below) in other Linux distros and extensive experience with Microsoft OS&#8217;s (from clear back in DOS).  

I&#8217;ve been searching the forums here, newsgroups and the web in general about this.  For example, enter the two words slow network into the forum search box and a long list of threads will show, so I know that others have had similar problems.

Since there are so many threads, I&#8217;m not going to try to link to them.  

To reiterate my own problem:  When I first managed to get Ubuntu installed using the Alternate CD (due to an inability for Ubiquity to properly recognize a root mount point, a bug that has been reported) I logged in as oem.  The interface came up properly, but when I tried to run the updates I found that the network was running VERY slowly (a low of 780Bps to a high of 18KBps, average about 7KBps as shown by the update monitor).  The same was true of Internet usage.  After the updates completed (four hours) I went ahead set up a new username.  When I logged back in, I noticed that the interface came up VERY slowly.  Ten or twelve seconds to see the wallpaper, five or so for the desktop icons to appear (active) another fifteen for the Gnome panels to open (no icons), another fifteen for the panel icons to appear (inactive) and another fifteen for the icons to activate.  Even then, applications took unreasonably long times to open.  A console did not even open completely.  After ten or fifteen minutes, applications start normally, including the console.  I tried shutting down ipv6 in both Firefox and through aliases with no effect on either network speed or startup behavior.

My system is a multiple boot Sempron 2600, 512megs memory, MSI motherboard with Nvidia nforce3 250 chipset, Nvidia Geforce2 MX400 viideo with 64megs, Realtek 8139 on-motherboard NIC.  I had bad experiences trying to switch, via dual booting, to XP.  I&#8217;ve also tried Mandrake/Mandriva in versions before 2006.  I want to move away from Windows, but want to keep my game access, so I not only have kept the Win98 boot, but also added Xandros 3 for its Windows parts.  I saw no network problems at all with Xandros or Win98.  When I tried Mandriva 2006 and later 2007 (but NOT earlier versions down to Mandrake 8.1), I saw the same slow network problem as I&#8217;m seeing with Ubuntu (it&#8217;s why I decided to try Ubuntu).  I did not see the interface problem, though if it were related to Gnome, it would not occur under Mandriva, which uses KDE.

There doesn&#8217;t seem to be a consensus regarding either the source or solution to the two problems, but the threads seem to fall into the following groups:

1.	Some incompatibility in the newest kernel used by Edgy and Feisty (2.6.17-11)
2.	A changed network setting in the newest updates (mostly wireless, but wired too)
3.	A problem relating to Gnome Display Manager (gdm)
4.	An incompatible video driver (primarily ATI)
5.	ipv6 incompatibilities
6.	hosts

I&#8217;ve seen this discussed for 6.10 and the 7.0 beta, but not the older version(s) like 6.06, so one of the first two items above may be the problem.  

I&#8217;d prefer to fix the problem rather than installing the older Ubuntu version, though I&#8217;m not adverse to either installing an older kernel or the older version if that is the only way.  

I hope for two things:  A solution and that this thread can be a nexus for solving the problems.  

To all who respond, thanks in advance.  Moderator: If you feel this is inappropriate for the forum heading where I placed it, please move it.

---

### Post by Musashi-san on 2007-04-13
I've got the same problem when trying to log in. After gdm log in, the system takes 5 or more minutes to get desktop ready.

Disabling ethernet:
```
#ifdown eth0
```
Desktop starts in less than 20 seconds.

Same problem after playing with /etc/hosts: [https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)

I found a clue about the problem:
```
#hostname
labxarxes25
#hostname -f
Hostname: Hostname lookup failure
```

Then i found in /etc/hostname file:
```
labxarxes25
```

/etc/hosts file:
```
127.0.0.1 localhost
127.0.1.1 my-desktop
```

**[SIZE="4"]SOLUTION:[/SIZE]**
Edit /etc/hosts to match /etc/hostname

/etc/hostname file:
```
labxarxes25
```

/etc/hosts file:
```
127.0.0.1 localhost labxarxes25
127.0.1.1 labxarxes25
```

Now if i run hostname:
```
#hostname
labxarxes25
#hostname -f
localhost
```

I hope this helps

---

### Post by msfisher on 2007-04-14
Thanks for the reply (I FINALLY got one!) Musashi-san.  I'd tried your idea before, but checked my system just to be sure.  I reset the  hostname stuff, but it still didn't help.

On a more general note, one thing I saw from other threads was a discussion of ping time.  I tried it on my setup.  If I ping localhost, all looks OK -- ping times about 0.03ms to 0.04ms.  When I try to ping my router, HUGE difference.  First ping takes >1000ms, second about 25ms, third back to >1000ms, and repeating indefinitely.  By the way, this corresponds to behavior I saw under Mandriva.

---

### Post by rotalesav on 2007-04-20
> **msfisher said:**
> When I try to ping my router, HUGE difference.  First ping takes >1000ms, second about 25ms, third back to >1000ms, and repeating indefinitely.  By the way, this corresponds to behavior I saw under Mandriva.

Uhm, looks like i have got the same problem. First connection to any location takes seconds, after that it runs a bit faster… Internet on other OS's installed on this computer work just fine, what could that be?

---

