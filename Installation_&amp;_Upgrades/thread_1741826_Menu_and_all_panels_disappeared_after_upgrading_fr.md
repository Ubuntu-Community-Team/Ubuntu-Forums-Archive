---
title: "Menu and all panels disappeared after upgrading from Ubuntu 10.10 to 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Uewd on 2011-04-28
Today I upgraded to the final release of Ubuntu 11.04. The upgrade completed successfully, but after restarting, the menu and all panels disappeared, even window borders. I tried to restart the PC, but same problem. Please help as fast as possible.

Any helpful reply will be appreciated.
Thanks.
Uewd.

---

### Post by Ethyrdude on 2011-04-28
Yep happened to me too, had to create a launcher for firefox, its really no big emergency, I am sure there is a simple fix so will be posting here as it happens

---

### Post by Ethyrdude on 2011-04-28
I cheated, before the upgrade i had kde and kdm installed so on login I picked Classic Ubuntu, viola!  My panels are back

---

### Post by Uewd on 2011-04-28
I got a **temporary** solution: When Linux boots (before account login), choose **Ubuntu Classic**. Then go to **System>Preferences>Startup Applications**. Click on **Add** and give it this name: **Gnome Panel**
and this Command: **gnome-panel**
After doing these steps, gnome panel will start on start up. How can I get the new Ubuntu 11.04 interface?

---

### Post by Ethyrdude on 2011-04-28
yeah actually i would too, i noticed something in synaptic about gnome-desktop and gnome-desktop universal, but i have no clue, so am hanging in there for an answer

---

### Post by aquamaster on 2011-04-28
same problem here, just upgraded and all my panels are gone, i cant see unity either, i hope that someone finds a solution to this and fast

---

### Post by Ethyrdude on 2011-04-28
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

warning this will destroy functionality of Unity

---

### Post by aquamaster on 2011-04-28
how do we get the new ubuntu interface?

---

### Post by Uewd on 2011-04-28
> **aquamaster said:**
> how do we get the new ubuntu interface?
I wanted to ask exactly the same question :)

---

### Post by Uewd on 2011-04-29
**I found a solution to enable the Unity interface**: 1. If CompizConfig Settings Manager is not installed, install it by running this command in terminal: **sudo aptitude install compizconfig-settings-manager**
2. Open **CompizConfig Settings Manager** by the command **ccsm**
3. **Enable** the **Ubuntu Unity Plugin**.

