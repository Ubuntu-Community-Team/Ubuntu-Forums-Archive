---
title: "Grub Update Modified Config File - Show Side by Side"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by keith5 on 2014-07-24
So I ran some updates today when prompted and a gui popped up asking "What do you want to do about modified configuration file grub?".  This had several options in the drop down, but it seemed that the main choices I had was to download the maintainer's version or to keep my local copy.  As far as I know, I haven't made any changes to the config files, unless having a windows install changed anything automatically.  But I have made no manual changes to the grub files.  

Curious what would change, I chose the "side by side" option, hoping to see what was going to change.  After selecting that option, the window merely closed and nothing happened.  So now, I am guessing that the maintainer's version wasn't installed, since I wasn't able to select that.  I don't know if there is a way to get back to that gui window or how to install the maintainer's version.  I am thinking that since I have made no manual changes to the grub config files, I would want the latest maintainer's version?  

I ran update-grub to see if that would help.  It ran successfully.  I then checked my /boot/grub directory and the files in there all have modified dates as of today.  I then checked my /etc/grub.d folder and the modified dates for those files is back in October 2013, which is around the first installation date for my ubuntu install.  I am not sure what the gui was trying to update, the files in grub.d or the files in /boot/grub.  I rebooted and grub works fine. 

Does anyone know if the maintainer's version would have updated any of the grub.d files?  Should I have installed the maintainer's version?  If so, I suppose I could just wait until some update prompts me again and I can select the maintainer's version at that time?  Thanks.

---

### Post by TheFu on 2014-07-24
Don't know.  Look at the backups from the day prior if you care. Altered comments? I wouldn't worry about grub, if it works and I didn't customize it.

I only do updates through a terminal and thought the side-by-side uses sdiff ... do you have that tool loaded?  In a GUI, I haven't any idea which tool they call out to.  meld?

---

### Post by grahammechanical on 2014-07-24
An update to Grub might bring in default Grub configuration files to over-write the existing ones.  It is preferable to bring in every thing as new than risk the update being broken because the user has modified one of the scripts.

If we make some modification to a grub configuration file then we get a choice to keep our existing file or allow it to be over-written by the new one. This I think is what is happening here.

You may not remember it but some change must have been made. The process is not intelligent. It is just following the rules it is programmed to follow. This is a request to reset to default.

Regards.

---

