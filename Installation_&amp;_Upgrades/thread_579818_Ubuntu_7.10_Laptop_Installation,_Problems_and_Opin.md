---
title: "Ubuntu 7.10 Laptop Installation, Problems and Opinions..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by BoardDWorld on 2007-10-18
Hello All,

Finally Ubuntu Gutsy Gibbon has officially been released, wasn't it fun trying to download! I had 5 or more servers close down on me, thank God for download managers!

I'm just going to share my initial experience of the installation onto my HP DV9224TX Laptop. It's not not quite the same experience I had several months ago when I tried Ubuntu Feisty which was just brilliant!

Booting up on the Live CD and I was confronted with a black screen with spots, I never had this problem with Feisty. This was simply resolved by loading in VGA safe mode. The installation went well other than it couldn't retrieve the APT security updates(I did have the internet running) which made the install more prolonged.

After the installation I immediately checked my Brother DCP-115C Printer, it has been installed as either a laser printer or copier as it has toner adjustments and very few other options, the DCP has many! Of course the test print doesn't work... It shouldn't be long and I'll have this resolved with a Brother CUPS driver, though on Feisty it started printing the page 3 inches from the top, hopefully it won't this time.

Next was to install nVidia's display driver. This went well which enabled me to use compiz-fusion but there isn't a settings GUI that I can find under system/preferences as  there was when I used the official repository from the link below on Feisty:

[http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository)

Also there's no cube by default how do I get it? I know there's the Configuration Editor but I wouldn't know where to start in there. What should I do? Is it safe to add the repositories above? Or is there some way to make the settings GUI show in the menu? Lastly on the subject of compiz the wobbly windows is very jagged and not at all smooth. I have never had this previously not even with all the constant updates, so it must be the nVidia driver??? I have a Geforce Go7600 with 1GB of VGA mem.

As with Feisty my built in Web cam doesn't work, unfortunately I'm finding it hard to track down a website I had found that supplied the needed driver. With it I had the web cam up and running brilliant on Feisty.

Other than the things mentioned everything is great. NTFS works swell as does all the other new features. WIFI works “out of the box” too as it did with Feisty.

That's about it for now, I have spent more time writing this than I have testing Gutsy. Any help with the things mentioned would be wonderful. 

P.S. Today marks the day I completely removed Vista, It's pure Ubuntu from now :popcorn:

---

### Post by mike.123850 on 2007-10-18
Not sure this will help, but type the following in a terminal window for Nvidia settings:

sudo nvidia-settings


Mike

---

### Post by mivo on 2007-10-18
> **BoardDWorld said:**
> Finally Ubuntu Gutsy Gibbon has officially been released, wasn't it fun trying to download! I had 5 or more servers close down on me, thank God for download managers!

The torrent works really well -- got it with full speed very quickly. Right now there are 2480 seeders and some 3000 downloaders, so it's a very healthy balance. :) Torrents are at the bottom of [this page]("http://releases.ubuntu.com/7.10/").

---

### Post by BoardDWorld on 2007-10-18
@ Mike Thanks but I mean the compiz settings GUI where you can control everything to do with compiz.

@ Mivo Too late now! hopefully others will clue up on it.

---

### Post by mike.123850 on 2007-10-18
Ok, then you might need to go to the synaptic package manager and get compizconfig-settings-manager. Don't quote me, do a little research on it first, but it might be that.

[http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide) ....... also has how to run the settings towards the bottom of the page I think.

Mike

---

### Post by BoardDWorld on 2007-10-18
Thanks Mike

---

### Post by mike.123850 on 2007-10-18
Ok, found help for you here:

[http://ubuntuforums.org/showthread.php?t=578937&highlight=compiz](http://ubuntuforums.org/showthread.php?t=578937&highlight=compiz)

Basically go to System ---- Preferences ---- Appearance 
While on the Theme "tab" click the Customize button at the bottom.

Mike

---

### Post by BoardDWorld on 2007-10-18
Thanks again but that thread comes to an end without any help, I will be watching it though. The system/preferences/appearance/customize doesn't have anything in regards to adjusting the compiz plug-in settings. It only controls the themes as it did previously but perhaps even in place of Emerald themes? I will find out soon. The only thing in relation to the compiz effects is the Visual effects tab but this is for a baby to play with. I want to be able to adjust all of the opening and closing effects and there duration, set the window dodge and all the other numerous settings there are.

I actually think at this stage it's not available, it's not installed and the package isn't available despite having the universe packages set.

---

### Post by BoardDWorld on 2007-10-18
Hello All, Just in regards to the compiz fusion manger problem it can be resolved with the following in terminal:

```
sudo aptitude install compizconfig-settings-manager python-compizconfig
```

Currently the "compiz-fusion-plugins-unofficial" package is not available but you could try it out at a later date with the "sudo aptitude install" command.

---

