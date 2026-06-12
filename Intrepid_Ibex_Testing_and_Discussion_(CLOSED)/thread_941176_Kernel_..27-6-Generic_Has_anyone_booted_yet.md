---
title: "Kernel ..27-6-Generic Has anyone booted yet?"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by douham on 2008-10-07
Hi

Just did a Dist-upgrade which got be the i386 2.6.27-6-Generic update. Cannot boot boot successfully, on text boot getting a hang at Uniform CD-ROM driver Rev: 3.20 . Booting into the -5 kernel no worries, searching in LP shows that the *-27..updates were supposed to fix this. Just checking before post a bug

Doug

---

### Post by mariner09 on 2008-10-07
I'm grabbing it right now and will report what I get...

---

### Post by RideBMX on 2008-10-07
Took me 3 tries to successfully boot into 2.6.27-6.

---

### Post by caryb on 2008-10-07
It worked straight up for me, but I must admit that my PC since the 2.27.* kernels has to have the quiet & splash removed from the menu.list otherwise my PC speaker beeps at 100db & I get hieroglyphic screen:confused: But knowing that I strip off the commands & I have no problems.

Cary

BTW NM 0.7 is a pig still:lolflag:


Cary

---

### Post by mariner09 on 2008-10-07
smcmackin@Mariner-T61:~/Desktop$ uname -r
2.6.27-6-generic

Booted fine for me...

---

### Post by ronacc on 2008-10-07
booted ok for me , no cahnges to the boot stanza except -5>-6. I'm 64bit .

---

### Post by FuturePilot on 2008-10-07
All is fine here.

---

### Post by PRGUY85 on 2008-10-07
I'm having problems as well specially in Kubuntu.  Ubuntu boots up fine however my network connections do not work.

---

### Post by nanog on 2008-10-08
boots fine on 2 boxes and 2 laptops. 

nm 7 is also an enormous improvement, imo.

---

### Post by autocrosser on 2008-10-08
-6 works very well for me--was getting erratic reboots at any-old-time with 4 -- 5 worked better & 6 looks like it "might" fix it for me--was almost impossible to pin down--nothing in the logs.......

---

### Post by gtdaqua on 2008-10-08
I have [this]("http://ubuntuforums.org/showthread.php?t=913771") error. Both on 2.6.27-5 and 2.6.27-6. I am using -4 which works.

---

### Post by waspbr on 2008-10-08
a positive point, they seem to have sorted out the bluetooth. 

I no longer need to do 

```
sudo hidd --search
```

to connect my BT mouse, there is a new and improved BT GUI via the applet

---

### Post by kforum on 2008-10-08
i had to try 2 times ot get it to boot, it would boot on the first one, but iit ignored my nvidia card it seems... so i had a OS with a black screen...

strange, but got fixed the second time.

whats with kubuntu anyway, such strange self-fixing issues... o.O

---

### Post by Kow on 2008-10-08
```

2.6.27-6-generic #1 SMP Tue Oct 7 04:15:23 UTC 2008 x86_64 GNU/Linux

```

Worked as any normal kernel update should. Using the latest intrepid nvidia driver.

---

### Post by autocrosser on 2008-10-08
Greeting Cary--OT--You have been having the same problem that I have--BIOS beeps that drive you mad?? I have FINALLY got mine under control--You need to look at the bug I've been flogging for several months now. Just found the answer last night & I would think that it would "fix" your issue also...take a look thru this:  
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

And look at the other bug I've referenced towards the bottom of the page..could turn the trick for you also.....

> **caryb said:**
> It worked straight up for me, but I must admit that my PC since the 2.27.* kernels has to have the quiet & splash removed from the menu.list otherwise my PC speaker beeps at 100db & I get hieroglyphic screen:confused: But knowing that I strip off the commands & I have no problems.

Cary

BTW NM 0.7 is a pig still:lolflag:


Cary

---

### Post by douham on 2008-10-08
I'm still having issues with 27-6. Booted fine 1st up new install on my old Pent 3 machine, still waiting on the nvidia 71 driver for an old TNT2 card though. Had no problems with this card through the alphas though.
However, my Core2 duo machine will not boot at all. Will try some of the work arounds in the Ibex forum.

---

### Post by douham on 2008-10-08
> **douham said:**
> I'm still having issues with 27-6. Booted fine 1st up new install on my old Pent 3 machine, still waiting on the nvidia 71 driver for an old TNT2 card though. Had no problems with this card through the alphas though.
However, my Core2 duo machine will not boot at all. Will try some of the work arounds in the Ibex forum.

Ha stupid me. I booted into the BIOS and consulted my m/b manual Realised that I had my SATA ctrl mode set to IDE and not AHCI(SATA).
Booted fine into 27-6, sweet

Doug

---

### Post by rbmorse on 2008-10-08
Glad you got it going, but the BIOS set to IDE should still have worked.

---

### Post by caryb on 2008-10-08
Autocrosser, I made the changes as per the instructions, I have the quiet splash entry added to my current kernel. It now boots without beeping but I dont get a splash screen?


Cary

---

### Post by caryb on 2008-10-09
2nd reboot no splash blue lines travelling down the page, kdm fails to load & have a 72 font logon:lolflag: removed previous changes & have my old verbose no splash bootup!

Cary

---

### Post by autocrosser on 2008-10-09
What you might need to do is muck with the resolutions--try 800x600 and such--it took me several times until I found the "sweet spot" that worked....

I also looked thru both posts very closely--the comments that chris_c made about the modes that were available were enlightening....

I forgot--have you installed v86d?

---

### Post by jerrylamos on 2008-10-09
Yes, this is installed 2.6.27-6 but it's got the same problem on IBM Thinkpad R31 that Beta & Alpha 6 do.  Alpha 5 runs.

With Ubuntu, after CD Live boots up, at the point the desktop should appear the screen goes black.  The Thinkpad is frozen except for power off.

Investigating see launchpad bug #25745 the problem is Compiz & Ubuntu Gnome.  Xubuntu & Kubuntu O.K., or installing xfce4 on Ubuntu is O.K., or removing Compiz with Synaptic.

All this has been a bit brutal - when I can get Gnome Metacity up, the desktop works, but Firefox fails with some problem with authority.

Jerry

p.s. The CD Live from today 20081009 booted on Compaq Presario - is that 2.6.27-6?  Tussling with the R31 I didn't check the Compaq much.

---

### Post by Sef on 2008-10-09
> Just did a Dist-upgrade which got be the i386 2.6.27-6-Generic update. Cannot boot boot successfully, on text boot getting a hang at Uniform CD-ROM driver Rev: 3.20 . Booting into the -5 kernel no worries, searching in LP shows that the *-27..updates were supposed to fix this. Just checking before post a bug

You should not do a dist-upgrade as it is no longer supported instead do it [this way]("http://ubuntuforums.org/showthread.php?t=936696").

---

