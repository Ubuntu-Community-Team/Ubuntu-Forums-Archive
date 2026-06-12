---
title: "E: dpkg was interuppted..I cant install packages after upgrade"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by bm143 on 2014-09-04
Hi everyone i recently uprgraded from ubuntu 12 to 14 but now i am having a problem installing packages.  when i had ubuntu 12 i had downloaded alien to convert files i used the command 
sudo apt-get install alien and it had installled just fine but after my upgrade i wasnt sure if i still had alien because the installation setup up said that some programs may be lost so i tried entering that same command to install alien again sudo apt-get install alien but then i get this error    E: dpkg was interuppted, you must manually run 'sudo dpkg  --configure -a' to correct the problem
    now what does this mean and how am i supposed to fix it.  Why is my package not being installed? Do i have the package and there is some error I dont get it please help. 
   Also if i do have alien on my machine how do i check to see if i do have it to where is it downloaded to.  thanks for your answers

---

### Post by grahammechanical on 2014-09-04
Have you run?

```
sudo dpkg --configure -a
```

If you search for alien in the software centre then a green tick mark against alien will tell that it is installed.

Regards.

---

