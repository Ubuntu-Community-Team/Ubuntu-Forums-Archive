---
title: "Boot stalls"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by maltopod on 2006-08-20
I start up the live cd and it works as everything should, i choose normal boot at the menu, and then it makes it past the mounting root filesystem screen, and starts to ok things, all this goes as it should until it gets to configuring network devices.  It stalls.  It just stops, no error message, no nothing, just never goes past this point. 
I am not entirely surprised that this is where it stops the motherboard has a built in nic that has never worked and caused all sorts of conflicts even with the original install of windows.
This is my first attempt at installing ubuntu, so i really dont know what i am doing, but after searching the forums i tried the acpi=off thing and it didnt make a difference.  
What shold i try?

---

### Post by meng on 2006-08-20
I'm not sure of the answer. If there's an NIC you're not using, the most it supposed to do is pause for a minute or less. Can you disable the NIC in the BIOS?

---

### Post by maltopod on 2006-08-20
Beautiful, that worked.  Thank you.  I should have done that long ago.  
But now it seems that the installation is freezing at 66% 
I dont know, i have tried it a couple times, but havent searched around to see if the answer is already said.  Thanks again.

---

### Post by meng on 2006-08-20
I've seen that complaint several times, but I don't know the answer to it. One wonders about a corrupted CD, or else maybe the Alternate CD is more appropriate for you.

---

