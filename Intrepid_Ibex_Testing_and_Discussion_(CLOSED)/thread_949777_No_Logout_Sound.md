---
title: "No Logout Sound"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kow on 2008-10-16
This problem has existed since we switched to Pulse Audio in hardy and from what I can tell has not been fixed yet (and is not noted in any of the release notes.) The logout sound never plays, even if one is set. It plays fine from System -> Preferences -> Sound. Not a major issue but it seems like one that should be easy to fix. I'm guessing it is the result of a race condition.... the sound system being shut down before GNOME wants to play the logout audio clip.

---

### Post by BlueSkyNIS on 2008-10-16
Yea, I second that, my thoughts exactly!

---

### Post by spsf on 2008-10-17
Same problem here, even with latest daily builds
Also the event sounds (windows maximize/minimize/button click/etc...) wont work either
It's not my hardware problem, because I tried mandriva 2009 and all sounds do work fine.
Hope devs get this fixed before the final release

---

### Post by go7Ul1ai on 2008-10-17
+1

---

### Post by shane19174 on 2008-10-17
The general lack of event sounds mentioned by spsf is a known bug: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507"). It's connected with libcanberra, for which there are lots of bugs at the moment: [https://bugs.launchpad.net/ubuntu/+source/libcanberra]("https://bugs.launchpad.net/ubuntu/+source/libcanberra").

---

### Post by spsf on 2008-10-17
> **shane19174 said:**
> The general lack of event sounds mentioned by spsf is a known bug: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507"). It's connected with libcanberra, for which there are lots of bugs at the moment: [https://bugs.launchpad.net/ubuntu/+source/libcanberra]("https://bugs.launchpad.net/ubuntu/+source/libcanberra").

