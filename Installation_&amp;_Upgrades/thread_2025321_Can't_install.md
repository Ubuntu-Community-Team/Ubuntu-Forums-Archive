---
title: "Can't install"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by timbo59 on 2012-07-14
We recently bought an older PC (Dell Optiplex GX520) with the idea of setting it up in our daughter's room for her to play on - there's a host of games available for Ubuntu which she loves, given that I've downloaded some of them on my own Ubuntu-driven PC. Only problem is that she now wants to monopolize that computer to play on - silly move on dad's part! Hence the notion of loading Ubuntu on to the other PC!

Problem is, I can't get Ubuntu to install on this particular PC no matter how hard I try. I can't for the life of me remember how I installed Ubuntu on my other computer, though I know I did it via a disc I burned, so I'm assuming I did it via a standard boot install. Well I can't do it on my daughter's PC.  It requires that I get into BIOS and reset the initialization to boot from the external CD drive that's attached, but the BIOS security won't let me, because someone has set a password on it. We bought the unit from a company liquidation sale, so there isn't a hope of finding anyone to tell us what the password is. Alternatively I've tried to see if I can install from within the Windows XP environment that's on board the computer and run Ubuntu side by side with Windows, but that doesn't work either. Every time I try initializing from the disc I get the following error message - D:\wubi.exe This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem.

My first preference would be to wipe XP altogether and do a clean install with Ubuntu. The second would be some kind of install from within XP. Can someone point the way on how I can solve this issue?

Thanks............Tim

---

### Post by dino99 on 2012-07-14
the best place about this pc is the Dell subforum here on ubuntuforums
but as the bios is paswword protected, you should ask the Dell support forum to bypass the protection and maybe flash the bios.

but you should be able to install via wubi, maybe using some boot option (search about "ubuntu boot option" on google)

---

### Post by Cheesemill on 2012-07-14
You can clear the BIOS password:
[http://support.dell.com/support/edocs/systems/opgx520/en/ug/advfeat0.htm](http://support.dell.com/support/edocs/systems/opgx520/en/ug/advfeat0.htm)

---

### Post by black veils on 2012-07-15
> **Cheesemill said:**
> You can clear the BIOS password:
[http://support.dell.com/support/edocs/systems/opgx520/en/ug/advfeat0.htm](http://support.dell.com/support/edocs/systems/opgx520/en/ug/advfeat0.htm)


you cant do anything until the bios is dealt with ^  scroll to the section 
**[SIZE=3]Clearing CMOS Settings[/SIZE]**

---

### Post by timbo59 on 2012-07-15
Hi again,
             Okay, I went to the site suggested and read up on the bit about removing the appropriate pin on the board to clear the password - only problem is that I can't find a pin anywhere on the board! Any suggestions on it's location?

Thanks again.............Tim

---

