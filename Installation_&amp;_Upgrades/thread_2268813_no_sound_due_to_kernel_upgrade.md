---
title: "no sound due to kernel upgrade ?"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by tomaasj on 2015-03-11
The configuration:

laptop: Acer Aspire V Nitro

dualboot windows 8.1 and Ubuntu 14.04 lts.


Dear Ubuntu people,

finally got the dualboot to work.  In both operating systems sound was working in both front speakers.

In ubuntu, I started to download applications, ubuntu extra's, setting up the desktop etc.

Executed the following commands in the terminal:

sudo apt-get update
sudo apt-get upgrade
sudo reboot

After the reboot the left speaker is consistently not working.  Checked messages to re-install alsmamixer etc. To no avail.

When checking the left and right speakers, through terminal commands (voice exclaiming "front left" and "front right"), with pulseaudio out in gui I see bars coming up the moment the spoken texts appears in the terminal for both speakers, except only the right speaker can be heard.

I found a post which describes a similar situation:  it has been suggested it has to do with the kernel upgrade but no solutions are offered.

Can anyone give me suggestions how to proceed ?  I am very motivated to solve this issue.

Thanks in advance

Tomaasj

---

### Post by tomaasj on 2015-03-21
OK,

empirical observation:

several times I re-installed ubuntu in the mentioned configuaration.  The sound problem as described has not occured anymore.  All speakers and headphones work.

I noticed that the problem occured once I started to install the Restricted Ubuntu Extra's from the repositories.  Each time time I installed this package I kept having problems installing some ms font.  Soon afterwards the sound in the left speaker became mute, although alsamixer and similar tools indicated that all speakers should work properly.

I re installed ubuntu on its designated partition, and this is important, not before I reformatted the partition.  Re-installing ubuntu on the partition with the previously installed ubuntu without formatting the partition, kept having a mute left speaker after installation was completed.

Anyway, once I encountered problems with a file within the browser or rhythmbox for example, I simply installed what was necessary to have sound working for that particular issue.

For now everything works.  I will have this thread marked as solved although I do not know what this incompatibility in the Restricted Ubuntu Extra's package is, what seems to cause a muted left speaker.

I would off course appreciate it if anyone could shed some light on this issue.  

Preliminary conclusion: There is something in this Resticted Ubuntu Extra's software package which causes some incompatibility with the sound system in the described configuration as mentioned above.

Hopefully fellow ubuntu users who have encountered similar problems with their sound system after installing ubuntu 14.04 on their configurations can take their advantage with my empirical observation.

Tomaasj

---

### Post by tomaasj on 2015-04-09
Problem returned.  Left speaker is mute again.  While streaming through Firefox, the sound disappeared from the left speaker.

Earphones are not affected.

Re-installed 14.04 on its partition but to no avail.  I tested the sound settings while running 14.04 from a USB drive, again, the left speaker remains silent.
  
Can anybody share some thoughts on this issue ?

Tomaasj

---

