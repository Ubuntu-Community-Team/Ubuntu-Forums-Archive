---
title: "Problem with update- Unable to lock Administration directory"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by majordread on 2011-10-12
Hello, I have seen multiple posters have this problem, but none of the solutions worked for me and I had an additional error on top of it. When I run terminal and type in 

sudo apt-get update

it runs as if it will update, but then I get this message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I have tried to edit the directory, and nothing has worked. I also am unable to use the update manager or the synaptic package handler. I have looked in my system monitor and as far as I can tell none of them are running in the background either.

Any help is much appreciated. :D

---

### Post by matt_symes on 2011-10-12
Hi

> **majordread said:**
> 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 

You have two errors here. 

1. You are missing a GPG key
2. The dpkg lock file is locked.

You should fix (2) before you fix (1).

Open a terminal and type
[FONT=monospace]
[/FONT]```
sudo lsof /var/lib/dpkg/lock
```Enter your password. It will not be echoed to the screen.
This will tell you what has got a lock on dpkg. 
Post the results back here. I am interested to see what has a lock on dpkg.

You can then either close that program, restart your PC or send a -TERM to the program with the lock by using kill and the pid.

After that you need to import the key.

EDIT: Added command.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
``` 
then type

```
sudo apt-get update
```
Kind regards

---

### Post by majordread on 2011-10-12
Thanks for the speedy reply.

After I typed in the command you prescribed, this is what I received:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tyler/.gvfs
      Output information may be incomplete.
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    15004 root    3uW  REG    8,1        0 7078501 /var/lib/dpkg/lock


I also apologize as I am fairly new to Ubuntu, so fixing this is a task in its own for me as of right now, but I hope to learn.

---

### Post by majordread on 2011-10-12
I apologize for the double post, but I killed the program and ran a configure on the dpkg so those errors are gone, now when I run sudo apt-get update I only get this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by matt_symes on 2011-10-12
Hi

> **majordread said:**
> 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tyler/.gvfs
      Output information may be incomplete.
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    15004 root    3uW  REG    8,1        0 7078501 /var/lib/dpkg/lock

dpkg itself has a lock on the lock file. It's possible it may have got stuck.

Out of interest do you have synaptic package manager, update manager or software center running ? 

If so then close that program, otherwise from the terminal type

```
sudo kill -TERM    15004
```to close dpkg gracefully.

See my edit on my last post on how to add the keys.

If you have any problems then post back.

Kind regards

---

### Post by matt_symes on 2011-10-12
Hi

We're kind of cross posting :)

Just in case you missed it.
> 
See my edit on my last post on how to add the keys.

If you have any problems then post back.Kind regards

---

### Post by majordread on 2011-10-12
Thanks a lot, both for your timely replies and your help. It worked, I was able to update, and my update programs are working normally again. Thank you very much.

---

### Post by bantolo on 2012-06-20
WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eko/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    2815 root    3rW  REG    8,5        0 1043009 /var/lib/dpkg/lock



please help

---

### Post by nothingspecial on 2012-06-20
Please create a new thread with as much detail as possible.

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

