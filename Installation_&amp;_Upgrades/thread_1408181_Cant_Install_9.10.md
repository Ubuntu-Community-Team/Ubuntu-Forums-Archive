---
title: "Cant Install 9.10"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by 1druid1 on 2010-02-16
Hi All
 
Its been a while since I have used Linux, going back to the early realeases of Red Hat and Mandrake. 
 
Decided to give it another shot and downloaded the 9.10 Desktop ISO.
 
I get tot the menu screen where I can Try Ubutu, Install Ubuntu, Test Drive, Test Memory ect.
 
Selected Install and it gets to the Ubuntu Icon screen, then goes to a black screen and hangs PC. Tried the Try Ubuntu Option same thing.
 
Redownloaded the ISO and burnt it again at 4x Speed, exactly the same thing. Created a bootable USB drive, tried installing it that way, same again. A little frustrated by this point.
 
Downloaded the Alternative Text Based Install, Installed fine, but as soon as Ubuntu Loads and gets to the Ubuntu Icon it goes black and hangs.
 
Just cant get this OS to run, any help.
 
System Specs
 
Abit IC7 Max 3 Motherboard
Gigabyte GV-R465D2-1GI ATI Radeon HD 4650 GPU
2 gb of memory
250gb Sata Drive
Intel Pentium 4 3.2 ghz CPU
 
Cheers
 
Dougie

---

### Post by pmlxuser on 2010-02-16
i think ts something to do with graphics, read more on your tpe of hardware specificaaly your graphis driver and its compatability with ubuntu 9.10

try logging in the fix mode, using the second option on boot, fix the problem from there

---

### Post by alexdnk on 2010-02-16
Look for graphic drivers for your PC. That may be the problem. while it's booting press Ctrl + Alt + F3. Install mc (Midnight Commander) through apt-get and then browse to a USB stick with your graphic drivers and install them (after you installed mc use 'sudo mc'). Find your drivers and installing them is up to you. Different drivers install differently from others. And try Xubuntu 9.10, it only has XFCE instead of GNOME. If not, I found that Ubuntu and Kubuntu 9.10 are a bit graphics hungry and if you dont have lots of video RAM (most PCs today have 128mb at least) their GUI or DE (depends) doesnt work . So try 9.04 and see how that runs. Hope this helps :popcorn:

---

### Post by 1druid1 on 2010-02-16
Hi
 
I will try the suggestions later on today. As for my GPU it has 1gig of ram so even most graphics power hungry apps run without a problem on it.
 
Cheers
 
Dougie

---

### Post by madmax.santana on 2010-02-16
I don't think it's a graphics problem... It has happened to me quite a times now... It has something to do with the disc-burning facility or even the drive... When I burnt a disk from my own drive, I got exactly the same problem...

Then I used the combo-drive of my neighbor, and it worked. I am not an expert at this so I dont know what exactly is the problem, but the thing worked for me. Try your neighbor, :)

---

### Post by dE_logics on 2010-02-16
> Gigabyte GV-R465D2-1GI ATI Radeon HD 4650 GPU

This is the one and only problem.

I would suggest -

You to reconfigure X and also xf86-video-ati (I don't know the package name in Ubuntu).

See if you have the caps/num lock button working, if so - 

> You need to reconfigure X server.

Press alt+cntrl+F2

Login with your username and passwd (you will not see the password being typed).

Run - 

```
sudo /etc/init.d/gdm stop
```

Then run - 

```
sudo Xorg -configure
```

```
cp /home/<your user name>/xorg.conf.new /etc/X11/xorg.conf
```

```
/etc/init.d/gdm start
```

If nothing works, again alt+cntrl F2 and type > dpkg-reconfigure xf86-video-ati

I'm not sure about "xf86-video-ati"...anyone got the right package name?

Another shot will be installing the proprietary fglrx drivers provided by ATI.

Next time ensure that if you're planning to run Linux on a system, it - 

1) Should not have ANY ATI component.
2) Should not have a Alps touchpad...it's horrible anyway in windows also.

---

### Post by 1druid1 on 2010-02-16
>  Should not have ANY ATI component.
 
 
You have to be kidding there, I have played about with linux on and off for years and have always used ATI cards, this is the first problem I have had. ATI just happen to be better performing cards for media applications especially with hardware HD.
 
I cant beleive the developers of Ubuntu would prefer Nvidia to ATI so there must be a fix for this, have tried you suggestions.
 
> sudo /etc/init.d/gdm stop
 
This takes me to the blank screen again.
 
> dpkg-reconfigure xf86-video-ati
 
Doesnt exsist.
 
Cheers
 
Dougie

---

### Post by darkod on 2010-02-16
Don't know if it can help, but my integrated HD3200 was restarting my PC, both Try Ubuntu mode and once I installed (the install went fine from the standard live cd by the way).

If you don't get a grub menu (if ubuntu is only OS), hit Shift but you have to get the timing right before it starts loading ubuntu and after BIOS is done.
In the main menu select the recovery mode entry.
You'll get a next menu, select something like "root with networking" to have internet access. Should work with wired internet, not sure about wireless.

Once the command prompt loads, install EnvyNG package:

sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

Select to install ATI driver (I didn't remove the current, there is option in the menu for that). From there on just follow the prompts. It will download from somewhere and install it automatically.
It will ask to restart when done. Select the normal mode entry and see if it helped. Worked for me right away.

---

### Post by 1druid1 on 2010-02-16
> **darkod said:**
> Don't know if it can help, but my integrated HD3200 was restarting my PC, both Try Ubuntu mode and once I installed (the install went fine from the standard live cd by the way).
 
If you don't get a grub menu (if ubuntu is only OS), hit Shift but you have to get the timing right before it starts loading ubuntu and after BIOS is done.
In the main menu select the recovery mode entry.
You'll get a next menu, select something like "root with networking" to have internet access. Should work with wired internet, not sure about wireless.
 
Once the command prompt loads, install EnvyNG package:
 
sudo apt-get install envyng-core envyng-qt
 
Run it in text mode with:
envyng -t
 
Select to install ATI driver (I didn't remove the current, there is option in the menu for that). From there on just follow the prompts. It will download from somewhere and install it automatically.
It will ask to restart when done. Select the normal mode entry and see if it helped. Worked for me right away.
 
 
Thankyou A++++++++++
 
Installed as above and everything works great now.
 
Superb Help
 
Cheers
 
Dougie

---

### Post by darkod on 2010-02-16
> **1druid1 said:**
> Thankyou A++++++++++
 
Installed as above and everything works great now.
 
Superb Help
 
Cheers
 
Dougie

Glad it helped. Just for information, the new version Lucid Lynx 10.04 LTS that is under development, images are updated every few days here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I created a usb stick with it (I can delete it anyway) and Lucid Try Ubuntu option is not restarting my PC any more like Karmic was. So it seems resolved for the next version.
Maybe you want to try out of curiosity, and if it still doesn't work it might be good idea to report it for your card while Lucid is still under development. Here in the Development section I think there is subforum for Lucid where you can probably report.

Enjoy Karmic now. :)

---

