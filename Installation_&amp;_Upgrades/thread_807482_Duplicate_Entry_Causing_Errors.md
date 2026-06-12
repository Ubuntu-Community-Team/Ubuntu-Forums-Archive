---
title: "Duplicate Entry Causing Errors"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by CrazyCanuck on 2008-05-25
Here is the error message:

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file /var/lib/dpkg/available
.
.
.

The actual error is a duplicate entry found in this file.  Here is the entry:

This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXrandr
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>J
Package: os-prober
Priority: extra
Section: utils
Installed-Size: 160
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Architecture: amd64
Version: 1.23ubuntu1
Size: 16660
Description: utility to detect other OSes on a set of drives
 This package detects other OSes available on a system and outputs the
 results in a generic machine-readable format.
Original-Maintainer: Debian Install System Team <debian-boot@lists.debian.org>

As you can see, there are TWO "Original-Maintainer" entries.  Is it safe to remove one of the entries, please let me know.

I am not able to update my OS (Hardy) and am not able to install anything else at all.  Hope you respond soon.  :)

P.S. My keyboard does not seem to be functioning as a QWERTY keyboard, I seem to be missing things such as my question mark, and asterisk, and ampersand.  Any ideas. (I dont know where my question mark key is lol so i cant use it, sorry)

CC

---

### Post by iaculallad on 2008-05-25
> **CrazyCanuck said:**
> Here is the error message:

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file /var/lib/dpkg/available
.
.
.

The actual error is a duplicate entry found in this file.  Here is the entry:

This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXrandr
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>J
Package: os-prober
Priority: extra
Section: utils
Installed-Size: 160
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Architecture: amd64
Version: 1.23ubuntu1
Size: 16660
Description: utility to detect other OSes on a set of drives
 This package detects other OSes available on a system and outputs the
 results in a generic machine-readable format.
Original-Maintainer: Debian Install System Team <debian-boot@lists.debian.org>

As you can see, there are TWO "Original-Maintainer" entries.  Is it safe to remove one of the entries, please let me know.

I am not able to update my OS (Hardy) and am not able to install anything else at all.  Hope you respond soon.  :)

P.S. My keyboard does not seem to be functioning as a QWERTY keyboard, I seem to be missing things such as my question mark, and asterisk, and ampersand.  Any ideas. (I dont know where my question mark key is lol so i cant use it, sorry)

CC

Try commenting both and issue the commands on your terminal:

Code:

> sudo apt-get update

As for the keyboard issue:

System->Preferences->Keyboard

and on the "Layouts" tab, select the "Generic 105-key (Intl) PC".

---

### Post by CrazyCanuck on 2008-05-25
Ok, two things.

Firstly, I can use // to remark lines of code, right.  If not, please tell me.

Secondly, I seem to not have proper authorization to save the file in question.  I installed with default settings, and I am the only user configured to operate in the OS.  Any ideas....and I will go alter my keyboard settings as I wait for a response.

Thanks much.

CC

---

### Post by CrazyCanuck on 2008-05-25
Ok, I went to change my keyboard settings, and discovered it already is at the proposed fix.  For some reason, my keyboard is not functioning as it should even though it is set at default as was suggested earlier.

CC

---

### Post by CrazyCanuck on 2008-05-25
Am I needing to alter my authorization in order to save a file...I am trying to save a file and for some odd reason, I am being told I am unauthorized to do so, even though I am the only user in the system.

CC

---

### Post by iaculallad on 2008-05-25
> **CrazyCanuck said:**
> Am I needing to alter my authorization in order to save a file...I am trying to save a file and for some odd reason, I am being told I am unauthorized to do so, even though I am the only user in the system.

CC

Make sure that you have the proper privilege/authorization in order for you to save changes on your system.

For the keyboard problem, try executing **setxkbmap**.

---

### Post by CrazyCanuck on 2008-05-25
setxkbmap did not work.  Keyboard still works fine, but I am missing keys, like something is lost is translation.

CC

---

### Post by ChameleonDave on 2008-05-25
> **CrazyCanuck said:**
> Am I needing to alter my authorization in order to save a file...I am trying to save a file and for some odd reason, I am being told I am unauthorized to do so, even though I am the only user in the system.

CC
To perform a command that requires admin privileges, put "sudo" before it.

For example, type "sudo rm -fr /boot" if you want to make your system unbootable.  ;-)

---

### Post by CrazyCanuck on 2008-05-25
LOL

Well, I tried:

sudo setxkbmap

...no effect.  How strange, I get everything up and running, then get a duplicate entry error, cant save the file once I edited it, and keyboard is not working, even though it appears as it should be working fine.

CC

---

### Post by CrazyCanuck on 2008-05-25
Ok, to recap.

I need to discover how to ensure I am a superuser on my OS.  For some reason, once I installed, logged in, I am not able to save any file(s) I edit.

