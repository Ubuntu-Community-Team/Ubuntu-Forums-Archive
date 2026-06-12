---
title: "Cant Install Netbeans on Ubuntu"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by qarout on 2008-07-03
I downloaded the .sh file from the NetBeans website and when i tried installing the following error showed up

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

can someone please help me. thanks

---

### Post by Partyboi2 on 2008-07-03
You can install netbeans through the ubuntu repositories by add/remove or from terminal
```
sudo apt-get install netbeans 
```But in answer to your post, you need to run the install script by
```
sudo sh myNetBeansInstall
``` from within the directory. (Change myNetBeansInstall to the actually name of the file) For example if the sh. file is on your desktop you would
```
 cd Desktop
```then 
```
 sudo sh myNetBeansInstall
```

---

