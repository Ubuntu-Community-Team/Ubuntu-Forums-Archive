---
title: "dmrc and ICEauthority"
date: 2017-01-15
forum: MINT
---

### Post by exsencon on 2017-01-15
I am really sorry to get back at this issue again.
I had a dmrc issue (don't know how I got it) but I went to this forum, found the solution and applied it only to find out that on restart I had a .ICEauthority issue now which is much harder to fix. I finally got it fixed (Recovery,not recovery, chown,chmod etc) only to find out I was sitting with the dmrc issue again. Now, that's something I can still live with because at least I can get into my home partition while with the .ICEauthority issue I couldn't get anywhere. This is just a very annoying problem that in my opinion should be easy to fix,I just don't know how.
Can anybody tell me to get rid of the dmrc issue without screwing up the .ICEauthority thing? Thank you. (Sorry if this post is not in the right place)
Running LinuxMint 17.1 in dualboot with Windows7.

---

### Post by ajgreeny on 2017-01-15
*Thread moved to **MINT**.* which is more appropriate and a better fit.

Have you by chance ever used sudo to start a GUI application as root?
That can sometimes, depending on the application itself, change ownership and permissions of files such as dmrc and .ICEauthority, giving users the sort of problems you speak of, which [I] assume was the inability to login as user.

**Never use sudo to start a GUI application, no matter what it is.** Either install **gksudo** and use that, or use **sudo -H** instead of sudo, which will not cause the problems you have seen.

---

### Post by exsencon on 2017-01-15
No, I never used sudo in a GUI. I always use sudo in a terminal.
The problem is that as it happened I fixed the .dmrc issue with what I found on this forum,and it went allright. Only on restart I got the .ICEauthority issue and that took me some time to fix only to get the .dmrc issue again.

---

### Post by ajgreeny on 2017-01-15
Of course you only use sudo in a terminal; that is the only place you can type it, but have you ever used, for example **sudo nautilus** to start the GUI application nautilus or any other GUI application with root permissions?

Without knowing what you did to solve your .dmrc and then the .ICEauthority problem it is impossible to help you further; you seem to have managed to get yourself into a chicken/egg situation, so tell us in more detail what your original problem, and what the solution was to the .dmrc and .ICEauthority difficulty.

---

### Post by exsencon on 2017-01-16
I am pretty sure I never used sudo nautilus. However, I installed a electronic ID card with the synaptic package manager and it installed alright and then it asked me to continue in a terminal with yes/no. I said yes and did:
sudo apt-get update
sudo apt-get install (the card) and it went alright. But after rebooting I got the .dmrc issue which I solved with:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
So I thought I fixed it only to find out I had a .ICEauthority issue now.which I tried to solve with:
[https://ubuntuforums.org/showthread.php?t=1841457](https://ubuntuforums.org/showthread.php?t=1841457)
I tried several suggestions there and after much trying and error (in recovery modus with the root item) I finally got it right only to be stuck with the dmrc issue again. And you're right, it is a chicken/egg situation. How do I get rid of the chicken and the egg?
Any suggestions are welcome. As for now,I am just ignoring the dmrc and I can live with it,but of course it is not right.

---

### Post by steeldriver on 2017-01-16
Please post the outputs of 

```

ls -ld ~/{,.dmrc,.ICEauthority}

```

and

```

find ~ ! -user $USER -o ! -group $(id -g) -ls

```

---

### Post by exsencon on 2017-01-16
OK. ls -ld ~/{,.dmrc,.ICEauthority} :

drwxrwxrwx 24 zeger zeger  4096 Jan 16 17:08 /home/zeger/
-rwxrwxrwx  1 zeger zeger    28 Jan 11 16:29 /home/zeger/.dmrc
-rw-------  1 zeger zeger 33670 Jan 16 17:08 /home/zeger/.ICEauthority

and find ~ ! -user $USER -o ! -group $(id -g) -ls :

NOTHING

---

### Post by deadflowr on 2017-01-16
Your dmrc permissions are too high.
It must not be writable by others
change it with
```
chmod 644 /home/zeger/.dmrc
```

---

### Post by ajgreeny on 2017-01-16
As is your **/home/zeger** directory, which appears to have universally open permissions; definitely not a good idea.

Just to check everything else show us the output of ```
ls -la
``` which will show permissions of all files and folders in the root of your home folder and may help us tell you where to go from here..

---

### Post by exsencon on 2017-01-17
Alright,her we go:

zeger@zeger-Inspiron-1501 ~ $ ls -la
total 5356
drwxrwxrwx 24 zeger zeger    4096 Jan 17 12:12 .
drwxr-xr-x  4 root  root     4096 Apr 11  2014 ..
drwxrwxrwx  3 zeger zeger    4096 Aug  6 15:12 .adobe
-rwxrwxrwx  1 zeger zeger    7270 Jan 16 17:55 .bash_history
-rwxrwxrwx  1 zeger zeger     220 Aug  5 15:22 .bash_logout
-rw-r--r--  1 zeger zeger   22928 Jan 17 12:22 .BEID_0.log
-rwxrwxrwx  1 root  root    67650 Jun  5  2015 brscan3-0.2.13-1.amd64.deb
-rwxrwxrwx  1 root  root    50852 Sep  5  2013 brscan-skey-0.2.4-1.amd64.deb
drwxrwxrwx 11 zeger zeger    4096 Jan  5 17:55 .cache
drwxrwxrwx  5 zeger zeger    4096 Jan 17 12:12 .cinnamon
drwxrwxrwx 21 zeger zeger    4096 Jan 16 15:36 .config
drwxrwxrwx  3 zeger zeger    4096 Aug  5 15:36 .dbus
-rwxrwxrwx  1 root  root    11582 Aug  5 20:15 dcp195ccupswrapper-1.1.3-1a.i386.deb
-rwxrwxrwx  1 root  root    13594 May 24  2013 dcp195ccupswrapper-1.1.3-1.i386.deb
-rwxrwxrwx  1 root  root   754902 Aug  5 20:15 dcp195clpr-1.1.3-1a.i386.deb
-rwxrwxrwx  1 root  root  1895542 May 24  2013 dcp195clpr-1.1.3-1.i386.deb
drwxrwxrwx  3 zeger zeger    4096 Aug  6 16:04 Desktop
-rwxrwxrwx  1 zeger zeger      28 Jan 11 16:29 .dmrc
drwxrwxrwx  2 zeger zeger    4096 Sep  4 00:08 Documents
drwxrwxrwx  2 zeger zeger    4096 Jan 16 16:45 Downloads
-rw-r--r--  1 zeger zeger 2473984 Apr  2  2008 DP905drivers.exe
drwxrwxrwx  4 zeger zeger    4096 Jan 17 12:12 .gconf
-rwxrwxrwx  1 zeger zeger       0 Jan 16 16:46 .gksu.lock
drwxrwxrwx  5 zeger zeger    4096 Aug  5 22:58 .gnome2
drwxrwxrwx  2 zeger zeger    4096 Aug  5 22:58 .gnome2_private
drwxrwxrwx  2 zeger zeger    4096 Aug  5 17:22 .hplip
-rw-------  1 zeger zeger   34040 Jan 17 12:12 .ICEauthority
drwxrwxrwx  3 zeger zeger    4096 Aug  5 15:37 .linuxmint
drwxrwxrwx  3 zeger zeger    4096 Aug  5 15:36 .local
drwxrwxrwx  3 zeger zeger    4096 Aug 11 14:25 .macromedia
drwxrwxrwx  4 zeger zeger    4096 Aug  5 16:21 .mozilla
drwxrwxrwx  2 zeger zeger    4096 Aug 24 14:46 Music
drwxrwxrwx  2 zeger zeger    4096 Aug  5 15:36 Pictures
-rwxrwxrwx  1 zeger zeger     675 Aug  5 15:22 .profile
drwxrwxrwx  2 zeger zeger    4096 Aug  5 15:36 Public
drwxrwxrwx  2 zeger zeger    4096 Aug  5 15:36 Templates
drwxrwxrwx  4 zeger zeger    4096 Aug  5 22:58 .thunderbird
-rwxrwxrwx  1 root  root       46 Aug  5 20:16 uninstaller_brscan3
-rwxrwxrwx  1 root  root       50 Aug  5 20:16 uninstaller_brscan-skey
-rwxrwxrwx  1 root  root     1270 Aug  5 20:16 uninstaller_DCP195C
drwxrwxrwx  2 zeger zeger    4096 Aug  5 15:36 Videos
-rwxrwxrwx  1 zeger zeger     130 Jan 11 16:29 .Xauthority
-rw-r--r--  1 zeger zeger    3802 Jan 17 12:22 .xsession-errors
zeger@zeger-Inspiron-1501 ~ $

---

### Post by ajgreeny on 2017-01-17
You have a few files that are root owned, but that may not matter for those as they are mainly .deb packages, and also your printer driver uninstaller packages.

However, you have a lot of permissions that are at least inappropriate, or at worst, could stop you logging in as user.

The .Xauthority file should have permissions **-rw-------** (600) not **-rwxrwxrwx** (777) as you have now.
Also, most of your folders and files have full permissions for all, ie, user, group and others, equivalent to having used a **chmod 777** command. Have you ever used such a command on your /home?

I would suggest you use command ```
sudo chown -R zeger:zeger /home/zeger
``` to make you owner of all then run ```
chmod -R 755 /home/zeger
``` and finally, just to make sure all is OK run ```
chmod 644 .dmrc && chmod 600 .Xauthority && chmod 600 .ICEauthority && chmod 644 .profile
```

I am not sure that final command is necessary but it will make sure that the file permissions you have had problems with are correctly set.

---

### Post by exsencon on 2017-01-17
I followed your suggestions but did not reboot-yet...
As for your question, I think I used chmod 777 to get rid of the .ICEauthority problem but I am not sure anymore.
OK,rebooting now.

---

### Post by exsencon on 2017-01-17
Alright! Booting normally now.
Thank you ajgreeny and all others.
I think we can close this thread now?

---

### Post by ajgreeny on 2017-01-17
Brilliant!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved, and continues so, to your satisfaction. It is a great help to users searching the forum.

---

