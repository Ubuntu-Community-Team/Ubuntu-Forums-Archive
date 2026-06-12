---
title: "password unable to login14.04"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by i_karpas on 2014-12-06
I am stuck with an upgrade from 12.04 to 14.04
  I did an upgrade on my Ubuntu 12.04 system, on a partitioned disk: Win 7 and Ubuntu12.04.  The upgrade seemed to work OK, once it said it was low on storage space,  continued, the next window was filled with blank squares, and two buttons I pressed the one I guessed was continue/OK, The installation continued thru all the steps, up to reboot (about 2 hours) without any interruptions. At the end I did a reboot that brought up a login window asking for a password,  that I didn't need in 12.04.

 I think the upgrade worked because the Desktop background was the same as in 12.04 but on it a stamp 14.04, also the directory address on the top left was mine.
 I tried using my admin. Password in 12.04 and the reply was failed to start session
  tried to login as Guest was again asked for a password used the one before (the only one I have) and the reply was invalid password

  I repeated this several times with the same results, I then tried opening a terminal (^/Alt/F2) &#8594; tty2; but again was asked to login/password the reply   login incorrect

  I looked in the ubuntuforums site for help and found 2 documents
   1.   How to reset your password in Ubuntu
   2.  Lost password
  Following the instructions in #1 -  in GRUB chose Ubuntu14.04 &#8230;. with recovery mode ;
 Ubuntu ...o-59 generic-pae

       root shell
  following the instructions entered     ls /home      this returned  a blank line (I'm the only user), the system then asks for a passwd <username>

  the username in my case was a blank space

  then appeared          enter new UNIX password  xxxx  &#8592; the new password 10 characters

         retype passwd  

  also entered command    mount -rw -o remount
          .
          .
         exit
  (prompt is   root@......#)
  returns the recovery menu   --->     resume     OK

  

  now I resumed normal boot in GRUB which asked for the password, entered the
  NEW PASSWORD
  and got    invalid password
  tried login as Guest (purple screen) again with NEW password and got failed to startsession
  
WHAT ELSE CAN I DO?

---

### Post by deadflowr on 2014-12-06
Two things that seem odd.
First Guest Sessions need no password to login.
It is part of the nopasswdlogin group.

Second, /home did not list any username?
Even if you are the only user, you would still have a folder in the home directory for that user.

Perhaps try to make a new user.
Follow the same instructions to reset your password, but this time instead of changing the password, add a user with
```
adduser newusername
```
changing newusername to whatever you want the new user to be called.
It'll then ask to make a password for the new user, and also create the home folder for the newly made user.
I would also recommend adding that new user to the sudo group
```
adduser newusername sudo
```
This will give the user admin rights.
Then exit, and I would do a real reboot, instead of continue on to login, if that makes sense.

If that works, then we can try to figure out what happen to the old user, and that users data...

---

### Post by ajgreeny on 2014-12-06
As you ran out of space when upgrading to 14.04, I suspect that there was perhaps a major failure in the whole procedure, and with no idea where you have gone wrong, or the upgrade has gone wrong, I would strongly recommend that you stop using the installed OS, and try to figure out what is actually on the disk using a live system, booted from a USB or DVD.

From the live system run sudo fdisk -l and if possible open nautilus or other file-manager to check that all your files do actually still exist.

---

### Post by Impavidus on 2014-12-06
Even if you only have a single user, that user's home directory should still be present, giving you one line of return. You didn't get that, which means that you may have a separate /home partition, which was unmounted in recovery mode.

Usernames cannot be a single space (I think), and if you run **passwd <space>**, Ubuntu won't see the single space argument and will change the password of the current user, which is root.

It seems to me that your system is completely messed up. Fixing broken release upgrades is something most people won't try.

---

### Post by i_karpas on 2014-12-07
I tried ur solution (create newuser, added to sudo) then ls /home -->newxxxx,   for the NEW UNIX password I entered the same one I chose before (see my initial thread), was asked several questions (Name,Room,etc. used default (return))   exited     shutdown.
Started the computer again and choosed Ubuntu from Grub (NO recovery mode), got the Desktop (14.04 stamp) now
there r 3 options listed
1. original user; 2. newuser;  3.Guest
using newuser and new password --> [FONT=arial black]Failed to start session[/FONT]
I then [FONT=arial]tried all the other users all returned   [/FONT]--> [FONT=arial black]Failed to start session[/FONT] [FONT=arial]or incorrect password

By the way, ur right, for guest no password is needed (click on arrow), but still it fails to login


[/FONT]

---

### Post by i_karpas on 2014-12-07
thnk u

---

### Post by Impavidus on 2014-12-07
> **i_karpas said:**
> I tried ur solution (create newuser, added to sudo) then ls /home -->newxxxx,   for the NEW UNIX password I entered the same one I chose before (see my initial thread), was asked several questions (Name,Room,etc. used default (return))   exited     shutdown.
Started the computer again and choosed Ubuntu from Grub (NO recovery mode), got the Desktop (14.04 stamp) now
there r 3 options listed
1. original user; 2. newuser;  3.Guest
using newuser and new password --> [FONT=arial black]Failed to start session[/FONT]
I then [FONT=arial]tried all the other users all returned   [/FONT]--> [FONT=arial black]Failed to start session[/FONT] [FONT=arial]or incorrect password

By the way, ur right, for guest no password is needed (click on arrow), but still it fails to login


[/FONT]

If you have a separate home partition and created the new user from the recovery console without mounting the /home partition, then the new user's home directory will be on the root partition, which will be hidden when you boot into normal mode as the /home partition will be mounted on top of it, making it impossible to login using the new user. But with a failed upgrade, there could me many other problems.

Did you have a separate /home partition? In that case you may be able to simply reinstall and reuse your existing /home partition. By default there is no /home partition, so if you have one, you should know.

---

### Post by i_karpas on 2014-12-07
the phrase 
"*there could me many other problems.*" 
I guess applies to me
thank you anyway

---

