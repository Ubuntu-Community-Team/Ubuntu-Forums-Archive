---
title: "Cant install/boot from live cd or Flash drive"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by BSanders84 on 2010-08-17
Hello all as i am new to Ubuntu as well as this is my first post.

Here is my problem. 

I have made several live Cd's and img for my flash drive and tried to even preview Ubuntu before install, but nothing seems to be working. it makes it to the screen that says Ubuntu with the dots and the dots "cycle" then afew seconds later, weather cd or flash drive, everything just stops and my computer freezes. Tried nomodeset and everything i could find between here and google to no avail. cant get past that load screen. Ive been lurking on the forum for days and finally got fed up enough to post this because im fresh and have no clue what im doing when it comes to this. all i know is i want something better than windows(lol) and Ubuntu seems like its right up my alley... i am not the average comp. user, my "skills" if you will, are better than most, but Linux... its like trying to reed Greek for me. Any help would be most appreciated! Thanks in advance!

Also, computer specs...
Toshiba A505-S6025
4gb Memory
Nvidia GeForce 310M (from what i read i will have trouble with this)
Realtek RTL8191SE wlan (also will have problems with this)

If anything else is needed that i forgot or did not post, please let me know. i would love to get this running!!!



EDIT: just ran live cd with virtual box and it started the demo of Ubuntu with no problem with no options(like nomodeset) checked off... apparently i think im doing something wrong when it comes to booting the other way... please help guys!

---

### Post by lechien73 on 2010-08-17
The LiveCD will start up ok under VirtualBox - because an ideal "generic" environment is presented.

Can you disable ACPI in the BIOS? If not, you could try booting with the "noacpi nomodeset xforcevesa" switches.

---

### Post by BSanders84 on 2010-08-17
> **lechien73 said:**
> The LiveCD will start up ok under VirtualBox - because an ideal "generic" environment is presented.

Can you disable ACPI in the BIOS? If not, you could try booting with the "noacpi nomodeset xforcevesa" switches.

Thanks for your quick reply! when i boot with nothing ticked on the f6 menu, it hangs with a bunch of word lines on the screen. the only way for me to make it to the ubuntu "load"? screen with the dots is to tick everything. i dont have a option for xforcevesa, i could try that. but where to put it?

---

