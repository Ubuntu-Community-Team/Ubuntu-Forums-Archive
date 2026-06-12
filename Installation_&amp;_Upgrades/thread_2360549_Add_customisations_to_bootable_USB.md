---
title: "Add customisations to bootable USB?"
date: 2017-05-05
forum: Installation &amp; Upgrades
---

### Post by hotpocky on 2017-05-05
I dual boot Linux and Windows, specifically I use Win 7 and Gnome (for its customisation). So you know my level of experience, it took me a week to figure out how to install a downloaded package file. I have Linux and Windows on a bootable USB each, but I have used several commands to customise my installed copy of linux, and make it resemble Windows.

My question is: How do I edit a Linux bootable (or save command-based changes to the bootable when "trying it out before installing") so that either the changes I've made to my installed version apply to the bootable? If this isn't so easily done, something like as adding an item to the desktop that can be used to execute a string of commands is within my range of skill, apart from the "adding to the desktop" part, as that would require editing the installer to tell it to do that.

I can download the things that change the desktop and put them in their own directory, would the respective commands go in the "command" file? If so, what would the syntax be? Any help is greatly appreciated. Sorry if this is asked before, all I could find with my search terms was "How to make a Linux bootable USB" and other basic things that don't even come close to the level of customisation I'm looking for. Also, sorry if this is in the wrong section, I figured "Installation & Upgrades" was as close as it gets.

---

### Post by yancek on 2017-05-05
It isn't really clear to me from your post whether you want to make changes to the installed Ubuntu or to the "Live CD" of Ubuntu.  The Live CD, whether it is on a CD/DVD or flash drive is an iso9660 type filesystem which by design is read-only.  You can boot your Ubuntu DVD/flash and make all the changes you want and use them as long as you want as long as you have enough RAM and your hardware does not fail and you do NOT REBOOT.  When you reboot the Live medium, everything is gone, that's by design.

So if you want to have a Live CD on a flash drive with the same software and changes as the installed system, options available are Systemback and Pinguy Builder.  I think both are in the repositories but if not, can easily be located with an online search.

As to your last paragraph, I think you would have to be more specific about what you want to get help with whatever it is you want to do.

---

### Post by hotpocky on 2017-05-05
Sorry, I'm not the most straightforward of people. As it happens you're exactly right: I intend to alter the Live CD so the Live Medium has the same look as my currently installed version. It sounds like Systemback and Pinguy may very well be what I'm looking for. Thank you, I've got a little research to look forward to!

---

