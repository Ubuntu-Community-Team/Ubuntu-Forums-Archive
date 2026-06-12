---
title: "how to unlock a a lock after a failed install (SOLVED)"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by kevinorourke2008 on 2013-04-10
Hi guys, I tried to install dropbox and it failed leaving me with a problem.
I am using ubuntu 12.04 lts on my acer aspire 1
I have tried to correct the problem by opening up synaptic package manager but it just keeps on telling me that another program is using it. I tried the pasted suggestion below but this is all that comes up.

sudo apt-get install -f
[sudo] password for kevin: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I looked in the /var/lib/dpkg and there is a file which is locked in there ! I am stumped as to where to go from here.

Any suggestions ??? :)

---

### Post by ibjsb4 on 2013-04-10
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by fantab on 2013-04-10
> **kevinorourke2008 said:**
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This error is usually reported when we try to run two apt-gets... like you may have the 'Software Updater" or Synaptic open and you try to use apt-get in the terminal. If you are doing so then don't and run only one apt-get application at one time.

If not, then use the command in the above post by ibjsb4, then run 'apt-get update', if it doesn't work then report back with the output of apt-get update.

---

### Post by kevinorourke2008 on 2013-04-10
Hi fantab,
I did as you suggested and I have posted the results below !

kevin@kevin-AOA150:~$ sudo rm /var/lib/dpkg/lock
[sudo] password for kevin: 
kevin@kevin-AOA150:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kevin@kevin-AOA150:~$

---

### Post by ibjsb4 on 2013-04-10
Reboot, then try an update and see if you get the same results.

---

### Post by kevinorourke2008 on 2013-04-10
ok will do

---

### Post by kevinorourke2008 on 2013-04-10
Hi ibjsb4, 
I shut down and restarted, and did the same again, here are the results.

kevin@kevin-AOA150:~$ sudo rm /var/lib/dpkg/lock
[sudo] password for kevin: 
kevin@kevin-AOA150:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kevin@kevin-AOA150:~$

---

### Post by ibjsb4 on 2013-04-10
That is:

**sudo** apt-get update

---

### Post by kevinorourke2008 on 2013-04-10
Hi ibjsb4,
Slightly different output this time ! I tried doing the "sudo dpkg --configure -a" and it says downloading, it goes to 100% and then stops doing anything ?

kevin@kevin-AOA150:~$  sudo rm /var/lib/dpkg/lock
[sudo] password for kevin: 
kevin@kevin-AOA150:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kevin@kevin-AOA150:~$ 

cheers Kev.

---

### Post by ibjsb4 on 2013-04-10
Open your "System Monitor" and go to processes.  Look for any package manager or packager updater that is open, like software center, update manager, synaptic.  If you find any, highlight it and use the "Kill" option.  Then update.

---

### Post by kevinorourke2008 on 2013-04-10
hi ibjsb4,
I tried what you suggested and there are both "aptd" and 2 x "dpkg" open when I try to kill them this is what happens.

Cannot kill process with pid 2665 with signal 9.
Operation not permitted.

---

### Post by Bashing-om on 2013-04-10
kevinorourke2008; Hi !

How about trying to get some more info on what is locking up "dpkg"
terminal codes:
```
sudo lsof /var/lib/dpkg/lock
sudo apt-get check
```[INDENT=3]just try'n to help

[/INDENT]

---

### Post by JPKnowMad on 2013-04-10
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/jpknowmad/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    2790 root    3uW  REG    8,1        0 2883723 /var/lib/dpkg/lock



I'm having the same problem and thats what I got

---

### Post by JPKnowMad on 2013-04-10
I was in the middle of an upgrade from 12.04 when my comp shutdown. I downloaded the 12.10 iso and tried to burn it to USB but i'm getting errors with that too. I went into terminal to do sudo apt-get update and upgrade but it keeps getting hung on the stupid nautilus dropbox thing. It reaches 100% and then nothing happens after that. Software center isn't acting right either. I think if I can just get past this dropbox issue and finish the upgrade, I can get my USB creator to work and start with a clean install

---

### Post by ibjsb4 on 2013-04-10
So originally this is a version upgrade from 12o4 to 12.10 that went bad?  Thats too bad.  I have tried in the past to help others with this type of problem and have not once succeeded.  Perhaps someone else will come along with a fix, but as far as I am concern you must backup you personal files and do a fresh install.

Sorry for the bad news :(

---

### Post by Bashing-om on 2013-04-10
@JPKnowMad;
Try this;
rerun the lsof command again to make sure that the PID is the same;
then run this code:
```
 ps aux | grep <that PID> ##confirmation of the process
kill -9 <that PID>
```

for example only:
```
ps aux | grep 3322
kill -9 3322
```
Now can you do the updates ?[INDENT=2]
hope this helps

[/INDENT]

---

### Post by kevinorourke2008 on 2013-04-11
SOLVED, I gave up and reinstalled the operating system. Everything works fine now.

---

### Post by Bashing-om on 2013-04-11
kevinorourke2008; Hey ,

That is one solution that always works !
[INDENT=2]
all's well that ends well

[/INDENT]

---

