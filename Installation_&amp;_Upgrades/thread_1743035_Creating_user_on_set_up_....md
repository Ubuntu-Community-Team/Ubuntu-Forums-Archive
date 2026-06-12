---
title: "Creating user on set up ..."
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by kufischer on 2011-04-29
Hi,

first of all, I have to stress that I am a quite happy user of ubuntu (kubuntu to be more specific).

Of course, I was interested to see what 11.04 would bring and it does look good however you want to use it.

The reason for this message is that there seems to be a "feature" of ubuntu (and this is true for the natty setup as well as for the kubuntu setup) that is quite annoying if you do not just want to use the pc you happen to have on its own.

Situation for me is that I HAVE to integrate my machines (at least 3 of the 4 but the 4th has to integrate with the other three so all 4 fall into the same pool) with the network of my company. And well, yes, I cannot just tell them that my uid should be 1001 because ubuntu seems to insist on this.

Ok, you can say just create a second user with the correct uid, gid and, yes, of course, that is what I try to do. It is a bit annoying that it seems that I need to creat necessarily a second user, however, this is not the thing that I really want to complain about here. If the creation of the second user would work smoothly but it does not!!!!

For what ever reason ubuntu insists that the scond user has the uid 1001, too!!! The guy inventing this part of ubuntu must have loved this nunmber for what ever reason, lol.

Anyway, the natty distirbution is a bit worse than kubunutu because it insists on creating the home directory with the wrong uid frist and fails misearbly later on, especially when you would like to have an encrypted home. kubuntu (possibly for this very reason) dose not even support to automatically generate encrypted homes. However, what ever I did with the second user also for kubuntu, the result was that in passwd I had a new entry with uid 1001 and needed to mannually edit passwd to set the desired uid and then use chmod to change the created home and after all then, yes, things work.

However, I would say this could be done at least a bit better ...

Of course, if I could tell you what I would love to have is the option on creating a new group (no way that you will have the group of my company setup correctly in your distribution) and set an explicit uid and gid for the user that is necessarily created for the installation. This would be just great!

You might say why I did not try to change uid, gid for the first user after the installation. Well, I tried once but failed misarbly with this probably because I wanted to have the home encrpted. Anyway to support this in a safe manner would be of course an option.

I would apreciate any comment on this topic that would allow me to change uid, gid for the first user while maintining my encrypted home for this user.

Thank you very much for your support,
best regards,

Klaus

---

### Post by dino99 on 2011-04-29
It's in /etc/login.defs. Look for UID_MIN

---

### Post by luvr on 2011-04-29
The first user created will have uid 1000, because, according to Debian policy rules, that is the first *"non-system"* user. Whenever you create a new user, the user and group administration utility will simply take the next free number; in other words, the second user will be uid 1001, the third user will be uid 1002, etc.

If you want to select the user id that you want to assign to a new user account, you will have to use the command line. Under Debian and derivatives (e.g., Ubuntu), you should use the **adduser** command to create a new user; similarly, to create a new group, you use the **addgroup** command.

So, if you need to create a new group for your new user, you should first run the following command (where GROUPNAME and GROUPID need to be set to the appropriate values, obviously):
```
sudo addgroup --gid GROUPID GROUPNAME
```
Then, to create a new user, and set its primary group to GROUPID, you would do the following (again, substituting appropriate values as required):
```
sudo adduser --home /home/USERNAME --shell /bin/bash --uid USERID --gid GROUPID --gecos 'FULLNAME' USERNAME
```
**_Further commands:_**

To add the user to other groups:
```
sudo usermod --append --groups GROUP1,GROUP2,...,GROUPn USERNAME
```
To set a password for the user:
```
sudo passwd USERNAME
```

---

### Post by kufischer on 2011-04-29
Hi luvr,

thanks for your comments and the command line commands. But of course my comments were made to what the graphical user interfaces in unity and kubuntu do when you use them to creat new groups. What they do right now is not really useful for a lot of use cases and I wonder why it should not be possible to make them work in a better manner.

Of course, I can get ubuntu doing what I want to have by doing some hacking on my own, be it with command line commands or with the help of an editor. However, it would be a bit more comfortable if the tools provided would do the job they pretend to do.

Additionally, I think that I am not the only one who would like to see the option of giving the first user to creat its own group with a specific gid and a specific uid. This shold not be to difficult to implement in some expert mode if the ubuntu community considers this to be an expert task ...

Best regards,

Klaus

---

