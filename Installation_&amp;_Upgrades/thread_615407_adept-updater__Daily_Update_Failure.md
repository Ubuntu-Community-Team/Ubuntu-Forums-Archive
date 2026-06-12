---
title: "adept-updater:  Daily Update Failure"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by tokyotea on 2007-11-17
Maybe a Newbie-grade Situation and Question

OS is Kubuntu 7.10

1.  adept-updater says that updates are available so I log in
2.  adept tells me that three Samba-related packages are available for updating
3.  I tell it to go ahead and make the updates
4.  the update fails
5.  when the machine is rebooted video has been reset to 640x480x16 from 1280x1024x32

I have tried running the updater a couple of times in automatic mode with the same result.

I got out the APT HOW-TO and followed the instructions for manual installation of updates from the console.

I ran "apt-get update" before and "apt-get autoclean" after so I do not think there are any leftovers to make trouble.

Part of the verbose output from an instruction of "apt-get -u upgrade" is as follows:

=-=-=-=-=-=-=-=-=-=

Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

=-=-=-=-=-=-=-=-=-=

As far as I can tell, the respository is in the update path.

I can't find any other reason for the "403 Forbidden" result.

I have no idea why all of this keeps affecting my video settings (which are correctly auto-detected when I run video and display settings Administrator mode).

---

### Post by PmDematagoda on 2007-11-17
The updates are not available because they are currently made inaccessible by the Ubuntu Security Team due to suspicions that they may be defective, it has nothing to do with a system component. But the issue concerning Adept is rather strange, maybe you should report it on launchpad.

---

### Post by tokyotea on 2007-11-17
Thanks.  I did more digging and found a bit of the same information.  But you tied it together more logically.

---

### Post by AJB2K3 on 2007-11-17
**[SIZE="6"]FYIAnyone else with this see sticky at top of forum ![/SIZE]**

---

### Post by tokyotea on 2007-11-17
> **AJB2K3 said:**
> **[SIZE="6"]FYIAnyone else with this see sticky at top of forum ![/SIZE]**

You mean the one that has messages from June?  Perhaps the Subject line should be changed to indicate that it covers all 403 Failure problems.  I know I would have discovered that before I posted my question if there were some indication that the sticky covered more than that one issue back in June.  I saw it and rejected it out of hand.

One other point; as a new Kubuntu user who came here from a background that goes all the way back to punch cards and paper tape via WIN, it would have been better to see the sticky message in question begin with the admonition "Just because it isn't working now doesn't mean it is broken.  Just because it failed this time doesn't mean you, the new user, screwed something up."  

BTW, my particular upgrade problem has been fixed with the latest set of upgrades available now.

---

