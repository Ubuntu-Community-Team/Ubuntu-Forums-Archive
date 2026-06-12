---
title: "Oh no! Error Loading Operating System :("
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by uberbuntufan64y on 2010-06-19
*PANIC* I just got through my Ubuntu install and I got an Error Loading Operating System!!!!
:confused:
*/PANIC*

---

### Post by presence1960 on 2010-06-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by uberbuntufan64y on 2010-06-21
Thanks for the quick reply but i r a n00b. its hard for me to understand the complicated instructions. any chance i can have the for dummies version? k thx!

---

### Post by uberbuntufan64y on 2010-06-23
bump

---

### Post by darkod on 2010-06-23
What's exactly complicated in the instructions in his post?

---

### Post by ronparent on 2010-06-23
Ok, I'll play the straight man. Highlight the text in the box labeled 'Code:'. Copy and paste it to a terminal you will open for that purpose (in the menu bar Application>Accessories>Terminal). Highlight and copy the output of the command and paste it to your reply - with or without quotes. Then the good people following this thread will then be able to read and interpret the results and hopefully tell you what to do.

---

### Post by uberbuntufan64y on 2010-06-25
> **ronparent said:**
> Ok, I'll play the straight man. Highlight the text in the box labeled 'Code:'. Copy and paste it to a terminal you will open for that purpose (in the menu bar Application>Accessories>Terminal). Highlight and copy the output of the command and paste it to your reply - with or without quotes. Then the good people following this thread will then be able to read and interpret the results and hopefully tell you what to do.

this seems like maybe I can figure it out. i will try and see what i get.

---

### Post by uberbuntufan64y on 2010-06-25
i forgot i installed it on vista not using a cd... oh noes #-o

---

### Post by uberbuntufan64y on 2010-06-25
any ideas on what to try now?

---

### Post by Rubi1200 on 2010-06-25
Are you talking about installing using Wubi?

If you want Vista back, take a look at this:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

---

### Post by uberbuntufan64y on 2010-07-26
> **Rubi1200 said:**
> Are you talking about installing using Wubi?

If you want Vista back, take a look at this:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

I got busy with things and had to put this project aside for awhile, but I just turned my computer back on and decided to try again but still it was a fail :(

---

### Post by CompEngStudnt on 2010-07-26
Wubi is the version I just had and it crashed a few times and had a few bugs. To really install ubuntu : you need to write it to a disc or usb. From there, you can try ubuntu with less problems. The update messed up by installation through Vista, and that is my solution the the problem you have.

It will only take a few minutes and all of the directions are in drop-downs on the download page.

---

