---
title: "Ubuntu 11.04 - permission constantly denied even to root"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by asaaki on 2011-06-28
Hi,
I just installed Ubuntu 11.04 (using wubi on my 64-bit windows 7). Everything seemed to be working fine until I got down to the main reason I installed it in the first place - have to work on some linux-only softwares.

But I can't build anything, I've tried four different programs that needed building. I'm running the terminal as root but I still get "Permission denied" if I run ./configure or make.

I use sudo -i, I've tried chmod and chown but nothing makes a difference, I never have permission.

Here's an example:

```
root@ubuntu:/media/560496170495F9E7/srilm# make World
make: execvp: /media/560496170495F9E7/srilm/sbin/machine-type: Permission denied

```

I used chmod 755 on machine-type, no difference.

Please help!

---

### Post by sanderd17 on 2011-06-28
The NTFS filesystem used by windows doesn't support user rights for files. You should copy the files to an ext4 partition (e.g. in your home directory) first. Afterwards, make it executable and run the configure script.

---

### Post by asaaki on 2011-06-28
Thanks for the reply!
I moved the folders to home/nlp, but I still have the same problem when I try 

```
root@ubuntu:/home/nlp/srilm/sbin# sudo make World
```I get the same make error saying Permission denied to sbin/machine-type

There's a slight improvement though. After applying chmod 777 to machine-type, now, if i got into sbin and do ```
ls -l
```, I get this:

```
-rwxrwxrwx 1 asaaki asaaki 4028 2011-06-28 10:21 machine-type
```before, I wasn't able to see any changes (all permissions granted) to the file "machine-type".

But even with those permissions, I don't seem able to do anything. I tried ./configure to install another tool, same problem.

```
root@ubuntu:/home/nlp/yamcha-0.33# ./configure
bash: ./configure: Permission denied

```

Any ideas?

---

### Post by sanderd17 on 2011-06-28
can you show me the permissions of the configure file?

```

ls -al configure

```

---

### Post by asaaki on 2011-06-28
Thanks! But i went on the ubuntu channel on IRC chat and got this permissions issue sorted out. Didn't exactly know why, but even though I'd given permissions, the executables that needed permissions didn't get them even when I did chmod 777. Just starting over again and unpacking the tarballs in the right directory worked. Maybe I just had too many shifting-folders-around/changing users/permissions all over the place.

---

