---
title: "boot freeze if not universal access preferences is loaded"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2010-04-21
Hello,

one of the last problems I face with ubuntu lucid is what more or less is described by the title:

while ubuntu lucid is booting, it goes where the user is required to type the username and the password.

Underneath, there is a panel bar, where it loads the universal access preferences icon.

If I wait a couple of seconds, until I see that icon, booting proceeds as expected. Yet, if I try to give my username and password immediately the screen freezes and I have to reboot.

Is something that happened to anyone else?

This is a constant thing happening from the first days updating to lucid. It happens also either logging out and long in back again or restarting.

Also I do not know how to report this problem.

Any ideas?

Regards!

---

### Post by Claus7 on 2010-04-21
Hello,

after tweaking a little with gdm theme:
[http://ubuntuforums.org/showpost.php?p=8348969&postcount=4](http://ubuntuforums.org/showpost.php?p=8348969&postcount=4)

now I might not connect at first time, yet there is no complete halt of my system...

Regards!

---

### Post by Claus7 on 2010-04-21
..only to be happy for not so many boots...

**MESSING THINGS**

So, I messed up my system a bit, trying to avoid this lock up thing. In the end, I ended up with a nice boot chart time, even though I think I can make it better...

What I did was to get rid off everything from karmic and focus on lucid. I uninstalled some karmic themes so as not to mess with the new ones...

I had installed a nice xsplash theme from here:
[http://ubuntuforums.org/showthread.php?t=1323777&highlight=karmic](http://ubuntuforums.org/showthread.php?t=1323777&highlight=karmic)

yet things did not go so well on booting so I uninstalled xsplash as well... 


Also I had enabled in xorg.conf the:     
Option "RenderAccel" "true"

So,
**PROBLEM**

The problem was that during boot I got frozen exactly after choosing me as a user -> I was not allowed to type my password.

Doing what the above post said, I was able to avoid complete halt, yet my computer did not proceed to boot fully clicking on user on the first time. It entered in a loop requiring once again to choose me as a user.
 
**SOLUTION 1**

The first solution is to keep things as it is in xorg.conf and change the option of universal access panel about _enhance contrast in colors_ (have this option **ticked**).

**SOLUTION 2**
Now, if I remove the Option "RenderAccel" "true" from xorg.conf I can enter with no problems either the option is ticked or not.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting) Freeze Bugs

**INSTALLING XSPLASH WITH CORRECT RESOLUTION**
In order to install a proper xsplash like the one I describe above, first of I have to have installed xsplash and xsplash artwork from synaptic. 

In /usr/share/images/xsplash/ folder there will be the contents of the default splash theme. We have to create a new folder there and move all the contents of the default splash theme keeping in mind the name of the bg_XXXxYYY.jpg file. (We need to remove only this file and keep all the others, yet splash files are supposed to entail all the necessary files as well).

Those XXXxYYY refer to the resolution needed by the boot process in order to display your xsplash theme. They are NOT necessarily refer to the resolution you keep your monitor. So, from the xsplash theme you have to have at least a file with resolution values equal to those of your default one.

As a result, in order to check if everything is ok, the command sudo xsplash should display your splash theme (press ESC to leave the screen). If not, there is something wrong.

I hope that after that everything will work ok...
The best boot time I got with cairo dock at boot was around 26 seconds! I think I can do better than that...

Regards!

PS: The option render acceleration in xorg had not caused me any problems before, so I guess that messing with universal access panel, might made something fishy...

---

### Post by Claus7 on 2010-04-21
Hello,

[LIST]
[*]solution two does not seem to work
[*]helpful post about changing splash and gdm theme: [http://ubuntuforums.org/showthread.php?t=1277030](http://ubuntuforums.org/showthread.php?t=1277030)
[*]helpful post about changing gdm theme:
[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

[*]Customize Karmic and Lucid screen, without splash, as before:
[http://www.omgubuntu.co.uk/2010/02/change-gdm-login-screen-background-in.html](http://www.omgubuntu.co.uk/2010/02/change-gdm-login-screen-background-in.html)
[/LIST]
Regards!

---

### Post by Claus7 on 2010-04-22
Hello,

this is a known bug, supposed to be fixed in release candidate:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/553200](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/553200)

Regards!

---

