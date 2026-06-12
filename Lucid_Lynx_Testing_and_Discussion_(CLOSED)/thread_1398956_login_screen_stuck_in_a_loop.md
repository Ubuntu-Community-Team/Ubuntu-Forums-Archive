---
title: "login screen stuck in a loop"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bumanie on 2010-02-05
My login screen seems to be stuck in a loop. I enter the password, which is accepted. The screen flickers as though it is going to open the desktop, but then it returns to the login screen and this happens over and over. I can update via console in safe mode, but so far no new updates have helped. I have tried to startx, but then it hangs at a black screen. Also tried to stop gdm - console told me that gdm was replaced by Upstart, so I tried to killall Upstart and console message was that it was an unknown process. Anyone got any ideas?

---

### Post by nanog on 2010-02-06
probably a failed upgrade.

have you tried reinstalling ubuntu-desktop -- this often breaks during partial upgrades. i would also try reinstalling dkms modules for any proprietary graphics drivers or just switching to the open source ones temporarily. kms is still buggy and depending on your driver you may want to add nomodeset to your grub boot options.

helpful commands:
[http://ubuntuforums.org/showpost.php?p=8637726&postcount=52](http://ubuntuforums.org/showpost.php?p=8637726&postcount=52)

chrooting:

[http://ubuntuforums.org/showpost.php?p=8628383&postcount=2](http://ubuntuforums.org/showpost.php?p=8628383&postcount=2)

---

### Post by 23dornot23d on 2010-02-06
Have you tried to install another Desktop Manager ..... 

I presume you are trying to start Gnome ...... and you already have removed gdm2.2




sudo apt-get install gnome-session


(  gdm2.2 caused me lots of boot display problems but eventually after removing gdm2.2 .... and replacing with kdm and kde .... all is ok now )


If you want to work in a desktop and see what is happening ...... thats why either ( KDM long install time ) or ( E16 short install time )

sudo apt-get install kdm
sudo apt-get install kde
............   or
sudo apt-get install e16 

E16 is a small desktop environment  ......... gnome and kde run inside it .... so even if its failing you may be able to see why .......

if not ...... as previously stated it may just be quicker to reinstall it ..... but if its a upgrade ..... 

make sure you backup your home directory ....... ( if its not safe on another partition ) .....

---

