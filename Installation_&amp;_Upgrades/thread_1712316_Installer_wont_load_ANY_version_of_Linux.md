---
title: "Installer wont load ANY version of Linux"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Beej701 on 2011-03-22
Hey everyone. I am a pretty savy windows user, but totaly new to Linux. When it comes to code and terminal editing I am just as lost as my grandfather. Anyhow, I am getting sick of Microsoft and I really wanted to try Linux. I saw the new unity interface that is coming out with Ubuntu and I really wanted to install it on my system.

The problem is, I cannot get Linux to install period. I have tried Kabuntu, Ubuntu, and Linux Mint. I get the same problem each time whenever I try either of them. The purple screen pops up, it takes like 5 mins, then the screen goes black and I get a ton of errors that list endlessly until I turn off the computer.

I decided to try the alternative version install of Ubuntu and I installed ok. But as soon as I enter my password to log in my mouse or keyboard, never both, one or the other, stop working. Mostly the mouse. I lost my keyboard but kept my mouse twice, where as I lost my mouse at least 10 times but not my keyboard. This of course makes using Ubuntu a rather unpleasant experience.

After doing some research, I think I learned that my mainboard's on board ati is the culprit. From what little I have been able to gather, believe me finding this stuff on Google took me a long time with trial and error, I think the general rule of thumb was that my mainboard is a real pain to install Linux on.

Here are my system specs screen shotted from cpuid:

[IMG]http://img585.imageshack.us/img585/7316/cpuzr.jpg[/IMG]

[IMG]http://img863.imageshack.us/img863/6859/mainboard.jpg[/IMG]

[IMG]http://img859.imageshack.us/img859/2434/memory.jpg[/IMG]

[IMG]http://img69.imageshack.us/img69/1314/spd1.jpg[/IMG]

[IMG]http://img705.imageshack.us/img705/8150/spd2m.jpg[/IMG]

[IMG]http://img859.imageshack.us/img859/1640/graphics.jpg[/IMG]

Thanks for any help anyone can provide. =)

---

### Post by Mark Phelps on 2011-03-22
According to a Google search, your motherboard has integrated Radeon Xpress 200 graphics -- which is not good because AMD dropped Linux driver support for that chipset years ago.  However, the default open-source video drivers should work OK.

As to onboard ATI graphics preventing USB devices from working, my current system has onboard graphics and that has no effect whatsoever on the USB devices.

---

### Post by Beej701 on 2011-03-23
Bump. Any help anyone can offer is appreciated. I really want to get away from Windows I cannot understand why this is happening.

---

### Post by Dutch70 on 2011-03-24
Hi and welcome to UF

If you're installing 11.04 while it's still in Alpha3, problems should be expected. 

Can you run 10.10 or 10.04 from the live cd or preferably usb stick? 
To see if you have the same problem. You can create a usb stick with Unetbootin, found here...
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Also, can you try a mouse or keyboard that plugs directly into your computer, not through a usb port? That may help narrow down the problem.

---

### Post by Beej701 on 2011-03-26
> **Dutch70 said:**
> Hi and welcome to UF

If you're installing 11.04 while it's still in Alpha3, problems should be expected. 

Can you run 10.10 or 10.04 from the live cd or preferably usb stick? 
To see if you have the same problem. You can create a usb stick with Unetbootin, found here...
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Also, can you try a mouse or keyboard that plugs directly into your computer, not through a usb port? That may help narrow down the problem.
Hi, I currently do not have a usb stick as my dog thought it made a nice chew toy. >.<

And I am using 10.10 for the reason you listed above. I originally tried to emulate ubuntu 11 with vmware, but with only 2 gigs of ram on Windows 7 it was an awful experience. So I decided to go with the current live version since it was to be a full install.

Also, I do have a non usb keyboard/mouse, and I tried those. After 5 or more boot ups with mouse and or keyboard failures, I gave up and am back here. Sorry for the slow response time, it's been a hectic week for me.

To be sure the OS itself wasn't freezing up, I let it run for a few mins, and its running fine. The update manager pops up, the clock is correct and continues to work. I even tried unplugging the keybord/mouse and replugging them in, nothing. After failure I would even switch from ps/2 to usb or vice versa while the os was running, nothing. I would try one usb and one ps/2, same problem.

Grrr I really want to give this a try, it's so maddening! No error screens, nothing concrete from google searches, I feel so stuck.

---

### Post by Beej701 on 2011-03-26
Based on what I have seen from this thread, could it be my video card for some reason? I honestly cant understand how a video card can do this, but my video card itself was referenced in this thread.

