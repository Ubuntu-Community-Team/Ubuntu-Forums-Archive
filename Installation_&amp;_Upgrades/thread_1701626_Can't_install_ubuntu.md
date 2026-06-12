---
title: "Can't install ubuntu"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by DrBob89 on 2011-03-06
I formatted my hard drive and created two partitions of 125gb each. I Installed Windows 7 in one and want to install Ubuntu in the other. I loaded Ubuntu on a thumb drive. When I boot from the thumb drive, I get a screen for language selection followed by a menu screen giving me options of a trial run of Ubuntu or installing it. Selecting either one gives me a black screen with a flashing cursor in the upper left hand corner.
 
Burned a CD, same problem. However, I burned the CD from the same ISO that I made the thumb drive from.
 
Bad ISO?
Monitor problem? ( I say that because I had a similar problem with the Windows install and had to use a different monitor, but changing the monitor this time didn't work.)
 
Other suggestions?
 
Bob

---

### Post by sanderd17 on 2011-03-06
[http://www.google.be/imgres?imgurl=http://karuppuswamy.com/wordpress/wp-content/uploads/2010/09/Screenshot1-450x281.png&imgrefurl=http://karuppuswamy.com/wordpress/tag/ubuntu/&usg=__3ofCLU2ghxsTGJXYhVw6o4s16f0=&h=281&w=450&sz=109&hl=nl&start=0&sig2=EIbs-EBK-O9rSzvkxbkbmA&zoom=1&tbnid=QG88lEFLnM6gfM:&tbnh=123&tbnw=197&ei=nh50TYPrBpGDswaHvJSIDg&prev=/images%3Fq%3Dubuntu%2B10.10%2Binstall%2Bscreenshots%26um%3D1%26hl%3Dnl%26client%3Dfirefox-a%26hs%3DiHj%26sa%3DN%26rls%3Dorg.mozilla:nl:official%26biw%3D1600%26bih%3D764%26tbs%3Disch:1&um=1&itbs=1&iact=hc&vpx=125&vpy=255&dur=130&hovh=177&hovw=284&tx=180&ty=71&oei=nh50TYPrBpGDswaHvJSIDg&page=1&ndsp=28&ved=1t:429,r:7,s:0](http://www.google.be/imgres?imgurl=http://karuppuswamy.com/wordpress/wp-content/uploads/2010/09/Screenshot1-450x281.png&imgrefurl=http://karuppuswamy.com/wordpress/tag/ubuntu/&usg=__3ofCLU2ghxsTGJXYhVw6o4s16f0=&h=281&w=450&sz=109&hl=nl&start=0&sig2=EIbs-EBK-O9rSzvkxbkbmA&zoom=1&tbnid=QG88lEFLnM6gfM:&tbnh=123&tbnw=197&ei=nh50TYPrBpGDswaHvJSIDg&prev=/images%3Fq%3Dubuntu%2B10.10%2Binstall%2Bscreenshots%26um%3D1%26hl%3Dnl%26client%3Dfirefox-a%26hs%3DiHj%26sa%3DN%26rls%3Dorg.mozilla:nl:official%26biw%3D1600%26bih%3D764%26tbs%3Disch:1&um=1&itbs=1&iact=hc&vpx=125&vpy=255&dur=130&hovh=177&hovw=284&tx=180&ty=71&oei=nh50TYPrBpGDswaHvJSIDg&page=1&ndsp=28&ved=1t:429,r:7,s:0)

This is the first screen that you should get.

If you don't get that one, are you sure you downloaded the right iso? Not an old one or an alternate installer.

You need the desktop edition.

---

### Post by JBAlaska on 2011-03-06
> **DrBob89 said:**
> I formatted my hard drive and created two partitions of 125gb each. I Installed Windows 7 in one and want to install Ubuntu in the other. I loaded Ubuntu on a thumb drive. When I boot from the thumb drive, **I get a screen for language selection followed by a menu screen giving me options of a trial run of Ubuntu or installing it.** Selecting either one gives me a black screen with a flashing cursor in the upper left hand corner.
 
Burned a CD, same problem. However, I burned the CD from the same ISO that I made the thumb drive from.
 
Bad ISO?
Monitor problem? ( I say that because I had a similar problem with the Windows install and had to use a different monitor, but changing the monitor this time didn't work.)
 
Other suggestions?
 
Bob

When you get to that point, hit F6 and then Esc to see the boot line

Add the following parameter to the end of the line: **nomodeset**
Than hit enter and try your install again.

---

### Post by DrBob89 on 2011-03-07
Thanks, that worked.

Bob

---

