---
title: "separate Home folder partition  and an error!!!"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2010-06-02
I had litte space for the Lucid install and hence dedided to change the home partition to a separate partition
so i followed *[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)* exactly
i was successful but i got this error resulting in disappearance of the *volume  control and shut down/restart/logoff control on panel* (thats what i have come across so far)

**Error:could not update ICEauthority file /home/richlyn/.ICEauthority**

and heres the other one

[B]the panel encountered a problem while loading
OAFIID:Gnome fast user switch applet   do you want to delete applet from configuration[/B]

is there something that i can fix manually or have i to undo the separate home partition?????/

---

### Post by arrange on 2010-06-02
There is no *fast-user-switch-applet* in Lucid, so you can remove the reference. The package now is **indicator-applet-session**.

Also check the ownership of the file **/home/richlyn/.ICEauthority**, and if it's not you, change it, for instance in [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```
sudo chown richlyn:richlyn /home/richlyn/.ICEauthority
```

---

### Post by oldfred on 2010-06-02
this link explains all the permissions and ownship settings. It may solve the problem.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by richlyn9 on 2010-06-03
> **arrange said:**
> There is no *fast-user-switch-applet* in Lucid, so you can remove the reference. The package now is **indicator-applet-session**.


Okay but the volume control and shutdown,logoff,restart applet or control is missing also is the evolution  applet is missing how do i get it back

---

### Post by BoneKracker on 2010-06-03
May have butchered permissions on other files in /home as well.

Might be best to:

```
sudo chown -R richlyn: /home/richlyn
```

[ Edit:  That advice you followed on some guy's blog erroneously had you copy the files (as root) without preserving permissions and ownership.  See, when you run 'cp' you are creating new files (unlike when you run 'mv').  Therefore, unless you tell it different, when you run 'cp' as root ('sudo cp'), it creates these new files as root, which makes them owned by root (and they'll also be created with permissions according to root's umask, which may be different from yours).  For future reference, a good way to do that is 'sudo cp -a' (or 'sudo cp -rp'; refer to 'man cp'). ]

---

### Post by richlyn9 on 2010-06-03
tried this and will let you know what happens


richlyn@richlyn-lucid:~$ sudo chown richlyn /home/richlyn/.dmrc
richlyn@richlyn-lucid:~$ chmod 644 /home/richlyn/.dmrc
richlyn@richlyn-lucid:~$ chmod 755 /home/richlyn
chmod: changing permissions of `/home/richlyn': Operation not permitted
richlyn@richlyn-lucid:~$ sudo chmod 755 /home/richlyn
richlyn@richlyn-lucid:~$ sudo chown richlyn:richlyn /home/richlyn/.ICEauthority
richlyn@richlyn-lucid:~$ 

also reinstalled indicator-session applet and indicator-session

---

### Post by richlyn9 on 2010-06-03
> **BoneKracker said:**
> May have butchered permissions on other files in /home as well.

Might be best to:

```
sudo chown -R richlyn: /home/richlyn
```