[http://ubuntuforums.org/showthread.php?t=1137378&page=6](http://ubuntuforums.org/showthread.php?t=1137378&page=6)

This was the only relevant information I could find after a lot of google searching. That thread is about 2 years old and the issue was on Ubuntu 9, not 10.10 which didn't exist yet.

---

### Post by Dutch70 on 2011-03-26
Have you tried nomodeset with the regular install, not alternate? 
Also, have tried to run the live cd instead of install to see if it will run from the live cd?

Links for selecting nomodeset and other options.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="RoyalBlue"]http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html[/COLOR]]("http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html")

Edit: You may also want to check the cd & the md5sum of the downloaded .iso.
[[COLOR="Blue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
[[COLOR="blue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

Other than that, I wouldn't know what it would be. Maybe someone else will have more input.

Best regards

---

### Post by Beej701 on 2011-03-26
Live CD hangs at the linux logo. Looking into the nomodset now.

---

### Post by Beej701 on 2011-03-26
At this point I am willing wager that something with my video card is making this happen. First I removed my pci-e nvidia gts250 and used straight up on board video. The problem was the same as before.

Then I went into that safe graphics mode and things got weird. The first message it gave me was that my video card was unrecognized and that I would have to configure it later. I logged in, but there were no icons or toolbars. The mouse was flickering really fast. I right clicked, and my menu options appeared. I was able to change my wallpaper. But the entire menu was flickering as well. With no toolbars, menus, and a seizure inducing repetitive flickering mouse, I decided to reboot, I couldn't do anything else.

I decided to try it one more time with the on board video in safe graphics mode, and I got a little further, I think. The flickering was gone, but I lost my mouse again. There were also again, no toolbars or icons. But I did get some errors. Perhaps these errors will help figure the problem out. I took a pic of them with my cell phone, here they are.

[IMG]http://img5.imageshack.us/img5/7251/img0631qy.jpg[/IMG]

[IMG]http://img8.imageshack.us/img8/3905/img0632o.jpg[/IMG]

Moving on, I then tried the same thing again, this time WITH my nvida gts250 instead of the on board video. I couldn't get as far. The keyboard would actually freeze up as I was typing my password sometimes. Other times the keyboard and mouse would work fine, but after I logged in the entire os would hang and nothing would load at all. Right clicking did not open a menu. Just to reiterate, everything I did in this post was all done on the nomodset version of ubuntu. Fresh format/install.

Finally, when I try to load up normally, with either on board video or my gts 250, it just freezes as soon as I press the login button after entering my password.

Edit: Just saw your your edit to your last post. Looking into that now.

---

### Post by Dutch70 on 2011-03-26
Just an idea, but if you can log-in without it freezing long enough to run the following command in terminal, it may stop it from freezing. I agree, it acts like a video card issue.

```
metacity --replace
```

Or ...right click the desktop, select "change desktop background" then click the "visual effects" tab & select "none" 

You can also get there by going to system > preferences > appearance, I think it is.

ps. You can attach pics using the paper clip in the toolbar. It's so much nicer :)

---

### Post by Beej701 on 2011-03-26
Im using a special hard drive for my ubuntu install. I took it it out and put it in my old computer, a pentium 4 ht with 1 gig of ram. I am currently making this post with ubuntu on my pentium 4. I didn't have to install anything, ubtunu loaded right up as soon as I turned this computer on. Def a hardware issue somewhere. *sigh*

---

### Post by Dutch70 on 2011-03-26
Nice work! So what are you're plans now?

---

### Post by Beej701 on 2011-03-26
For now to familiarize myself with Ubuntu. In a week or so I'll be done building my core 2 duo system with 4 gigs of ram. I just gotta buy the ram. The board and cpu were a gift so the system is a nice upgrade from a pentium D. All I'm paying for is the ram so woot.

I plan to put ubuntu on that system. I just hope that my video card problems dont follow me over to that system as I am bringing my gts 250 over to that system. The fact that I had problems even with that video card removed from the mainboard gives me hope that ubuntu will install with little fuss on my new machine. For now I am giving up on trying to install it on my pentium D, like I said next week I wont be using it anyways. Thanks for the help. :)

---

### Post by Dutch70 on 2011-03-26
> **Beej701 said:**
> For now to familiarize myself with Ubuntu. In a week or so I'll be done building my core 2 duo system with 4 gigs of ram. I just gotta buy the ram. The board and cpu were a gift so the system is a nice upgrade from a pentium D. All I'm paying for is the ram so woot.

I plan to put ubuntu on that system. I just hope that my video card problems dont follow me over to that system as I am bringing my gts 250 over to that system. The fact that I had problems even with that video card removed from the mainboard gives me hope that ubuntu will install with little fuss on my new machine. For now I am giving up on trying to install it on my pentium D, like I said next week I wont be using it anyways. Thanks for the help. :)

Ok, good luck with your new system. 

On a side note though, there is a linux distro that will run well on that pentium D. 

There is always Xubuntu & Lubuntu that are made to run on older machines & keep you in the buntu family. They are nicer OS's than one would think.

Regards

---

