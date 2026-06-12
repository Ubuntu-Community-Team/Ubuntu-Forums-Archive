---
title: "Black Screen On Boot - Ubuntu 14.04.2"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by ryan148 on 2015-03-22
Hello,

I am new to Linux so bear with me please.

I installed Ubuntu 14.04.2 on my custom made PC and on initial boot up, I was experiencing very poor resolution (almost could not read text on screen) as well as some vertical lines on the top 3/4 of the screen.  I followed this guy's instructions for updating my NVIDIA graphics card (GTX 750 Ti Superclocked):

[https://www.youtube.com/watch?v=ioMeSCoyYng](https://www.youtube.com/watch?v=ioMeSCoyYng)

After doing this, I restarted the computer and now my screen is black.  I can't see or do anything.  How can I go about fixing this?  Any help is much appreciated.

Thanks!

---

### Post by kc1di on 2015-03-22
According to Nvidia you should be using the 334.21 driver  or Newer for that card.  
It is not in the repository yet so you'll have to get it from a PPA or Nvidia's webpage. 
You can add the Xorg-edgers ppa and get 346  or download from nvidia. 

Edgers ppa is found here :
[http://www.ubuntuupdates.org/ppa/xorg-edgers]("http://www.ubuntuupdates.org/ppa/xorg-edgers")
and Nvidia's page is here:
[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/334.21/NVIDIA-Linux-x86_64-334.21.run&lang=us&type=geforcem]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/334.21/NVIDIA-Linux-x86_64-334.21.run&lang=us&type=geforcem")

Good luck :)

---

### Post by ryan148 on 2015-03-22
Thanks Dave!

One question on the PPA method - since I'll have to type in the attached code without being able to see my terminal, will terminal require me to enter my password after each line (due to using the sudo command)?  Otherwise if I download it directly from NVIDIA, how do I go about installing it without seeing the terminal?  Thanks!

sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install <package name>

---

### Post by ryan148 on 2015-03-22
Nevermind I think I figured it out - thanks Dave!

---

### Post by CantankRus on 2015-03-22
Try ctrl+alt+F1 and login.
Purge nvidia drivers...
```
sudo apt-get purge nvidia*
```

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install ppa-purge nvidia-346
```

Also installs ppa-purge so you can purge xorg-edgers if you have problems.
To purge if needed....
```
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

