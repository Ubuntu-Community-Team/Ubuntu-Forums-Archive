---
title: "No version of Ubuntu will run or install...."
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by locknessmonster on 2012-12-23
Long story short a family member of ours was having computer issues and is not very computer savvy. She dropped off her tower and I was messing around with it a little bit and finally found out that she had completely fried the harddrive. I bought a new harddrive (the exact same model) and it currently has a pre-existing windows xp on it. 

I have tried 12.10, 12.04, 8.04, 6... etc. I have tried at least 5 different liveCD distributions. When booting from the liveCD the main menu pops up just fine. After this however I cannot do anything. On 12.10 and 12.04 clicking "try before installation", "install" or anything causes the computer to just endlessly restart. On the older versions (such as 8.04) it starts unpacking and then a black screen with a single blinking underscore appears and then nothing happens. I have tried liveCD, I have tried installation through USB, I have tried what seems like almost everything.

Eventually I gave up and tried to use ophcrack to just unlock the windows xp for her so she had something and that keeps freezing on the "unpacking linux..." screen. It is a compaq presario from.. Probably around 2004 or so. The computer had 512mb RAM and I installed an additonal 256mb for her so memory isn't a major issue here. I feel like I have gone through everything and just don't know what to do for her from here. 

Any help would be GREATLY appreciated. Thanks :D

---

### Post by Bucky Ball on 2012-12-23
Welcome to the forums.

Try 12.04. When you get to the Try Ubuntu, hit F6. From the pop-up menu choose 'nomodset'. Proceed ...

11.04 and earlier are no longer supported and could compromise the security of your machine. The stable 12.04 LTS is supported for five years, until April 2017.

PS: Please use paragraphs. Big blocks of text are unappealing and hard, if not impossible, for some users to read. This will increase your chances of help (some users will see the big black blob and move on).

---

### Post by 2F4U on 2012-12-24
Since so many different versions are not working, I am thinking that there could be an issue with RAM. I would suggest that you run memtest from a liveCD. Let it run for at least two iterations.

---

### Post by oldfred on 2012-12-24
If the computer is that old does it have a CPU with the PAE extensions? You may have to install Lubuntu to have a 32bit version that works.

       [https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

### Post by locknessmonster on 2012-12-24
Sorry for the huge paragraph of text originally I posted that late last night and have been pretty busy recently. 

I am performing a memory test now and will try different installation options and see what happens. If nothing works there then I will try out lubuntu. Thanks everyone for the replies.

EDIT:UPDATE: Memory tests passed. Tried using nomodeset and tried lubuntu both with the same result. After choosing either try without installing or install, the screen would wait a few seconds, then the screen would turn black as if an empty command prompt with no words. Wait a few more seconds, and then I can hear the computer turn off for a second then restart. :?

---

### Post by Bucky Ball on 2012-12-24
> **locknessmonster said:**
> Sorry for the huge paragraph of text originally I posted ...

All good. Just a heads up so you might have a better chance of helpers populating your thread.  ;)

---

### Post by locknessmonster on 2012-12-24
Still trying, nothing working. 

Just to see I made a disc for Fedora to see if other linux distributions would work. This one didn't autorestart the computer but gave me an error message. It consisted of mainly a huge block of numbers and at the end said 

Code:Bad EIP Value
Kernel Panic - not syncing Attempting to kill init!

I'm not sure what that means.

Edit: I tested all of these discs on stable computers to ensure that they were working properly, including this one that gave the odd error on the computer im working on.

---

### Post by locknessmonster on 2012-12-25
Nothing works at all I am on wit's end. I tried multiple different linux distro's, tried tried every possible combination of load settings. AntiX linux seemed to be the closest I could get to working but eventually just went blackscreen and stopped.

---

### Post by snowpine on 2012-12-25
Lots of good sales at Best Buy today. :)

---

### Post by Bucky Ball on 2012-12-26
locknessmonster: Your problem is bizarre and unique! It could be some odd combo of the RAM you installed with the original that is causing the conflict. Perhaps, just for a test, try taking out the RAM you installed and installing Xubuntu or Lubuntu with the 512Mb original RAM and see if you get a glitch (they should install or at least we might learn something from the outcome ...).

;)

---

