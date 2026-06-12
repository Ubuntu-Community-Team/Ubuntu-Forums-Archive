---
title: "Unity/Compiz broken on 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Moyamo on 2012-04-27
I recently upgraded to Ubuntu 12.04 with some difficulty.

What happened was I left my laptop on through out the night and in the morning I wanted to see the progress of the upgrade. The screen was black and when I shifted the mouse the screen would momentarily flash my background image.

I assumed the update was complete and thought the problem would go away when I rebooted. So I turned of the system (via TTY1) and when I booted it went straight to recovery.

I realized that the update had not completed and ran.

```

apt-get -f install
apt-get dist-upgrade

```

The update continued and everything was fine. I then rebooted the computer and to my pleasure saw the login manager. But when I logged in I never got the Unity shell. Instead I got a purple screen and a dialog stating that compiz could not load.

I am currently using awesome wm which seems to be working properly. How can I fix unity?

Any help will be appreciated.
Thanks in advanced.

---

### Post by kc1di on 2012-04-27
What Video Card are you using?

if It' Nvidia there is a bug that prevents the Nvidia Current and maybe others from working with Compiz.  It's been reported and should be being worked on.  

If that is your case log into a 2d session (You can choose 2d at the loging prompt by clicking of the little ubuntu logo in the upper right of the login box) that should work and go to Additional Drivers tool and remove Nvidia Propriety Drivers.  Then it should work for you in 3d.  

by the way if you clicked install 3rd party software at the install Nvidia Propritory drives will be install and active. 

Good Luck,
D :)

---

### Post by Moyamo on 2012-04-27
I have an ATI card. Should I install fglrx?

---

### Post by mastablasta on 2012-04-27
> **Moyamo said:**
> I have an ATI card. Should I install fglrx?

which ATI? if old one then no, if you have new(er) AMD chips then yes.

---

### Post by JedV on 2012-04-27
> **kc1di said:**
> What Video Card are you using?

if It' Nvidia there is a bug that prevents the Nvidia Current and maybe others from working with Compiz.  It's been reported and should be being worked on.  

If that is your case log into a 2d session (You can choose 2d at the loging prompt by clicking of the little ubuntu logo in the upper right of the login box) that should work and go to Additional Drivers tool and remove Nvidia Propriety Drivers.  Then it should work for you in 3d.  

by the way if you clicked install 3rd party software at the install Nvidia Propritory drives will be install and active. 

Good Luck,
D :)

Thanks for the tip.  I thought that I'd be in the market for a new video card :)  You made my day kc1di!!!!!!!!

---

### Post by Moyamo on 2012-04-27
I think I'll install fglrx and see what happens.

---

### Post by SevenThunders on 2012-04-27
> **kc1di said:**
> What Video Card are you using?

if It' Nvidia there is a bug that prevents the Nvidia Current and maybe others from working with Compiz.  It's been reported and should be being worked on.  

If that is your case log into a 2d session (You can choose 2d at the loging prompt by clicking of the little ubuntu logo in the upper right of the login box) that should work and go to Additional Drivers tool and remove Nvidia Propriety Drivers.  Then it should work for you in 3d.  

by the way if you clicked install 3rd party software at the install Nvidia Propritory drives will be install and active. 

Good Luck,
D :)

Additional drivers tool?  I have no idea what that is.  I have the same problem, no compiz and no unity.I am logged in to a 2D manager (gnome) and am using cairo-dock.  

In ubuntu's software manager I see that I have Nvidia binary X.Org driver.  I presume this is Nvidia's proprietary driver?  Are you saying I have to uninstall this?  What about support for CUDA?

This is seriously messed up.  I guess I should have realized 12.04 is still in defacto beta status.  As an added bonus Ubuntu software center keeps crashing.

---

### Post by Moyamo on 2012-04-28
After installing fglrx everything works fine. I will mark this thread as solved. I suggest you  create a new thread for the nvidia cards.

---