Thanks for replying!
Hope it gets fixed, because comparing the events sounds behavior between Ubuntu 8.1 and Mandriva 2009 is like Win 3.11 to WinXP :(
I think this sound bug is very important to this new release, because its a new feature introduced in Gnome 2.24; However I think it wont get fixed before the final release, its too close, only 13 days.... and this bug is present since day 1.

---

### Post by shane19174 on 2008-10-17
Yes, I agree that it's important in terms of getting people to adopt Ubuntu in favor of other OS's. That is, it may just be a "cosmetic" issue for already devoted users, but such "little things" are quite important when it comes to first impressions. But you never know, maybe it'll get fixed in time (?).
Shane

---

### Post by FuturePilot on 2008-10-17
This is actually not a libcanberra bug. The logout sound has been broken since Gutsy.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245")

Unfortunately it doesn't look like it will be fixed any time soon.:(

---

### Post by shane19174 on 2008-10-17
I see, thanks for the correction.

---

### Post by spsf on 2008-10-17
> **FuturePilot said:**
> This is actually not a libcanberra bug. The logout sound has been broken since Gutsy.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245")

Unfortunately it doesn't look like it will be fixed any time soon.:(

It means 2+ years?
How come? Looks like it will never be fixed...

---

### Post by crjackson on 2008-10-17
> **FuturePilot said:**
> This is actually not a libcanberra bug. The logout sound has been broken since Gutsy.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245")

Unfortunately it doesn't look like it will be fixed any time soon.:(

Some bugs just seem to become a tradition. I too noticed this when moving from 7.04. I really hoped things would be better with 8.04, but here we are at 8.10 and it's still hanging around.

---

### Post by exploder on 2008-10-17
Here is a work around to get the log off and shutdown sounds.

[http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858)

This fix works fine in Hardy and it should work in Intrepid as well.

---

### Post by yosemite610 on 2008-10-17
My idiot-meter is pegging out on this one... I mean, if you don't have the ability to fix it, remove it (option to add/change login/logout sounds).

---

### Post by spsf on 2008-10-18
> **crjackson said:**
> Some bugs just seem to become a tradition. I too noticed this when moving from 7.04. I really hoped things would be better with 8.04, but here we are at 8.10 and it's still hanging around.
I just dont understand why there are only few complaints about these problems.
I used Kubuntu before with no problems with sounds so far, now I decided to move to Gnome because of the horrible KDE4 interface and the new sound events in Gnome 2.24.
My first try with gnome was Mandriva 2009 RC and all sounds did work fine, and still work in 2009 final.
I'd like to stick to ubuntu family, but I cant live without those bells and whistles, lol!
I reported this problem in launchpad.net, but it seems no one in the development team cares....
I still have hope! May some dedicated devs will listen to us!
Regards

---

### Post by Kow on 2008-10-18
> **crjackson said:**
> Some bugs just seem to become a tradition. I too noticed this when moving from 7.04. I really hoped things would be better with 8.04, but here we are at 8.10 and it's still hanging around.

And that is the only reason I brought this up. Bugs are not supposed to be a tradition. If the logout sound is supposed to play then it should play... If Ubuntu wants to be professional in it's market then bugs like this cannot simply be thrown in the trash and forgotten about. Even the most novice user will be able to figure out something is wrong when a logout clip is selected in the Sound app, plays fine... but doesn't play on logout.

---

### Post by shane19174 on 2008-10-18
I agree with the sentiments here, and though I don't want to change the topic, I'd just like to ask if there's anyone out there who has the rest (or any of the other) system events. I have the drumroll at the GDM login screen, then the default Ubuntu login sound, but that's all. I know I'm not alone, as all the libcanberra bugs attest, but I just wanted to know if EVERYONE is affected or only a lot of people.

Thanks,
Shane

---

### Post by hartl_vienna on 2008-10-18
@shane19174: I have the same problem on my Dell XPS M1330. 

I hope this bug will be fixed, because it gives a very unprofessional impression for new users if such a trivial thing like the system-sounds doesn't work.

---

### Post by spsf on 2008-10-18
> **shane19174 said:**
> I agree with the sentiments here, and though I don't want to change the topic, I'd just like to ask if there's anyone out there who has the rest (or any of the other) system events. I have the drumroll at the GDM login screen, then the default Ubuntu login sound, but that's all. I know I'm not alone, as all the libcanberra bugs attest, but I just wanted to know if EVERYONE is affected or only a lot of people.

Thanks,
Shane

Exactly the same problem :(
Maybe change the topic to "No Logout and Events Sounds" ?? Just an opinion...

---

### Post by yosemite610 on 2008-10-18
I went to [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245) and selected the "This bug affects me too" option at the top of the page.

I have no idea if this is effective...

---

### Post by spsf on 2008-10-18
> **yosemite610 said:**
> I went to [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/229245) and selected the "This bug affects me too" option at the top of the page.

I have no idea if this is effective...
I filled a new bug with links related to this post and other bugs already posted.

[https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549)

Apparently nobody reads those bugs except the users affected :(

---

### Post by yosemite610 on 2008-10-19
> **spsf said:**
> I filled a new bug with links related to this post and other bugs already posted.

[https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549)

Apparently nobody reads those bugs except the users affected :(

Selected the "This bug affects me too" option for this one as well, and it appeared to change the status to 'Confirmed'.

---

### Post by exploder on 2008-10-19
I added to the bug report. Everything else in Intrepid is looking pretty good, having the system sounds working again would add polish to the final release and the sounds have not worked for a long time.

---

### Post by spsf on 2008-10-19
Thanks all of you trying to get the attention of development team
At launchpad [https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549) , apparently one of the devs marked as a duplicated of another bug, but I think he's mistaken.
Please do login into launchpad and report the bug as NOT duplicated, maybe they can focus on this real problem
Thanks
Regards
Sergio

---

### Post by Nerd_bloke on 2008-10-20
There are a few bugs in this general area... the one that looks like it has a possible solution is

[https://bugs.launchpad.net/bugs/273507](https://bugs.launchpad.net/bugs/273507)

But I'm not sure if Canberra can be updated for Intrepid due to its dependencies.

---

### Post by spsf on 2008-10-21
> **Nerd_bloke said:**
> There are a few bugs in this general area... the one that looks like it has a possible solution is

[https://bugs.launchpad.net/bugs/273507](https://bugs.launchpad.net/bugs/273507)

But I'm not sure if Canberra can be updated for Intrepid due to its dependencies.

Thanks for the libcanberra comment
I found this page: [https://launchpad.net/~gkulyk/+archive](https://launchpad.net/~gkulyk/+archive) with the latest libcanberra 0.10 (the one used in intrepid is outdated 0.6).
I included the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reloaded. Immediately the new 0.10 showed up as an upgrade, marked all upgrades, and rebooted.
WOW!! All the "Allerts and Sound Effects" working 100%!!
Just had to manually select some windows minimize/maximize sounds and everything is ok now!
Just one minor problem, the logout sound still not working, but I think it's related to another bug.
Hope it helps!
Regards
Sergio
ps. I'd like to say thank you to Gert Kulyk ([https://launchpad.net/~gkulyk](https://launchpad.net/~gkulyk)) for his excellent work with canberra, hope the devs include this upgrade soon in intrepid.
ps2. Also posted this solution to the bug a i filled earlier ([https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549) and also here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/274124](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/274124))

---

### Post by shane19174 on 2008-10-21
> Thanks for the libcanberra comment
I found this page: [https://launchpad.net/~gkulyk/+archive](https://launchpad.net/~gkulyk/+archive) with the latest libcanberra 0.10 (the one used in intrepid is outdated 0.6).
I included the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reloaded. Immediately the new 0.10 showed up as an upgrade, marked all upgrades, and rebooted.
WOW!! All the "Allerts and Sound Effects" working 100%!!
Just had to manually select some windows minimize/maximize sounds and everything is ok now!
Just one minor problem, the logout sound still not working, but I think it's related to another bug.
Hope it helps!
Regards
Sergio
ps. I'd like to say thank you to Gert Kulyk ([https://launchpad.net/~gkulyk](https://launchpad.net/~gkulyk)) for his excellent work with canberra, hope the devs include this upgrade soon in intrepid.
ps2. Also posted this solution to the bug a i filled earlier ([https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549) and also here: [https://bugs.launchpad.net/ubuntu/+s...io/+bug/274124](https://bugs.launchpad.net/ubuntu/+s...io/+bug/274124))

Sergio, thanks! It worked for me. Now I would be interested in trying out some other sounds, though. Does anyone know where you can get the default Gnome sound theme (if there is such a thing)? A little tired of drums and such (though it's nice to have sound at all...)

Thanks again,
Shane

---

### Post by FuturePilot on 2008-10-21
> **spsf said:**
> Thanks for the libcanberra comment
I found this page: [https://launchpad.net/~gkulyk/+archive](https://launchpad.net/~gkulyk/+archive) with the latest libcanberra 0.10 (the one used in intrepid is outdated 0.6).
I included the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reloaded. Immediately the new 0.10 showed up as an upgrade, marked all upgrades, and rebooted.
WOW!! All the "Allerts and Sound Effects" working 100%!!
Just had to manually select some windows minimize/maximize sounds and everything is ok now!
Just one minor problem, the logout sound still not working, but I think it's related to another bug.
Hope it helps!
Regards
Sergio
ps. I'd like to say thank you to Gert Kulyk ([https://launchpad.net/~gkulyk](https://launchpad.net/~gkulyk)) for his excellent work with canberra, hope the devs include this upgrade soon in intrepid.
ps2. Also posted this solution to the bug a i filled earlier ([https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549) and also here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/274124](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/274124))

Awesome! All the system sounds are working now, except the logout sound, but that is a separate issue from libcanberra. The only thing that still doesn't work is the Alert sound. It should play a nice subtle "ding" instead I get a very harsh system beep. :(

---

### Post by shane19174 on 2008-10-21
So if this fix works so smoothly (which it at least appears to do), then why isn't it incorporated into Ubuntu yet? Or is there a risk of something else breaking?
Shane

---

### Post by spsf on 2008-10-21
I'm glad I helped you guys!
I'm also happy because I can stay with Ubuntu instead of moving to another distro

> **shane19174 said:**
> So if this fix works so smoothly (which it at least appears to do), then why isn't it incorporated into Ubuntu yet? Or is there a risk of something else breaking?
Shane

Yes Shane, don't know either, as I wrote before, apparently the development/release team don't care for cosmetic features like sound :( 
If you check my posts at launchpad there are no answers at all :(
Looks like they don't even read the posts at launchpad...
Thank god Gert Kulyk released this updated libcanberra!
Lets hope some developer reads this and the fix gets incorporated into RC or final 8.10, this way we can have a better user experience out of the box!
Regards
Sergio

---

### Post by exploder on 2008-10-21
I also hope this fix makes it into Intrepid.

---

### Post by spsf on 2008-10-22
> **exploder said:**
> I also hope this fix makes it into Intrepid.
Lets pray! :lolflag:

---

### Post by Robertjm on 2008-10-22
When you read the Gutsy/Hardy bug someone quoted earlier, its status is marked as Low "WON'T FIX." Is it won't fix because it was reported in Gutsy and Hardy? 

If it's not fix will it be addressed again short of a new bug being reported?

---

### Post by spsf on 2008-10-22
> **Robertjm said:**
> When you read the Gutsy/Hardy bug someone quoted earlier, its status is marked as Low "WON'T FIX." Is it won't fix because it was reported in Gutsy and Hardy? 

If it's not fix will it be addressed again short of a new bug being reported?
Don't know, I'm no expert, just an ordinary user!:)

---

### Post by yosemite610 on 2008-10-24
After the latest update (oct24) my gdm-login bell sounds and I'm actually getting login sound effects (I have enabled the compiz 'logo' and it seems perfectly timed to the login sound now ;')

Fixed for anyone else?

---

### Post by FuturePilot on 2008-10-24
> **yosemite610 said:**
> After the latest update (oct24) my gdm-login bell sounds and I'm actually getting login sound effects (I have enabled the compiz 'logo' and it seems perfectly timed to the login sound now ;')

Fixed for anyone else?

No, the login sound has always worked for me. The problem here is the **logout** sound that has been broken for a long time and other related system sounds that don't work because of a libcanberra bug.

---

