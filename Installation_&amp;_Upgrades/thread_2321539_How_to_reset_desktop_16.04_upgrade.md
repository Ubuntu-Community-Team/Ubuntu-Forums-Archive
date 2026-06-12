---
title: "How to reset desktop? 16.04 upgrade?"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by davehenson on 2016-04-22
I just upgraded from 15.10 to 16.04 and now when I log into the unity desktop, I only see the icons that I had on my desktop before. The "windows" key does not work and all I can do is right click, change wallpaper and then drop to settings.  I cannot even power off from the desktop. Kill the power and then log into a guest account and it looks like normal. I did figure out how to get to the command line (ctrl+alt+f1) to get a terminal.  

What to do next?  I'm thinking I should be able to reset the desktop preferences for the user by maybe deleting the desktop config that it loads?  Or maybe reinstall unity altogether?  I dont know.  I do have a backup so I could do a fresh install and then restore my home directory but that seems like a cop out. 

Any tips or should I drop back and do a fresh install?

---

### Post by deadflowr on 2016-04-22
If you can get the right click option on the desktop (to change the wallpaper, et cetra ) you should be able to get a terminal session on the desktop.
try **ctrl + alt + T **while in the desktop.
if a terminal pops up try these commands
```
dconf reset -f /org/compiz/
```
and then 
```
setsid unity
```
The first command resets the configuration to the defaults, and the second reloads unity.


Edit: alternatively, if you cannot get a terminal with the keybindings, when you right click on the desktop,
It should have an option to create a new folder.
Do that.
Then click  to open that new folder and the file manager will open.
In the file manager go to the side panel area and go to the option Computer.
The main window should show a bunch of folders, locate the folder marked usr.
Then in usr locate the folder share.
Then in share locate the folder applications.
In the applications folder, scroll down till you get to Terminal.
double click and it should open a terminal.
fwiw

---

### Post by davehenson on 2016-04-23
thanks deadflowr!  Actually I can't even get a terminal with ctrl+alt+T.  I did drop back to cli with ctrl-alt-f1.  then I tried running the dconf as you suggested but it returned ```
"no command dconf found", did you mean debconf, dtconf, dconf from package dconf-cli
```  I tried ```
apt-get install dconf
``` and it returned ```
package dconf is not available, but is referred to by another package. this may mean that the package is missing , has been obsoleted  or is only available from another source. E: package dconf has no installation candidate.
``` 

hmmm....(scratches head)


I wonder if its possible to force a complete unity reinstall. thinking maybe a large chunk is missing??

---

### Post by deadflowr on 2016-04-23
I'd run
```
sudo apt get update && sudo apt-get install ubuntu-desktop
```
(You can run that from the ctrl+alt+f1/tty1 console)
If it says already the newest version try:
```
sudo apt-get install --reinstall ubuntu-desktop
```
dconf-cli is a dependency for unity, so it not being there is troublesome.
Hopefully an attempt reinstall of the ubuntu-desktop package should glean some light, or possibly (fingers crosses) fix it.

If any errors, even though you can not post them (obviously) try as best you can to give us the gist, please.

Hope it helps

---

### Post by davehenson on 2016-04-23
thanks deadflowr. that helped although it didn't fix it. :(  I ran the first command you suggested and it stated as you guessed, that it was at the latest version. So I then ran the second and it ran fine with no errors. I then rebooted just to make sure everything was restarted and I get the same result when I log into unity. there must be deeper issues as you mentioned b/c when I do log into the desktop and bring up the change wallpaper window (by right click on desktop), I can go deeper in the window to the settings but I cannot move the window at all and see no buttons to even close the window. I had used the ui tweak tools on my 15.10 so I wonder if those tools really mucked it up. I can reinstall, I just hate to give up. :)

---

### Post by davehenson on 2016-04-23
Deadflowr, one good thing though is I can now run the dconf command you mentioned in your first reply.  I have to run from a tty1 console. run it and it returns "error: Cannot autolatch D-bus without x11 $Display".  Then it gives me direction on proper usage.

---

### Post by linsms on 2016-04-23
I've exactly the same problem, but none of the pourposed solutions worked. I've installed mate to be able to work, but I would prefer unity. Any ideas to make it work?
Thanks

---

### Post by koma77 on 2016-04-23
For the record: this seems to be the exact same error I got after upgrading to 16.04! I created a thread about this yesterday.

---

### Post by linsms on 2016-04-23
I've read it. Do you have a solution?

---

### Post by koma77 on 2016-04-23
No, not yet. I will try to debug it somehow and/or report a bug to Canonical since I believe this has to do with unity.
Do you also have an NVidia graphics card? And does your guest account work as well?

---

### Post by koma77 on 2016-04-23
Ok, I think I got it working alright. Funnily enough I'm quite sure I did try this several times yesterday, but this is what I did from a terminal windows inside the broken unity environment (right click, select terminal):

sudo apt-get install --reinstall ubuntu-desktop unity
dconf reset -f /org/compiz
dconf reset -f /org/compiz/

(Note that I did not use sudo in the last two commands)

---

### Post by davehenson on 2016-04-23
NOt sure on the graphic cardin my Lenovo notebook but yes, my guest account works fine. It just erases after I log out of it. :D

---

### Post by koma77 on 2016-04-23
It sounds like the same issue I had for sure...

---

### Post by linsms on 2016-04-23
> **koma77 said:**
> Ok, I think I got it working alright. Funnily enough I'm quite sure I did try this several times yesterday, but this is what I did from a terminal windows inside the broken unity environment (right click, select terminal):

sudo apt-get install --reinstall ubuntu-desktop unity
dconf reset -f /org/compiz
dconf reset -f /org/compiz/

(Note that I did not use sudo in the last two commands)

It works after reboot. I've unity again. Thanks a lot!

---

