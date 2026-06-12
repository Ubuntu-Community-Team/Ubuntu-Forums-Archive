---
title: "Upgrade to Jaunty, hold back Xorg? Fglrx?"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by timmy334 on 2009-03-25
I was thinking this afternoon(dangerous, I know). Could one install Intrepid, set Synaptic to hold back Xorg to the version in Intrepid, change repos to Jaunty and upgrade to Jaunty from there? Would that work so those of us with ATI cards that they will not support in their drivers for Xorg 1.6 can have our full eyecandy goodness? I am in Jaunty right now and it uses the 'radeon' module. Yeah, it works. But, it is a little less responsive than fglrx. Or, must Jaunty use the new Xorg?

---

### Post by ktp on 2009-03-25
I would like to know also...since i have seen some rendering issues with the open source ati drivers.  Hopefully it gets better soon.  

Using following X.Org seems to help lot but still have minior rendering issues:
[PHP]Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#       SubSection "Display"
#               Virtual 2960 1050
#       EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelDFS" "on"
        Option          "AccelMethod"  "EXA"
        Option          "MigrationHeuristic"  "smart"
        Option          "EnablePageFlip"  "on"
        Option          "EnableDepthMoves"  "on"
        Option          "ColorTiling"  "on"
#       Option          "DisplayPriority"  "HIGH"
#       Option          "DepthBits"  "24"
#       Option          "SubPixelOrder"  "RBG"
#       Option          "DRI" "on"
        Option          "FBTexPercent"  "0"
        Option          "RenderAccel"  "on"
EndSection

Section "ServerFlags"
        Option          "DontZap"       "off"
EndSection
[/PHP]

---

### Post by screaminj3sus on 2009-03-26
There is a beta fglrx in the jaunty repos that works with the new xorg I am using it now with an hd2600. works well unless you use compiz which runs like absolute crap.

Works fine with no compiz though, video ect.. seems good.
[http://i44.tinypic.com/2ijmcyp.png](http://i44.tinypic.com/2ijmcyp.png)

---

### Post by screaminj3sus on 2009-03-26
I'm trying the opensource driver now and I am actually finding it much better than fglrx for video playback, no tearing! I get no display gltcihes with it but resizing a video hard locks my computer which is a bit of a speedbump... scrolling and such is much smoother than flgrx too.

---

### Post by Dawei87 on 2009-03-26
i have been using the beta fglrx in jaunty and so far it works better than intrepid with latest catalyst control drivers. works fine with compiz, still a little tear but not as bad. only thing, in jaunty and intrepid i have been unable to use any media centers. just a blank full screen that locks my computer. but other than that the beta fglrx works like a charm

---

### Post by screaminj3sus on 2009-03-26
what card do you have? for me compiz or any composited desktop runs multitudes slower than in 8.10.

---

### Post by timmy334 on 2009-03-26
I am using my laptop. My video chip is a Mobility Radeon X600. I am pretty sure that the new fglrx will not support mine. I don’t know what r*** it is, but it is 3.5 years old. The ‘radeon’ module works very well. It is noticeably slower when switching themes in Emerald and will NOT, under any circumstances, work with the compiz ‘blur’ plugin. It is a tiny bit less-snappy in speed than fglrx in Intrepid, but I still have my eye-candy, minus the cool blur :) That is why I want to try installing Intrepid and locking xorg at that version and then upgrading to Jaunty. If that works, that will save many Ubuntu-ers a lot of hassle, at least with that part :)
I am thinking though that this solution is too simple and logical to work properly :) But, I will give it a go tonight. If it doesn’t work, I will just do a clean install of Jaunty again and start forcing myself to get used to the open source driver w/o my precious blur. I do agree that video playback is better using the ‘radeon’ module. I wish ATI would just open-source their driver! It’s not like we’re using it to run other video cards. They are still getting our money for the cards! Why keep the driver closed if open-sourcing it helps us enjoy their cards more?

---

### Post by sdowney717 on 2009-03-26
how about trying google earth?

---

### Post by markharding557 on 2009-03-26
> **timmy334 said:**
> I am using my laptop. My video chip is a Mobility Radeon X600. I am pretty sure that the new fglrx will not support mine. I don’t know what r*** it is, but it is 3.5 years old. The ‘radeon’ module works very well. It is noticeably slower when switching themes in Emerald and will NOT, under any circumstances, work with the compiz ‘blur’ plugin. It is a tiny bit less-snappy in speed than fglrx in Intrepid, but I still have my eye-candy, minus the cool blur :) That is why I want to try installing Intrepid and locking xorg at that version and then upgrading to Jaunty. If that works, that will save many Ubuntu-ers a lot of hassle, at least with that part :)
I am thinking though that this solution is too simple and logical to work properly :) But, I will give it a go tonight. If it doesn’t work, I will just do a clean install of Jaunty again and start forcing myself to get used to the open source driver w/o my precious blur. I do agree that video playback is better using the ‘radeon’ module. I wish ATI would just open-source their driver! It’s not like we’re using it to run other video cards. They are still getting our money for the cards! Why keep the driver closed if open-sourcing it helps us enjoy their cards more?

i'm in the same boat only difference is i use my ati for games like nexuiz and open arena so using a poorer alternative simply is not an option

---

### Post by markharding557 on 2009-03-26
i have attempted to downgrade xorg on jaunty in virtual box but this caused all sorts of issues so i don't think it is going to work that way,so good luck in your experiment.

---

### Post by ktp on 2009-03-26
According to this R600 should be supported.  Fglrx only dropped R300-500

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by krazyd on 2009-03-27
Yes, but the X600 has a R300 chip.

AMD is still supporting these chips, just in the open-source drivers, not fglrx.

@timmy: have you enabled EXA?

---

### Post by TaTaE on 2009-03-28
Seems like Catalyst 9.3 is out and is the LAST VERSION TO SUPPORT R300 - R500 CHIPSETS !!!

---

### Post by zika on 2009-03-28
> **TaTaE said:**
> Seems like Catalyst 9.3 is out and is the LAST VERSION TO SUPPORT R300 - R500 CHIPSETS !!!
how does it work in JJ? is it worth of trouble?

according to this it seems it is not for JJ:[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=2)

I've read and re-read documentation and I can not see why it would not work with JJ... ?

---

### Post by timmy334 on 2009-03-28
> **zika said:**
> how does it work in JJ? is it worth of trouble?

according to this it seems it is not for JJ:[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=2)

I've read and re-read documentation and I can not see why it would not work with JJ... ?

Well, I'll try my little experiment. But, if it fails, I will not worry about it. My video chip is dying a slow death so I will need another laptop soon anyway. So, can any of you recommend a good laptop that plays nice with Ubuntu? Also, with the newer Xorg, should I get an Nvidia chip or stick with ATI?

---

### Post by ktp on 2009-03-28
See this thread

[http://ubuntuforums.org/showthread.php?t=1105143](http://ubuntuforums.org/showthread.php?t=1105143)

---

