---
title: "Upgrade to Intrepid now or wait?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cullinane on 2008-10-05
Hey all- this is my first post on the boards, though have been using Ubuntu since Hardy was released. 
My question is simple: If I were to install the Intrepid beta would updating it to the 'complete' stable version at the end of the month be a simple matter of updating via the update manager or would it require a fresh install? Would it make more sense to wait? I do want to do a total wipe of my Hardy partition as I'm having some issues with video functionality in general

So should I wait, or will the updates from beta to stable Intrepid be painless? Thanks in advance.

---

### Post by Pumalite on 2008-10-05
Intrepid is in development. There are still a few bugs to work out. You can help test, doing a clean install. Then keeping up with the updates would get you to the final release.

---

### Post by Herman on 2008-10-05
:) The best way to move to Intrepid, is to resize your Hardy partition and install Intrepid after it, if you have plenty of hard disk space.
Then you can leave your data in Hardy Heron and continue to use that if you find that Intrepid isn't quite ready for you yet.

In your particular case you may find that Intrepid is better for you.

In my case, I use Kompozer a lot, (almost all the time), and unfortunately it crashes in Intrepid as soon as I touch a table in it. Other than that Intrepid is working fine for me.
Other people might discover that some other little problem bothers them, so generally it wouldn't be wise for most people to try to use Intrepid as their main operating system yet.
When Intrepid is officially released, it still might take another week or two for things to settle down and stabilize.

When Intrepid is ready, and when I'm ready, all I will do is transfer my personal files and settings over from Hardy into Intrepid and then stop using Hardy so much. I'll leave it there though. Eventually I will replace it with whatever new version will come after Intrepid. When that one is ready, I'll move into that one, and so on.

I always feel sorry for people who install with a separate /home partition thinking they don't need to back up their files because 'their files are safe' that way.
Every time a new version of Ubuntu is released, there will be a lot of posts here in the forums with people crying because either they upgraded and something went wrong, or they installed / again, keeping their separate /home (without making a backup), and something went wrong, and they lost all their data.

Whatever your preferred method of doing things is doesn't really matter, as long as you're having fun. But making a backup is the most important thing of all, even if we do have excellent file recover software here these days.

Regards, Herman :)

---

### Post by Pumalite on 2008-10-05
I'm one of those that have a separate /home, but I never use it. When the occasion comes; I just do a clean install.

---

### Post by cariboo on 2008-10-05
Unless you are comfortable with dealing with and repair video problems, and other things that just don't work properly, I wuold suggest you wait until the release. Beta software, is really unfinished software, unlike Windows where their betas are really rc's. Intrepid is mostly usable, but some people are having problems getting things to work. Have a look here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

to see some of the problems people are having.

JIm

---

### Post by Spaceman9 on 2008-10-05
If you already have 8.04 LTS installed you don't have to install 8.10. You'll get everything for 8.10 in your updates to 8.04.

8.04 is a rolling version of Ubuntu. That means you can keep 8.04 on your hard drive untill April, 24 2011 and all the new stuff is added to it with the automatic update thing in Ubuntu.

---

### Post by picpak on 2008-10-05
> **Spaceman9 said:**
> If you already have 8.04 LTS installed you don't have to install 8.10. You'll get everything for 8.10 in your updates to 8.04.

Not necessarily. LTSs only cover security updates, not program version updates.

---

### Post by WWSmith36 on 2008-10-05
One word........Backports

---

### Post by Spaceman9 on 2008-10-05
> **picpak said:**
> Not necessarily. LTSs only cover security updates, not program version updates.

Oh buggers! That's the one thing I don't like about Linux. Every six months I have to install another updated version. So, every six months I have to type in all my member names and passwords and reinstall all the software I had installed and working. That really burns my toast! 

It's a good thing I like Linux. Otherwise, I'd keep using it anyway.

---

### Post by snowpine on 2008-10-05
> **Spaceman9 said:**
> If you already have 8.04 LTS installed you don't have to install 8.10. You'll get everything for 8.10 in your updates to 8.04.

8.04 is a rolling version of Ubuntu. That means you can keep 8.04 on your hard drive untill April, 24 2011 and all the new stuff is added to it with the automatic update thing in Ubuntu.

This is absolutely not true. Ubuntu does not do rolling upgrades. If you stick with 8.04, packages are "frozen" at their current version. You will continue to get big fixes and security upgrades, and your system will become more and more stable over the next 3 years. That's what LTS means.

As mentioned, there is a "backports" system in place for those who want to have the latest and greatest version of a particular package/application.

---

### Post by snowpine on 2008-10-05
> **Spaceman9 said:**
> Oh buggers! That's the one thing I don't like about Linux. Every six months I have to install another updated version. So, every six months I have to type in all my member names and passwords and reinstall all the software I had installed and working. That really burns my toast! 

