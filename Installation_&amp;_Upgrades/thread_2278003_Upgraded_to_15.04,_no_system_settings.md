---
title: "Upgraded to 15.04, no system settings?"
date: 2015-05-13
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2015-05-13
Hi,

I recently upgraded to 15.04 and I don't know if this is a new feature or what but my system settings looks like a bad mobile phone crossover. 
When trying to reach any other settings, such as sound settings or about this computer from the dropdown menus up in the right corner, nothing happens. It's as if the GUI isn't installed. 

I'll link a video to show you what I mean.

[https://youtu.be/jqs5p8yhhEQ](https://youtu.be/jqs5p8yhhEQ)

Regards.

---

### Post by monkeybrain20122 on 2015-05-13
I don't know how you got there, it looks like unity 8 on some Youtube demos I saw. Mine is same as 14.04.

---

### Post by grahammechanical on 2015-05-13
If we install Unity 8 or unity8-desktop-session-mir we get some utilities that are from the Ubuntu phone because the Ubuntu phone is Unity 8 running on Mir. These utilities include the System Settings from the Ubuntu phone. So, we will then have two different kinds of System Settings. As well as other utilities from the phone OS.

It seems that in your case and for some reason the traditional Ubuntu System Settings has been removed. You may be able to solve this by installing unity-control-centre.

I do not think that the upgrade to 15.04 has caused this at all. And installing unity8-desktop-session-mir will not remove unity-control-center either. How things got to be this way I cannot even guess.

Regards.

---

### Post by pingaan on 2015-05-14
Tried installing unity-control-center and got:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Tried installing libcheese-gtk23 via Ubuntu Software Center but it ended wih a crash... :(

---

### Post by monkeybrain20122 on 2015-05-15
Well what exactly did you do to get 15.04?

---

### Post by pingaan on 2015-05-17
I used Upgrade Manager.

---

### Post by dino99 on 2015-05-17
purge all the unity 8 packages if they are installed

---

### Post by pingaan on 2015-05-18
II have unity8, unity8-common and unity8-private isntalled but none of them can be uninstalled due to similar errors to the one above; libcheese*.

---

