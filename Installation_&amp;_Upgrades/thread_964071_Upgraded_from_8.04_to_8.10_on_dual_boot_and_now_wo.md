---
title: "Upgraded from 8.04 to 8.10 on dual boot and now won't boot at all"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by jf1991999 on 2008-10-30
I am using an HP Pavilion dv6000.  I have had it set up to dual boot between vista and 8.04.

Today I used the update option to upgrade.  It took over 2 hours to search for old applications.  The update finally finished and asked to reboot.  When the system relaunches I have the old options of booting vista or 8.04.  When I select 8.04, Ubuntu appears to boot normally and then goes to a screen with 5 text lines the last being:

Running local boot scripts (/etc/rc.local)  OK

It doesn't progress after this.  I rebooted again after waiting about 30 minutes and got the same result.

I hope I haven't killed my system.  Is this issue that the initial screen with my boot options does not list 8.10 and so will not boot?  Any help would be appreciated.  While I have used ubuntu for well over 18 months I am really just a novice.****

---

### Post by lemming465 on 2008-11-01
You are another victim of of some regressions in legacy ATI or Nvidia graphics drivers with the new X server, alas.  If you check /var/log/X.0.log it will probably contain a lament about not finding any usable screens.  You can probably log in using terminal sessions on the virtual consoles (e.g. press ALT-F2).  You can try changing to *Driver "vesa"* in /etc/X11/xorg.conf as a temporary expedient.  Otherwise you may want to consider downgrading back to 8.04; the easiest way to do that would be with a reinstall.

---

### Post by Craige4107 on 2008-11-01
> **jf1991999 said:**
> I am using an HP Pavilion dv6000.  I have had it set up to dual boot between vista and 8.04.

Today I used the update option to upgrade.  It took over 2 hours to search for old applications.  The update finally finished and asked to reboot.  When the system relaunches I have the old options of booting vista or 8.04.  When I select 8.04, Ubuntu appears to boot normally and then goes to a screen with 5 text lines the last being:

Running local boot scripts (/etc/rc.local)  OK

It doesn't progress after this.  I rebooted again after waiting about 30 minutes and got the same result.

I hope I haven't killed my system.  Is this issue that the initial screen with my boot options does not list 8.10 and so will not boot?  Any help would be appreciated.  While I have used ubuntu for well over 18 months I am really just a novice.****
That's exactly what happened on my laptop JF.  Toshiba Satellite, AMD Turion64, with ATI Video and Realtek NICs.  Was too frustrated at this point, after my 3rd attempt to install 8.10.  Reinstalled my OS, and partitioned for my next try with Linux.  I don't think it'll be Ubuntu though.  Good Luck.

---

### Post by raucous1 on 2008-11-01
I am having the same problem. Tried to upgrade my Dell Inspiron 9300 laptop to from Hardy to Intrepid, and now I can't get past (/etc/rc.local). Any suggestions?

---

### Post by ajacx on 2008-11-01
> **raucous1 said:**
> I am having the same problem. Tried to upgrade my Dell Inspiron 9300 laptop to from Hardy to Intrepid, and now I can't get past (/etc/rc.local). Any suggestions?

You might want to see this thread [http://ubuntuforums.org/showthread.php?t=963774](http://ubuntuforums.org/showthread.php?t=963774), where several people had the same issue, and it looks like some of them tried fresh installs, or went back to 8.04 till the nvidia problem is fixed.

I've got a question, because my update was a disaster and even the new kernels were not installed. So my grub menu only has the old 8.04 2.6.21-24 kernel options (I checked my boot directory, they're the only ones installed there). Does your grub menu have the new kernels as options (note that this also seems to be an issue for some, even if the new kernels have been installed, grub hasn't always been updated, as far as I could tell from other posts on this forum)?

---

