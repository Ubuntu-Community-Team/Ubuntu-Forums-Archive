---
title: "Downloading and Installing Packages"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by uxohus2b on 2006-06-27
Hello,

I just installed Ubuntu 6.06 on a desktop PC that has NO Internet connection. But I have a laptop also running Ubuntu 6.06 that gets wireless Internet. 

My question is: How can I download packages using Synaptic on my laptop and install them on my desktop? I'd rather avoid searching for and downloading individual packages (with dependencies and all) from the Ubuntu website. Is there a simple way to download packages in Synaptic to a specified folder and use them on a different computer?

Thanks!

---

### Post by ubuntu27 on 2006-06-27
Maybe this would help: [http://ubuntuforums.org/showthread.php?t=183933](http://ubuntuforums.org/showthread.php?t=183933)

CD for users who have slow/no internet on their Ubuntu computer, and want to install upgrades and commonly used extras, like media playback, language support, etc.

---

### Post by aysiu on 2006-06-27
You can always try the community-created (well, it's mainly one person, actually) Ubuntu Plus, which is an add-on CD with a lot of popular software:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

Or *aptmove*, which allows you to create a local repository of your own:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

Or something simple may work for individual programs. On the machine that has internet: ```
apt-get clean
sudo aptitude update
sudo aptitude install *nameofprogram*
``` Then copy all the .deb files from /var/cache/apt/archives to a USB device, and copy from that to the desktop of the Ubuntu with no internet and: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by uxohus2b on 2006-06-28
thanks a lot for your help, and the very thoughtful comparsion between windows and ubuntu :)

---

### Post by uxohus2b on 2006-07-03
[QUOTE=uxohus2b]Hello,

I just installed Ubuntu 6.06 on a desktop PC that has NO Internet connection. But I have a laptop also running Ubuntu 6.06 that gets wireless Internet. 

My question is: How can I download packages using Synaptic on my laptop and install them on my desktop? I'd rather avoid searching for and downloading individual packages (with dependencies and all) from the Ubuntu website. Is there a simple way to download packages in Synaptic to a specified folder and use them on a different computer?

Thanks![/QUOTE]

I realized an easy way to do this:
All downloaded packages (.deb files) are saved in:
/var/cache/apt/archive/
So you can just copy all the deb files from this directory to a USB disk or whatever, and just take it to the no-internet computer and install them all there.

so, from connected pc:
cp -R /var/cache/apt/archive/* /media/USB/
then at the unconnected pc:
dpkg -iR /media/USB/*.deb

---

