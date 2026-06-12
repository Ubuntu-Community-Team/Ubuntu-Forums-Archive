---
title: "Karmic hot keys"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ArtLaForge on 2009-09-28
Hi forum guru's, I started Ubuntu with Jaunty Alpha 1, had so much fun I built a second computer and loaded Karmic alpha 1. Jaunty was a pretty bumpy road at the beginning but reading all the posts and reading all of Kier Thomas's books I'm coming up to speed. Karmic has been pretty stable compared to Jaunty for me, I've opted for 64 bit this time too. Flash was my concern with the 64 bit distro but that must have gotten fixed, works great. My question: I was used to Alt/F2 for the run command in Jaunty and It doesn't seem to be implemented in Karmic. Did It get changed or just not implemented? Also I've noticed Evo has the same issue both in 32 and 64 bit with double contacts in the list when forwarding email when you select the "To" field. Has anyone else experienced that?

Can't wait for the Lynx:P

---

### Post by ArtLaForge on 2009-09-28
Hmmmm. Must be a private club????

---

### Post by Elfy on 2009-09-28
You expect that to help get an answer?

When someone who can answer see's the thread it will get one, in the meantime be patient.

---

### Post by nhasian on 2009-09-28
personally i'm more likely to look at a thread if it has 0 responses.  if it has 1 or 2 responses then i'll assume that the question had been answered, or is in the process of being answered.  anyway, to answer your question ArtLaForge (at least one of them anyway) Alt-F2 has always worked for me in karmic to bring up the run dialogue box.  

If you using 64bit ubuntu, hopefully you grabbed the 64bit adobe flash from labs.adobe.com instead of using the 32bit version from the ubuntu repos.

As for Evolution, i've never even used that.  I like Thunderbird because its cross platform :)

---

### Post by ArtLaForge on 2009-09-28
> **nhasian said:**
> personally i'm more likely to look at a thread if it has 0 responses.  if it has 1 or 2 responses then i'll assume that the question had been answered, or is in the process of being answered.  anyway, to answer your question ArtLaForge (at least one of them anyway) Alt-F2 has always worked for me in karmic to bring up the run dialogue box.  

If you using 64bit ubuntu, hopefully you grabbed the 64bit adobe flash from labs.adobe.com instead of using the 32bit version from the ubuntu repos.

As for Evolution, i've never even used that.  I like Thunderbird because its cross platform :)

Thanks for the response nhasian, my appologies for being so impatient, I'm new to forums, I'm learning. The Alt F2 hot key did not work for me in either Karmic 32 or 64 bit, which was two different ISO's and two different CD burns, I wouldn't think that would be the problem. But since it works on your machine I'm left scratching my head. Everthing else is working flawlessly. I hate to reinstall to see if I recover the hot key. As to the adobe flash, I read so many horror posts about flash and all the work arounds, that I just installed the flashplugin-nonfree from synaptic and it works on everything I use. I'm happy:P

---

### Post by Sophont on 2009-09-28
Are you up-to-date with your updates?

Until last week there was a regressen which broke Alt-F1 and Alt-F2 *if* the background of the panel was changed (for example I had it set to transparency).

That was fixed a few days ago though.
Alt-F2 works for me again.

---

### Post by ArtLaForge on 2009-09-28
My update manager has 143 updates and some of them were not available, didn't want to do a partial update. So I will check tomorrow. Maybe that is all I need. Thanks for the info.

---

### Post by ArtLaForge on 2009-09-29
I ran the update manager, still says partial install, so I ran a partial and the ubuntu-desktop was kept back. Still do not have Alt F2 working. so perhaps the fix is in the ubuntu-desktop??? I'm not sure why this package was kept back, is there a way of finding out? I'm not that familiar with terminal commands that might indicate what the reason would be, any help would be appreciated.

---

### Post by meborc on 2009-09-29
if you are adventurous you could try ```
sudo apt-get update && sudo apt-get dist-upgrade
``` 
this will update the info and then try to do a dist-upgrade... a dist-upgrade is a more forceful way to upgrade (it is the way i do it)

just be sure to look if any packages gets REMOVED flag... if so it is up to you if you want to continue or not

sometimes there are packages that get removed because they are replaced with other packages (like the recent software-store replacement with software-center)

