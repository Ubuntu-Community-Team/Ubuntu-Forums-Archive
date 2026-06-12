---
title: "Lucid 10.04 grub problem"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ex-wirecutter on 2010-04-24
I have just tried to install Lucid 10.04 AMD 64 dual boot with Windows 7 64bit  using the side by side option choose at startup .
I checked the CD for errors and ran it as a live no install to see if it worked , all o.k. I then clicked on install and all appeared to go as normal. Until the post installation restart then I got " error no such partition " and " grub rescue " . So now I can't use Windows either !
I have tried using the repair disk for Windows but cant get past the grub error. Suggestions would be welcome as I have now had to drag an old PC out of retirement to write this .

---

### Post by kansasnoob on 2010-04-24
Boot the Live CD choosing "try without changes" and from the live desktop run the Boot Info Script and post the results as explained here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ex-wirecutter on 2010-04-24
Thanks for the reply , this may take a while as I will have to transfer monitor/keyboard etc. back to the faulty PC then copy the results and then set up this standby PC again .

---

### Post by kansasnoob on 2010-04-24
> **ex-wirecutter said:**
> Thanks for the reply , this may take a while as I will have to transfer monitor/keyboard etc. back to the faulty PC then copy the results and then set up this standby PC again .

Can't you just keep running the Live Desktop from the "sick" computer?

That is, actually post the results from the Live Desktop. It's going to be very slow and painful otherwise :)

I realize that the Live Desktop is slower than an actual installed OS but there is a strong chance that we'll need to pull up more info from the sick machine.

---

### Post by ex-wirecutter on 2010-04-24
As requested am now using the PC  with the faulty grub from the live CD , but having downloaded boot info script , when I use the command as per the instructions copied and pasted from the download , and viewed in gedit ,I get "no such file". When I do a search for it I get " not found" .
If this is going to take up a lot of your time I will just reinstall Windows and put it down as a dead loss , perhaps wait for the final release .

---

### Post by kansasnoob on 2010-04-24
Look in the Downloads folder.

Edit: I must run out to the pharmacy, I'll be back shortly.

---

### Post by ex-wirecutter on 2010-04-24
O.K. Thanks for trying , Downloads is empty , so I guess it's gone , never mind seems from this forum quite a few people are having grub problems so will just have to wait for the final release . All my Windows files were backed up to an external drive so no loss . Thanks again for your time . Please leave it at that.

---

### Post by QLee on 2010-04-24
I remember seeing this on launchpad. I haven't investigated it but the error message suggests it might be related.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/440587](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/440587)

There may be other launchpad reports, I didn't search.

---

### Post by ex-wirecutter on 2010-04-24
Thanks QLee , glad I am not alone.
off now.

---

### Post by oldfred on 2010-04-24
A lot of the initial bugs with grub2 have work arounds or quick fixes. Meierfra documented many of them here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

When you ran the boot info script it should have said where it saved results.txt. Usually desktop or documents.

---

### Post by kansasnoob on 2010-04-24
Beware, total rant ahead :)

I see the OP already said, "off now", so this is just targeted at the "choir" I guess, but consider a few things:

1) People continually rant about how buggy a release is. Yet the same people seem to have no patience in helping to troubleshoot what went wrong!

In this case the OP is perfectly willing to spend a considerable amount of time to reinstall Windows and restore a backup, **[COLOR="Red"]but NO time[/COLOR]** to troubleshoot what went wrong!

2) Without troubleshooting how can we be sure if this was due to a bug or operator error? IMO it's never good to resize Win7 or Vista with anything but their own partitioning tools as it appears the OP did!

I personally wish that if ubiquity/parted "sees" a Win7 or Vista OS it would just stop with that type of message :) Something like:

**It's best to resize Win7 or Vista with it's own partitioning tools. Click on quit to use the Win tools now or click on cancel to allow Ubuntu to repartition.**

3) We continually see complaints about the "devs"! One was so bold as to suggest the devs work all weekends for several weeks to fix all bugs! What an incredible crock!!!!!!!!!!!!!

The devs work very, very hard! But they can only work with the info put in front of them. Good bug filing and follow up on those bugs is essential.

4) This is open source! Quite simply you're either part of the solution or you're part of the problem! Which you choose to be is up to you :)

End rant.

---

