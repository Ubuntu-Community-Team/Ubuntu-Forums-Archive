---
title: "uninstalation of application errors"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by specter51095 on 2010-01-30
a few days ago i installed the application wine for running windows .exe s when it started to bug out i tryed to uninstall and reinstall and being new to linux i googled how to uninstall it and i got alot of search it in the synaptic package manager and uninstall it from their so i did that but after that the wine tab was still in the apps dropdown tab but this time it was only a folder (not the wine icon) and it had just the program files i installed with it so i went to wine FAQs and used terminal commands:
rm -rf $HOME/.wine[FONT=Verdana]\[/FONT]
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
 to  remove all wine created desktop and applications entrys but now when i try to reinstall it it says there is still broken pkgs on your computer please remove those before installing so i went back to the pkg manager and found that their was no broken pkgs i took this to wine forums and they said there has been some reported uninstall problems with ubuntus resent updates and refered me here can anyone help me find and remove those broken packages 

im useing ubuntu 9.10 and used wine 1.37 if that help

---

