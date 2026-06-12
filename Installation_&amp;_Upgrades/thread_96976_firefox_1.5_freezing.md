---
title: "firefox 1.5 freezing"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by Chippendale on 2005-11-30
so i installed ff1.5 using this guide

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

and then suddenly, it freezes up.... making me reboot (reset, pushing the button) on my computer... its only been a couple hours since i install 1.5...

has this happened to anyone else??

---

### Post by Hobbes on 2005-11-30
yea it just started happening to me.  Not sure if it's one of the extensions i recently installed or just the newest 1.5, but its happened a couple times in the last few hours.

I'm going to go back to 1.0.7 for now, but if you figure out what's causing it maybe I'll switch back.

I recently installed: Colorful Tabs and De.lici.ous, maybe updated some others, not sure.

Good Luck!

---

### Post by Chippendale on 2005-11-30
it's probably just 1.5 itself. i have other extensions installed 

ill let you know if i find anything

---

### Post by jrib on 2005-11-30
This hasn't happened to me.  I used it since beta1 too and it never froze on me.  Can you list your extensions?

---

### Post by Chippendale on 2005-11-30
ImageZoom  0.2.1

CustomizeGoogle 0.39

BookmarkBackup 0.3.3

Adblock 0.5.2.39

Super DragAndGo 0.2.4

MediaPlayerConnectivity 0.4.9.4

those are the ones i installed besides the other 2 that came with 1.5

Talkback and DOM Inspector

---

### Post by jwd45244 on 2005-11-30
Do you have an Nvida Graphics card?  If you don't have the right drivers many apps that "scroll" like Firefox can lock up.  The instructions are in the Help documentation in the Ubuntu Startup Guide in the hardware section.

---

### Post by Chippendale on 2005-11-30
i have an Ati radeon 9800 pro 128mb with the latest fglrx drivers

---

### Post by AmboyGuy on 2005-11-30
[B]Chippendale try uninstalling AdBlock and get Adblock Plus if you need the functions.

If you look in the Mozillazine Builds forum ( [http://forums.mozillazine.org/viewforum.php?f=23]("http://forums.mozillazine.org/viewforum.php?f=23") ) at the 'Official build is out...' topics this is headlined right on the first page.
I can't seem to connect to the site right now, seems they're down. Maybe to help with downloads of the new release of 1.5 ???

Another problem might be your profile. Try creating a new one using the -p option for 1.5.

1.5 might work fine with a 1.0.7 profile but 1.0.7 will surely puke on the changes 1.5 will make to it's profile.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9a1) Gecko/20051130 Firefox/1.6a1
[/B]

---

### Post by mc_bizon on 2005-11-30
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) :

> Notes

    * You will no longer get automatic updates through the repositories (but firefox itself has a built into auto-updater).
    * The Totem video plugin doesn't seem to work with firefox 1.5. You may want to install package 'mozilla-mplayer' instead before you start.
    * You need package 'libstdc++5' installed.
    *** If you are using scim-1.0.2 as your input method platform, firefox will crash on startup.**


maybe thats the reason

---

### Post by Chippendale on 2005-12-01
thanks guys everythings working fine now :D

---

### Post by Hobbes on 2005-12-01
hmm it appears it isn't firefox itself, as i have now gotten crashes (and im talking full system hangs, can't even get to anything, must hard reboot) from opera and synaptic...

I did recently switch out my 9800 pro for a geforce4, so I will look into the nvidia bug listed above.

Thanks for your help.

---

### Post by Treviño on 2005-12-15
[QUOTE=Chippendale]thanks guys everythings working fine now :D[/QUOTE]
How have you solved?

I've the same problem both with Firefox 1.5 and Thunderbird 1.5 (RC1).  I simply can't browse, because firefox freezes and cpu use increases, btw I can still use my system.

Any suggestion? I've tried some build of Firefox, now I'm using a self-compiled one, that btw it's faster when it doesn't freeze... :(

PS: I'm using ATI's fglrx drivers, 8.19.10, not the latest, but I don't think that upgrade could fix anything... I'm saying this because from [here]("http://www.ubuntuforums.org/showpost.php?p=356725&postcount=7"), it seems an important thing...

---

### Post by Treviño on 2006-02-03
Isn't anyone with this problem?? I always have it with stable thunderbird 1.5 and firefox 1.5.1...

Page freezes some seconds and after it scrolls up to the beginning of the page... :|

---

### Post by Treviño on 2006-02-11
I think that I've **solved** that problem... I'm using Kubuntu and before I used the Window style called "Keramic", and to add the same theme to gtk applications I used gtk-qt-engine. Now I've changed theme using the really good style called QtCurve (look for it in kde-look) that includes both gtk-1.x, gtk-2.x and Qt themes, so I've a great graphic in all qt and gtk applications with no freezing problems in Thunderbird and Firefox >= 1.5 ;)

Bye!

---

### Post by ita on 2006-02-21
hi all ...

im pretty new to linux (like a year) and very new to (k)ubuntu .. like for 1 week now.

i also followed same install help for the firefox 1.5.0.1 .. actually at this very moment im posting this reply from within my firefox 1.5.0.1 ... 

my problem is: firefox freezes from time to time .. i did nothing special - just normal usage of firefox and the net like i did for the last week with the "old" firefox (which was rock solid). since the upgrade this morning firefox froze 5 times .. i click a link, or open new tab - HALT! ... kde lets me minimize/maximize window, but the app is gone .. i have to kill firefox and restart it. 

i followd the extended documentation for installation, i already had the libstdc5 installed and i dont use SCIM (whatever that is - my adept tells me all packages called *scim* are NOT installed).

since i dont want to downgrade again i asked on kubuntu channel on freenode where i was sent here. 

anyhelp is greatly appreciated cause i need to do webstuff and for now im back to konqueror. and no! i dont want to hear my windows using colleagues say "use iexplorer heeeheeeheee" everytime they pass my desk.

thanks in advance!
-ita

---

