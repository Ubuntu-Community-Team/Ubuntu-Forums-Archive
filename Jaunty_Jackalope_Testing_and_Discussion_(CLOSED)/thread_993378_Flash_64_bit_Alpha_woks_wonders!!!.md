---
title: "Flash 64 bit Alpha woks wonders!!!"
date: 2008-11-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Trueno22 on 2008-11-25
I just installed the Alpha of the 64bit Flash and to my surprise it works way better than the emulated stable 32bit Flash.  

Should I continue using the 32bit for the sake of testing?

---

### Post by Slug71 on 2008-11-25
I would continue using the 64bit.
I'd probably even install FF-3.1 and use it with that since Jaunty will probably ship with FF-3.1.

---

### Post by ronacc on 2008-11-25
since you are 64bit I would continue with the 64 bit flash I intend to , I'm sure it will be the default for 64bit soon .

---

### Post by Slug71 on 2008-11-25
I will try it out with FF-3.1 as soon as i do a fresh install since Grub2 broke my broke my Jaunty. Well i kinda forgot to rename the drives first.

FF-3.1B2pre works pretty well too.

---

### Post by dakkar9999 on 2008-11-25
Could you give link for download and install instructions?  Thanks!

BTW, how can I tell if Firefox is running in 32 or 64 bit?

---

### Post by syko21 on 2008-11-25
Firefox -> Help -> About

```
Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4
```

---

### Post by dakkar9999 on 2008-11-25
Thanks!  Now I know i'm running 64 bit as well!  Just need the link and installation info!

Cheer!

---

### Post by Slug71 on 2008-11-25
> deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main

If you add that to your sources, then type firefox 3.1 in Synaptic it should be there.

DONT do the updates in update manager that come through when you add that to the sources list.
Do it with Synaptic or add/remove if you're using Packagekit.

---

### Post by ronacc on 2008-11-25
look here for the d/l link and instalation instructions .
[http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)

---

### Post by dakkar9999 on 2008-11-25
Well,  I did the Firefox 3.1 install from Synaptic.  It shows as being installed, but my browser still shows 3.0.4 Canonical 1.0 even after computer restart...

---

### Post by BwackNinja on 2008-11-25
Its installed separate from regular firefox. It'll be called "Shiretoko" or "Minefield" in Applications > Network.

---

### Post by ronacc on 2008-11-25
see screenshot I am posting from it now:)

---

### Post by ktp on 2008-11-25
I am loving the 64-bit flash support too.  It really works nice.  No reall big issues so far.  This really shows that Linux is picking up or why would Adobe release a 64-bit version on it; even before Windows and Mac??? :)

---

### Post by ronacc on 2008-11-25
because they're using us as a guinea pig so they don't break OSX:lolflag:

---

### Post by phenest on 2008-11-26
Will 64 bit Flash be packaged for Jaunty? I'm using it now, and it's very good.

---

### Post by ronacc on 2008-11-26
go ahead and put it in for inclusion , so far I haven't seen any posts from people who have tried it that haven't had good results.

---

### Post by dakkar9999 on 2008-11-26
Yup, got it.  How can i tell Shiretoko to use the 64bit Flash file?  Because I think it's using the 32 bit one.  It's kind of a jerky playback.  Also, both in Firefox and Shiretoko, I cannot playback in full screen.

And my sound does not work.  But that's another problem.  I think that's from the latest ALSA update...  my soundcard (M-Audio Revolution 7.1) does not show up in the playback options...  only in the capture.

---

### Post by phenest on 2008-11-26
> **ronacc said:**
> go ahead and put it in for inclusion , so far I haven't seen any posts from people who have tried it that haven't had good results.

How is that done? Never done it before.

---

### Post by plun on 2008-11-26
Request is filed already

