---
title: "Corrupted update?"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by tardis40 on 2010-07-22
I have a Dell XPS 64 bit with a dual boot - Vista and and Ubuntu 9.10. It has an nvidia graphics card.

I checked the update to 10.04 with Update Manager and toward the end of the installation I received an error message it wasn't able to complete the update.  It appeared to try to reverse the installation.

Before "reversing" I got to the point to telling it to use the package maintainers version of menu.lst

The grub menu at startup shows both Windows Vista and several kernals.  Vista starts normally when selecting Windows.

However, when selecting the latest kernel (or any kernel for that matter) I end up at a tty login of user and password input and then ends up at a command line.  I then must type startx to get to the window gui.

When in the gui I can confirm that it's running 10.04 and there is an nvidia option under Administration. I've updated the nvidia drivers from nvidias web site.

When I try to start Hardware from Administration, it doesn't load.  And if I try to run Update manager and answer yes to the updates I get errors about dependancies.

I'm new to Ubuntu so I have no idea how to get the old window gui on startup like I had in 9.1.  How do I? I assume there's an issue with the graphics card.

Also, I thought 10.04 used a new grub2 but when I go to the old grub menu.lst and modify it, that is what is showing on startup of the computer.

Any and all help appreciated.

Larry

I should have also noted that a LiveCD runs fine and the gui on my computer looks like the old 9.1 rather than the 10.04 liveCD.  Also, when the computer starts a purple screen is displayed that simply says Ubuntu 10.04 and some dots under it. Then it goes to tty.

---

