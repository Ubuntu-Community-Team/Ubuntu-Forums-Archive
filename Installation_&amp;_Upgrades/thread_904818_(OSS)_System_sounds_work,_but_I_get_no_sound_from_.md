---
title: "(OSS) System sounds work, but I get no sound from any vidoes (flash or other)"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by javaikky on 2008-08-29
Edit : I accidently put this in the wrong section! sorry.  Is there any way for me to move this ? Or should I post fresh in the multimedia forum .

I'm fairly new to the Linux side of the world, but I've been heavily involved with IT, and Windows for many years, and I consider myself above average in just about everything but Linux lol.  
  I don't usually like to have to ask for help, but I'm completly stumpped and don't know what to do. 

  
 I am using 8.04 and I have an XI-FI extreme audio card, and rather than go with Alsa, using OSS seemed to be the easier path.  

   My first 8.04 install went very well, I had the sound work in just about everything but .WMV. I had all my applications from work running ( Remedy, Lotus Notes 8.01, Juniper network connect ect) with no problems. 

   However, during my quest to get WMV files to play correctly, I inadvertently screwed something up and broke my sound completely. 

    With nothing left to do, I backed up, and reinstalled the OS. 

    I proceeded just as before, installed OSS, went through all the configs described in this article  "http://ubuntuforums.org/showpost.php?p=4874981&postcount=2". 
     
    I did nothing different from the first time, but for some reason I can get no sounds while playing any video.  Not Flash, or any other format. 
     
    I've scoured these forums, but I have been unable to find any solution, at least not one I am able to understand.  
   
    I've tried multiple players,  VLC, MPlayer, Gnome Mplayer, Totem, Kaffiene, Movie Player, etc but nothing is working. 

    I go to system/preferences/sound/ and I set everything to auto detect, and everything will test out ok .  

   However I do notice, that OSS is not in the list.  I find this very odd, as if I select any of the options aside from auto detect, the test will fail . 

   Please if at all possible help me.  

   I have completely made the switch to Linux, and I haven't looked back till now. 

   Any info/advice is greatly appreciated. 

    Either way, anyone who reads this post have a great holiday, and try not to eat to much on Monday.  

   Kind Regards, 
   
     Mike

 PS: I did replace the libaudio file with the OSS version.

---

### Post by iaculallad on 2008-08-29
Had you tried installing the Restricted codecs?

Add the Medibuntu Repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O
/etc/apt/sources.list.d/medibuntu.list
```

now, add the keyring:

```
sudo apt-get install medibuntu-keyring && sudo aptitude update
```

Install Flash:

```
sudo apt-get install flashplugin-nonfree
```

Install codecs:

```
sudo apt-get install w32codecs
```

the DVD packages:

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4
```

You might be needing to install the flash plugin wrapper:

```
sudo apt-get install libflashsupport
```

---

### Post by javaikky on 2008-08-29
Thanks for info sir. I will attemp to validate first thing am

---

