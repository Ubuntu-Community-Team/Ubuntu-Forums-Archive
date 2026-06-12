---
title: "Question about updating to jaunty."
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-03-30
Just curious as I have never updated distros before... Do you HAVE to update using the live CD or can you update using command line?  And if you can update using command line, so you have to re-install everything again?  Like the medibuntu repositories and packages you have installed like VLC and my settings for my home directory etc?


Sorry if this seems like an easy question to the old hands here, but I am still a veritable Babe in the open source world and have never done a distro upgrade before..(unless you count getting rid of Windoze and installing Ubuntu.)

Thanks for reading.

---

### Post by Therion on 2009-03-30
> **cptrohn said:**
> Just curious as I have never updated distros before... Do you HAVE to update using the live CD or can you update using command line?
You can upgrade from the command line, yes.  If decide to take this route know that you can not skip released versions; meaning if you're running 8.04 (Hardy) and want to install 9.04 you must upgrade to 8.10 (Intrepid) and then upgrade *again* to 9.04 (Jaunty).  On a personal note, I don't recommend doing "dist-upgrades" (meaning upgrades from the command line).  Many people will disagree, and I'm not saying they're wrong, but the only time I've ever had an upgrade issue, big or small, is when I used dist-upgrade instead of doing a clean install.  But that's just me; your mileage WILL vary.

> **cptrohn said:**
> And if you can update using command line, so you have to re-install everything again?  Like the medibuntu repositories and packages you have installed like VLC and my settings for my home directory etc?
No...  At least in theory.  If we assume (!) that everything goes juuuuuuust right during the dist-upgrade, all your data and settings will remain intact.  Tempting I know.  It's the Siren's call of doing a dist-upgrade versus doing a clean install.  What separates those who hear this song and manage to navigate the waters unharmed from those who wind up washed up on the rocks?  No man can say with certainty.  The decision is yours.

---

### Post by DougieFresh4U on 2009-03-30
Most would not recommend updating via terminal. It can be done by altering your 'sources list', where as you change all instances of 'Intrepid' to 'Jaunty', then saving and update and upgrade via terminal. Some repo's  are not ready for Jaunty yet. Medibuntu is one that is one that is in Jaunty.
I am just answering your question, I am not recommending you upgrade this way!

---

### Post by Kareeser on 2009-03-30
There's a much easier method:
```
update-manager -d
```

Needs a GUI though, as the update manager is a GUI program.

---

### Post by cptrohn on 2009-03-30
Ok, thanks for all the great answers guys!

---

### Post by cptrohn on 2009-03-30
> **Therion said:**
> You can upgrade from the command line, yes.  If decide to take this route know that you can not skip released versions; meaning if you're running 8.04 (Hardy) and want to install 9.04 you must upgrade to 8.10 (Intrepid) and then upgrade *again* to 9.04 (Jaunty).  On a personal note, I don't recommend doing "dist-upgrades" (meaning upgrades from the command line).  Many people will disagree, and I'm not saying they're wrong, but the only time I've ever had an upgrade issue, big or small, is when I used dist-upgrade instead of doing a clean install.  But that's just me; your mileage WILL vary.


No...  At least in theory.  If we assume (!) that everything goes juuuuuuust right during the dist-upgrade, all your data and settings will remain intact.  Tempting I know.  It's the Siren's call of doing a dist-upgrade versus doing a clean install.  What separates those who hear this song and manage to navigate the waters unharmed from those who wind up washed up on the rocks?  No man can say with certainty.  The decision is yours.

Not having to re-install everything does make it sound tempting to at least give it a try.... I mean what is the worst that could happen?  That I would just have to re-install from a live CD if things went wrong?  Or is there the risk of damaging hardware too?

---

### Post by ghindo on 2009-03-30
There is absolutely no risk of damaging your hardware.  Go for it! ;)

---

### Post by drs305 on 2009-03-30
If you don't have a separate /home partition and elect to do a clean install you will be spending time recreating your old settings. If you do an online upgrade you may have problems (though I haven't experienced them).

Here's the middle ground. From the livecd or systemrescuecd, use *partimage* to make a copy of your system partition. I'd say 'exact copy' but partimage doesn't include free space. Then run the online update. If it works, fine. If it doesn't, you can restore  your old system or do a clean install. 

