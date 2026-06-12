---
title: "Flash 10 with Intrepid. Does 64 bit work?"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roasted on 2008-10-23
I'm just curious, does Intrepid 64 bit (in its current state now) work with Flash 10? Or only 32 bit? 

I've searched but surprisingly didn't find any direct answers... Just people asking the same question.

---

### Post by bash on 2008-10-23
Yep. Works like a charm. With that I mean the installation. The plugin itself is still the same old buggy thing that loves to happily crash. But that is not something Ubuntu can change. Adobe has to finally release a proper flashplayer for Linux.

To get it up and running though, the only thing needed is:

```
sudo apt-get install flashplugin-nonfree
```

That will take of everything and after restarting Firefox you should have a working Flashplayer.

---

### Post by Roasted on 2008-10-23
Really? I heard great things about Flash 10. I just always forgot to ask if the users were in 32 bit land or 64. I heard it's real smooth and you can full screen it now. Is that the case with flashplugin-nonfree?? I figured that'd still be 9...

---

### Post by Roasted on 2008-10-23
Didn't work. Says I have no flash player installed or an old version, according to YouTube.

---

### Post by | MM | on 2008-10-23
> **Roasted said:**
> I'm just curious, does Intrepid 64 bit (in its current state now) work with Flash 10? Or only 32 bit? 

I've searched but surprisingly didn't find any direct answers... Just people asking the same question.

Works great for me.  Ubuntu x86_64 with nvidia 177 drivers.

---

### Post by Roasted on 2008-10-23
> **| MM | said:**
> Works great for me.  Ubuntu x86_64 with nvidia 177 drivers.

I'm stupid. I didn't have my nvidia drivers installed. Now I have 177 drivers and Flash 10 on Intrepid 64 bit.

---

### Post by jprophet420 on 2008-10-23
Mine works great, I just used a script I found on this forum.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by Roasted on 2008-10-23
Yeah, but that's flash 9. I want 10... but I got it. :)

---

### Post by jprophet420 on 2008-10-23
I am sorry. Forgot to mention it updates to 10, but you got it working anyway.

---

### Post by petersaints on 2008-10-24
It works relatively well on 64-bit... but I still have some websites that crash in 64-bit (using nspluginwrapper 1.1.2 and Flash 10 Final) but on 32-bit (with Flash 10 Final) are working perfectly. I still prefer 32-bit because of this issue... Adobe has to release native 64-bit version of Flash soon!!

---

### Post by Roasted on 2008-10-24
I'd be on 32 bit normally, but seeing as though everything I use works fine in 64 bit plus I have 4gb of RAM (otherwise in 32 bit land I'd miss out on a gig) I just try to stick with 64 bit.

---

### Post by zorkerz on 2008-10-29
Im on a 64 bit intrepid install and flash has been working just fine for me until a day or tow ago. Now when I try to start any movie I get less than a second of sound before the video freezes and sound stops. Sometimes I get a grey screen or white screen where the flash video should be. 

Any ideas what I can do to look into this?

---

### Post by Roasted on 2008-10-29
Every once in a while I get a gray screen. Refreshing the web page does the trick.

---

