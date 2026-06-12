---
title: "Have the Intel graphics drivers been fixed?"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by danbuter on 2010-02-21
I can't use KK because the intel graphics drivers won't work on my HP netbook. Have they upgraded these drivers for LL yet?

---

### Post by cariboo on 2010-02-21
I think it depends on what chipset you computer is running. Karmic works well for me, on my atom powered media center pc. The only thing I have a problem with is the default flash installed from the repositories, It brings the system to a stand still when playing full screen HD flash videos. My system has the 945 graphics chipset.

---

### Post by psyke83 on 2010-02-21
That's a pretty vague question. What's your integrated graphics card model? What's the specific problem that prevented the drivers from working?

---

### Post by VMC on 2010-02-21
Here's my Intel card, as an example:
lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation **82865G** Integrated Graphics Controller (rev 02)

The problem I'm having is with the games. I get "trails" or "ghosting" when I move a card. Maybe other areas too, I first noticed it there.

Other than that, its ok. 

Look at you home folder files ".xsession-errors", for any indication or problems.

---

### Post by danbuter on 2010-02-21
Intel Graphics Media Accelerator 950

I get a black screen in KK.

---

### Post by sports fan Matt on 2010-02-21
I cant figure out the command to see what intel drivers I have..can someone lead me to it?

---

### Post by andrewabc on 2010-02-21
> **danbuter said:**
> Intel Graphics Media Accelerator 950

I get a black screen in KK.

Intel graphics should work really well with GMA950. My nettop works fine.

Have you tried another liveusb of it? Install doesn't work or liveusb?

Either way to answer your question wait until late Thursday and alpha 3 will be out, and you can run the livecd/usb to see if you have same problem.

Ask question in this thread Thursday and Friday and people will have more responses.

---

### Post by Starks on 2010-02-21
> **sox fan Matt said:**
> I cant figure out the command to see what intel drivers I have..can someone lead me to it?
lspci -v | grep VGA

---

### Post by dentaku65 on 2010-02-21
Did u tried with nomodeset option at grub?

add nomodeset at the kernel line 
```
quiet splash nomodeset
```

at the boot pres esc in order to see the grub entries, then press 'e' (edit) key at the first kernel, add nomodeset as indicated above, ctrl-x to boot

---

### Post by psyke83 on 2010-02-21
> **VMC said:**
> Here's my Intel card, as an example:
lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation **82865G** Integrated Graphics Controller (rev 02)

The problem I'm having is with the games. I get "trails" or "ghosting" when I move a card. Maybe other areas too, I first noticed it there.

Other than that, its ok. 

Look at you home folder files ".xsession-errors", for any indication or problems.

That's not a graphics driver problem - it's a performance issue with the latest client-side window decoration code in GTK. There's about two or three threads discussing this already, with links to the bug report.

---

### Post by VMC on 2010-02-21
> **sox fan Matt said:**
> I cant figure out the command to see what intel drivers I have..can someone lead me to it?

Maybe this:

 ```
aptitude show xserver-xorg-video-intel|grep Ver
Version: 2:2.9.1-1ubuntu6
```

---

### Post by VMC on 2010-02-21
> **psyke83 said:**
> ...it's a performance issue with the latest client-side window decoration code in GTK. There's about two or three threads discussing this already, with links to the bug report.Other than the one I [create]("http://ubuntuforums.org/showthread.php?t=1410357"), can you point me to the other 2 threads. This starting occurring in just the past week. Searching didn't reveal any other threads.

---

### Post by GeoPirate on 2010-02-21
does anyone know if they have fixed the intel i3 intergrated intel graphics yet?

---

### Post by psyke83 on 2010-02-21
> **VMC said:**
> Other than the one I [create]("http://ubuntuforums.org/showthread.php?t=1410357"), can you point me to the other 2 threads. This starting occurring in just the past week. Searching didn't reveal any other threads.

That's the thread - it appears that you didn't see the latest comments to the bug report (the summary was changed, as the issue was not related to Rhythmbox alone).

Reverting to version 2.19.5-1ubuntu2 of the gtk packages resolves the performance issue (including stutter in Aislerot).

---

### Post by sports fan Matt on 2010-02-21
My bad, i meant the chipset.  I'm trying to see if it's worth it to re-upgrade to lucid then leave it alone

---

### Post by psyke83 on 2010-02-21
> **sox fan Matt said:**
> My bad, i meant the chipset.  I'm trying to see if it's worth it to re-upgrade to lucid then leave it alone

```
lspci | grep VGA
```

---

### Post by sports fan Matt on 2010-02-21
Anyone had any issues with  VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)?

---

### Post by pferraro on 2010-02-22
> **GeoPirate said:**
> does anyone know if they have fixed the intel i3 intergrated intel graphics yet?

No - full support for the integrated graphics found on Arrandale processors requires version 2.10.0 of the intel xorg drivers.

[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)
"* Improved support for Intel® HD Graphics (in Intel® 2010 Core i7/i5/i3 Processor Series)."

You can upgrade to this version via the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by diebels on 2010-02-22
> **pferraro said:**
> No - full support for the integrated graphics found on Arrandale processors requires version 2.10.0 of the intel xorg drivers.

[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)
"* Improved support for Intel® HD Graphics (in Intel® 2010 Core i7/i5/i3 Processor Series)."

You can upgrade to this version via the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Anybody knows which version Lucid is going to have at release?

---

### Post by glasen on 2010-02-22
BTW, if someone is interested, i've made a PPA with the latest git-version of the Intel-driver.

I've added two small header files, which add some missing functions of the Lucid "libdrm"-package (Mostly Xv-overlay stuff, see also the changelog of the PPA-package). The driver compiles cleanly under a normal lucid installation (No need for xorg-edgers-PPA or other non-Lucid packages)

The driver works perfectly on my 855GM-chipset (Dell Latitude D505). It even supports Xv-overlay with KMS (Requires a kernel patch, which is not included in vanilla Linux 2.6.32).

[PPA - Intel Driver 2.10git]("https://launchpad.net/~glasen/+archive/intel-driver")

---

### Post by GeoPirate on 2010-02-22
Thanks a bunch, the UPS man is dropping off my shiny new i3 tomorrow, can't wait to check it out.

---

### Post by goebbe on 2010-02-24
If the standard installation freezes (black screen) early in the boot process, 
and if the only way to boot your system is to set the "nomodeset"-option then you may be interested in the following bug report: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/522940](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/522940)

(You can confirm by choosing "this bug affects you" in the bug report)

---

### Post by teh603 on 2010-02-26
Tried Alpha 3 it on my Inspiron 1564, and everything seems to work ok, even Compiz. Haven't tried any advanced diagnostics or anything like that, though.

---

### Post by GeoPirate on 2010-02-26
yeah, I got 2 systems I installed the first one on wednesday with alpha2 and it was a PITA to get everything working, but I used alpha3 for the second system and it just installed and booted without a glitch.  If you get a new system definetly go with aplha3.

---

### Post by dentaku65 on 2010-02-28
I'm still under this issue 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001)
in fact I cannot use/boot Lucid (Alpha 3) with or without nomodeset with my intel card
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by danbuter on 2010-02-28
I tried the latest cd for LL, and on install, it went black screen partway in again. I then installed OpenSUSE with no issues. So both Novell and Red Hat have fixed this bug, but it's still active in Ubuntu, which bugs me, as I prefer Ubuntu.

---

### Post by IanW on 2010-03-01
Phoronix reports Intel have released a new driver (2.11.0-rc1) [http://www.phoronix.com/scan.php?page=news_item&px=ODAyMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODAyMQ).

---

