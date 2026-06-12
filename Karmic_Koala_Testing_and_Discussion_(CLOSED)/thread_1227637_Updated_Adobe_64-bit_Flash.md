---
title: "Updated Adobe 64-bit Flash"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xebian on 2009-07-30
Get the new updated 64-bit Flash here

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by Arup on 2009-07-30
Many thanks for the update, was looking for it.

---

### Post by philcamlin on 2009-07-30
thnks for the info i should upgrade my grandmas now

---

### Post by quazi on 2009-07-30
Any idea of what this update's supposed to do?  Improved support for flash sure would be nice.

---

### Post by michaelzap on 2009-07-30
Excellent! All I did was to rename ~/.mozilla/plugins/libflashplayer.so to libflashplayer.old and copy the new file there. Relaunched Firefox and it Flash seems to be working much more reliably than the beta version I had before (no major CPU spikes so far).

---

### Post by Nburnes on 2009-07-30
Thank you for alerting us of the update. :popcorn:

---

### Post by quazi on 2009-07-30
I copied this version over to /usr/lib/flashplugin-installer/libflashplayer.so and it broke flash in both chromium and firefox.  What gives?

---

### Post by darco on 2009-07-31
> **quazi said:**
> I copied this version over to /usr/lib/flashplugin-installer/libflashplayer.so and it broke flash in both chromium and firefox.  What gives?

did you uninstall the previous version?

darco

---

### Post by steveneddy on 2009-07-31
Sweet! Thanks....

---

### Post by quazi on 2009-07-31
> **darco said:**
> did you uninstall the previous version?

darco

No, I simply backed up the old libflashplayer.so

I didn't think it'd be necessary to remove the older version.

---

### Post by darco on 2009-07-31
the adobe website says to uninstall....I did and created my sym link to FF and all is well...Opera picked it right up..Chromium...probably wont work...

darco

edit-nope...chromium a no-go...ever since the Chromium team decided to check the mozilla/plugins folder for flash, it no longer works. Before I was using a x32 flash and it was fine....

---

### Post by xebian on 2009-07-31
> **darco said:**
> the adobe website says to uninstall....I did and created my sym link to FF and all is well...Opera picked it right up..Chromium...probably wont work...

darco

edit-nope...chromium a no-go...ever since the Chromium team decided to check the mozilla/plugins folder for flash, it no longer works. Before I was using a x32 flash and it was fine....

Chromium-browser still uses the 32-bit.  BTW there is an update as well for the 32-bit. Actually flash is now much better as well.

---

### Post by darco on 2009-07-31
> **xebian said:**
> Chromium-browser still uses the 32-bit.  BTW there is an update as well for the 32-bit. Actually flash is now much better as well.

If I knew how to make chromium point to another folder for flash than I would insert the x32 flash a be good to go but....

darco

---

### Post by lithorus on 2009-07-31
> **darco said:**
> the adobe website says to uninstall....I did and created my sym link to FF and all is well...Opera picked it right up..Chromium...probably wont work...

darco

edit-nope...chromium a no-go...ever since the Chromium team decided to check the mozilla/plugins folder for flash, it no longer works. Before I was using a x32 flash and it was fine....
Wow, that was a rather stupid decission I have to say. Atleast they could check for arch first..

---

### Post by ronacc on 2009-07-31
> **lithorus said:**
> Wow, that was a rather stupid decission I have to say. Atleast they could check for arch first..

well what else would you expect fom google ? now if the folks who make bing created a browser they would never make that mistake:lolflag::lolflag::lolflag:

---

### Post by phenest on 2009-07-31
It's still alpha.:(

---

### Post by litspliff on 2009-07-31
sorry guys, but any noob reading this has gone back to using windows by now...not a very good how-to. here's a simple step-by-step to keep M$ from stealing back customers.


[SIZE=5][COLOR=Red]FRESH INSTALL OF FLASH_10_alpha_refresh for firefox ON A FRESH UBUNTU64 (JAUNTY) INSTALL[/COLOR][/SIZE]


[LIST=1]
[*]DOWNLOAD FILE: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
[*]open with archive manager....extract libflashplayer.so file to your desktop.
[*]open a fresh terminal (not sudo-root terminal) in your home directory (you should be there already)
[*]```
mkdir .mozilla/plugins
``` (if you don't already have it....i didn't)
[*]```
cp ./Desktop/libflashplayer.so ./.mozilla/plugins/libflashplayer.so
```
[*]close and restart, or just start your firefox (mine actually crashed when i copied the file, so i just restarted and it works fine)
[/LIST]

