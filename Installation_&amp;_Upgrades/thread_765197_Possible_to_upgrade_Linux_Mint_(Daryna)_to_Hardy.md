---
title: "Possible to upgrade Linux Mint (Daryna) to Hardy?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by britgamer on 2008-04-24
Hello all,

 I'm currently using Linux Mint Daryna which is based on Ubuntu Gutsy but I've decided I've had enough of it and would like to try Ubuntu Hardy.
 
 As far as I know Daryna is simply Gutsy with an extra repository which has Mint specific packages which take precedence over any Ubuntu package.  

 Does anyone know if I will be able to upgrade it Hardy if I remove/comment out the Mint repository and upgrade in the normal Gutsy to Hardy way? I've had a look round the forums (and around the Mint ones) but failed to find anything.

 I know a clean install would probably involve less pain but I've spent quite alot of time getting wireless working and changing config files etc to get it just the way I like it. Plus I am curious as to what will happen!

Any info would be much appreciated

Cheers


(I hope this is the right place for this question)

---

### Post by CyberCowboy on 2008-04-24
You probably/possibly could do it, but it is NOT recommended.  I've not used Mint so can't say for sure but if they have changed file system lay-outs, or any of about 100 things you could be in a world of hurt.  Sorry bud.

---

### Post by Joeb454 on 2008-04-24
I'd recommend you do a fresh install as CyberCowboy mentioned :)

It's not too difficult, just back up your /home directory and whatnot :)

---

### Post by CyberCowboy on 2008-04-24
> **Joeb454 said:**
> I'd recommend you do a fresh install as CyberCowboy mentioned :)

It's not too difficult, just back up your /home directory and whatnot :)

to save most of your configurations also backup your /etc directory

Not sure about MINT but in Ubuntu you can export a list of presently installed packages as well making it very easy to re-install the programs you're used to down the line (not sure how this would work across 2 different distro's)

And to help prevent problems in the future on this install make your /home it's own partition.  That way down the line you don't have to worry about backing it up.

---

### Post by bg1256 on 2008-04-24
Either wait until a new arrive of Mint is released or do a fresh install. Those seem like the only two sensible options to me.

---

### Post by britgamer on 2008-04-24
Well that seems pretty conclusive.

I know I should really have had a seperate /home in the first place, my desktop has and it does make things easier.

Thnkfully my customisations are only to do with one program so I'll back that up instead of the entirety of /etc.

If I have to backup everything anyway I may attempt it anyway, just to satisfy my curiosity and give others an idea of what will happen

---

### Post by mister_pink on 2008-04-24
I was going to say back up then do it anyway. It either works or doesn't, and if it doesn't then you can just reinstall which you were going to do anyway. I get the impression mint isn't really all that different. You might want to try and remove some of the mint only programs first.

---

### Post by britgamer on 2008-04-24
Well I don't actually use any of the mint programs (it's at least of part of why I want to upgrade). The only mint programs I know of are the mint installer (which is in addition to synaptic) and a few additions to Gnome, as I use a tiled wm and apt the vast majority of the time. If it's only these that mess up I probably wouldn't notice. 

I'll check to see what happens to them still if I try it out, I'm sure I'm abit of a rarity as a mint user!

---

### Post by bioborg on 2008-04-26
I just did a:
```
sudo do-release-upgrade
```

I am running Linux Mint Daryna.  This'll be my 5th Hardy upgrade.
We'll see how it goes.  Probably better than the one from edgy (which is going slowly but surely).

---

### Post by CyberCowboy on 2008-04-27
I'd be interested to know how it goes, I've got a Debian Woody server that I'd like to move over to Ubuntu but it's got about 3 TB of data that I presently have no where to move it too.

---

### Post by mister_pink on 2008-04-27
I don't think Debian -> Ubuntu is going to work very well, they're too different I'd think. I'd suggest making a new partition for ubuntu and keeping your obscene amounts of data separate. When you create the partition you'll have to select where it goes carefully, otherwise you could end up moving all that data down the disk which would take... well forever. I'd guess that making a partition at the end would cause less trouble.

I always have this trouble, everyone says backup, backup, backup! but its very difficult when you have that much data! I just have to backup really vital things.

---

### Post by mister_pink on 2008-04-27
Edit: Whoops, forum funkyness! Is there a delete post button?

---

### Post by CyberCowboy on 2008-04-27
yea the previous admin setup the drive structure and only made 2 partitions on the raid 5 swap and / so all of the data is on the / partition as well so I can't easily move it since combined I've only got about 5 TB of disk space.  (we do video editing), I could over an extended weekend do a dump to tape and then restore, but with this much data I'm not sure I would have the time to backup everything, make the switch to U and then restore before the users come back....  Anyone have suggestions (Not trying to hijack, may start new thread)

---

