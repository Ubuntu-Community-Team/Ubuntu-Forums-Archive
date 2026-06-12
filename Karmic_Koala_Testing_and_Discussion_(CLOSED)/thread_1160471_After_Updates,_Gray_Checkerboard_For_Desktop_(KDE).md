---
title: "After Updates, Gray Checkerboard For Desktop (KDE)"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-05-15
I installed the 9.10 Alpha for Kubuntu which seemed to go pretty well for an Alpha.  However after the first available updates, once rebooted, all I have for a desktop background is a gray and white checkerboard pattern.  The icons on the taskbar are a bit skewed, but work okay, as does the Menu.  Applications open fine...just seems to be the background.  I tried two or three installs and get the same thing...and have continued doing updates but no change.  I have the Nvidia driver installed for the Nvidia 8400GS video card.  I tried the updates before installing the video driver and had the same situation.

Anyone else experiencing this, or can someone give me an idea as to what I might try to get the regular desktop back?  I can't right click on this checkerboard and get to where wallpaper or themes can be changed.

Thanks,
zenarcher

---

### Post by fifth on 2009-05-15
> **zenarcher said:**
> I installed the 9.10 Alpha for Kubuntu which seemed to go pretty well for an Alpha.  However after the first available updates, once rebooted, all I have for a desktop background is a gray and white checkerboard pattern.  The icons on the taskbar are a bit skewed, but work okay, as does the Menu.  Applications open fine...just seems to be the background.  I tried two or three installs and get the same thing...and have continued doing updates but no change.  I have the Nvidia driver installed for the Nvidia 8400GS video card.  I tried the updates before installing the video driver and had the same situation.

Anyone else experiencing this, or can someone give me an idea as to what I might try to get the regular desktop back?  I can't right click on this checkerboard and get to where wallpaper or themes can be changed.

Thanks,
zenarcher

Same all round I think.

KDE is being upgraded, be patient and check the updates when available. When all updated packages are uploaded all should be good again with extra KDE 4.3 goodness.

btww, logging in from a gnome koala and first looks its still not pretty ;) and please don't flame me ;)

---

### Post by vikrant82 on 2009-05-15
Damn ... 

My KDE crashed on me in evening. I had been banging my head ever since. I thought the crash corrupted some files. 