[https://bugs.launchpad.net/bugs/299146](https://bugs.launchpad.net/bugs/299146)

The Debian bug seems to be "untouched"...

---

### Post by pferraro on 2008-11-26
> **dakkar9999 said:**
> Well,  I did the Firefox 3.1 install from Synaptic.  It shows as being installed, but my browser still shows 3.0.4 Canonical 1.0 even after computer restart...

Installing firefox-3.1 does not replace the old version.  Try ALT-F2, then type firefox-3.1.

---

### Post by Progressive on 2008-11-26
I am having some problems with it in Firefox. It won't recognize my flash plugin on [www.imeem.com](www.imeem.com)

It does recognize it in Konqueror. I have had this problem with a few other sites too, not just imeem. Forget which ones though...

Anyone else having the same problem?

---

### Post by philinux on 2008-11-27
Just installed Jaunty alpha1 . Got the 64bit flash and it's working ok. The site you mention works ok here.

---

### Post by luceerose on 2008-11-27
Hey,
I just installed flash in jaunty.
Once I figured out where the mozilla/plugins folder was it took seconds.
Too easy.

Any of you know how to install DVD playback ???
I've installed Totem-Xine as a start, but I imagine I will need libdvdcss2 or similar along with some others ?

EDIT: Also [as this is installed on my crappy machine], Does any1 know how I might get a functioning ATI driver ???
I have never installed an ATI driver under Linux before, as I [almost] always use nvidia.

---

### Post by philinux on 2008-11-27
I install ubuntu-restricted-extras then purged flash and nspluginwrapper.

You need medibuntu click the link.

Change intrepid to jaunty to add the repo list.

---

### Post by ktp on 2008-11-27
I have been using the ATI drivers and they are really easy to install...I mean ubuntu does all the work.

---

### Post by MacUntu on 2008-11-28
Does it still have problems with special characters?

You can test it here: [http://www.get-the-flash.de/tutorials/textfeld.swf](http://www.get-the-flash.de/tutorials/textfeld.swf)

---

### Post by GSMX on 2008-11-28
I haven't had any problems with this alpha, great work from Adobe, i'm starting to like that company again :P

> **MacUntu said:**
> Does it still have problems with special characters?

You can test it here: [http://www.get-the-flash.de/tutorials/textfeld.swf](http://www.get-the-flash.de/tutorials/textfeld.swf)
I tried ï ñ ë and they don't work, but I kind of doubt the greatness of this particular application, AFAIK if the flash app just uses UTF-8, everything should work fine

---

### Post by zika on 2008-11-28
can it be used in Intrepid? whar are the benefits using this 64bit flash instead of 
File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r12?

when You gave a code for making a change did You have this plugin in mind?

---

### Post by ronacc on 2008-11-28
works great in intrepid , just purge flashplugin-non free first and delete nspluginwrapper .

---

### Post by zika on 2008-11-28
is this the right peace of code for what You have suggested:

```
sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
(create plugins dir if it doesn't exist)
```I've edited this message several times while testing it and it works! both this peace of code and plugin!

Thanks!

---

### Post by ktp on 2008-11-28
similar to what I did and works great in intrepid

---

### Post by MacUntu on 2008-11-28
> **GSMX said:**
> I tried ï ñ ë and they don't work, but I kind of doubt the greatness of this particular application, AFAIK if the flash app just uses UTF-8, everything should work fine

Thanks. Too bad "should work" is not enough:

[http://bugs.adobe.com/jira/browse/FP-40](http://bugs.adobe.com/jira/browse/FP-40)

That's a really annoying bug.

---

### Post by yostral on 2008-11-28
> **zika said:**
> 
```
...
sudo wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
sudo tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
```


Why sudo ? You don't need !

And even the last command line, you can just copy the .so file to ~./mozilla/plugins (create plugins directory first).

Don't use sudo when you don't have to :).

---

### Post by plun on 2008-11-28
> **yostral said:**
> 

Don't use sudo when you don't have to :).

No... you can do everything with Nautilus....:)

Right click unpack and Ctrl-H and just drag & drop with Nautilus...:-({|=

---

### Post by zika on 2008-11-28
> **yostral said:**
> Why sudo ? You don't need !

And even the last command line, you can just copy the .so file to ~./mozilla/plugins (create plugins directory first).

Don't use sudo when you don't have to :).

You are totally right! I was editing that piece of 'code' several times and finally I added that sudo eventhough I did not use it myself ... silly me ... :) I will try next time to make as short code as humanly possible as I do try (almost) always ... :)

have a good night or whatever ... :)

---

### Post by c-m on 2008-11-28
everyone mentions removing flashnonfree but I never had that installed as it was. I followed a howto on these forums and installed flash 10.

I installed this new 64-bit version and although it works i.e i don't get grey boxes anymore etc.. playback on iplayer is jerky

---

### Post by luceerose on 2008-11-30
Do you guys get the impression that the final release of jaunty might be coming with 64-bit flash included ???

---

### Post by Gina on 2008-11-30
Well it should do!

---

### Post by zika on 2008-11-30
> **Slug71 said:**
> If you add that to your sources, then type firefox 3.1 in Synaptic it should be there.

DONT do the updates in update manager that come through when you add that to the sources list.
Do it with Synaptic or add/remove if you're using Packagekit.

Does this work on Intrepid? Should "jaunty" be substituted with "intrepid"? I tried Shiretoko bu simply unpacking the archive. It ran flawlessly but asked for every single plugin. I did not sucumb and simply erased it ... ;) If I install it this way will it update every day or so as development progresses?

---

