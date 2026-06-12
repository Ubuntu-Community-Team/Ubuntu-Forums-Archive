---
title: "Is gutsy7.10 kubuntu update really broken??"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by jammeramd64 on 2008-03-07
Hi All,
Noob HERE, I have worked with windows , xp and vista, as well as knoppix , mepis and ubuntu, kubuntu....

Downloaded ubuntu gutsy gibbon 7.10 installation and update went flawless...
Not the same for kubuntu, should note here( didn't install kde from ubuntu, but installed kubuntu from cd install disk after checking it for errors...installation went ok but when came time to upgrade 158 packages.. it broke..
couldn't get into the kdm gui only cli..

Also it wanted to fullly upgrade to 7.10 what ever that means ( I thought I had gusty 7.10 kubuntu cd install disk 697 mb i386 .iso

My question is, are the repositories down or are they broken or what,..
I just cant believe their broken because ubuntu did so well with it's upgrade...
Would appreciate any help with this matter before I try another upgrade...

Thanks All jammeramd64:popcorn:

---

### Post by jammeramd64 on 2008-03-07
Maybe i should be more clear on this, ubuntu rocks , kubuntu rocks hard, 
I am trying to get Windows users converted to linux, 

gdm is great but just is not quite right ,the  similarities just  are not  there ,like with kubuntu kde , kdm, it has more of a windows feel to it , and that is the key to getting more people into Linux as an open source o.s. Once their comfortable with kdm  then i'll show them gdm gnome...But i cant get updates to work right in kde.. 
Again any help would be appreciated , Thanks ALL......

---

### Post by Mark Bowers on 2008-03-07
Hi - I'm relieved to see your post. 

I have a Lenovo R61i that I installed 64-bit Kubuntu 7.10 on in January and all went well. I eventually decided to try Ubuntu 7.10 for comparison purposes. Several days ago I decided to move back to Kubuntu. The installation goes OK, but when it updates the programs after installation it errors out (when applying the changes after downloads - it corrupts the installation (kernel)?). It sounds like my error messages and symptoms were EXACTLY as yours.

I tried this several times with the same results. I thought it must be repository problems but had not got around to a post. Hopefully we'll find out what the problem is. For now, I'm back to Ubuntu.

M. Bowers

---

### Post by .nedberg on 2008-03-07
If you run```
sudo apt-get update
sudo apt-get upgrade
```
in a terminal I think you get an error claiming some packages did not install correctly. It tells you to run ```
dpkg --configure -a
``` if I remember correctly. Try that, it fixed it for me!

---

### Post by Mark Bowers on 2008-03-07
Well, I'm still pretty new at this, but I'm not sure if your suggestion will help. I (and I think the original post) were installing Kubuntu Feisty from scratch. The basic installation goes fine, but when it prompts you to update your packages, the following occurs.
 - Downloads all updates/packages
 - Begins to apply all of the upgrades
 - About 2/3rd of the way through the application of upgrades, the process errors out

At that point, I tried to reboot, but when I did it errors out (at reboot) and states the installation is corrupted (don't remember the exact wording).

Are you suggesting that after it errors out, I should open a terminal and then attempt the update all over again using apt-get? I guess I'm a bit hesitant to try that as I'm back to using Ubuntu and would have to reinstall Kubuntu. And, since this all worked fine in January, I can't help but think that something has gone awry in the repositories.

M. Bowers

---

### Post by jammeramd64 on 2008-03-07
Well thanks for the info..
             I did the sudo apt-get update. sudo apt-get upgrade, no errors @all so far??? 


               Thanks again for the info on this problem...hopefully solved

---

### Post by jammeramd64 on 2008-03-07
I think adept package manager is..., not as good as apt-get, this may not be the right place for this post but o well :KS

---

### Post by Mark Bowers on 2008-03-07
Well - I'm intrigued now. I'll reinstall Kubuntu 7.10 over the weekend and try aptitude for the updates. If it worked for you, it should work on my end. Are you using the 32b or 64b version?

M. Bowers

---

### Post by jammeramd64 on 2008-03-07
I have AMD dual core 4000+ 64b, with 2 gig's ram and 320 gig sata hd, machine...., 

            but not ready for 64 bit O.S. I am using the gutsy gibbon 32bit  i386.iso  697 mb cd not dvd... I like both versions of ubuntu7.10... LINUX ROCKS!!!!!

---

### Post by .nedberg on 2008-03-08
> **Mark Bowers said:**
> Well, I'm still pretty new at this, but I'm not sure if your suggestion will help. I (and I think the original post) were installing Kubuntu Feisty from scratch. The basic installation goes fine, but when it prompts you to update your packages, the following occurs.
 - Downloads all updates/packages
 - Begins to apply all of the upgrades
 - About 2/3rd of the way through the application of upgrades, the process errors out

At that point, I tried to reboot, but when I did it errors out (at reboot) and states the installation is corrupted (don't remember the exact wording).

Are you suggesting that after it errors out, I should open a terminal and then attempt the update all over again using apt-get? I guess I'm a bit hesitant to try that as I'm back to using Ubuntu and would have to reinstall Kubuntu. And, since this all worked fine in January, I can't help but think that something has gone awry in the repositories.

M. Bowers

If you get to a terminal, then yes, try the commands I gave you:
```

sudo apt-get update
sudo apt-get upgrade

```
you might also try
```

sudo apt-get dist-upgrade

```
but I would wait and see if the first ones worked before I did that.

If this works it should fix the problem (not sure about 64bit as I use 32bit on my AMD64) and you won't need to reinstall. I never rebooted when I had the problem though...

---