I deleted all configs, reinstalled everything. Literally banging it. In shock, awe and frustration i even deleted all my configs :(

Anyways, plasma is crashing. Try posting your .xsession-errors

I have made a post regarding same in [kubuntuforums.]("http://kubuntuforums.net/forums/index.php?topic=3103908.msg181289#msg181289")

---

### Post by vikrant82 on 2009-05-15
Somehow I managed to pity my amarok configs, and saved all my years of stats. Got to be more patient with these alphas :P

---

### Post by caryb on 2009-05-15
I have trhe same problem + my laptop can no longer used as it was intended! it is so hot I cant stand it being on me. I am now using aggressive power saving mode so it doesn't give off the burning smell. on investigation I find this in top all the time...
```
 4660 cary      20   0  722m  71m  28m R   57  3.6   4:24.89 plasma
 4043 root      20   0  320m  91m  10m R   41  4.7   3:23.43 Xorg

``` 

Plasma & xorg are using 100% cpu

Cary

---

### Post by zenarcher on 2009-05-15
Thanks so much for the feedback!  At least I know I'm not alone!  I'm sure it will be sorted out pretty soon with updates.  I'm pretty patient with the testing stuff, as I'm retired and keep one computer just for testing new stuff...so I don't mind when I have to do a reinstall or wait for update fixes.  I just like knowing I'm not alone!

Regards,
zenarcher

---

### Post by caryb on 2009-05-15
In my impatience I ran the following to install some of the constipated packages, it did not fix the problem but it did install a lot of 4.3 stuff sitting in the wings.
```
sudo apt-get -f install
```  
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/*.deb

```
```
sudo apt-get -f install
```
```
sudo reboot
```

Cary

BTW this is not for the faint hearted:-)

---

### Post by skierkyles on 2009-05-16
Still broken for everybody else?

Still broken for me.

---

### Post by vikrant82 on 2009-05-16
Are you also using kubuntu-experimental PPA ?

---

### Post by ruik on 2009-05-16
Broken here too.. using kubuntu experimental ppa.

---

### Post by fifth on 2009-05-16
Yep still broken, not using any ppa's, just the karmic repos. Have forced the install of the problem packages but no change yet.

---

### Post by zenarcher on 2009-05-16
Still broken here for me, as well and I'm not using any experimental PPA's.  Currently, I have 24 blocked packages and one which isn't blocked but won't install.

Cheers,
zenarcher

---

### Post by skierkyles on 2009-05-16
> **vikrant82 said:**
> Are you also using kubuntu-experimental PPA ?

No im not, but I did do what caryb did, and its still broke.

---

### Post by ruik on 2009-05-16
[https://edge.launchpad.net/~kubuntu-ppa/+archive/experimental](https://edge.launchpad.net/~kubuntu-ppa/+archive/experimental) doesn't have any karmic packages anymore:?:

---

### Post by brm on 2009-05-16
I have had the same problem.

This was the second day of the new development cycle and the first day the KDE 4.3 beta was released from experimental into broader consumption.

"dpkg -i --force-overwrite" will install blocked packages, but it will take more than that to bring back the broken Plasma components. I suspect that will come in the next round of updates. In the meantime, I see no need for anyone to reinstall or to nuke their configs. (BTW, I saved my current config and tried a new one just to be sure. That didn't work either, so I restored the existing one.)

---

### Post by vishalrao on 2009-05-16
Just went to the #kubuntu-devel IRC channel on Freenode to snoop on devs' chat :) Looks like they're still working on fixing breakage and uploading the remaining 4.3 beta1 packages so it should be here soon enough, I just hope I can get to try out before Monday...

---

### Post by caryb on 2009-05-16
> **vishalrao said:**
> Just went to the #kubuntu-devel IRC channel on Freenode to snoop on devs' chat :) Looks like they're still working on fixing breakage and uploading the remaining 4.3 beta1 packages so it should be here soon enough, I just hope I can get to try out before Monday...

In the meantime watch your cpu temp with plasma in it's stuffed state! If you are on a laptop select the battery symbol in the task bar & select aggressive powersave mode & that will keep the cpu from frying,


Cary

---

### Post by zenarcher on 2009-05-16
More updates just came through and I installed them.  That really borked the system.  After rebooting, I was left with nothing but a black screen...I had gkrellm installed and that was all I could see on the totally black background.  I just went back to square one and did a fresh install.  Think I'll sit with that until I see someone posting here that everything is working again after updates.

Cheers,
zenarcher

---

### Post by xebian on 2009-05-16
Just updated, and looks like everything seems to be working ok now.

---

### Post by vishalrao on 2009-05-16
Its now working better (desktop wallpaper etc okay) but aptitude still shows some errors installing packages and some held-back etc... so still not all-clear :D

---

### Post by zenarcher on 2009-05-16
I think I'll wait until tomorrow, just to be on the safe side...then try the updates again.

Thanks for the info!
zenarcher

---

### Post by brm on 2009-05-16
I am writing this at 20090517T0100 UTC which is 9:00 p.m. Saturday evening EDT in my part of Canada (and the USA).

The updates must still be propagating around the world and apparently have not yet reached the North American pool of Ubuntu servers. My understanding is that Canada and the USA are a pool of load-balanced servers. I remember once pinging ca.ubuntu.com and us.ubuntu.com and got back the same IP address.

Many (perhaps all) of the current broken packages arise from the same file appearing in more than one package. That is a no-no in the APT packaging system which requires every system file to be contained in one and only one package. This is an easy error to make at the time of a massive transition such as from KDE 4.2 to 4.3 (admittedly beta). It too will resolve in short order. In the meantime, one can go into the /var/cache/apt/archive directory and run sudo dpkg -i --force-overwrite <stem>*.deb on the broken packages.

---

### Post by brm on 2009-05-17
Wandering somewhat OT:

As expected, the updates reached the North American server pool shortly after I posted the preceding message.

Final configuration and setup of many KDE 4.3 beta packages continues to be hampered by the problem of duplicate files: the same file, perhaps something as small as an icon graphic, being inadvertently included in two packages. If one of those packages is a core file, it might block configuration of much of the update.

In circumstances such as this, there is no risk (at least, none that I know of) to the stability of one's system in "forcing" the update.

My own experience is that I have done this many times over several years. I have never had a problem. While that is not in itself a convincing argument, analytically, a duplicate support file should not pose a risk to system stability.

---

### Post by caryb on 2009-05-17
Fixed for me at 8am EST (Australian) time you will have to do a dpkg force to install all the deps! I cant use any of my wallpapers but I do have all the widgets etc back & the default blue background:D


Cary

---

### Post by inportb on 2009-05-17
lol... i must have been fortunate; i jumped on the alpha bandwagon at 10 :p
oh well... plenty of other breakages to play with in the future *whistle*

---

### Post by zenarcher on 2009-05-18
Everything here has updated except I have kdeplasma-addons and avahi-daemon still sitting as blocked packages.  I haven't rebooted, however, for fear of losing everything again, until those are cleared to update.

Cheers,
zenarcher

---

### Post by dalamar666 on 2009-07-30
I had the issue as well with the gray checkerboard.  I went through using the adept package manager and removed everything plasma related.  When I was going through that I had a number of the plasma files that were damaged.  I tried to update those and got errors about the jaunty repositories not being able to find the files.  I was finally able to remove all of pulse.  I restarted x server and only got a black desktop and my mouse.  Amarok loaded and would load my playlists cause it was running when I restarted X.  From the login screen I tried a safe boot and it just came right back to the login screen.  I opened up console and tried a sudo apt-get install.  That went through looking for updates and tried to update but failed as well with the Jaunty links.

I am pretty sure that all of my settings are going to be ok because of what worked with amarok.  Does anyone know how to correct this without completely reinstalling?


On another note not sure if this is related or not, but after I ran the updates and before I reboot x.  I would try to empty the recycle bin and there were folders in there, it gave me errors about deleting the folders saying that it was expecting files instead of folders.  Then when I tried to delete files that were seperate it gave me an access denied error.

Any help will be greatly appriciated.  I really need to get some files and bookmarks saved and so a reinstall is not an easy option right now.

Thanks in advanced

---

### Post by dalamar666 on 2009-07-31
I FIXED IT!!!!!!

I have no clue how but I did and everything saved!

Here are some things I remember from the last 2 hours.

kdebase-runtime and kdebase-workspace-bin were corrupted.

I did multiple dpkg --force removes on it and sudo apt-get -f install I even did a sudo apt-get -f upgrade.  That failed then I did a sudo apt-get install and then another -f install and it works.  No errors came back in terminal that told me it was done.

I hope this will help others find a direction to go.  I apologize for my notes not being as perfect as they should be to guide others to the answers.

---

