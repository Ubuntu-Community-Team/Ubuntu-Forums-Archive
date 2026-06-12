---
title: "Admin password is wrong??"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by kvndodson91 on 2010-05-03
I hope this is in the right section. After I did a clean install for 10.04 I had to reinstall my printer drivers. during setup it ask me for my password. I had no problem with 9.10 but now I cant go any farther then that, it keeps telling me my own password is wrong. any ideas on how to get it to work?

where i got the driver from
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)

---

### Post by wilee-nilee on 2010-05-03
This may help, but maybe wait for others to chime in.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by kvndodson91 on 2010-05-03
If all else fails ill try that. I dont think its the problem, I use my password for everything else, its just during the driver installation it apparently isnt correct. But i guess i wont know until i try it. thanks for the reply.

---

### Post by wilee-nilee on 2010-05-03
> **kvndodson91 said:**
> I hope this is in the right section. After I did a clean install for 10.04 I had to reinstall my printer drivers. during setup it ask me for my password. I had no problem with 9.10 but now I cant go any farther then that, it keeps telling me my own password is wrong. any ideas on how to get it to work?

where i got the driver from
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)

So did you go to system-admin-printing to see if the drivers are available via Ubuntu. Generally you don't have to get them from a manufacturer.

---

### Post by kvndodson91 on 2010-05-03
I tried that, and it could not find drivers for Lexmark 2600 series printers

---

### Post by wilee-nilee on 2010-05-03
> **kvndodson91 said:**
> I tried that, and it could not find drivers for Lexmark 2600 series printers

I figure you had, I wonder if this a root access 1st before installing the driver, issue. I have no clue really I have never had to install a 3rd part driver.
[http://ubuntuforums.org/showthread.php?p=6439321](http://ubuntuforums.org/showthread.php?p=6439321)
Found this 3rd post by sef has a link to installation in Ubuntu.

---

### Post by kvndodson91 on 2010-05-04
I had an idea. im somewhat new to linux and im still learning the terminal and how it generally works so bare with me if this doesnt make sense. i remember making a root launcher a while back with the code

```
gksudo "gnome-open %u"
```

so i could drag and drop things to open as root. i gave it a try with the driver file (which is a shell file, .deb.sh) and it didnt work. but the principal is still there. can i create a launcher to launch a shell script as root? just a thought, not sure if it would work

---

### Post by wbar2 on 2010-11-21
> **kvndodson91 said:**
> I hope this is in the right section. After I did a clean install for 10.04 I had to reinstall my printer drivers. during setup it ask me for my password. I had no problem with 9.10 but now I cant go any farther then that, it keeps telling me my own password is wrong. any ideas on how to get it to work?

where i got the driver from
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2650&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)

It's asking for the root password. Trying running the script with sudo in the terminal using:

```
sudo sh NAMEOFSCRIPT.sh
```

---

