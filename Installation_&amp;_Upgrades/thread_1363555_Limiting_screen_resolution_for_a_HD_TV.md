---
title: "Limiting screen resolution for a HD TV"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by neelapala on 2009-12-24
Hello, 
I have searched and even tried out some of the solutions posted on this topic, managed to screw up the OS and now have done a total Ubuntu 9.1 reinstall. 

I installed 9.1 on an old PC I had(complete install)and hooked it up to my Toshiba 1080p HD TV. However, I only get a 800x600 screen resolution. Previously, I had Win XP and got a 1280X1024 resolution on the TV. I am not sure what type of Graphics card I have,it is an old PII system. My TV is a Toshiba Regza 1080p.

I tried some of the things posted as solutions for this problem, including editing xorg.conf file and managed to somehow screw it up. So far most of the search results seemed to be oriented towards resolving the graphics card driver issue. One suggestion that I found seemed to make some sense on trying to write in the horizontal frequencies and vertical frequencis.
Anyone have any idea how I go about getting a bigger screen resolution. If you are kind enough to do so, please do so with a total neewbie in mind.

I am also thinking of hooking up the CPU to my computer monitor and doing the find hardware drivers for monitor thing to see if Ubuntu would automatically find a higher screen resolution and then see if I can hook it up to the TV.

I basically want to use my TV as a monitor, find a wireless keyboard/trackball combo to browse the net from the couch. Connect an external harddrive and play movies from there.
So far, I am just getting frustrated even though I feel Ubunu is refreshingly different than Win.

Thank you.

Update: Now resolved.

---

### Post by laceration on 2009-12-24
You have 2 possible issues that I can think of.  The first one is your video driver.  Ubuntu sometimes does not install the best video drivers by default because they use proprietary source code.  This is easily remedied though.  Open MainMenu -> System -> Administration -> Hardware Drivers.(This might be in a slightly different location, I am using an older ver of Ubuntu)  Hopefully there will be a proprietary driver for you to install there.  If not you will have to find out what kind of video hardware you have.  Do this by opening a terminal(Menu -> Accesories -> Terminal ) + typing at the prompt:
```
lspci | grep VGA 
``` 
(be sure to capitalize the VGA)
Then I would suggest searching these forums.  Undoubtedly there will be something here.
The second issue you may have is that an old computer just will not have the horsepower to drive a hidef monitor very well.  Linux Video drivers may not always match what the window drivers can do, even though they are making great progress.

---