My keyboard has been installed with the default system setting, and not working correctly.  I am missing my asterix, ampersand, and question mark keys.  They probably are mapped elsewhere on the keyboard, this is currently unknown.  Possibly missing other keys too, unsure.

I have been trying to get all the updates, and during the update process, got a duplicate entry error.  It has been suggested I rem out both entries.  Is // the proper way to remark out lines of code.  Sorry, no question mark...:(

CC

---

### Post by iaculallad on 2008-05-25
> **CrazyCanuck said:**
> Ok, two things.

Firstly, I can use // to remark lines of code, right.  If not, please tell me.

Secondly, I seem to not have proper authorization to save the file in question.  I installed with default settings, and I am the only user configured to operate in the OS.  Any ideas....and I will go alter my keyboard settings as I wait for a response.

Thanks much.

CC

Post us your /etc/apt/sources.list

Code:

> cat /etc/apt/sources.list

---

### Post by CrazyCanuck on 2008-05-25
here you go.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by ChameleonDave on 2008-05-25
Well, we should probably deal with the main problem first.

```
cd /var/lib/dpkg/
sudo mkdir info.backup
sudo mv info/os-probe* info.backup/
sudo apt-get purge os-prober
sudo apt-get update
```

This might fix it.  No promises though.  It could make your PC catch fire and devour your cat.

---

### Post by CrazyCanuck on 2008-05-25
Thanks Dave, it did not work.  Attempt at updating gave me the same error message with duplicate fields of Original-Maintainer entries.

CC

---

### Post by CrazyCanuck on 2008-05-25
Here is the entry I am attempting to edit.

Here is the error message:

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file /var/lib/dpkg/available
.
.
.

The actual error is a duplicate entry found in this file. Here is the entry:

This module can be found at
git://anongit.freedesktop.org/git/xorg/lib/libXrandr
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>J
Package: os-prober
Priority: extra
Section: utils
Installed-Size: 160
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Architecture: amd64
Version: 1.23ubuntu1
Size: 16660
Description: utility to detect other OSes on a set of drives
This package detects other OSes available on a system and outputs the
results in a generic machine-readable format.
Original-Maintainer: Debian Install System Team <debian-boot@lists.debian.org>

The file is:

/var/lib/dpkg/available

I am not able to alter this file.  System says I am not authorized to do so.

As you can see there is a duplicate entry here, that needs to be resolved.  I am not able to update the OS or do any installations of any packages.

Second issue, is a keyboard that does not function as it should be using the default keyboard setting once it was installed.  I am missing my question mark, and am unable to type out an email address.

Hope this brings you all to speed.

CC

---

### Post by iaculallad on 2008-05-25
To edit with priveledge, enter the command:

Code:

> sudo gedit /var/lib/dpkg/available

---

### Post by CrazyCanuck on 2008-05-25
Ok, that command allowed to me save the file.  I am requiring proper remark keystrokes now.  Do I remark out the entire field as shown or just the two duplicate entries, I am unsure.

CC

---

### Post by iaculallad on 2008-05-25
> **CrazyCanuck said:**
> Ok, that command allowed to me save the file.  I am requiring proper remark keystrokes now.  Do I remark out the entire field as shown or just the two duplicate entries, I am unsure.

CC

what about doing:

sudo cp /var/lib/dpkg/available /var/lib/dpkg/available.bak
cd /var/lib/dpkg
sudo rm available
sudo apt-get update

---

### Post by CrazyCanuck on 2008-05-25
Renaming the "available" file to available.bak did not work.  Now I have a missing file error.  We are getting closer.

CC

---

### Post by CrazyCanuck on 2008-05-25
Missing file issue has been resolved.

Duplicate entry error within "available" file remains to hinder my ability to update and/or install packages.

CC

---

### Post by iaculallad on 2008-05-25
> **CrazyCanuck said:**
> Missing file issue has been resolved.

Duplicate entry error within "available" file remains to hinder my ability to update and/or install packages.

CC

What about reversing the process again:

Code:
> sudo cp /var/lib/dpkg/available.bak /var/lib/dpkg/available

And issue the command below since we're configuring python in var/lib/dpkg/available.

Code:
> sudo dpkg --configure python2.5-minimal
sudo apt-get update

---

### Post by CrazyCanuck on 2008-05-25
Reversing the process maintains the duplicate entry issue within "available".  Not able to update system files.  Thankyou for being patient, I am not a slouch, just silly-new to Ubuntu.  I will get better the more times I do things inside of Hardy.

CC

---

### Post by CrazyCanuck on 2008-05-26
UPDATE:

If you are living in Canada, and are not using a French OS or keyboard, do not select Canada as your keyboard layout during the installation phase of Hardy.  If you select Canada as your keyboard layout, you will lose functionality of certain keys: they disappear or get re-mapped.

Chose USA as your keyboard layout, and your OS and keyboard will thank you. :)

I just re-installed Hardy, and am now going to try to download the updates and see what happens next.

CC

---

