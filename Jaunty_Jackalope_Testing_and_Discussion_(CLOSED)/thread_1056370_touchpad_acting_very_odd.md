---
title: "touchpad acting very odd"
date: 2009-01-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mullens101 on 2009-01-31
Hello,
   I've been running jaunty for several weeks now.  I have a lenovo 300 n100 and things were going well.  I have a synaptics touchpad that's been working great on ubuntu for a couple of years.  After an update this week though, it's acting very odd.  If I left click on a scroll bar and drag, it's OK until I lift my finger from the pad to scroll further down.  when I lift my finger, it basically disconnects and I have to re-click.

   Further than that, sometimes clicking in a title bar to move a window causes the window to minimize, while clicking on things, occasionally the screen "warps" for lack of a better word, and the cursor is suddenly located in the top left of the screen, and other times just single clicking on a dialog box randomly pastes stuff into the box.  Highlighting text has become nearly impossible and very frustrating.

   I've checked my xorg.conf and it has the same settings that have worked for eons on feisty, gutsy, hardy, and intrepid.

Any ideas what's going on?

---

### Post by Starks on 2009-01-31
Which driver does your touchpad use? Synaptics?

If so, then I too am experiencing quirky behavior. Then again, I might just have stupid fingers.

---

### Post by mullens101 on 2009-01-31
yes, I'm using the synaptics driver

---

### Post by mullens101 on 2009-01-31
Here's the corresponding section from my xorg.conf

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

---

### Post by t.alex on 2009-01-31
hi,

take a look at 
-> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320639](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320639)
-> [https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/322659](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/322659)

---

### Post by mullens101 on 2009-01-31
Thanks for the links, I had just found the first but the second helped.  I basically followed the downgrade path, per the second link.

I downloaded 0.15.2-0ubuntu8 from
[https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-input-synaptics/0.15.2-0ubuntu8](https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-input-synaptics/0.15.2-0ubuntu8)

then I uninstalled xserver-xorg-input-synaptics and installed the downloaded .deb ... all is well again.

---

### Post by caryb on 2009-02-01
I downgraded to fix mine as well, I had the touchpad left hand button pasting whatever was in the clipboard cache:confused:


Cary

---

### Post by Gina on 2009-02-01
I installed today's daily build onto my laptop to use ext4 format (other installation was from Alpha 1 updated and ext3) now with the new system my touchpad doesn't work properly - the pointer moves but tapping doesn't, nor scrolling.  It is also a Synaptic.  So I confirm this regression.

---

### Post by _oOMOo_ on 2009-02-11
The problems with my synaptics touchpad have been resolved in the main, however, there are a couple of alterations in the default configuration:

The vertical scroll area is so far over to the right of the pad that it's difficult to use.

Multiple finger tapping is IMHO misconfigured. Tapping with 2 fingers emulates a middle click, while tapping with 3 emulates a right click. I think this should be the other way around, because consistently tapping successfully with 3 fingers is more difficult than with 2, and right click is used more frequently than middle click. If you see what I mean. And you'd be forgiven if you didn't.

Now we seem to be moving towards xinput, is there a script we can use to set the configuration of the touchpad rather than editing xorg.conf?

Thanks, Jon

---

### Post by firstc624 on 2009-02-11
cary did you have to do anything to get your touchpad working?  mine is curently diabled or something.  i can used the trackpoint just fine, which i actually prefer, but it is nice to have the ability to   use the touchpad, is the driver for it not installed by default like it is in heron?

---

