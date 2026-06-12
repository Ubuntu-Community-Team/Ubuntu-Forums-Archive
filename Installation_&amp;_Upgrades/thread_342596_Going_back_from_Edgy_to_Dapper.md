---
title: "Going back from Edgy to Dapper?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by bootslap on 2007-01-20
Hi,

I tried to upgrade from Dapper to Edgy, and seem to have hit a problem. However, now I would like to go back to good old Dapper. What is the best way to do it? I do not want to download all the updates again, nor would like to loose the applications that I had donwloaded. Is it possible to avoid a complete reinstall or is it inevitable?

Thanks in advance..

And ... yes remembered ... what should I backup to save my data home or root? Just a newbie ... so apologize for such dumb questions...

---

### Post by wpshooter on 2007-01-20
IMO, the very BEST way would be a complete re-installation of Dapper from scratch.  I hope you have your /home of a separate partition, if you don't you should have.  If you do, just reinstall and don't format your home partition.  Always make 3 partitions: / for root, /home for home, and /swap for linux swap.

---

### Post by Tiede on 2007-01-20
Hmmm... Currently, downgrading is not supported. What exactly are your problems in edgy. Maybe we can help. Also, how did you upgrade? Through apt-get? aptitude? or the supported update-manager -c option. Tell us more, and we'll try to help.
Try this in a terminal: ```
sudo apt-get install ubuntu-desktop
```
Report it to us and in the mean time, try this in a terminal:
```
 less /etc/apt/sources.list | grep dapper
```
if it returns something, then do the following (if it doesn't skip to next step. **be careful with this command. it can be harmful if not followed correctly**
```
 sudo gedit /etc/apt/sources.list
```
In there, type Ctrl+F and in the Search box, write dapper. In the replace box write edgy. Click Search and Replace. It should tell you how many instances are replaced.
close the application.
Next step: back in the terminal, type ```
sudo apt-get update
``` to update your package list. Then, do ```
sudo apt-get install ubuntu-desktop
``` to make sure it is installed.
Finally, type ```
sudo apt-get dist-upgrade
``` reboot when it ends and relaunch in a terminal ```
sudo apt-get dist-upgrade
```

---

### Post by bootslap on 2007-01-20
Hey ... thanks a lot ... Will post the results on Sunday, when I am on broadband.. now I'm using dial-up ... I guess, since I have my home on another partition, surely it would help.

Thanks a lot once again ... Ubuntu rocks!!:guitar:  It's the ubuntu community that is alive and kicking!! And i love this place!!!):P

---

