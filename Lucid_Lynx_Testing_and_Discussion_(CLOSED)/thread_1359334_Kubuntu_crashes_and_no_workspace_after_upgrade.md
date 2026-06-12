---
title: "Kubuntu crashes and no workspace after upgrade"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-12-19
Has anyone had segfault problems with Kubuntu Lucid ?
I've been having the KDE daemon, Knetworkmanager daemon and now Plasma Workspace daemon crashes with segfault (signal 11). When I had this problem initially and tried to report the problem the gathered information was deemed to be 'probably useless' by apport (or at least the KDE equivalent). The Plasma Workspace daemon has only occurred since I upgraded to the 2.6.32-8 kernel and now I can't even attempt to report the problem as I don't see a desktop. Recovery mode only gets me to a tty1 console. 
What is the KDE equivalent of startx ?
Upgrade was from the previous -7 kernel. Ubuntu -8 kernel works fine on the same PC (but different partition).

---

### Post by caryb on 2009-12-19
Mine crashes trying to send bug report automaticly So I don't bother


Cary

---

### Post by Universal344 on 2009-12-20
I haven't had any major crashes yet, nut I've had what deems to be drawing issues with qt.  Parts of applications (especially plasma) will turn black seemingly randomly.  Does anyone else have this problem?

---

### Post by slakkie on 2009-12-20
I can't boot using KDE on Ubuntu. I'm back in Debain. I'll maybe disable kdm and see how it goes.

---

### Post by hikaricore on 2009-12-20
No problems here.
My desktop widgets got all fuggored up the other day and I had to redo them but other than that everything works.

---

### Post by VMC on 2009-12-21
I have nothing to add here except that I installed Kubuntu 9.10 for the first time. I got all the 9.10 family from a dvd magazine.

I have been a Gnome user forever, but tried KDE on , Fedora, PC-BSD and openSUSE. I read terrible reviews regarding ubuntu kde version. But after install of Kubuntu 9.10 and I got everything se up I was very pleased with the outcome. Works very well. It pays sometimes not to listen to rumors :)

Now I'm also running Ubuntu Lucid and keeping updated. No issues to date.

I was then thinking of making use of another partition and upgrading my Kubuntu 9.10 to Lucid.

Reading this thread maybe I'll wait, if it crashes all the time. I do really like KDE 9.10 though.

---

### Post by Kevbert on 2009-12-21
Thanks for all the replies. Kubuntu Lucid may just not like my hardware, but it's very strange that Ubuntu Lucid is fine. I'll just have to try a new clean install at Alpha 2 and see if that helps.

---

### Post by xebian on 2009-12-22
I could not get the plamsa-desktop since 4.4B1.  Now that B2 is here I still get this black background.
```

Dec 22 07:36:33 lulu kdm_greet[4705]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
Dec 22 07:36:48 lulu kernel: [  714.127632] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Dec 22 07:36:48 lulu anacron[4865]: Anacron 2.3 started on 2009-12-22
Dec 22 07:36:48 lulu anacron[4865]: Normal exit (0 jobs run)
Dec 22 07:36:52 lulu kernel: [  719.004134] drkonqi[4910]: segfault at 0 ip 00007f4807e0debb sp 00007fff029c0130 error 4 in libkdecore.so.5.4.0[7f4807d6b000+28f000]
Dec 22 07:36:54 lulu kernel: [  720.531448] plasma-desktop[4909]: segfault at 0 ip 00007f0612d23877 sp 00007fffa3a09470 error 4 in libplasma.so.3.0.0[7f0612bfa000+2a3000]

```

I was being patient till 4.4 B2 but now it's ironic I have to use lxde to get a decent system.  Reinstalling kdelibs5 and desktop-plasma and even a complete fresh install did not help. :confused:

---

### Post by hikaricore on 2009-12-22
Still having 0 problems myself.
There were a massive number of kde packages updated today, I suggest doing a dist-upgrade.

---

### Post by xebian on 2009-12-22
> **hikaricore said:**
> Still having 0 problems myself.
There were a massive number of kde packages updated today, I suggest doing a dist-upgrade.

Didn't I say "..now that B2 is now here.."  ?

---

### Post by hikaricore on 2009-12-22
Well I'd not refreshed the page for several hours and didn't see your post.

*shrug*

---

### Post by almostlinux on 2010-01-06
Same thing here .. segfaults on start up. Can't use desktop. I installed a daily yesterday .. same thing.

---

### Post by vikrant82 on 2010-01-06
Mostly its stable, but it hates me playing around with activities.

---