It's a good thing I like Linux. Otherwise, I'd keep using it anyway.

Not true; nobody is forcing you to upgrade every 6 months. There are people on these forums who are still using 6.06, for example. Also, you always have the choice to dist-upgrade instead of a fresh install, in which case you keep all of your programs, data, saved passwords, etc. 

Also there are many other distros of Linux with completely different development cycles, Debian (very slow and deliberate development with an emphasis on stability) and Arch (constantly rolling upgrades), for example.

---

### Post by Spaceman9 on 2008-10-05
> **snowpine said:**
> This is absolutely not true. Ubuntu does not do rolling upgrades. If you stick with 8.04, packages are "frozen" at their current version. You will continue to get big fixes and security upgrades, and your system will become more and more stable over the next 3 years. That's what LTS means.

As mentioned, there is a "backports" system in place for those who want to have the latest and greatest version of a particular package/application.

Ok, so how do I get the backports installed? I'd rather keep 8.04 as long as I can.

---

### Post by Pumalite on 2008-10-05
System>Administration>Software Sources
Tick backports
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by snowpine on 2008-10-05
> **Spaceman9 said:**
> Ok, so how do I get the backports installed? I'd rather keep 8.04 as long as I can.

Required reading: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Disclaimer: I've never actually used backports myself; I haven't been using Ubuntu long enough to be left behind. :)

---

### Post by Spaceman9 on 2008-10-05
> **Pumalite said:**
> System>Administration>Software Sources
Tick backports
sudo apt-get update
sudo apt-get dist-upgrade

Hi Pumalite, you've helped me before, how ya been. Thankx for the help again.


> **snowpine said:**
> Required reading: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Disclaimer: I've never actually used backports myself; I haven't been using Ubuntu long enough to be left behind. :)

Ok, thankx for the link. I read it and it looks like Ubuntu really doesn't want people using backports. I might as well just install the stupid 8.10 upgrade. That means I'll have to wait till next month to do something I was going to do this month. Buggers!

---

### Post by cullinane on 2008-10-05
Cheers for the help everyone. I think I'm going to wait til Intrepid is officially released and do a clean install. With a bit of luck I'll be able to get my video/audio issues and dual-screen setup sorted out- and if so, will be able to leave XP behind forever.
Until then! :)

---

### Post by Pumalite on 2008-10-05
'Hi Pumalite, you've helped me before, how ya been. Thankx for the help again.'

Still ticking. You are welcome. Any time.

---

### Post by Spaceman9 on 2008-10-07
snowpine I was looking at Ubuntu docs and stuff and I found this [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

"Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions."

Doesn't this mean I can just download the 8.10 upgrade in to my install of 8.04? Wouldn't that be the same as doing an complete install of 8.10?

I don't mean to give you a hard time. I just hate to have to reinstall all the programs and type in my member names and passwords again.

---

### Post by snowpine on 2008-10-07
> **Spaceman9 said:**
> snowpine I was looking at Ubuntu docs and stuff and I found this [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

"Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions."

Doesn't this mean I can just download the 8.10 upgrade in to my install of 8.04? Wouldn't that be the same as doing an complete install of 8.10?

I don't mean to give you a hard time. I just hate to have to reinstall all the programs and type in my member names and passwords again.

Yes, that is just the GUI method to accomplish the 'dist-upgrade' that Pumalite and I described in posts #11 and 13. 

Some people on the forums prefer a fresh install to an upgrade, for various reasons. Personally, I am an upgrader, not a fresh installer, and I've never had any problems. so I say 'why not.' :)

---

### Post by wkulecz on 2008-10-07
Hard drives are cheap.  If it ain't broke, don't fix it.

If your video issues are a problem, get another hard drive, remove your current working drive and sub in the new drive for a fresh install of the new system.  If it don't work out, put the original drive back in and you are only out the time you spent playing around with the new stuff.

--wally.

---

### Post by Elfy on 2008-10-07
I would just add here that if you haven't actually even booted the livecd how doyou know that there aren't any issues with your system.

You could possibily end up with no usable system.

Just a thought...

---

### Post by Pumalite on 2008-10-07
Intel boards with Gigabyte controlled Ethernet should stay away from Intrepid for the moment
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

---

### Post by Elfy on 2008-10-07
+1 and legacy nvidia don't work with the new xorg either, though that's not in quite the same league ;)

---

### Post by Spaceman9 on 2008-10-07
> **snowpine said:**
> Yes, that is just the GUI method to accomplish the 'dist-upgrade' that Pumalite and I described in posts #11 and 13. 

Some people on the forums prefer a fresh install to an upgrade, for various reasons. Personally, I am an upgrader, not a fresh installer, and I've never had any problems. so I say 'why not.' :)

Excellent! I wanna be an upgrader too! lol I love Ubuntu!:)

---

