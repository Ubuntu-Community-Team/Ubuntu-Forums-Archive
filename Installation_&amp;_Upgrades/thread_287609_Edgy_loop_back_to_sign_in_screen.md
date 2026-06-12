---
title: "Edgy loop back to sign in screen"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by gu014 on 2006-10-29
Hello,
I just upgraded to edgy and after attempting to log in with my default session(GNOME) i continuously get looped back to the sign in screen.  With any other session such as KDE i am able to login without issue.  Just when i try and log in with GNOME i enter my user name and password and the screen goes black...hangs for a few seconds and then goes directly back to the sign-in screen. any help would be appreciated.  thank you very much.

---

### Post by taurus on 2006-10-29
Maybe you should start a KDE session and look in ~/.dmrc to make sure it has the right permissions and ownership.  You should be the owner of that file and you should have read and write permissions to it!!!

---

### Post by gu014 on 2006-10-29
ok, i tried that and there seems to be some improvment. it loads the desktop initially but only for a few seconds. it then goes back to the black screen..hangs for a few seconds and then loops back to the sign in screen??

---

### Post by taurus on 2006-10-29
How did you change the ownership and permissions of your ~/.dmrc?  You probably need to boot into recovery mode (from GRUB menu) and at the prompt, do

```
cd /home/john (assuming john is your login name...)
chown john:john .dmrc
chmod 644 .dmrc

```
Reboot and see if you now can log in with user john!

---

### Post by gu014 on 2006-10-29
from kde i just did a chmod 755 .dmrc

---

### Post by gu014 on 2006-10-29
thank you very much. that has worked although one problem remains.  my lower panel contained only launchers and now all the icons show the gnome icon and the launchers are all empty(commands+comment+name) all gone

[IMG]http://gaight.com/Screenshot.png[/IMG]

Any idea how i can recover this?
I dont know if it is relevent or no but in ~/ there are .gnome and .gnome2  ?

---

### Post by taurus on 2006-10-29
Could it be permissions problem with your user account?  What is the output of this command from a terminal (and if you don't want people to see files or directories you have in your personal account, don't include them here)...

```
ls -la ~
```

---

### Post by gu014 on 2006-10-29
```
-rw-------  1 sean sean    11425 2006-10-29 00:59 .bash_history
-rw-r--r--  1 sean sean      414 2006-07-27 09:08 .bash_profile
-rw-r--r--  1 sean sean     2227 2006-07-27 09:08 .bashrc
drwx------  5 sean sean     4096 2006-08-21 00:22 .cache
drwx------  7 sean sean     4096 2006-08-06 00:39 .config
-rw-r--r--  1 sean sean       24 2006-08-03 22:23 .dmrc
-rw-------  1 sean sean       16 2006-07-27 17:19 .esd_auth
drwx------  6 sean sean     4096 2006-10-29 01:03 .gconf
drwx------  2 sean sean     4096 2006-10-29 01:08 .gconfd
drwxr-xr-x  5 sean sean     4096 2006-08-26 19:04 .gkrellm2
-rw-r-----  1 sean sean        0 2006-10-29 01:03 .gksu.lock
drwxr-xr-x  2 sean sean     4096 2006-08-31 21:30 .gnochm
drwxr-xr-x  7 sean sean     4096 2006-09-08 17:56 .gnome
drwxr-xr-x  7 sean sean     4096 2006-10-29 00:59 .gnome2
drwx------ 15 sean sean     4096 2006-10-29 00:10 .gnome2.bak
drwx------  2 sean sean     4096 2006-08-09 18:55 .gnome2_private
drwx------  2 sean sean     4096 2006-09-08 17:49 .gnome_private
drwx------  2 sean sean     4096 2006-08-09 19:56 .gnupg
drwxr-xr-x  5 sean sean     4096 2006-09-20 22:47 .gqview
drwxr-xr-x  2 sean sean     4096 2006-10-29 00:08 .gstreamer-0.10
drwxr-xr-x  2 sean sean     4096 2006-07-27 17:19 .gstreamer-0.8
-rw-------  1 sean sean        0 2006-08-28 22:41 .gtk-bookmarks
-rw-r--r--  1 sean sean       86 2006-10-23 16:51 .gtkrc-1.2-gnome2
-rw-r--r--  1 sean sean    26726 2006-10-07 09:32 hs_err_pid7887.log
-rw-r--r--  1 sean sean    26488 2006-10-07 09:36 hs_err_pid8184.log
-rw-r--r--  1 sean sean    25221 2006-10-07 09:43 hs_err_pid8714.log
-rw-r--r--  1 sean sean    23134 2006-10-07 09:43 hs_err_pid9996.log
-rw-r--r--  1 sean sean        0 2006-08-22 18:52 hsqlprefs.dat
-rw-------  1 sean sean     9533 2006-10-29 01:02 .ICEauthority
drwxr-xr-x 10 sean sean     4096 2006-10-21 11:29 .icons
-rw-r--r--  1 sean sean       41 2006-08-01 22:01 .install4j
drwxr-xr-x  4 sean sean     4096 2006-10-01 11:43 .java
-rw-r--r--  1 sean sean    33686 2006-08-05 16:29 jriddell.key
drwx------  4 sean sean     4096 2006-08-01 18:35 .kde
-rw-------  1 sean sean      160 2006-08-01 18:35 .kderc
-rw-------  1 sean sean       35 2006-10-11 00:48 .lesshst
drwx------  3 sean sean     4096 2006-08-01 18:35 .local
drwx------  3 sean sean     4096 2006-08-09 20:07 .loki
drwxr-xr-x  3 sean sean     4096 2006-07-30 21:37 .mcop
-rw-------  1 sean sean       31 2006-10-24 20:36 .mcoprc
drwxr-xr-x  3 sean sean     4096 2006-08-30 16:48 .menu
-rw-r--r--  1 sean sean        0 2006-07-27 10:42 .sudo_as_admin_successful
-rw-r--r--  1 sean sean     3571 2006-09-08 17:56 translog.20060908175631.log
drwx------  2 sean sean    12288 2006-09-04 19:36 .Trash
```

---

