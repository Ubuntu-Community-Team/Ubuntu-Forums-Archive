---
title: "Upgrade problems 9,04 to 10.x"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by abucksdiver on 2010-05-19
Hi, 
Last night I tried to upgrade from 9.04 to the latest 10. version on my Acer TravelMate C302XMi laptop. (This was from the "Upgrade to 10" link in the updates manager).

However, after completing, the laptop will not boot. It starts to start up, but then I get the message "Acer- WMI: No or unsupported wmi interface, unable to load."

After a few seconds, it then reports "Starting up".

It briefly displays the the graphical Ubuntu screen with the dots beneath the logo.

Then the screen goes blank, and nothing further happens...

Any suggestions on how I can get the laptop to work again?

Many thanks

---

### Post by GEZEN Foundation on 2010-05-19
The quickest way is to do a clean install and put back your backed-up data.

Before upgrading your system always back-up your:

1 - (created) documents/pictures/music/etcetera
2 - e-mail (both Evolution and Thunderbird provide funtions to export all of your stored mail and easily import it on fresh/other systems)
3 - bookmarks
4 - usernames, passwords, registration- and serialnumbers.

Ubuntu installers create one big combined system/boot and data partition as standard ( I think this is very very wrong, just like Windoze does it) 

Wise people created a separate DATA-partition where they store all your own files. Even "MyDocuments" can be linked to a directory on the DATA-partition then.

After you do a clean install (with the same partition selected for boot and system), your DATA is still there. You only have to put  back your item 2,3,4 back-ups.

---

### Post by abucksdiver on 2010-05-19
Isn't hindsight wonderful :-(

---

### Post by abucksdiver on 2010-05-19
It may be too late considering that the laptop died after my attempted upgrade last night, but how do I back-up the passwords/usernames/registration/serial nos?

Thanks

---

