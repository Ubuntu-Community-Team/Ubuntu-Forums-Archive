---
title: "black screen on ubuntu 9.10 lenovo install."
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by 10010110 on 2009-11-17
Hey guys, Finally taking the full dive into linux double booting win 7 *only as backup, hate it* but every time I try to Fresh install ubuntu 9.10 32 & 64 bit or even upgrade it on a lenovo y550 (4186), I get a black screen, I see a flash of a few white lines for an instant then black and it stays there, let it sit for 5 hrs came back and still there. Ive tried looking around and tried the key combos at start but to no avial, any help would be amazing, trying to get it installed so I can start working on the WIRELESS issue in ubuntu studio haha please keep in mind im new to linux but can use terminal a little. can ANYONE help me???
 
proc: Intel core2 duo p8600 @ 2.40ghz
ram: 2.00gb ram
graph: intel 45 express chipset family

---

### Post by hellmet on 2009-11-18
At what stage of the installation is that happening? Also, have you tested the RAM? Let us know more details.

---

### Post by 10010110 on 2009-11-18
it begins right after I start, goes to boot into install and then black screen and ive tried the memtest and no issues where found.  so I choose english>next>try/install or even direct install>black screen.

---

### Post by TheDelChop on 2009-11-18
I also have this exact same problem.

---

### Post by 10010110 on 2009-11-24
After looking for weeks still no solution to the black screen if any one finds any thing out please let me know, I would love to indulge me some 9.10 hehe

---

### Post by ntom-taylor on 2009-11-28
I have the exact same problem.

> it begins right after I start, goes to boot into install and then black screen and ive tried the memtest and no issues where found. so I choose english>next>try/install or even direct install>black screen.

I am using ubuntu-9.10-desktop-i386.iso
Checked the md5sums of local copy and matches.. 

Never had any problems in the past with 7.10 or 8.04 - this is my first time of this hanging black screen @ installation..


********************

with disbaling 'quiet' and adding 'nosplash'. . system seems to be looping saying stuff like;

```

sr 1:0:0:0 [sr0] Unhandled sense code
sr 1:0:0:0 [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 1:0:0:0 [sr0] Sense Key : Hardware Error [current] 
sr 1:0:0:0 [sr0] Add. Sense: Timeout on logical unit
end_request: I/0 error, dev sr0, sector 274680

```

Hope this helps in sorting this issues for myself and others..

---

### Post by 10010110 on 2009-11-29
Hey guys sorry if I did but have I posted this in the right area?? And I guess I will just wait till April 2010 for[URL="https://wiki.ubuntu.com/LucidLynx"] Lucid Lynx (10.04)
[/URL]

---

### Post by izelpii on 2009-11-30
Hey, I just bought the same laptop (but with i7).

Did you checked this link?

[http://ubuntuforums.org/showthread.php?t=1300067](http://ubuntuforums.org/showthread.php?t=1300067)

---

### Post by echotone on 2009-12-11
I have the same exact problem. BUT!!! What i noticed is that i never had this problem until i tried win7. now all of a sudden, i cant load the free competition software. coincidence??? I HIGHLY doubt it. I tested my memory with the ubuntu cd and tried both the install and live session. nothing works.

I can at least get the system installed with the alternate cd but i still cant boot into it. i get the white line flashes and then it stays black. I am going crazy over this. all i want is my ubuntu back...:(((((

P.S. ---I am having problems on my pentium 4 desktop. I have a core2Duo in my laptop and i have gone from win7 to xp to ubuntu all in the same day with no problem. so idk what the deal is with my desktop.

---

### Post by 10010110 on 2009-12-28
Same here, installed Fail 7 then Xp and cant upgrade to 10 without black screen.

---

### Post by 10010110 on 2010-01-10
not sure why I haven't thought of this before but has any one tried to write zeros to to your drive? that way its virtually a fresh drive....may give it a try. will update later.

---

### Post by devix91 on 2010-01-10
I am also experiencing this problem, if any of you find a solution PLEASE let us know how you did it!
:D good luck to ya' all and thanks ^__^

EDIT: If you go over |"Install UBUNTU", press F4 and "run in safe graphics" mode ( or something along those lines), it should work.
Worked for me, hope it works for you too ^_________^

---

### Post by mugz on 2010-02-09
Hey,

I had the same problem with a Toshiba Satellite a110. I tried the installation with a live CD of 9.04 Jaunty Jackalope and it worked without problems. I will try to upgrade to 9.10 afterwards.

---

### Post by spyrule on 2010-03-03
I have the Lenovo y550 too (the one with the t6500 Centrino). I initially installed 9.04 on the system (not dual-booting or anything) and everything worked great. Ran all of the updates, everything worked great. Upgraded to to 9.10 and black screen on boot. I could hear the chime when Ubuntu logged in, but nothing but black. The only thing I could do was hit escape while the GRUB was loading, and boot from the old kernel (I dont' remember the version numbers). The only problem when booting this way was that the trackpad wouldn't work. So I plugged in a usb mouse and everything else worked fine. Though, I didn't really want to carry a usb mouse around with me everywhere I took the laptop, so I reinstalled 9.04; ran all updates except  the upgrade to 9.10; and now everything works great! I tried several things when I was getting the black screen, but nothing panned out. 

The re-install of 9.04 is the only non-irritating way to go, me thinks. Run all the updates, but don't upgrade to 9.10.

---

### Post by spyrule on 2010-03-15
So, I ended up following the instructions [here]("http://guide.ubuntuforums.org/showthread.php?t=1409194&highlight=lenovo+y550#5") and everything works great now!

Here's what I did in a nutshell:

1. Upgrade to Karmic (the same steps may work from a fresh install, but I haven't done it)

2. After upgrading, you'll need to restart the computer. When the boot process hits the Grub screen (you may have to hit ESC to get to it), choose "Ubuntu 9.10, kernel 2.6.28-18-generic"... Upon booting, you may need to have a usb mouse handy, as the trackpad may not respond

3. Ubuntu should have loaded. If it did, add 'deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main' and 'deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main' (without the quotes) to your repository list (System->Administration->Software Sources)

4. Run update manager, you should have a whole bunch of packages that can be installed from the aforementioned sources

5. From a terminal type: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confBAK, then run: sudo gedit /etc/X11/xorg.conf, and make the settings look like so:
          ```
          Section "Device"
              Identifier    "Configured Video Device"
              Driver        "intel"
          EndSection

          Section "Screen"
              Identifier     "Default Screen"
              Monitor       "Configured Monitor"
              Device        "Configured Video Device"
          EndSection
```5. Edit /etc/xdg/compiz/compiz-manager, and add 'INDIRECT="yes"' after the last line, like so:
          ```
          COMPIZ_BIN_PATH="/usr/bin/"
          PLUGIN_PATH="/usr/lib/compiz/"
          COMPIZ_NAME="compiz.real"
          INDIRECT="yes"
```7. Reboot your computer, and everything should work okay.


** - 'Driver "intel"' is of course assuming that you have an Intel video card as opposed to NVidia. I've only done this with a Intel card.

Please let me know if this works for you!

---

