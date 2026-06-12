---
title: "xorg broken? cannot load radeon"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tournesolo on 2009-09-13
After upgrading my powerbook G4 to 9.10 today, xorg doesnt start anymore complaining that it cannot load the module radeon and hence "no screens found". (X was working fine on this machine with 9.04)

Is anybody else seeing this? Any workaround? 
Thanks!

ps/update: it turns out the /etc/X11/xorg.conf is now empty (zero length)...

---

### Post by alligoodw on 2009-09-13
> **tournesolo said:**
> After upgrading my powerbook G4 to 9.10 today, xorg doesnt start anymore complaining that it cannot load the module radeon and hence "no screens found". (X was working fine on this machine with 9.04)

Is anybody else seeing this? Any workaround? 
Thanks!

ps/update: it turns out the /etc/X11/xorg.conf is now empty (zero length)...

After updating today, I can't get anything either.  I see the Nvidia splash screen and then the screen flashes two or three times and then stops.  I never get into the GUI.

---

### Post by tournesolo on 2009-09-13
Here is a workaround which partially fixes the issue: use the fbdev driver instead of the radeon driver in your xorg.conf

Since I had no xorg.conf anymore, what I actually did was to run this in a console, as root:

Xorg -configure

Then move the resulting config file to /etc/X11/xorg.conf. Now X starts up, though ugly and limping...
(the solution was gleaned from a thread here a week ago: [http://ubuntuforums.org/showpost.php?p=7902691&postcount=11](http://ubuntuforums.org/showpost.php?p=7902691&postcount=11))

---

### Post by tournesolo on 2009-09-22
Bump!

With an up to date system as of 22 Sept, it is still impossible to load the radeon / ati drivers. The system complains about:

 dlopen: libdrm_radeon.so.1: cannot open shared object file: no such file or directory

And then

(EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so

Anybody else seeing this?

(An improvement is that it now automatically loads the framebuffer driver instead, even in the absence of an xorg.conf file telling it to do so).

---

### Post by Claus7 on 2009-09-22
Hello,

some days ago I updated my alpha karmic and when it rebooted I could not see a thing. Blackity black black was the result, without even a cursor popping up in the left corner of the screen. No matter what, I was able to see the nvidia logo, yet to no avail. After that it was total darkness. Also I have to add that I was trying to install the nvidia drivers from the ubuntu synaptic package manager (having them already installed from nvidia web site), which might have messed things. Anyway, the result was disastrous.

Now, what I did was to update my system some days afterwards, while opening my system from the recovery mode. The update went ok. Then I uninstalled and installed the Nvidia drivers downloading the drivers from the web site of nvidia (all these without graphical environment). In the end I was able to recover my old xorg.conf file (ALWAYS keep a backup of a working xorg.conf, since it is valuable these days) and put it in place (/etc/X11/xorg.conf). 

The next time I rebooted I had (and still have) some messages about some unknown links, yet the system enters in log page normally.

What I would try is to recover my old xorg.conf file. If you search in the aforementioned folder, I think that you will be able to find one, which will be your last working configuration.

Hope this helped a little,
Regards!

---

### Post by tournesolo on 2009-09-22
Thanks Claus - but you are talking about a different bug (black screen, which I do not get) and a different situation: I do have my old working xorg.conf, that's not the issue. So again, the radeon driver does not load, with or without a good xorg.conf. It says:

   dlopen: libdrm_radeon.so.1: cannot open shared object file: no such file or directory
   (EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so

It doesn't look like a known issue -- I'll open a bug report.

---

### Post by Claus7 on 2009-09-22
Hello,

first as you have seen I have nvidia and not ati, so I have not faced exactly the same problem as you. I pointed in a general direction, in case this might fix the problem to you. I do not deny, that my problem seems different than yours, yet:

> **tournesolo said:**
> 
ps/update: it turns out the /etc/X11/xorg.conf is now empty (zero length)...

so that means that your original xorg.conf file was not there anymore.

In addition I saw:
> **alligoodw said:**
> After updating today, I can't get anything either.  I see the Nvidia splash screen and then the screen flashes two or three times and then stops.  I never get into the GUI.
which seems more or less similar to what I describe.

Also:
> **tournesolo said:**
> 
Since I had no xorg.conf anymore, what I actually did was to run this in a console, as root:

Xorg -configure

Then move the resulting config file to /etc/X11/xorg.conf. Now X starts up, though ugly and limping...
(the solution was gleaned from a thread here a week ago: [http://ubuntuforums.org/showpost.php?p=7902691&postcount=11](http://ubuntuforums.org/showpost.php?p=7902691&postcount=11))

from what I get from the above quote you try to reconfigure that file. NO MATTER what I have tried since jaunty, the only solution that saved me was an old xorg.conf file I had since dapper days. I was not able to recreate a descent file with any commands. The only thing I was able to do so was a mediocre xorg file, which was giving me a bad screen. This is the main reason I stuck with that and told you all these things. 

> **tournesolo said:**
> Thanks Claus - but you are talking about a different bug (black screen, which I do not get) and a different situation: I do have my old working xorg.conf, that's not the issue. So again, the radeon driver does not load, with or without a good xorg.conf. It says:

   dlopen: libdrm_radeon.so.1: cannot open shared object file: no such file or directory
   (EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so

It doesn't look like a known issue -- I'll open a bug report.

Yes you can. Searching a little more I see that others have this as well and mostly they get that error during an upgrade. 

Hope you will fix your issue,
Regards!

---

### Post by tournesolo on 2009-09-22
Fixed. It turns out that a dependency was missing: installing libdrm-radeon1 provided  the file libdrm_radeon.so.1 and fixed the issue. 

(And thanks for trying to help!)

---

### Post by Claus7 on 2009-09-23
Hello,

very glad you solved your problem! So the "no such file or directory" was once again a missing library!...
I'm still learning and assimilate in the process!

Regards,
happy ubuntu-ing!

---

