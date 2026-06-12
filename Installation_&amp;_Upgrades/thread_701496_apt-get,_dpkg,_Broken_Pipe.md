---
title: "apt-get, dpkg, Broken Pipe"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by bhiksha on 2008-02-19
Hi All,

I was trying to install build-essential on my fresh Ubut6.06 installation and Im not sure exactly what happened, but synaptic died.

Thereafter I get:

>> apt-get
broken pipe
>> dpkg
broken pipe

Simply invoking these programs gives me a broken pipe. Synaptic, of course, doesnt even come up any more.

Any advice on how to fix this would be greatly appreciated.

Thanks
Bhiksha

---

### Post by dstew on 2008-02-19
Open a command line and enter the command```
sudo apt-get install build-essential
``` and post the exact error message to the forum.

---

### Post by bhiksha on 2008-02-20
> **dstew said:**
> Open a command line and enter the command```
sudo apt-get install build-essential
``` and post the exact error message to the forum.


Here it is:

bash>>sudo apt-get install build-essential
Password:
Broken pipe


Alternately, I do a sudo sh to get a root shell and:

#apt-get install build-essential
Broken pipe

#apt-get
Broken pipe

#dpkg
Broken pipe

Thanks
Bhiksha

---

### Post by bhiksha on 2008-02-21
Actually, it gets better:

>>sudo aptitude
Broken pipe

After this:
>>sudo sh
Broken pipe

>>sudo visudo
Broken pipe

>>sudo ls
Broken pipe

The machine is basically useless.

I can't upgrade or up anything since I cannot even sudo anymore!!

---

### Post by ColdCore on 2008-03-01
Check that you are still a member of the admin group. I got the same error on Ubuntu 7.10 after I had been removed from that group by mistake. I had used the usermod command line utility to add myself to a new group and, using the wrong options, had at the same time removed myself from all the other groups. Not surprisingly, also the sound stopped working for the same reason.

You should find your user name in the file /etc/group, on the line starting with 'admin'. The line could read, for example, ```
admin:x:110:yourname
```  There can be several user names that are separated with commas, but your name should be one of those. If the name is not there, one must reboot to fix the problem. After the grub boot manager had loaded, one can access the grub menu by pressing <esc> (as the on-screen instructions say). By selecting the recovery mode one becomes root and one can edit the group file, adding the user to the group. At least that fixed the problem for me. 

If this does not work, I would use passwd command (still in the recovery mode) to set a password for the root user. That way one can at least use command line package management tools as root, even if sudo does not work.

---

