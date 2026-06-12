---
title: "Error with SUper-Boot-Manager Installation"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by antoniospider on 2013-05-21
Greeting !
i have some problem with the super-boot-utility .
i followed the instructions : 


```
sudo add-apt-repository ppa:ingalex/super-boot-manager

sudo apt-get update
```

and then executed the command to install :

```
sudo apt-get install super-boot-manager 
[sudo] password for vision: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 super-boot-manager : Depends: plymouth-x11 (>= 0.8.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

i've tried different solutions but anything resolved... can you help me??
I don't need specifically this utility in case you have another one which still do the same ting , it' s really good for me ! let me know 
my purpose is to change tha splash screen after the boot and , in case i can do , the bios splash screen with one of mine
thanks a lot!! antonio

---

### Post by antoniospider on 2013-05-21
how can i resolve that line ?? thanks in advance !
```
[COLOR=#000000][FONT=Ubuntu Mono] super-boot-manager : Depends: plymouth-x11 (>= 0.8.2) but it is not going to be installed[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
i have ubuntu 13.04 

[/FONT][/COLOR]

---

### Post by antoniospider on 2013-05-21
any suggestions ? thanks a lot !

---

### Post by oldfred on 2013-05-21
Please do not bump more than once per 24 hours.

I do not know that app. Sounds interesting. I have 12.04 and still have plymouth installed, but do not know if newer version still has it or not. 

If it is just background image you want.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

