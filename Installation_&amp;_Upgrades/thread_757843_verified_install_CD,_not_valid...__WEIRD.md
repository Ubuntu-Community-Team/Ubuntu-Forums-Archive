---
title: "verified install CD, not valid...  WEIRD"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by nrcraig on 2008-04-17
I built my own PC to install Ubuntu....   This is what I've done so far...

1.) Used normal live CD to install, but then it just doesn't and says something about low graphics mode. The three choices bring me to the same black screen with a flashing courser.... not a command prompt... I tried.  Looked up this issue, folks said use a different CD, still nothing.  Verified that the boot cd was good on a different PC.

2.) Swapped out DVD drives... just for fun. :)

3.) Installed Micro$oft product.... guess that's what you pay for.

4.) Found someone else having similar troubles, allegedly due to the same integrated graphics (7020 nvidia).  Suggests alternate-install CD... that worked for the fella with "my" problem..... VERY HAPPY.

5.) Went through 3 CDs of the alt-intstall before I thought maybe I should check the md5sum on the two ISO files that I had. Both passed, however the integrity check on the newly built PC failed. So, I did a integrity check on a different PC... crossing my fingers the entire check.... that was dumb crossing your fingers never works.

6.) Get on the forums looking for this problem... I guess I took being an individual too seriously.

7.) Beg... PLEASE HELP ME.... PLEASE I DON'T WANT TO RETURN TO THE BAD HABIT THAT I LEFT 3 YEARS AGO.... PLEASE..... I WONT DO IT!!!

---

### Post by wpshooter on 2008-04-17
Please tell us something about the CD drive/burner that you are using.

Thanks.

---

### Post by nrcraig on 2008-04-18
I've used 3 different CD burners to make the install CDs.  Following sources: a Dell, an IBM Lenovo, and an iMac.  The Drive on the newly built PC is a Phillips with lightscribe, but I also tried to install using a standard Dell optical drive that I used when installing Ubuntu and Suse on that Dell.  I can't imagine that it's the optical drive... unless you see an issue with what I've told you.

---

### Post by Sef on 2008-04-18
Do you have an extra graphics card around?   If so, put it in and try it.

---

### Post by wpshooter on 2008-04-18
How do you have your optical drive connected to the motherboard ?  Is it an IDE drive and if so, what connector are you putting it on ?  How is the optical driver jumpered ?

If it is IDE, my suggestion would be to put it on the secondary IDE controller (without any thing else on that belt) and I would jumper it as MASTER.

Have you checked the FIRMWARE on the optical drive to make sure it is up-to-date ?

Are you sure that you have ALL of the power connectors, etc. on the motherboard on the correct connector/pins on the motherboard ?

---

### Post by nrcraig on 2008-04-18
Alright.... 

Sef- no, sadly I don't having a graphics card laying about and in the spirit of keeping this a budget box, on principle I'm not going to buy one till the end.... maybe next time I go visit the folks (2-4 weeks) I'll borrow theirs to check it out.

wpshooter- even though ever fiber in my body really didn't want to open that box... I did, because well... you never do know. Everything was plugged in firmly and all was well.  I tried putting the optical drive on the secondary IDE and it all worked out the same. The jumper was on master the whole time, and my hard drive is SATA so the optical is the only thing on it.  I haven't checked the firmware on the drive... I would have to wait to visit the folks for that.

Another slightly odd thing... for the two different iso files, on two different CD's (two different brands), burnt from two different computers.... have two different fail spots. The iso files have been verified and the CD's have been verified with an integrity test on a different PC.  To make things ever more odd is that the integrity tests on the built PC has varied in the spots to stop.

CD 1
1 - 9%
2 - 9%
3 - 17%
4 - 9%
6 - 15%
6 - 9%

CD 2
1 - 33%
2 - 35%

CD 2 on secondary IDE
1 - 33%
2 - 40%

Now, I work in a technical support job and wouldn't like me very much... but please stick with me.

Thanks guy/gals

---

### Post by nrcraig on 2008-04-19
Well, after my last post I decided that despite swapping out optical drives before and being able to install Windows I had better go to Wal-Mart and get a different one.  Guess what... it worked!!

wpshooter- How do I give you a Thank you?  Even though I was sure it couldn't possibly be a optical drive issue you were prasistant.  On top of that you made me do those first troubleshooting things... like check all my insides... it's a duh step, but sometime we get ahead of ourselfs and forget to turn it on. :)

Well anyway... it sounds like my HD is going to take a dump... it's making a click sound every 6-7 sec., but Ubuntu is installed so all is well in my book right now.

Thanks much!!

---

