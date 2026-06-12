---
title: "Installation on Vaio"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by chao_ordep on 2010-09-04
Hi 

I will like to know why I can't install ubuntu on a sony vaio model** **PCV-W10 the funny part is that I can use Ubuntu of the live CD but not intall it I've install a new HD and check it and it's fine I think it is a Driver problem

Thankx ahead of time

---

### Post by Sonsum on 2010-09-05
Can you give us some info on what's happening? Because theoretically, if you can run it from live-cd, you should be able to boot it.

---

### Post by presence1960 on 2010-09-05
> **chao_ordep said:**
> Hi 

I will like to know why I can't install ubuntu on a sony vaio model** **PCV-W10 the funny part is that I can use Ubuntu of the live CD but not intall it I've install a new HD and check it and it's fine I think it is a Driver problem

Thankx ahead of time

Not much helpful info on your question. What do you mean by you can't install it? What exactly happens when you try to install ubuntu? If you have windows on that disk did you: Are you doing an install side by side installation? Did you defrag windows at least once , preferably twice prior to trying to install ubuntu. Did you turn off system restore in control panel prior to trying to install ubuntu?

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the ubuntu iso before burning to a disk?

Did you burn the iso as an image to disk at no more than 4x-8x speed? 

Upon booting the disk did you choose check disk for defects?

So we can get more info to help you do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by dirghrabadia on 2010-09-05
Are you trying to dual-boot or just want Ubuntu on your Vaio?

---

### Post by chao_ordep on 2010-09-06
Thankx for the quick response. I am trying to install ubuntu by itself with now to diferent Hard Drives and I did check the opcion of checking the Hard Drive before Install and it passes so I proceed to install and it does the partition and begins to install buy right before it's about to finish it says it failed, I'll get the exact message I get and post it and also I will Get more info on the problem and generate the boot file.

Once again thank you for everything

---

### Post by chao_ordep on 2010-09-06
Thankx for the quick response. I am trying to install ubuntu by itself  with now to diferent Hard Drives and I did check the opcion of checking  the Hard Drive before Install and it passes so I proceed to install and  it does the partition and begins to install buy right before it's about  to finish it says it failed, I'll get the exact message I get and post  it and also I will Get more info on the problem and generate the boot  file.

Once again thank you for everything

---

