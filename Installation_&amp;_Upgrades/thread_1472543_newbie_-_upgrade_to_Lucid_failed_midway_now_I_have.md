---
title: "newbie - upgrade to Lucid failed midway now I have probs"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by aundapenner on 2010-05-04
While I am a ubuntu newbie, I consider myself comfortable with computers in general. But, with ubuntu, I think I need some hand holding. please?
 
I am using an asus eee and had previously installed the netbook version. 
 
I ran all the updates today for the previous version then ran the upgrade to lucid. It said it would take a while so I walked away. I came back to a black screen with no response (netbook was plugged in during install). I hit a few buttons, again no response. I reboot, thinking maybe it got hung up. 
 
Now I can't do anything. First I kept getting an error indicating the startup file couldn't be found. So I tried to use the netbook remix USB files, but it wouldn't recognize the usb.
 
So I changed the settings for the system to go first to the usb. But then it couldn't find any system. *(duh!) to run off of. 
 
I have searched for help but can't seem to find something either dumbed down enough for me to understand or with the problems I am having.
 
I just rebooted my netbook to write down the error messages I am getting and the grub loads okay. Then I get a usb:id307: unable to access message.
 
And now, finally I get the chance to login with my login and password (which I had not gotten previously).
 
So I log in and it tells me welcome to ubuntu! but I have no clue what to do from here! :confused:
 
Can someone hold my hand through this? (oh yeah, one more thing - as brilliant as I am, I did not back up my hard drive)
 
Also - I only run ubuntu, no partitions.

---

### Post by Cynical on 2010-05-04
Well now that you are back into your system, backup whatever you need and run the command ```
update-manager -d
``` in a terminal, or you can go to System > Administration > Update Manager, then check for updates and follow the instructions after it asks if you want to upgrade.

---

### Post by aundapenner on 2010-05-04
Thanks Cynical for the response.
 
So how do I get back into my system?  It gives me [EMAIL="alice@alice-laptop:~$"]alice@alice-laptop:~$[/EMAIL]
 
from there I can type various commands, right?
 
I tried typing in update-manager -d and it gave me the following:
 
GtkWarnin: could not open display warnings.warn(str(e), _gtk.Warning) 
 
Traceback (most recent call last): File "/usr/bin/update-manager", line 41, in <module>gtk.init_check()
 
RuntimError: could not open display
 
Then gives me the initial alice-laptop thing again.  :(

---

