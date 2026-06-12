---
title: "upgrading to karmic alpha 5 from jaunty stuck at installation"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2009-09-05
Hello,

while I was trying to upgrade my system from jaunty to karmic koala version alpha 5, my computer stuck. After a hard reboot I have the ability to enter in karmic, yet I only have the ability to use the terminal.

The problem is that while I was on the step of the installation of the packages (the step of downloading them was successful and over) I opened opera. The result was that my pc "stuck". 

Is there a possibility I can "rejuvenate" the installation via command line?

Thank's a lot,
Regards!

---

### Post by paul_in_london on 2009-09-05
Try rebooting into recovery mode. When you reach the menu, choose **netroot** to get a root prompt. Then run:

```
aptitude update
aptitude safe-upgrade
```

---

### Post by Claus7 on 2009-09-05
Hello,

first of all thanks for your response. 

Before anything else I have to say that I cannot see in the grub menu anything that has to do with karmic. The upgrade process was interrupted way before the installation of the kernel and the update of the grub menu. 
So I enter to the latest recovery mode of jaunty.
Now about the commmands I have to say this:
i)the first one was completed successfully without giving any errors.
ii)the second one was interrupted very early saying that revolution(!) had unmet dependencies. 

What I want to do is, if possible, to resume the upgrade of jaunty to karmic from the installation step, without having to use any cd.

Thanks once again,
Regards!

---

### Post by paul_in_london on 2009-09-05
Revolution?! Hmm. Get a root prompt again. Have a look at **/etc/apt/sources.list**. Change all occurrences of **jaunty** to **karmic** in that file if necessary. (You could use **nano** to edit it). Then repeat the **aptitude** commands. If it still doesn't work, try doing:

```
dpkg --configure -a
```

and then try to update/upgrade again.

HTH.

---

### Post by bear24rw on 2009-09-05
safe-upgrade wont solve dependancies

```

sudo aptitude update
sudo aptitude full-upgrade

```

---

### Post by paul_in_london on 2009-09-05
Fair point. I should have said dist-upgrade or full-upgrade (same thing)!

---

### Post by Claus7 on 2009-09-05
Hello once again!

I had checked my /etc/apt/sources.list and all the uncommented lines have the string karmic.

Now trying the dpkg --configure -a it took some time yet it ended with some errors like:
ubuntu desktop cannot be installed, it has some unmet dependencies (like xsplash if I remember correctly) which is not installable.
also evolution had some unmet dependencies.

I will try the **sudo aptitude full-upgrade** command and let you know. Unfortunately I boot from my old hard disk to write these things, so I delay in responses.

Regards!

---

### Post by paul_in_london on 2009-09-05
Ok, good luck!

---

### Post by Claus7 on 2009-09-05
Hello,

thank you *paul_in_london* and *bear24rw*! The upgrade is completed. I'm talking to you now from karmic alpha 5! I have some things to report, yet I'm very tired now. I'll fill this in tomorrow.

Thanks once again,
Regards!

---

### Post by Claus7 on 2009-09-06
Hello once again!

The following post will summarize all the steps I followed in order to have a complete upgrade from jaunty 9.04 to karmic 9.10 alpha 5 and refer to the impediments I faced while doing so.

At the beginning I pressed Alt+F2 and in the panel that appeared I typed:

```
update-manager -d
``` 

That way I was starting the procedure of updating my machine. Everything was going smooth and normal, till the step of the installation of the packages. I had the finest idea to open opera browser and suddenly everything stopped working. The thing is that jaunty was prone to freezing (even though many kernel versions were appearing in the meantime) so either it was jaunty's fault entirely or mine as well, because I "pushed" the system at a time I should have avoided to do so.

The thing is that I had to restart my system with the hard way, meaning that I had to press the restart button. And now the real story begins!

I had the impression, that since the downloading of the packages went ok, that somehow I could resume the process of updating, at the installation step, via command line. 

My impression seemed to be correct and *paul_in_london* and *bear24rw* had the good intention to provide some help.

Now, what I suppose that someone has to do under the same circumstances would be to choose **netroot** from **recovery mode** of your **latest kernel option** in the **grub menu** and:
check if /etc/apt/sources.list
has karmic (or the version you wish to update to) as a string name and type

```
sudo aptitude update
sudo aptitude full-upgrade
```

I typed this and the procedure of updating continued as expected. Just some few remarks. While installing software I was supposed to answer some questions. If you type something that you do not wish, I have no idea how you can delete it. Fortunately I was asked very few questions...
Also the screen after some time went totally black. In order to bring it back I pressed the button Page Down. I do not know if any key would do the same. The mouse was not working at the moment, which is normal. 

And finally something else:when the installation finished I rebooted my system and at the step:
> checking root file system

I got:
> fsck died with exit status 4

> An automatic file system check (fsck) at the root filesystem failed.
A manual fsck must be performed, then the system restarted. ....

There I typed manually the command fsck and when it finished I rebooted. The next time I did the same and in the end I typed ctrl+D

The reboot process continued and I was able finally to see the desktop of karmic.

The fsck thing I think that has to do with an old disk of mine and is irrelevant with the upgrade process. Yet, because previously, with other upgrades, I hadn't faced anything like that, I refer it here.

So alpha 5 is here and running!

Thank you once again,
I hope this recapitulates things so as to be helpful for others,
Regards!

---

