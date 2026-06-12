---
title: "Auto updaye problem?"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by kiwi-pete on 2008-08-27
Here is the error I get with the Update Manager;

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

Here is what I get when I click on the Run this Action Now button;
An error occured

The following details are provided:
W: GPG error: [http://falcon.landure.fr](http://falcon.landure.fr) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CA3E3239FA7DC39
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release](http://wine.budgetdedicated.com/apt/dists/hardy/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.

What's going on here?
I have version 8.04.1

---

### Post by Partyboi2 on 2008-08-27
open a terminal and try re adding the key
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` then
```
 sudo apt-get update
```

---

### Post by kiwi-pete on 2008-08-27
> **Partyboi2 said:**
> open a terminal and try re adding the key
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` then
```
 sudo apt-get update
```

I get this error on the first command.
gpg: no valid OpenPGP data found.

---

### Post by Beth1957 on 2008-09-10
> **Partyboi2 said:**
> open a terminal and try re adding the key
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` then
```
 sudo apt-get update
```
Cheers Partyboi2; I was having the same problem with the authentication key for Wine and this solved it.
However, Wine isn't working; when I click on an .exe file & select "open with wine..." I get a brief flicker on the screen & nothing else happens. Any advice please?
Running HH, Wine is the one downloaded from Synaptic Package Manager.
Cheers,

---

### Post by Partyboi2 on 2008-09-10
> **Beth1957 said:**
> Cheers Partyboi2; I was having the same problem with the authentication key for Wine and this solved it.
However, Wine isn't working; when I click on an .exe file & select "open with wine..." I get a brief flicker on the screen & nothing else happens. Any advice please?
Running HH, Wine is the one downloaded from Synaptic Package Manager.
Cheers,
try starting the program from a terminal
```
wine <program.exe>
``` and see what happens

---

### Post by kiwi-pete on 2008-09-28
Thanks for all the help and suggestions, I have done a fresh install of Ubuntu and am in the middle of re-installing everything, being careful about what i put back. :)

---

### Post by WWSmith36 on 2008-09-28
I am curious about the contents of you source list.  Can you please post the output of

```
cat /etc/atp/sources.list
```

Thank you

---

### Post by kiwi-pete on 2008-09-28
cat: /etc/atp/sources.list: No such file or directory

---

### Post by Partyboi2 on 2008-09-28
That command is spelled wrong, its meant to be
```
cat /etc/apt/sources.list
```> I am curious about the contents of you source list.  Can you please post the output of They have reinstalled so there sources.list would be a vanilla one.

---

### Post by WWSmith36 on 2008-09-28
Sorry about the typo, its

```
cat /etc/apt/sources.list
```

---

### Post by kiwi-pete on 2008-09-28
kiwipete@ubuntu-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
kiwipete@ubuntu-laptop:~$ 

I do find however that as a sole user of this laptop, I no longer have access to the root or sudo powers if I go into the "file system" from within the "Places" menu. I can assign sudo to kiwipete using sudo su in terminal. Last install time I was able to do all manner of things from anywhere, esp accessing "etc" files and "usr" files etc etc.

---

### Post by Partyboi2 on 2008-09-28
> I do find however that as a sole user of this laptop, I no longer have access to the root or sudo powers if I go into the "file system" from within the "Places" menu. I can assign sudo to kiwipete using sudo su in terminal. Last install time I was able to do all manner of things from anywhere, esp accessing "etc" files and "usr" files etc etc.
You mean you cannot write to anything outside your /home directory or that you can not read anything outside your /home directory? You should be able to read the files in /etc /boot etc just not write to them without admin privileges.

---

### Post by kiwi-pete on 2008-09-28
> **Partyboi2 said:**
> You mean you cannot write to anything outside your /home directory or that you can not read anything outside your /home directory? You should be able to read the files in /etc /boot etc just not write to them without admin privileges.

Yes I mean I cannot write to them anymore. I used to be able to before I did a fresh install, but cannot remember what I did to allow this.
Its handy for adding some of the many M$ fonts I have that I like to use, etc etc etc.

---

### Post by Partyboi2 on 2008-09-29
For security purpose ubuntu is setup so that you cannot write to files outside your /home directory without admin rights. What you might find useful is that you can run a couple of scripts to open a file or location with admin rights with basically a click of the mouse. Have a read through of [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/NautilusScriptsHowto#Edit%20file%20with%20gedit%20with%20root-privileges") I would recommend 
"Edit file with gedit with root-privileges" "Open Nautilus with root-privileges here" and "Run file with root privileges" You may find some of the others useful as well.

---

### Post by kiwi-pete on 2008-09-29
Hmmm, these scripts seem a little confusing to me sorry. Is there an easier way to gain admin rights from log on? I know it was that way in the last install as I could access everything from the places drop down menu.

---

