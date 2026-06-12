---
title: "Confusion over 64bit Flash"
date: 2009-02-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-14
Im confused on Jaunty's current flash plugin for 64bit systems

I thought we moved to the native 64bit flash

But I see that we have 32bit libs being added during the install

Can someone clarify please

---

### Post by plun on 2009-02-14
Its still an "alpha" so Debian wont touch it....

Works just great despite of Debian !

Download:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by kurros on 2009-02-14
Yes the current package still uses nspluginwrapper on the 32bit version (which isn't such a horrible thing since it helps isolate flash).

---

### Post by ronacc on 2009-02-14
maybe, but the 64bit version of flash works better ,atleast for me .

---

### Post by Slug71 on 2009-02-14
Yep the Alpha 64bit is way better than the one currently with Ubuntu.
Works just fine.

---

### Post by Gourgi on 2009-02-15
i think i saw a bug report for this 
but the devs strongly insisted that flash 64 bit is used in jaunty.
i'll have to search launchpad for this to find again.

---

### Post by David A Knight on 2009-02-15
> **Slug71 said:**
> Yep the Alpha 64bit is way better than the one currently with Ubuntu.
Works just fine.

If by just fine you mean pulls down the whole browser if you close a tab that happened to have some flash in it and still sucks up 100% cpu on many occasions then yes.

---

### Post by walmis on 2009-02-15
Youtube HD fullscreen playback is waaay faster for me with 32bit flash + nspluginwrapper than the 64bit version.

---

### Post by plun on 2009-02-25
a new release is available, still alpha

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


libflashplayer-**10.0.22.87**.linux-x86_64

------------------------------
32bit is also updated
[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

---

### Post by Nullack on 2009-02-25
thanks mate

---

### Post by plun on 2009-02-25
> **Nullack said:**
> thanks mate

Well... we must try to get this thing within Jaunty.

Just a joke with a big Ia32 package.......

---

### Post by taavikko on 2009-02-25
> **Nullack said:**
> Im confused on Jaunty's current flash plugin for 64bit systems

I thought we moved to the native 64bit flash

But I see that we have 32bit libs being added during the install

Can someone clarify please

+1 ,should use native 64bit flash 
Since flashplugin-nonfree(64) is only pkg pulling nspluginwrapper and 32-libs.

Even java has gone full-64 plugin (sun-java6u12)

Maybe FFe/wishlist?

---

### Post by portis on 2009-02-25
Debian has already turned to this native 64bit plugin.

flashplugin-nonfree (1:2.5) unstable; urgency=low

---

### Post by Nullack on 2009-02-25
Only 32 bit supports opengl acceleration, with compiz off.

---

### Post by jp_coll2003 on 2009-02-25
I did not realise that this  was the case but I installed the 64 bit version manually anyway when I first installed Jaunty as well as the 64 bit Java install... Personally, I think these run soo much smoother than the 32 bit versions.

---

### Post by taavikko on 2009-02-25
> **jp_coll2003 said:**
> I did not realise that this  was the case but I installed the 64 bit version manually anyway when I first installed Jaunty as well as the 64 bit Java install... Personally, I think these run soo much smoother than the 32 bit versions.

64-bit java is already in, no need to manually install that one.

Now just waiting for 64bit flash that we can get rid of excess 32bit libraries and cruft :D

---

### Post by plun on 2009-02-25
> **taavikko said:**
> 
Now just waiting for 64bit flash that we can get rid of excess 32bit libraries and cruft :D

Well... lets sing the "crap-song" and maybe something happens...):P

Latest 64bit version is "snappier"/faster  ;)


(also a ugly security hole for the moment which this version fixes)

---

### Post by taavikko on 2009-02-25
> **plun said:**
> Well... lets sing the "crap-song" and maybe something happens...):P


I have an better idea, lets just start the new computer-janitor program, maybe it removes unwanted crap...

I posted a question in LP, but there hasn't been any answers yet...

---

### Post by | MM | on 2009-02-25
> **David A Knight said:**
> If by just fine you mean pulls down the whole browser if you close a tab that happened to have some flash in it and still sucks up 100% cpu on many occasions then yes.

For me Flash 64 is leaps and bounds ahead of the previous Flash releases.  Are you using Firefox?  Because, yea, Flash takes down Firefox quite often... Opera doesn't seem to crash when Flash has an issue.  Also i think Flash stability is quite GPU specific.  I recently got a new mobo, CPU and GPU  (NV6600 -> NV9800) and since the upgrade have notice _much_ improved stability on the part of Flash.

---

### Post by nanog on 2009-02-25
for me nspluginwrapper is/was a disaster. before native 64 bit flash became  available i could not run flash on my workstations.

---

### Post by Nullack on 2009-02-25
> **| MM | said:**
> For me Flash 64 is leaps and bounds ahead of the previous Flash releases.

Not for me, until we have 64bit opengl acceleration like the 32bit version

---

### Post by plun on 2009-02-25
> **Nullack said:**
> Not for me, until we have 64bit opengl acceleration like the 32bit version

Can you please give us reference URL for your challenge ?

This is my reference:
[http://playrapport.se](http://playrapport.se)

Swedish national news..... without ads... ;)

---

### Post by dBuster on 2009-02-25
I have had no issues with installing the 64bit flash and did it from the script contained in the this posting:  [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

I ran that script first before installing any other flavor of flash to include the 32bit version.  However I believe this script will remove any other version. 

For the latest release I edited the script file and replaced the two instances of the download file with the current download file.  Then I executed and my flash was and is now updated to the Feb 24th release.  

Sure it is still an alpha release but it runs smoothly for me without any issues and I even have sound!

---

### Post by Nullack on 2009-02-25
> **plun said:**
> Can you please give us reference URL for your challenge ?

Mate I dont have any particular website, its simply that for my test system which is not very powerful I wouldnt be prepared to run flash without OpenGL acceleration. Theres just too much of a load with software decoding.

And oh, it doesnt work with compiz on which is just another reason that until proper GPU memory management gets fully implemented into the graphics stack compiz will continue to be broken.

---

### Post by ronacc on 2009-02-25
> **plun said:**
> Can you please give us reference URL for your challenge ?

This is my reference:
[http://playrapport.se](http://playrapport.se)

Swedish national news..... without ads... ;)

translate isn't working , I couldn't understand a word he said .:lolflag:

---

### Post by Gina on 2009-02-26
> **plun said:**
> Can you please give us reference URL for your challenge ?

This is my reference:
[http://playrapport.se](http://playrapport.se)

Swedish national news..... without ads... ;)That's working for me (AMD64 X2) except that I have no sound - but that's another issue (reported elsewhere).

EDIT - Sound OK now after update - so yes that's working fine.

---

