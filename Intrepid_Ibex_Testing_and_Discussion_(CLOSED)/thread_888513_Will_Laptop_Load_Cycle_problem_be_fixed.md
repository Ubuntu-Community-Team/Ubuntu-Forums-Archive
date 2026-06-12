---
title: "Will Laptop Load Cycle problem be fixed?"
date: 2008-08-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sealbhach on 2008-08-13
I was just wondering if this problem was going to be sorted out - where laptop hard drives are killed in the space of a few months by the Agressive Power Management?

[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

This is a real life FUD-inducing issue and I would hope it is fixed soon. Otherwise horror stories will start circulating and nobody will want to try Linux.


.

---

### Post by olskar on 2008-08-13
I strongly agree with you, this should be high priority (and apparently is since it has been marked a critical bug).


According to a comment at [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) :

"For first steps to solution see bug 250935 and bug 250938"

[https://bugs.launchpad.net/bugs/250935](https://bugs.launchpad.net/bugs/250935)
[https://bugs.launchpad.net/bugs/250938](https://bugs.launchpad.net/bugs/250938)

---

### Post by BCurtisWX on 2008-08-13
> **olskar said:**
> I strongly agree with you, this should be high priority (and apparently is since it has been marked a critical bug).


According to a comment at [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) :

"For first steps to solution see bug 250935 and bug 250938"

[https://bugs.launchpad.net/bugs/250935](https://bugs.launchpad.net/bugs/250935)
[https://bugs.launchpad.net/bugs/250938](https://bugs.launchpad.net/bugs/250938)

So since those two bugs appear to show that the load cycle problem is fixed and now working as designed, how will I know that my laptop is using it (if not already doing so)?

---

### Post by olskar on 2008-08-13
This bugfix alone does not fix the Load Cycle problem but it is a neccesary bugfix for the Load Cycle bug to be fixed, at least that is how I understand it

---

### Post by Johnsie on 2008-08-13
I've had hard drives in two Ubuntu laptops burn out. I'm not impressed that this is still an issue. I would be afraid to install Ubuntu on another laptop. It seems to work fine on with the hard disks desktops though. I've been using Ubuntu for several eyars on laptops and desktops but now I wont put it on a laptop.

---

### Post by olskar on 2008-08-13
> **Johnsie said:**
> I've had hard drives in two Ubuntu laptops burn out. I'm not impressed that this is still an issue. I would be afraid to install Ubuntu on another laptop. It seems to work fine on with the hard disks desktops though. I've been using Ubuntu for several eyars on laptops and desktops but now I wont put it on a laptop.


This issue isn't always an issue if you are aware of it. Mostly all it takes is a simple change in a file. This is more of a problem for people who are not aware of the problem (a majority) and therefore this should be fixed as soon as possible.

---

### Post by conundrumx on 2008-08-13
There was a rather long thread about this in the Help forum, or perhaps the Community Cafe.  Included were instructions for testing if you're affected by the issue and the steps to correct it.

I realize that's not as good as there being no problem at all, but for the people reading this thread help is available.  (If you can't find it with the search I'll go looking.)

---

### Post by Sealbhach on 2008-08-13
> **conundrumx said:**
>   (If you can't find it with the search I'll go looking.)

Thanks, that's very good of you - but I already have a link to it in my opening post.

It's a serious serious issue - imho - and I would be shocked if it was not fixed in Intrepid.


.

---

### Post by nlz on 2008-08-13
Sealbhach: Does your Vaio suffer from this problem?

---

### Post by Sealbhach on 2008-08-13
> **nlz said:**
> Sealbhach: Does your Vaio suffer from this problem?

Yes, I think so. It used to make that clicking noise all the time, so when I applied the ugly fix it stopped.

Luckily I'm under 10,000 after four months of use.


.

---

### Post by olskar on 2008-08-13
I recently bought a new laptop harddrive from seagate (ST9160821A) and the problem was there. It slowly clicked itself to death, but I fixed it with the ugly fix.

---

### Post by conundrumx on 2008-08-13
> **Sealbhach said:**
> Thanks, that's very good of you - but I already have a link to it in my opening post.

It's a serious serious issue - imho - and I would be shocked if it was not fixed in Intrepid.


.

I suppose that's what I get for not following links and reading too early in the morning. :rolleyes:

For my piece, I've a T61p (relatively new) and had no issues whatsoever.

---

### Post by Johnsie on 2008-08-14
If they aren't going to fix the bug then  they should at least warn people about the risk. Personally I'd prefer a fix and I wish I'd been informed of the problem BEFORE the damage occured. I'm having to use an EEEPC now lol.

---

### Post by hexion on 2008-08-14
> **olskar said:**
> [https://bugs.launchpad.net/bugs/250938](https://bugs.launchpad.net/bugs/250938)


Bug fixed in intrepid:

acpi-support (0.110) intrepid; urgency=low   * Let laptop-mode-tools run properly (closes LP: #250938)
    - power.sh: remove laptop-mode invocations, should be handled by pm-utils
    - acpi-support: remove SPINDOWN_TIME, should be controlled by laptop-mode
  -- Alexey Borzenkov <snaury@gmail.com>   Tue, 22 Jul 2008 23:59:07 +0400

> **olskar said:**
> 

[https://bugs.launchpad.net/bugs/250935](https://bugs.launchpad.net/bugs/250935)

laptop-mode-tools (1.45-1ubuntu1) intrepid; urgency=low   [ Tormod Volden ]
  * Merge from debian unstable (LP: #255446), remaining changes:
    - etc/init.d/laptop-mode: Check if laptop mode is disabled in
      /etc/default/laptop-mode (that's the file laptop_mode looks into, too,
      but it incorrectly evaluates the ENABLE_LAPTOP_MODE setting) as well
      as in /etc/default/acpi-support.
    - usr/sbin/laptop_mode: Do not parse arguments, ignore "force" and
      let start/stop mean enable/disable.
    - /usr/sbin/laptop_mode: Do not read $ACTIVATE_WITH_POSSIBLE_DATA_LOSS
      from /var/run/laptop-mode-state to see if state has changed.
    - debian/rules: Do not ship acpi/apm scripts (we handle that ourselves)
    - debian/laptop-mode-tools.preinst: Remove any old acpi/apm scripts
    - debian/laptop-mode-tools.postinst: Create /etc/default/laptop-mode
      (with ENABLE_LAPTOP_MODE=false) if the file does not exist yet and we
      are on ppc.
    - Also accept "stop" as second argument since the init script
      calls laptop_mode with "init stop"
   [ Alexey Borzenkov ]
  * Change default settings to match acpi-support (LP: #250935)
    - etc/laptop-mode/laptop-mode.conf: change default spindown time and
      power management modes
  * Add pm-utils hooks to ensure laptop-mode is running as expected after
    power change or thaw/resume
    - power.d/laptop-mode: runs laptop-mode on power change
    - sleep.d/96laptop-mode: runs laptop-mode on thaw/resume
 laptop-mode-tools (1.45-1) unstable; urgency=low
   * New upstream version 1.45.
  * New upstream version 1.44:
    * Strip non-numeric suffixes from kernel minor version number.
      Closes: #488950.
    * Remove spurious error message on machines that don't have
      /sys/class/power_supply. Closes: #490167.
    * Fix incorrect path to laptop-mode.conf in the laptop-mode.conf(8)
      manual page. Closes: #488261.
    * Add sched-mc-power-savings module. Closes: #490587.
 laptop-mode-tools (1.43-1) unstable; urgency=low
   * New upstream version 1.43:
    * Don't use temp file in init script, that doesn't work if /tmp is
      mounted readonly. Closes: #480946.
    * Fix IPW2100 power management so that power management mode stays
      enabled even on AC. If we don't do this, we can't control the
      transmit power at all because we let the chipset handle it.
      Closes: #481180.
    * Replace *_ENABLE_HAL_POLLING settings by *_DISABLE_HAL_POLLING.
      More intuitive that way. The old settings were also interpreted
      in reverse. The backward compatibility layer actually *fixes that*
      because it was a bug, so behaviour will change for 1.42
      installations. Closes: #482307.
    * Get rid of bashism in laptop-mode module.
  * Put URL on separate line in README. Closes: #486467.
  * Set DM-Upload-Allowed field to yes.
  * Fix bashism in lm-profiler script. Closes: #480606
  -- Tormod Volden <debian.tormod@gmail.com>   Wed, 06 Aug 2008 20:06:08 +0200

---

### Post by olskar on 2008-08-14
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

Affects   Status         Importance

Suse   	  Fix Released   Unknown 
Debian	  Fix Released   Unknown 
Ubuntu    Triaged   	 Critical 


E.g no fix yet for Ubuntu

---

### Post by hexion on 2008-08-14
I guess you all already read somewhere this workaround, but just in case..
This is the only one that worked here.

sudo pico /etc/rc.local

Add this line before the "exit 0":
hdparm -B 255 /dev/sda

Until the devs solve the issue, that should do the job.

---

