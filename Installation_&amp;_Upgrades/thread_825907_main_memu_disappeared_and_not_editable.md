---
title: "main memu disappeared and not editable"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by wanginc on 2008-06-11
Hi I have just updated from 7.10 to 8.04 and after restart my main menu was really minimal: games>opentt and internet>bittorrent that was it!
After searching and found nothing useful than install ubuntu-desktop that I all ready had installed, I tried the magic button in system>preferences>main menu: reset to default. After cliking this all was gone and when I click on system>preferences>main menu nothing comes up. 

Is there a way to get it back working? 

Is there also a way if I get it back working t get at least a  default main menu?

PS I triead allready to create a new user but nothing happened :(

---

### Post by avtolle on 2008-06-11
Try this (off the top of my head): Right Click on Applications, Select Edit Menus from the pop-up, and if it works, select "Revert" (from memory) to hopefully get you back.

---

### Post by wolfen69 on 2008-06-11
do alt-F2 and check  off run in terminal, do```
sudo apt-get install gnome-menus
```

---

### Post by wanginc on 2008-06-11
thanks to wolfen69

Here is what I did
and got my main menu back:

tried to use apt-get install gnome-menus but it was already there but broken so I uninstalled it, this uninstalled allot of other stuff like ubuntu-desktop

Then first sudo apt-get install gnome-menus
it will ask you if you want to use a new file for the menus and I said yes.

then  sudo apt-get install ubuntu-desktop.

restart and all was there again....my old main menu!

Hope it will help some one Ciao!
:guitar:

---

### Post by nikolaos on 2008-07-30
it sure did help me, Thanks!!!

---

