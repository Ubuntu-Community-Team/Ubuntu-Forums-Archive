---
title: "Wine help wanted please."
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by ashenrose on 2006-09-16
I have installed wine, its in my /usr/lib directory, but I don't know how to open it. This sounds really feeble :S

There is nothing in applications to start it or on the desktop.

---

### Post by tagra123 on 2006-09-16
wine somewindows.exe

---

### Post by ashenrose on 2006-09-16
Pardon me?

That doesn't make a lot of sense to me.

---

### Post by kenm on 2006-09-16
What tagra123 is trying to say, somewhat tersely, is to use wine you provide the name of the windows application you want to run. For example, to run a Windows application called somewindows.exe enter the command:
```
wine somewindows.exe
```

---

### Post by th3t1nm4n on 2006-09-16
You can install Wine from WineHQ's repositories, I recommend that you do, they release frequent updates for it. Read how to do that here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
If you're running Edgy Eft, just tell it that you're running Dapper until Edgy has support.

You use wine to run .exe files by opening a terminal and typing "wine /location/of/win32-app.exe", you will most likely need to configure wine somewhat to get audio working in many games/apps, to do this run "winecfg".
One of the common changes that you may have to do is click on the Audio tab and change Hardware Acceleration to Emulation.

Good Luck

---

### Post by ashenrose on 2006-09-17
Thank you for your help. I shall be trying to download apps to run in wine so I can test it out.

---

### Post by Ambimom on 2006-09-17
Chances are, it's installed but you don't realize it...that's what happened to me....

when you want to open something in it, you right click on the windows application and you'll see instructions to open in wine...

---

### Post by tagra123 on 2006-09-18
> **ashenrose said:**
> Pardon me?

That doesn't make a lot of sense to me.


Sorry for the brevity. kenm gave a more detailed answer.


I have wine and CrossoverOffice installed. A lot of non-supported programs will run with crossover. 

My real solution was to install VMPlayer and the Trial VMWorkstation.

I used VMWorkstation to create a virtual machine and disk. Install Windows, Then when the VMWorkstation trial expires just use the free vmplayer to run the Virtual MAchine. 

My personal opinion is all but very simple applications work best using Windows, but crossover office has some programs working that I could not get to work with wine.

There's a how-to for installing VMPlayer in the forums. I'd skip the part with qemu, which I thought was very slow. Instead of going through the steps the author of the how-to gives about creating a virtual disk -- at that point create the virtual disk using VMWorkstation.

---

