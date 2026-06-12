---
title: "[SOLVED] your session ended in less than 10 secs error"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by minal on 2007-09-10
Hi all,

          When i tried to boot my pc it's giving following error.

    "Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

I dont think disk space is a problem. I have enough disk space.

The error log in the .xsession-errors file says

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "minal"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp : Private socket dir: permission denied.

---

### Post by jolan_jj on 2007-09-10
I think I can remember me having the same problem some time ago. It something with the permisssions to ICEauthority file. Try logging in the failsafe terminal og typing ```
sudo chmod 777 /home/yourusername/.ICEauthority
``` It helped in my case. You can change the permissions so only you can acces the file afterwards.

Cheers :)

---

### Post by jolan_jj on 2007-09-10
*Edit:* Or maybe ```
sudo chown yourusername /home/yourusername/.ICEauthority
```. One of those (or maybe both) does the trick.

---

### Post by minal on 2007-09-10
hi...

thanx for reply..
im now at workplace.. but definetly will try this whn wil go home..

---

### Post by minal on 2007-09-11
hi,

i got the answer... actually i messed up wid /tmp folder ..

but now its working fine..

thanx for the help..

---

### Post by vanadium on 2007-09-11
This thread is marked solved, yet people who hope to find a solution here, won't have a clue except for the advice of jolan_jj. Can you tell more specifically how you solved the problem (how did you "mess up" with /tmp, how did you resolve that?)

---

### Post by minal on 2007-09-12
hi vanadium

actually i creted one partition which i needed for scratchbox. but while partitioning i mounted it on /tmp.
So it was unable to get /tmp folder. 
I just did

umount /tmp

and then mounted that partition on another folder named scratchbox..

and dis solved my prob.

---

### Post by marstein on 2008-02-04
I did get the same error message. In my case the error was mkdtemp: private socket dir Permission denied.

First I had to log in somehow and using a failsafe terminal session worked. I used x-window-manager so that I could at least resize windows.

The problem was that no files in /tmp could be created. I opened a terminal and did:

$ cd /tmp
$ touch xxx

This should have created an empty file /tmp/xxx, but instead a permission denied error came up.

$ ls -ld /tmp
$ id

told me that the directory had a group write permission for users (=the name of a group) and that my user was not in the users group any more. I added my user to the group using 

sudo usermod -a -G users Martin

and after logging out I could log in normally again.


Hope this helps someone...

M

---

