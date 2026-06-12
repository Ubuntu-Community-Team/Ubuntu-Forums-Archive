---
title: "Error message after attempt to install printer"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by Davis_Goertzen on 2014-09-13
I have an old Brother HL-1230 printer which I tried to install following the command line instructions from the Brother website. At first, it did not appear to work properly, but for some reason now it does; I'm not sure why. Some odd things are happening now, which I would appreciate help in solving.

- When I try to open the Ubuntu Softward Centre, it will bring up the screen and the logo as if it's trying to load the home screen, and then disappear.

- When I try to open Synaptic Package Manager, it asks for my password, and then before it loads the packages an error window comes up with this message:
E: The package hl1230lpr:i386 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

- In the top right corner to the left of my WiFi icon, there is an error symbol, and when I click on it, this is what it says:
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Unknown Error: '<class 'System error'>' (E: The package hl1230lpr:i386 needs to be reinstalled, but I can't find an archive for it.)'. This usually means that your installed packages have unmet dependencies


So if anyone can help me figure out what's happening and how to solve it, that would be greatly appreciated. This is on a laptop running Ubuntu 14.04, and the printer is connected with a cable which is parallel interface on the printer end and USB on the computer end.

Thanks.

---

### Post by Davis_Goertzen on 2014-09-13
After doing some Googling around, I believe I have found a solution to the problem. I used the command below to make a backup of /var/lib/dpkg/status.

> sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bkup

After that, I ran the following command to edit the file:

> sudo gedit /var/lib/dpkg/status

Following this, I did a search in the resulting file for "hl1230" and changed the status from "install reinstreq half-installed" to "install ok installed" manually.

Hopefully this helps anyone who encounters a problem like this in the future.

---

### Post by Bashing-om on 2014-09-13
Davis_Goertzen; Hey, hey !

Thanks for sharing your solution.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]1 for all
[INDENT][INDENT][INDENT][INDENT]and all for one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Davis_Goertzen on 2014-09-13
Quick update:
It turns out that I had to go back into that file I mentioned above and delete the group of lines associated with "hl1230" so I thought I would just mention that.

---

