---
title: "Switch from 64-bit to 32-bit"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Foxtrots on 2010-04-19
Is this possible, I'm a noob, 1 day user. I already have the 32 Bit LIVE Cd Burned. I want to install using the same partition my 64-bit is installed on. Could someone give me steps please. Thanks

---

### Post by Slim Odds on 2010-04-19
> **Foxtrots said:**
> Is this possible, I'm a noob, 1 day user. I already have the 32 Bit LIVE Cd Burned. I want to install using the same partition my 64-bit is installed on. Could someone give me steps please. Thanks

You can't "switch". You can reinstall. I'd download the 64 bit if I was you.

Are there any details that you're leaving out that we should know?

---

### Post by Water_Spirit on 2010-04-20
> **Foxtrots said:**
> Is this possible, I'm a noob, 1 day user. I already have the 32 Bit LIVE Cd Burned. I want to install using the same partition my 64-bit is installed on. Could someone give me steps please. Thanks
 
Can you give some more detail on what you are trying to do ie; what is the existing 64 bit.

---

### Post by Foxtrots on 2010-04-20
I have 9.10 64-bit installed. I'm trying to reinstall 32-bit. I want to install using the partition I already have 64-bit installed on.

---

### Post by P4man on 2010-04-20
Why would you go back to 32 bit?
Anyway, unless you created a seperate /home partition, then your only option is a complete reinstall, so back up all your data. Boot from the CD, and then you can install using the same partitions by selecting the advanced partition setup during installation, and selecting the same partition as your new "/" (root). You will lose anything on it.

---

### Post by Cabs21 on 2010-04-20
> **Foxtrots said:**
> Is this possible, I'm a noob, 1 day user. I already have the 32 Bit LIVE Cd Burned. I want to install using the same partition my 64-bit is installed on. Could someone give me steps please. Thanks


64-bit machines can use 32-bit software but 32-bit machines can not use 64-bit software.  That being said.  Put the install LIVE CD in the drive, and follow the step by step install procedure for the simplest install.  If you want more complex install follow the guides on the web site.

---

### Post by Foxtrots on 2010-04-20
I can't get my wireless to work on 64-bit and I read somewhere that it might work on 32-bit. I'm going to try that when I arrive home P4man.

---

### Post by P4man on 2010-04-20
Seems unlikely 32 bit would help you. But feel free to boot from the CD, select a live session and test. If (as I suspect) it doesnt work, then there is no point reinstalling. Instead, let us know what wifi card you have. If you dont know, from a terminal type:

```
lspci
```

(if its an internal card). Or

```
lsusb
```

(if its a usb wifi stick)

And copy paste the output here. Precious few wifi cards cant be made to work with ubuntu.

---

### Post by Foxtrots on 2010-04-20
Its an old D-Link. DWL-G132. I installed ndiswrapper got it installed ran ndiswrapper -l it was present just could never get it to detect the router.

---

### Post by P4man on 2010-04-20
> **Foxtrots said:**
> Its an old D-Link. DWL-G132. I installed ndiswrapper got it installed ran ndiswrapper -l it was present just could never get it to detect the router.

Ugh.. a quick google seems to indicate that its one of the worst wifi sticks you can get for linux. 

Anyway, if you use ndiswrapper on 64 bit ubuntu, you must also feed it the 64 bit windows drivers. If there isnt one, then maybe reinstalling 32 bit ubuntu could be part of a solution, then use 32 bit windows drivers in ndiswrapper and hope for the best. But frankly I see so many negative reports, i wonder if you're not better off buying a new usb wifi stick that is properly supported. They cost next to nothing.

---

### Post by Foxtrots on 2010-04-20
I know, I think I'm going to buy a new one soon. I'm going to try this if it works I'll use it if not, back to 64. Thanks thought P4man.

---