### Post by xebian on 2008-11-30
> **larsenguitars said:**
> Do you guys get the impression that the final release of jaunty might be coming with 64-bit flash included ???

No and never unless Adobe and Ubuntu agree to a re-distribution which I doubt.

But Adobe does not stop you from installing in any Ubuntu 64-bit OS be it be dapper, edgy, feisty, gutsy, hardy, intrepid or jaunty.

---

### Post by xebian on 2008-11-30
> **Gina said:**
> Well it should do!

Can't do.  See my post above.

---

### Post by ronacc on 2008-11-30
would Adobe object to a script that downloaded and installed it from their site like Suse used to do with the Nvidia drivers ? 
that way Ubuntu would not actually be "redistributing" it.

---

### Post by xebian on 2008-11-30
> **ronacc said:**
> would Adobe object to a script that downloaded and installed it from their site like Suse used to do with the Nvidia drivers ? 
that way Ubuntu would not actually be "redistributing" it.

Didn't I say '.. Adobe does not stop you ..'  :confused:

---

### Post by Gina on 2008-11-30
Maybe that's the answer :)

---

### Post by zika on 2008-11-30
> **Slug71 said:**
> If you add that to your sources, then type firefox 3.1 in Synaptic it should be there.

DONT do the updates in update manager that come through when you add that to the sources list.
Do it with Synaptic or add/remove if you're using Packagekit.

I've tried this today but the repo-s are empty? yes, I've checked under intrepid and under others ...

it seems that the (empty repo)-virus is spreading from the openoffice repo ... :)

---

### Post by uBeer on 2008-11-30
> **ronacc said:**
> would Adobe object to a script that downloaded and installed it from their site like Suse used to do with the Nvidia drivers ? 
that way Ubuntu would not actually be "redistributing" it.

You can see in the output in the command line that if you are installing the flashplayer-nonfree package (or whatever it's called), it will get the player from Adobe's website, so actually the package ís a kind of script already ;) It just checks if the md5 in the deb package is the same as the file downloaded from Adobe. I found out when there was some trouble with a mismatch...

But all this talking about flash 64 bit makes me wanna switch to 64, maybe during the Christmas days...
:popcorn:

---

### Post by Slug71 on 2008-12-01
> **zika said:**
> I've tried this today but the repo-s are empty? yes, I've checked under intrepid and under others ...

it seems that the (empty repo)-virus is spreading from the openoffice repo ... :)

I think it may be in the Jaunty repo's as of today.

---

### Post by phenest on 2008-12-01
Hmmm. It has some issues on some sites, e.g. [http://www.bbc.co.uk/doctorwho/]("http://www.bbc.co.uk/doctorwho/")

---

### Post by Gina on 2008-12-01
Well, that one works fine for me :)  nvidia GeForce 6200 running 177 driver - 22" WS LCD screen.

---

### Post by ronacc on 2008-12-01
what I can get off the site works ok for me with the 180.08 driver and 7600gs I can't get most of the videos because I'm in the US :mad:

---

### Post by Gina on 2008-12-01
Just installed Firefox 3.1 and it's still working fine in that :)

---

### Post by FlareHeart on 2008-12-01
Hey there guys, I am hoping you can help a newb like me out. 

I have a fresh install of Kubuntu 8.04 (I didn't like KDE4) and when I copy the extracted flash plugin to the plugins folder (inside the hidden .mozilla folder of course) and then open FireFox and check in the plugins it is not recognized. I even tried manually placing the plugin file into the /usr/lib/firefox-addons/plugins and it still won't work. 

I have rebooted my computer after both times and FireFox was not running during either one of the file placements. Why won't my FireFox see this plugin? 

FireFox version: 3.0.4
Kubuntu Version: 8.04
Computer Specs:
AMD Phenom 9600 Quad Core CPU
NVIDIA GeForce 9600 GT Sonic (1 GB of Video RAM)
4 GB of OCZ Reaper HPC RAM (DDR2 1066)
500 GB Seagate Barracuda HDD (SATA)
LG GSAH22N DVD/CD RW Drive
Dell 22" Widescreen monitor


UPDATE: I have now also tried placing it into the /usr/lib/mozilla/plugins and that did not work either. I'm running out of ideas! Can anyone help?

---

### Post by ronacc on 2008-12-01
mine is in /usr/lib/mozilla/plugins

---

### Post by FlareHeart on 2008-12-01
Thanks for the help ronacc...I have discovered that if I place it in both my home folder .mozilla/plugins and the usr/lib/mozilla/plugins at the same time, it is now enabled. Now to go test it out. I'll be back soon with an update!

UPDATE: Youtube seems to work OK. Still needing to do some more extensive testing though.

---

