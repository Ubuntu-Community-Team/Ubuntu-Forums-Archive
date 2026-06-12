---
title: "After installing new ATI drivers, keyboard and mouse do not work at all"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Grumpyo on 2012-03-10
Hi,

So I've had ubuntu for years now and never had major problems... until now...

I just bought a new computer a sony VAIO YB3V1E. As usual first thing I do is wipe out windows and install ubuntu 10.04. 

Everything works fine but I realize that the resolution is just terrible. I try to change it in the monitor tab but it only gives me 2 choices of 4:3 options, no 16:9 or anything else.... so it's pretty bad because the computer is not usable with a 4:3 resolution, it just kills your eyes.

After looking online I realize that it is because the computer has an AMD Radeon HD 6320 Graphics card and that linux with ATI doesn't see eye to eye...  and so I just don't have the right drivers.

So I look for a solution for that and stumble upon this page:[COLOR=Purple] [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) [/COLOR]

I just followed the instructions in the guide, first removed the drivers then reinstalled them manually. 

This worked perfectly, I get a new 16:9 resolution... [COLOR=RoyalBlue]everything looks nice and shiny BUT the mouse and keyboard do not work at all[/COLOR]. I tried USB mouse and keyboard as well, and nothing... :confused:

So I killed x using ctrl+printscr+e and there it's fine I can type no problem so it must be some sort of incompatibility with the drivers again....

And that's where I am completely stuck...:( I've already spent hours on the problem and just can't solve it... so if anyone knows what to do and can help that would be really really nice!

Thanks a bunch!

---

### Post by Mark Phelps on 2012-03-12
Since you seem to be able to get to a command line, I would use the info in the link below to remove the restricted drivers and replace them with the open-source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

You didn't say which AMD driver version you installed, but the Catalyst 12.2 just came out within the last couple of days.  IF you installed an older version, you could try those instead.

---

### Post by Grumpyo on 2012-03-22
Hi, 

Sorry for the late answer, subscription email went into spam so I didn't see your answer :(

I never managed to fix the problem even by trying what you said so I bypassed it and just wiped out ubuntu 10.04 and installed xubuntu 11.10... and it worked... I guess this card was just not supported by ubuntu 10.04.... 

Thanks for the help :)

---

