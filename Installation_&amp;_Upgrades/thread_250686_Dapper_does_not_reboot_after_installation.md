---
title: "Dapper does not reboot after installation"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by nanbudh on 2006-09-04
i am very exited about ubuntu dapper, i have never used a linux before and am a new crossover from windows. But i need help urgently as i have to get system ready for usage in my college lab. *i must not fail, must not need to revert back to windows*. PLEASE HELP!. here is what happens:
 i download desktop cd iso. burn it. check cd for error. it says 0 checksum errors which i assume as a green signal. i start the boot. reach the desktop screen and click the install icon. thru the options i choose automatic partitioning. i also choose to erase entire disk as  need a clean install. well everything goes well and a confirmatory message is shown that everything is well and now reboot. well it ejects the CD on reboot but after a moment it freezes on the following message (i may be forgetting exact wording)
'loading root file system'
'waiting for root file system'
then the screen changes from graphical to text console and i can  read several line to this effect: 
hard disk geometry of partitions does not match with something and some volume not found.
my system is PIV 1.3 ghz, 256 mb sdram and 20 gb samsung hard disk.

i am lost](*,) . PLEASE HELP. THANKS IN ADVANCE

---

### Post by zxee on 2006-09-04
Have you tried text mode installation?
On some hardware the alternate cd seems to be a better choice so you could try that too.
I also recomend the ubuntu guides: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by nanbudh on 2006-09-04
thanks for reply. is there a choice of text/ graphical intall? i'll look for it. for the second suggestion, it would be too dificult for me to download a whole 700 mb again but who knows if i nothing else works i might have to.
when i boot again from live cd and then try to install again and choose manual partitions i am shown existing partitions from previous install and there the status of the top most partition /dev/**something** is shown to inactive. is there a clue here?? is there a way to make it active. and i have read about a partition being 'bootable' too. whats that?

---

### Post by cotcot on 2006-09-04
The first option of the alternate install CD is "install in text mode".
Do not be afraid to choose this option instead of the graphical way (the CD you already have). This text mode is the way the previous versions of ubuntu were installed. There is a good guidance in the text mode.

---

### Post by nanbudh on 2006-09-05
thanks for help. i downloaded the 'alternate iso' image and loaded through text mode and it worked!! thanks.

---

