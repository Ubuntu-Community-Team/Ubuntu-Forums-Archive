---
title: "Failed graphics on live cd"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by joebow1991 on 2012-04-10
Okay, so I have a toshiba x505-q880 running windows 7 with the 64gb ssd and the 500gb hdd. If I try to go into the live cd, it shows the purple welcome screed with the 4 red dots and then I get a black screen with green dots and a half inch white lines forming a maze accross the screen. Ive tried using ubuntu 11.10 and the new beta both 64 bit and both react the same. I know I ran a previous version of ubuntu previously on the live cd and it was fine so I'm at a loss. All I can say more is that it almost looks like the refresh rate is out of the screens range but obviously I cant be sure. So thanks for any help in advancee.

---

### Post by mastablasta on 2012-04-11
what graphics card(s) do you have on that maschine?
 
did you try selecting nomodeset on boot or one of other boot options? 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by joebow1991 on 2012-05-01
Okay, I have an Nvidia GeForce gts 360m and I got it to work with  nomodeset but the problem now is when i start the computer all i get is a blinking white line on the top left of the screen... thanks for the post! any suggestions for this one?

---

### Post by MonkeyPaw on 2012-05-01
Can you hook up to an external monitor to see if those results are any different? You might be able to get an install done that way, and then run nVidia's drivers and see if that brings life to your panel.

Also, make sure your 12.04 ISO is complete. Perhaps a bad download?

---

### Post by joebow1991 on 2012-05-04
Hey, lmao you were right... It was a bad download and I ended up having to use nomodeset as well but all is good now :) thanks guys! much apreciated!

---

