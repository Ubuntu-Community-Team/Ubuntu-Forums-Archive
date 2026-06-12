---
title: "Clean install grub2 fakeraid"
date: 2018-09-10
forum: Installation &amp; Upgrades
---

### Post by LinuxAlexs on 2018-09-10
Hi

I am trying to do a clean install of Ubuntu, just accepted the defaults. Sadly booting gives a flashing cursor.

I have a fakeraid mirror on a Dell Vostro 200. I ran the repair utility as well...

More info:
[http://paste.ubuntu.com/p/Mv4Yq2Cws8](http://paste.ubuntu.com/p/Mv4Yq2Cws8)

Any ideas?

Thanks

---

### Post by oldfred on 2018-09-10
Did you try the fix from Boot-Repair.

The Ubuntu desktop installer does not work or does not work well with most RAID type configurations. But the server installer does work for RAID.

---

### Post by LinuxAlexs on 2018-09-10
I installed boot repair utility hence pastebin link. Follows it's instructions.
Ubuntu desktop was installed on mdadm.
Thx

---

### Post by oldfred on 2018-09-10
Last line says this:
The settings chosen by the user will not act on the boot.


Or did you run the report after running an update?

---

### Post by LinuxAlexs on 2018-09-11
Ah. I'll send another pastebin later today sorry. This was before I rebooted after running the repair utility.

---

### Post by LinuxAlexs on 2018-09-12
OK here is a report generated after reboot, many apologies..

[http://paste.ubuntu.com/p/PB4Qm9fdBv/](http://paste.ubuntu.com/p/PB4Qm9fdBv/)

---

### Post by oldfred on 2018-09-12
I do not know RAID, other than the desktop installer normally does not work with RAID. It used to not work at all, now it will install, but grub does not. Server install often required, then add desktop.

I also thought Boot-Repair then did work as it installs the server drivers. But it said this:
> mdadm packages needed

I have this in my notes:
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 
You may want to manually install mdadm before running Boot-Repair.

These are now older.
      
 User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)
Issues with encrypted FakeRAID
[https://ubuntuforums.org/showthread.php?t=2353942](https://ubuntuforums.org/showthread.php?t=2353942) 
    
       [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by LinuxAlexs on 2018-09-12
Yup that's exactly it. This method didn't work for 1.5 tb hard drive mirror but does work with 320GB mirror.

Thanks!!!!

Solved enough for me!

---

### Post by oldfred on 2018-09-12
Glad that worked.
You can change to [Solved].

---

