---
title: "Trouble installing Ubuntu"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by lolerzone on 2015-06-04
So i got a new computer the other day, and right after building it, i tried to install ubuntu. First i tried 15.04. I could get as far as selecting to install ubuntu and watch the loading screen that comes after that, and then it blackscreened and said "invalid format". Whenn looking for solutions i tried adding nomodeset to the grub2 menu and starting the "try ubuntu" mode and pressing ctrl+alt+f1 and putting in sudo dpkg-reconfigure xserver-xorg

after that did not work i tried to install 14.10 instead, and that just resulted in a blackscreen after selecting install ubuntu.

specs:
GTX 970 windforce
i7 4790k
4 gb of ram
gigabyte gaming 5 (motherboard)

thanks in advance!

---

### Post by Bucky Ball on 2015-06-04
Why not try to install the stable LTS release, 14.04 LTS? See how that goes. It is supported until April 2019. The interim releases you tried, 14.10 and 15.04, are supported for nine months, until July this year and January 2016 respectively. They will then be unsupported and you will need to upgrade.

Boot from the 14.04 LTS install media (disk or USB) and 'Try Ubuntu'. If you are still greeted with a black screen add the 'nodmodeset' option at the 'Try Ubuntu' screen by hitting F6 and choosing that option from the popup menu (think that's still where it is although haven't used that option in awhile).

---

### Post by lolerzone on 2015-06-04
I just tried that, and it still results in a blackscreen. I assume that you meant to press e and add nomodeset at the end of the line starting with linux?

---

### Post by Bucky Ball on 2015-06-04
Yep, you can do it by editing the kernel line, but not sure how you're doing that if you are not able to install or get a grub menu.

What I meant was: Boot from the install media (disk or USB)> when you get to the screen of options to 'Try Ubuntu' 'Install Ubuntu' etc., hit F6 key and choose nomodeset from there. Select 'Try Ubuntu' and see if you can get to a desktop. If you can, that is the issue, and we can proceed to install and make the change permanent (which it isn't if you edit the kernel line or use nomodeset the way I've just described when installing).

---

### Post by lolerzone on 2015-06-04
Pressing f6 at that point does not do anything. Also, i found [This]("http://ubuntuforums.org/showthread.php?t=2262451") forum thread that is relevant to my problem, but i can use that fix as I can't even get to the splash.

---

### Post by Bucky Ball on 2015-06-04
Check [here]("http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html") under 'Live CD/USB Environment'. Can you get to the nomodeset option by pressing any key during boot from the install media?

---

### Post by lolerzone on 2015-06-04
i tried pressing different buttons right after selecting try ubuntu, and now there is a underscore at the top left of my screen (not blinking)

---

### Post by Bucky Ball on 2015-06-04
Not after selecting 'Try Ubuntu' but before it even gets there ...

After the manufacturer splash at boot, start hitting any key, for instance. Don't wait for the 'Try Ubuntu' options screen ...

---

### Post by lolerzone on 2015-06-04
that just seems to open the bios

---

### Post by lolerzone on 2015-06-04
Have i understood it wrong?

---

### Post by Bucky Ball on 2015-06-04
* Silly me. Try [this]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options"). ;)

Once you're at the correct screen you'll see the F6 options along the bottom, just hit F6 and choose 'nomodeset'.

---

### Post by RobGoss on 2015-06-05
From what I understand you build this machine correct?

Question: is Ubuntu the first system that you try to install on this machine is seems like there might be something wrong with the hardware. I have installed Just about every distor that Ubuntu has to offer and I have never gotten a black or blue screen.

---

### Post by Bucky Ball on 2015-06-06
That is great, RobGoss, but a blank screen at boot after a new install is what the issue is here and it is by no means a rare one. ;)

Still haven't managed to test the nomodeset option yet and don't see any evidence of anything being wrong with the hardware at this point  ...

The OP says, in the first post:

> I could get as far as selecting to install ubuntu and watch the loading screen that comes after that, and then it blackscreened and said "invalid format".

This indicates the hardware is working just fine when booting from the install media. It is only on attempting to install that things go pear-shaped, exactly at the point where nomodeset might help.

@OP: Can you select 'Try Ubuntu' and get to a desktop ok? Please let us know.

---

