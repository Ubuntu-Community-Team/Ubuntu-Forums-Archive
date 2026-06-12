---
title: "Wacom &quot;Relative Mode&quot; Problems"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by mistersocks on 2009-11-28
Hello,

Karmic Kola 64-bit

Wacom  bamboo 
[COLOR=Red]**Tablet not working when set to Relative mode**
[/COLOR]
I am a some what experienced user. After a clean install of Ubuntu I have my Wacom tablet up and working but not without problems. Everything functions correctly so long as things are set to absolute mode. When I switch to relative mode I run into issues inside of my drawing programs.


After using  xsetwacom to change my wacom tablet to relative mode it seems to work correctly but in GIMP and MYPAINT the Stylus reacts sporadicly, by sporadically I mean almost not at all, and I lose pressure sensitivity.

I have tried reverting back to the Xorg method but run into the same problems. I have also tried to set the mode to relative in the .fdi options again it appears to take the proper effect but inside of the programs it again fails to function properly.

[COLOR=Red]**:: Please HELP ::**[/COLOR] (ill be on windows till some one can :confused: )

---

### Post by ola on 2010-03-06
Did you find any solution? I'm having the same problem.

---

### Post by mistersocks on 2010-03-08
Yeah actually i did put the words in quotes so instead of stylus put 'stylus' or what ever the item you are trying to change the settings for is called in your xorg.conf

---

### Post by ola on 2010-03-09
Since then I have run into another problem (with [Lucid and Wacoms]("http://ubuntuforums.org/showthread.php?t=1423278")) so I'll see when I can try it. Thanks a lot for answering though!

---

### Post by mistersocks on 2010-03-09
I have been making a whole set up for digital art work including 3d design and painting. I might be able to offer you some advice. What are the other problems you have hade.

---

### Post by ola on 2010-03-10
Ah, nice!

I can't find the device with xsetwacom anymore (since Lucid upgrade). Check out this thread: [http://ubuntuforums.org/showthread.php?t=1423278](http://ubuntuforums.org/showthread.php?t=1423278)

Thanks in advance!

//Ola

---

### Post by megawebmaster on 2010-03-13
Hi! I've got Wacom Bamboo Fun Pen&Touch Tablet (CTH-461) and I've got the same problem as you - pressure sensitivity works when Stylus is set to Absolute mode, but when I'm trying to set it to Relative (which is more convenient to me) Stylus isn't working nearly at all in Gimp... Have you solved this problem in Karmic 64-bit?

---

### Post by ola on 2010-03-13
Hi,

I'm still having the same issues so no, I haven't found a solution for it yet.

---

### Post by megawebmaster on 2010-03-14
So we have to wait for newer driver or something...

P.S. Now I've got another problem - touch isn't working at all. Maybe you have a few pieces of advice for me?

---

### Post by ola on 2010-03-14
What do you mean with *touch*?

---

### Post by mistersocks on 2010-03-15
I have to be honest and say that I have given up on Ubuntu. Its a wonderful OS and has its uses. I have even used it to push Linux on some family members, in fact my mother won't use anything else any more.  But I just use Debian for my 3d work and digital painting. You will still have many of the problems you do now but they just seem easier to work out....a lot easier.

---

### Post by megawebmaster on 2010-03-20
I mean using tablet as touchpad with fingers ;)

---

### Post by ola on 2010-03-20
Nice! I didn't even know that was possible.

There has been a [bug report in Windows on similar offset problems]("https://bugzilla.gnome.org/show_bug.cgi?id=154657") for some years. The solution there is to start Gimp with *--no-wintab* which disables the pressure sensibility but it works. No good solution. 

This issue might be the same? I haven't tried it yet.

---

### Post by BuffGuy900 on 2010-03-26
@ola: I think the GTK bug is spot-on, however I can't (and don't want to) run GIMP without pressure sensitivity.

Here's my issue as I experienced it:

Only when tablet is in relative mode (as desired)

GIMP or Inkscape fixes the the drawing-tool coordinates at (0,0) on the WINDOW
or SCREEN (depending on program setting)

GIMP/Inkscape reports drawing-tool coordinates as if the the tool was placed at
(0,0) in the WINDOW or SCREEN
This may be a negative value

The actual pointer (read by Kubuntu) exhibits desired/expected behavior
Therefore I can control menus, etc.

Since it happens in both GIMP and Inkscape, I think this is an issue with GTK

This does not occur when tablet is in absolute mode

Kubuntu 9.04 (Jaunty)
GTK v. 2.16.1-0ubuntu2
GIMP 2.6.6
Wacom Bamboo Fun 4x6

---

### Post by thegeologician on 2010-05-27
@BuffGuy900: yeah, I see the same behaviour. When looking at the raw input from the board (with xidump) that is what the coordinate reading is: in relative mode, you get relative coordinates for every readout, i.e. somewhere in the range +/-~40. Seems, these get mapped into the "drawing space" directly...

@wegawebmaster: same here. haven't got the touch to work (yet?) - did you find a solution?

---

### Post by thegeologician on 2010-05-27
Update: I found some solution for the touch in [this]("http://ubuntuforums.org/showpost.php?p=8823142&postcount=875") post, but experience the same problems others report: the mouse-movement with the touchpad is sketchy, often looses track... Gestures work in principle, but with the same issues...
Let's hope for a new version of the driver soon...

---

### Post by Favux on 2010-05-27
Hi thegeologician,

> Let's hope for a new version of the driver soon...

A new gestures patch was submitted a few weeks ago.  It was reviewed and was resubmitted today.  Hopefully it will pass muster and be comitted shortly.  Then you'd just need to clone the xf86-input-wacom git to get updated touch/gestures.

---

