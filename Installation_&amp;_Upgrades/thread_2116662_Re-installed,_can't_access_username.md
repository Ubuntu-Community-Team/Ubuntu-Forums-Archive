---
title: "Re-installed, can't access username"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by AtariBaby on 2013-02-16
**1. Recently my ubuntu machine started performing badly.** BTW I'm a total n00b.

I read about using the LiveCD, ejecting the mounts, and installing again, to fix issues. I did this, selecting options to keep files and programs, and when prompted, I upgraded to 12.10.

All went well, but at the end it asked me for a username and computername. I forgot I already had those, and I supplied different ones.

Looking through the directory structure of the machine, I can see my old username and all its folders and files appear to be intact. However, if I log out of the new, *wrong* user, I can't login as the old, *original* user. How can I fix this?

**2. I got the following help on the problem:**

Thomas Krüger:

About the usernames and passwords:
If I read it correctly, you have a new fully working account, but you want the old account back.
You can get at a list of all users by opening the Terminal application and running:

getent passwd

The username is in the first field, the numeric ID in the third. On Ubuntu IDs &#8805; 1000 are "normal" users. IDs below and 65534 are system users for servers and services.
Now see if there are actually two user accounts in that range. It should be most likely IDs 1000 and 1001 then.

If you have two accounts, you can reset the password of the other user with this command in the Terminal:

sudo passwd username

Replace "username" with the real username and type the new password twice. Nothing will be echoed (no *** will be shown).

If you don't see a second username, please run the exact command below (use copy & paste) in the Terminal and copy the full output for us. We will tell you how to recover the old user profile.

id; stat /home/*; getent passwd | fgrep bash


**3. I didn't see the username in the list, so I did the second command.** FYI the username with all my files and programs in it is misterfantastic

```
uid=1000(ataribaby) gid=1000(ataribaby) groups=1000(ataribaby),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),107(lpadmin),124(sambashare)
  File: `/home/ataribaby'
  Size: 4096 Blocks: 8 IO Block: 4096 directory
Device: 801h/2049d	Inode: 3088386 Links: 21
Access: (0755/drwxr-xr-x) Uid: ( 1000/ataribaby) Gid: ( 1000/ataribaby)
Access: 2013-02-14 22:52:55.813571132 -0800
Modify: 2013-02-15 07:37:47.379133237 -0800
Change: 2013-02-15 07:37:47.379133237 -0800
 Birth: -
  File: `/home/misterfantastic'
  Size: 4096 Blocks: 8 IO Block: 4096 directory
Device: 801h/2049d	Inode: 3014658 Links: 49
Access: (0755/drwxr-xr-x) Uid: ( 1000/ataribaby) Gid: ( 1000/ataribaby)
Access: 2013-02-14 21:53:20.890549241 -0800
Modify: 2013-02-14 21:34:03.215410964 -0800
Change: 2013-02-14 21:34:03.215410964 -0800
 Birth: -
root:x:0:0:root:/root:/bin/bash
ataribaby:x:1000:1000:,,,:/home/ataribaby:/bin/bash
```

**4. That's where I'm at, and I would like to get this fixed while I have time this morning. Can anyone tell me what to do next?**

---

### Post by darkod on 2013-02-16
I guess what you want is adding a new user with existing home folder. That would be like:
```
sudo adduser --home /home/misterfantastic misterfantastic
```

That will ask you to enter a new password. You will have to run that command from the currently working user of course.

Also, if you want misterfantastic to have sudo rights you will have to add it too. Otherwise only the new user, the first user of the new installation will have sudo rights.

---

### Post by AtariBaby on 2013-02-16
I did as you instructed plus added the user to sudo.

Thanks for the help. Unfortunately, when I try to log in to misterfantastic now, I enter the password on the login screen and I get the bongo drums and go back to the login screen.

I Know the password is correct because if I try a different password, I see an error that I'm using an incorrect password. But the correct password doesn't let me in, as previously mentioned.

---

### Post by schragge on 2013-02-16
There can be a problem because your old user's numeric IDs are identical to those of the new one (UID=1000, GID=1000). That means that all files in */home/misterfantastic* are now owned by *ataribaby*. When you add a new user with the name *misterfantastic* as Darko suggested, he'll get [UID=1001, GID=1001] and *misterfantastic* won't be able to access files in his own home directory unless you
```

sudo chown -R --from=ataribaby:ataribaby misterfantastic:misterfantastic /home/misterfantastic

```

[highlight]Update 1.[/highlight]
Yeah. That's what you've got now. Log in as *ataribaby* and do what I said.

