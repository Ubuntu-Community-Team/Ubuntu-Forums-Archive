---
title: "Installation stops seconds after boot"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by punkinside on 2005-04-26
Hey, hopefully im just being an idiot... but I pop in an ubuntu installation cd a friend gave to me, boot from it, press enter on the first page to get the normal setup, everything starts fine it starts printing a lot of crap on the screen and then it goes completely blank! what appears on the screen goes fast very fast so I cant really tell you what was the last thing I saw.. is it possible that the cd is damaged? my friend installed it without a hitch... (well, several actually but it DID finish) since i had just the the cd i decided to check the md5sum. I used the roxio disc copier to make an .iso image of the cd my friend gave me and cheked it and they didnt match.. is there a chance that this is wrong? I had to copy the cd to a brand new .iso like I said.... the installation went fine with my friend... anyway... Im downloading the .iso from the page again just in case

---

### Post by DutchLau on 2005-04-26
Sounds like you just answered your own question. Go for the new Iso, I do it all the time. 

TIP: let the Ubuntu partitioner auto-partition your hdd, that way the swap and the ext2 are configured properly. Good luck!

---

### Post by punkinside on 2005-04-26
well, maybe thats another problem... im installing so as to have dual boot with XP... used system rescue CD from linux as suggested by someone on another thread and resized the only partition leaving some space for ubuntu without any filesystem so it could partition that space at will... could that be a problem? XP is still working just fine... btw im trying to run it on a Toshiba Sattellite A70

---

### Post by punkinside on 2005-04-26
well... got the new .iso, cheked the md5sums and it was all ok but had the same problem... i think it was the partitions so ill just tweak those for a bit with sysrescue lets see what happens.. if anybody's got any other ideas as to what may be causing this, your help would be greately appreciated

---

### Post by punkinside on 2005-04-27
All set i just had to put in some special parameters in the boot cause it wasent getting along with my lcd everything is up and running!

---

