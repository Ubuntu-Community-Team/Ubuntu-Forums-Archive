---
title: "Xorg- I'm frightened"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by broomfighter on 2007-10-19
I've been using feisty since the begining of summer, trouble free except for manually entering HorizSync and VertRefresh, and I'm excited about upgrading to gutsy. Only trouble is, I can't see anything when I start the livecd
lol
I select Start or Install Ubuntu, but once it loads all I see is a kaleidescope
I thought it might have something to do with Xorg
Any help would be greatly appreciated- I want to see compiz fusion!
Thanks

---

### Post by repawn on 2007-10-20
Hi - I had the same problem with a few different machines - I just booted into safe graphics mode in the beginning. It usually gave me a pretty usable resolution. I am not sure that you will be able to see compiz with the livecd though. After iinstall I did have compiz though.

---

### Post by broomfighter on 2007-10-20
tried safe graphics mode and no love
i tried to upgrade from feisty but there was a bug with update manager and it quit
i restarted and when I logged in I got the kaleidascope
so I reinstalled feisty

---

### Post by broomfighter on 2007-10-25
Any idea what may be the problem?
Anyone?

---

### Post by tipiglen on 2007-10-25
sounds something like what I've got.  All the way through boot to login (I hear the drums) and I enter username and password (I hear the music), but no display.  before I tried 

sudo dpkg-reconfigure xserver-xorg 

I had the kaleidoscope, but now it's a blank screen and I can no longer get a terminal from ctrl/alt/F2, so I can't do anything.  FRUSTRATING!

I had Dapper working fine and then went through the sequential upgrade (official method) and now I've got nothing.  (thankfully I've got my laptop and it's doing fine on Gutsy)

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by kramer99 on 2007-10-26
Yep, exactly the same thing as what happened to me... I like the way you refer to it: "kaleidoscope", better than what I called it when describing it in an earlier post ("shifting mess of colours with black lines).

I spent ages and tried all sorts of different things but couldn't get it to work.  I've pretty much given up and am installing Fedora on that laptop as I type this.

---

### Post by broomfighter on 2007-10-27
It looks like this is a problem many people are having
does anyone have any idea how to fix it?

---

### Post by tipiglen on 2007-10-28
IF you can get a terminal (command line)  try ctrl/alt/F2 or 'recovery mode'  

try

sudo dpkg-reconfigure xserver-xorg 

and follow the answers offered.  I finally got a screen back and a more-or-less working installation by putting in "intel" as driver for my semi-ancient box.

I hope everyone enjoyed their extra hour this morning!

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

Williams and Holland's Law:
	If enough data is collected, anything may be proven by statistical
	methods.

---

