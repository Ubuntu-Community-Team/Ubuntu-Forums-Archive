---
title: "BACKUP HELP: Ubuntu 8.10 is not starting and I need to back-up my files"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by lostbuntu on 2010-03-12
***_1st:_*** [SOLVED] [http://ubuntuforums.org/showpost.php?p=8956304&postcount=10](http://ubuntuforums.org/showpost.php?p=8956304&postcount=10) thank you the [SalixOS GNU/Linux Team]("http://www.salixos.org/wiki/index.php/Salix_OS:Team") for all your help and attention!
It might be because of the last (or one of the latest) software updates of Canonical

Ubuntu 8.10 is showing its routine check up and after it showing a Terminal Interface with [[COLOR=Red]fail[/COLOR]]

How do I fix it?

*EDIT: Note: I'm using _**Lenovo 300 N100**_ (laptop)*


**_*2nd:*_** [SOLVED] [http://ubuntuforums.org/showpost.php?p=8954505&postcount=7](http://ubuntuforums.org/showpost.php?p=8954505&postcount=7) (thanks, sxmaxchine)
I'm going to install [Slax]("http://www.slax.org/") on a USB Drive to back up the rest of my personal information in my hard drive (where Ubuntu 8.10 is installed), _but_ some of the files (that I've made) cannot be read by other "groups" except the owner

Does anybody know _how to hack the permission_ to access ALL files and to copy them?



Please Help, ASAP.

---

### Post by lostbuntu on 2010-03-12
*_**P/s:**_*
I'm now running Ubuntu 8.10 _Live session user_ (LiveCD)

---

### Post by sxmaxchine on 2010-03-12
try running the live cd and put the files on a usb or you could also try making this portable damn small linux however you do need a windows pc to make it, info [here]("http://www.pendrivelinux.com/all-in-one-usb-dsl/")

---

### Post by lostbuntu on 2010-03-12
Hi, sxmaxchine, and thank you for replying ;)

I'm going to install Slax since I know it much better and I had similar problem before (when I had WinXP)

But will I be able to READ any sort of file, regardless to the permissions issue?

---

### Post by sxmaxchine on 2010-03-12
no worries hope you get your problem fixed

---

### Post by lostbuntu on 2010-03-12
I remember that I read some threads about [ClamAV false positive]("http://ubuntuforums.org/showthread.php?t=1021013") and someone wrote how to fix/reinstall broken ubuntu/packages


How do I fix broken packages?

How do I bypass file-permissions?

---

### Post by sxmaxchine on 2010-03-12
i dont know how to fix broken packages

to bypass file-permissions in ubuntu you could try running nautilus (file explorer) in super user mode to do this run below code in terminal.

sudo nautilus

you may also need to open the program in super user mode it is the same code just change the program name for example to run vlc in super mode run

sudo vlc

hope this helps

---

### Post by lostbuntu on 2010-03-12
Oops, lol!

SUDO, GKSU, etc.

I'm not using LiveCD much... :S

I mean, I already know it, but when it looks like that it is an end and there is nothing to do... I'm kinda not functioning right...

Thank you, sxmaxchine.



[SIZE=3]*OK, anyone knows how to fix a broken Ubuntu (8.10)*[/SIZE]

---

### Post by lostbuntu on 2010-03-12
I'm, now, using [Slax]("http://www.slax.org/") (my first ever GNU/Linux ride) since [it is very easy to install on a USB Drive]("http://www.slax.org/documentation_install_slax.php") (only a running script!)

and, it has [K3B]("http://en.wikipedia.org/wiki/K3b")!

I have only one laptop computer machine here so... you know why Slax is the only choice for this back-up task... ;)

---

### Post by lostbuntu on 2010-03-12
problem solved!!! Ubuntu 8.10 is on-line again

THANK YOU, to the [SalixOS]("http://www.salixos.org/") devs [JRD]("http://www.salixos.org/wiki/index.php/Salix_OS:Team#Cyrille_Pontvieux") and [gapan]("http://www.salixos.org/wiki/index.php/Salix_OS:Team#George_Vlahavas") for all their help!!!

I used [SalixOS LiveCD]("http://www.salixos.org/forum/viewtopic.php?f=17&t=530") (_note_: this can be done with ANY LiveCD)


run **_fsck_** (in my case it was: _**fsck /dev/sda1**_)

**fsck /dev/sda1**

```
root@salix:~# fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?
```> [18:03:34] lostbuntu: continue?
[18:05:51] JRD: lostbuntu, no
[18:05:55] JRD: you must unmount it**umount /dev/sda1**
**fsck /dev/sda1**

```
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
/dev/sda1: |======                                                  / 10.5%
/dev/sda1: |==================                                      / 31.7%
/dev/sda1: |=======================                                 - 41.7%
/dev/sda1: |========================================                - 64.1%
Pass 2: Checking directory structure
/dev/sda1: |=========================================               | 72.5%
/dev/sda1: |=============================================           | 80.6%
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 589955
Connect to /lost+found<y>?
```> [18:27:12] lostbuntu: Connect to /lost+found<y>?
[18:27:19] lostbuntu: what should I do now?
[18:27:07] JRD: answer yes
[18:27:10] JRD: you have no choice
[18:27:19] lostbuntu: ^_^
[18:28:02] lostbuntu: y pressed.```
Inode 589955 ref count is 2, should be 1.  Fix<y>?
```> JRD: answer yes```
Inode 589957 ref count is 1, should be 2.  Fix<y>?
```> JRD: answer yes```
Pass 5: Checking group summary information
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 222072/4702208 files (2.6% non-contiguous), 8205055/18788009 blocks
```> [18:32:42] JRD: you need to reboot now[SIZE=5]_**[COLOR=Lime][COLOR=LightBlue]![/COLOR][COLOR=Yellow]![/COLOR][COLOR=DarkOrange]![/COLOR] S[COLOR=Red]O[/COLOR][COLOR=Olive]L[/COLOR][COLOR=RoyalBlue]V[/COLOR][COLOR=Plum]E[/COLOR][COLOR=DeepSkyBlue]D [/COLOR][COLOR=YellowGreen]![/COLOR][/COLOR]**_[/SIZE][SIZE=5][COLOR=Black]_**!**_[/COLOR][/SIZE][SIZE=5]_**[COLOR=Lime][COLOR=Wheat]![/COLOR][/COLOR]**_[/SIZE]

---

