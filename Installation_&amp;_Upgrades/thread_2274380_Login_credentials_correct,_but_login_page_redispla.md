---
title: "Login credentials correct, but login page redisplayed"
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by cperry2 on 2015-04-20
Post[ login screen appears again immediately after logging in on 14.04]("http://ubuntuforums.org/showthread.php?t=2242561") is most similar to my problem, but thought I should post a new thread in case my request for help in that thread is not picked up.

I am a complete newbie to Linux/Ubuntu, using LTS 14.04 on a Asus 64-bit  machine.  Everything working fine until I ran clamtk using admin  privileges to update it, and now having similar problems as the original  poster in the above thread, i.e., login credentials accepted but the login page  is re-displayed and cannot access my user account (although the guest account is accessible).

Followed the advice in the earlier post, navigated to the root shell prompt in the recovery menu, and found no files for the suggested commands:

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

### Post by cperry2 on 2015-04-20
further information on this issue, ran command

find $HOME -not -user $USER -exec ls -lad {} \; to find which files in the home directory I did not own, and this command returned

-rw------ 1 10490 floppy 57218 [date]  root/.clamtk/viruses/Dynamic.pdf

---

### Post by Impavidus on 2015-04-20
> **cperry2 said:**
> 

Command ls -al /home returns:

drwxr-xr-x  4 root root 4096 
drwxr-xr-x  25 root root 4096
**dr-x-----  3 [username] [username] 4096**
drwxr-xr-x  3 root root 4096


It seems that you don't have write permission in your own home directory. Maybe you can still login on the console (ctrl+alt+F2, return to the GUI with ctrl+alt+F7), I'm not sure about that. Else boot into recovery mode, drop to a root shell and remount the file system read-write. There are tutorials on that. Then use```
chmod 700 /home/[username]
```Substitute your own user name.

---

### Post by cperry2 on 2015-04-20
Ok many thanks.  I will try and let you know.

---

