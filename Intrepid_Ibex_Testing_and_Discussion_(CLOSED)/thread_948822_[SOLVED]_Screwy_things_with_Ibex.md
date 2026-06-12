---
title: "[SOLVED] Screwy things with Ibex"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wenuswilson on 2008-10-15
I just upgraded to Intrepid Ibex. I am running a T61 Thinkpad. I have a few problems that I have no idea how to solve. First, My keyboard layout reverted to the standard keyboard and now all of my keys are not matching up well. For example, pressing Up yields a print screen. The delete key doesn't do anything, movement keys don't move, etc. Second, my wireless connection doesn't seem to work either. Third, I used the thinkwiki directions to get the Trackpoint scroll to work and that doesn't seem to do anything.

Any ideas? Thanks in advance.

---

### Post by sokopok on 2008-10-15
For the keyboard you could
```
sudo dpkg-reconfigure xserver-xorg
```
This will rerun the X setup and you can select the correct keyboard layout again.

---

### Post by Yellow Pasque on 2008-10-15
For the wireless, identify your wireless card with:
```
sudo lshw -C network
```
Then, search the forums or Ubuntu Documentation. Wireless howto's are very common.

---

### Post by wenuswilson on 2008-10-16
> **Temüjin said:**
> For the wireless, identify your wireless card with:
```
sudo lshw -C network
```
Then, search the forums or Ubuntu Documentation. Wireless howto's are very common.

I hate to sound like a nub, but currently in the world of figuring this out, I am, how do I enable my wireless because it is currently saying disabled. Side note-- the whole confusion lies in the fact that Ubuntu usually figures this out so I don't have to think about it.

Thank you.

---

### Post by wenuswilson on 2008-10-16
> **sokopok said:**
> For the keyboard you could
```
sudo dpkg-reconfigure xserver-xorg
```
This will rerun the X setup and you can select the correct keyboard layout again.

Didn't change a thing, actually quite depressing to not be able to use the left and right movements to click yes or no on questions but having to resort to tab. thank you for you input though, much appreciated.

---

### Post by philinux on 2008-10-16
Make a specific post about one problem. Use a descriptive title and post here. You'll get more joy. Dont forget to include your system specs.
[Ibex]("http://ubuntuforums.org/forumdisplay.php?f=346")

---

### Post by Sef on 2008-10-16
Moved to Ibex forum.

---

### Post by gjoellee on 2008-10-16
> **wenuswilson said:**
> I just upgraded to Intrepid Ibex. I am running a T61 Thinkpad. I have a few problems that I have no idea how to solve. First, My keyboard layout reverted to the standard keyboard and now all of my keys are not matching up well. For example, pressing Up yields a print screen. The delete key doesn't do anything, movement keys don't move, etc. Second, my wireless connection doesn't seem to work either. Third, I used the thinkwiki directions to get the Trackpoint scroll to work and that doesn't seem to do anything.

Any ideas? Thanks in advance.

Go to System->Preferences->Keyboard, now go do the "Layout" tab and select your keyboard layout. Set your layout to "Default" and delete the other one. Now click "close". The changes will take effect after a reboot.

---

### Post by wenuswilson on 2008-10-16
> **gjoellee said:**
> Go to System->Preferences->Keyboard, now go do the "Layout" tab and select your keyboard layout. Set your layout to "Default" and delete the other one. Now click "close". The changes will take effect after a reboot.

I have already tried that, the Keyboard model is set to IBM Thinkpad R60/R61/T60/T61 ...granted my computer is new so it's a Lenovo and language is set to everything I want/need. Up still gets me a print screen option.

---

### Post by psyke83 on 2008-10-16
> **wenuswilson said:**
> I have already tried that, the Keyboard model is set to IBM Thinkpad R60/R61/T60/T61 ...granted my computer is new so it's a Lenovo and language is set to everything I want/need. Up still gets me a print screen option.

The Alpha 6 release notes said that you should set the keyboard type to "Generic/Evdev-managed keyboard" in System -> Preferences -> Keyboard. I didn't see it mentioned in the Beta release notes, but it may still be necessary.

If it still didn't work, then also try the "automatic" reconfiguration option for xserver-xorg:
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wenuswilson on 2008-10-16
> **psyke83 said:**
> The Alpha 6 release notes said that you should set the keyboard type to "Generic/Evdev-managed keyboard" in System -> Preferences -> Keyboard. I didn't see it mentioned in the Beta release notes, but it may still be necessary.

If it still didn't work, then also try the "automatic" reconfiguration option for xserver-xorg:
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

The delete buttons and movement keys work properly now, thank you, the volume buttons and the fn + movement keys to make media play still don't work but that's fine for now.

Thank you!

---

### Post by wenuswilson on 2008-10-21
Alright for those who may be in the same boat as I was -- I solved it.

In Admin -> Software Sources -> Third-party Updates -> Unsupported updates. Make sure it's checked. That was you can get all of the updates. And everything that I had problems with will go away. My mistake.

---

