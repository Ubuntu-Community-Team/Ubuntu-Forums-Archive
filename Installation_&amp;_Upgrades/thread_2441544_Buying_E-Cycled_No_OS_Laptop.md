---
title: "Buying E-Cycled No OS Laptop"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by stoneheart2 on 2020-04-24
I have my eye on a recycled HP laptop off eBay.  It comes with no OS and originally came with Windows 8 from HP.  I believe this model will have UEFI on it.  I haven't installed Ubuntu since UEFI came about.  Do I have to worry about anything when the hard drive comes empty of any Windows?

---

### Post by TheFu on 2020-04-24
Nothing except it being an HP.  

Some old HP systems (old being relative), especially the really cheap ones from the time, didn't fully implement the EFI standard so you may need to manually copy some boot files around.

The best advice I have is to google for "ubuntu install {laptop model}" to see if there are issues.

For about 5 yrs, I organized an InstallFest for my Linux Group at a local University. Typically, we'd have about 70 students and 5 non-students come for help installing. We'd push using virtual machines, since the students would likely have only 1 computer and required Windows for their classwork.  All sorts of computers would show up. About 30% would be the cheapest model possible, which meant the BIOS options would almost always be limited and even if the CPU supported VT-x/AMD-v (HW-virtualization support), the BIOS wouldn't have a way to enable it.  Some Celerion CPUs support VT-x. Same for Pentiums.  All Core i3/i5/i7 will.  Virtualization is very handy for all sorts of reasons, even if only to try a new release without risk to the current install.

I avoid HP PC equipment after being burned a few times. HP makes fantastic servers, however.
Over the years, I've owned HP, Dell, Lenovo, IBM, Asus, Acer, Toshiba laptops.  My next one will be either a Dell or Lenovo. I'm tired of keyboards, batteries, and power cords being substandard.  The HP laptops were provided by work. I've owned one HP desktop, which couldn't stay booted. Literally, would boot in the the Windows version it came with and walk away. Come back 4 hrs later to a BSoD. 6 months of firmware updates, patching, HP support emails, calls, and that $1000 was a total waste. Never again.

My current laptop is a used Asus X510UAR($305) (Core i5-8250U) and every few weeks another key fails to work on it.  A replacement keyboard is about $40, but installing it requires removing everything inside the case, including the laptop motherboard. So, it will be about $140 for someone qualified to replace the keyboard.  

Same keyboard issue for my Toshiba. The **new** toshiba CB35 (Core i3-5015U) ($430) had a bulging battery in addition to about 10 failed keys after about 2-3 yrs of use. It needed the EFI boot files to be copied manually for a trouble-free boot.  It would boot without those using the EFI manager built-into the BIOS.

Before that, it was a **new** Acer C720 Celeron 2995U ($212).  Certain keys failed after about 18 months of use, so I got a replacement and did all the swapping to install it. After that, the screen failed, replaced that.  When I was done, the system refused to boot. It was bricked. So I had a 3 yr old $200 new laptop with $60 of new parts in it and needed about $30 more to re-flash the BIOS.  A used version of the same thing was $80 at the time.  No more good money following bad anymore.

OTOH, I have a Dell 1558 laptop (Core i5-24xxU) from 2010 that still works, just big and heavy. New it only had about 2 hrs of battery. Lugging almost 6 lbs around isn't my goal anymore.  When I bought it, I didn't take any laptop traveling.  It replaced a damaged Dell 1535 (C2D) that broke after being dropped. 100% my fault. The 1558 was perhaps the best laptop I've owned/used except the weight. Clearly, it is outdated today and Dell tends to run $100 more for the same specs as other vendors.  To me, the lack of issues makes that slight extra worth it. I still use it daily.

I loved that Toshiba CB35, except the 4G of RAM. 8G Really is the minimal for my needs. It is a cheap ultrabook. Light (sub-3lbs), fast, perfect size, great resolution, amazing battery life, just the 8-12 broken keys on the keyboard is really the issue. Replacing the keyboard on all these devices is like open heart surgery - everything has to be pulled out of the case.  The bulging battery can be replaced. I still miss the Toshiba. Need to re-purpose it, perhaps as a media player using a wireless keyboard? Today, a couple of raspberry-pis do media playback very well. As a chromebook, physical modifications were necessary so it could boot non-ChromeOS. Those cannot be undone to my knowledge.

I was traveling with a Nokia tablet (central/south America) or an Asus Eee (N270) which was just really slow, terrible resolution and couldn't play hidef videos. The Eee was a great machine for the time and the keyboard lasted. I traveled a few continents with that thing.

But we all have different priorities and my anecdotes are not sufficient for decisions which should be made based on statistics. Perhaps I'm just harder on keyboards that most people or perhaps the last 3 laptops I've had were just so very cheap that cheap keyboards are part of the savings?

Be certain to read this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Monocerotis on 2020-04-24
> **stoneheart2 said:**
> Do I have to worry about anything when the hard drive comes empty of any Windows?

That should not be a problem in installing Ubuntu on it. Well, as long as it comes with a hard drive. You may have to wipe it if it has not been done already, but it's not something that the Ubuntu setup program can't do, so it should not be a problem. Other than that, you have all the usual things to consider when buying a used device.

---

### Post by super-jugaad on 2020-04-25
I am currently busy on a similar project and have found the following to be of great assistance. I suggest you peruse carefully in the provided order so that you can make an informed decision. As "[**[COLOR=#000000]Monocerotis[/COLOR]**]("https://ubuntuforums.org/member.php?u=1344884")" mentioned, don't forget to consider the usual factors of buying a pre-owned device.

1) [https://releases.ubuntu.com/](https://releases.ubuntu.com/)
2) [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
3) [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
4) [https://askubuntu.com/questions/206407/how-do-i-find-out-which-version-and-derivative-of-ubuntu-is-right-for-my-hardware](https://askubuntu.com/questions/206407/how-do-i-find-out-which-version-and-derivative-of-ubuntu-is-right-for-my-hardware)
5) [https://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop](https://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop)

---

### Post by mail-2o on 2020-04-29
TheFu has had some interesting experiences, but mine, with a number of laptops, over a few decades is that reliability goes in phases. For a few years, one will be best, then another manufacturer, then that changes. Currently I'm using an HP Elitebook (bought for [COLOR=#000000][FONT=Verdana]£[/FONT][/COLOR]80 several years ago). It is an i5 4gb and is excellent, IMO, running Lubuntu 20.04. Maybe I just bought a good one. 

Some people advise against buying laptops more than a few years old, but I've never had a problem.

---

### Post by GhX6GZMB on 2020-04-29
Depends on the HP model.
The Business notebooks were excellent, the Consumer types not.
I'm still running two 10+ years old HP/Compaq 6910p and they are perfect (and significantly faster than my 2 years old Win10 Dell).
They both run Lubuntu 19.10 with 4 GB resp. 2 GB.

---

