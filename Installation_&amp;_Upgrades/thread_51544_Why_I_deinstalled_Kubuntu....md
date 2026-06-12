---
title: "Why I deinstalled Kubuntu..."
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by mortoray on 2005-07-24
I recently installed Kubuntu (AMD64 version) to try out the distribution.  Below I list the reasons why I decided not to continue using Kubuntu (after several days of working with it).  This is not meant as a flame, but rather some insights as to what may turn away other users as well.

In no particular order:

- different root/user mode which is confusing at first, and hard to switch if not liked:
--"Run as root" prompts are asking for user password (non-intuitive)
--if a user doesn't have admin permission, all links inside KDE to admin utilities fail (since it is trying to sudo as existing user)
--cannot revert easily to traditional setup, where KDE links run as root with root password and non-admin users can still click the links

- cannot add a printer: enter "Admin mode" on printer manager still does not allow the adding of a printer, I had to su in a commad prompt and then run the print manager to get that option enabled

- Initial setup produced a non-working system.  Incorrectly determined/configured the Radeon Express 200.  While this isn't strictly kubuntu's fault, it nonetheless is annoying.

- required typing special boot parameters to startup (acpi=off in this case), but didn't seem to provide any instructions on boot about how to do it (assumed previous kernel knowledge)

-Sound system continues to get a CPU overload message with a standard install

-KDM login isn't offering Gnome login session even though gnome is available

-Kynaptic shows no progress bar or display while downloading/installing

-very unstable firefox, and the wrong firefox version number

The things I did like are:

-integration of 32bit apps in the 64bit environment (like OpenOffice)

-a clean desktop/start menu (though the organization in the menu is kind of weird)

---

### Post by Soulfly on 2005-07-24
[QUOTE=mortoray]
- different root/user mode which is confusing at first, and hard to switch if not liked:[/QUOTE]

Do you mean the administrator mode? Where did you find the button to activate that ?  I cannot find the "button" im required to press.

---

### Post by ThatRickGuy on 2005-07-24
> 
- different root/user mode which is confusing at first, and hard to switch if not liked:
--"Run as root" prompts are asking for user password (non-intuitive)
--if a user doesn't have admin permission, all links inside KDE to admin utilities fail (since it is trying to sudo as existing user)
--cannot revert easily to traditional setup, where KDE links run as root with root password and non-admin users can still click the links


I have similar feelings. Another annoyance with security is setting things up. I should not have to open a terminal to sudo just to copy/move/delete a file. I should be able to set up some sort of power user account that I can manage installations with, or better yet, if I try to do something my account can not do, prompt me for either another account, or the sudo password.

The one that annoys the crap out of me is that there is no default, easily accessed way to open Nautalis consistantly. One dispaly is shown if I open a file browser, another is shown if I right-click and hit open folder. What ever the settings are should be consistant no matter how Nautalis is opened. Also, the search feature should be built into nautalis, not an entirely seperate thing in a different menu. I know these are Nautalis' (not Ubuntu's) faults, but it's wrapped up under the Ubuntu label to the end user.

Other show stoppers include driver support. I'm running vesa drivers on a $300 graphics card. I have no sound for my onboard ACC 97 sound proc. I didn't even attempt to install the printer. I can't see my proc or MB temp feeds. Again, not Ubuntu specific, but still under the Ubuntu banner from the end user's point of view.

> -very unstable firefox, and the wrong firefox version number

Agreed! Clicking in the address bar doesn't highlight everything, opening a new tab (ctrl-T, or right clicking and selecting open in new tab) crashes ALL open FF browsers. 

Anyways, many frustrations. I was hoping I could have a stable environment to get into some development using Mono, but it looks like I'm going to have to wait for another few releases to feel comfy with the environment.

-Rick

---

### Post by ThatRickGuy on 2005-07-24
Oh, and another odity. What ever was the last thing displayed, is displayed under some gabled text before the login screen loads. IE: If I'm in XP, reboot and goto Ubuntu, the first GUI I see is the desktop color from XP. If I get into Ubuntu/Gnome and have a few terminals open, a FF browser and a file browser open, and then type sudo shutdown -r now in a root terminal, when the GDM loads, I will see that exact desktop for about 3 seconds befor the login screen.

-Rick

---

### Post by wh0rd on 2005-08-11
I've recently switched to KDE from Gnome and it seems Gnome was more smooth than KDE. This includes wireless managers, login managers, etc...

---

