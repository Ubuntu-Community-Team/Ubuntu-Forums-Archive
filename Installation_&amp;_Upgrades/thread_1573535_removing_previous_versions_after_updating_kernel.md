---
title: "removing previous versions after updating kernel"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by michael2009 on 2010-09-12
I have looked for existing threads on this issue, but found no matches, so I am starting a new one.

I first installed Ubuntu 9.04  on my laptop from a bought CD last year. When I later installed the kernel updtates with the Update Manager, I noticed the the list of versions growing when I booted up. 

Then something horrible happened. After installing maybe the third or fourth kernel update, I couldn't boot into Ubuntu, it failed every time. After that I left Ubuntu broken on my laptop for a while.

I have now reinstalled from the CD again. However, I am now very wary when it comes to installing even the important security updates, never mind the recommended ones! I prefer to keep it simple, because I don't want to do any more reinstalls for a while. 

So far I have just one kernel headers update on the boot list, and I am trying to figure out how to remove the previous one. I do not see the point in having a growing list of them again. Can anyone tell me how to remove the previous ones from the list?

---

### Post by drs305 on 2010-09-12
Ubuntu Tweak, an easy-to-use GUI app, is the best solution. You can read about how to install and use it in the "Removing Older Kernels" section (near the end of the first post) of the SUM link in my signature line.  

The app the post was written for, StartUp-Manager, is also still useful if you just want to hide the kernel from the menu but not actually remove it from your system.

---

### Post by michael2009 on 2010-09-12
Thanks for that very quick reply! I am one of those people not very confident with command lines, but I have recently succeeded in running simple commands like sudo apt-get update and autoremove (after being prompted to do this in recovery mode), so I shall install Ubunu Tweak a you suggested, and give it a go... can you just reassure me that there is no danger of me knocking out my system with Ubuntu Tweak, assuming I follow your instructions... sorry I am just nervous of tinkering with the system more than I need to I guess. 

While on the subject of updating kernels, and also newer versions of Ubuntu, what is the purpose of doing this every time a new one becomes available? Is it just to improve the system security? I ask this because my laptop is quite old (compaq n400c) and is getting quite slow with the newer, more sophisticated distros, especially as I only have 256 Mb RAM.

---

### Post by drs305 on 2010-09-12
Yes, Ubuntu Tweak is a safe way to remove kernels since it won't let you uninstall the one you are currently running. Many users want to keep at least two kernels - at least for a while - when a new one appears on the menu. The reason is to have a known working backup in case the new one presents problems with a piece of your hardware.

If you have only the normal repositories enabled in Ubuntu you *should* be safe. These updates have been tested by the Ubuntu team to ensure compatibility. Of course there are no guarantees - as you have experienced.

If you are especially skittish, you can set your system to update less frequently or even not at all, although I wouldn't recommend the latter. You definitely want to get the security updates, if nothing else.

Make the setting changes in either Synaptic, Update Manager or Software Sources/Software Center.

You can learn more about how the repositories are set up by reading the Ubuntu community doc:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by michael2009 on 2010-09-12
whoops! I just downloaded Ubuntu Tweak from their website, and followed the prompt to open with debi package manager, and I have received an error message: Error: Dependency is not satisfiable: policykit-1-gnome|policykit-1-qt

what should I do now?

---

### Post by drs305 on 2010-09-12
> **michael2009 said:**
> whoops! I just downloaded Ubuntu Tweak from their website, and followed the prompt to open with debi package manager, and I have received an error message: Error: Dependency is not satisfiable: policykit-1-gnome|policykit-1-qt

what should I do now?

