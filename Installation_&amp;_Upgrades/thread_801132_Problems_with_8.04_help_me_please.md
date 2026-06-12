---
title: "Problems with 8.04 help me please"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by neku on 2008-05-20
Ok. I have the 8.04 iso on my disk burnt on properly to a cd-r and i want to dual boot so i go to my bios set it to disk boot it boots the disk. I go to start with install then install later cause i saw a video telling me to do that so i go into it planing to install and set partition it gets to a black screen with some text saying loading local boot or something then says ok for them all then nothing it just stays that way for ages so i restart and choose just install and says aload of stuff then something about the command prompt i dunno about that so none of it loads i need help lol


ok also my friend has now helped me install 7.10 and when i installed all of the updates it installed them but nothings showing up now help lol

---

### Post by zvacet on 2008-05-20
> ok also my friend has now helped me install 7.10 

Does it mean that you are runing Gutsy (Ubuntu 7.10) right now?If that is a case then go to the system<admin>software sources and check all under ubuntu software and updates tab.Reload.Now in system>admin>update manager and you should see message that new version is available for upgrade.Before you go for upgrade,do you have separate home partition?If you don´t make one folllowing [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.Other solution is to backup your files(burn on CD/DVD or some other method).You can do upgrade via net or from alternate CD.I prefer(that means nothing) alternate CD because if something goes wrong you allways have CD to  install again.Instructions for both ways are [here.]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by neku on 2008-05-20
ok he says im on feisty fawn and i have it set up as a different partition and when i tryed to update on that menu it just came up with some random sudo  error thing so i got rid of sudo password using terminal and now i click update it comes up with it saying its downloading 2 tools then it just disappears and nothing happens

---

### Post by zvacet on 2008-05-20
You can not use two upgrade tools in same time like synaptic and upgrade manager.You have to use just one of them.If you want to upgrade from Feisty to Hardy it goes like this **Feisty>Gutsy>Hardy**.Your Feisty have to be up to date and then you can upgrade to Gutsy.....Maybe it is better solution to download Hardy alternate CD and do fresh install with it.

---

