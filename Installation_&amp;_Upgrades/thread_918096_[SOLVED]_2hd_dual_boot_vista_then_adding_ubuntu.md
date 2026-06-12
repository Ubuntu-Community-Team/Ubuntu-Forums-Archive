---
title: "[SOLVED] 2hd dual boot vista then adding ubuntu?"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by ubuuntu9897 on 2008-09-12
hey guys im not new to ubuntu for say but i have vista and am wondering what to do I have 2 500gb hard drives i was thinking of giving ubuntu some of my second one 
my hard drives are like this
c://454 gb
d;// 11 gbs its for recovery i dont think its an actual frive though and 
e;//465 gb

can you tell me what to do i saw a guide that says grub works for dual booting vista and grub but i heard that it doesnt as well can you clear it up for me. i had it dual booting 98 and ubuntu 7.10 before but i was away form using ubuntu for aa bit as by power supply blew on that one.

---

### Post by Pumalite on 2008-09-12
If you are going to have Vista and Ubuntu in 2 different drives; read this:
[http://ubuntuforums.org/showthread.php?t=881102&highlight=Dualboot+Hard+Drives](http://ubuntuforums.org/showthread.php?t=881102&highlight=Dualboot+Hard+Drives)

---

### Post by caljohnsmith on 2008-09-12
Ubuuntu9897, you can definitely boot Vista from Grub. I would recommend that before you install Ubuntu, while you are in the Live CD, first do:
```
sudo fdisk -l
```
From that output, figure out which is going to be your Ubuntu HDD (should be sda or sdb). Then when you run the Ubuntu installer and get to the final step to install Ubuntu, click the "advanced" button and tell Grub to install to /dev/sda or /dev/sdb, whichever is your Ubuntu HDD. That way, your two HDDs will be independent, and if one breaks the other won't care; you will still be able to boot the drive that is OK. The last step would be to make sure your BIOS is set to boot the Ubuntu HDD first, and then to boot your Windows drive all you need to do is add the following to your /boot/grub/menu.lst:
```
title Windows HDD
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Or if you prefer, you can boot the Windows partition directly with the syntax used in the thread Pumalite gave. The end result will be exactly the same. Let us know how it goes. :)

---

### Post by ubuuntu9897 on 2008-09-12
one thing though i may not want the boot scrren to actualy vome up maybe pres abutton real fast to bring it up can I do that as well?

---

### Post by caljohnsmith on 2008-09-12
> **ubuuntu9897 said:**
> one thing though i may not want the boot scrren to actualy vome up maybe pres abutton real fast to bring it up can I do that as well?
Sure, in your Grub's /boot/grub/menu.lst, just uncomment the line that says "#hidddenmenu" so it is instead "hiddenmenu". Then on start up you will have to press ESC to get the menu, otherwise Grub loads the default OS entry that you have set with the "default X" line in menu.lst, where X is a number. Note that the numbering in Grub starts at 0, so making the first OS entry the default entry would be "default 0", the 2nd OS entry "default 1", etc.

---

### Post by ubuuntu9897 on 2008-09-12
well one more question man i have alot lol I sort not sure if i should go with 32 bit or 64 i have a processor that would proble be good a and phenom x4 my windows is 32 bit though whitch one do you think i should go with i only have 3gbs of ram, but one bug i think i have is i want the fancy graphic effects but on the 64 bit live cd witch im using right now i cant get them could i get them if i install i have a  ati 2400xt pciexpress video card? If icant i may want to use the 32 bit disk?

---

### Post by Pumalite on 2008-09-12
Your ATI card might be your biggest problem.

---

### Post by ubuuntu9897 on 2008-09-12
i know its not the best but still? I confused on witch route i should take 32 or 64 though.

---

### Post by Pumalite on 2008-09-12
You can use either one. 64 bit handles your RAM better.
Some people prefer 32 bit for personal reasons.

---

### Post by ubuuntu9897 on 2008-09-12
ugh now i realize i told grub to ibn stall on hd1 since it said hd0 when i opened up advanced is there anything to fix that so it boots from /dev/sdb using the live cd?

---

### Post by ubuuntu9897 on 2008-09-13
Ugh i finnaly made it into my ubtunu install but  i had to use super grub disk to get inim confused really onwhat to now i try to fix it with that ssk but i continue to get error 22 i want to be able to boot directly in please help. is there a way i can delte geub from ubuntu then reinstall it with the grub disk?

---

### Post by ubuuntu9897 on 2008-09-13
ugh well the grub disk must have fixed me as im in unfirtunatlay booted from the first drive though time to see if vista works ;)

---

### Post by ubuuntu9897 on 2008-09-13
one more thing hte ati 24000 does work the fancy graphics :) for nayone else who wants to konw that i wonder why it didnt like how i put grub on hd2 for now i be okay with it hd1 but i still rather not have it on there but windows works so im okay

---

