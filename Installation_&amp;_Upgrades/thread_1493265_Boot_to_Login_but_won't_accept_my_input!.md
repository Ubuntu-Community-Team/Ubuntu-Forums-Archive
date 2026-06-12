---
title: "Boot to Login but won't accept my input!"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by murdison on 2010-05-25
Sorry if this has been addressed elsewhere... I've searched but not found my exact problem.

Two weeks ago, I followed directions to update to the new version and let things go. It seemed to run fine, no errors and in the end, I was at the new generic GUI with all of my usual desktop present.

For some reason, last week after a power outage at my house, the system boots to a login screen that is basically all black with a little window in the middle giving me the option of loging in under my username or "other". When I click my username the screen goes black, there is a brief flicker of text at the top and an arrow appears. After a second or two, the same login screen reappears... no error... 

If I try "other" it changes to a new username/password window, and if I enter my username/password... exactly the same behavior. I have no idea what is going on.

Secondly, when the login screen appears, there is a message at the top right telling me something along the lines of power management did not start...

Third, I have been able to easily get to my desktop by VNC up until this happened... now it refuses connection or times out trying!

My other computers in my home network are windows, and they are able to see my shares on the Linux machine even though I am not logged in... 

I don't know where to begin. Any help is sorely appreciated!!

---

### Post by cariboo on 2010-05-25
Boot from the live cd and run fsck on the partitions, for example if / is on /dev/sda1 then the command would be:

```
sudo fsck -y /dev/sda1
```

the above command should fix any inconsistencies in the file system.

---

### Post by rob45 on 2010-05-26
Hi i also had log in issues.Have you tried sudo passwd username...?  New at this so correct were necassary anyone.
Or it sudo passwd.....from terminal.

---

