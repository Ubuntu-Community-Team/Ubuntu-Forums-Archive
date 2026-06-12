---
title: "Hoary RC installation problem - ~/.Xsession-errors"
date: 2005-04-03
forum: Installation &amp; Upgrades
---

### Post by adbak on 2005-04-03
I downloaded the Release Candidate earlier today for Hoary and the md5sums matched.  I installed it, downloaded everything from the internet and when I got to the GDM login screen, after I put in my name and password, I got this error message:
```
Your session only lasted less than 10 seconds.  If you have not logged out yourself this could mean that there is some installation problemor that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
```
Then there's a checkbox with "View details (~/.Xsession-errors file)" written next to it.  I click on the box and get this:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/Sessreg -a -w /var/log/wtmp -u /var/run/wtmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "adam"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:20153):libgnomevfs-WARNING**: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/adam/.gnome2` Permission denied
```
NOTE: 'adam' is my username.

So I then hit Ctrl+Alt+F2 to get to a terminal and type "sudo mkdir .gnome2", hit Ctrl+Alt+F7 to get back to the login screen.  I log in and then get the same message, only this time it can't create the directory ~/.gnome2_private.  After I mkdir that folder, I then get this message after logging in through gdm:
```
Your session only lasted less than 10 seconds.  If you have not logged out yourself this could mean that there is some installation problemor that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/Sessreg -a -w /var/log/wtmp -u /var/run/wtmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "adam"
/etc/gdm/Xsession: Beginning session setup...

Could not set mode 0700 on private per-user configuration directory `/home/adam/.gnome2_private`: Operation not permitted
```

Anyone know how to help me get to the rockin' new Hoary?

Dell Dimension 4600
Pentium 4
512 DDR-SDRAM
nVidia GeForce4 mx 440

/dev/hda2 is FAT32 with 2.5gb of free space, not formatted because it holds my videos and music.
/dev/hda4 is ext3, formatted as '/' with 16gb capacity.
/dev/hda5 is ReiserFS, formatted as '/home' with 55gb capacity.
/dev/hda6 is swap, formatted as swap with 512mb capacity.

---

### Post by Gandalf on 2005-04-03
[QUOTE=adbak]I downloaded the Release Candidate earlier today for Hoary and the md5sums matched.  I installed it, downloaded everything from the internet and when I got to the GDM login screen, after I put in my name and password, I got this error message:
```
Your session only lasted less than 10 seconds.  If you have not logged out yourself this could mean that there is some installation problemor that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
```
Then there's a checkbox with "View details (~/.Xsession-errors file)" written next to it.  I click on the box and get this:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/Sessreg -a -w /var/log/wtmp -u /var/run/wtmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "adam"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:20153):libgnomevfs-WARNING**: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/adam/.gnome2` Permission denied
```
NOTE: 'adam' is my username.

So I then hit Ctrl+Alt+F2 to get to a terminal and type "sudo mkdir .gnome2", hit Ctrl+Alt+F7 to get back to the login screen.  I log in and then get the same message, only this time it can't create the directory ~/.gnome2_private.  After I mkdir that folder, I then get this message after logging in through gdm:
```
Your session only lasted less than 10 seconds.  If you have not logged out yourself this could mean that there is some installation problemor that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/Sessreg -a -w /var/log/wtmp -u /var/run/wtmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "adam"
/etc/gdm/Xsession: Beginning session setup...

Could not set mode 0700 on private per-user configuration directory `/home/adam/.gnome2_private`: Operation not permitted
```

Anyone know how to help me get to the rockin' new Hoary?

Dell Dimension 4600
Pentium 4
512 DDR-SDRAM
nVidia GeForce4 mx 440

/dev/hda2 is FAT32 with 2.5gb of free space, not formatted because it holds my videos and music.
/dev/hda4 is ext3, formatted as '/' with 16gb capacity.
/dev/hda5 is ReiserFS, formatted as '/home' with 55gb capacity.
/dev/hda6 is swap, formatted as swap with 512mb capacity.[/QUOTE]
 nope, yesterday i have downloaded/installed hoary, works perfectly

---

### Post by adbak on 2005-04-04
UPDATE:  I reinstalled Hoary RC but this time I didn't tell it to mount the FAT32 partition from installation.  I just added it to the fstab so we'll see how it reacts then.

EDIT:  I added "/dev/hda2     /home/adam/music     vfat    uid=500,gid=500,users,rw,umask=0000     0    0" to fstab and it will mount and give no errors, but it won't mount the partition on bootup.  In the scrolling messages after GRUB, it mentions that /home/adam/music does not exist, but I've already mkdir'd that folder.  Anyone know how I can have it set to mount on boot-up?

---

### Post by grendelkhan on 2005-04-04
why do you have the umask entry in there?  Since it's rw, you really don't need anything special.  I do it to my ntfs partition but I mount is as read only and I'm just enforcing that policy.

---

### Post by stenbock on 2005-04-05
I had the same problem but I don't now why. 
Press "ctrl alt f1" and login to the consol, there in your home folder type:
sudo chmop 777 .ICEa... just tab to get the whole name.

that worked for me

---

### Post by Topper on 2005-04-09
[QUOTE=stenbock]I had the same problem but I don't now why. 
Press "ctrl alt f1" and login to the consol, there in your home folder type:
sudo chmop 777 .ICEa... just tab to get the whole name.

that worked for me[/QUOTE]

I got the very same problem. I tried followig the above procedure(although I used chmod instead of chmop ;-)), but pressing tab-key after .ICEa doesn't give anything after I cd'ed to my home directory. Like it doesn't exist there...

Anyone got a clue what to do?

---

### Post by bsm2005 on 2005-04-19
Well I like th look & feel of the live cd but the install well lets just say that's another story. I have been using Mandrake/Mandriva for over 2 years and the latest crap they put out has pushed me away from it. I really need an answer to the above posts for I really,really,really want to installl this fine looking distro. I have tried all that was posted here to no avail.

---

### Post by bsm2005 on 2005-04-19
ok figured out a fix for this problem. login to term session then cd to /tmp/ then rm -rf /tmp/* hit enter then log out and start a default session of gnome and now all is well :-) \\:D/

---

