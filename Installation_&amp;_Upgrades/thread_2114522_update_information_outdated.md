---
title: "update information outdated"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by Lucius Ferus on 2013-02-10
Hello,
I have a red icon on the top pannel in my Xubuntu install, saying like update information outdated.
I've read a similar thread here and tried  sudo apt-get update and, it installed several packages but by the end produces the following output and the red icon comes back again:

W: Failed to fetch cdrom://Xubuntu 12.10 _Quantal Quetzal_ - Alpha i386 (20120724)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 12.10 _Quantal Quetzal_ - Alpha i386 (20120724)/dists/quantal/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 12.10 _Quantal Quetzal_ - Alpha i386 (20120724)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 12.10 _Quantal Quetzal_ - Alpha i386 (20120724)/dists/quantal/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

My preferences are set for daily updates.
I would apreciate help.
Best regards.:guitar:

---

### Post by ibjsb4 on 2013-02-10
Looks like you need to uncheck CDrom

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Lucius Ferus on 2013-02-10
Well, it didn't worked; in the first box that appears i can't check or uncheck the cd-rom box, in the other sources box i can and i did but, firstly it worked and now it doesn't anymore, the icon is back.
I would appreciate whatever other ideas.

---

### Post by ibjsb4 on 2013-02-10
edit

---

### Post by Lucius Ferus on 2013-02-10
In Other Software it is not possible to edit, not available, grey like, but the cd-rom Xubuntu ect... was unchecked.

---

### Post by Bashing-om on 2013-02-10
Lucius Ferus; Hi;

Have you rebooted after unchecking the CDrom checkbox ? Then reload the sources ?

If there still exist a difficulty ..take a look at the source file directly and ensure if an entry for CDrom exist in that file that it is commented (#) out.
```
cat /etc/apt/sources.list 
```[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by Lucius Ferus on 2013-02-11
Well, ther's a screenshot of what i had in front of me; even selecting cd-rom i couldn't edit it. Reload the sources, there's no such option there either. But, i rebooted acouple of times.
Finally, i decided to remove it, it's unlikely i need it.
And for just now it's OK. But, that icon might come back, although it wouldn't make any sense...
So Thank's you both. But don't forgget, if that icon returns i'll be back.
I'll be back as well to see if you post any comment.
Cheers.):P

---

### Post by Bucky Ball on 2013-02-11
Open a terminal and run:

```
sudo apt-get update
sudo apt-get upgrade
```

That will get everything completely updated. The update icon will return when there are available updates and depending on how often you've set the system to notify you of updates.

---

### Post by ibjsb4 on 2013-02-11
If you have resolved this please ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Lucius Ferus on 2013-02-11
Everything seem's OK.
Thank's everybody.

---