### Post by VMC on 2010-01-06
> **Kevbert said:**
> Has anyone had segfault problems with Kubuntu Lucid ?
I've been having the KDE daemon, Knetworkmanager daemon and now Plasma Workspace daemon crashes with segfault (signal 11). When I had this problem initially and tried to report the problem the gathered information was deemed to be 'probably useless' by apport (or at least the KDE equivalent). The Plasma Workspace daemon has only occurred since I upgraded to the 2.6.32-8 kernel and now I can't even attempt to report the problem as I don't see a desktop. Recovery mode only gets me to a tty1 console. 
What is the KDE equivalent of startx ?
Upgrade was from the previous -7 kernel. Ubuntu -8 kernel works fine on the same PC (but different partition).

I now get these error messages. Thinking it was KDE error I tried to reopen one of their (kde.org) bug reports. I get the above errors on every logoff, reboot, or restart or shutdown.

---

### Post by VMC on 2010-01-07
> **Kevbert said:**
> Has anyone had segfault problems with Kubuntu Lucid ?
I've been having the KDE daemon, Knetworkmanager daemon and now Plasma Workspace daemon crashes with segfault (signal 11). When I had this problem initially and tried to report the problem the gathered information was deemed to be 'probably useless' by apport (or at least the KDE equivalent). The Plasma Workspace daemon has only occurred since I upgraded to the 2.6.32-8 kernel and now I can't even attempt to report the problem as I don't see a desktop. Recovery mode only gets me to a tty1 console. 
What is the KDE equivalent of startx ?
Upgrade was from the previous -7 kernel. Ubuntu -8 kernel works fine on the same PC (but different partition).

I just filed a [**bug report**]("https://bugs.launchpad.net/ubuntu/+bug/504375") on this. I'm not sure the info that I was able to get is enough. I only had less than 30 seconds to grab it.

---

### Post by Kevbert on 2010-01-08
Thanks VMC. I've added some logs/comments to your bug report and cross referenced it to this thread. I'll also try to get a screenshot (via mobile phone) and attach that.

---

### Post by VMC on 2010-01-08
> **Kevbert said:**
> Thanks VMC. I've added some logs/comments to your bug report and cross referenced it to this thread. I'll also try to get a screenshot (via mobile phone) and attach that.

Thanks for your input and this topic. At the time I was using Kubuntu 9.10 and had no issues.

I'm also wondering why there appears to be just you and me having this problem?!

If I could extend restart/shutdown/logoff from 30 seconds to a few minutes I could print out the crash dialogue that appears. Earlier version of kde4 allowed that option.

---

### Post by Kevbert on 2010-01-15
Just performed a clean Alpha2 install (kernel 32-10) and Kubuntu starts OK with it's fancy new theme. 
Unfortunately it looks like Kubuntu is going the same way as Windows, after a reboot new shortcuts are found, reboot - a few more...
Still get the two prompts when logging in as before and now only get segfaults on knetworkmanager. I'll probably need to wait a few days more before the other segfaults appear (after I get wired and WLAN working).

---

### Post by VMC on 2010-01-15
> **Kevbert said:**
> Just performed a clean Alpha2 install (kernel 32-10) and Kubuntu starts OK with it's fancy new theme. 
Unfortunately it looks like Kubuntu is going the same way as Windows, after a reboot new shortcuts are found, reboot - a few more...
Still get the two prompts when logging in as before and now only get segfaults on knetworkmanager. I'll probably need to wait a few days more before the other segfaults appear (after I get wired and WLAN working).
We had mixed experiences. Installed new A2, then I still get all the seg faults as before.
But I don't get any shortcuts. Where do you see them, desktop?

Regarding login, I use the convenience auto login, and all I have to do is hit return only once. Compiz is nowhere to be found.

---

### Post by Kevbert on 2010-01-15
A little box appears on the right-hand side of the screen saying a shortcut has been added for ... On the first restart I had a single column of them going from top to bottom of the desktop screen as soon as the KDE desktop is displayed. On the second and third restarts a new one appeared. They're displayed for just over a second, each time.
Still having trouble getting my Broadcom wireless to work even after copying firmware to /lib/firmware, rebooting and trying to turn on wireless with
```
sudo ifconfig wlan0 up
```
The knetworkmanager segfault occurs when I restart (every time).

Edit: Now got wireless working, had to do a complete power down. Still get segfault for knetworkmanager on when ask PC to restart.
On the fourth boot I managed to get a photo of the shortcut message (another new one) which is attached.
There's also a [COLOR="Red"][bug]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/429867")[/COLOR] with unattended-updates if you perform an upgrade.

---

