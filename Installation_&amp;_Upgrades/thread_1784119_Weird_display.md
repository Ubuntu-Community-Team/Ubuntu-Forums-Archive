---
title: "Weird display"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by brokenlegguy on 2011-06-16
I don't think that this pertains is fixed by the graphics sticky because I can log in to the system.... so here's the story.

- I installed ubuntu 11.04 64 bit via the windows installer.
- changed display to dual screen
- installed some apps from the ubuntu software center
- installed ia32-libs and then xampp
- installed recommended graphics drivers. 
- *tried to display to dual screen told x server had to be restarted
- rebooted machine and logged in and main screen is white except for the docks and second monitor has a background image.
- tried to go to system settings and can't see the window to go to the graphics driver setting and revert back.
- I can open other apps and see them but I can't re-size.

What the heck? Obviously I'm a noob and am not sure about my next steps. Any assistance would be appreciated.


Thanks,

Ed

---

### Post by brokenlegguy on 2011-06-17
Okay, I've sort of solved it.

Here's what I did.
-  uninstalled/reinstalled ubuntu
- installed nvidia display drivers
-  clicked x server display configuration and made my changes to dual screen.
- clicked save to x configuration file and made sure that the merge check box was unchecked

Now I can use the main monitor again.
[B]
Here's the problems I'm having now.[/B]
- I can't move a program to the second monitor but I can move the mouse around on it.
- I can't have more than one program open at a time with out all the program windows going white. 

When I didn't have display divers installed I could do both of those things. Is there something I'm missing in the display driver configuration panel?

- Ed

---

### Post by blackmail on 2011-06-17
I also solved many of my own posts by myself, i feel you bro! anyway thnx for posting the answer though so that we can all benefit from it :D

---

### Post by brokenlegguy on 2011-06-17
Thanks blackmail. 

My biggest problem with my current issues I'm having is that I don't know what I'm looking for. So I'm not sure where to begin. We'll see what happens.  

If I find a solution or someone points me in the right direction I'll spell out the solution as before so it's easy to find for others. Actually I'll append both solutions to the first post or give a post number for reference.


- Ed

---

### Post by blackmail on 2011-06-19
One good advice would be:
I have seen many people on youtube having 3-6-9 and so on monitor configurations, so i think they got them to work somehow, try searching for some of those vids and ask around if they faced the same problem or if they can point you to the right direction.

BTW i also have had quite some problems with my Ubuntu 11.04 distro, i could not log in to the Desktop, the system halted at some point when loading the modules and there was all black, then with Ctrl+Alt+F2..6 i have tried TTYs and logged in with text mode and also tried to start the X server via /etc/init.d/gdm start and it did not help, so i rebooted in recovery mode and then i have installed the Gnome3 from the homepage and also installed the drivers from the nVIDIA site... now my computer works, but this unity thing just messed everything so badly up...

---

### Post by brokenlegguy on 2011-06-20
That's an avenue I didn't think of. I'll see what I can find out there. If I can't find anything I'll contact the authors of some of the videos to see what issues they ran into and what they suggest.

Thanks again man, I really appreciate the help.

 -Ed

---

### Post by brokenlegguy on 2011-06-20
The best that I seem to be able to do is to make Ubuntu believe that both monitors are one display by leaving the Configuration option on TwinView. 

When I had that set before, when I first installed Ubuntu, both monitors displayed the same thing. So I'm not sure why it's worked now. 

Is it because the Position option for both monitors where set to +0+0??

-Ed

---

### Post by blackmail on 2011-07-22
...strange are the ways of the Ubuntu OS...

Anyway does it work now, or can i be of any help?

---