i've only been using it for about 20 minutes, so i don't have any bugreports yet.:popcorn:

---

### Post by phenest on 2009-07-31
That's all very well, but if you have the 32-bit version installed, it needs un-installing first. Otherwise the 2 versions will conflict.

---

### Post by litspliff on 2009-07-31
yes....correct....that's why i included the word

FRESH!
i really like that word...

someone should do a STALE install how-to

better yet, a RANCID install

---

### Post by philinux on 2009-07-31
Their version numbering is weird. I checked this couple days ago and it was version 10.0.22.87. Now it's gone to 10.0.32.18.

---

### Post by philinux on 2009-07-31
> **quazi said:**
> Any idea of what this update's supposed to do?  Improved support for flash sure would be nice.
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

---

### Post by zika on 2009-07-31
> **xebian said:**
> Get the new updated 64-bit Flash here[ http://labs.adobe.com/technologies/flashplayer10/]("http://labs.adobe.com/technologies/flashplayer10/")Thank You! Nice touch before my (I hope) month long sea-side vacation without computer ... :)

---

### Post by YukaToshi on 2009-07-31
+1

Thank you.

---

### Post by amano on 2009-07-31
Is there a chance that an official karmic package could pull this in?

Shall we file a bug?

---

### Post by phenest on 2009-07-31
> **philinux said:**
> Their version numbering is weird. I checked this couple days ago and it was version 10.0.22.87. Now it's gone to 10.0.32.18.

Developers don't always release every version, especially when it's only a revision.

---

### Post by tjeremiah on 2009-07-31
did what the site said and FF doesnt see it. Went back to the previous version and all is well again :(

---

### Post by phenest on 2009-07-31
> **tjeremiah said:**
> did what the site said and FF doesnt see it. Went back to the previous version and all is well again :(

Are you using the 32-bit version installed from the repository? If so, un-install it first.

---

### Post by taavikko on 2009-07-31
> **tjeremiah said:**
> did what the site said and FF doesnt see it. Went back to the previous version and all is well again :(

Just on a safe side:
Restarting browser is a "must"...

---

### Post by Slug71 on 2009-07-31
> **tjeremiah said:**
> did what the site said and FF doesnt see it. Went back to the previous version and all is well again :(


Put the file in usr/lib/mozilla/plugins. That worked for me.

---

### Post by Slug71 on 2009-07-31
> **litspliff said:**
> sorry guys, but any noob reading this has gone back to using windows by now...not a very good how-to. here's a simple step-by-step to keep M$ from stealing back customers.


[SIZE=5][COLOR=Red]FRESH INSTALL OF FLASH_10_alpha_refresh for firefox ON A FRESH UBUNTU64 (JAUNTY) INSTALL[/COLOR][/SIZE]


[LIST=1]
[*]DOWNLOAD FILE: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
[*]open with archive manager....extract libflashplayer.so file to your desktop.
[*]open a fresh terminal (not sudo-root terminal) in your home directory (you should be there already)
[*]```
mkdir .mozilla/plugins
``` (if you don't already have it....i didn't)
[*]```
cp ./Desktop/libflashplayer.so ./.mozilla/plugins/libflashplayer.so
```
[*]close and restart, or just start your firefox (mine actually crashed when i copied the file, so i just restarted and it works fine)
[/LIST]

i've only been using it for about 20 minutes, so i don't have any bugreports yet.:popcorn:

I find putting the libflashplayer.so file in usr/lib/mozilla/plugins is less hassle free.

Extract tar.gz file to desktop then just move it.

---

### Post by taavikko on 2009-07-31
> **Slug71 said:**
> I find putting the libflashplayer.so file in usr/lib/mozilla/plugins is less hassle free.

Extract tar.gz file to desktop then just move it.

and is needed if system has more than one (1) user.
That how-to copied to user own home, so any other user has no access to it (without a hassle)

---

### Post by novafluxx on 2009-07-31
About time a refresh was released! Been to many months! I wish there were a changelog somewhere lol

---

### Post by tjeremiah on 2009-07-31
> **Slug71 said:**
> Put the file in usr/lib/mozilla/plugins. That worked for me.

did that. I never installed flash from synaptics or anywhere else before. I just downloaded the 64bit flash and put the file in that (^) folder. FF doesnt detect the new one but the old flash 64. But im not complaining, ill figure it out. And I did get rid of the old before putting in the new.

---

### Post by zoomy942 on 2009-07-31
installed it.  thanks!

---

### Post by litspliff on 2009-07-31
> **Slug71 said:**
> I find putting the libflashplayer.so file in usr/lib/mozilla/plugins is less hassle free.

Extract tar.gz file to desktop then just move it.


exactly what hassle is that? 

[SIZE=2][COLOR=Red]the only difference is that installing into home folder only installs it for that specific user.[/COLOR][/SIZE]
....that's something that i would recommend for a development release.

put it in usr/lib/mozilla/plugins if it's a stable release, but it's just rude to force experimental software on your fellow users. 

when the wife calls you at work about her myspace pages being all f'd up, that's hassle.

---

### Post by taavikko on 2009-07-31
This new update is eating CPU quite happily

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3263 taavikko  20   0  829m 165m  33m S  103  4.2   2:57.63 firefox-3.5
```

---

### Post by litspliff on 2009-07-31
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
1000      3444 18.8 21.2 951120 187620 ?       Rl   12:11   2:44 /usr/lib/firefo
```


mine is doing okay with a few flash applets and 6 tabs open.

---

### Post by phenest on 2009-07-31
> **litspliff said:**
> exactly what hassle is that? 

[SIZE=2][COLOR=Red]the only difference is that installing into home folder only installs it for that specific user.[/COLOR][/SIZE]
....that's something that i would recommend for a development release.

put it in usr/lib/mozilla/plugins if it's a stable release, but it's just rude to force experimental software on your fellow users. 

when the wife calls you at work about her myspace pages being all f'd up, that's hassle.

We're supposed to be testing Karmic. To do so, one must investigate all avenues.

---

### Post by wayne_cat on 2009-07-31
> **litspliff said:**
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
1000      3444 18.8 21.2 951120 187620 ?       Rl   12:11   2:44 /usr/lib/firefo
```
mine is doing okay with a few flash applets and 6 tabs open.

hmm ... firefox 3.0 on Jaunty ... taavikko is using firefox 3.5 on karmic

---

### Post by Arup on 2009-07-31
No CPU issues here, runs better than the previous one specially in full screen mode, I think the load is being distributed better on the GPU.

---

### Post by litspliff on 2009-07-31
yeah....this seems more like a thread for the 64-bit area....i stumbled across it doing a search for "flash 64 bit".

much respect to the karmic people, but this is a big topic as far as 64bit ubuntu in general, so i'm participating anyhow.

at least you get to compare benchmarks now!

---

### Post by taavikko on 2009-07-31
> **Arup said:**
> No CPU issues here, runs better than the previous one specially in full screen mode, I think the load is being distributed better on the GPU.

Just took small glimpse, used youtube, put the vid in fullscreen
switched to tty1 and observed "top"
Xorg and arora both consumed 100<% of CPU

This was tested on 9.10 KDE and arora (core7 920 cpu and Nvidia 9800gtx+)

---

### Post by Arup on 2009-07-31
> **taavikko said:**
> Just took small glimpse, used youtube, put the vid in fullscreen
switched to tty1 and observed "top"
Xorg and arora both consumed 100<% of CPU

This was tested on 9.10 KDE and arora (core7 920 cpu and Nvidia 9800gtx+)

Dual quad core here with cheapo nvidia 8400 and latest 199.18 drivers. I am running Jaunty and have checked out youtube with Opera and FF 3.5

---

### Post by Slug71 on 2009-07-31
> **litspliff said:**
> exactly what hassle is that? 

[SIZE=2][COLOR=Red]the only difference is that installing into home folder only installs it for that specific user.[/COLOR][/SIZE]
....that's something that i would recommend for a development release.

put it in usr/lib/mozilla/plugins if it's a stable release, but it's just rude to force experimental software on your fellow users. 

when the wife calls you at work about her myspace pages being all f'd up, that's hassle.


Doing it in the /home never worked for me. FF just didnt see it. Only have one user too. A few other members around the forums have had the same experience.

---

### Post by wayne_cat on 2009-07-31
> **Slug71 said:**
> Doing it in the /home never worked for me. FF just didnt see it. Only have one user too. A few other members around the forums have had the same experience.


create a link to the plugin 

```
ln -s /path/to/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so 
```

---

### Post by quazi on 2009-08-01
Uninstalling beforehand fixed it for me.  Flash has worked perfectly since (whereas before it would have occasional errors).

---

### Post by ktp on 2009-08-01
> **darco said:**
> If I knew how to make chromium point to another folder for flash than I would insert the x32 flash a be good to go but....

darco

I am using 32-bit plugin for chromium and 64-bit for firefox.

Put 32-bit in /usr/lib/chromium-browser/plugins/ and I have 64-bit in ~/.mozilla/plugins/

---

### Post by darco on 2009-08-01
> **ktp said:**
> I am using 32-bit plugin for chromium and 64-bit for firefox.

Put 32-bit in /usr/lib/chromium-browser/plugins/ and I have 64-bit in ~/.mozilla/plugins/

Thats how I had it setup before..flash worked fine. Which ever snapshot that was recently posted (maybe within last 2 weeks ago) causes huge cpu spikes for me. Reading the output, I see that its trying to read the flash plugin from the .mozilla/plugin folder...it ignores the chromium plugin folder...w/o the --enable -plugin option, its still a screamin' browser..

darco

---

### Post by ktp on 2009-08-01
> **darco said:**
> Thats how I had it setup before..flash worked fine. Which ever snapshot that was recently posted (maybe within last 2 weeks ago) causes huge cpu spikes for me. Reading the output, I see that its trying to read the flash plugin from the .mozilla/plugin folder...it ignores the chromium plugin folder...w/o the --enable -plugin option, its still a screamin' browser..

darco

I know there were/are still flash issues...but today's build is pretty good for me.  It had fix for linux flash plugin issue using 100% CPU...which I was seeing with gmail.

I see chromium reading .mozilla plugin folder, well all the folders where firfox/mozilla puts plugins, but for me they are all 64-bit so I get wrong class error.  But no high CPU with todays build.

Chromium seems to be shaping into day2day usable browser...at least for me.  I wish java plugin would work...but can leave without it because of chromium speed.

---

### Post by Slug71 on 2009-08-01
> **wayne_cat said:**
> create a link to the plugin 

```
ln -s /path/to/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so 
```

Thanks, will use that next time.

---

### Post by Ux64 on 2009-08-02
With megaupload and filefront whole browser crashes due Adobe Flash pluging hanging when trying to upload larger files.

Related sites:
[http://www.megaupload.com/](http://www.megaupload.com/)
[http://www.filefront.com/](http://www.filefront.com/)

Screenshot when FF 3.5 with Flash 64 bit is stuck.
SS: [http://server2.jaatiedostosi.com/HCABw5/crash2.png](http://server2.jaatiedostosi.com/HCABw5/crash2.png)

Problem only exist with larger files. So when you're reproducing it, don't use small files. With pre-existing or small files everything work perfecty.
SS: [http://server2.jaatiedostosi.com/rXxBPU/crash3.png](http://server2.jaatiedostosi.com/rXxBPU/crash3.png)

Joke... Maybe files larger than 50 megabytes are too large for 64 bit system to handle... ;)

Issue reported directly to Adobe.

---

### Post by taavikko on 2009-08-02
> **Ux64 said:**
> I would like to report issue!

With megaupload and filefront whole browser crashes due Adobe Flash pluging hanging when trying to upload larger files.

I didn't find from Adobes page direct feedback link, so I'm reporting issue here.


For reporting bugs concerning flash
[http://bugs.adobe.com/flashplayer/](http://bugs.adobe.com/flashplayer/)

Maybe i should link this too in the Finnish forums ;)

---

### Post by darco on 2009-08-02
> **ktp said:**
> I know there were/are still flash issues...but today's build is pretty good for me.  It had fix for linux flash plugin issue using 100% CPU...which I was seeing with gmail.

I see chromium reading .mozilla plugin folder, well all the folders where firfox/mozilla puts plugins, but for me they are all 64-bit so I get wrong class error.  But no high CPU with todays build.

Chromium seems to be shaping into day2day usable browser...at least for me.  I wish java plugin would work...but can leave without it because of chromium speed.

Wow...recvd an update for Chromium on a Sunday morning!..anyways
build 22243 seems to have solved my problem. No more high cpu usage when using the x32 flash player..great!
Im running Mint X64 btw...

---

### Post by caeroe on 2009-08-03
> **xebian said:**
> Get the new updated 64-bit Flash here

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

I did, and it's horrible.  Fullscreen Flash performance is completely subpar.  Trying to watch anything in fullscreen from Hulu or Youtube is impossible, the FPS goes down to 1-3.

---

### Post by Twitch6000 on 2009-08-04
Can anyone give me detail on how good this alpha is?

I have been thinking about switching back to 64bit,but flash has always let me down :[.

---

