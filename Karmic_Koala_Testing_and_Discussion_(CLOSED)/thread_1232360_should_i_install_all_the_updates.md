---
title: "should i install all the updates???"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by super kim on 2009-08-05
i have just installed the karmic koala as i have been running it off of the live cd for a day now with no problems whatsoever, i can also report that the video card and sound card etc have all been set up automatically and they all work :)

However when i went to play an avi video with totem the dialogue comes up to tell me the required plug in is not installed. i chose not to search for plug ins since the video's were playing fine when i was booting from the live cd. instead i open my synaptic package manager to see if gstreamer was installed, and indeed it is installed however there is a funky lil star in the otherwise boring grey box. first time i've seen a star so i investigated and found that gstreamer is installed but has an update, there are others that appeared in my search for "gstrea" they also had the update icon.

i clicked on mark all updated and was a little surprised to see that there udates for nearly every thing installed, including the linux headers and drivers for my graphics card.

i decided to wait to see what you can suggest as i dont want to upgrade everything since i've only just installed ubuntu 9.10.

please help i am dying to watch this film, and i missed top gear at the weekend and i cant use the bbc i player yet :(

---

### Post by Bigtime_Scrub on 2009-08-05
Well if you're using Karmic I would expect that the updates would be coming in almost daily. I think it is beta software at this point Im not sure. If you are worried about breaking things, then just select the gstreamer plugin updates only. When the update notifier pops up with the list of all possible updates, just uncheck the ones you dont want and then update. You can always go back and get the rest of the updates later.

---

### Post by philinux on 2009-08-05
You do realise that Karmic K is at alpha three and is likely to suffer major breakage at some time. It's still in development.

However you need to click the links below for medibuntu and restrictedformats.

Karmic forum.
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by super kim on 2009-08-05
i know that karimic is in the alpha stage and have been told by everyone that it will break and not work...
however as i said before it ALL works (nearly) i am stuck with the dual display.

I will just update the packages as i need them to keep on the safe side, anyway i have an ingenious set up. my ubuntu is on its own little hdd, and i have another little drive with jaunty on it so if it all goes t*ts up then i have that to fall back on

oh yes i remember now the restricted formats i'll check that right away, then update gstreamer thanks peeps! :D

---

### Post by philinux on 2009-08-05
Thats my rig too. Jaunty on disk1 karmic on disk2.

On Karmic only I would use this. Never click yes to partial upgrade if you use update manager.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Watch out if it wants to remove a lot of stuff. If it does cancel it and wait.

---

### Post by super kim on 2009-08-05
```
sudo apt-get update && sudo apt-get dist-upgrade
```


but wont that be updating everything??? thats what i didn't want to do since it works right now and if i suddenly update everything at the same time how will i know what to change back if it goes wrong?

Why wont ubuntu (jaunty and karmic) see my tv? its a very nice tv and i have a svhs lead

---

### Post by philinux on 2009-08-05
> **super kim said:**
> ```
sudo apt-get update && sudo apt-get dist-upgrade
```


but wont that be updating everything??? thats what i didn't want to do since it works right now and if i suddenly update everything at the same time how will i know what to change back if it goes wrong?

Why wont ubuntu (jaunty and karmic) see my tv? its a very nice tv and i have a svhs lead

The whole point of running Karmic now is to test for bugs etc and therefore contribute to it's success. No point not doing all updates. Run Jaunty as your main system. Test Karmic. :D

---

### Post by super kim on 2009-08-05
> **philinux said:**
> The whole point of running Karmic now is to test for bugs etc and therefore contribute to it's success. No point not doing all updates. Run Jaunty as your main system. Test Karmic. :D

but like i said if i install everything how do i know what has gone wrong if it doesn't work anymore? to be honest i don't know how to file/report a bug properly and my point in installing karmic is that it works on my system better than jaunty, i was having trouble with this and that in jaunty but i've had no issue with karmic **yet**,

---

### Post by philinux on 2009-08-05
There are **loads of updates **nearly every day because it's a development version. Hard to be selective.

Filing bugs is real easy.
[http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)

---

### Post by QIII on 2009-08-05
I'd dist-upgrade.

The whole point of the testing cycle at this stage is to be sure that the entire package is behaving itself.

Keep in mind that even a dist-upgrade is not quite like a clean install, however.

---

### Post by bugritall on 2009-08-05
> **super kim said:**
> Why wont ubuntu (jaunty and karmic) see my tv? its a very nice tv and i have a svhs leadI have cloned my Jaunty installation to a new partition and upgraded it to Karmic. Karmic doesn't recognise my DVB-TV stick.

Furthermore, Flash got all messed up when I allowed Karmic to do an auto-update. I like to take a break and watch 4oD and iPlayer from time to time, so the mishap was rather annoying. Flash wouldn't uninstall so that I could reinstall and I finished up cloning and upgrading again, so beware. Remember the old adage *If it ain't broke, don't fix it!*

---

### Post by slakkie on 2009-08-05
Running an development version, in a beginners forum, asking wheter or not to update...

If you want stable run 8.04. If you want a bit more current, get 9.04. IMO this is asking for trouble..

---

### Post by bugritall on 2009-08-05
> **slakkie said:**
> Running an development version, in a beginners forum, asking wheter or not to update...

If you want stable run 8.04. If you want a bit more current, get 9.04. IMO this is asking for trouble..
Aw, c'mon, where's your sense of adventure? :D:D:D

---

### Post by slakkie on 2009-08-06
Haha, good one. Don't mind adventures, but somehow I see a thread coming, Ubuntu doesn't cut it for me, updates broke my system, please help!

I think a beginner should not try to play with experimental software (unless that experimental software supports something the user absolutely needs to have). But instead should try to understand the OS and then wonder off in the depths of that OS. Same thing I will not install experimental OpenSolaris images. I want to play with something stable before going alpha testing.

---

### Post by super kim on 2009-08-06
well i have a hard drive with jaunty, a hard drive with karmic and i keep all my personal files on removable hard drives so the trouble i could get into is limited. i am just excited with my recent love of ubuntu. yes i am certainly a beginner in the wonderful world of linux hence my forum choices, i have got years of computer breaking and then having to rebuild/repair experience in windows, and i'm confident that i can continue this pattern with ubuntu.
it might seem silly to you but it's only when you break something that you learn how it really works.

---

### Post by slakkie on 2009-08-06
That I agree with. But plenty to break on a normal system.. :P

At least you asking question. Best of luck with Karmic and Jaunty!

---

