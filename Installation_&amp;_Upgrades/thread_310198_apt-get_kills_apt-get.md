---
title: "apt-get kills apt-get"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by rdoolen on 2006-11-30
I am pretty new to Ubuntu and things had been going smoothly. However, I tried to upgrade from Dapper to Edgy. It froze in the middle and before I could make note of anything, it rebooted. I guess I should say it tried to reboot, but couldn't.

The good news, I thought, was that I backed up the system just before I tried to upgrade. I booted from the CD and tried to restore the system. I basically followed the guide found here: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Things seemed ok at first, but anytime I try to install an update, in update manager, synaptic or apt-get, things go horibly wrong, many programs won't run, including launching the terminal from gnome. 

When I run apt-get upgrade I see this numerous times:
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.

Followed by:

Errors were encountered while processing:
 hal
 hal-device-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)


When I do try to launch things from a terminal, I get the error:

apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)



The only thing I noticed that was odd about the restore was the message "tar: Error exit delayed from previous errors" at the end of the extration of the back-up file. There was no indication of any 'previous errors.' Also, the backup and restore guide said I would have to re make un-backed up directories, like lost+found, but they are already there.

I also tried restoring from an older back-up but that seems to act in the same way.

It is not clear that the failed upgrade caused my problem.

Any help would be apreciated.

---

### Post by taurus on 2006-11-30
The first question is how did you upgrade from Dapper to Edgy???

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by rdoolen on 2006-11-30
I tried my best to follow the directions as they appeared. I initiated the upgrade with:

gksu "update-manager -c"

---

### Post by rdoolen on 2006-12-01
Well, I have at least been able to restore my system.

I went back and read ALL of the instructions 

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem). 

I noticed a line that said that files made since the backup are not over-written. I figured some left over files that were not replaced during the restore were screwing things up. I deleted lots of stuff,  then restored, and my system went back to exactly the way it was. I actually made some mistakes deleting things, like sudo, that made it impossible to restore without the liveCD, but that was no problem. Now things seem to be exactly as they were.

The question remains, why did the upgrade crash in the first place. Now that I am resonably confident that I can restore my system, I might just try again. Is there a way to generate a log of what is happening? That might make it easier to track down the problem.

---

