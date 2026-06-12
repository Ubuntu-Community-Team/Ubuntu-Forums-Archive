---
title: "Xbmc"
date: 2009-10-31
forum: Kentucky Team - US
---

### Post by tom_d on 2009-10-31
Hi Does anone use XbMC?  If so how do I install plugins so I can watch videos, listen to music.  thankss in advance.  tom_d

---

### Post by doppis on 2009-11-03
this video show's an easy way to get plugins at the end.....[http://www.youtube.com/watch?v=v74uBBJUuKQ](http://www.youtube.com/watch?v=v74uBBJUuKQ)

---

### Post by tom_d on 2009-11-04
HI I watched your video this morning.  YOu make it look easy.  
  Thank you      tom_d

---

### Post by tom_d on 2009-11-12
Hi i am having trouble installing plugins.  I can't find where to install theml them,  I DOWNLOADED AN INSTALLER, BUT i CAN'T FIGURE HOW IT WORKS.  i CAN'T FIND THE FOLDER THAT i CAN DRAG AND DROP EITHER.  
  i OPENED /USR/SHARE/XBMC.  
  My question is how and where do I put the plugins in.  thnaks   tom_d

---

### Post by tom_d on 2009-11-12
HI I am haveing trouble adding or installing plugins to xbmc.  I have downloaded an installer, but I can't figure how to use it. 
 I can't find where to drag and drop the plugins.  I have looked in /usr/shre/xbmc.  I have opened each of the folders and can find no place to drag and drop the plugins.  
   How do I get plugins installed.  thanks tom-d

---

### Post by sdowney717 on 2009-11-18
you can actually just copy them into the plugins/video folder.
the xbmc folder is hidden, so select to show hidden files and folders in nautilus
not all of these work, about 20% of them are having some sort of problem

if you can get xbmc into library mode then you can use the builtin scraper to get list out movie info

---

### Post by tom_d on 2009-11-25
Thanks I finally have it working.  You guys and gals are great.  thaks  tom_d

---

### Post by mtn on 2009-11-30
Hi, I'm having problems installing plugins for XBMC on my laptop which is running Ubuntu Karmic 9.10.

I have installed XBMC through the Ubuntu Software Centre - it works great. However, I have written 2 plugins for XBMC that work on my Xbox/XBMC but I can't get them to show up on my Ubuntu/XBMC.

I have tried copying the plugin's folders to home/.xbmc/plugins/video, as well as, /usr/share/xbmc/plugins/video - no joy though. 

All I had to do to install plugins on Xbox/XBMC was copy the plugin's folders to e:/apps/xbmc/plugins/video and they showed up in video>plugins along with iPlayer, You Tube etc

One of the plugins I'm struggling with can be downloaded from here: [http://www.box.net/xbmx-plug-ins]("http://www.box.net/xbmx-plug-ins")

Any help would be much appreciated, thanks.

---

### Post by mtn on 2009-11-30
Ok, I have got the plugins to show up in XBMC. However the plugins don't run when selected in XBMC?!

I had to add the plugins folder as a source in: ```
/home/username/.xbmc/userdata/sources.xml
```

i.e. in the video section of the xml I had to add these lines
```

<source>
     <name>Video Plugins</name>
     <path pathversion="1">/home/username/.xbmc/plugins/video/</path>
</source>
```

so the file originally looked like this

```
<sources>
    <programs>
        <default pathversion="1"></default>
    </programs>
    <video>
        <default pathversion="1"></default>
    </video>
    <music>
        <default pathversion="1"></default>
    </music>
    <pictures>
        <default pathversion="1"></default>
    </pictures>
    <files>
        <default pathversion="1"></default>
    </files>
</sources>
```

and now looks like this

```
<sources>
    <programs>
        <default pathversion="1"></default>
    </programs>
    <video>
        <default pathversion="1"></default>
	<source>
            <name>Video Plugins</name>
            <path pathversion="1">/home/username/.xbmc/plugins/video/</path>
        </source>
    </video>
    <music>
        <default pathversion="1"></default>
    </music>
    <pictures>
        <default pathversion="1"></default>
    </pictures>
    <files>
        <default pathversion="1"></default>
    </files>
</sources>

```

---

