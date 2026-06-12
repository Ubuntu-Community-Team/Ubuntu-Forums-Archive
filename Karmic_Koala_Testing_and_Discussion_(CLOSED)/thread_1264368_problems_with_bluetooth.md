---
title: "problems with bluetooth"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by waspbr on 2009-09-12
hello there chaps, I have recently updated karmic on 2 machines to the lastest *.10 kernel, however since then i have not been able to use my bluetooth mice. 

I tried to run the bluetooth-properties menu, and tried to add a device.here is the terminal output:

```
** (bluetooth-wizard:10947): WARNING **: Could not load UI from /usr/share/gnome-bluetooth/wizard.ui: Duplicate object id 'label1' on line 394 (previously on line 20)

```

I went to the file, but it was a little too much for me, has anyone got any tips or should I just wait for the next update?

meanwhile I have been using my crappy cheap emergency usb mouse. 

let the good times roll.

---

### Post by Sophont on 2009-09-12
Known problem. There was another thread about this a week ago or so.

Somebody left a duplicate label name in that file.

The error actually explains it nicely:
> Duplicate object id 'label1' on line 394 (previously on line 20)

The name label1 got used on line 20 - and later again on line 394.

Easily fixed.

Edit the given xml file and change the second label1 into something else (and unique) - I used labelx (following the first threads example) - but I guess the particular name is irrelevant as long as it is a unique one.

My BT mouse worked fine ever since.

Example:
sudo nano /usr/share/gnome-bluetooth/wizard.ui

Then press ctrl-w to find label1 - then again to find the second occurrence - then replace the label1 with labelx.

Come back if you have any problems or questions.

---

### Post by waspbr on 2009-09-12
it works, thanks for the tip

---

