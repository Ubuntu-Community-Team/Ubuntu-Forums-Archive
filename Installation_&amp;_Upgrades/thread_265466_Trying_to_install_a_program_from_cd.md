---
title: "Trying to install a program from cd"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by penguinchrissy on 2006-09-26
I have a program called MATLab that I need to use for school and think this would be a really nice chance to try and use linux more because the program runs on linux. I'm having trouble installing it though I run through everything the book tells me to do but its no go.

```
dj@dj-laptop:~$ mkdir /cdrom
mkdir: cannot create directory `/cdrom': File exists
dj@dj-laptop:~$ mount /cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
dj@dj-laptop:~$ cd /usr/local/matlab71_sv
dj@dj-laptop:/usr/local/matlab71_sv$ /media/cdrom0/install_unix.sh
bash: /media/cdrom0/install_unix.sh: /bin/sh: bad interpreter: Permission denieddj@dj-laptop:/usr/local/matlab71_sv$ sudo /media/cdrom0/install_unix.sh
Password:
sudo: unable to execute /media/cdrom0/install_unix.sh: Permission denied
dj@dj-laptop:/usr/local/matlab71_sv$


```

As you can see I tried to do things stright from the book even though I knew they wouldn't work but I can't figure out why I'm the Premission denied. Any help would be great.

---

### Post by po0f on 2006-09-26
penguinchrissy,

Try copying the install script to your home directory and running it from there.

[EDIT]
```
$ cp /media/cdrom0/install_unix.sh ~
$ chmod u+x ~/install_unix.sh  # Just to make sure it has execute permission
$ ./install_unix.sh
```

---

