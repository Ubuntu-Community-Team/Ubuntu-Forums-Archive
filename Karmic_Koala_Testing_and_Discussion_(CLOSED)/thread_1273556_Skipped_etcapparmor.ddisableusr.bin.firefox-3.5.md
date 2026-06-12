---
title: "Skipped: etc/apparmor.d/disable/usr.bin.firefox-3.5"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-09-23
Anyone else getting this message at boot?
```
Skipped: etc/apparmor.d/disable/usr.bin.firefox-3.5
```

---

### Post by ilovebrownies on 2009-09-23
I get this too.

---

### Post by Squonk07 on 2009-09-23
Here, too. It doesn't seem to affect my boot process, other than wasting time.

---

### Post by celticbhoy on 2009-09-23
+1 for me to.

---

### Post by Longinus00 on 2009-09-23
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/435285](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/435285)

---

### Post by novafluxx on 2009-09-23
I get it too, its known already. I'm hoping to see no boot-strings at all after Karmic is released, unless I specify I want to see them. So far XSplash is excellent

---

### Post by NCLI on 2009-09-23
I hope this isn't anything dangerous :(

---

### Post by oasick on 2009-09-23
me too...

---

### Post by stevetxt on 2009-09-23
I get this one too, followed by fsck which says my partitions are clean and then a few more messages before xsplash starts.  Can anyone tell me where to see a log of these messages?  I also get some messages on shutdown.

---

### Post by novafluxx on 2009-09-23
> **stevetxt said:**
> I get this one too, followed by fsck which says my partitions are clean and then a few more messages before xsplash starts.  Can anyone tell me where to see a log of these messages?  I also get some messages on shutdown.

Same issues here...it happens on my laptop, but not on the virtualbox install.

I'm getting boot messages before XSplash comes up, also on shutdown I don't see USplash, only the console then it seems to hang and then shutoff.

Virtualbox shows me USplash on shutdown.

Strange issues...and if I knew where to go to view logs I could post them here as well for somone to analyze and tell me if all is well

---

### Post by flamefury on 2009-09-23
I've had this too, and a the fsck thing happened once. After it ran and I rebooted, the boot process went fine.

Still, wonder what this thing does...

---

### Post by solitaire on 2009-09-24
I get the same apparmor error.

It's just annoying ^_^ lol

---

### Post by Slug71 on 2009-09-24
+1

---

### Post by joey-elijah on 2009-09-24
Call me unoriginal, but i get it too!

It's *slightly* annoying because i really want to time by boot speed and compare it to Jaunty and Ibex just to see realworld results on my hardware.... but i get bored waiting for all of the 'text' to scroll and proceed to XSplash.

---

### Post by alvevind on 2009-09-24
I'm also getting this.

The system boots up but then after a while just stops with a black screen. If I press a button I get the terminal with the text 
"Skipped: etc/apparmor.d/disable/usr.bin.firefox-3.5" 
and a termial login prompt.

I login to a commandline prompt and (based on advice from a previous tread) I write 
"sudo restart gdm". 

This gives me the graphical login screen and from there everything proceeds as normal.

I have all the latest updates and have restarted the computer several times but I can not get to the graphical login window without doing the terminal login and gdm restart first.

Is this what everyone must currently cope with or does it only happen to certain users?

(I have a rather old PC btw)

---

### Post by orc_dragoon on 2009-09-24
fsck happens on and off, but the apparmor happens all the time. Doesnt harm anything, but it does slow down the proccess. This happens on my eeepc.

---

### Post by Amaranth on 2009-09-24
It's not actually slowing anything down telling you it skipped it. It's skipping it because enabling it slowed things down.

---

### Post by zoomy942 on 2009-09-24
im getting it too

---

### Post by vicky_love on 2009-09-25
+1 from me too
getting this msg at every boot.

---

### Post by ricsi-pontaz on 2009-09-25
+1

Is somebody know how can we solve this?

---

### Post by Longinus00 on 2009-09-25
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/435285](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/435285)

Bug report now says that there's a fix out so it should show up in the near future.

---

### Post by stevetxt on 2009-09-25
I still get this message after having done the update with the version of apparmor that should contain the fix.  Maybe there's something I need to do in addition.

---

### Post by zoff_ita on 2009-09-25
> **stevetxt said:**
> I still get this message after having done the update with the version of apparmor that should contain the fix.  Maybe there's something I need to do in addition.

The same for me...

---

### Post by Longinus00 on 2009-09-25
Dang, you guys are right.

---

### Post by !nkubus on 2009-09-25
Me to I still get this message as well as a pci thing before plus the fsk line also.

---

### Post by WiFi Ed on 2009-09-25
> **!nkubus said:**
> Me to I still get this message as well as a pci thing before plus the fsk line also.

Same for me.

apparmor firefox message, something about pci and pci e, and the fsck messages.:confused:

---

### Post by vfontanela on 2009-09-26
+1

---

### Post by DougieFresh4U on 2009-09-26
Hadn't updated/upgraded in a couple of days here on my 32 bit. Had about 283 updates this evening and rebooted twice and the **etc/apparmor.d/disable/usr.bin.firefox-3.5** was still present.
All is working as should be, for now :)

---

### Post by novafluxx on 2009-09-26
> **DougieFresh4U said:**
> Hadn't updated/upgraded in a couple of days here on my 32 bit. Had about 283 updates this evening and rebooted twice and the **etc/apparmor.d/disable/usr.bin.firefox-3.5** was still present.
All is working as should be, for now :)

Just thought the general idea was to have NO boot text on startup under normal circumstances. So far this isn't the case. It happens on my Dell Inspiron 1318 and in Virtual Box.

