---
title: "offline installation of ubuntu packages"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by princemaozh on 2011-10-24
1) I executed following commands on one online PC
sudo aptitude install <package1>
sudo aptitude install <package2>
...
sudo aptitude install <packagen>
during installation, all the required .deb files were downloaded in directory /var/cache/apt/archives/, which if fine.
 
2) then I copied those .deb files to the same directory (/var/cache/apt/archives/) on another OFFLINE PC. And I tried to run the same commands to do the offline installation.
sudo aptitude install <package1>
sudo aptitude install <package2>
...
sudo aptitude install <packagen>
 
The offline installation is failed with following error messages:
-----------
Couldn't find any package whose name or description matched "<package1>"
Couldn't find any package whose name or description matched "<package1>"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
 
...
 
-----------
 
My question is: 
why the offline installation is failed? (all need .deb files are already there)
anything else needs to do besides copying all required *.deb files into /var/cache/apt/archives/ ?

---

### Post by raja.genupula on 2011-10-24
> **princemaozh said:**
> 1) I executed following commands on one online PC
sudo aptitude install <package1>
sudo aptitude install <package2>
...
sudo aptitude install <packagen>
during installation, all the required .deb files were downloaded in directory /var/cache/apt/archives/, which if fine.
 
2) then I copied those .deb files to the same directory (/var/cache/apt/archives/) on another OFFLINE PC. And I tried to run the same commands to do the offline installation.
sudo aptitude install <package1>
sudo aptitude install <package2>
...
sudo aptitude install <packagen>
 
The offline installation is failed with following error messages:
-----------
Couldn't find any package whose name or description matched "<package1>"
Couldn't find any package whose name or description matched "<package1>"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
 
...
 
-----------
 
My question is: 
why the offline installation is failed? (all need .deb files are already there)
anything else needs to do besides copying all required *.deb files into /var/cache/apt/archives/ ?


HI man 

you can install those packages with this command

```
sudo dpkg -i pkgname.deb
```

this will install the packages and make sure that while doing this process you should be in the directory where you have your deb pkg's. .

All the best.

---

### Post by princemaozh on 2011-10-24
Raja,  thanks for you anwser.
 
"dpkg -i <pkg>.deb" will not take care of the package dependencies, while "apg-get install <pkg>" and "aptitude install <pkg>" will do.  So i am worrying there might be some potential problems if we simply use "dpkg -i".
 
Anybody can explain why the error message "Couldn't find any package whose name or description matched <package1>" come?  I have already copied those required .deb files to the directory /var/cache/apt/archives/,  why "aptitude install" is failed?
(note: actually many forum threads suggested the offline installation by copying .deb files into directory /var/cache/apt/archives/)

---

### Post by raja.genupula on 2011-10-24
> **princemaozh said:**
> Raja,  thanks for you anwser.
 
"dpkg -i <pkg>.deb" will not take care of the package dependencies, while "apg-get install <pkg>" and "aptitude install <pkg>" will do.  So i am worrying there might be some potential problems if we simply use "dpkg -i".
 
Anybody can explain why the error message "Couldn't find any package whose name or description matched <package1>" come?  I have already copied those required .deb files to the directory /var/cache/apt/archives/,  why "aptitude install" is failed?
(note: actually many forum threads suggested the offline installation by copying .deb files into directory /var/cache/apt/archives/)

you mean are you doing as this **sudo aptitude install <pkg>**
If yes , then actually at that after install you should have to write that pkg name

for example if you wanna install firefox then this is the way 

[B]sudo aptitude install firefox

[/B]like this you have to do[B].
All the best .
[/B]

---

### Post by princemaozh on 2011-10-24
raja, yes i did something like "sudo aptitude install firefox" (use package name instead of .deb file name).
 
since all the required .deb files are available in /var/cache/apt/archives/,  my expectation is that the offline installation should be successful after executing "sudo aptitude install <pgkname>", as if I do the installation on an online machine.
 
I do not know the reason of failure.  I guess maybe something else should be configured for offline installation.  (after googling,  no clear answer found)

---

### Post by raja.genupula on 2011-10-25
could you please paste as it as the terminal code what you have you typed .

we need to help you.

all the best,

---

### Post by princemaozh on 2011-10-25
I typed below command on an offline machine:
 
[EMAIL="maoz@maoz-ws:~$"]```
[/EMAIL][EMAIL="maoz@maoz-ws:~$"]maoz@maoz-ws:~$[/EMAIL][EMAIL="maoz@maoz-ws:~$"] sudo aptitude install build-essentials
[sudo] password for maoz:
Couldn't find any package whose name or description matched "build-essentials"
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


```[/EMAIL]

---

### Post by dino99 on 2011-10-25
if it cant find itself the real path, then give it, or move to that folder and run your command from there .

---

### Post by princemaozh on 2011-10-25
> if it cant find itself the real path, then give it, or move to that folder and run your command from there . 
 
I tried to execute command "sudo aptitude install build-essentials" in directory "/var/cache/apt/archives/" where the required .deb files reside, but it still does not work (with the same output messages).
 
dino99, do you mean that? anyway, thanks for your reply.

---

