---
title: "HELP!  I can't install Ubuntu 10.10"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by FSCII on 2011-02-11
Here's what happens to me - inserting cd and reboot - Ubuntu goes straight into demo/live mode.

The screen displays 2/3 of the background screen then gray underneath  (like a truncated image).  I'm able to change the background though.
 

Repeat and press F6 while booting I can choose language and install  ubuntu (looks NOTHING like the screenshots on Ubuntu help pages).  I  pick English and Install and Ubuntu goes straight to the demo mode  w/corrupt screen.

HELP PLZ (its going to be a dual boot w/Vista and I've already followed  the Ubuntu directions on making a 2nd partition for Ubuntu but can't  install!!!!)

(Im using ubutntu live 32 bit version its going to go alongside vista and if i like ubuntu it'll replace vista on the laptop)

---

### Post by slooksterpsv on 2011-02-11
What kind of a computer is it? I know we need to set a boot option set in when we attempt to boot (to see if it fixes the issue) nomodeset

I can't remember how to boot though so let me grab my other laptop and I'll be back to help ya. I can't remember if it works the same as it did in 8.04 or if 10.04+ was different for setting boot options.

---

### Post by slooksterpsv on 2011-02-11
Ok, so when you boot you should get like a purple screen with a little guy and an icon at the bottom middle. Press the ESC key when this shows up, it should give you a menu like:

Try Ubuntu
Install Ubuntu
..
..

Once here press the F6 key (on Try Ubuntu) and either select the option nomodeset, press Esc then enter, or press Esc and press left then right and type in nomodeset then press Enter.

Let me know if that works for you.

---

### Post by FSCII on 2011-02-11
I don't get a purple screen it goes straight to Ubuntu live.  And if I am quick and hit f6 I get a menu and pick english.  Then a vertical menu with these options:

Try Ubuntu Without Installing
Install Ubuntu
Check disc for defects
Test Memory
Boot from first hard disk

I pick Install Ubuntu -- and then for all intents and purposes its like I never picked install - it goes to live mode with the corrupted background image and clicking on the icon (within ubuntu) to install ubuntu, does nothing :(

I'm using a 2 year old Gateway HDMI laptop widescreen with Intel centrino processor dual core with 4gb ram

---

### Post by FSCII on 2011-02-11
Ok I'm trying this now with the nomode hidden menu via F6...

Now the screen is looking different... saying Ubuntu 10.10 with red and white dots beneath it - omg maybe its working...

Stay tuned...

---

### Post by FSCII on 2011-02-11
Will I need to take any other "off the beaten track" steps to get Ubuntu installed in Dual boot mode?


Ok Update:  After doing the F6 nomode thing Ubuntu again comes up with 2/3 of the background screen (lower 1/3 is gray/corrupt) with the following error message

The panel encountered a problem while loading

"OAFIID:GNOME_FastUserSwitchApplet"

Do you want to delete the applet from your configuration?

(I'm not sure if its installing or not - once again looks like I'm in the live mode idunno):confused:

---

### Post by slooksterpsv on 2011-02-11
> **FSCII said:**
> Will I need to take any other "off the beaten track" steps to get Ubuntu installed in Dual boot mode?


Ok Update:  After doing the F6 nomode thing Ubuntu again comes up with 2/3 of the background screen (lower 1/3 is gray/corrupt) with the following error message

The panel encountered a problem while loading

"OAFIID:GNOME_FastUserSwitchApplet"

Do you want to delete the applet from your configuration?

(I'm not sure if its installing or not - once again looks like I'm in the live mode idunno):confused:
Odd, usually I select keep or don't delete, then open a terminal and run: 

pkill gnome-panel

What's your hardware specs?

---

### Post by FSCII on 2011-02-11
I have Gateway laptop widescreen (1900x1200), 4gb ram, 160gb hard drive (120gb partition for windows vista and 40gb partition for ubuntu [as of yet unused]).

---

### Post by FSCII on 2011-02-11
I closed out the error messages and it left me looking like im in live mode demo of ubuntu again omg:confused:

---

### Post by FSCII on 2011-02-11
Ok one final update.  I repeated what you said and did the nomodest setting and then install ubuntu.  This time I didn't get that gnome error...

However I'm still stuck with the corrupted background screen and the appearance that it did not install but im in Unbuntu live :(

I'm going nuts here - any more suggestions?

---

### Post by FSCII on 2011-02-11
Ok I got past this - problem was *1* bad file on the entire disc when I used the option to check disc.  I'm still stuck but I'll start a new thread on the current problem lol thank you!

---