### Post by ex-wirecutter on 2010-04-24
Have just come back to say sorry if I appear to have left this in the air but I was unable to help as I am not an expert , just an enthusiast . Having noted that this bug was reported to launchpad , I felt there was nothing I could do.

---

### Post by oldfred on 2010-04-24
Post the script, it is there somewhere if you ran it. Then we may be able to tell what the problem is.

And look at the link I gave in #9 as it more than likely has a fix for you.

Actually with Karmic and grub2 I had the least number of problems installing to two systems (essentially none) than all the installs and upgrades for the last 3 years. Actually after Karmic, I expected no issue with Lucid but it requires a video mode setting to get into it.

Also I think found something in the script that grub 1.98 does not display the correct drive. Lucid installed to sdc7 and grub1.98 to sda. My results.txt says the grub2 in sda boots partition 7 in the same drive. There is no partition 7 in sda and it boots ok to sdc7.

---

### Post by ex-wirecutter on 2010-04-24
I'm beginning to wish I hadn't posted this query , or at least not on this particular forum as most of what people are saying is beyond me , but when I asked an earlier Lucid related question in absolute begginers , it was moved to here by a moderator , so I assumed this was the place. Anyway , as mentioned in an earlier post I never got boot info to work , no doubt due to my inexperience terminal was unable to find the command . So could we please leave it there gentlemen ?
Thank you.
Furthermore how was I to know gparted couldn't handle a Windows 7 partition ?
Once again , thank you.

---

### Post by QLee on 2010-04-24
[QUOTE=ex-wirecutter]I'm beginning to wish I hadn't posted this query , or at least not on this particular forum as most of what people are saying is beyond me , but when I asked an earlier Lucid related question in absolute begginers , it was moved to here by a moderator , so I assumed this was the place. Anyway , as mentioned in an earlier post I never got boot info to work , no doubt due to my inexperience terminal was unable to find the command . So could we please leave it there gentlemen ?
Thank you.
Furthermore how was I to know gparted couldn't handle a Windows 7 partition ?
Once again , thank you.[/QUOTE]

As far as I can tell, you didn't do anything wrong. As a matter of fact, I think you did things correctly, you tried the unreleased software and then realised that at your current stage of knowledge and experience you would wait for release.

I don't think kansasnoob's rant (which was identified as such) was directed at you specifically, just one of the artifacts of the frustrations we all feel from time to time. I'm sure you'll understand if you think about it how frustrating it can be to be constantly working on problems, with a real desire to help someone and then that person loses interest. There are lots of places where the advice to use Lucid (at this point) for testing and discussion only, yet a lot of effort is spent in this sub forum helping people who should have never tried. Please don't take kansasnoob's comments to heart personally, see them as a chance for others to learn. My experience is that kansasnoob has useful advice and skill. And we all "burn out" from time-to-time.

---

### Post by kansasnoob on 2010-04-24
> **QLee said:**
> As far as I can tell, you didn't do anything wrong. As a matter of fact, I think you did things correctly, you tried the unreleased software and then realised that at your current stage of knowledge and experience you would wait for release.

I don't think kansasnoob's rant (which was identified as such) was directed at you specifically, just one of the artifacts of the frustrations we all feel from time to time. I'm sure you'll understand if you think about it how frustrating it can be to be constantly working on problems, with a real desire to help someone and then that person loses interest. There are lots of places where the advice to use Lucid (at this point) for testing and discussion only, yet a lot of effort is spent in this sub forum helping people who should have never tried. Please don't take kansasnoob's comments to heart personally, see them as a chance for others to learn. My experience is that kansasnoob has useful advice and skill. And we all "burn out" from time-to-time.

Qlee, you're partly right but also not.

Consider this: the OP is now whining, "I'm beginning to wish I hadn't posted this query....".

But their second follow-up post was, "If this is going to take up a lot of your time I will just reinstall Windows and put it down as a dead loss , perhaps wait for the final release".

That does not indicate a lack of knowledge, but rather a lack of cooperation! And upon not being able to run the Boot Info Script properly the response was, "never mind seems from this forum quite a few people are having grub problems so will just have to wait for the final release . All my Windows files were backed up to an external drive so no loss . Thanks again for your time . **Please leave it at that.**"

My comprehension skills are just fine! My vision less so, and my hearing even less yet, but I can read quite well.

---

