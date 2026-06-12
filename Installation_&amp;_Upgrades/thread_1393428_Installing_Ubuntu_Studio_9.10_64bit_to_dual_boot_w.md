---
title: "Installing Ubuntu Studio 9.10 64bit to dual boot with existing windows XP OS"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Miscible21 on 2010-01-29
Im so confused.

I have been using ubuntu for a little while so i'm not a total newbie. But im not very confident with installing the latest verion of ubuntu studio. Previously i upgraded to ubuntu studio through the terminal window from Jaunty. This time i want to do a fresh install via a DVD. I tried earlier but the part im confused about is the partitioning and formatting process. I have 2 hardrives. One of my hard drives has my XP OS on it along with my entire life. So I cant afford to make a mistake. The other has an older 32bit version of ubuntu studio on it. 

I have looked online but I havent found much help. What i was thinking of is just unplugging my windows drive, doing a fresh install on the other. But then i wouldnt know what to expect when i boot up and plug in the XP drive.

I would be so grateful for some detailed help. Thankyou in advance.

---

### Post by kansasnoob on 2010-01-29
> What i was thinking of is just unplugging my windows drive, doing a fresh install on the other. But then i wouldnt know what to expect when i boot up and plug in the XP drive.

That is actually a very good idea. Then if BIOS and/or cabling is set so that the Ubuntu drive boots first, and if this install has grub2, adding Windows should be as simple as running:

```
sudo update-grub
```

---

### Post by raymondh on 2010-01-29
+ 1 if you really want to make sure you don't touch your win HD

---

### Post by Miscible21 on 2010-01-29
> **kansasnoob said:**
> That is actually a very good idea. Then if BIOS and/or cabling is set so that the Ubuntu drive boots first, and if this install has grub2, adding Windows should be as simple as running:

```
sudo update-grub
```

Thank you so much! i have an idea that that would work too. I can check and change the BIOS setting if neccessary. BUt im a little unsure of how my cabling should be set, and im uncertain about grub2. If you could elaborate a bit i think it may help me understand. But again, thank you so much!

---

### Post by raymondh on 2010-01-29
> **Miscible21 said:**
> Thank you so much! i have an idea that that would work too. I can check and change the BIOS setting if neccessary. BUt im a little unsure of how my cabling should be set, and im uncertain about grub2. If you could elaborate a bit i think it may help me understand. But again, thank you so much!

Let me ***try*** to pick-up on KansasNoob's suggestion ....

Look at how your HD's are connected to the board.  

If both HD's are connected DIRECTLY to the board, then just unplug the win HD.  That means that the ubuntu install will happen ONLY to the remaining HD and GRUB2 (the bootloader) will install to the MBR of that HD. Finish the install and do the updates as needed.  If everything is OK, shut down and re-plug the win HD.  start-up again and go to BIOS first to make sure that both HD's are recognized and that the ubuntu HD is set to BOOT FIRST.  As you continue to boot up, you will only be able to boot into ubuntu.  Access a terminal and run the command

```
sudo update-grub
```

which will allow GRUB2 to find and incorporate windows in the menu.  Reboot .... access windows ....ensure that windows is booting fine.  If there are problems, you can easily unplug the ubuntu HD and just boot into windows as it and its' bootloader has not been touched (remember GRUB2 is in the MBR of the ubuntu HD and not the win HD).

If the HD's are  inter-linked and only one HD is connected to the board, then you may have a master-slave setup.  That means you have to 'de-link' and configure/make sure that only the ubuntu HD is connected to the board so that you only install unto it.  Afterwards, same process.  Re-link, set ubuntu HD as first to boot, update grub.

There is a faster, less 'surgical' method but as you hinted in your first post, it all depends on your current comfort level and confidence in installations.

Post back if you need further clarifications.  Oh, before proceeding, do make sure you have a working/tested back-up of your files. 

Regards,

Raymond

---

### Post by Miscible21 on 2010-01-30
Thanks again for your posts raymondh. 

I followed your initial advice and winged it. I went fairly smoothly, but i think my ubuntu studio disk may have been damaged from the start. As a result the install, allthough functional, was not complete. So the grub command didnt work, along with many of the apps that come with the full ubuntu studio package. As a result I just reinstalled Karmic and i plan to add the production software that i need manually for now. It's a pity because i wanted to have a true ubuntu studio experience, plus i wanted to start using the 64bit version of the software. Anyway, i will be keeping at it. I may even try to istall ubuntu studio on a completely separate machine at a later stage, it may be a better that way.

---

### Post by raymondh on 2010-01-30
you're welcome ... glad you got it going :)

Happy ubuntu-ing.

Raymond

---