I also get dropped to terminal on shutdown, instead of seeing usplash or anything fancy.

I'm going to do a clean install once beta comes out. I'll see how it goes then!

---

### Post by Squonk07 on 2009-09-26
> **novafluxx said:**
> 

I'm going to do a clean install once beta comes out. I'll see how it goes then!

I always do this on principle. It's good to start afresh, and since I keep my personal files on a separate drive (or partition in this case) it's just a question of reinstalling the OS and applications.

+1 (still) on the weird apparmor string and fsck. It even had the nerve one time to tell me that it hadn't fsck'ed in twenty boots, when it has done so every boot.

At least everything still works fine. I'll sit back and let the devs sort this one out; I'm more than confident they'll get this settled in time for the beta.

---

### Post by novafluxx on 2009-09-26
> **Squonk07 said:**
> I always do this on principle. It's good to start afresh, and since I keep my personal files on a separate drive (or partition in this case) it's just a question of reinstalling the OS and applications.

+1 (still) on the weird apparmor string and fsck. It even had the nerve one time to tell me that it hadn't fsck'ed in twenty boots, when it has done so every boot.

At least everything still works fine. I'll sit back and let the devs sort this one out; I'm more than confident they'll get this settled in time for the beta.

Mine's been asking me to run on startup but I start the computer on battery so it skips it lol

It doesn't actually do the check every boot, it only runs to check how long its been since a check was performed, and then after a set amount, it will run the check. So while fsck does run, it doesn't actually check on every boot (unless you're an exception, and encountering a bug!)

---

### Post by Squonk07 on 2009-09-26
> **novafluxx said:**
> Mine's been asking me to run on startup but I start the computer on battery so it skips it lol

It doesn't actually do the check every boot, it only runs to check how long its been since a check was performed, and then after a set amount, it will run the check. So while fsck does run, it doesn't actually check on every boot (unless you're an exception, and encountering a bug!)

I think you're right about that. The text flashes by so fast that I couldn't really tell what it was doing. I just assumed since it showed progress percentages to the right that it was conducting some sort of check.

Thanks for the response. :)

---

### Post by qwerty800 on 2009-09-27
+1

Since this is more of a warning than an error, the computer should just skip it, and not display all of this text.

I still have hope than this will probably be resolved during the beta.

---

### Post by thiebaude on 2009-09-27
+1 and I get the firmware bug error thing also.

---

### Post by FrancoNero on 2009-09-27
yeah same here +1

unfortunate, wanted to show friends the new ubuntu, but as long as there's text during boot-up, that's not an option :D

---

### Post by W2IBC on 2009-09-27
got the firefox issue.

also get the disk check thing also. allways says its clean

---

### Post by Longinus00 on 2009-09-27
This seems like stuff that used to be always hidden by the usplash. Maybe they really should just throw up the usplash image while waiting for xsplash to start.

---

### Post by dudude on 2009-09-28
The current status of the bug [here]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/435285") has been changed to "Fix Committed," so hopefully this means that this bug will be really for real fixed when the update arrives.

---

### Post by stevetxt on 2009-09-28
I tried it with the apparmor that just came as an update.  That gets rid of the initial "Skipped:..."  message.  Then I get some fsck messages saying my disks are clean followed my more messages, including "starting apparmor profiles" and then "skipping ... firefox-3.5" and a couple more before the xsplash starts.  These messages now have the appearance of being written with X as opposed to console type style as with the previous "Skipped: ..." message.  Everything with the actual boot process seems fine though.

---

### Post by raqball on 2009-09-28
> **stevetxt said:**
> I tried it with the apparmor that just came as an update.  That gets rid of the initial "Skipped:..."  message.  Then I get some fsck messages saying my disks are clean followed my more messages, including "starting apparmor profiles" and then "skipping ... firefox-3.5" and a couple more before the xsplash starts.  These messages now have the appearance of being written with X as opposed to console type style as with the previous "Skipped: ..." message.  Everything with the actual boot process seems fine though.

Same here after update... Guess it's just reworded now... :)

---

### Post by Squonk07 on 2009-09-28
> **stevetxt said:**
> I tried it with the apparmor that just came as an update.  That gets rid of the initial "Skipped:..."  message.  Then I get some fsck messages saying my disks are clean followed my more messages, including "starting apparmor profiles" and then "skipping ... firefox-3.5" and a couple more before the xsplash starts.  These messages now have the appearance of being written with X as opposed to console type style as with the previous "Skipped: ..." message.  Everything with the actual boot process seems fine though.

Same here. I rebooted specifically to see if this new update solved this issue. They're sneaky--they buried the message in the text string for the fsck as though we wouldn't notice. ;)

Seriously, though, I'm sure this will iron itself out. Karmic boots every time for me so obviously this stuff isn't harmful.

---

### Post by hblaw on 2009-09-28
Emm... It seems I am not alone here. I also see a lot of trash when booting before seeing the splash screen. Seriously, why do these programs need to print messages on the screen instead of logging them in some files? I see no rationale to print anything on the screen at the boot time other than errors that hang the system. Just ignore all the immaterial warnings and messages, and put them somewhere we need to deliberately look for. :)

---

### Post by NormanFLinux on 2009-09-28
It bothers me but I live with it. Its alpha, after all. When we get an ursplash screen, we won't be bothered by text bootup messages anymore.

---

### Post by hblaw on 2009-09-28
Does it mean that something is supposed to cover the messages and that has not been implemented yet? If this is the case then good. Nothing to worry.

---

### Post by FrancoNero on 2009-10-02
yeah today's update... no dice... pity....

---

