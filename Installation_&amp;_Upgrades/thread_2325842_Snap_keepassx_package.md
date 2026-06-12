---
title: "Snap keepassx package"
date: 2016-05-25
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2016-05-25
I tried to install keepassx from the snap package on 16.04 just to try out the new package format. It installed, but when I opened it, it didn't render with the correct theme, nor could I navigate to my Documents folder where my database was. The same package installed from Apt works as expected. Has anyone as tried the snap package?and does it work for you ?

---

### Post by howefield on 2016-05-26
Have tried the keepassx snap package and confirm on both counts, appearance and reading the file system outside of it's own "container". Only way to get a working snappy keepassx was to copy the database to the snap folder.

```
/home/*user*/snap/keepassx-elopio/1/
```

Have yet to look around and find out whether it is possible to allow the application to browse the file system.

---

### Post by cybergalvez on 2016-05-26
saw that last night after I posted this. Yes I was able to open the file system within its container. I really didn't g much further, not sure how useful it is if you can't go outiside the container. Also I really didnt like that it didn't get themed, instead it was themed with the standard ugly gtk default theme not the nice paper theme that I am using. To me it just looks like some bugs in the snap package format that still need to be worked out, either that or this particular package was not created correctly. Didn't see any other GUI applications to try out to see if other behaved the same way or not.

---

### Post by howefield on 2016-05-26
> **cybergalvez said:**
> ...To me it just looks like some bugs in the snap package format that still need to be worked out, either that or this particular package was not created correctly. ....

Pretty sure it is just early days and stuff like this will be worked out rather than an incorrect package..

---

### Post by elopio3 on 2017-02-28
Hey, better to reply late than never.
I made that package to test a few things, but it was by no means official nor stable nor intended to be pretty :)

After finishing my tests, I tried to send it upstream for them to take care of polishing the final details, and found that the keepassx developer was missing in action and that a new community fork was starting.

So, instead of installing keepassx-elopio, try installing keepassxc:

sudo snap install keepassxc

If you still find any problems there, please report them directly to the upstream developers: [https://github.com/keepassxreboot/keepassxc/issues](https://github.com/keepassxreboot/keepassxc/issues)

Also note that snaps by default can only read and write to ~/snap/<snap-name>. That's for security, you don't want your skype snap to be able to read your keepassx database. On the phone we have a content intermediary to give access to specific files, but on the desktop that's still work in progress. To solve that for now, some snaps have a temporary plug that gives them access to all the files in the $HOME that are not hidden and not in the directory owned by any snap.

---

### Post by howefield on 2017-03-01
Thanks for the update elopio3, appreciate the info on keepassxc.

---

### Post by AMusnikow on 2017-03-26
> **howefield said:**
> Thanks for the update elopio3, appreciate the info on keepassxc.
I installed keepassxc from Ubuntu Software and was able to open my .kdbx file. It looks good.

---

### Post by usinguuu on 2017-04-12
Yes, keepassxc looks good but unfortunately does not use interface removable-media.

---

### Post by kenwag on 2017-05-07
I also was unable to access my DB file in Dropbox using the version of keepassx from the Ubuntu software installer, but OK with the apt-get install version.  (On Ubuntu 16.04)
Makes snaps pretty useless for me.

---

