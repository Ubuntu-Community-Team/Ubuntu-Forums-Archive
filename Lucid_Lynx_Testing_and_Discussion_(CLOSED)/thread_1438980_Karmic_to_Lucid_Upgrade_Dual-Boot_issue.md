---
title: "Karmic to Lucid Upgrade Dual-Boot issue"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jeff May on 2010-03-25
Soooooo . . . I did a update-manager -d upgrade of my Karmic installation to try out Lucid Lynx Beta 1.
 
My first impressions are pretty good overall, much faster boot times, a cleaner more up-to-date look, some nice integrated functionality, etc. Window control buttons on the left are going to take a little getting used to.
 
My machine is a dual boot install with Windows 7 pro on sda1/sda2 (Win 7 installs a small boot partition) and Ubuntu on sda5. I've been running Grub2 since installing Karmic.
 
After the upgrade Ubuntu would load without problem, but I was no longer able to access my Windows 7 installation from the Grub menu. Selecting Windows 7 would simply reload the Grub menu. I looked at /boot/grub/grub.cfg and everything appeared to be correct. A little more fishing around showed that grub-install had overwritten the Windows bootloader on sda1.
 
The fix was to re-install the bootloader and update the MBR by booting from the Windows 7 CD, going to the repair utility, and from a command prompt issuing the bootrec /fixboot and bootrec /fixmbr commands. Of course, this results in booting directly to Windows so I booted Ubuntu Live from my Karmic CD and did a grub-install to sda5.
 
Back up and running 100%.
 
I've seen reports of this in various places, so I don't think I'm alone.
 
 
 
System: Asus / AMD Dual-Core (Windsor) / Dual-Boot Win7 pro 64 / Ubuntu Lucid Beta1 64

---

### Post by quixote on 2010-03-26
You may want to mark this "solved" since you did a nice job of explaining the fix for a problem that shouldn't be happening.  It does because the grub default is to load in the MBR, which overwrites whatever is there, which is D. U. M. B. beyond belief.  There's an option --which should be the default!-- to install grub to the ubuntu boot **partition** (sda5 in your example).  Then this sort of thing wouldn't happen.

Anyway, for those who hate the new button placement as much as I do (I mean *Why?*  What for?  What purpose does it serve?  Except to annoy the user with having to relearn years' worth of muscle memory just to perform *the same exact task*!) this is how you fix it:

--start gconf-editor. If you don't have it, install via synaptic.  
--go to /apps/metacity/general/button_layout.
":" indicates placement.  eg
```
:minimize,maximize,close
``` means buttons on the right, in the order given
```
menu:minimize,maximize,close
```means menu on the left, buttons on the right.

---

### Post by Jeff May on 2010-03-26
> **quixote said:**
> You may want to mark this "solved" since you did a nice job of explaining the fix for a problem that shouldn't be happening. It does because the grub default is to load in the MBR, which overwrites whatever is there, which is D. U. M. B. beyond belief. There's an option --which should be the default!-- to install grub to the ubuntu boot **partition** (sda5 in your example). Then this sort of thing wouldn't happen. 
 
Point taken. I don't understand AT ALL why this should have happened when using the update-manager -d method of upgrading a previous version.
 
That's very broken, as far as I'm concerned.
 
 
> **quixote said:**
>  Anyway, for those who hate the new button placement as much as I do (I mean *Why?* What for? What purpose does it serve? Except to annoy the user with having to relearn years' worth of muscle memory just to perform *the same exact task*!) this is how you fix it:
 
--start gconf-editor. If you don't have it, install via synaptic. 
--go to /apps/metacity/general/button_layout.
":" indicates placement. eg
```
:minimize,maximize,close
``` means buttons on the right, in the order given
```
menu:minimize,maximize,close
```means menu on the left, buttons on the right.
 
 
Yea . . . I'm sort of wondering why we're bothering to move something that works perfectly well where it's been for a long time. I still haven't heard anybody come up with a good reason for it.
 
Are we just trying to be "un-Windows"?

---

### Post by quixote on 2010-03-27
> very broken
Yup.

> Are we just trying to be "un-Windows"? 
As far as I can tell, double yup! :rolleyes:

---

### Post by QLee on 2010-03-27
[QUOTE=quixote]Yup.


As far as I can tell, double yup! :rolleyes:[/QUOTE]

I'm going to guess that you guys don't use Apples, eh?

Further, I'm going to guess that you've not used any old GNU/Linux software, ones that had the icons on the left, some also had scroll bar on left.

---

### Post by quixote on 2010-03-27
You guess wrong.  I used Macs in the early 1990s, and intermittently ever since.  Some critical software in my field (evolutionary biology) was available primarily on Macs.  And as for old Linux: the first computer I learned to use was Unix System 5, and I don't mean Release 5.  That was Release 1.  I used graphical windowing systems first on a Sun system sometime in the 1980s, used Silicon Graphics systems, and either three or four (can't remember) different flavors of Linux after that got under way.

That still doesn't mean I think it's a good idea to push buttons around just because you can.

(To be clear: they can put the buttons wherever they want and MAKE THE SETTING CUSTOMIZABLE.  We should all be able to have our own desktops set to our own preferences!)

---

### Post by QLee on 2010-03-28
[QUOTE=quixote]You guess wrong.  I used Macs in the early 1990s, and intermittently ever since.  Some critical software in my field (evolutionary biology) was available primarily on Macs.  And as for old Linux: the first computer I learned to use was Unix System 5, and I don't mean Release 5.  That was Release 1.  I used graphical windowing systems first on a Sun system sometime in the 1980s, used Silicon Graphics systems, and either three or four (can't remember) different flavors of Linux after that got under way.

That still doesn't mean I think it's a good idea to push buttons around just because you can.

(To be clear: they can put the buttons wherever they want and MAKE THE SETTING CUSTOMIZABLE.  We should all be able to have our own desktops set to our own preferences!)[/QUOTE]

Ah, I understand now. Since they are already customisible, you're referring to GUI customisible. Somewhat of an uncommon opinion from someone of your vast experience, usually us older GNU/Linux experienced guys aren't as concerned with someone else making things easy from a GUI.

My point, which wasn't made well, was that the choice to have the buttons on the left is neither unique to Ubuntu nor "new". Since you've been around a while, you will have seen the phrase, Linux is about choice. I don't think they changed it just because they could, I think some people might like it the way it is now.

---

### Post by quixote on 2010-03-29
I don't have that much experience in computers.  But I've spent most of my life teaching biology in universities, and I really do have vaaast experience about presentation of information and usability.

Linux is about choice indeed.  We're pretty good on CLI choices, but, face it, that's near-irrelevant for someone from the Windows or the Mac world.  If you're at all concerned about ordinary users or new users (and I'm one of these people who wants Linux on every phone and computer) then you want to make it easier for *everybody*.  Not just devs and geeks.  How hard would it be to program in a simple right-click choice?

(Did you ever see IBM's old OS2?  You could customize everything to your own liking, without ever editing a config file.)

---

