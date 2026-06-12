---
title: "Difficulty installing Ubuntu Desktop because of screen resolution"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by campem on 2007-03-27
Hey everyone,

I just booted up the live CD and double clicked the install icon. The installer launches fine but my screen resolution is set to 640*480 which means that the installer window is biger than the screen which means that the ok / cancel buttons aren't showing on screen and I can't resize the window... Whilw I can manage to use TAB and guess which button I'm at it makes for a very frustrating install. What can I do to get around the problem.

Thanks

---

### Post by kellemes on 2007-03-27
Can't you get to the Gnome resolution-dialog to change the settings?
Or try xrandr from terminal, not sure if installed with LiveCD though..

---

### Post by campem on 2007-03-27
> **kellemes said:**
> Can't you get to the Gnome resolution-dialog to change the settings?
Or try xrandr from terminal, not sure if installed with LiveCD though..
If you mean System > Preferences > Screen Resolution I can run it but unfortunately I only have 640*480 as a option. xrandr gives me the same results. I downloaded the alternate version and will try with that.

---

### Post by NJC on 2007-03-27
campem;

I had the exact same problem and it was VERY hard to install trying to calculate how many times I needed to press Tab to get to the next screen. I have the Matrox G200 chip. 

Running the LiveCD in Safe Graphics mode enabled the proper resolution. Let me know if this helps.

---

### Post by Pale_Buddha on 2007-03-27
OK, this is admittedly a sloppy work-around...

I had the same problem so I used to right-click on each install page and choose "move".  Then, I slid each page up so I could see the Next button

Not pretty but it works
PB

---

### Post by campem on 2007-03-27
Thanks NJC, Pale_Buddha and everyone else,

it's nice to know that I'm not alone with these problems, though I find it very strange. BTW I did try other modes and still it didn't work. I'm now using the alternate version which as a nice text mode which suits me just fine!

---

### Post by NJC on 2007-03-27
campem;

I'm guessing Ubuntu hasn't recognized your video card/chip. You may need to edit xorg.conf (backup file first) and run xserver-xorg dpkg-reconfigure in a terminal. 

There's lots of info regarding xorg.conf editing ... check out the official Ubuntu docs:

[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28monitor%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28monitor%29)

---

### Post by Neobuntu on 2007-03-27
Opps, duplicate. Please see below.

---

### Post by Neobuntu on 2007-03-27
That's right. There may even be a temporary setting glitch with the upgrade of new xorg packages. 

Indeed,  just ...```
sudo dpkg-reconfigure xserver-xorg
``` and you don't even have to edit the configuration text file.

Just hit enter and select most defaults (quickly as a time saver).

Now this may seem a little geeky to the newbie (and should be improved), it's really quite simple.

--------General Directions (read)--------------

Be sure (at first) you select the right video card because it will default to nv instead of nvidia (for example) if you have (direct) 3D already installed installed(which *ubuntu does nicely).

Select many(about Ten or more) defaults (hit tab to say "OK" on some) until you get to the monitor section. This goes fast the Second time through.

If you want your login screen to look right (correct resolution), un-star(unselect) any higher resolutions, than the one you want and your display can do best(in your opinion).

Now, normally select the "Medium" method and make your best choice. Restart and if all is well (and your refresh rate is higher than 60Hz on CRT tube monitors to stop flicker.) then you are done.

(This represents a minimal change strategy and thereby reduces the very large number of possibilities that will not work correctly and/or optimally. Do not play around unless you have a lot of time. You will find this "xorg.config" file backed up automatically but you can also just arrow up and reconfigure your "X" again, if needed.)

If you then have a problem, your particular display may not be recognized (Yet, and you may report this) and this is increasingly rare. Take heart, there exists a simple solution, however. Simple "Google" search for your particular display and model (or notebook) for it's Horizontal and Vertical specs and simply enter them using the "Advance" method instead of the "Medium" method; in the above process.

Example of found (Googled) info (DON"T USE JUST ANY VALUE IT MAY HARM YOUR DISPLAY) :

```
Horizontal 30-95 (KHz), Vertical is 50-160 (Hz)
```

--------End General Directions----------------------------------------------------------------------------------------------

You can (of course) edit the "xorg.conf" file but then, typos and file backup become issues.

You may want to > sudo aptitude install mc so that you can navigate and edit files (restore backups) more easily without  graphics (X working).

Jot down the following commands if you are not familiar with them then
Hold CTRL+ALT and press F1, login and...

 Then...```
sudo /etc/init.d/gdm stop
```  OR ```
sudo /etc/init.d/kdm stop
```  AND ```
sudo dpkg-reconfigure xserver-xorg
``` Follow above directions and hit your up arrow key to:```
sudo /etc/init.d/gdm start OR sudo /etc/initi.d/kdm start
```

...works for me. I have even setup extreamly high res, brand new Dell notebooks using this method and following Goggled specs and tips relevant to such model. Someone is always blazing a path; even on the new (atypical) devices.

Hope this help you.

P.S. Remember, never buy devices or computers including devices where their chip-sets are made to only work with Windows. A simple Google search BEFORE you buy will reveal the competitive hardware. Most manufactures are seeking new openess with open software at this time. Those that do not are cheating and will be remembered.

---

### Post by Neobuntu on 2007-03-27
Get er' done!

---

