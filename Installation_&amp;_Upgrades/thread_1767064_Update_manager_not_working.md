---
title: "Update manager not working"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by leifwi on 2011-05-25
The update manager is showing available updates, but when I klick the install button, the activity indicator rotates for a few seconds, after that nothing happens. 

I have a similar problem with the date and time application. When I select it from the menu nothing happens.

The computer is a Thinkpad T41 with ubuntu 11.04.

---

### Post by mörgæs on 2011-05-25
What happens if you boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by leifwi on 2011-05-25
I have tried the

sudo apt-get update
sudo apt-get upgrade

and that installed a lot of updates, but did not solve the original problem.
I did not try the "clean" option, because I had just made a clean installation of the 11.04 (not upgrade from the previous version).

---

### Post by mörgæs on 2011-05-25
'Clean' in this context only means that old cached packages are removed. It is a good routine for saving space.

I don't get it completely - what is the problem now, after you are able to install the updates?

---

### Post by leifwi on 2011-05-25
The original problems still remain. The update manager (System/Administration/update manager) GUI, and the Date and Time GUI are still not working. When trying them the activity indicator rotates for a few seconds and after that nothing happens.

---

### Post by leifwi on 2011-05-25
In addition to the previous. I can see the available updates, but when I click the install button nothing happens.

---

### Post by plucky on 2011-05-25
> **leifwi said:**
> In addition to the previous. I can see the available updates, but when I click the install button nothing happens.

Are the updates ticked?

If they are not,then try ```
sudo apt-get dist-upgrade
```


Good Luck

---

### Post by leifwi on 2011-05-25
Yes they are ticked. I can also untick or tick any item, but after pressing the install button nothing happens. In the previou version (10.04) I was promted for a password.

---

### Post by mörgæs on 2011-05-25
I wouldn't bother with Update Manager, as long as apt is working. Update Manager calls an apt-process anyway behind the curtain.

---

### Post by leifwi on 2011-05-25
The same problem is also with the date and time setting. When I select that in the Administration menu, nothing happens. There is probably a way around that also, but in general, if a GUI is available for something one would expect it should work, or is to much to ask?

---