[ Edit:  That advice you followed on some guy's blog erroneously had you copy the files (as root) without preserving permissions and ownership.  See, when you run 'cp' you are creating new files (unlike when you run 'mv').  Therefore, unless you tell it different, when you run 'cp' as root ('sudo cp'), it creates these new files as root, which makes them owned by root (and they'll also be created with permissions according to root's umask, which may be different from yours).  For future reference, a good way to do that is 'sudo cp -a' (or 'sudo cp -rp'; refer to 'man cp'). ]

That didn't permit me to do changes BoneKarcker
and i will be doubly sure before following anyones blog tutorials(bu i learn by making some mistakes)

richlyn@richlyn-lucid:~$ sudo chown -R richlyn: /home/richlyn
chown: cannot access `/home/richlyn/.gvfs': Permission denied
richlyn@richlyn-lucid:~$

---

### Post by BoneKracker on 2010-06-03
> **richlyn9 said:**
> That didn't permit me to do changes BoneKarcker
and i will be doubly sure before following anyones blog tutorials(bu i learn by making some mistakes)

richlyn@richlyn-lucid:~$ sudo chown -R richlyn: /home/richlyn
chown: cannot access `/home/richlyn/.gvfs': Permission denied
richlyn@richlyn-lucid:~$

Hmmm...  I don't use Gnome, but I would guess that's a directory full of stuff pertaining to the Gome Virtual Filesystem.  I don't know why you can't change ownership on it, probably because somebody thinks they were being clever, didn't want users to delete it, and took all write permissions off it or made it immutable.

Could you paste the output of:
```
ls -al ~
```
(So we can see what's set on the rest of it while we're at it.)

What you were doing will also work (going through and changing ownership on each file or directory one by one), but it shouldn't be that hard.

---

### Post by richlyn9 on 2010-06-03
> **richlyn9 said:**
> tried this and will let you know what happens


richlyn@richlyn-lucid:~$ sudo chown richlyn /home/richlyn/.dmrc
richlyn@richlyn-lucid:~$ chmod 644 /home/richlyn/.dmrc
richlyn@richlyn-lucid:~$ chmod 755 /home/richlyn
chmod: changing permissions of `/home/richlyn': Operation not permitted
richlyn@richlyn-lucid:~$ sudo chmod 755 /home/richlyn
richlyn@richlyn-lucid:~$ sudo chown richlyn:richlyn /home/richlyn/.ICEauthority
richlyn@richlyn-lucid:~$ 

also reinstalled indicator-session applet and indicator-session

[B][I]That worked!!
the error now does not come and the applets are now visible!![/I][/B]

thinking back i wonder what went wrong in the procedure to change the home partition to a separate one.BoneKracker's sugession is a good point to start.
will try to fix it.

---

### Post by richlyn9 on 2010-06-03
> **BoneKracker said:**
> Hmmm...  I don't use Gnome, but I would guess that's a directory full of stuff pertaining to the Gome Virtual Filesystem.  I don't know why you can't change ownership on it, probably because somebody thinks they were being clever, didn't want users to delete it, and took all write permissions off it or made it immutable.

Could you paste the output of:
```
ls -al ~
```
(So we can see what's set on the rest of it while we're at it.)

What you were doing will also work (going through and changing ownership on each file or directory one by one), but it shouldn't be that hard.

richlyn@richlyn-lucid:~$ ls -al ~
total 220
drwxr-xr-x 34 richlyn richlyn  4096 2010-06-03 11:15 .
drwxr-xr-x  5 root    root     4096 2010-06-02 23:16 ..
-rw-------  1 richlyn richlyn   841 2010-06-03 11:14 .bash_history
drwx------  9 richlyn richlyn  4096 2010-06-03 11:17 .cache
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .checkgmail
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .compiz
drwxr-xr-x 13 richlyn richlyn  4096 2010-06-03 11:17 .config
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .dbus
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-03 11:15 Desktop
-rw-r--r--  1 richlyn richlyn    36 2010-06-03 11:14 .dmrc
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-03 11:15 Documents
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-03 11:15 Downloads
-rw-------  1 richlyn richlyn    16 2010-06-02 23:16 .esd_auth
drwxr-xr-x  8 richlyn richlyn  4096 2010-06-02 23:16 .evolution
drwxr-xr-x  5 richlyn richlyn  4096 2010-06-03 11:14 .gconf
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-03 11:28 .gconfd
-rw-r-----  1 richlyn richlyn     0 2010-06-03 10:54 .gksu.lock
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .gnash
drwxr-xr-x 10 richlyn richlyn  4096 2010-06-03 11:19 .gnome2
drwx------  2 richlyn richlyn  4096 2010-06-02 23:16 .gnome2_private
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .gstreamer-0.10
-rw-r--r--  1 richlyn richlyn   147 2010-06-03 11:14 .gtk-bookmarks
dr-x------  2 richlyn richlyn     0 2010-06-03 11:14 .gvfs
-rw-------  1 richlyn richlyn  6228 2010-06-03 11:14 .ICEauthority
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .icons
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .local
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .mission-control
drwxr-xr-x  4 richlyn richlyn  4096 2010-06-02 23:16 .mozilla
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 Music
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .nautilus
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-03 11:15 Pictures
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 Public
drwx------  2 richlyn richlyn  4096 2010-06-03 11:07 .pulse
-rw-------  1 richlyn richlyn   256 2010-06-02 23:16 .pulse-cookie
-rw-------  1 richlyn richlyn 23864 2010-06-03 11:15 .recently-used.xbel
-rw-r--r--  1 richlyn richlyn     0 2010-06-02 23:16 .sudo_as_admin_successful
drwxr-xr-x  4 richlyn richlyn  4096 2010-06-02 23:16 .sudoku
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 Templates
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .themes
drwxr-xr-x  5 richlyn richlyn  4096 2010-06-02 23:16 .thumbnails
drwx------  2 richlyn richlyn  4096 2010-06-02 23:16 .update-notifier
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 Videos
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .xinput.d
-rw-------  1 richlyn richlyn  4331 2010-06-03 11:34 .xsession-errors
-rw-------  1 richlyn richlyn 28290 2010-06-03 11:14 .xsession-errors.old
richlyn@richlyn-lucid:~$

---

### Post by BoneKracker on 2010-06-03
> **richlyn9 said:**
> (bu i learn by making some mistakes)

We all do, and sometimes that's the best way to learn.  And, you're also learning other stuff in the process of fixing it. :)

Sometimes you have to use questionable documentation because it's all you can find.  Don't feel bad about it.

I can't count the times I've hosed up my system so bad I had to reinstall it from scratch.  If you don't try things, you don't learn.

---

### Post by BoneKracker on 2010-06-03
> **richlyn9 said:**
> richlyn@richlyn-lucid:~$ ls -al ~
total 220
drwxr-xr-x 34 richlyn richlyn  4096 2010-06-03 11:15 .
drwxr-xr-x  5 root    root     4096 2010-06-02 23:16 ..
-rw-------  1 richlyn richlyn   841 2010-06-03 11:14 .bash_history
drwx------  9 richlyn richlyn  4096 2010-06-03 11:17 .cache
drwxr-xr-x  3 richlyn richlyn  4096 2010-06-02 23:16 .checkgmail
.
.
.
drwxr-xr-x  2 richlyn richlyn  4096 2010-06-02 23:16 .xinput.d
-rw-------  1 richlyn richlyn  4331 2010-06-03 11:34 .xsession-errors
-rw-------  1 richlyn richlyn 28290 2010-06-03 11:14 .xsession-errors.old
richlyn@richlyn-lucid:~$

That's all looking okay to me at a quick glance.  **Maybe an Ubuntu user can compare it to their home directory and advise.**

I'd just go through and make sure there's nothing owned by root in there (and there probably shouldn't be anything that has root for a GID either.

Either I was wrong about what happened, or the chown command ran and modified the ownership on everything but .gvfs (which didn't get changed during copy because of permissions).  Or you have fixed it piece-by-piece.

Anything still not working right?

---

### Post by richlyn9 on 2010-06-03
No bad feelings at all...
may i know what did you look in that result that told you what belongs to whom...just curious 

I learn thing and put it on my blog as well (coz theres so many results when u google things i decided to put all my learnings on my [blog]("http://rxezlqu.wordpress.com") for reference..who knows someone can learn without busting his install)

BTY yes all dosent seems right
i logged out and logged in thet other user on the same install and it still age the original error and the applets also are missing.

guess i need to run those commands for the other user as well.But its wierd how the applets dont show up here.

---

### Post by BoneKracker on 2010-06-03
> **richlyn9 said:**
> No bad feelings at all...
may i know what did you look in that result that told you what belongs to whom...just curious 
Couple samples here:
```
drwxr-xr-x 2 richlyn richlyn 4096 2010-06-02 23:16 Music
dr-x------ 2 richlyn richlyn 0 2010-06-03 11:14 .gvfs

```
The first character is what it is (directory, file, etc.).
The rest of that string is permissions (user, group, other).
Next is number of links (for directory that lists number of files inside the directory)
Then you have owner, group, size, modification date and time, and filename.

So I was looking at "richlyn richlyn" right up and down the list, and I said to myself, "all the UID and GID are correct, at least at this level".

> **richlyn9 said:**
> BTY yes all dosent seems right
i logged out and logged in thet other user on the same install and it still age the original error and the applets also are missing.

guess i need to run those commands for the other user as well.But its wierd how the applets dont show up here.

By the way, the reason file ownership caused this is because your individual user preferences (and other user-specific configuration information) for gnome are stored in your home directory.  When you start Gnome, it's spawned off of a login shell that started in your name.  So Gnome is running with your privileges.  So if you can't access those files, Gnome can't either and it forgets what things you have configured.

I'm not following all the errors in detail, but I think your missing applets problem is unrelated to this ownership issue (and is upgrade-related or something).

I'm still not sure why you couldn't change ownership on ~/.gvfs (although you apparently already owned it).  Out of curiosity, could you show me:
```
lsattr -d ~/.gvfs
lsattr ~/.gvfs
```

---

### Post by richlyn9 on 2010-06-03
that gave an error:
richlyn@richlyn-lucid:~$ lsattr -d ~/.gvfs
lsattr: Inappropriate ioctl for device While reading flags on /home/richlyn/.gvfs
richlyn@richlyn-lucid:~$ 

but no issues i was impatient so i just backed up the other users files from home folder and deleted the user also removed the home folder and recreated the user again and everything is fine now.

---

### Post by richlyn9 on 2010-06-03
Thanks BoneKracker you been immense help!!

---

### Post by BoneKracker on 2010-06-03
> **richlyn9 said:**
> Thanks BoneKracker you been immense help!!

You're welcome.

By the way, based on that ioctl error, I think what happened when we originally did 'sudo chown -R /home/richlyn' and it gave an error was that it was unable to change permissions on .gvfs because it is actually a mount point containing a filesystem that only exists in RAM (like /proc or /sys).  A mystery to learn more about some day.

Good luck.

---

