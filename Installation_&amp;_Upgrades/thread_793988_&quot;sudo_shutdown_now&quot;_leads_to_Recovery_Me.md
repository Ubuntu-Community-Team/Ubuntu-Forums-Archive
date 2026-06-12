---
title: "&quot;sudo shutdown now&quot; leads to Recovery Menu"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by gotee12 on 2008-05-14
I'm experiencing a problem with shutting down my Ubuntu machines ever since yesterday's SSL and Gnome updates were applied ( yesterday as in 3-13-08 ). I tagged onto the end of [this post]("http://ubuntuforums.org/showthread.php?p=4952454#post4952454") and [this Launchpad bug]("https://bugs.launchpad.net/ubuntu/+bug/216006") but I thought it best to start a thread devoted to this issue. (If starting this thread was a bad idea, please be gentle in your admonition.)

In a nutshell, after yesterday's updates I am no longer able to successfully and cleanly shutdown these machines from the CLI. 

Issuing the command: 
```
sudo shutdown now
```
..while in the CLI exits the GDM session and takes me to the Recovery Menu.

Issuing the commands:
```
sudo reboot now
```
or
```
sudo shutdown -h now
```
..from the CLI work successfully. Though I have read that using the -h switch with shutdown calls for an immediate halt to all process and does not allow the processes to terminate gracefully, so I do not want to make a habit of using the -h switch.

Since I am seeing this issue on three seperate machines with disparate hardware, I'm assuming this affects more users than just myself. And since this issue did not occur until after yesterday's updates, I'm inclined to believe they may have been the cause. Though I would much more suspect Gnome updates causing this behaviour versus SSL.

Any ideas? Thanx in advance.

P.S. - I noticed this morning that there is another update for SSL, it has been applied but the issue still remains. Though like I said, I really believe it has to do with the update to Gnome from yesterday.

---

### Post by Joeb454 on 2008-05-14
I've never used shutdown without a switch. I always use ```
sudo shutdown -P now
``` Does that work for you?

---

### Post by gotee12 on 2008-05-14
Yep, that works. Should shutdown always be used with the -P switch? Is that a safer way to shutdown versus using "sudo shutdown now"? 

Also, seeing as how a command is not functioning in the same manner as it was before an update (and I didn't see anything in the updates stating that the usage of the command had been changed), should this be considered a bug?

I read in the other posts, that were somewhat related to this one, to just use switches. I didn't know whether this issue should be brought up or not honestly, but once I experienced it on my work PC as well, I thought it might be mention worthy.

Thanx for your quick response Joeb454!

---

### Post by blingo on 2008-10-10
Bump, is shutdown -P safe?

---

### Post by iaculallad on 2008-10-10
> **blingo said:**
> Bump, is shutdown -P safe?

Sure it's safe. -P switch tells the shutdown command to power the system off after it has been brought down.

```
man shutdown
```

---

### Post by venturax on 2010-02-25
Any news about whats causing this? I have just gotten it on 2 machines during the last couple of days. 
BTW, [SIZE=5]do not[/SIZE] select "repair broken packages". This thrashed my machine completely and grub couldn't connect to the disk at all. I had to reinstall it, causing me use a live cd to salvage some data :(

---

### Post by bgervasi on 2010-02-25
I have been getting this also on all my ubuntu servers.

I come from a sun house, so "shutdown -y -g0 -i6" is a habit.  Been doing this on ubuntu also.  After the last patch upgrade, shutdown with an -i6 goes into recovery.  shutdown -r now works fine and init 6 or reboot all do not do this but the -i6 option in shutdown.

---

### Post by lofttroy on 2010-03-29
Anyone have a reason for this?  I am getting tired of hitting the power button to shutdown the computer.  With 9.04 the computer shuts down fine, after the upgrade every time I shutdown it comes up with a stupid recovery menu.  And if I do anything the computer just takes me right back to the login prompt.  I can't imagine it good for computers to get a hard power down.  This computer is running only the 64-bit server version (no GUI).

---

### Post by venturax on 2010-03-30
@lofttroy: instead of using ```
shutdown now
``` which caused all the trouble, I now use ```
shutdown -h now
``` which works fine.

I have tried googling more information about the issue, but I have hit a dead end every time. All "solutions" to the problem is to remember an option parameter :-) It isn't a solution but it's a way to make the symptom go away..

Sorry I couldn't provide more information. Please post if you find the explanation

---

### Post by cmjrees on 2010-05-02
> **venturax said:**
> @lofttroy: instead of using ```
shutdown now
``` which caused all the trouble, I now use ```
shutdown -h now
``` which works fine.

I have tried googling more information about the issue, but I have hit a dead end every time. All "solutions" to the problem is to remember an option parameter :-) It isn't a solution but it's a way to make the symptom go away..

Sorry I couldn't provide more information. Please post if you find the explanation

It's historical. Single user mode (Ubuntu's recovery mode) is used by server administrators for backup and most major architectural work.

```
shutdown now
``` is the way to put computers into single user mode, synonymous with ```
telinit 1
``` on System V (including GNU/Linux) systems.

---

