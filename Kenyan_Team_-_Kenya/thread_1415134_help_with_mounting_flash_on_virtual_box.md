---
title: "help with mounting flash on virtual box"
date: 2010-02-24
forum: Kenyan Team - Kenya
---

### Post by kibaya on 2010-02-24
hi i need help on mounting my usb devises on vitual box in linux:confused:

---

### Post by trendseta on 2011-01-04
[LIST=1]
[*]Which version of virtual box are you using?
[*]Which Os are you using as host, and which one as guest?
[/LIST]

---

### Post by subchief on 2011-06-16
First start virtual box.
before starting the machine if its windows xp you want to run, click on settings and select shared folders.
click on the add icon and add a new shared folder. This should be your flash drive.
next save the settings and start the virtual machine.
install virtual box additions in the virtual machine by running setup from virtualbox iso image on my computer. this will usually be in the place of the cd drive of the virtual machine.
after installing the virtual box additions or if already installed,click on start menu and open the run icon.
then type

\\vboxsvr\sharename

where share name is the name of the flash disk!!!
This should open up the usb drive.

alternatively,

open Windows Explorer and look for it under “My Networking Places” -> “Entire Network” -> “VirtualBox
Shared Folders”. By right-clicking on a shared folder and selecting “Map network drive”
from the menu that pops up, you can assign a drive letter to that shared folder.

Hope that helps!!

~subchief~;)

---

