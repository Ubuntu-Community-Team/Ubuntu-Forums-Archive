---
title: "Upgrade 10.04 from 32 bit to 64 bit"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by caradeporra on 2010-10-14
Hello all,

  I have searched and scoured for a good tutorial on the easiest way to upgrade from 32 bit to 64 bit.  I just got a memory upgrade to 8Gb and I don't want that money to be wasted since my 32 bit install will not see it.  If there is a way to get my 32 bit system to see all the RAM I would appreciate that.

  Other than that, I would like to know what to back up so I can keep as many settings as possible the same.  I am a not an expert on which programs will be different.  The main programs I use are as follows:

VirtualBox
KMyMoney
QuantaPlus
GKrell
Screenlets
Tellico
RubyMine

  I assume the easiest thing would be to just back up all my files and reinstall these programs.  Main question is what folders can I back up?  Home folder is a given, but what other folders will remain the same from 32 bit to 64 bit.

  If anyone knows of a tutorial out there that goes through all this it would be much appreciated.

Carade

---

### Post by cascade9 on 2010-10-14
You can tupgrade from 32bit to 64bit, you would need to reinstall. 

Getting a PAE kernel would let you see all the RAM, but 64bit is a better option IMO.

---

### Post by Slim Odds on 2010-10-14
This keeps coming up again and again.

You're wasting your time and everyone else's.

Just backup your data and install the 64 bit version.

---

### Post by caradeporra on 2010-10-14
Cascade, thanks for your input - I agree with you that 64bit is the better option.

Slim, mucho sorry to waste your time.  I realize one can't upgrade directly to 64 bit. I understand that in order to upgrade one needs to format and install 64 bit.  My main question, and I should have made this clearer, is what to back up.  I mean, it isn't the same as a complete backup/restore would be since it will be 64 bit kernels and files.  What files can be backed up?

Mainly, is there a way to back up RubyMine or do I simply need to reinstall and reconfigure it entirely.  What about VirtualBox...will the VBoxManage clonehd backup/restore method work to 64 bit?  Or will those all need to be reconfigured from scratch as well.  What about system settings, all from scratch also?


Thank you!

---

### Post by oldos2er on 2010-10-14
If you have /home on a separate partition from /, opt not to format /home when you install 64-bit. If not, you'd want to save all the hidden files and folders and in your /home which contain program settings, etc.

---

### Post by Slim Odds on 2010-10-14
> **caradeporra said:**
> Cascade, thanks for your input - I agree with you that 64bit is the better option.

Slim, mucho sorry to waste your time.  I realize one can't upgrade directly to 64 bit. I understand that in order to upgrade one needs to format and install 64 bit.  My main question, and I should have made this clearer, is what to back up.  I mean, it isn't the same as a complete backup/restore would be since it will be 64 bit kernels and files.  What files can be backed up?

Mainly, is there a way to back up RubyMine or do I simply need to reinstall and reconfigure it entirely.  What about VirtualBox...will the VBoxManage clonehd backup/restore method work to 64 bit?  Or will those all need to be reconfigured from scratch as well.  What about system settings, all from scratch also?


Thank you!

Sorry, I didn't mean to get on your case. But this "upgrade from 32 to 64" is usually someone wanting a magic bullet so they don't actually have to install the 64 bit from scratch.

Indeed, your home folder is most important. There may also be some configuration files in /etc/ that you want to preserve.

Stuff like special network settings, ssh config, etc. are in that tree.

---

### Post by caradeporra on 2010-10-14
Thanks oldos and slim, that's helpful.

Slim, I understand - that is why I am trying to get the real answers.  I tried to find a tutorial that talks about what all to back up but haven't found any!  I do have network settings I would like to keep.  I have my entire /home folder backed up in a tar file.  Any ideas on what else can be backed up.  All of the backup/restore tutorials I have found are wrapped around simple backups and restores, not for upgrades - and especially for upgrades to 64 bit.

---

