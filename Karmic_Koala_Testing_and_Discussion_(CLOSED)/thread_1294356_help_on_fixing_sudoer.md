---
title: "help on fixing sudoer"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-18
hacking again and messed up how do i correct

ay@ray-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
>>> /etc/sudoers: syntax error near line 25 <<<
sudo: parse error in /etc/sudoers near line 25
sudo: no valid sudoers sources found, quitting
ray@ray-desktop:~$ 



tks in advance

---

### Post by rburkartjo on 2009-10-18
and again

ray@ray-desktop:~$ sudo visudo
>>> /etc/sudoers: syntax error near line 25 <<<
sudo: parse error in /etc/sudoers near line 25
sudo: no valid sudoers sources found, quitting
ray@ray-desktop:~$

---

### Post by sisco311 on 2009-10-18
Reboot in Recovery Mode and edit the file:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

The default file looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
#%sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by ViRMiN on 2009-10-18
Your best option would probably be to boot from the live CD, mount your hard-disk partitions and then edit your troubled /etc/sudoers file using visudo.

Using visudo will warn you of errors before saving.  Don't save the file if there are errors - as you've seen it causing a bit of grief but, as long as you've physical access to the box it's not too big an issue.

---

### Post by rburkartjo on 2009-10-18
vir good idea will try that couldnt get what sisco said to work and he usually has good advise
tks

---

### Post by sisco311 on 2009-10-18
> **ViRMiN said:**
> Your best option would probably be to boot from the live CD, mount your hard-disk partitions and then edit your troubled /etc/sudoers file using visudo.

Using visudo will warn you of errors before saving.  Don't save the file if there are errors - as you've seen it causing a bit of grief but, as long as you've physical access to the box it's not too big an issue.

Editing the file with visudo from a live cd or another linux distro is a little tricky. You have to chroot to the Ubuntu installation.

assuming that the root partition is mounted under /media/ubuntu:
```
sudo chroot /media/ubuntu
VISUAL=gedit visudo
```
should do the trick.

for a fully functional chroot environment you have to mount some virtual filesystems:
```

sudo mount -t sysfs none /media/ubuntu/sys
sudo mount -t proc none /media/ubuntu/proc
sudo mount --bind /dev/ /media/ubuntu/dev
sudo mount --bind /dev/pts /media/ubuntu/dev/pts
sudo mount -o bind /etc/resolv.conf /media/ubuntu/etc/resolv.conf
sudo chroot /media/ubuntu
VISUAL=nano visudo
```
[/code]

---

### Post by rburkartjo on 2009-10-18
okay guys getting there not bad for a 60 year old fart here is where i am at if you could advise me how to proceed would appreciate it


ray@ray-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentation fault
ray@ray-desktop:~$

---

### Post by sisco311 on 2009-10-18
> **rburkartjo said:**
> okay guys getting there not bad for a 60 year old fart here is where i am at if you could advise me how to proceed would appreciate it


ray@ray-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentation fault
ray@ray-desktop:~$

You have to set the correct permissions on the sudoers file(Case 3 in the psychocats tutorial)

In the Recovery Mode run:
```
chmod 0440 /etc/sudoers
```

---

### Post by rburkartjo on 2009-10-18
sisco tks will try now

---

### Post by rburkartjo on 2009-10-18
no luck sisco any other ideas

---

### Post by rburkartjo on 2009-10-18
ray@ray-desktop:~$ sudo -i
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentation fault
ray@ray-desktop:~$ 
still same error cant fix in recovery mode

---

### Post by ViRMiN on 2009-10-18
> **sisco311 said:**
> Editing the file with visudo from a live cd or another linux distro is a little tricky. You have to chroot to the Ubuntu installation.

Could you not forget about chroot'ing the environment by specifying the file for editing like this (assuming that the usual '/' filesystem is mounted as '/mnt/usualroot'):

```
visudo -f /mnt/usualroot/etc/sudoers
```

---

