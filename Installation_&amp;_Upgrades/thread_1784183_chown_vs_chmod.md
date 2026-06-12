---
title: "chown vs chmod"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by fisheater on 2011-06-16
hi all,

i'm a bit out of my depth with this questions. i had to rebuild after a mobo failure, and a few other bumps that wouldnt allow me to copy my HD into my new tower. now i have installed 11.04 and am reinstalling and repermissioning all my files.

question: set ownership of my files (non-encrypted)

sudo chown -R fisheater /home/fisheater (1)
sudo chmod -R 700 /home/fisheater        (2)
sudo chmod -R 755 /home/fisheater/shared (3)

(1) Makes the user's folder owned by that user
(2) Prevents read, write and execute access for everyone but that user
(3) Adds read and execute access for everyone and write access for the user to the shared folder

-R means apply the command recursively.

(from: [http://superuser.com/questions/197232/making-home-folders-private-in-ubuntu-10-4](http://superuser.com/questions/197232/making-home-folders-private-in-ubuntu-10-4))

this is a bit different from what i did on my first setup, does this seem like correct terminal commands? (i.e. this wont lock me out?)

thanks for checking!

FE

---

### Post by sidzen on 2011-06-16
ex: 

chown -R fisheater:fisheater ./*  [while in the /home/ directory]

see [http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)

For chmod, see
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

BTW, sockeye is my favorite!

---

### Post by lisati on 2011-06-16
This is something that might baffle a user new to the *NIX way of managing file permissions. Here goes with a brief explanation:

**chown** is about which user on the system "owns" the files, and **chmod** is about who can do what with a file. :D

---

### Post by fisheater on 2011-06-16
Thanks, that makes some sense now. I admit any man or mildly technical explanation drops me into uncharted depths, your simple explanation helps me understand. 

But from that a few questions.

1.
What does fisheater:fisheater represent? i.e. why twice? I used this in trying to get my NAS permissions setup to allow me to rsync it (...which didnt work: [http://ubuntuforums.org/showthread.php?t=1772551](http://ubuntuforums.org/showthread.php?t=1772551)).

2.
This worked!
sudo chown -R fisheater:fisheater ./*

But this didn't:
sudo chmod -R 700 /home/fisheater

It generated this error
chmod: cannot access `/home/fisheater/.gvfs': Permission denied

I read it is the virtual filesystem for the GNOME desktop, but how do I chmod it to 700? 

Thanks!

Long live salmon!

---

### Post by nitstorm on 2011-06-16
> **fisheater said:**
> 

But from that a few questions.

1.
What does fisheater:fisheater represent? i.e. why twice?


You mention fisheater twice because it's ```
chown user:group
``` So it means give the user fisheater of the fisheater group ownership of the file.

> 2. This worked!
sudo chown -R fisheater:fisheater ./*

But this didn't:
sudo chmod -R 700 /home/fisheater


The first command gave you ownership of the file, i.e., it transferred the ownership to you. The second command (chmod) said "make the current file own be able to read, write and execute whereas the group and others are unable to read, write or execute.
> 
It generated this error
chmod: cannot access `/home/fisheater/.gvfs': Permission denied


Means you don't have permissions to perform the action required on that file.

---

### Post by fisheater on 2011-06-16
Great summary, thanks! This is making sense, even to a non-computer background type like me.

I guess the only remaining question is how do I escalate my permissions to be able to 

```
sudo chmod -R 700 /home/fisheater 
```

This is my computer, set up from a blank HD. That means that somehow I need to get to root. That said, I was under the impression that 

```
sudo
```

before any terminal commands would prompt for my password, then if successful, would allow ?superuser status.

Suggestions?

Thanks!

---

### Post by sidzen on 2011-06-17
You're entering dangerous territory for ubuntu users with your question about how to become root (do so only when not connected to the internet in any way).  In sequence at the command prompt --

[B]sudo passwd root 
cd /home/[/B]
**chmod -R 700 ./***    [this command will not display correctly wrapped in PHP]
**exit**

-----------------------------------------------------------------------------------------
Command            Meaning

**chmod 400** *file*        To protect a file against accidental overwriting.
**chmod 500** *directory*    To protect yourself from accidentally removing, renaming or
            moving files from this directory.
**chmod 600** *file*        A private file only changeable by the user who entered this
            command.
**chmod 644*** file*        A publicly readable file that can only be changed by the issuing
            user.
**chmod 660** *file*        Users belonging to your group can change this file, others don't
            have any access to it at all.
**chmod 700** *file*        Protects a file against any access from other users, while the
            issuing user still has full access.
**chmod 755** *directory*    For files that should be readable & executable by others, but
            only changeable by issuing user.
**chmod 775 ***file*        Standard file sharing mode for a group.
**chmod 777** *file*        Everybody can do everything to this file.
-----------------------------------------------------------------------------------------
I am not an elementary teacher -- my apologies -- however,
Best wishes!

---

### Post by fisheater on 2011-06-17
Great stuff, thanks for spelling it out. 

My question that comes out of this is what is different? I mean to say that my ubuntu 8.10 install was chown 700 with no error message, then that change persisted in all my upgrades 9.04 -> 9.10 -> 10.04. 

Has there been a change in the permissions in 11.04 or is this typical of a fresh install?

Thanks for keeping me on the right path (i.e. linux!)

FE

---

### Post by sidzen on 2011-06-18
I cannot answer your question because I do not use 11.04 and do not intend to do so.
I am sticking with LTS as of 10.04.02 because too-buggy new releases is the primary weakness 
I see with ubuntu.
I'm glad both of being some help and to see someone taking time to learn the Command Line,
for . . .

---

### Post by fisheater on 2011-06-30
Thanks, sorted it out. My question about why it worked in 9.04 but not in 11.04 remains, but the issue is resolved.

Found this beauty of an explanation:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for your help.

FE

---

### Post by fisheater on 2011-06-30
> **sidzen said:**
> I cannot answer your question because I do not use 11.04 and do not intend to do so.
I am sticking with LTS as of 10.04.02 because too-buggy new releases is the primary weakness 
I see with ubuntu.
I'm glad both of being some help and to see someone taking time to learn the Command Line,
for . . .

I do lament upgrading to 11.04, my 10.04 LTS was working well, but I was unable to get my new computer to boot from any iteration of the LiveCD. It got hung in the text part of the CD spin up. I went the path of least resistance and loaded the version that would load. WinXP wouldn't install either...

Thanks!

---

