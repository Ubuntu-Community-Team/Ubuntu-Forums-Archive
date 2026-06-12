---
title: "changing password in recovery mode not working"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Tom1942 on 2006-08-27
I didn't use my pc, which has only xubuntu installed, for two days.  I am the only user and the only person to work with it.  I did not change, add or delete anything from the last time I used the pc.  My username and password worked the last time I used the pc.

When I typed in my username and password today all that happened was a loop back to the box wanting me to log in again.  I made sure I typed both username and password correctly, twice.

I searched the forums and found that I could boot in recovery mode and then type in passwd [username] at the command line prompt.  I did that.  

The pc booted to this command line prompt-
boot@[pc name]:~#
I typed in passwd [username]

This prompt appeared-
Enter new UNIX password:

I entered a new password.  
This prompt appeared-
Retype new UNIX password:

I retyped the new password.
This prompt appeared:
passwd: password updated successfully
root@[pc name]:~#

I typed exit.
The pc began rebooting.

Xubuntu booted up and presented a input box for username.
I typed my username (very carefully).
I was asked for my password.  I typed the new password (very carefully).  

It looped back to asking for the username again.  It seems I am locked out, unless I re-install Xubuntu (maybe).

Before I ask for tips on what to do next, I'd like to say that I have found all the replies to my postings to be friendly and helpful.  I want to set up a useful, functional xubuntu pc.  But, I'm becoming quite depressed.  I consider myself a power windows user.  I have, in the past, learned to use a unix OS on a Sparc20 workstation.  That was almost 10 years ago and I know I'm a novice linux user.  I know I have a lot to learn.  But, the type of problem described above, unknown failure to retain or accept a username and password is very discouraging.  Up until this, I believed my problems were due to being a novice and lacking experience.  I don't know what to make of this password problem.

What I am I missing?  My experience tells me it's probably me, but I've never had problems like this.

Kindly point me in the right direction. :confused:  :confused:  :confused:

---

### Post by Tom1942 on 2006-08-28
I hope someone will eventually be able to provide some insight on this problem.

In the meantime, my install of Xubuntu was so flaky I decided to re-install from the Live CD.

I now seem to have a stable install and I am now working on tweaking it.  

I know I'll be back to this forum with more questions as I work through the tweaking process.

---

### Post by symka on 2008-07-10
Sorry if this topic is out-of-date, but I've just had the same problem as Tom1942... My initial password for ubuntu contained special symbols, and immediately after I installed Ubuntu I could login and update the system (I have used the password several times and everything was working!). On the second startup I continued receiving the error "incorrect login or password". So I have done the same procedure as Tom without success. After several trials I changed the password so that it did not contain any special symbol, and finally I was able to login! Hope it can help someone.

---

