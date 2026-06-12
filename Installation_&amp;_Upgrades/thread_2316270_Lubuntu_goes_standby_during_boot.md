---
title: "Lubuntu goes standby during boot"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by linuxkvh on 2016-03-06
Hi, 

I have been using Lubuntu over the past decade, but am having an installation issue with Lubuntu 15.10 that I had previously on 14.3: Lubuntu installed correctly (I presume) but during boot suddenly goes to sleep (enters standby mode). After waking up (manually), it sometimes (but not always) happens a second time. Then after the desktop appears, everything is back to normal. I had this before with a previous version (14.03), and it causes me a headache. 

The issue does not happen while installing other distros or OS (I currently dual boot it with W7), so I'm pretty sure this is not a hardware issue.

For your information, some specs. I use Forcepae on a Dell inspiron 700m.

Any thoughts on how to resolve this issue? 

---------

Processor: Intel(R) Pentium(R) M processor 1.60GHz  (non-pae)
Family, model, stepping: 6, 13, 6 (Pentium III/Pentium III Xeon/Celeron)
[TABLE]
[TR]
[TD="class: ecxfield"]Memory:[/TD]
[TD="class: ecxvalue"]2045MB (427MB used)[/TD]
[/TR]
[TR]
[TD="class: ecxfield"]Operating System:[/TD]
[TD="class: ecxvalue"]Ubuntu [Lubuntu] 15.10[/TD]
[/TR]
[/TABLE]

---

### Post by mörgæs on 2016-03-08
> **linuxkvh said:**
> 
I have been using Lubuntu over the past decade
That's a long time considering that the first Lubuntu ISO was 10.04.

Though you say that the hardware is fine: Are you using the original powersupply? I have seen similar problems when trying to use one which does not deliver enough current.

---

### Post by linuxkvh on 2016-03-08
[COLOR=#222222][FONT=Verdana]Hi,

You're right I'm not using the original Dell power supply, but a HP one withsimilar specs. I have just attempted a boot with the original one, but theStandby issue remains.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]The specs are as follows:

Dell Inspiron 700m (original; not in use because of slightlydamaged cable):
Input: AC 100-240V, 50-60Hz
Output: DC 19.5V, 3.34A
Power: 65W

HP power supply
Input: AC 100-240V, 50-60Hz
Output: DC 18.5V, 3.5A
Power: 65W

As you can see, the HP specs are almost the same as the original one. However, as I said earlier, the Standby issue only happens with Lubuntu, not withW7 on dual boot. I might consider buying an original Dell one, if that could help resolve the issue. The laptop goes in Standby mode about ten seconds into boot (after grub).
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Could it be that the &#8220;Forcepae&#8221; command has some nefasteffect on the boot? 

> **mörgæs said:**
> That's a long time considering that the first LubuntuISO was 10.04.
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Thanks for correcting me!  It almost feels like adecade has past since Lubuntu started back in 2008... :)[/FONT][/COLOR]

---

### Post by mörgæs on 2016-03-09
You could try the almost-finished 16.04 to see if it changes anything but I can't promise you anything. 

If the computer goes into standby using also the original powersupply then I don't have more ideas, sorry.

---

### Post by bill101 on 2016-04-24
Solution here is to disable [COLOR=#323232][FONT=arial]ACPI (Advanced Configuration and Power Interface).  Basically in Grub:
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

[/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#323232]This update worked for me.  Only downside is that the battery is not recognized in my laptop however it still functions.  Additionally, when I shutdown, I have to physically press and hold the power button once OS shutdown completes.  Not perfect solution, but better than experience with startup when it goes into sleep mode both at grub startup as well as lubuntu. Note there is a number of other forum threads/info out there on this topic and the solution.

Note I am currently running 16.04 and still require this "fix" on my Acer netbook.  [/COLOR][/SIZE][/FONT]

---

### Post by DirkN on 2016-05-15
Hi bill101,

> **bill101 said:**
> Solution here is to disable [COLOR=#323232][FONT=arial]ACPI (Advanced Configuration and Power Interface).  Basically in Grub:
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

[/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#323232]This update worked for me.  Only downside is that the battery is not recognized in my laptop however it still functions.  Additionally, when I shutdown, I have to physically press and hold the power button once OS shutdown completes.  Not perfect solution, but better than experience with startup when it goes into sleep mode both at grub startup as well as lubuntu. Note there is a number of other forum threads/info out there on this topic and the solution.

Note I am currently running 16.04 and still require this "fix" on my Acer netbook.  [/COLOR][/SIZE][/FONT]

Do you know if someone is working on this issue at Ubuntu? I have the same problem with my Acer TM C300.
TIA
  Dirk

---

### Post by atmaps on 2016-05-18
I'm having this problem, too. Running Lubuntu 16.04 on a Siemens-Fujitsu Amilo 7400M (Pentium M 1.4 GHz). This is really a bother as it concerns especially those older laptops - the ones Lubuntu was actually made for ...

---

### Post by mörgæs on 2016-05-18
And your question is...? 

A possible fix has been posted above. Did it help?

By the way, it would be interesting to see how Xubuntu or Mate works on the same hardware. I'm not sure it's a Lubuntu only problem.

---

### Post by a_pirard on 2016-06-23
I am having exactly that problem
on SONY VAYIO VPCF12S1E, battery failing and removed
16.04 Xubuntu + MATE Destop added
acpi=off works as described above

I'm wondering if
- the problem starts during boot
- it lasts while lightdm runs
- it stops when entering a session
- it resumes when returning to lightdn

if the problem is not related to a lightdm setting

---

### Post by Dukenukemx on 2016-06-29
I'm having this problem with an old Presario 2200 with a Celeron or Pentium M @ 1.3Ghz.  Tried the "fix" on Xubuntu 16.04, but I don't like it.  I would like to keep standby if possible.  Does this occur in Debian?  I'm willing to try other distros, even if that means more work for me.  This is for an old woman I know who refuses to throw this thing away.  Worse yet, the DVD drive no longer works, so installing a different distro is hard.

---

### Post by Dukenukemx on 2016-06-30
I tried Debian 8 Jessie with Mate, and so far so good.  BTW the laptop is a Celeron M it turns out.  Everything seems to work, no standby when booting or shutting down, and closing the lid and opening it will resume without issue.  There was no need to force PAE or disable ACPI.  Of course I now have to find a way to make Debian easy to use for grandma, but it shouldn't be too much harder than Ubuntu.  I installed the BCM4306 wifi driver without issue.  

For those looking for a fix, you can download the ISO's here.  LXDE is one of the choices.  
[http://cdimage.debian.org/debian-cd/current-live/i386/bt-hybrid/](http://cdimage.debian.org/debian-cd/current-live/i386/bt-hybrid/)

---

### Post by Dukenukemx on 2016-06-30
Might have a solution for those with Ubuntu still.  In Debian I did have a problem with the laptop sleeping when shutting down or restarting.  I found something you add to grub that might fix it, or at least it did for me on Debian 8.  I was able to shut the laptop down twice, so it couldn't be just luck.

Edit grub and add this GRUB_CMDLINE_LINUX="acpi_sleep=nonvs".  Save and update grub and reboot.

---

