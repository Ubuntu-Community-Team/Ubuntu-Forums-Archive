---
title: "Alpha 6 released"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-12
Last alpha before beta

[http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)
[http://cdimage.ubuntu.com/releases/jaunty/alpha-6/](http://cdimage.ubuntu.com/releases/jaunty/alpha-6/)
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

Don't know if the info at first link is up to date. Looks the same as for alpha 4 and 5.

If you are already using an alpha, you do not need to download/install this. you should already be up to date.

---

### Post by xtoudi on 2009-03-12
> **andrewabc said:**
> 
If you are already using an alpha, you do not need to download/install this. you should already be up to date.

OK is it working for you?? I mean **apt-get dist-upgrade**. For me there's nothing to upgrade.

---

### Post by andrewabc on 2009-03-12
> **xtoudi said:**
> OK is it working for you?? I mean **apt-get dist-upgrade**. For me there's nothing to upgrade.

On my old computer, I installed alpha 5. Right now it has all the updates installed and is the same as downloading/installing .iso alpha6

If you installed a previous alpha, and kept up to date with updates, you are basically running alpha6. There is no apt-get dist-upgrade when new alphas/betas/RC are released if you were already using an alpha.

Are you upgrading from 8.10? I wouldn't recommend that.

---

### Post by xtoudi on 2009-03-12
> **andrewabc said:**
> On my old computer, I installed alpha 5. Right now it has all the updates installed and is the same as downloading/installing .iso alpha6

If you installed a previous alpha, and kept up to date with updates, you are basically running alpha6. There is no apt-get dist-upgrade when new alphas/betas/RC are released if you were already using an alpha.

Are you upgrading from 8.10? I wouldn't recommend that.

I've got Alpha 5 indeed. Up-to-date of course;)
So ... should I think that now I've got Aplha6??

---

### Post by ruik on 2009-03-12
> **xtoudi said:**
> I've got Alpha 5 indeed. Up-to-date of course;)
So ... should I think that now I've got Aplha6??

Yes.

---

### Post by bobmatino17 on 2009-03-12
... dont try upgrading from 8.10 or 8.04... bad experience... i still love jaunty though!

---

### Post by wipeout140 on 2009-03-12
> **xtoudi said:**
> I've got Alpha 5 indeed. Up-to-date of course;)
So ... should I think that now I've got Aplha6??

Yes

---

### Post by andrewabc on 2009-03-12
> **xtoudi said:**
> I've got Alpha 5 indeed. Up-to-date of course;)
So ... should I think that now I've got Aplha6??

Yes.
And when beta and RC and final are released, you will not have to download iso and install it.
As long as you keep up to date with updates, you will have the latest version.

---

### Post by xtoudi on 2009-03-12
Thx ... I don't need waste my time waiting for sth:)

---

### Post by xtoudi on 2009-03-12
OK. I think that I should say that I've got Alpha 5 (now is 6) upgraded from 8.10 ;) There was nothing problems with that in my case. Additionally I've got EXT4 boot/root partition (upgraded EXT3) - there was a few troubles with that. But finally everyting is fine (excepet pulseaudio server - some problems with sending a lot of sound data from one PC /PA client/ to other PC /PA server/).
But ... 8.10 to 9.04 is possible without any problems;)

---

### Post by forumache on 2009-03-13
> **xtoudi said:**
> But ... 8.10 to 9.04 is possible without any problems;)

Same here.

People who had a bad experience with update, have you filled bug reports on launchpad?

Remember, Ubuntu Linux is not like "the other OS", you don't need to reinstall. A dist upgrade should be smooth. I upgraded Ubuntu since 6.04, on the same computer, and it runs perfectly.

Please help make the dist-upgrade experience a smooth one for other users by reporting your negative experience with as much details as you can provide.

Thanks in advance.

---

### Post by Nullack on 2009-03-13
Fresh install fails for me using ubiquity on AMD64, Ive bugged it.

---

### Post by bluenova on 2009-03-13
I decided to give Alpha 6 a go. Installing on AMD64 / nVidia system but the 32bit addition with the alternative disk (fresh install).

Streight after selecting install I get a message 'CPUFREQ: NO NFORCE2 CHIPSET' and the installer hangs. I found a reference to that error [here]("http://ubuntuforums.org/showthread.php?t=1074757&highlight=cpufreq") but supposedly it was fixed before Aplha 6. If I disable ACPI it still gives the message but gets passed it and continues the install but the computer then runs very slowly.

---

### Post by ELD on 2009-03-13
Where can i find some mirrors for the alpha 6 download?

---

### Post by ubu-for on 2009-03-13
> **bluenova said:**
> I decided to give Alpha 6 a go. Installing on AMD64 / nVidia system but the 32bit addition with the alternative disk (fresh install).

Try the Desktop CD instead.

---

### Post by rogerdean on 2009-03-14
Folks, on the a6 download page I also see a 4.3GB DVD image. Can anyone tell me what this is, what's on it, and whether DVD images exist for releases?

Allbest
Roger

---

### Post by andrewabc on 2009-03-14
> **rogerdean said:**
> Folks, on the a6 download page I also see a 4.3GB DVD image. Can anyone tell me what this is, what's on it, and whether DVD images exist for releases?

Allbest
Roger

Yes there are always DVD releases.
DVD contains lots of extra programs and stuff on the DVD.
Think of it as having a repository on the DVD. The DVD will install just like the CD (I think), with same default software etc. But if you need other software you can get it from the DVD.

This is useful for people with slow/no internet connections. Download the DVD somewheres with fast internet. Then install it, and if additional software wanted, some of it will be on DVD and can get it from there. You can point to the DVD as a  source in system->admin->software sources->3rd party->add cd-rom

If you have a decent internet conection better off geting CD and putting it on cd-rw disc, then update cd-rw everytime there is a new release.

---

### Post by rogerdean on 2009-03-14
thanks andrew - wish i'd found that before. would have saved a whole lot of slow downloading...
cheers

---

