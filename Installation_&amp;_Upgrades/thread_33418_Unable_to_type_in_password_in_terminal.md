---
title: "Unable to type in password in terminal"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by n21roadie on 2005-05-10
Another problem with this flavour of linux , i now cannot type in my password in terminal to open/edit files ? , was able to but not now,

Which platform of linux is the best ????

---

### Post by Zelut on 2005-05-10
You're going to open up quite a thread asking 'which distro is the best'.  There are so many out there & so many people are dedicated to their distro... we could argue for months about which is better.  It all just depends on what you're looking for.

Is there anything you've changed or installed since you were able to enter your password?  Maybe that is the issue.

Are you using sudo <editor> <filename> ?

---

### Post by Maestro23 on 2005-05-10
[QUOTE=n21roadie]Another problem with this flavour of linux , i now cannot type in my password in terminal to open/edit files ? , was able to but not now,

Which platform of linux is the best ????[/QUOTE]


Have you check the Starter Guide for help yet?: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Zelut on 2005-05-10
The user guide is a GREAT help and I also use the ubuntuaddon pack found here:

[www.christeredwards.com/test/ubuntuaddon.zip](www.christeredwards.com/test/ubuntuaddon.zip) (I actually can't find where I saw it originally but I have it backed up on my private server.  Simply unzip & run # sudo ubuntuaddon.sh.

this installs some updates & automatically does a lot of the work that the ubuntu guide shows you how to do manually.  Give it a try

---

### Post by n21roadie on 2005-05-11
Many thanks for the replies so far, must check them out,

Another question is there any system check program , similiar to
Chkdsk, and the event viewer in wind*ws

---

### Post by Zelut on 2005-05-11
Not sure about the event viewer (never used it in windows, never looked for it here) but I do know that the linux filesystem automatically checks & defrags (if needed) at reboot.  

I'm sorry I dont remember the command to manually check, I'm sure someone here does.  I'm fairly new back to linux myself.  I used to know all this junk but its been years since I was a user (sounds like some kind of reverse AA meeting lol)

---

### Post by n21roadie on 2005-05-11
Still unable to type in password , 
is it possible to disable password in terminal,

---

### Post by Malac on 2006-07-14
Just to make certain, you do know that the terminal doesn't show any feedback that you are typing in the password, the cursor doesn't move and there are no asterisks.
just type in your password and hit enter. Ctrl-U resets it if you make a mistake.

---

### Post by adottedfellow on 2006-08-06
i can't type the damn password in the terminal. i tried typing it after pushing enter it was saying wrong password. i am trying to use the "su" command and it was aking for a password and i can't type it. please do help me i can't unpack needed drivers so i can connect to the internet using ubuntu 5.1

---

### Post by Malac on 2006-08-06
Okay there is a huge amount of threads about this on the forums from new users.
to run some thing as root type:
```
sudo [SIZE=2][COLOR=DarkRed]*(plus the command you wish to run)*[/COLOR][/SIZE]
```
Then you will be asked for your initial user password.
To use "su" you will need to "sudo" it first as in:
```
sudo su
```
If you have setup a root password in [System->Administration->Users and Groups]
You can just type in "su" and the root password which willl probably be different than your initial user. Though this last method is not recommended for security reasons.

---

