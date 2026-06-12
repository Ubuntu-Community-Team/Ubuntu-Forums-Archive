---
title: "My livecd wont go past partion part??"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by SenorGeltabz84 on 2008-09-26
My dumb brother messed his pc up so I tried installing gutsy on it and it just wont go past the part where it asks for keyboard type. It finishes partition load bar then freezes. I left it over night to see if it was his computer, nothing. So i used live cd and tried g parted and nothing (froze again). I tried burning an .iso and just booting from BIOS and still nothing. I'm lost !

---

### Post by robert shearer on 2008-09-26
Lets start with some more info so we can help you.

What PC are you trying to install Ubuntu onto? 

What Ubuntu cd are you using? (does it have a GUI desktop when you boot it up or does it bring up a blue screen with text?

Do you have internet access for downloading large files? (You are trying to install Gutsy 7.10 and the current version is Hardy 8.04.1) 
You may need to download a newer version with better hardware recognition and support.

So, post back this info and we can plan the next move.

---

### Post by prshah on 2008-09-26
> **SenorGeltabz84 said:**
> 
I tried installing gutsy on it and it just wont go past the part where it asks for keyboard type. It finishes partition load bar then freezes. 

Few things to check:

[indent]a. Prior to 8.04, SATA drivers are not included in the distribution. So maybe the partitioner is freezing since it cannot detect your SATA HDD. Obviously this will affect you only if you're running a SATA HDD. You can check if any HDD/partitions are detected with the command```
sudo fdisk -l
``` from the terminal (Applications-Accessories-Terminal). If you have an IDE HDD this does not apply to you.

b. Do you have any bad sectors? If, when the install freezes up, the HDD light on the tower is burning constantly (steady, not blinking) for over 5 mins, this is a bad sign and can be a symptom of bad sectors. If this is your case, post back for a resolution.

c. Can you tower's processor be overheating? Check if the system fans are running (Physically check this by opening up the tower and turning on the system). If your BIOS supports it, check the processor temperature in the BIOS.

d. Is there any particular reason you don't want to use Hardy? As the latest, and as a LTS, it will be a better choice.[/indent]

Post back if none of the above seem to apply.

---