BUT NOW **I CAN'T SEE ANY WINDOW BORDER**. SEE EXAMPLE:
[http://img217.imageshack.us/f/screenshot1kxq.png/](http://img217.imageshack.us/f/screenshot1kxq.png/)
Please help me to get the window borders back.

---

### Post by Uewd on 2011-04-29
Now I understood that there is no use of the Unity interface. After enabling it, I found plenty of bugs in it. So I may stop using the Unity interface if it continued to do that.

---

### Post by Uewd on 2011-04-29
[URL="http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176"][SIZE=4]Ubuntu Unity interface is full of bugs[/SIZE].
[/URL]

---

### Post by Uewd on 2011-04-29
SOLUTION
Here is what to do:
1. I recommend that you don't use the new Ubuntu Unity interface because lots of bugs so we will wait until the next release in October 2011.
2. Get the classic interface back in Ubuntu 11.04 (recommended): [http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176](http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176)

3. @Canonical: I am disappointed :( . Please Fix the problems with your Unity interface.

---

### Post by aquamaster on 2011-04-29
did that now everything is fixed, but i dont have windows borders either :(

i dont have problems with my unity interface

---

### Post by Uewd on 2011-04-29
> **aquamaster said:**
> did that now everything is fixed, but i dont have windows borders either :(

i dont have problems with my unity interface
Open **CompizConfig Settings Manager** and check the option **Window Decoration** to enable Window Borders.

If you can't resize the windows, then check the option **Resize Window**.

If you can't move the windows, then check the option **Move Window**.

**NOTE:**
After doing these steps, Everything is fine except that it crashes a lot after checking or unchecking options in [B]CompizConfig Settings Manager. If the above panel crashed, enter this command in terminal so that you can logout and login again to fix this problem:
gnome-session-save --kill

[/B]The above command opens the dialog that asks you if you want to log out or to switch user.

Hope this helps.
Explanation was a bit confusing. Sorry.
Thanks.
Uewd.

---

### Post by aquamaster on 2011-04-29
ughh cant do it because if i enable windows decorations then unity disappers

---

### Post by makro on 2011-04-29
Try to rename/delete compiz* folder(s) under ~/.config and restart session

---

### Post by sieve on 2011-04-29
Based on what I had seen in the leadup to launch, I knew things would be different, but assumed it was largely minor and cosmetic.  I had no idea it would be such a big change.  I have a hard time finding things now or having the GUI do what I want.

I like the idea that they keep the OS current and am not opposed to change, but this has been a frustrating experience so far.

I might try it for a while as is to see if I warm up to it, but it's good to know that there are options to go back to the status quo.

---

### Post by Uewd on 2011-04-30
> **aquamaster said:**
> ughh cant do it because if i enable windows decorations then unity disappers
Strange...
If I enabled Window Decoration Unity will just crash, which can be fixed by a logout.

---

### Post by MugOTea on 2011-04-30
To be fair, on my HP/Compaq6720s (crappy laptop) the upgrade went well, and only took about 3hr.

When it finally restarted after the upgrade all my screenlets and system tray icons (skype, dropbox) had gone, and I thought WTF??

I've had a day since then, reading up on unity and the other problems the people have experienced so far with Unity / 11.04. For the most part I can see, and even quite like where they're going with unity!

I've found fixes in these forums for the system tray icons, they can be reinstated, and I also found out that the screenlets that I used before the upgrade were still there and I just had to re launch the screenlets server application and add them to my desktop again.

The main problem for me is the window decorations and the fact that the unity top bar has a habit of crashing when any compiz settings are changed.

I think I could get used to the dashboard instead of the applications menu - as users perhaps we just need to push on through the bugs and HOPE CANONICAL ARE SEEING OUR CRIES FOR WINDOW DECORATIONS!!! lol

---

### Post by Uewd on 2011-05-01
> **MugOTea said:**
> To be fair, on my HP/Compaq6720s (crappy laptop) the upgrade went well, and only took about 3hr.

When it finally restarted after the upgrade all my screenlets and system tray icons (skype, dropbox) had gone, and I thought WTF??

I've had a day since then, reading up on unity and the other problems the people have experienced so far with Unity / 11.04. For the most part I can see, and even quite like where they're going with unity!

I've found fixes in these forums for the system tray icons, they can be reinstated, and I also found out that the screenlets that I used before the upgrade were still there and I just had to re launch the screenlets server application and add them to my desktop again.

The main problem for me is the window decorations and the fact that the unity top bar has a habit of crashing when any compiz settings are changed.

I think I could get used to the dashboard instead of the applications menu - as users perhaps we just need to push on through the bugs and HOPE CANONICAL ARE SEEING OUR CRIES FOR WINDOW DECORATIONS!!! lol
Exactly the same problem I am facing. Canonical must find a fix for the Unity interface issues.

---

### Post by Uewd on 2011-05-01
See a picture of the crashed panel in Ubuntu 11.04:

---

### Post by Tanker Bob on 2011-05-01
> **Uewd said:**
> See a picture of the crashed panel in Ubuntu 11.04:

Same problem here. Not only does the top panel disappear, but the Applications and Files & Folders applets disappear from the Unity launcher. I can duplicate this at will by changing the Trail Focus setting in CCSM amongst others. Logging out and back in resets everything.

I've also noticed that Compiz and Unity launcher settings don't always stick across reboots. This includes icon sizes and transparency in the Unity launcher, but also for the general desktop.

Unity doesn't seem like it's ready for prime time yet. It's way too easy to crash by doing ordinary tasks. Casual users will likely be easily discouraged.

---

### Post by johnshore on 2011-05-01
> **Uewd said:**
> SOLUTION
Here is what to do:
1. I recommend that you don't use the new Ubuntu Unity interface because lots of bugs so we will wait until the next release in October 2011.
2. Get the classic interface back in Ubuntu 11.04 (recommended): [http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176](http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176)

3. @Canonical: I am disappointed :( . Please Fix the problems with your Unity interface.
Thank you so much! I now have the desktop I know and understand with all the Natty updates

John

---

### Post by lcason on 2011-05-01
:confused:

I've always had positive results with Ubuntu upgrades, so I didn't hesitate to upgrade to 11.04. Wasn't too happy with the initial experience on the new Unity interface, but decided to give it a few days before making final judgement. I hate pop-up tool bars, so I figured out how to set the display state to static. But when I sat down to pay bills just now, I noticed that the Compiz Fusion screen manager doesn't recalculate the remaining screen size. So CTRL+ALT+4 for a left half-screen overlaps with CTRL+ALT+6 for a right half-screen. Yuck! 

So, I figured that there must be some simple way out of here, to put me back to a more conventional UI. Hmmm, here's something. "Disable Unity Plug-in". Sounds reasonable. Take away the plug-in, and things should go back to what they were before the plug-in twisted them up.  #*$%&$!!!!  Nope!  What you get is a UI with **NO UI**!!  Nice going guys.  Tried a restart just to see if something would check to see that there's a blank desktop and help me out. But no help.

I just tried the gnome3 solution suggested earlier in this thread. Disabling Unity is exactly what I wanted to do. Unfortunately, now I cannot login to Gnome. Regardless of the session type I select, I get the same error message:

> Could not update ICEauthority /home/lee/.ICEauthority

So, I think I'll try the ZDnet howto next before I wipe and reload 10.10, which was working just fine. Drat. Scratch that--it's not a solution for me.

Reinstalling 10.10 now, so don't waste time with a solution on my account. Thanks.

---

### Post by thomasmilo on 2011-05-02
Ethyrdude,
Thank you for the tip. I followed your procedure
QUOTE
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
END QUOTE
This seemed to go okay.  But now after rebooting, after typing my password to log into gdm, I get the following message:
QUOTE
Could not update ICEauthority file /home/tomsomers/.ICEauthority"
END QUOTE
Can you help me understand what to do now, since I cannot log in at all?  
Thank you for any help.

---

### Post by Uewd on 2011-05-02
> **johnshore said:**
> Thank you so much! I now have the desktop I know and understand with all the Natty updates

John
You are welcome!

---

### Post by Uewd on 2011-05-02
> **thomasmilo said:**
> Ethyrdude,
Thank you for the tip. I followed your procedure
QUOTE
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
END QUOTE
This seemed to go okay.  But now after rebooting, after typing my password to log into gdm, I get the following message:
QUOTE
Could not update ICEauthority file /home/tomsomers/.ICEauthority"
END QUOTE
Can you help me understand what to do now, since I cannot log in at all?  
Thank you for any help.
This topic may help you: [http://ubuntuforums.org/showthread.php?t=949750&page=2]("http://ubuntuforums.org/showthread.php?t=949750")

---

### Post by Uewd on 2011-05-03
**[SIZE=3]Note[/SIZE]:**
[B]
If you want to get the Unity interface Working properly, then you need a fresh install of Ubuntu 11.04.[/B]

**If you want to get the classic Ubuntu look,** then _*[**click here.**]("http://www.zdnet.com/blog/hardware/how-to-disable-unity-and-go-back-to-the-classic-interface-in-ubuntu-1104-natty-narwhal/12176")*_

---

### Post by Uewd on 2011-05-04
I think **I am going to do a fresh install of Ubuntu 11.04.**

---

### Post by stanislav.chekalin on 2011-05-04
> **Uewd said:**
> I think **I am going to do a fresh install of Ubuntu 11.04.**
I have reinstalled Ubuntu completely the day before yesterday and still have the same problems. 

I have noticed that the window borders and panel disappear more often when I am using IntelliJ IDEA. Maybe there is a problem with Java applications.  

Window borders and panel also disappear when I am changing settings in compiz config.

---

### Post by Uewd on 2011-05-05
Reinstalling Ubuntu 11.04 Solved the problem. Thanks a lot for all who replied. :) 
Hope this solution helps.

---

### Post by Uewd on 2011-05-05
> **stanislav.chekalin said:**
> I have reinstalled Ubuntu completely the day before yesterday and still have the same problems. 

I have noticed that the window borders and panel disappear more often when I am using IntelliJ IDEA. Maybe there is a problem with Java applications.  

Window borders and panel also disappear when I am changing settings in compiz config.

Strange. I deleted all Linux partitions and recreated them. After reinstalling I faced no problem :)

---

