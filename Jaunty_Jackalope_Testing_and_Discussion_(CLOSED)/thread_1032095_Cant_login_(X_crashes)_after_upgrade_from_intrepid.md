---
title: "Cant login (X crashes) after upgrade from intrepid to jaunty - Intel 915"
date: 2009-01-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-01-06
After an upgrade to Jaunty this morning, I can no longer login using X. Soon after entering username/password, there is some random screen with bluish patterns and then X server crashes and I am thrown back to login screen.

I understand that X server is pretty much unstable right now, but are there any workarounds to get it working on Intel 915GM

Attaching my Xorg.0.log

---

### Post by ShirishAg75 on 2009-01-06
Did you try the workaround given at the first post at [http://ubuntuforums.org/showthread.php?t=1024573](http://ubuntuforums.org/showthread.php?t=1024573)

---

### Post by vikrant82 on 2009-01-06
Yes, I have tried it, that workaround didn't work either...

Anyone heard of these lines in logs:

```
AUDIT: Tue Jan  6 16:14:06 2009: 4614: client 4 rejected from local host ( uid=0 gid=0 pid=4636 )
```

---

### Post by jerrylamos on 2009-01-06
Compiz is on by default except for some Intel graphics such as i845G and 82830 which are "blacklisted" since the developers haven't fixed the problem(s).  I don't know whether the Intel 915 driver can handle Compiz fancy glitzy appearance only tricks or not.

What I do when I suspect Compiz is:
Boot in recovery mode
Select root shell prompt
apt-get remove compiz compiz-core
exit
resume normal boot

From forum posts, there are tons of pc's with Intel graphics out there, however for whatever reason the associated X Intel drivers seem to get little attention.

Good luck, jerry

---

### Post by ShirishAg75 on 2009-01-06
vikrant82, 
 What jerrylamos is saying is very much possible.

What I would suggest is instead of just blindly following stuff to try a script called compiz-check. 

Go to recovery and use netroot (if that's possible)

if not then use root and do the following 

```
$ dhclient
```then download the script 

```

$ wget http://blogage.de/files/9124/download -O compiz-check
```
```

$ chmod +x compiz-check
```And finally 

```
$ ./compiz-check
```you should get output something like this 

```

$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```If you get some error then it means your something or the other (software or hardware) is not suitable for compiz. 

In which event you should do what he has said earlier.

---

### Post by vikrant82 on 2009-01-06
Well, compiz-check shows everything green. 

I am not completely out, I am able to use other WMs. Right now I am in IceWM. 

But i did remove compiz for the sake of it. 

Its only, gnome and Kde which is crashing .. 

The culprit lines are sure, "client 4 rejected from local host ( uid=0 gid=0 pid=4636 )"

Time to play with other window managers for now .. and hoping for that magic update that will fix everything... :)

---

### Post by darkenergy on 2009-01-14
same problem here!

i even reinstalled the system completely since i got some other problems during the update from intrepid.

luckily i can start firefox from the console but it's not very nice to "work" without a desktop environment but this way i have access to synaptic etc.

any suggestions?

maybe i should try to uninstall the whole compiz stuff

---

### Post by vikrant82 on 2009-01-15
Uninstalling compiz wouldnnt help either, since its a problem with xserver itself. You can install other WMs like IceWM or Fluxbox.

Or you can still boot into gnome desktop by using some other failsafe driver like fbdev or vesa. Mention them in your xorg.conf and you should have a gnome session running after few prompts.

---

### Post by vikrant82 on 2009-02-01
> **vikrant82 said:**
> Well, compiz-check shows everything green. 

Time to play with other window managers for now .. and hoping for that magic update that will fix everything... :)

So, the wait is over finally those magic updates did come. Back to intel driver.

---

### Post by PRGUY85 on 2009-02-03
I have an old HP DV1315cl laptop with Intel 915.  There is no restricted driver shown for it and when I click on Normal/Advanced desktop effects on Appearance, I get nothing.

Any ideas?

---

### Post by PRGUY85 on 2009-02-04
Anyone?

---

### Post by vikrant82 on 2009-02-05
Intel Video chips do not require 'Restricted Drivers'. Restricted drivers are used by cards which do not have open source drivers. For example cards from manufacturers like Nvidia, ATI.

---

### Post by PRGUY85 on 2009-02-05
> **vikrant82 said:**
> Intel Video chips do not require 'Restricted Drivers'. Restricted drivers are used by cards which do not have open source drivers. For example cards from manufacturers like Nvidia, ATI.

Well, when I hit Advanced Effects or Normal on Appearance dialog, I can't get them to work.  Do I have to manually edit the xorg.conf file for it work properly?

---

