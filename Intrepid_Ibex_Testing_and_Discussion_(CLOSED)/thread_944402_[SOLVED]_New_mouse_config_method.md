---
title: "[SOLVED] New mouse config method?"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mosimea on 2008-10-11
I am about at wit's end trying to get the scroll wheel on my Logitech LX8 mouse working properly.  My understanding is that HAL should have it work "automagically" and that the xorg.conf is no longer used to map the buttons (although I have tried using it).  If that is so and one's mouse still does not work, where do you go to make the fix?

Currently, the scrollwheel will scroll nautilus windows when the cursor is over the scrollbar, but in most other applications (Firefox, OpenOffice, etc.) I can only scroll up/down by pushing the scrollwheel left and right.

It would be great if the Mouse Preferences had button mapping options.

---

### Post by sjust on 2008-10-11
I have had the same problem since I went to Intrepid beta. I have used the command ```
xinput set-button-map "Logitech USB RECEIVER" 1 2 3 4 5 11 12 8 9 10 6 7
``` to set my buttons to the right order. I am using a LX7 so the buttons might be close for you. Now for a small rant. Why is this all being changed without the proper documentation for xinput. I have been using BTNX since it was first released. In fact if you check the forum for BTNX I was of the first to submit code to help make BTNX work. This program was great for setting up your mouse. Then everything had to be changed and now it does not work. This is not moving forward it is moving backward because we are now back to where we started from, no way to configure multi-button mice. If things like this are going to change then proper documentation must be written and new tools must be created to use the new procedures before it is sent out to the end user, or we will never convert people from windows. End rant. Have a nice day.

---

### Post by autocrosser on 2008-10-11
Take a look at:
[http://ubuntuforums.org/showthread.php?t=938487](http://ubuntuforums.org/showthread.php?t=938487)

The way mice/keyboards are configured has changed with Xorg 1.5--you need to create files that Hal can use.

---

### Post by mosimea on 2008-10-11
Based on your suggestions, I tried the following:

First (since it seemed the easiest to test :)) I tried using what worked for Sjust: 

```
xinput set-button-map "Logitech USB RECEIVER" 1 2 3 4 5 11 12 8 9 10 6 7
``` 

No love, it said there wasn't said device.  Odd, as a cat /proc/bus/input/devices showed a "Logitech USB Receiver".  Case sensitive, perhaps? Tried this mixed case version without success as well.

Next tried "xinput list", which showed it liked to be called "Configured Mouse".  "xinput query-state" of "Configured Mouse" stated that it has 32 buttons.  Hmmm.

So I tried:

```
xinput set-button-map "Configured Mouse" 1 2 3 4 5 6 7 8 9
```

Hurray!  Scrollbar works up down and side to side, forward and back buttons work as well.

I then checked to see if this is written out to a /etc/hal/fdi/policy/mouse-wheel.fdi file, but found nothing. Xinput changes are dynamic?  I certainly could add the xinput call to run at boot, but should I also try to translate this to a mouse-wheel.fdi file?

---

### Post by autocrosser on 2008-10-11
If you create a .fdi file it will "stay" that way...I say this loosely--there is too little doc support as of yet....

---

### Post by canabal on 2008-10-11
I wish btnx would work for intrepid, but the developer is not going to continue because he has to completely re-build it with the new method.

---

