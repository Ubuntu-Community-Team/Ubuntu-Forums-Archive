---
title: "Cannot updgrade from 16.04 to 18.04 Error in update?"
date: 2019-09-07
forum: Installation &amp; Upgrades
---

### Post by richardlc on 2019-09-07
At the end of each update the following phrases appear:

                        Reading package lists... Done

 W: Problem unlinking the file lists.old - Clean (21: Is a directory)

  
Upgrades work after that, but after an exhaustive process of installing 18.04 LTS online I am informed that the installation fails.

I don't really want to install from the ISO that I now have on a thumb drive of 18.04 LTS, because I understand that I shall have to reformat the HDD and therefore reinstall all settings and files from Backup.  I was able to upgrade from 16.04 LTS on my wife's machine without problems to 18.04 LTS.

This error has been there for at least a year with no apparent effect on upgrades at all.  Today I did a successful "full-upgrade" 
 Can someone please explain it and correct it?

---

### Post by CatKiller on 2019-09-07
I've not ever seen the issue that you're having, but this error

```
W: Problem unlinking the file lists.old - Clean (21: Is a directory)
``` 
is saying that a file it's trying to clean up (lists.old) is unexpectedly a directory. Since it's an error that crops up as part of the upgrade process, I'd imagine that it's in /etc/apt. Deleting or renaming the lists.old directory should clear that error.

---

### Post by cruzer001 on 2019-09-07
Yes
Sounds like you modified your sources list.  Please post the output of:
```
ls /etc/apt
```

---

### Post by richardlc on 2019-09-07
Many thanks for the prompt replies.  The statement appears at the end of the update not the upgrades which seem to work well without error.
```

 rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ ls /etc/apt
apt.conf.d     sources.list              sources.list.save  trusted.gpg~
auth.conf.d    sources.list.d            trustdb.gpg        trusted.gpg.d
preferences.d  sources.list.distUpgrade  trusted.gpg
rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ 


```
I hope that the listing helps. 
What does W: signify?
Regards
richardlc

---

### Post by CatKiller on 2019-09-08
> **richardlc said:**
> What does W: signify?

Warning.

As opposed to E: Error or I: Information.

---

### Post by cruzer001 on 2019-09-08
Well, we both expected it to be there but its not.  Like CatKiller said, its a warning and will not affect updates.  Could go away with a reboot.

You can search your file system for it or just not concern yourself with it.  It upgrades, so its good.

---

### Post by richardlc on 2019-09-09
Thank you very much.  And for fixing the broken code brackets: I think I have now worked out from all the excellent Wiki contents how to put them in properly! 

Meanwhile, although it will do upgrades all the time, it won't do a "release-upgrade" without the error or warning at the end of the process, so I shall search the system as you suggested for the errant directory.  I can't remember how to do that at present, but will revise my terminal techniques to do so!  I shall return with the results in due course!

---

