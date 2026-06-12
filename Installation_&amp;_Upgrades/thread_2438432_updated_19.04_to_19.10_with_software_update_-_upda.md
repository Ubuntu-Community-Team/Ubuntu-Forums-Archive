---
title: "updated 19.04 to 19.10 with software update - update distribution option. problems,.."
date: 2020-03-12
forum: Installation &amp; Upgrades
---

### Post by m8w on 2020-03-12
what is the matter?

immediately checking if my topic already posted I click the option in this browser then this window opens new window that I can not close :(   anyway

there is no desktop in the first 7-10 boots just right click for the programs on the desktop no desktop bar on the edge of the desktop or much of anything going on.  OK 

after maybe boots reboots booted again.  seems.. 

There is now a desktop bar on the edge of the desktop top but no courser or mouse pointer moving to my mouse movements - it is invisible till .. I somehow light up the top corner where the select program options drop down because I thought to click for it to drop it down -- and then I have the pointer it is back

the reason for not updating with the DVD is my double density DVD Burner from 2006(passed between a few computer upgrades) finally dies and I hope it is not needed anymore. :) 

this update is baffling so the ctrl alt del selection brings me to a desktop asking for my password. and there is also my old desktop image there ,,, right now the screen is black and the settings are not letting me put that image or any image on the desktop or even add panels or anything else.

It seems with certain control panels that have no close box and cover the top right corner to go to another control panel leaves me to ctrl alt del a restart again.. :(   IDK 

this typing is kinda difficult as right now this window can't be configured and is half down the screen here were I might not be able to post mmmmm ok there is the scroll bar so maybe I can post it .

the only real solution I might be able to do in this type of environment would be a reboot some more.  hey I do have spell check so all is not lost maybe.

---

### Post by m8w on 2020-03-12
OK it is slowly being configured ,, i guess that was the problem the whole time I had the display window set in the wrong place.. that resetting it put me back to the desktop with the image and the right click menu of programs.---

I have to assume it all went well in the update but did not go well with the configurations of the environment :(    IDK more settings to set I guess.. I am spending weeks with this configuration problem. going on.. oh and getting used to the new distribution

---

### Post by u666sa on 2020-03-13
Apt install mesa-utils
Then
Glxinfo | grep OpenGL

Bet you using llvmpipe.

I had similar problems in FreeBSD, no live with llvmpipe.

If you want linux you have to realize something, new stuff creates troubles. That 19 os is for testing stuff out, so that wr later run it trouble free. You are a beta tester. Go with LTS if you want stability.

---

### Post by m8w on 2020-03-16
I want to use ubuntu for music stuff.. I was doing midi stuff with things and such before.. I thought (the problem right there) that I was going to the new release all tested... so now, because it seems I have to configure the whole thing for each boot.. every single time.. yeah it must be beta.. I have.. the disk for 18 and 19.04 but my disk play/burner is still dead and I really don't want to replace that. 000 I guess.. I will try something to some how.. ,,, but what now.. I don't want to do a configure each boot .. and.. I bet the music programs have just as many bugs .. :(   thanks  u666sa   So I know now that it is beta .. know that all too well. -  I will see what is possible maybe post a different thread if I need help with the downgrade. --

---

### Post by Impavidus on 2020-03-16
Release upgrades aren't always very reliable. On a clean system with hardware that works well with Linux, they usually work. For me release upgrades always work, but even then I found it's better to use a fresh install once every two years/four releases. If your system is less clean or if you have driver difficulties, release upgrades are less reliable. And I found that troubleshooting a failed release upgrade is rarely worth the time. Better to just fresh install.

Most computers that are less than 12 years old or so can boot from usb. There's no need for dvd. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I wouldn't call the interim releases beta versions, but they are indeed somewhat less polished than the LTS releases.

---

