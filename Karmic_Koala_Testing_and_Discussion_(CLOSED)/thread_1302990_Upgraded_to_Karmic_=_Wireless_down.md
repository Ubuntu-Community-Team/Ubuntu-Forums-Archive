---
title: "Upgraded to Karmic = Wireless down"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sweetafton on 2009-10-27
Having just updated to the beta of KK from JJ, I notice I no longer have wireless. A run of lshw -C network gives me (I can't copy it directly, as without wireless internet on the computer I have no internet, so I'm using a different computer and will paraphrase): 

*network UNCLAIMED
description: Ethernet cont.....
product: AR5001 Wireless Netw....
vendor: Atheros Communications Inc.
etc.

Wireless worked for me out of the box in JJ. Any ideas?:confused:

---

### Post by B!aine on 2009-10-27
I had a similar problem when I did the same thing.  My solution was to go back to 9.04 and wait for the final release of 9.10.  If it still has issues, I will fight that then.  Sorry for not being any real help.

---

### Post by sweetafton on 2009-10-27
Was thinking that. Guess I might have to just revert and wait 2 damned days!! :D

---

### Post by mavros on 2009-10-27
Did you have a look under administration ->  hardware drivers? You might need one. I have a broadcom wireless card and that that only worked after I loaded the propriety driver B43.

When you can get a wired connection for a moment you can download and activate it. You can also download it on another computer and copy and install.

---

### Post by sweetafton on 2009-10-27
The proprietary drivers list is empty.

---

### Post by sweetafton on 2009-10-27
If I wished to go back to Jaunty, is there any alternative to a wipe/reinstall? I would then lose all the programmes I installed. :(

---

### Post by anewguy on 2009-10-27
2 questions;

- do you have the Windows driver for the wireless adapter, perhaps on CD?

- do you have a copy of the 9.10 LiveCD or install media?

Dave :)

---

### Post by sweetafton on 2009-10-27
-1: Likely lost in the mists of time and clutter, but I'm sure I can download it somewhere...
-2: I did an upgrade. I only have the 9.04 live disk.

---

### Post by anewguy on 2009-10-27
Try this:

- open a terminal window (applications/accessories/terminal)

- type:

cd /etc/modprobe.d <press enter>

sudo gedit blacklist-ath_pci <press enter>

find the line that says:

blacklist ath_pci

add a "#" to the front of that line so it looks like:

#blacklist ath_pci

save the file, exit the editor and reboot.  Then check to see if your wireless is working.  Reason:  found thread on the net that the Atheros driver never gets loaded (madwifi - for your AR5001) because of the blacklist added in 9.10.  The "#" just comments it out, so the driver is loaded.

Dave :)

---

### Post by sweetafton on 2009-10-27
:popcorn:

---

### Post by anewguy on 2009-10-28
Ok, color me really stupid - did it work?  If so, great!  If not, let us know and we'll try some more.

Dave :)

---

### Post by sweetafton on 2009-10-28
Sorry, yes it worked. I had an unrelated keyboard problem. (damn ps/2) so had to reply via smilie! :KS

---

### Post by anewguy on 2009-10-28
Glad it worked for you.  If you would, please marked the thread as solved, since Karmic is being release there will probably be many people running into similar problems, and this could help them as well.

Dave :)

---

