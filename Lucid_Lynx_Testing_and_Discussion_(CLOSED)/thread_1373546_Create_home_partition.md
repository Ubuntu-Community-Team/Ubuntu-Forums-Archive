---
title: "Create /home partition"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by PaulInBHC on 2010-01-05
I have WinXP with C: and D: partitions, 9.10 partition, 10.04 A1 partition. I am supposing that when A2 is ready, I should make a LiveCD and a fresh install. What do I need to do to create a /home partition now and what do I move from /home in the 9.10 and 10.04 to be able to use it and not lose it if I delete one or both installs?
Thanks

---

### Post by bruno9779 on 2010-01-05
here: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

This is a pretty good tutorial on how to do that.

I Have never tried using the same /home with different /boot.
I guess that some applications that link to kernel modules directly, like virtualbox, would stop working

---

### Post by drs305 on 2010-01-05
It's not difficult at all. I prefer the first link, but pyschocat's has been used for a long time to move /home.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by ronacc on 2010-01-05
do you have any unallocated space on the drive ? if not it gets a bit more complicated .

---

### Post by PaulInBHC on 2010-01-05
Thanks for the links.

@ronacc I moved things around with gparted when I installed 10.04 then learned about grub2, lol
I deleted the swap at the front and created a swap at the back then read about swap space and partitions and why it wasn't working. What a mess I made. I'm trying to avoid that now.

Edit no unallocated space but figured I would make some from the others or delete 10.04 A1

---

### Post by PaulInBHC on 2010-01-10
I followed the psychocats instructions. I gparted, deleted a swap partion that wasn't being used, moved things around (wrongly but it worked, just took a long time) created 10g partition. I followed the instructions but I had two homes to move. I did the 9.10 first and when I did the 10.04 I saw a lot of the message that a newer or same file existed and would not be replaced. I ended up with my 9.10 desktop and FF bookmarks in my 10.04 install.
Then I gparted again and set the flag for the 10.04 sda to boot. To my surprise the grub 2 menu came up on reboot and I was in 10.04.
Now gparted shows the home partition with 8g out of 10. I think I'll gain space when I get rid of the backups and unused programs.

When I look at my new home, it shows the folders with a padlock symbol. Properties shows I do not own these files. How do I change this?

---

### Post by drs305 on 2010-01-10
> **PaulInBHC said:**
> 
When I look at my new home, it shows the folders with a padlock symbol. Properties shows I do not own these files. How do I change this?

You can run these commands substituting your [COLOR="DarkRed"]username[/COLOR]:
```
sudo chown -R *username:* /home/*[COLOR="DarkRed"]username[/COLOR]*  # if you get a ".gvfs" error message, don't worry about it.
chmod 755 /home/*[COLOR="DarkRed"]username[/COLOR]*
chmod 644 /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc

```

This will make all the files in $HOME owned by you, and change the permissions of $HOME/.dmrc to the proper ones. For more on what you are doing, refer to:
[Solving .dmrc and $HOME Permission Errors  ]("http://ubuntuforums.org/showthread.php?p=6161267")

---

### Post by PaulInBHC on 2010-01-10
Thanks, that works. Now if I can just get my desktop back. I fixed FF.

---

### Post by VMC on 2010-01-10
> **PaulInBHC said:**
> ...10.04 A1 partition. I am supposing that when A2 is ready, I should make a LiveCD and a fresh install. ...I'm curious why you think you need a fresh install.
 If you have been keeping updated then when A2 rolls along, your already there. 
The only other reason is to test the A2 install.

---

### Post by PaulInBHC on 2010-01-10
I've been safe updating all along and still have a black screen at login. I get the bongo sound, type my name and password anyway and get the desktop. Then I don't have a mouse pointer so I have to fumble into the Synaptic and type pointer in the search box. Then I have a pointer on screen.

I thought that maybe a fresh install of A2 might fix this and I would be testing the iso too.

---

### Post by PaulInBHC on 2010-01-11
Last night I used the Update manager as I had been on XP for a while. I get the popup warning and click ok. It checks for updates and a short list, all greyed out. At the top it says my system was last updated 8 days ago. I decide to click Check and lo and behold, 253 items 106mb. I install (that took a long time on high speed cable) and restart. Still no login or mouse pointer. Oh well FF works.

Tonight I checked an old game in wine. On exit I had a black screen, no response. I hit the case button and tried to start 9.10. It gives a bunch of text about mountall and ext2 in sda3. I give up.

Back to 10.04 and try update manager. It list a few, ok, then I get a popup about Grub-PC and do I want to keep or replace. I replace.

Good news is I booted into XP just fine. Think I'll stay here till Saturday and decide how I want to go about 10.04 A2 and 9.10

---

