---
title: "Retrieving data from my old home folder"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2010-01-05
Okay so here are the steps I took and the mess I put myself in:

I have a 500 GB HDD. On it, I had Ubuntu on a 400 GB partition and an empty 100 GB partition.
I checked out Computer Janitor to find out what it was all about. There, a list of about 8-9 things were all checked in the "Unused" column. Well, some of that stuff I did use, while most of it I could not understand.

Fearing I might damage the machine, I unchecked everything and exited the application. 

So, later on, when I rebooted, the only thing I could see once I was logged on, was the default Ubuntu wallpaper and no icon, no toolbars, no nothing. So I thought "F***!! I just erased all my data and all my applications". So I installed windoze 7 on the free 100 GB partition (I intended to do that eventually anyway) and I built an other bootable Ubuntu flash drive OS - which I'm using right now.

From here (the USB stick UBUNTU) I can browse the 400 GB Ubuntu partition but it won't allow me access to the home folder, which is where all my data and files were. The following message shows up:
> The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "pepelapiu".
So here are my two questions:

- Can I get my old Ubuntu OS back?
- If not, how can I access my old home/"username" folder to copy it and save it on my external HDD?

Thanx and HAPPY NEW YEAR!!!
PepeLapiu :)

---

### Post by garryknight on 2010-01-05
If the partition containing the directory is mounted, you can open a console and enter
```

chown -R yourname /whereveritsmounted/home/username

```Obviously you have to do some substitution here. "yourname" is your login name and "/whereveritsmounted" could be somewhere like "/mnt/oldpartition" depending on where it's mounted. You probably get the picture.

The chown command changes ownership of directories and files. The -R parameter tells it to recurse (dig down into) subdirectories. You can also use it as:
```

chown -R username.group /directory

```and it will change the group ownership of the directory and everything in it. And, of course, you don't need the -R parameter unless you specifically want to affect *everything* inside a directory.

---

### Post by PepeLapiu on 2010-01-05
Well, thanx a lot for the help so fast. However, I did as you said and here are the results:
> To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.



ubuntu@ubuntu:~$ chown -R pepelapiu /media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu

chown: invalid user: `pepelapiu'

ubuntu@ubuntu:~$ chown -R ubuntu /media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu

chown: cannot read directory `/media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu': Permission denied

ubuntu@ubuntu:~$ chown -R username.group/directory

chown: missing operand after `username.group/directory'

Try `chown --help' for more information.

ubuntu@ubuntu:~$ chown -R username.group/media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu

chown: missing operand after `username.group/media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu'

Try `chown --help' for more information.

ubuntu@ubuntu:~$ 
 

I could not tell from your post if the username is "ubuntu" (default in flash drive Ubuntu) ..... "pepelapiu" which is the one I was using on the istalled Ubuntu.
So I tried both.

---

### Post by michy99 on 2010-01-05
Use the 'sudo' command to give yourself root permissions.```
sudo chown -R ubuntu /media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu
```

---

### Post by PepeLapiu on 2010-01-05
> **michy99 said:**
> Use the 'sudo' command to give yourself root permissions.```
sudo chown -R ubuntu /media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu
```

Duh! Pardon my noobinism ..... BRB :D

---

### Post by PepeLapiu on 2010-01-05
Thanx again to you too michy99 for your generous help. 
Here's the result:
```
ubuntu@ubuntu:~$ sudo chown -R ubuntu /media/7a94cfc6-b121-4338-9c7a-55870e7e033e/home/pepelapiu
ubuntu@ubuntu:~$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
ubuntu@ubuntu:~$ sudo ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
ubuntu@ubuntu:~$ 
```

---

### Post by michy99 on 2010-01-06
You didn't mention that it was encrypted. I'm afraid your out of my league here.

---

### Post by garryknight on 2010-01-06
Yes, I'm out of my league too. Sorry I forgot to mention the 'sudo'... :redface:

---

### Post by PepeLapiu on 2010-01-06
Okay, on the USB OS, if I create a user account with the same name and same password as the one I was using, would it recognize it as the same useror would it decline it?

I'm going to give it a try right now and see if it works.

---

### Post by garryknight on 2010-01-07
Now that I *do* know. The user and group name are not what is important. You need to create a user and/or group that has the same id numbers. In a console, run "id" to see what your current uid (user id) and gid (group id) are.

Precisely how you create a user with a specific uid and gid depends on whether you do it from the command line or using a GUI. On the command line the format is "useradd -u uid -g gid", so you'd do something like:

```

useradd -u 1000 -g 1000 pepelapiu

```

---

