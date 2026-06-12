---
title: "upgrade to Narwahl not successful"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Chuck_N on 2011-05-13
after upgrade to Narwahl, my Grub menu now offers 2.6.38.8 at the top, which gets me only a series of error messages, and  2.6.32.21 further down which run, gives me an empty desktop, no history or Bookmarks, but will get me to the web and to installed programs and seems to work okay.

The error messages under 2.6.38.8 basically says
  Init: udev trigger main process terminated with status 1 UDEVmonitor main process killed by Term signal.
  init: Plymouth-splash main process (176) terminated with status 2.

Is it an option somehow to back out of this upgrade and return to my former operating system (I forget if it was Lynx or Meerkat?)   If not, what is a recommend pursuit? 
-Chuck

---

### Post by blauendonau on 2011-05-13
Sorry, once you've upgraded it's irreversible. The only way to get back to 10.04 or 10.10 is to clean-reinstall it over Natty. Can't help with you with the boot problem, but I've had serious problems with 11.04 too that made it unusable and forced me to go back to Lucid. My only suggestion is to stay away from Natty and stick with the LTS until Natty matures or 11.10 comes out (I believe Oneric will be an improvement).

---

### Post by Chuck_N on 2011-05-13
> **blauendonau said:**
> Sorry, once you've upgraded it's irreversible. The only way to get back to 10.04 or 10.10 is to clean-reinstall it over Natty. Can't help with you with the boot problem, but I've had serious problems with 11.04 too that made it unusable and forced me to go back to Lucid. My only suggestion is to stay away from Natty and stick with the LTS until Natty matures or 11.10 comes out (I believe Oneric will be an improvement).

Why would my desktop come up empty on the upgrade.  Is there a way to retrieve the folders I had there?

---

### Post by blauendonau on 2011-05-13
Did you actually save files to the desktop itself, or are you talking about launchers (shortcuts) to programs elsewhere? If you click on the Ubuntu logo in the upper-left corner of the screen you should be able to access installed programs through the menu.

---

### Post by Chuck_N on 2011-05-13
> **blauendonau said:**
> Did you actually save files to the desktop itself, or are you talking about launchers (shortcuts) to programs elsewhere? If you click on the Ubuntu logo in the upper-left corner of the screen you should be able to access installed programs through the menu.

I had shortcuts and I had folders of pictures. Everything is gone now

---

### Post by confused57 on 2011-05-13
You should be able to boot an Ubuntu live cd, your / &/or /home partition should be located under places.  Click on the "Show Hidden Files"(home/Desktop), copy & paste all your home files/folders to a usb drive or another partition, reinstall Maverick or install Natty, then copy all your files/folders into your new home.

Added:  After copying all your home files/folders to a backup media, instead of reinstalling just yet, you could open a terminal & run:
```
sudo dpkg --configure -a
sudo apt-get install -f
```
I don't know if this might repair the upgrade or not.

---

### Post by Chuck_N on 2011-05-15
oh well, if I cursor-down on GRUB, I can select the Lucid option 10.04 which seems stable.
That's okay. I can retrieve my picture folders from external backups.

Only real problem  I have is one I had b4. Desktop icons are large and I can't change  System/Preferences/Appearance/Visual effects. It searches for drivers and then says  Cannot be Enabled.   I think this has to do with my lack of video  card and on-board graphics in this old desktop.  I blow up, too, if I attempt to use the GL screensavers.

---

### Post by Chuck_N on 2011-05-15
> **confused57 said:**
> 

Added:  After copying all your home files/folders to a backup media, instead of reinstalling just yet, you could open a terminal & run:
```
sudo dpkg --configure -a
sudo apt-get install -f
```I don't know if this might repair the upgrade or not.

okay; not sure what it did, but it ran

---

### Post by dino99 on 2011-05-15
regenerate the desktop, run either:

metacity --replace &
gnome-panel --replace &

---

### Post by Chuck_N on 2011-05-15
> **dino99 said:**
> regenerate the desktop, run either:

metacity --replace &
gnome-panel --replace &

tried 'em both
shouldn't have
they did nothing for my desktop;
but now I have a graphics problem again, which has not surfaced in quite a while
since I eliminated the GL screensaver.

Now again at random times the screen goes black and everything is froze
only option is to powerdown and restart.

---

### Post by MAFoElffen on 2011-05-15
> **Chuck_N said:**
> tried 'em both
shouldn't have
they did nothing for my desktop;
but now I have a graphics problem again, which has not surfaced in quite a while
since I eliminated the GL screensaver.

Now again at random times the screen goes black and everything is froze
only option is to powerdown and restart.
ROTFLMAO!!!  

WAIT!?!  If you are booting Norwhal into Unity for the first time after an upgrade from an earlier realease, you are NOT going to see any shortcuts on the desktop that you saved previously... It uses a diffrent desktop and menuing sceme... They are there and you can re-add them.

However, if at the GDM login > after you selected your userid and looked at the lower bar > selected Ubuntu classic... Then you would get the old familiar gnome desktop and all those old saved shortcuts should still be there setup as before.

If you start reinstalling and replacing config files, those are going to get replaced or overwritten.

---

### Post by Chuck_N on 2011-05-15
> **MAFoElffen said:**
> 
ROTFLMAO!!!  



me thinketh thou art too easily amused.

I'm tired of messing with this.
Just wish I hadn't upgraded.
To heck with Narwahl; 
I'll keep choosing  Lucid  off the GRUB menu;
at least it's stable.

I can reload the pics from backup and proceed from here......

---

### Post by quickk on 2011-05-18
The desktop is just like any other folder, and you should be able to access the files through the file manager Nautilus.  I believe that the new Ubuntu does not show the contents of the desktop folder on the desktop (if that makes any sense!).   It is also possible that you have installed Ubuntu 11.04 with a new user name, so you won't see your old files.

To get your old files, go to the /home folder.   You should then see a folder for each user.   Inside each of these folders there is a Desktop folder.   One of them should contain your old files.  

I hope this helps!

---

### Post by Chuck_N on 2011-05-19
> **quickk said:**
> The desktop is just like any other folder, and you should be able to access the files through the file manager Nautilus. I believe that the new Ubuntu does not show the contents of the desktop folder on the desktop (if that makes any sense!). It is also possible that you have installed Ubuntu 11.04 with a new user name, so you won't see your old files.
 
To get your old files, go to the /home folder. You should then see a folder for each user. Inside each of these folders there is a Desktop folder. One of them should contain your old files. 
 
I hope this helps!
 
Okay. I will check this out when I get back home.
Thanks.
-Chuck

---