On this page you can get an older version which will match your system:
[http://code.google.com/p/ubuntu-tweak/downloads/list]("http://code.google.com/p/ubuntu-tweak/downloads/list")

---

### Post by drs305 on 2010-09-12
By the way, if you really still are running 9.04 Jaunty, are you aware it reaches End of Life (EOL) next month and you won't be able to do updates?

[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

Actually, that appears to be an older link, but the process is the same.

---

### Post by michael2009 on 2010-09-12
Yes I have the repositories set to only show the important security updates, and the recommended ones from jaunty. I definitely don't need the source code stuff... I am no developer as you can probably guess by now!

correction: the the error warning comes from Package Installer...

---

### Post by michael2009 on 2010-09-12
aha... yes I did read that recently, which brings me back to my earlier question about newer versions of Ubuntu. Do I really need newer and better versions when my laptop can barely cope with the existing one? (I am satisfied with jaunty, it does everything I need it for, mainly word processing, updating web pages and Firefox, which I always update when the newer versions become available)

---

### Post by drs305 on 2010-09-12
> **michael2009 said:**
> aha... yes I did read that recently, which brings me back to my earlier question about newer versions of Ubuntu. Do I really need newer and better versions when my laptop can barely cope with the existing one? (I am satisfied with jaunty, it does everything I need it for, mainly word processing, updating web pages and Firefox, which I always update when the newer versions become available)

That's a decision only you can make. While I update software, I run a computer until it becomes incapable of what I need it to do so I understand your thought process. (I have some old computers)  You won't be getting security updates. Ubuntu has come a long way in 18 months.

I think what I'd do is learn how to make an image of your Ubuntu install, and perhaps make a separate /home so you can keep a lot of your configuration changes. Then I'd go for broke with 10.04, which is a LTS version. If it doesn't work out, restore your old image and you haven't really lost anything except for a few hours of install time. If it does, you probably won't have to worry about it until your computer wears out.

---

### Post by michael2009 on 2010-09-12
OK. I have downloaded one of the older versions, [ubuntu-tweak_0.4.8-1~jaunty1_all.deb    ]("http://code.google.com/p/ubuntu-tweak/downloads/detail?name=ubuntu-tweak_0.4.8-1%7Ejaunty1_all.deb&can=2&q="),  but I now have a download error message: 

/tmp/ubuntu-tweak_0.4.8-1~jaunty1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I don't know how to do this :(

---

### Post by drs305 on 2010-09-12
> **michael2009 said:**
> /tmp/ubuntu-tweak_0.4.8-1~jaunty1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I don't know how to do this :(

If it's what I think - open nautilus, right click on the .deb file, and select Open With and find Gdebi (if Jaunty has it).

If not, open a terminal, change into the folder with the Ubuntu-Tweak deb, and run:
```
sudo dpkg -i <packagename>
```

Just type the first few letters of the ubuntu-tweak deb name and hit Tab and it should autocomplete. 

Have to log off now - I'll check back tomorrow. :-)

---

### Post by michael2009 on 2010-09-12
Right then. If I want to install 10.04, will it replace the jaunty version, or will jaunty remain on my computer in some form? 
When I installed my Ubuntu system, I went for automatic partitioning, which has turned out to be trouble free, but it means I have no separate Home partition. If I create a new partition with the /home path, does it mean my configuration and files will automatically transfer to that partition? Or will I have to move them manually afterwards?

---

### Post by michael2009 on 2010-09-12
ok thanks for all your assistance:)

---

### Post by aeronutt on 2010-09-12
Also easy using Synaptic package manager.

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by drs305 on 2010-09-13
> **michael2009 said:**
> Right then. If I want to install 10.04, will it replace the jaunty version, or will jaunty remain on my computer in some form? 
When I installed my Ubuntu system, I went for automatic partitioning, which has turned out to be trouble free, but it means I have no separate Home partition. If I create a new partition with the /home path, does it mean my configuration and files will automatically transfer to that partition? Or will I have to move them manually afterwards?

Since you can't directly upgrade from 9.04 to 10.04 (Lucid), you would have to upgrade "through" 9.10 first or do a clean install of Lucid. With a clean install, you lose your customizations. There are things you can do to make things easier in the transition though, such as exporting a list of your current applications via Synaptic so you can install them all on the new setup. And don't forget to copy any data you have on your Lucid partition elsewhere before overwriting it!

Another option would be to create a new partition and install Lucid on the new partition, keeping your current Jaunty system as well - at least for the time being. 

Having a separate home means that your configurations would stay close to the way they are now. I wouldn't recommend sharing the same /home with both Jaunty and Lucid, but you can move your /home folder and then tell any clean install where your home partition is located. Here are a couple of links on how to create a separate home partition.
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

