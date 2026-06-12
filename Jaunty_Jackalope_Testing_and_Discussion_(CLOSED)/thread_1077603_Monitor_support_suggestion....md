---
title: "Monitor support suggestion..."
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Gizenshya on 2009-02-22
Apparently a lot of people have serious trouble with monitors from HP, Dell, Compaq, and other computer manufacturers.  Many of the monitors are often not recognized by ubuntu, and ubuntu sets the screen resolution very low... so low the computers are not practically useful. I just ran into a case of this myself, and I've found several recent posts by people with the same problem.  It took a LOT of googling, trouble-shooting attempts, and I think I'm close to a solution (to use generic monitor settings by manually setting the xorg.conf file).  A major problem with this is that, from my searches, it is often misdiagnosed as several things, most often as some sort of graphics card/driver issue.

I strongly suspect that this turns a lot of people away from ubuntu, because of what I see as a problem with a simple solution.  And when one considers the number of people with these types of computers (hint: A LOT), the need for change becomes clear.

Monitors are fairly standardized, and many (don't have figures, sorry) are able to use generic monitor drivers effectively. Perhaps nearly all of them?

My suggestion:

adding something in the System->Preferences->Screen Resolution menus to "Try Generic Drivers" for monitors that are Unknown.  Perhaps having a message something like "Your Monitor is Not Recognized" and having an option to try generic settings.  Or maybe, "Try known settings" where you can input them, and wait 15 seconds to accept or revert.  Or, perhaps incorporating some sort of database with dell, HP and other monitors' known capabilities so that you could manually choose yours (or type it in).

There are several ways something like this could be handled, and it depends on issues that I don't know much about (like: how to deal with refresh rates?  HorizSync? options? etc...).  But something the number of people that some sort of intuitive menu like this would help makes it well worth any effort, in my opinion.

---

### Post by Neon Lights on 2009-02-22
I believe this is more a problem with the Video Card drivers not being right, rather than a problem with the monitor.

---

### Post by ronacc on 2009-02-22
no he is right about some monitors not being recognised ( or reporting themselves wrong) . I have one that works just fine if I hand modify the screen section in my xorg.conf or use nvidia-settings to configure my display but defaults to 800x600 if I do nothing and believe me that looks like c**p on a 1680x1050 WS .

---

### Post by caryb on 2009-02-23
Here here! I am experiencing this with lots of my setups (have 120 Kubuntu machines on my network) they do not have common cards. I downloaded a application the name eludes me at the moment but it interrogates the monitor for it's resolutions it is capable of. The last one I was playing with was a HP vp17 monitor when I interrogated it the output said the correct model but when it came to the resolution part is was total gibberish! My thought is if we are using this info for setting up xorg God help us. There has to be a overide to help us to fix this quick or as the previous poster said we will be driving people away in droves.


Cary

---

### Post by ronacc on 2009-02-23
@caryb if you remember the name of that app please post it , I found an rpm (monito-edid) but haven't been able to get it to convert yet .

---

### Post by frankwakeman on 2009-02-23
I'll also say 'here here!'.  I hope the Ubuntu team get onto this.

---

### Post by Edho on 2009-02-23
Same problem here.

SIS mboard,all in, + verry common lcd monitor Acer AL712.
Jaunty has trouble to detect the right settings.
Editing the Xorg.conf file do not help.

Former versions of Ubuntu did all work fine with the same hardware.

---

