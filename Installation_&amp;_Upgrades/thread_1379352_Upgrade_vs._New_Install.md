---
title: "Upgrade vs. New Install"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by edwardLS on 2010-01-12
I am in the process of making the switch from another OS to Ubuntu as my main OS on all my Desktops and Laptops.  However, as I see it, I have a real problem.

Background:  I have (only option) satellite internet at home which comes with a Fair Access Policy.  Bottom line is that upgrading Ubuntu from one version to the next is not a viable option.  I have been doing a new install as each new Ubuntu version was released.  I download the ISO image at work, burn it to CD, and carry it home.

If I go to the trouble of installing potentially several packages of application I desire/need, they will need to be re-loaded with a new install which I would like to avoid.  I have already put all my data (/home) on a separate partition.  

Am I overlooking the solution to my problem?  What I would like - is to download the new version ISO, carry it home and perform an Upgrade rather than a New Install from that new version.  Something like when I boot the LiveCD, I get an additional menu option to Upgrade the hard drive installation.  

Your comments and critisms are welcome.  I simply want to learn.

---

### Post by slakkie on 2010-01-13
Hi, have a look at the link in my signature about upgrading Ubuntu. Then have a look at the alternate CD section, it is exactly what you want/need.

---

### Post by edwardLS on 2010-01-13
slakkie,

This looks really great for my situation.  Thanks, I really appreciate the pointer.

Ed

---

### Post by miniyak on 2010-01-13
In my experience upgrades never go as well as clean installs

there are ways to make clean installs a little less painful though and I have been exploring them lately

One of these ways I have found is to just back up the settings folders of the programs that you use the most

for example I use a program called miro the aggregates video feeds. In order to remember my settings from one install to the next, I have found that simply copying the contents of the ".miro" folder that is hidden in the home directory onto external media for backup works. After the new version of ubuntu is installed I install the same version of miro then copy my settings into the new settings folder after i have run miro for the first time. Merge all, replace all, then I'm all set, same video feeds as before. This didn't work for all of the settings though (for instance video expiration time) 

With firefox 3.5rc from 3.5 current though i wasnt as lucky though because of the version change... not a big deal considering i use xmarks

Hopefully in the future ubuntu one will be able to carry over most of your settings... actually i heard that it already does for tomboy notes and evolution

---

### Post by slakkie on 2010-01-14
> **miniyak said:**
> 
for example I use a program called miro the aggregates video feeds. In order to remember my settings from one install to the next, I have found that simply copying the contents of the ".miro" folder that is hidden in the home directory onto external media for backup works. After the new version of ubuntu is installed I install the same version of miro then copy my settings into the new settings folder after i have run miro for the first time. Merge all, replace all, then I'm all set, same video feeds as before. This didn't work for all of the settings though (for instance video expiration time) 

With firefox 3.5rc from 3.5 current though i wasnt as lucky though because of the version change... not a big deal considering i use xmarks

Hopefully in the future ubuntu one will be able to carry over most of your settings... actually i heard that it already does for tomboy notes and evolution

Looks like you reinstall each Ubuntu version to upgrade and don't have a separate partition for /home. When you do, there is no need to copy files. I have the same homedir as I had for 6.06 and every setting I had is preserved. Ubuntu preserves all your settings when upgrading.

---

### Post by barnex on 2010-01-14
I also have the experience that in-place upgrades never work as well as clean installs...

---

### Post by miniyak on 2010-01-14
haha i did have a second partition for home by default on my s76 laptop... At the time i reinstalled i just couldn't see how that was helpfull

but i guess if you format the file system partition then install to that or something this type of thing would have been a lot more simple. Ubiquity hasn't really been streamlined for that however. I just needed to get my system back online in the fastest possible way i knew. That is, after borking grub a few days ago... decided to reinstall after finding restoring grub was taking to long...

I definitely want to learn some of the more complicated/ less streamlined solutions but sometimes things just have to get done.

---

