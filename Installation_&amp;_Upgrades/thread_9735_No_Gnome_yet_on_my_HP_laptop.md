---
title: "No Gnome yet on my HP laptop"
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by Mira on 2004-12-31
I must say...I love how the install looked...no bells and whistles and few questions, made it hard not to drool on the keyboard. ;-)

But to the point....I have a laptop, a HP pavillion zv5330EA, with nvidia stuff in it...geforce4 videostuff and nforce2 sound and the unavoidable RTL8139 ethernet.
My experience with linux is a few distro's of Mandrake and Debian. I got Debian on my desktop puter...I wanted something different for my laptop..
I tried Gentoo....and hated it from the part the disc booted it and gave me just a prompt with no explaination. Shoved in Mandrake...it gave great bells and whistles which worked perfectly until the install finished and gave me no mouse or touchpad and shortly after garbled the screen. 
Urgh!

Now Ubuntu looked very smooth until..........the sys rebooted and gave me prompt.
I typed startx...command unknown..too bad...gdm neither...urhm..
I typed in apt-get gdm..to see what would happen...receiving the strange sensation of the realization that the install never asked me for a root password......and therefore wasn't surprised to get the response I had no permision to apt-get anything

So I searched this forum and saw the advice to "sudo passwd root" to set password. Sad enough it asked me password instead of leting me set it.

So now I need to know 2 things...

First things first: How do I set password without doing it the hard way with using instal disc again, recovery blabla. 
I want root. I need root. Must have root. Please help me get root!

Second....since I see no others with the prob of having prompt instead of GUI, is it a prob that I should compile nvidia drivers? Should I compile the kernel as well perhaps to get it exactly right? Or do I just need to apt-get something else?

Pretty please with sugar, chocolat chips, rum and a cherry on top.....oh and whipped cream ofcourse! :-)

---

### Post by NewbieNik on 2004-12-31
Mira,

I'm new to this myself, but I hope I can shed some light for you and if I'm wrong then people will correct me!!!

First off...No root user needed, using the SUDO (Super User DO) will run the command effectively as root. The password you need to enter is *your* password, not roots.
Not using root as a user is the main security benefit of Linux.

Second off, I have read that there were some issues with Nvidia drivers. Try searching the forums for Vidia and you will see plenty of help.

Hope you enjoy Ubuntu as much as I do when you're up and running!

---

