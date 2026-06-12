---
title: "Plymouth (oh no!) and ATI/FGLRX. NoCanDo, Really?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-22
A few posts recently:[I]

"The nice Ubuntu logo with glowing dots that you were seeing before you have installed the fglrx driver was being shown because the (default) open-source ati driver supports KMS. And the proprietary fglrx does not. Therefore, plymouth doesn't look so good."

"Everything fine so far , except the plymouth issue"[/I]

Ok, I am really getting sick of this Plymouth.  And with an ATI card, it seems even more futile (It's useless except for a few seconds at boot, and has killed the Recovery Console.)

So what is the next step for us testers with ATI cards?

---

### Post by myddewji13 on 2010-03-22
+1 ...

---

### Post by shindou01 on 2010-03-22
i get the picture......
I'm running on ATI 3200HD...wew...and I can't even open the ATI Catalyst Control Centre cause it keeps telling me i don't have any drivers installed...and the Plymouth thing keeps on getting to my nerves...

---

### Post by lxp121 on 2010-03-22
download the new fglrx driver from [https://bugs.launchpad.net/bugs/494699](https://bugs.launchpad.net/bugs/494699)

after installation

cd /etc/ati
sudo cp control.dpkg-bak control.dpkg
sudo cp amdpscdb.default.dpkg-bak amdpscdb.default

then

aticonfig --initial -f


> **shindou01 said:**
> i get the picture......
I'm running on ATI 3200HD...wew...and I can't even open the ATI Catalyst Control Centre cause it keeps telling me i don't have any drivers installed...and the Plymouth thing keeps on getting to my nerves...

---

### Post by Longinus00 on 2010-03-22
This was very easy for me to solve, I just stopped using the proprietary drivers. Best choice I ever made.

---

### Post by emarkay on 2010-03-23
> **lxp121 said:**
> download the new fglrx driver from [https://bugs.launchpad.net/bugs/494699](https://bugs.launchpad.net/bugs/494699)


Wait - I thought the issues were because of this file (the 5th release of it):
***fglrx-installer_8.721.orig.tar.gz***

Not the file you mentioned (in the Bug Report):
***xserver-xorg-video-ati_6.12.191.orig.tar.gz***

Now I am confused...

---

### Post by svaens on 2010-03-23
> **Longinus00 said:**
> This was very easy for me to solve, I just stopped using the proprietary drivers. Best choice I ever made.
But the open source driver doesn't have power management .... so i've read. So it is always fast, or always slow .... sounds a bit dangerous to a laptop to use it.... unless I am wrong ?

---

### Post by myddewji13 on 2010-03-23
> **svaens said:**
> But the open source driver doesn't have power management .... so i've read. So it is always fast, or always slow .... sounds a bit dangerous to a laptop to use it.... unless I am wrong ?

No power management = not being able to wake up from sleep...otherwise trust me I'd be using it too....

---

### Post by psyke83 on 2010-03-23
emarkay & others,

Before this thread goes down in flames, how about reading [this]("http://ubuntuforums.org/showpost.php?p=8995529&postcount=7") post (and the whole thread for context) ;).

There are dozens of threads dealing with plymouth already, one more is not necessary.

---

### Post by psyke83 on 2010-03-23
> **svaens said:**
> But the open source driver doesn't have power management .... so i've read. So it is always fast, or always slow .... sounds a bit dangerous to a laptop to use it.... unless I am wrong ?

Relevant parts of "man radeon":

>        Option "ClockGating" "boolean"
              Enable  dynamic  clock  gating.   This can help reduce heat and
              increase battery life by  reducing  power  usage.   Some  users
              report  reduced  3D performance with this enabled.  The default
              is off.

       Option "ForceLowPowerMode" "boolean"
              Enable a static low power mode.  This can help reduce heat  and
              increase battery life by reducing power usage at the expense of
              performance. The default is off.

       Option "DynamicPM" "boolean"
              Enable dynamic power mode switching.  This can help reduce heat
              and increase battery life by reducing power usage when the sys&#8208;
              tem is idle (DPMS active). The default is off.

From "man radeonhd":

> 
       Option "ForceLowPowerMode" "boolean"
              Enable to statically set GPU  engine  clock  to  a  lower  than
              default  value.  This  can  help  reduce power consumption. The
              default is off.

       Option "LowPowerModeEngineClock" "integer"
              Engine  clock  frequency  to  use  when  ForceLowPowerMode   is
              enabled, in Hz. If not set, the minimum known working frequency
              is used.  If integer is negative, validation  is  skipped,  and
              the absolute value is used for the engine clock.

---

### Post by svaens on 2010-03-25
> **myddewji13 said:**
> No power management = not being able to wake up from sleep...otherwise trust me I'd be using it too....

hmm .... I think not. 

I am currently using the default open source driver for ATI, 
and my sleep is working fine!

---

### Post by proxess on 2010-04-12
I'd use the FOSS drivers if they supported the Evergreen. I even had to move to 10.04 to get support. FGLRX really needs KMS.

---

### Post by emarkay on 2010-04-12
Forgot this one - solved - works OK as of a few days ago!  Thanks!

---

### Post by myddewji13 on 2010-04-12
> **svaens said:**
> hmm .... I think not. 

I am currently using the default open source driver for ATI, 
and my sleep is working fine!

Then please explain to me how I can't resume from sleep till I install fglrx...

---

### Post by svaens on 2010-04-12
> **myddewji13 said:**
> Then please explain to me how I can't resume from sleep till I install fglrx...

just worked for me. Earlier alpha it didn't, but recently, it has worked fine. 

I have an ATI Radeon Mobility HD 3470
on an Intel core duo processor. 
(sony vaio)

---