### Post by britgamer on 2008-04-28
OK I've just completed the upgrade (I sent it downloading overnight) and provisionally it seems to have worked...mostly.

After I removed the mint repo I had to download ubuntu-desktop before it allowed me to upgrade and I had update-manager crash on me a couple of times, both when downloading and whilst configuring the programs. After it crashed whilst configuring it wouldn't start again so I had to use "dpkg --configure -a" to carry on.

It's finished now and all I've noticed is:

wicd has been removed and replaced with gnome-network-manager but I think this is due to wicd being on a 3rd party repo and gnome-network-manager being in ubuntu-desktop

The mint menu bar wasn't removed neither was the mint update tool, however some of the linux mint programs in the menu bar have been and their entires are now squares and the second column of the mint menu bar doesn't work

The hardy theme hasn't been loaded, instead the mint theme is still in place (although I don't know whether the hardy theme should have been loaded by default or not)



I'll carry on using it today and post again if I find anything else that's changed

---

### Post by britgamer on 2008-04-28
Just a couple more things. I've been using it all day and the only other problems I've had have been:

The changes I made to wmii's wmiirc file didn't work, I think this got updated so I'm not entirely surprised

When I first turned it on the startup sounds were abit garbled, I looked at alsamixer and it said the PCM was set to 628%. The sound was fine after this was set to a sane value



I'm actually pretty surprised at how well the upgrade went, though I wouldn't recommend it for any PC with important information on it

---

### Post by bioborg on 2008-04-30
Everything went fairly smoothly.  I said Y, or I nstall package maintainers version, for every conf file it asked me about.  Currently I am at 800x600 resolution, and the start menu doesn't work very well.  I went ahead and did a ```
sudo apt-get install ubuntu-desktop
``` next.  It's installing a whole bunch of packages now.  After it's done, I'll see what I cant do about Nvidia drivers and screen resolution and getting the bars in the right places and such.  Might have been easier to go Kubuntu, and have the kde start fresh, I think in retrospect.  I think I will also get rid of any of these packages I still have:
mintupdate - Linux Mint Update Manager
mintdesktop - makes the most out of your Gnome desktop
mintartwork-bianca - Bianca's artwork.
mintupdate-gnome - Gnome Menu Entry for mintUpdate
mintassistant - first run assistant for Linux Mint
mintwifi - Collection of drivers for you to configure your WIFI card through ndiswrapper without connecting to the Internet.
mintupload - Uploads files on the Internet
mintassistant-gnome - Gnome integration for mintAssistant
usplash-theme-mint - Usplash theme for Linux Mint
mintmenu - The Linux Mint Menu for Gnome
mintinstall - The Linux Mint Installer

I will post again soon, with more results.

---

### Post by bioborg on 2008-04-30
I would upgrade your Woody server to Etch and be happy with that, if you can't move the data.  I foresee possible issues.  There were people trying to upgrade woody to warty, I think that can be done, but then you have to upgrade warty to hoary to breezy to dapper, then dapper to hardy:
[http://ubuntuforums.org/showthread.php?t=163631](http://ubuntuforums.org/showthread.php?t=163631)
sounds like a serious pain. I just upgraded Etch to Hardy on an older laptop, and it took forever (well, some of it was because I spilled tea on the keyboard and had to turn it off and take it apart and dry it, but it's in the final stages of gutsy-hardy right now.  kick *** toshiba portege 3480ct!)

---

### Post by bioborg on 2008-05-02
So, the upgrade from Mint to Hardy went pretty smooth, after my previous issues I installed ubuntu-desktop and uninstalled everything mint I could find... but was unable to get the gnome desktop looking how I wanted it to. I dragged the bar up top, put a new one in the bottom, but am having trouble moving stuff around to my liking, so I installed kubuntu-desktop .

Everything looks great in Kubuntu, seems to be a success

---

### Post by mick222 on 2008-05-17
i did it compiz doesn't work removed mint install and mint tools otherwise ok . new mint is out based on ardy i think.

---

### Post by mick222 on 2008-05-17
how do i get the hardy theme just need it to show friends what I'm running all windows users .

---

### Post by Oldsoldier2003 on 2008-05-17
> **mister_pink said:**
> I don't think Debian -> Ubuntu is going to work very well, they're too different I'd think. I'd suggest making a new partition for ubuntu and keeping your obscene amounts of data separate. When you create the partition you'll have to select where it goes carefully, otherwise you could end up moving all that data down the disk which would take... well forever. I'd guess that making a partition at the end would cause less trouble.

I always have this trouble, everyone says backup, backup, backup! but its very difficult when you have that much data! I just have to backup really vital things.

I agree about the Debian -> Ubuntu swap. Also tbh for a server Debian is way better than Ubuntu and much more stable. I've tried Ubuntu on my server and found that Debian just works better- I won't be using Ubuntu on servers anytime soon... like say the next several years...

---

