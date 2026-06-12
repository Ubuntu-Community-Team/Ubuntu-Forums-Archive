---
title: "Gutsy and Dell ATG D630"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by gruss on 2008-01-16
Anyone accomplished this lately?  Did some searching and it seems there are a few issues but i'm wondering if i should stock up on beverages and plan a weekend or have most of the bugs been ironed out.  most of the threads seemed to be back from Oct and it seems most issues are or can be resolved.  I coud live without sound, for well, ever but wifi would be nice :)
LiveCD loads, but screen res is off, and no network, BT or sound although the device mgr appears to show everthing (but sound card).  is this just a matter of laoding some restriicted drivers or am i gonna bleed some?  Not asking  for a step by step, just wondering if this is a huge PITA, or just like every other clean install on a notebook?

I need to keep XP on there too, any horror stories about g-parted?  I've used partition magic numerous times with no ill results and could use it again but if I can do it all from the cd I like trying new things.

---

### Post by RockHaxor on 2008-01-16
I just installed gutsy on my friends 1710 with little problems. Sound, Webcam, and Flash in firefox were really the only issues.

---

### Post by gruss on 2008-01-16
Encouraging, mine doesnt have anywhere near the bells and whistles of an XPS...just ready to upgrade ubuntu out of its VMware session on the notebook.  I'm likeing it on my older pc's and want to see how it does with something more modern than a PIII

---

### Post by irish8890 on 2008-01-17
I have a Dell 630 - internals should be identical with the exception of the ATG packaging.

I used g-parted to create my partitions (shrunk WinXP to 30GB, 10GB or so for /, 40GB for home, 1GB swap & 512k for /boot.
I used te alternate install cd to install the 64-bit Gutsy.

Ubuntu 7.10 installed fine and worked.  I did have to do a couple of things to get things working to my liking:

- To fix grahics: Download nVidia linux drivers from their web-site and install them.  You have to shut down the graphics server, gdm, to run the nVidia provided scripts,

- To fix sound: I followed Method G from here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

- To make the Touchpad work a little better I added these three lines to my /etc/X11/xorg.conf file:
        Option          "SHMConfig"     "true"
        Option          "MaxSpeed"      "0.99"
        Option          "AccelFactor"   "0.08"
The touchpad worked more to my liking (not sure which post I picked that from).

- I have the Dell 1505 Draft 802.11n card,  I have not been able to get this card to work with WEP or WPA.  However, unsing ndiswrapper and extracting the Dell driver as outlined in the links below got me to where I can use wireless.  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Disable wireless security on your router when you try to connect. I have MAC filtering to only allow my laptop. For security you can try:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)


Post back if you have trouble I can try to help.  I am also interested to know if you manage to get wireless security working.

Good Luck!

John

---

### Post by gruss on 2008-01-19
I'm going to try that on the touchpad thanks!!!  it moves sooo slow and cant speed it up, the eraser mouse work ok but I hate those.

All in all the install was pretty smooth, not any worse I don't think than doing a straight install from XP...except that I'm way more familiar with windows but I can't blame ubuntu for that.

G-Parted worked like a champ
I have the boradcom 1390 wireless adapter so I dont think what I did will be the same as yours?  Had to use ndiswrapper but its been stable hooked up to my WPA wireless at home.  If you want to try it I can find the links to the directions I used, they were on the wiki somewhere, under "G method" for "wireless on D630"

Still have the minor sound problem of the "exponential volume control"  where the first 2/3's of the slider do very little and the last 3rd is pretty much all your control but its adequate, dont do much serious listening on it.  If I do I'll probably pick up a turtle beach usb sound card.

Mine doesnt have the nVidia card for video, its intel and worked fine out  the box from what I can tell.  EDIT:  Well while poking around with no real problems to solve I tried to pretty it up a bit but found I cant enable anything fancy?  Compiz is installed but I'm kinda lost.  That was easy, lost no more add "SKIP_CHECKS=yes" to compiz-manager and going.  Dont think I'll the heavy stuff just leave the middle of the road settings.

The last peice of the puzzle is BT, looks like the OBEX is working, although I havent done a complete test, probably try with the razr and Tungsten tonight, but it would be nice if my little mogo pc card mouse worked to...I dont' have my hopes though ;)  EDIT: Can navigate the razr filesystem via BT but cant transfer files to my palm, have to keep working on that but I heard it was a bug so...Anyone have any ideas on the mouse though I'd appreciate it.

So far 2 boxes @ home completely converted and running fine and now the dual boot 64bit ubuntu on the d630 seems stable, and with the lower overhead than XP runs nicely (although xp runs really well with 2 gig of ram in it too).  The innards on the ATG are pretty much the same as the standard latitudes, just hardened against shock, same internals are available for either.  Actually the suspend and hibernate work better than XP so far.  It occasionally hangs in suspend mode in XP havent seen that yet in ubuntu!  Both OS's hibernate fine.

Is there a "good" reason to use the 64 bt install vs the 32 bit?  I've seen a few progs that won't work on the 64 bit version, not deal breakers but support seems lacking?

Heres the thread that helped get my wireless working:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

