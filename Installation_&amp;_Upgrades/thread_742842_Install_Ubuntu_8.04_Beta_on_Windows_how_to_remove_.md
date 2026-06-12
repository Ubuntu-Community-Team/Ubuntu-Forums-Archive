---
title: "Install Ubuntu 8.04 Beta on Windows how to remove boot loader ?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by JOKe on 2008-04-02
Hello i installed Ubuntu 8.04 beta just to check it and after i  install it on windows it add somethink to the windows boot loader not in master boot record where i can choise Windows / Ubuntu 
after i uninstall ubuntu the windows boot loader is still there  can i remove it ?

---

### Post by PmDematagoda on 2008-04-02
I am afraid I do not comprehend what you are saying, but I think you are saying:-

"I installed Ubuntu 8.04 to have a look and afterwards I just reinstalled Windows back, but now I am unable to boot to Ubuntu since Windows has overwritten the MBR."

Am I on target?

---

### Post by JOKe on 2008-04-02
No no  I installed ubuntu 8.04 as Windows Install using WUBU , installation in windows partion in some folder not in other partion and this doesnt effect on MBR but adds ubuntu in a list in windows boot loader not in master boot loader, in windows boot loader on this partion ( the partion which is active and where windows is installed ) . After i remove ubuntu from Windows // Add remove programs the entry in windows boot loader exists. ( check this [http://lifehacker.com/software/ubuntu/install-and-run-ubuntu-without-disturbing-windows-228956.php](http://lifehacker.com/software/ubuntu/install-and-run-ubuntu-without-disturbing-windows-228956.php) and this [http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)  )

---

### Post by Captain Giraffe on 2008-04-02
Go 
Start / My Computer [Right click Properties] / Advanced / [Start up and recovery] Settings / [System startup] Edit ...  then remove the lines referencing  ubuntu. 
Save the original file before you make any changes just in casee you make a mistake.
 The Edit button makes the boot.ini fil editable. Editing it from explorer wont work under most circumstances.

---

