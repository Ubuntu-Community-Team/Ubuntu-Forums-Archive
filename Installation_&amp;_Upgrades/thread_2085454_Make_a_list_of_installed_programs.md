---
title: "Make a list of installed programs"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by bob-linux-user on 2012-11-18
I want to make a list of all the programs I have installed on 12.04 before I do a clean install of 12.10. I have seen various ways of getting the computer to come up with a list, but this would be a list of **every** program on the PC. What I would really like is a list of the "main" programs and as such I thought a complete list of all the programs referenced by alacarte from the gnome fallback menu would be the way forward. 

Is there an easy way of doing this please? Is the alacarte configuration held in a plain text file somewhere?

Please advise.

---

### Post by darkod on 2012-11-18
This is old but it should work, if that's what you need:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I guess you can edit the my-packages file before using it in the new installation so you can remove some packages that you don't wish to install.

Since this is a dpkg list it should also include programs you installed manually with .deb files but if they are not in the repository of 12.10 it can't install them automatically so you will have to do it manually again.

---

### Post by ibjsb4 on 2012-11-18
I found this

[http://ubuntuforums.org/showthread.php?t=1449509](http://ubuntuforums.org/showthread.php?t=1449509)

Myself, when I want a list of GUI app's I just go to /usr/share/applications.

---

### Post by bob-linux-user on 2012-11-18
Thank you all for your prompt replies. I made a list of all the applications in usr/share/applications by putting a simple script 
ls > file.txt
in the folder and running it. I now have a list I can edit etc.
Thank you

---

### Post by ibjsb4 on 2012-11-18
Works for me too  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by raja.genupula on 2012-11-18
> **bob-linux-user said:**
> I want to make a list of all the programs I have installed on 12.04 before I do a clean install of 12.10. I have seen various ways of getting the computer to come up with a list, but this would be a list of **every** program on the PC. What I would really like is a list of the "main" programs and as such I thought a complete list of all the programs referenced by alacarte from the gnome fallback menu would be the way forward. 

Is there an easy way of doing this please? Is the alacarte configuration held in a plain text file somewhere?

Please advise.

Software center can also help you with this .

---

