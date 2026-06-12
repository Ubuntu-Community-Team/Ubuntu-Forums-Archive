---
title: "upgrading 8.10 to 9.04  nvidia 180.29 to 180.44 &quot;cannot upgrade &quot;"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by stoneybridge on 2009-04-06
hi i tried upgrading using the update manager, everything went well untill it tried to update the nvidia 180.29 driver (i think) it came up with loads of errors and said that upgrading wasn't possible, i had updated the driver myself a while ago, mostly through trail and error and am guessing i didn't do it correctly,

now when i turn on i just get a command prompt, typing startx
throws up this... 

[[IMG]http://img217.imageshack.us/img217/1971/image168.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image168.jpg)

as a know next to nothing about linux this is highly confusing, sum config file is messed up?
i tried uninstalling 180.29 then reinstalling it this throws up this...

[[IMG]http://img217.imageshack.us/img217/2585/image171.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image171.jpg)
 
pressing ok gets this..

[[IMG]http://img217.imageshack.us/img217/1747/image172k.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image172k.jpg)

ok again this...

[[IMG]http://img217.imageshack.us/img217/6623/image173.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image173.jpg)

then it goes back to the command line, typing startx gets this...

[[IMG]http://img217.imageshack.us/img217/554/image174.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image174.jpg)

i know i'm doing it all wrong, but wanted to give the error messages, any help would be greatly appreciated

---

### Post by SketchyClown on 2009-04-06
Manual installation is so much easier, and less problems. Here's how I do it.

First: **Download** the drivers from NVIDIA.

Then make sure the driver file is executable. **Right-click >Properties >Permissions >Allow Executing**.

Then reboot into the **recovery console **mode. When GRUB loads, hit **ESC** and select the recovery console. Don't attempt to install them through the Terminal while the desktop is loaded or they will not install properly. Do it from recovery.

When the menu pops up, select **netroot.**

Navigate to where the driver file is. Example:$**cd /home/yourusername/Desktop**

Run the file.  $**./NVIDIA*.run**

Follow the prompts to install, it may ask you to uninstall the current driver, let it do so.

Let it set up your xorg.conf and you should be good to go.

Reboot.

---

### Post by stoneybridge on 2009-04-06
cheers for that, my problem is upgrading 8.10 to 9.04 has somehow screwed up my ubuntu instalation, possibly relating to a an updated nvidia driver conflict?

i carn't now boot into ubuntu, it just goes to the command line, the error message is above and what nvidia has to say about the config files, that is just for imformation i didn't even know a new driver was out. cheers for the reply though;)

---

### Post by Twitch6000 on 2009-04-06
okay just try this when you boot up, type startx


It will either start in a low res mode or give you a detail of the problem.

If you get the detail thing please post them.

If you go into low res just reinstall the nvidia driver.

---

### Post by cariboo on 2009-04-06
You're probably having problems because the upgrade did not complete. Start up in recovery mode and at the menu select, drop to root prompt with networking. At the prompt type:

```
apt-get install -f
```

then

```
apt-get update && apt-get dist-upgrade
```

Once the updates are completely finished, then install the restricted drivers. Jaunty is still in beta, so be prepared to run into more problems. It is not recommended that people that have little experience using Linux use a release until after it's final release.

Jim

---

### Post by stoneybridge on 2009-04-07
i,ve sorted it by going to the repair console and clicking on  repair files or summat, suppose it was a bit obvious shouldn't start panicing if somthing goes wrong!
 jaunty's looking great noticed a few bits and bats that work better,

thanks for your time guys

---