### Post by cruzer001 on 2019-09-09
Please post
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```
Also clean the package system, see if it helps.
```
sudo apt autoremove && sudo apt clean
```
Verify the cache is clean, should show all zero's.
```
du -ch /var/cache/apt/archives/
```
If packages still remain in cache
```
sudo rm -r /var/cache/apt/archives/*
```
and reboot

---

### Post by richardlc on 2019-09-13
Many thanks again.  Here is the response to your command on the terminal.  I shall be interested to know what it means.  I have also tried a search for  lists.old in directories which I shall show you after your response to this suggestion.


```
rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial universe
deb-src http://archive.ubuntu.com/ubuntu xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
deb-src http://archive.ubuntu.com/ubuntu xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
deb-src http://archive.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

# deb http://download.virtualbox.org/virtualbox/debian xenial contrib # disabled on upgrade to xenial
# deb-src http://download.virtualbox.org/virtualbox/debian xenial contrib # disabled on upgrade to xenial
/etc/apt/sources.list.d/librecad-dev-ubuntu-librecad-stable-xenial.list
/etc/apt/sources.list.d/skype-stable.list
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list
rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ 


```

---

### Post by cruzer001 on 2019-09-13
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
That line needs to either be removed or commented (#) out.
```
sudo -H gedit /etc/apt/sources.list
```
And you need to disable all PPAs.
librecad
skype
yannubuntu

Should be able to do that with your sources gui.
```
software-properties-gtk
```
Then update and upgrade

That should allow you to move on to 18.04

---

### Post by richardlc on 2019-09-13
Very many thanks Cruzer! I shall let you know how it goes.

---

### Post by richardlc on 2019-09-14
Thank you again.  I performed the actions successfully, but on doing an update, received the same warning, W: as documented originally on the subject of "lists.old".

On 10th September I did a search as mentioned previously.  I enclose the result below, and ask whether this will still interfere with the release upgrade.  As permission to access the "lists.old" is denied is there any way to remove these "directories"?

                        ```
rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ find ~ -type d -name "lists.old"

 find: ‘/home/rlcooper/.cache/dconf’: Permission denied
 find: ‘/home/rlcooper/.gvfs’: Permission denied
 rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ ^C
 
 

```

 
Many thanks for your patience!

---

### Post by CatKiller on 2019-09-14
The directory you're interested in won't be in your Home directory, which is where you're searching with that command. The two results that you listed aren't matches, they're just showing that the find tool is having trouble working with the virtual files.

Somewhere in /etc/apt/, /var/cache/, or /tmp/would be likely places for apt's scripts to be creating and deleting files, I'd imagine.

---

### Post by cruzer001 on 2019-09-15
Check this out

[https://askubuntu.com/questions/89393/how-to-search-entire-hard-drive-for-a-file](https://askubuntu.com/questions/89393/how-to-search-entire-hard-drive-for-a-file)

---

### Post by richardlc on 2019-09-20
Thank you, again.
 I tried to locate 'lists.old' by using 'locate' and unearthed 3 or so pages  of them as posted below.  I am ignorant as to whether any of these are causing the warning notice 'W'  in 'update', and if so whether I can delete any of these instances safely.  I hope the list is not too big!

                           ```
rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ sudo locate -i "lists.old"

 [sudo] password for rlcooper:  

 /var/lib/apt/lists/lists.old

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_Release

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_Release.gpg

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.canonical.com_ubuntu_dists_trusty_partner_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_Release

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_Release.gpg

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_main_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_Release
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_Release.gpg
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_main_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-security_universe_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release.gpg

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_main_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_Release
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fAU

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_main_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fAU
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_source_Sources

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en%5fAU
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_restricted_source_Sources
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en%5fAU

 /var/lib/apt/lists/lists.old/archive.ubuntu.com_ubuntu_dists_trusty_universe_source_Sources
 /var/lib/apt/lists/lists.old/extras.ubuntu.com_ubuntu_dists_trusty_Release
 /var/lib/apt/lists/lists.old/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg
 /var/lib/apt/lists/lists.old/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
 /var/lib/apt/lists/lists.old/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages

 /var/lib/apt/lists/lists.old/extras.ubuntu.com_ubuntu_dists_trusty_main_source_Sources

 /var/lib/apt/lists/lists.old/lock

 /var/lib/apt/lists/lists.old/partial
 /var/lib/apt/lists/lists.old/partial/archive.canonical.com_ubuntu_dists_trusty_Release.gpg.reverify
 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty-backports_Release.gpg.reverify
 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty-security_Release.gpg.reverify
 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release.gpg.reverify

 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg.reverify

 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages

 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages.decomp.FAILED
 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
 /var/lib/apt/lists/lists.old/partial/archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages.decomp.FAILED
 /var/lib/apt/lists/lists.old/partial/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg.reverify
 rlcooper@rlcooper-HP-250-G3-Notebook-PC:~$ 

 
 
  
```

---

### Post by cruzer001 on 2019-09-20
Congratulations!  You found it, now nuke it :)
```
sudo rm -r /var/lib/apt/list/list.old
```
That directory should not of been there in the first place.

---

### Post by richardlc on 2019-09-20
Fantastic!  :P  That has removed the warning and probably solved the installation fault/failure  of the distribution upgrade to 18,04 LTS which I shall try soon!
Thank you very much for all the patient help and expertise!

---

### Post by cruzer001 on 2019-09-21
Your welcome

Keep in mind that your install has fragments of 8.04 still floating around.  This can easily cause system glitches.  You are **overdue** for a fresh install.  When you decide to upgrade to 20.04 I would suggest a fresh install instead of a release upgrade.

---

