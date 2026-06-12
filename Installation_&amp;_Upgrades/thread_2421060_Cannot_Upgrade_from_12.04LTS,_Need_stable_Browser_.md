---
title: "Cannot Upgrade from 12.04LTS, Need stable Browser atleast..."
date: 2019-06-15
forum: Installation &amp; Upgrades
---

### Post by adambond on 2019-06-15
I am currently (still :(  ) running 12.04lts  only because my system wont upgrade... for what ever reason.  I dont know.  

Since i cant upgrade, at the very least, i need a stable browser. Or let me rephrase that, I need to know how to install a stable browser. My current Firefox (52.0.2 32bit) and Chrome ([COLOR=#303942][FONT=Ubuntu]48.0.2564.109)[/FONT][/COLOR] are getting pretty glitchy, and they both now no longer play Netflix. Among many other problems. 

One of the problems im having installing anything is my Wine is also a train wreck apparently. It wont install anything. 

Can anyone point me to the best course of action, before im forced to just go out and buy what ever flavor windows in currently on. :sad:

Thank you in advance

---

### Post by coffeecat on 2019-06-15
> **adambond said:**
> my system wont upgrade... for what ever reason.

The reason is simple. Ubuntu 12.04 is not just dead; it is a rotting corpse. It passed end of life over 2 years ago. The repositories are closed, which is why you cannot update it. It is a security disaster waiting to happen.  

> **adambond said:**
> 
Can anyone point me to the best course of action

Your best course of action is to backup all your personal data and make a fresh install of a supported version. 18.04, as the latest in-support LTS, would be a good choice. Please be aware that the desktop environment has changed. With 12.04 you had Unity. The default desktop in 18.04 is gnome, although you can still install Unity in 18.04 if you prefer that.

---

### Post by oldfred on 2019-06-15
The 14.04 LTS has reached end of life. So 12.04 is way past old.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Best to backup /home and list of installed apps (but many have changed) and do a new clean install.
       
       
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below): 
    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
      [/URL]
 [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) 
            Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

### Post by adambond on 2019-06-15
Thanks for the help. 

 I know how to backup pics and docs sure. But I do not know exactly how to back up anything else. 

Would backing up to USB be sufficient?  

I am running a 32bit system, and running Nvidia, would these be a problem doing clean install on latest ubuntu version?

---

### Post by adambond on 2019-06-15
Thanks Oldfred, very helpful!

---

### Post by crip720 on 2019-06-15
You said 32bit system, is that you are using a 32bit OS, or you need a 32bit because your CPU is old enough to be only 32bit(like a P4).  You would have better luck with Lubuntu/Xubuntu if you need a 32bit OS.  There is no more Chrome for 32bit OSs, you need a 64bit system if you want Chrome.

---

### Post by oldfred on 2019-06-15
What is system spec?

I updated, my 2006 32 bit system to 64 bit in 2009. But that required a full reinstall and restore of my data. I had the data in /home & my data partitions, but did not have a list of installed apps.
But when that old you should manually edit list of installed apps to remove old kernels and anything you are not now using. It is just a text file.

---

### Post by adambond on 2019-06-30
Thanks for all the help so far. Its gone smooth till now. 

Not sure if I should start a new thread or not. So i'll continue this one. I have a new computer with fresh Ubuntu and firefox on it. 

Heres the issue. 

I need to export my old firefox data to the new firefox on the new computer. 

New firefox is V65 (64bit), old firefox version is 52.0.2 (32bit). 

I tried the "refresh" method of creating the "Old Firefox data" folder, and copy/pasting it into the new firefox directory.  It literally does nothing. I go to check to see if the logins/passwords transferred over, and its still empty. 

I can manage to copy/paste a bookmark file over and get the bookmarks to show up. But absolutely cannot get the logins/passwords to copy over. 

I tried pasteing the "Old Firefox Data" file into the new firefox's Local directory, AND even the root directory. With no luck for the logins/passwords. :(

---

### Post by wildmanne39 on 2019-06-30
Yes please start a new thread with this new issue, if this thread is solved please use thread tools at the top of the page to mark this thread solved.

Thanks

---

### Post by rsteinmetz70112 on 2019-07-01
Perhaps there should be an abandoned Tag :cool:

---

