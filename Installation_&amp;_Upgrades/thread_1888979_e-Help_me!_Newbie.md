---
title: "e-Help me! Newbie"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by nsalekz on 2011-11-30
Hi there, this is my first post in the forum.
I deleted my micro$oft OS ( format my HDD) and installed Ubuntu 10.04 - and then updated to the latest version ( 11.10, if not wrong ) I found on the site. 

So, I got few questions.. Tried to do some search, but couldn't get any results.

Ok, those are the main ''problems'' for me :

1) Can't access ''root'' folder. ( I guess that's my HDD?)

2) I'm the only user, which means I'm the root user? If yes, why I get denial. Eg, can't enter 
some folders, can't move folder and such?

3) I'd like to have the ''HDD'' from M$ in Computer. ( Inside file system ) 


Thanks for your time, I'm looking forward for some answers :)

Peace and love from 
 Serbia, Novi Sad

---

### Post by BC59 on 2011-11-30
Let's see now.

When you open the Nautilus (the Linux file Explorer) you have to see something like the thumbnail.

On the left panel you can see the The Devices (if you have a different partition etc) Computer and underneath Home and your personal folders Documents, Downloads, Music etc and File System. Finally you can see the Network if you have establish one with other computers.

Now the Home is the personal part of the computer in which you can access without password.

The File system is the part of the System computer. You can access it but you need password to make changes and it's not recommended to do any, unless you are absolutely sure what you are doing.

If you see for instance in the forum or in other sites examples of commands to make changes on the System, many times is needed the root password.

So if you see a command

```
sudo apt-get update
```

means you have to open a terminal (command-line interface) with CTRL+ALT+T or searching in dash search and copy paste the command.
Paste in a terminal is CTRL+SHIFT+V
Then hit Enter and then needs your root password.

The command Update is to update the system to be up to date in order to be able to react on other commands.

Then usually you perform the next command which is

```
sudo apt-get upgrade
``` 

to install to the system the last updates if any.

---

### Post by nsalekz on 2011-11-30
> **BC59 said:**
> Let's see now.

When you open the Nautilus (the Linux file Explorer) you have to see something like the thumbnail.

On the left panel you can see the The Devices (if you have a different partition etc) Computer and underneath Home and your personal folders Documents, Downloads, Music etc and File System. Finally you can see the Network if you have establish one with other computers.

Now the Home is the personal part of the computer in which you can access without password.

The File system is the part of the System computer. You can access it but you need password to make changes and it's not recommended to do any, unless you are absolutely sure what you are doing.

If you see for instance in the forum or in other sites examples of commands to make changes on the System, many times is needed the root password.

So if you see a command

```
sudo apt-get update
```means you have to open a terminal (command-line interface) with CTRL+ALT+T or searching in dash search and copy paste the command.
Paste in a terminal is CTRL+SHIFT+V
Then hit Enter and then needs your root password.

The command Update is to update the system to be up to date in order to be able to react on other commands.

Then usually you perform the next command which is

```
sudo apt-get upgrade
```to install to the system the last updates if any.


Thanks [BC59]("http://ubuntuforums.org/member.php?u=1498360"), it helped me much :)

Now, the only thing left is :
Access to my HDD.

Idk if this what I'm gonna say is possible, but it's worth a try.

Since Ubuntu can't run a application I want ( A game called Lineage 2 ), the setup.exe wont load after I run it w/ Wine.

I was wondering, if I'm able to put w/e I like on my HDD and have the view of a M$ HDD
like in windows?

I could make some stuff by myself from there, cause I'm using windows since I remember myself.

So, what I want to do is :

Download / extract to : C:/program_files/#/#
Cause the directory of the game setup goes there. And I need to do some modifications to the game client.

Hope I've explained it clearly :P

Thanks a lot for your time, appreciate it!

---

### Post by cholericfun on 2011-11-30
i would guess wine does exactly that.
and even if you somehow managed to change the folder structure to your liking (which can be done with symbolic links i guess): its the contents that your program is looking for.

if wine doesnt do it (and there may well be a fix for that) then maybe try virtualbox (i.e. install windows on a virtual computer from within the ubuntu install) ?

---

### Post by BC59 on 2011-11-30
If you are going to install the game to Ubuntu through Wine we have the following situation:

Installing Wine AND run it for first time, it's created a virtual Windows installation which is called wineprefix.

This " c:/ " you can find it in home and pressing CTRL+H to see the hidden folders. The folder is called .wine (the -.- on the front is to make it hidden).

In .wine and in the folder drive_c there is your HDD of virtual windows. If you install the game through Wine you'll find the installation on Program Files.

Problem. If you make the changes you say as you did in Windows, it's not sure the game will play.  The changes should be made by Wine config and Winetricks which is included in Wine. Just google and find how for every program.

---

### Post by MG&amp;TL on 2011-11-30
Yeah, there is no such thing as C:/ in Linux/Unix filesystems. Run in a terminal:

```
sudo apt-get install wine
```

and then run it with wine. If that doesn't work, run windows in virtualbox.

Windows filesystems have C:/,    Unix  has "/". Documents/pics and stuff are under /home/"username"/

If, for whatever reason, you do need to access a bit of the filesystem which is not /home/"username"/ (installing the program is NOT a good reason), you can do it with:

```
gksu nautilus
```

which will launch a file browser as root (administrator). BE VERY CAREFUL.

If you need to run something else as root, use 

```
sudo <command>
```

---

### Post by nsalekz on 2011-11-30
Stop bombarding me with information! :P

Well, I've found everything useful till now. I want to thank you all for your precious time.

I've downloaded VM ( Virtual box ) virtualbox-4.1_4.1.6 

Can't get it work :(

Could someone explain to a blond how to do it?

Thanks in advance!

---

### Post by BC59 on 2011-11-30
Where is the problem with Virtualbox?

---

### Post by cholericfun on 2011-11-30
throw your virtualbox download away and use the software centre to install.

maybe have a little more trying and reading with your wine installation though.

PS:
maybe that wasnt clear earlyer. The virtualbox itself is no good to you. You need to get a windows CD and install it to the VB.

---

