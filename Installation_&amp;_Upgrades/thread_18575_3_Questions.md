---
title: "3 Questions"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-03-07
1.I have reinstalled ubuntu and i have from previosly installed ubuntu cache folder
with all packages now can i set this to be displayed at Synaptic?
2. Is there any good software for dialing some dialer?
3.I have ATI Radeon 9600 How to set-up TV OUT is this even possible??
Thanks

---

### Post by dewey on 2005-03-07
I don't quite understand your first two questions, but the third is a given.

ATI has recently released new linux drivers, and while compiling them, you can enable or disable TV Out Support.
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I suggest reading up on the forums about the drivers, it's given a few people some trouble, including me.

---

### Post by bored2k on 2005-03-07
[QUOTE=dado]1.I have reinstalled ubuntu and i have from previosly installed ubuntu cache folder
with all packages now can i set this to be displayed at Synaptic?
2. Is there any good software for dialing some dialer?
3.I have ATI Radeon 9600 How to set-up TV OUT is this even possible??
Thanks[/QUOTE]

Im guessing question 1 implies you having a backup of the /var/cache with all your apt-acquired .deb files, and u want them 2 show in synaptic.

1. Well, easyiest way is to put the .deb files back in /var/cache/apt/archives/ and clic Reload in Synaptic.

2. Whatever you mean, dialing free rhymes with [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/) .

3. Already answered before me .

---

### Post by dado on 2005-03-08
Thanks but how can i copy archives back to /var/cache/apt/archives/
I have tried like this 
sudo cp archives /var/cache/apt/archives but i get error!

---

### Post by dado on 2005-03-09
Please answer me!!!

---

### Post by Juergen on 2005-03-09
It would help to tell us the error you get.
Try
```
sudo cp archives/* /var/cache/apt/archives
```This saves you the re-download, but you still need your entries in sources.lst.

If you want to create your own repository containing these files, you need to create a Packages.gz with 'dpkg-scanpackages'. 
Look here:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781568](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781568)
for more info

---

