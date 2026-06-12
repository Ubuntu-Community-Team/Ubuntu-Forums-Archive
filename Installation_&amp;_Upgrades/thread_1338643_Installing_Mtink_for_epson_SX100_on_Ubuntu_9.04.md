---
title: "Installing Mtink for epson SX100 on Ubuntu 9.04"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Nightstrike2009 on 2009-11-26
Hiya everyone,

I have made progress with enabling ink monitors for my sx100 printer so far I have:

Downloaded and Installed:
[COLOR="Green"]
mtink_1.0.16-1_i386.deb
lesstif2_0.95.0-2.1ubuntu1_i386.deb[/COLOR]

Sorted out how to change necessary permissions below:

Then Hold ALT + F2 Keys "Run Command" Window should appear.

code:
sudo Nautilus

Then Click "Run"

Window should now appear in red marked "Root - File Browser" at the top.

Click Filesystem/Dev/Usb/lp0

When lp0 is highlighted, right click "Properties" form menu.

Where Menu displays "Others" , change "Access" from "None" to "Read & Write"
then click "Close"

Then Hold ALT + F2 Keys "Run Command" Window should appear, select
"Run In Terminal Box".

code:
sudo adduser 'username' lp

Note: username should be your username and quotations are neccessary.

Enter root password when prompted.

Reboot Ubuntu 9.04

Go To Menu>Accessories>Mtink
Click "Preferences" Button, Select "Port choice" (/dev/usb/lp0) & "Printer Choice"

Selected port choice as: /dev/usb/lp0

[COLOR="Red"]Then I have got to printer choice and sx100 is not on the list. any idea which printer to select? :([/COLOR]

I believe this is the final stage and Its annoying me that printer is not selectable after all this.

---

### Post by Nightstrike2009 on 2009-11-26
Failing this can anyone suggest a different ink status monitor that works for Epson Sx100 on Ubuntu 9.04?

Its one of the reasons i still use windows and would like to get shut of windows and run ubuntu.

---

### Post by Nightstrike2009 on 2009-11-26
Ive also tried the "escputil" Program:

[COLOR="Green"]escputil_5.2.3-0ubuntu5_i386.deb[/COLOR]

Code:
sudo escputil -i -r /dev/usb/lp0

in the terminal, it should output remaining ink level in terminal but it doesn't


For gods sake I just want to check my ink levels on my printer why does this have to be so hard in ubuntu?

PS: My epson SX100 is detected and can print from openoffice writer

---

### Post by Nightstrike2009 on 2009-11-26
UPDATE: Thread renamed from "Installing Mtink for epson SX100 on Ubuntu 9.04" to "Installing Ink Levels Monitor for epson SX100 on Ubuntu 9.04"

As long as I can get this to work I am not bothered which program I use now. :(

---

