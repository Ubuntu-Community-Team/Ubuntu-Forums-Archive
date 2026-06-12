---
title: "login screen appears again immediately after logging in on 14.04"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by nightfall2 on 2014-09-02
I upgraded to Ubuntu 14.04.1 LTS (from 12.04 LTS) some weeks ago on my Dell XPS17 laptop. Since yesterday, after an update which I think involved a new kernel, I can no longer login to unity. I get to the login prompt with the list of users and "Guest session" on the left side, but typing my password leads to the NVIDIA logo showing again and then moments later the login screen appears again. This happens every time I try to login. Oddly enough, when I choose 'Guest session' at the login screen I can then make use of my laptop, but obviously cannot get at my real user's data. I've tried going back to the previous kernel, but that doesn't solve anything. I can login at the console just fine (ctrl-alt-f1). I don't remember touching anything else that could have possibly caused something like this, haven't touched any config files on this laptop for a while now.

Any ideas on where to begin to find out where the problem is?

---

### Post by Bashing-om on 2014-09-02
nightfall2; Hi Welcome to the forum .

> **nightfall2 said:**
> 

Any ideas on where to begin to find out where the problem is?

I would start by making sure "you" have authority to access the GUI:
From the console (F1), logged into the system; what returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/<your_user_name>

```
Depending on those returns is what to do
[INDENT][INDENT][INDENT]oh what to do
[/INDENT][/INDENT][/INDENT]

---

### Post by nightfall2 on 2014-09-03
That was a great place to start looking! Turns out .Xauthority was owned by root:root. Wonder how that ever happened, but I changed it back and I can login again. Thanks for the quick feedback and excellent tip!

---

### Post by Bashing-om on 2014-09-03
nightfall2; Great !

An easy fix.

That situation is often a result of "sudo'n" where you should not have been sudo'n, As in an exercise of admin authority within your home directory where "you" have autonomous control, and elevated privileges are not needed and will result in undesired side effects.

As this matter is now concluded:
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and
 precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by cperry2 on 2015-04-20
Apologies if I am not violating protocol regarding thread, but this thread is the closest to my problem.

Am a complete newbie to Linux/Ubuntu, using 14.04 on a Asus 64 bit machine.  Everything working fine until I ran clamtk using admin privileges to update it, and now having similar problems as the original poster in this thread, i.e., login credentials accepted but login page is re-displayed.

Navigated to the root shell prompt in the recovery menu and found no files for commands:

ls -al .Xauthority
ls -al .ICEauthority


Command ls -al /home returns:

drwxr-xr-x  4 root root 4096 
drwxr-xr-x  25 root root 4096
dr-x-----  3 [username] [username] 4096
drwxr-xr-x  3 root root 4096

Command ls -al /home/[username] returns:

dr-x-----  3 [username] [username] 4096
drwxr-xr-x  4 **root root** 4096
lrwxrrwxrwx  1 [username] [username] 56
drwx-----  7 [username] [username] 4096
lrwxrrwxrwx  1 [username] [username] 29 
-rw-r--r--   1 [username] [username] 15591
lrwxrrwxrwx  1 [username] [username] 28 
lrwxrrwxrwx  1 [username] [username] 52

The second entry appears to indicate root ownership, but as I am a complete novice, I cannot be not sure.  

Any advice as to how to correct the problem would be greatly appreciated!

---

### Post by Bashing-om on 2015-04-20
cperry2; Hi !

'root' ownership of the ' .. ' directory is proper, as root has to have the access to the parent directory.
```

sysop@1404mini:~$ ls -al /home/sysop
total 4592
drwxr-xr-x 29 sysop sysop    4096 Apr 20 11:45 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 Sep 13  2014 #1334<snip>

```

As to not having the .Xauthotity and .ICEauthority files ... not too sure that from the root shell one would.
I will reboot later and check... 
A better approach is to boot to terminal from the login-screen :
At the login screen key combo ctl+alt+F1 will yield a console interface.
Can you log into the system from this console with username and password ? - there is no response when password is entered ; enter your password blindly and hit the enter key.
From this interface, what now results :
```

ls -al .Xauthoroty
ls -al .ICEauthority

```

A bit more info, see then what is to be done.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

