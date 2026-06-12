---
title: "GRUB predicament"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by scofisticated on 2010-10-11
ok, sit up straight cause this is going to take a while.

i used  WUBI to put Ubuntu on an SD card. i ran it off that for a while, and  keeping my Vista. then i tried upgrading to to 10.10. there was even a  special installer for GRUB in the process.

that's when the  problem started. after my comp finished the upgrade, it restarted. but  this time, in grub rescue. i tried some of the codes in the wiki, but  everything came up unknown command. then someone in the chat told me to  use a Live CD and a Super GRUB2 cd. 

the LiveCD booted to a  screen with a picture of a "keyboard=person with a circle around it".  then after a few minutes of just that, lines of text reading:[INDENT]EDD: error 8000 reading sector 3567
EDD: error 8000 reading sector 3577
(and more with consecutive numbers)
[/INDENT]the  Super GRUB2 cd let me get the OS list i usually get from starting up.  only Vista would start up without problem. Ubuntu had.. a problem i cant  recall right now.

i redid the Live CD, and im back in Ubuntu. i  tried the ways of reinstalling GRUB2, as advised by the chats, but  nothing seemed to work as described in the reinstallation section of [this]("https://help.ubuntu.com/community/Grub2").

and  that is where i stand right now. also, my SD drive's light doesnt turn  off now, even when there is no card in it. im kind of worried that when  GRUB installed at the 10.10 upgrade, it made that a partisan.

---

### Post by bcbc on 2010-10-12
Reinstall the windows bootloader required for WUBI installs - on XP run "fixmbr", on vista/7 run "bootrec.exe"

Or boot a live CD and install lilo in a form equivalent to the windows bootloader (ignore warnings relating to booting linux)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That will get windows booting. You will probably still have problems booting wubi since the 10.10 upgrade has bugs. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by scofisticated on 2010-10-12
awesome. that solved the boot problem. the OS menu comes up the same as before. Windows and Ubuntu come up no prob. but Ubuntu takes a while to activate the mouse. and then a while longer to activate the keyboard. but that may be an Ubuntu prob.

the only thing im still worried about is the SD drive. the light is still on. and in Windows, none of the memory card drives show up. and even when my SD card is in the drive, i cant access it.

i'll but this as Solved, but if anyone can help me with the memory card drive problem, i would really appreciate it.

thank you soo much bcbc.

---

