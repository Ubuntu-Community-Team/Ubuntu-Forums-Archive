---
title: "Shut down during upgrade bricked pc"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by toolmania1 on 2011-12-05
I know, I made a bad mistake, a rookie one even.  But, I need to move on from it and need help.

During the upgrade from Ubuntu 10 to 11, I shut down the pc.  ( I know, it was very dumb ).

Now, I cannot start Ubuntu.  I cannot reinstall Ubuntu.  I cannot wipe the pc using Darik's Boot and Nuke.  I put these cds in and they start for a few seconds.  Then, the pc just shuts down.  I had no problems like this before I made this major error.

Any ideas on how I can save my pc?  I don't care about saving anything from Ubuntu.  I am ok with a clean install.  I just want to wipe it back to square one and cannot even do that.  

Also, I get no errors on the screen.  The pc just reboots.

---

### Post by kio_http on 2011-12-05
> **toolmania1 said:**
> I know, I made a bad mistake, a rookie one even.  But, I need to move on from it and need help.

During the upgrade from Ubuntu 10 to 11, I shut down the pc.  ( I know, it was very dumb ).

Now, I cannot start Ubuntu.  I cannot reinstall Ubuntu.  I cannot wipe the pc using Darik's Boot and Nuke.  I put these cds in and they start for a few seconds.  Then, the pc just shuts down.  I had no problems like this before I made this major error.

Any ideas on how I can save my pc?  I don't care about saving anything from Ubuntu.  I am ok with a clean install.  I just want to wipe it back to square one and cannot even do that.  

Also, I get no errors on the screen.  The pc just reboots.

Hi try booting an Ubuntu live cd. Open Nautilus from there to backup files from the system. Then run the installer and under manual partitioning select the partition where Ubuntu was installed, format it and mount it as / then proceed.

---

### Post by toolmania1 on 2011-12-05
I did try a live Ubuntu cd also.  Same thing happened as the pc just shut down.  I will try again though.  Maybe I will have better luck.  I know, it doesn't make sense.  I should be able to run the Ultimate book disk that I also tried and wipe the pc or run the Ubuntu live cd like you said.

---

### Post by kio_http on 2011-12-05
> **toolmania1 said:**
> I did try a live Ubuntu cd also.  Same thing happened as the pc just shut down.  I will try again though.  Maybe I will have better luck.  I know, it doesn't make sense.  I should be able to run the Ultimate book disk that I also tried and wipe the pc or run the Ubuntu live cd like you said.

Sounds like a hardware issue to me. Enter BIOS setup and reset to defaults then boot. Also if the BIOS has a temperature monitor keep the PC on it there and keep an eye on the readings and check if it goes off.

---

### Post by toolmania1 on 2011-12-05
Ok, I will try that.

I do know for sure that the pc does shut down when it overheats since I have to put a fan by it.  But, we did that for a while with no issues.  I need to get a pc fan or two to put inside.  There is one in there, but it is not enough for some reason.

But, regardless, everything was fine until I made this bonehead move.  We had been using the pc, with the external fan blowing on it for half a year with Ubuntu on it no problem.  So, maybe if I just try again, something will work this time. 

:-)

Thanks for the ideas!

---

### Post by kio_http on 2011-12-05
> **toolmania1 said:**
> Ok, I will try that.

I do know for sure that the pc does shut down when it overheats since I have to put a fan by it.  But, we did that for a while with no issues.  I need to get a pc fan or two to put inside.  There is one in there, but it is not enough for some reason.

But, regardless, everything was fine until I made this bonehead move.  We had been using the pc, with the external fan blowing on it for half a year with Ubuntu on it no problem.  So, maybe if I just try again, something will work this time. 

:-)

Thanks for the ideas!

Seems like coincidence with such a FAN configuration, if the fan has become old it will slow down with time and someday stop (happened to my pentium 4) But the PC off from the mains for 15 minutes. Then try again. Note if you do manage to boot Ubuntu running
```
sudo apt-get install -f
```will resume the upgrade

---

### Post by Mark Phelps on 2011-12-05
If you had to use an external fan to cool your PC in order to get it to run under Ubuntu v10.x, it's very likely that you will NOT be able to get it to run under 11.10 -- because there have been lots of reports of PCs with that version overheating.

Your original thread was all within a half-hour or so -- not enough to let the PC cool down.

I would leave it alone overnight and see if it boots (cold) in the morning.  IF it does, then it's likely that 11.10 is too demanding for the PC.  In that case, I would reinstall the older (working) version and stick with that for a while.

---

### Post by abrahamarroyoitm on 2011-12-05
Hi, i need a little help about one similar problem, i was removing virtualbox and i turned off the computer, now i cannot remove it completely also cannot reinstall it haha =), what do i have to do?

Thanks for help

---

### Post by kio_http on 2011-12-06
> **Mark Phelps said:**
> If you had to use an external fan to cool your PC in order to get it to run under Ubuntu v10.x, it's very likely that you will NOT be able to get it to run under 11.10 -- because there have been lots of reports of PCs with that version overheating.

Your original thread was all within a half-hour or so -- not enough to let the PC cool down.

I would leave it alone overnight and see if it boots (cold) in the morning.  IF it does, then it's likely that 11.10 is too demanding for the PC.  In that case, I would reinstall the older (working) version and stick with that for a while.

If the CPU fan is working properly as Intel or AMD intends it too, even the most CPU intensive thing should never have to cause it to switch off. It should slow it down but never switch off because of software overload.

---

### Post by toolmania1 on 2011-12-09
I still have not tried to reinstall yet.  I will post the results of that soon.  But, I would like to note I did file a bug about being able to "Shut Down" Ubuntu in the middle of an upgrade.  If this will cause issues when trying to start Ubuntu back up, then the option should be taken away.  I know it is a very stupid thing I did, but, let's face it, we all have done something stupid along the way.  

However, in the grand scheme we cannot hold everyone's hand all the time either.  I know this.  I knew better then and know better now especially.  So, I reap the consequences now and I am sure I will have this figured out soon.  It just would be a nice feature to not allow anyone else to make the same mistake.  I will see what the developers come back with.

---

### Post by toolmania1 on 2011-12-10
Kio and Mark,

Thanks for the observation of the small amount of time between my posts and suggestions about it being hardware.  I tried some days later and was able to get Ubuntu 11 installed.  However, I ran into one more problem about the boot hanging at the battery prompt.

[http://ubuntuforums.org/archive/index.php/t-1741512.html](http://ubuntuforums.org/archive/index.php/t-1741512.html)

So, I am just going to put Ubuntu 10.10 back on.  

This is good news though!

---

### Post by toolmania1 on 2011-12-10
I have successfully installed Ubuntu 10.10 from a Ubuntu live dvd I made.  So, when I could not start the computer back up it was because of a heat issue.  

I also did not get the boot problem where Ubuntu 11 hung at the battery statment.

I am closing this thread.

---