Here's a good link for using Partimage:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by cptrohn on 2009-03-30
> **drs305 said:**
> If you don't have a separate /home partition and elect to do a clean install you will be spending time recreating your old settings. If you do an online upgrade you may have problems (though I haven't experienced them).

Here's the middle ground. From the livecd or systemrescuecd, use *partimage* to make a copy of your system partition. I'd say 'exact copy' but partimage doesn't include free space. Then run the online update. If it works, fine. If it doesn't, you can restore  your old system or do a clean install. 

Here's a good link for using Partimage:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

Thanks for that information!

---

### Post by Therion on 2009-03-30
> **cptrohn said:**
> Not having to re-install everything does make it sound tempting to at least give it a try.... I mean what is the worst that could happen?  That I would just have to re-install from a live CD if things went wrong?  Or is there the risk of damaging hardware too?
Oh no, there's no risk of damaging your hardware.  Worst case scenario is, yeah, a bad install and you wind up doing a clean install on top of it.  

Thing is, doing a dist-upgrade can take a looooong time and, potentially, leave you with a system that "works" but is full of weird quirks and what not that test the limits of your sanity since you now don't know if all this weirdness is due to doing a dist-upgrade, or if it's the distro itself...  So you wind up running around in circles like a chicken with it's head cut off trying to fix this stuff that really can't BE fixed and then, finally, in a colossal fit of rage and supreme human torment you wind up killing your entire family *and* the new couple next door that just moved in. Ugh!  Who needs all that?  Just do a clean install.

---

### Post by cptrohn on 2009-03-30
> **Therion said:**
> Oh no, there's no risk of damaging your hardware.  Worst case scenario is, yeah, a bad install and you wind up doing a clean install on top of it.  

Thing is, doing a dist-upgrade can take a looooong time and, potentially, leave you with a system that "works" but is full of weird quirks and what not that test the limits of your sanity since you now don't know if all this weirdness is due to doing a dist-upgrade, or if it's the distro itself...  So you wind up running around in circles like a chicken with it's head cut off trying to fix this stuff that really can't BE fixed and then, finally, in a colossal fit of rage and supreme human torment you wind up killing your entire family *and* the new couple next door that just moved in. Ugh!  Who needs all that?  Just do a clean install.

:lolflag:

Well... I guess I could do that for the new neighbors sake.:lolflag:

---

### Post by cptrohn on 2009-03-30
BUT  just suppose I don't really care much for my new nosy, loud neighbors anyway..........;p

Would this be the proper procedure to give it a try?
[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu)

---

### Post by Therion on 2009-03-30
> **cptrohn said:**
> BUT just suppose I don't really care much for my new nosy, loud neighbors anyway...
Well I'm not saying that dist-upgrade will turn you into a raging homicidal maniac, oh no.  Faaaar be it from ME to say something like THAT... But I'm not saying it *won't* either.  I think the question you should be asking yourself is... "Do I feel lucky?"  Well, DO you?  Bear in mind this IS Jaunty Jackalope we're discussing here.  A disto so powerful it could blow your head clean off...

> **cptrohn said:**
> Would this be the proper procedure to give it a try?
Sure.  What the h-ll, right?  Just be sure to use an Ubuntu Alternate install CD unless you're ACTUALLY one of.. of.. well you know... a KDE <shiver> user.

---

### Post by ghindo on 2009-03-30
> **cptrohn said:**
> BUT  just suppose I don't really care much for my new nosy, loud neighbors anyway..........;p

Would this be the proper procedure to give it a try?
[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu)Yes, if you're using Kubuntu, then that's the proper way to do a dist-upgrade (as opposed to a fresh install).

---

### Post by cptrohn on 2009-03-30
> **Therion said:**
> Well I'm not saying that dist-upgrade will turn you into a raging homicidal maniac, oh no.  Faaaar be it from ME to say something like THAT... But I'm not saying it *won't* either.  I think the question you should be asking yourself is... "Do I feel lucky?"  Well, DO you?  Bear in mind this IS Jaunty Jackalope we're discussing here.  A disto so powerful it could blow your head clean off...


Sure.  What the h-ll, right?  Just be sure to use an Ubuntu Alternate install CD unless you're ACTUALLY one of.. of.. well you know... a KDE <shiver> user.

Yeah, I like KDE...



You guys might want to say a little prayer for the neighbors tonight.:)

---

