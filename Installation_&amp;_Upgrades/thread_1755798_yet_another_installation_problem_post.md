---
title: "yet another installation problem post"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by labatts on 2011-05-11
(there seem to be a few of these, hence the title.  I did not see my specific problem, so I made a new one.)

**What I am trying to do:**
I currently have ubuntu 11.04 installed on my computer (_dell xps400_).  I previously had installed kubuntu 11.04, but there was an issue (bug reported) about webcam mics not working on skype.  Since my inlaws want to see their grandchildren, I dutifully switched to ubuntu.  Now, I would like to install kubuntu 11.04 alongside ubuntu so that I can tell whether or not skype is working correctly now since there has been a recent update to audio stuff. - I realise that I could simply install kubuntu-desktop, but I don't want to do that for a couple reasons.
[B]
Problem:[/B]
Kubuntu 11.04 installer freezes just prior to the screen that allows you to select the partition.  This happens regardless of whether I boot to the live cd (live cd works fine) or try to install directly.  I have checked the md5sum, downloaded twice, used two different cds.  Nothing seems to make a difference.  **Any help is appreciated.**

---

### Post by Quackers on 2011-05-11
Have you used the "check for errors" menu item on the cd?

---

### Post by blauendonau on 2011-05-11
Sounds like you might have a bad CD. Did you burn an .iso image to the CD yourself or did you get the CDs from somewhere else? Disk burners aren't perfect, make sure to use the slowest burn rate available (8x is recommended) to lessen the chance of problems. I suggest checking for errors via the provided tool on the live CD.

(BTW, if you didn't want to install kubuntu-desktop because of all the programs included in the package, it is possible to download a KDE-base package without any of the typical Kubuntu applications like konqueror, etc. I haven't tried that in Natty but it should be possible.)

---

### Post by labatts on 2011-05-11
No, that I haven't tried.  I will do so tonight.

---

### Post by labatts on 2011-05-11
Okay, thanks both of you for the help.  Seems Quackers was right:  I ran the 'check for errors" prompt on the cd, and it found 1 error.  Seems it only FINDS the errors, but does not fix them as it only gives the option to restart the machine.

So, I am downloading yet another time (this will be the third).  

TO answer your questions, I wrote the iso to the cd myself via the standard right click function in ubuntu.  I checked this time, and there are only 2 options for speed:  maximum and 10x.  

You are right, I don't like the multitude of packages in the menu (kde and gnome), but that is not why I want to have separate installs.  I mainly want to see if skype works now.  I am afraid that if I simply sudo apt-get install kde-base (or whatever) that skype will work simply because I have the gnome stuff installed (perhaps I am wrong?).  

What I ultimately want to do is a fresh install of kubuntu, wiping everything clean.  But I don't want to do that unless I know that skype will work.

I will let you know if the new download works... =)

---

### Post by Quackers on 2011-05-11
There is no need to download the iso again if you have already checked the md5sum of the one you have. It's the burning that's the problem. Many people use Brasero to burn the image, whereas others recommend k3b which has been more consistent for me. The speed should be more variable too.

---

### Post by labatts on 2011-05-12
It finally occured to me that I could test the cd on my netbook (not actually installing it, but seeing if I can get to the hard drive formatting screen - the install cd freezes just prior to this screen).  This worked just fine on my netbook (it is my desktop that is giving me trouble) which tells me that the cd is fine. ** I think the install cd seems to be having trouble reading my partitions.**


I am not sure what to do about that.  I think there is gparted? but I have never used it, so I will check that out.  If it matters, there is only the one os currently installed (ubuntu natty).  Hopefully this is not pointing to more serious problems (seems unlikely since i just clean installed ubuntu two weeks ago).

Again, thanks for the help so far.  Hope you guys have some suggestions =)

---

### Post by labatts on 2011-05-13
I installed kubuntu by itself (wiping existing ubuntu, rather than installing side by side), and it worked fine.  So, it seems that the installer cannot handle 2 ubuntu derivatives at the same time.  Thanks all for the help. 

Not sure how to mark as solved...

---

### Post by Quackers on 2011-05-13
The 11.04 installer can handle previous installations of Windows and Ubuntu just fine. Something else is wqrong. It's possible that your partition tablw was damaged perhaps, or maybe you already had 4 primary partitions on the disc. We'll never know now though  :-)
To mark the thread solved use the Thread Tools heading (in red) near the top of the page.

---

### Post by labatts on 2011-05-13
> **Quackers said:**
> The 11.04 installer can handle previous installations of Windows and Ubuntu just fine. Something else is wqrong. It's possible that your partition tablw was damaged perhaps, or maybe you already had 4 primary partitions on the disc. We'll never know now though  :-)
To mark the thread solved use the Thread Tools heading (in red) near the top of the page.

Hehe - I am quite happy not knowing.  To be clear, though, Windows was never involved.  I quit that habit years ago!  I was trying to have ubuntu 11.04 along with kubuntu 11.04.  Anyway, thanks again for the help.  

By the way: if anyone else is having a similar issue with skype in kubuntu, the solution i used was found at [https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274](https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274) .

Quackers, I think I miss understood you (blush).  Thanks

---

