---
title: "system&gt;shutdown now does nothing ."
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-08-09
system>shutdown  nolonger even takes you to the login window it does nothing at all only brings up a dialog box that disapears when you select any choice with no effect . the logout button still works . sudo shutdown now takes you to the recovery menu . this started after lastnights updates . filed bug#256496

---

### Post by cariboo on 2008-08-09
I can confirm the bug, but I see that it has already been reported by someone else. One other thing I can confirm is that compiz finally works again.

Jim

---

### Post by DavidONE on 2008-08-10
It's been flagged as a duplicate of [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506) and a patch has been released, so I guess it should be fixed soon....

---

### Post by ronacc on 2008-08-10
thanks for the info . I hope it really is a duplicate of 250506 . I was aware of that one but this is a bit different , system>shutdown was taking you to the gdm login screen and you could select shutdown from the options menu there . now for me atleast it dosen't even do that, it does nothing at all. I hope the patch they mention fixes it .

---

### Post by Gina on 2008-08-10
Same here. **System > Shut Down** then clicking **Shut Down** or **Restart** does nothing other than close the dialog.  I'm using command line to restart or shutdown.  At least that's a bit better than getting up and pushing the  button on the system box!!

---

### Post by ronacc on 2008-08-10
@ Gina  you can still use the logout/switch user button (running green man top right) to get to the login screen and shutdown from the options menu there .

---

### Post by Gina on 2008-08-10
True :)  The CLI way is quicker though :)

---

### Post by Nullack on 2008-08-10
Fixes have hit the build farm, joy

---

### Post by Gina on 2008-08-10
Yippee :lolflag:

---

### Post by ronacc on 2008-08-10
I hope the fix actualy does , I'm not sure this is the same bug that they marked it as a dupe of , the takes you to the login window has been around since alpha 1 this one just started with the august 8 updates .

---

### Post by autocrosser on 2008-08-10
Cross-fingers.....I've been just grabbing a term & doing a sudo reboot----bad form you know:)

---

### Post by rockface on 2008-08-17
> **autocrosser said:**
> Cross-fingers.....I've been just grabbing a term & doing a sudo reboot----bad form you know:)

Problem with shut-down dialogue still persists, bummer.

---

### Post by Trespasser on 2008-08-17
Yes, the Shutdown function not working is a bummer but I'm sure it will be sorted out soon. On a side note I'd like to say that this new kernel (2.6.26.5) is doing quite well. It now runs a Windows program I was using under Wine without a problem. Prior to this kernel it would freeze-up while loading (I would expect alsa related). Now I can stop dabbling in other distros trying to find a solution.

Later...

---

### Post by Exsecrabilus on 2008-08-18
> **ronacc said:**
> sudo shutdown now takes you to the recovery menu .
```
sudo shutdown now -P
```

---

### Post by Gina on 2008-08-19
I've set up a launcher on the top panel containing **sudo reboot** set to Type **Application in Terminal**.  Now if I click the icon a Terminal window pops up asking for password.  Do that and the system reboots.  Should be similar for shut down.

---

### Post by jfernyhough on 2008-08-19
Instead of doing a nasty forced reboot you can simply log out, then shutdown from GDM.

---

### Post by Gina on 2008-08-19
Yes, that's what I was doing but it's a lot of faffing about.  Reboot from command line does the same thing.

---