but just so i warned you - dist-upgrade'ing can bring your system to it's knees... but it can also fix some issues you are having ;)

---

### Post by Sophont on 2009-09-29
With
```
sudo aptitude safe-upgrade
```
you can get all the updates that are not held back. (after doing "sudo aptitude update" of course)

In addition - assuming you're not tight on RAM - I recommend installing VirtualBox (the OSE version is in the repo) and install another Karmic in a VM.

I always do the updates first on that VM version - if the most important apps still run and I can still restart the VM - then I follow up with doing the updates on the main version.

In general you should wait out held back updates - but sometimes you need them to get ahead. Testing them first on a VM ensures you avoid major breakage where it counts.

I did the ubuntu-desktop updates last weekend (after waiting for a week or so) - and it went ok.

---

### Post by ArtLaForge on 2009-09-29
> **meborc said:**
> if you are adventurous you could try ```
sudo apt-get update && sudo apt-get dist-upgrade
```this will update the info and then try to do a dist-upgrade... a dist-upgrade is a more forceful way to upgrade (it is the way i do it)

just be sure to look if any packages gets REMOVED flag... if so it is up to you if you want to continue or not

sometimes there are packages that get removed because they are replaced with other packages (like the recent software-store replacement with software-center)

but just so i warned you - dist-upgrade'ing can bring your system to it's knees... but it can also fix some issues you are having ;)

I'm adventurous! The text flew by, I did see software-store dependency issues. Booted up ok, but still no Alt F2 command prompt. Update manager says I am up to date. Thank You at least my update issue is taken care of. As for Karmic every thing seems to be running smooth. I can live with the hot key problem, Karmic release is just around the corner maybe the next update will take care of whatever that issue is. Thanks Again:)

---

### Post by meborc on 2009-09-30
> **ArtLaForge said:**
> I'm adventurous! The text flew by, I did see software-store dependency issues. Booted up ok, but still no Alt F2 command prompt. Update manager says I am up to date. Thank You at least my update issue is taken care of. As for Karmic every thing seems to be running smooth. I can live with the hot key problem, Karmic release is just around the corner maybe the next update will take care of whatever that issue is. Thanks Again:)


you should look into compiz hotkeys... if for example alt+f2 is used for something by goth gnome and compiz, none of them will work

i remember a friend, who put alt+tab up as the keybind to change keyboard language... of course the window changing did not work any more... i looked 2 days until i found the problem :D

---

### Post by ArtLaForge on 2009-09-30
> **meborc said:**
> you should look into compiz hotkeys... if for example alt+f2 is used for something by goth gnome and compiz, none of them will work

i remember a friend, who put alt+tab up as the keybind to change keyboard language... of course the window changing did not work any more... i looked 2 days until i found the problem :D

Checked the compiz hotkeys most of the hot keys were disabled I didn't see a Alt F2 at all. Don't know where to look for goth gnome hot keys, where would I find those? 

Thanks for the reply:P

---

### Post by meborc on 2009-09-30
> **ArtLaForge said:**
> Checked the compiz hotkeys most of the hot keys were disabled I didn't see a Alt F2 at all. Don't know where to look for goth gnome hot keys, where would I find those? 

Thanks for the reply:P

have you checked system-preferences-keyboard_shortcuts ? is alt-f2 set as it should be?

---

### Post by ArtLaForge on 2009-09-30
> **meborc said:**
> have you checked system-preferences-keyboard_shortcuts ? is alt-f2 set as it should be?

Just checked the keyboard shortcuts. I do not see anything listed for Alt F1 or Alt F2, Most of them are disabled.

---

### Post by ArtLaForge on 2009-10-04
> **meborc said:**
> have you checked system-preferences-keyboard_shortcuts ? is alt-f2 set as it should be?

The shortcuts were not listed in system-preferences-keyboard_shortcuts and I could not add them? Since it was not a big issue and beta was near I waited for beta and installed a fresh beta release, similar symptoms. The short cuts were listed in the keyboard conf but Alt F1 or F2 still didn't work. Borrowed a keyboard, rebooted and now everything is working fine.

---

### Post by ArtLaForge on 2009-10-04
It appears that Jaunty/Karmic do not recognize the Microsoft Digital Media Pro keyboard

---

