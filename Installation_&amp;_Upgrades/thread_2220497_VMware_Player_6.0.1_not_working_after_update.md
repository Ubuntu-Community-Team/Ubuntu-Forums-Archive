---
title: "VMware Player 6.0.1 not working after update"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by Fisher on 2014-04-28
Hi!
I was using ubuntu 13.10, and updated to 14.04
VMware Player was working fine, but now it starts up saing it needs to compile and load modules into kernel, then, it gives me an error when compiling Virtual Network Devices.
The log file: [http://pastebin.com/VEu2uJfr](http://pastebin.com/VEu2uJfr)
Could not find what is happenig.
Can someone please help?

---

### Post by stozz2 on 2014-04-28
Sounds to me that you need to go to your install the_ restricted extras_ these items are propitiatory software and are not open source.
So they are not installed automatically....

**It is also important for you to know that installing these restricted extras, may not be legal in some countries.**

Now Proceed and open up your Software Center

_You may need to edit your Software Sources_

Click Edit Menu or press [ALT] + [ E ] within the Software Sources 
And ensure that the **Software restricted by Copyright or legal issues (multiverse) **has been selected and has a tick beside it.
This is found under the Ubuntu Software Tab

Now Close that window and return to the Software Center  and preform a search for "_Restricted Extras_"
You should find these search results for : xubuntu; Kubuntu and Ubuntu...
Click on install for your Ubuntu Version

---

### Post by Fisher on 2014-04-28
Installed the restricted extras.
Same problem :-( ...

---

### Post by ubfan1 on 2014-04-28
uPDATE TO VMPLAYER 6.02

---

### Post by Fisher on 2014-04-29
Solved!!! Could not imagine it was THIS simple!!
Thanks!!!

---

