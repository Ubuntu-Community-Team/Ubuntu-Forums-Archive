---
title: "Karmic video resolutions &amp; refresh rates"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BavarianPH on 2009-10-10
[SIZE=3]In Jaunty my display settings accurately gave me resolutions **above 1024x768 -** higher refresh rates up to **85 Hz**
(**1024x768@85** - lesser refresh rates for higher resolutions)[/SIZE]

[SIZE=3]Having searched the forums & tried to create & modify the xorg.conf file (in **Karmic beta**), 
I could not create any higher [/SIZE][SIZE=3]resolutions or refresh rates. 
***current settings: ***
[B]
1024x768@75[/B] (hard on my eyes)
Asus P5E-VM HDMI PC
Intel duo processor: 2.20 GHz
**Intel 82G35** Express Integrated Graphics Card rev 3, 328MB 
[I][B]
xorg.log:[/B][/I]     
[COLOR=Red]Error  Failed to load module "i810" (module does not exist, 0)[/COLOR]
     [/SIZE][SIZE=3][COLOR=Orange]
     Warning    Falling back to old probe method for vesa
     Warning    Falling back to old probe method for fbdev[/COLOR][/SIZE]
   [SIZE=3]  
    Information    intel(0): 720x400@70Hz
    Information    intel(0): 640x480@60Hz
    Information    intel(0): 640x480@75Hz
    Information    intel(0): 800x600@75Hz
    Information    intel(0): 1024x768@75Hz[/SIZE]
[SIZE=3][U][B]
Karmic *beta* update[/B][/U] apparently substituted 
[B][I]
xserver-xorg-video-i810[/I][/B] intel driver ***with***
[B]
xserver-xorg-video-intel[/B] 2.9.0 1ubuntu1[/SIZE]  

[SIZE=3]***Karmic beta OS*** apparently still uses older info instead of using the newer driver!?! - my guess -

Please advise in detail, understandable to 
a former Windows user still ***fairly new*** to **Ubuntu** & Linux

I tried to upload the **X.org Log** file 
copied from ***KS****ystemLog*** viewer.

Thank you for any help you could provide!

[B][COLOR=Blue]BavarianPH

[/COLOR][/B][/SIZE][COLOR=Blue][SIZE=3][COLOR=Black]**PS:** this is my first thread post ever, I hope I did it right, if not, please advice!
[/COLOR][/SIZE][/COLOR][B][COLOR=Blue][SIZE=3][COLOR=Black]
Thank you again[/COLOR][/SIZE][/COLOR][/B]**[COLOR=Blue][SIZE=3][COLOR=Black]![/COLOR][/SIZE][/COLOR]**
[B][COLOR=Blue]


[/COLOR][/B]

---

### Post by louieb on 2009-10-10
You did just fine with the information in your post. Shows you did research into the problem. 

Karmic is beta - still a work in progress. Please check  [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") to see if the problem has been reported. If it has then you can find if it is being worked on. 

Sorry not to be of much help - the fixes I would have suggested a year or two ago no longer apply with new xorg.

---

### Post by bapoumba on 2009-10-10
Moved to Karmic.

---

