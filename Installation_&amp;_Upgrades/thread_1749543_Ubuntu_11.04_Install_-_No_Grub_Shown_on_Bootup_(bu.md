---
title: "Ubuntu 11.04 Install - No Grub Shown on Bootup (but is installed)"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Astra on 2011-05-04
I am very much a newbie so please pitch responses at that level.

Have just installed Ubuntu 11.04, the system is to dual boot with XP.

Ubuntu is installed, have been into it and it seems to be working fine.  However, when I bootup the computer I get no "Grub!" [Grub is now going to take over the boot process textual alert]. And, once the system gets past that screen, there is no list of Operating Systems to boot choices. Just boots straight into Ubuntu - always.

Solved that by installing 'Startup Manager' (which I knew about from slight previous exposure to Linux) and set the default operating system to Windows XP - this means that now I can't get into Ubuntu.

How do I get Grub to show that 'Grub alert'? And how do I get Grub to offer choices of OS to boot in to?

---

### Post by tyrolian2 on 2011-05-11
I have a very similar problem that I partially solved and it might be of some help in your situation.  
Yesterday I upgraded my dual boot system to 11.04 and now I get no grub menu and it always boots into Ubuntu.  I never had problems before with grub after upgrades.  Anyway, right when the grub menu should appear my monitor says it is getting a bad video resolution.  This means the grub program is running but it is not displaying on the screen.

The trick is to pretend the menu is there and hit the right keys to make the menu selection.  Assuming your menu is anything like mine, Ubuntu will be the topmost selection and Windows will be the last selection.   When the grub menu should appear,  hit a bunch of up arrows (3 or 4) and then hit the enter key to select Ubuntu.  Hit a bunch of down arrows and then hit enter to select Windows.  Grub should give you 10 seconds to make your selection before it boots to the default.

If you get Ubuntu to boot, run Startup Manager and try a different video resolution for grub.

---

### Post by Astra on 2011-05-12
I did work out blind use of arrow-keys and then <Enter> when you think you're probably on the correct grub menu item.

Have now read several posts in a number of Linux forums on installing Grub2 to a small partition of its own - and not as part any Linux install. From there it can be used to chainload any OS, including Windows, with that OS using it's own boot-loading system to manage its own booting. Seems to me the way to go as then I only need to work out how to deal with the Grub2 sitting in its own partition - and I get to keep that for later use with any Linux distro I try later.

Think video issue is correct and thanks for tip on way to alter, didn't think of that myself. Now I'll see if I can find if there is a way to instruct Grub2 on its own partition to set res according to own preference.

For just now Ubuntu is off drive because of video driver issues in Desktop environment proper, difficult to do productive work with so low res and refresh frequency. (Did get an alert on install that there may be a video driver issue, downloaded appropriate NVIDIA driver but didn't fix issue. Will pursue how/if possible to get better, more accurate res option choices, and clean reinstall within the next couple of weeks.)

---------------

Now have a new, additional, hard-drive so in next few days can fully image off my first drive and have another go at installing Ubuntu with no worries if it doesn't work out first time - just restore the entire first drive in one fell swoop and back to base one to try again.

Thanks for reply.

---

### Post by deepaksharma on 2011-09-25
I solved the problem of no Grub Menu at Bootup in a Dual boot system with Ubuntu 11.04 and windows 7. Here is what I did.
In a terminal as sudo or root  edit the file /etc/default/grub un-comment the line that says #gfx640x480 by removing the #
then as sudo or root run the comand "update-grub" without the quotes.

thanks 
source: [http://melpctec.blogspot.com/2011/05/no-grub-menu-at-bootup-ubuntu-1104.html](http://melpctec.blogspot.com/2011/05/no-grub-menu-at-bootup-ubuntu-1104.html)

---

### Post by bossbruin on 2011-11-20
> **tyrolian2 said:**
> I have a very similar problem that I partially solved and it might be of some help in your situation.  
Yesterday I upgraded my dual boot system to 11.04 and now I get no grub menu and it always boots into Ubuntu.  I never had problems before with grub after upgrades.  Anyway, right when the grub menu should appear my monitor says it is getting a bad video resolution.  This means the grub program is running but it is not displaying on the screen.

The trick is to pretend the menu is there and hit the right keys to make the menu selection.  Assuming your menu is anything like mine, Ubuntu will be the topmost selection and Windows will be the last selection.   When the grub menu should appear,  hit a bunch of up arrows (3 or 4) and then hit the enter key to select Ubuntu.  Hit a bunch of down arrows and then hit enter to select Windows.  Grub should give you 10 seconds to make your selection before it boots to the default.

If you get Ubuntu to boot, run Startup Manager and try a different video resolution for grub.


This worked perfectly with me after numerous "terminal" fixes did not.  thank you

---

