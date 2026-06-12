---
title: "Help, i messed up my sudoers file"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by mwolfe on 2005-08-28
I was trying to update my sudoers file so all users could start firestarter and i made a syntax error.. This means i can't use the sudo command, and for some reason the root terminal is not working, i get an error message.
```

Failed to run /usr/bin/x-terminal-emulator:
 Child terminated with 1 status

```

I've always just used sudo for commands in ubuntu since i never have given the system a root password, and i've been unsuccessful at loggin in as root or su'ing to root.. How can i fix my sudoers file?

---

### Post by mwolfe on 2005-08-28
Damn it looks like i'm screwed.. I had never activated a root account, so i can't get full privileges.. And i can't edit that file without root privileges. I can't sudo because it doesnt work since the file is messed up.. The only way i can think of fixing it is to edit the file from outside this environment.. any good ideas for this?

---

### Post by manicka on 2005-08-28
Download a knoppix live CD. You should be able to boot into knoppix, mount the partition and change the sudo file back. 
Knoppix is great and has saved me a few times.

---

### Post by mwolfe on 2005-08-28
Alright i'll do that.. 
I thought i had it fixed, i was able to find a driver for read/write access to ext3 for windows..
I opened up a decent editor and deleted the last line, which is the one that i had added and nothing more.. ( i was a bit scared about the new line codes between systems because i know that can be a problem).

I booted ubuntu, and tried to sudo.. It says 
mwolfe@wolfesystem:/etc$ sudo
sudo: /etc/sudoers is mode 0644, should be 0440
I dont' know why it changed the permissions, i suppose so that it did that when i opened it in windows.. 

I'm downloading knoppix now.. HOpefully it will be done downloading within a a few hours..

---

### Post by az on 2005-08-28
No, just boot into recovery mode and
nano /etc/sudoers

or

passwd (name) (password)


If you never set a root password, you are dropped into a root shell in recovery mode.  No need to download anything.

---

### Post by Sam on 2005-08-28
Also use 'visudo', it checks the syntax before saving.
From Gnome:
```
$ export EDITOR=gedit && sudo visudo
```
From the console:
```
$ sudo visudo
```

---

### Post by mwolfe on 2005-08-28
Alright i'm not sure what you guys are referring to, but when i boot up in recovery mode i get asked for the root password for maintenance, i do not know what this is (there really isnt one, i'm the only one who uses this computer, and i never set one) i've tried my user password, and a blank password and neither work.
It also says press control-d to continue, if i do that it just boots ubuntu like normal. If i open a terminal there i cannot sudo, and i cannot open the root terminal, i get that error i mentioned above. I downloaded knoppix live, i'll burn that and try it most likely since i can't get anything else to work

---

### Post by mwolfe on 2005-08-28
Alright i'm sorry, i guess i can get in to edit it using nano.. The problem now doesnt seem to be the syntax, it says the 
sudo: /etc/sudoers is mode 0644, should be 0440

i checked the permissions on the file, this is what i get
-rw-r--r--   1 root   root       405 2005-08-28 09:49 sudoers

so i tried 
mwolfe@wolfesystem:/etc$ chmod 0440 sudoers
chmod: changing permissions of `sudoers': Operation not permitted


I'm not sure what to do.. should make another sudoers file with the correct syntax and permissions and overwrite this one? 
Does anyone have one they could send me? 
My IM name is mizzulla.

---

### Post by mwolfe on 2005-08-28
everything is back working. I downloaded an ubuntu live cd, booted it, mounted my hard disk drive, and changed the permissions on the file back to 0440 and restarted, everything looks like its working now. I think this is a good time to go activate my root account.

---

