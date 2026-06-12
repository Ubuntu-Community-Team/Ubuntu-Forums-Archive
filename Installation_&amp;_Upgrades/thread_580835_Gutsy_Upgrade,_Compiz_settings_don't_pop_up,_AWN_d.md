---
title: "Gutsy Upgrade, Compiz settings don't pop up, AWN doesn't work anymore"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by feeman_4_life on 2007-10-19
I just upgraded to Gutsy Gibbon!  GUI XORG! YAY!!  

I did it via the alternate CD.  However, my compiz from Feisty and AWN, don't work anymore.  I can load the preferences for AWN, but the dock doesn't appear.  I can't access the Compiz Settings, so I can't use it at all.  Emerald got uninstalled for some reason.  

Is this normal?  Has anybody seen this?

---

### Post by Harmshi on 2007-10-19
same thing happened to me. I installed using the update manager.
Comepletely lost AWN. Compiz seems to work, but i can't access the settings.

How do I install AWN again in Gutsy?

---

### Post by lordgreg on 2007-10-19
exactly the same problem here. updated to 7.10. cannot open the compiz settings window. i don't know if you noticed but, the default ubuntu theme is again here with default effects (aka. wobbling windows), but that's all. 

ps: anyone has two printing options in System > Administration? 

hope anyone knows the solution on getting compiz back to work as usual.

thank you

---

### Post by quoick on 2007-10-19
You can get the compiz settings back by typing

> sudo apt-get install compizconfig-settings-manager

You can then modify everything from **System - Preferences - Advanced Desktop Effects Settings** and it is the same as before the upgrade

AWN seems a little broken at the moment and I can't get it working. I would give it a couple of days before a stable repository is created for it.

---

### Post by lordgreg on 2007-10-19
hi quoick. justr tried that. first it said i allready have the latest version, so i removed whole compiz, reinstalled, then also added compizconfig-setting-manager. it does show in preferences, but when i click on it, nothing happens ://

---

### Post by Dracojk on 2007-10-19
I get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-setting-manager


When I try to apt-get the settings manager.  Being the linux nub I am, I don't have a clue how to tell the command to look in the right place for the file. :confused:

---

### Post by mats-a on 2007-10-19
I have the same problem

---

### Post by hamster_billy on 2007-10-19
I also have the same problem. I expected problems - it took me a week to get Compiz working after upgrading to Feisty, and I imagined it would be similar this time. Life would be so much easier if you were given the option '[Do/Do not] screw up Compiz on upgrade'. 

I did have the additional problem that the default setting after the upgrade (Preference > Appearance > Visual Effects > Normal) wouldn't run gnome-terminal - it flashed up then disappeared - so I had to find my way through to switching this to None before I could do anything at all.

Apart from this I'm fairly happy so far. gDesklets is the only other thing I've found which fails. I'm /very/ happy to have the Bluetooth stuff built in, and Pidgin working properly.

---

### Post by hamster_billy on 2007-10-19
I just removed compizconfig-settings-manager, then did an apt-get autoremove, then reinstalled compizconfig-setting-manager. It all now seems to work as it ought to. Except that in the fancy Visual Effects dialogue Normal is still selected rather than Custom, but I can live with that! That was /far/ less painful than last time. I hope it turns out to be this simple for everyone else.

---

### Post by quoick on 2007-10-19
> **lordgreg said:**
> hi quoick. justr tried that. first it said i allready have the latest version, so i removed whole compiz, reinstalled, then also added compizconfig-setting-manager. it does show in preferences, but when i click on it, nothing happens ://

Hi

You just needed to copy the line from the post and put it into the terminal. Compiz Setting Manager is just another module you didn't have to reinstall it (I have just done a fresh install of Ubuntu bit and the above worked fine). I would suggest this. Open your software sources in **System-Administration** and make sure that all the Download from the Internet sources have check marks beside them. Open the terminal and type
```
sudo apt-get remove compiz-settings-manager
```

```
sudo apt-get autoremove
```

Then go to **System-Preferences-Appearance-Visual Effects** and choose **Extra**

If it starts to download compiz then hopefully all is good (or likewise you get wobbly window automagically). Then in the terminal type (or actually just copy from below and middle mouse click into terminal).
```
sudo apt-get install compiz-settings-manager
```

Hopefully this should fix it.

---

### Post by ahman_ra on 2007-10-19
i just upgraded today, the fix for me was to auto remove compizconfig-settings-manager then add it back as mentioned above.  Now I can readd all my compiz lovin'

---

### Post by feeman_4_life on 2007-10-19
cool!  thanks for the help guys!

I will definitely try it.  What about for AWN and Emerald though?

Same general steps?

Furthermore, what does "autoremove" do anyway?

---

### Post by andsegu on 2007-10-20
Thanks dude!! It did work for me :)

---

### Post by feeman_4_life on 2007-10-20
Those instructions didn't work for me.......

oh well

I'll just format and install gutsy.  I really wish the upgrade can go with no flaws.

---

