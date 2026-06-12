---
title: "No Shutdown With 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Frantic_Earthling on 2011-10-14
I have just upgraded from 11.04 to 11.10.

The upgrade went smoothly. Everything seems to be working fine with one exception: I cannot shutdown, either from the menu or with *sudo shutdown now* or *sudo shutdown -P 0*.

The only messages I get are:

* Killing all remaining processes  [FAIL]
* Asking all remaining processes to terminate [OK]

then the system hangs.

If I switch off my machine and restart 11.10, I get no errors, the system starts normally.

---

### Post by An Sanct on 2011-10-14
Have you tried to [log off] first and from the log in screen to choose shut down?

I have seen, that if I push the power button, Ubuntu asks me what to do: restart/shutdown/hibernate, maybe you can try that too.

---

### Post by Frantic_Earthling on 2011-10-14
Yes, I tried all those options.

Unfortunately, they lead to exactly the same error messages after which my systems hangs.

---

### Post by An Sanct on 2011-10-14
What does the shutdown log say?

Location: */var/log/dmesg*

Perhaps, if the log is too large, rename it to something like dmesg.old and post the new version including the crash.

PS. please attach it as a file (click "Go Advanced" and find the attach file button - paper clip, to do so)

---

### Post by Frantic_Earthling on 2011-10-15
Thanks for your help, but I have decided that I would do a fresh install, which is what I usually do.

I don't like upgrading and apparently, facts bore me out!

---

### Post by Frantic_Earthling on 2011-10-15
My fresh install shuts down without any problem.
An Sanct, thanks for your help.

Actually, I think that the problem was due to the fact that the French  Oneiric archive repositories I was using were down. Something was missing in my upgrade.

I did my fresh install from UK repositories without any hitch.

---

### Post by vanadium on 2011-10-15
Another possibility why your system wouldn't shutdown could have been that you had the LibreOffice quickstarter running.

---

### Post by Frantic_Earthling on 2011-10-15
Do you mean the systray quickstarter?

I never activate it, but I will bear this in mind.

---

### Post by neorg on 2011-10-22
Same problem here.
Laptop won't shut down

**Killing all remaining processes  [fail]**

Waiting for a solution.

---

### Post by Frantic_Earthling on 2011-10-23
Actually, even though I did a fresh install, I still once in a while get this freeze during shutdown. After these messages: 

> * Killing all remaining processes [FAIL]
* Asking all remaining processes to terminate [OK]

The system hangs.

---

### Post by neorg on 2011-10-23
I noticed the following. 

During normal operations sometime programs hangs in the desktop. Than the system won't shutdown. 

When I first kill the hanging programs, shutdown will successfully complete.

(I did not do a fresh install. I updated from 11.04)

---

### Post by ronzo on 2011-10-26
I've upgraded to Oneiric on 3 systems and NONE of them shuts down properly. (also the release-upgrade did not complete without errors on those systems...)

---

### Post by jonbonjovi on 2011-11-02
Same problem here on a HP dv-5.

Until 11.04 no problem. The issue started when installed (fresh install) the 11.10.

---

### Post by Rebecca807 on 2011-11-04
Ever since the last update in 11.10, Unbuntu won't shut down for me either.  I'm fairly new to Unbuntu and unfamiliar with some of the commands I've read.  I guess I better read up because saying goodbye to Gates felt too liberating to go back now.  Mine was not a fresh install, I updated from 11.04.

---

### Post by ballantony on 2011-11-04
I'm getting the same problem.  It seems to happen when you've swithced users during a session

---

### Post by Barnbrat on 2011-11-08
Yep, same discovery here, especially if someone forgets to log out and switches to another user.

---

### Post by missmoondog on 2011-11-08
slightly off topic, but still related in some regards.

not that i get errors, but in 11.04 several of the machines i maintain, i have to log out, click shutdown, then from that login window, click shutdown from the menu in the lower right corner.

the one machine i had a clean install of 11.10 on, did exactly the same thing.

edit:
now have all 9 machines i maintain updated to 11.10. where did the option to logout THEN go into suspend go? are you automatically logged out when going into suspend?

---

### Post by Pépou on 2011-11-19
Same problem here : no shutdown with my dell inspiron 6400 and ubuntu 11.10...

---

### Post by neorg on 2011-11-19
I did a complete fresh install (no dist-upgrade) and now the problem went away. 

I noticed also some other problems with the dist-upgrade from 11.04 to 11.10. Scribus-ng didn start (cached op start up) and I couldn't save files in GIMP correct, while saving a file GIMP locked up fully.

I am running Ubuntu for 7 year now and had noticed problems with the dist-upgrade more than once. It alway better to do a fresh install.

---

### Post by Drum Pan Sound on 2012-04-18
*Disclaimer:  I'm new to everything and know nothing*

I've got the message, "Asking all remaining processes to terminate..." after a fresh install of 11.10 on a Dell Dimension 4550 tower.  It's been stuck about a half hour.  

I think I'm gonna kill it and see if it boots into the OS based on what  I've read.  Perhaps my problem is something like others' from this  thread.   One thing - the fan has not worked for  years and it makes me wonder if the MoBo is wonky as XP had been seeming  more sluggish even after the last few OS re-installs.  Maybe a hardware  failure can trigger the problem?



:guitar:

Update:  I was able to boot into the OS and shutdown without issue.

---

### Post by jamesgthang on 2012-04-18
In my case, I found it to be related to NFS.  

I have another file server running Ubuntu 10.10 which shuts down faster than my main desktop.  If I leave the NFS server on and shutdown the main desktop, it powers off with no issues.  

If I shut down the file server without first un-mounting it on the main desktop, the system hangs at the point described in this thread.

---