[highlight]Update 2.[/highlight]
> I did this, selecting options to keep files and programsI'm not sure if this option keeps intact only files in the home folder. Please post the output of
```
stat /var/mail/*
```

---

### Post by darkod on 2013-02-16
It might not own the home folder any more. Go into the working user and try this:
```
sudo chown -R misterfantastic:misterfantastic /home/misterfantastic
```

If that doesn't help, I have no idea.

And next time when upgrading/replacing an installation, don't forget your user. :) This is not windows and linux is VERY strict with permissions.

In your old install your first user was 1000 and now as second user will be 1001. But I hope the chown command above can help make it owner of the home folder again.

Don't try to manually force it to be 1000, I think it will only get you into more trouble.

---

### Post by AtariBaby on 2013-02-16
Wow guys, I'm in. :guitar:

I hope I can bug you a little more. I see I have a new problem. None of my programs like sabnzbd+ or sickbeard have started automatically like they used to. Any ideas what I'll need to do get all this stuff running again?

---

### Post by schragge on 2013-02-16
If you entered my variant of chown then try
```
sudo chown -R --from=ataribaby misterfantastic /home/misterfantastic

```

---

### Post by AtariBaby on 2013-02-16
Thanks. I tried that again, but programs still won't start automatically like they used to. I tried to manually start sick beard and got an error that the cheetah module wasn't installed. What to do about all these problems?

---

### Post by AtariBaby on 2013-02-16
been trying to solve the problem on my own, not much success.

---

### Post by darkod on 2013-02-16
Sorry, but I can't help much with programs not running. As mentioned, Linux is very strict with permissions and I don't even know where to start looking.

If they were installed somewhere like /usr/local (or have one part of the files there), they might belong to the new user now (user code 1000) instead of your old user.

You managed to set the correct ownership of the home folder but other files outside it will still remain "messed up".

---

### Post by schragge on 2013-02-16
Just guessing, try this
```

groups ataribaby misterfantastic

```

Compare the group lists for both users, and if they differ, add the new user to all groups the old one is member of.

---

### Post by schragge on 2013-02-16
Another thought.
> **AtariBaby said:**
> I tried to manually start sick beard and got an error that the cheetah module wasn't installed.Have you tried to reinstall all the required dependencies?
```

sudo apt-get install python-cheetah

```

---

### Post by AtariBaby on 2013-02-16
Well, not the end of the world. I've begun to just reinstall everything I want running again. I just hope I don't have a mess out there waiting to confound me in the future.

Thanks to all who helped, and will check back to see if anyone knows the solution.

---

### Post by AtariBaby on 2013-02-16
> **schragge said:**
> Another thought.
Have you tried to reinstall all the required dependencies?
```

sudo apt-get install python-cheetah

```

Oh I missed a couple of replies. Yes, that's what I did. Basically, just started reinstalling as I'm going along.

---

### Post by AtariBaby on 2013-02-16
> **schragge said:**
> Just guessing, try this
```

groups ataribaby misterfantastic

```

Compare the group lists for both users, and if they differ, add the new user to all groups the old one is member of.

Might be onto to something here! Will google how to add misterfanstastic to that long list of groups he isnt' in and report back!

---

### Post by schragge on 2013-02-16
Try
```

id -Gn ataribaby|cut -d' ' -f2-|xargs -n1 sudo adduser misterfantastic

```

---

### Post by AtariBaby on 2013-02-17
> **schragge said:**
> Try
```

id -Gn ataribaby|cut -d' ' -f2-|xargs -n1 sudo adduser misterfantastic

```

Thank you for that Jedi command! I have much to learn.

----

None of this has restore normal operations, which is okay. It seems for some reason much needs to be reinstalled, although the configurations are usually there once it's done. I'll just keep reinstalling and I thank you all for your help. If any of you wind up in San Francisco's Alamo Square, coffee/adult beverage is on me.

---

### Post by schragge on 2013-02-17
Oh it's not jedi at all.

There are three commands connected through a pipeline.

The first one, *id -Gn ataribaby*, basically does the same as *groups ataribaby*: shows groups the user ataribaby is member of, but in a slightly different format. Try it in a terminal, and see.

The second one, *cut*, takes the output of *id* as its input, and retains all space-delimited fields, but the first (the first group is the private group of that user, we don't need it).

The third, *xargs* is more interesting. To see, what it does, replace *sudo* with *echo* and run it again:
```

id -Gn ataribaby|cut -d' ' -f2-|xargs -n1 echo adduser misterfantastic

```

---

