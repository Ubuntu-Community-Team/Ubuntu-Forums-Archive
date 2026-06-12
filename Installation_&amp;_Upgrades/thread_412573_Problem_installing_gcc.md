---
title: "Problem installing gcc"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by esb on 2007-04-18
I have as I have seen many others before me, a problem with the need of gcc to get a program installed on my computer. I have already seen that I should write 

>sudo apt-get update
>sudo apt-get install gcc
>sudo apt-get install build-essential

The first command runs ok, but the second gives the following prompt:
"
Need to get 0B/3942kB of archives.
After unpacking 13.1MB of additional disk space will be used.
Do you want to continue [Y/n]
"

 I press y and get the message:

"
Media change: please insert the disc labeled
 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)'
in the drive '/cdrom/' and press enter
"

My problem is that I use a computer that I have borrowed wih Ubuntu already installed (but with permission to install new programs and features of course), and do not have the requested CD.

How can I work around this problem? Anyone?
If this thread is  in the wrong forum, please inform me so that I can post a message in a more suited one.
Esb

---

### Post by dreadlord_chris on 2007-04-18
In a terminal:
```

sudo nano /etc/apt/sources.list

```
This will open your Repositories list for editing. Look for the CDROM line and comment it out - put ## at the beginning of the line.
Save the file - Control-x > Y > Enter (leave the filename the same)

apt* *should* stop asking for a CD now

---

### Post by esb on 2007-04-18
Thanks! That worked :-)

---

