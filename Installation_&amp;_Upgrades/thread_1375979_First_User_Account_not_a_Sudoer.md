---
title: "First User Account not a Sudoer"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by nicktids on 2010-01-08
Hi i've just installed Karmic 9.10 via the mini.iso, options ubuntu generic and then installing the ubuntu server and ubuntu as packages.

In the setup I give the root user an account then set up a user account and its not a Sudoer so when i first log in I can't do anything.

Tried reinstalling and on my 5th install now, and tried jsut going with no packages but still the first user account is not in the sudoer.

And yes have tried "su username" and "su"  and "sudo -i" to get the root account to work and nothing all just fail.

I have had the mini.iso working in the past and the first user created was a sudo from the off.  What am I doing wrong

nb can no longer boot from live cd's as well, i was previously but now get ubuntu stdin error 0.

---

### Post by theotherjustin on 2010-01-08
Have you tried "sudo su -" and then issuing "passwd" when in root to set the root password?

---

### Post by sisco311 on 2010-01-08
Is your user in the admin group?

```
id
```

If yes, what's the output of:
```
pkexec cat /etc/sudoers
```
?

---

### Post by nicktids on 2010-01-08
su
Hi thanks for the replys

 entering "sudo su -" and then the user password leaves me with user not in sudoer file this will be logged 

entering id give a "groups =4(adm)"  so i'm guessing i'm in admin but i can run anything. 

So I have no idea, only a week ago I managed to install to a USB drive this was and i got sudo access without any problem by "su"

to your edit at the mo i have only a minimal install without pkexec installed at all but I've tried nano to read the sudoers file and don't have read access

---

### Post by sisco311 on 2010-01-08
> **nicktids said:**
> su
Hi thanks for the replys

 entering "sudo su -" and then the user password leaves me with user not in sudoer file this will be logged 

entering id give a "groups =4(adm)"  so i'm guessing i'm in admin but i can run anything. 


The name of the admin group is admin not adm. :)

Boot in the recovery mode and add your user to the admin group and edit the sudoers file if needed:

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by nicktids on 2010-01-08
thanks will try now and report back.

Do you know a reason why this has happened?  If not don't worry.

---

### Post by sisco311 on 2010-01-08
> **nicktids said:**
> thanks will try now and report back.

Do you know a reason why this has happened?  If not don't worry.

Well, I'm not sure, but, a bad burn, a damaged or corrupted installation CD or a failing cd-rom drive may cause this kind of problems.

---

### Post by nicktids on 2010-01-08
Thanks for the link did not know that you could get in to a recovery terminal and get to a root login like that very useful.

Went through all the steps on that site and they all failed.

even "adduser *username* admin" gave me a no admin group on the computer which scared me as googled how to add an admin group and found nothing.

But turned out there was no password set for the root I have no idea why as I was entering it every time on the install just as i have done before.

Anyway fixed by loggin in to the recovery and setting the password via passwd.

Thanks alot for your help sisco311 and theotherjustin and I hope this thread help someone else in the future.

edit seen your last  comment above and as I was using the mini.iso on a usb key which downloads all the install files each timeI would have assumed that this couldn't happen!

---

### Post by nicktids on 2010-01-08
I tell a lie I fixed it by editing the /etc/sudoers file to make all users root access this is of course wrong. so don't uncomment the below

#%sudo ALL=NOPASSWD: ALL

So I did find the right file to edited at the site you suggested [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) 

on that site says to add your username to the admin tag.  Admin tag didn't exist for me so and the 106 number was taken up by another command so I created a new line and added a new number

admin:!:109:username

anyone know if this will break something with a new number, but it seems to work and my user name is now in the admin group

---

