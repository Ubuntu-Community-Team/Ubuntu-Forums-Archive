---
title: "Upgrading my Ubuntu OS"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2011-10-10
I currently have Ubuntu 10.04.3 LTS installed on my computer and im wondering if upgrading to 10.10 would be a wise choice or not.

My specs are as follows
80GB hard drive
1GB of RAM
64MB of embedded graphics memory
Pentium 4 2.80GHZ CPU 

I just want a straight up opinion not a link to a spec page ive checked the specs i know what they are im just curious if upgrading would really be any benefit or not.

---

### Post by IWantFroyo on 2011-10-10
Ubuntu 10.10 gets more feature-related updates. If you want to have a more up-to-date system without messing with a ton of PPAs, I would advise you update. If stability and security is more important for you, I would suggest you stick with Lucid.

Maverick was a very good release, however. If you were going to update, that's what I would recommend you update to.

---

### Post by shahan on 2011-10-10
Ubuntu 10.10 includes more strong Hardware support then before. and some fixes of bugs. I suggest you to upgrade.

---

### Post by TheRacerX on 2011-10-10
thanks i was getting annoyed with the computer constantly asking me to update everytime i turn on the computer so i was curious as to if 10.10 would run smoothly or not since my computer isnt all that powerful

---

### Post by IWantFroyo on 2011-10-10
It should work. Maverick is probably the same in resource use as Lucid was.

---

### Post by snowpine on 2011-10-10
The biggest Pro to 10.10 is that all your software would be 6 months newer (but not as new as 11.04 or 11.10 obviously).

The biggest Con to 10.10 is that it has a shorter support period. 10.10 will only be supported until Apriil 2012, whereas 10.04 will be supported through April 2013 (plus you will be able to upgrade directly from 10.04 to 12.04, the next LTS).

I recommend you test-drive a Live CD of 10.10 before making up your mind.

---

### Post by thatguruguy on 2011-10-10
> **TheRacerX said:**
> I currently have Ubuntu 10.04.3 LTS installed on my computer and im wondering if upgrading to 10.10 would be a wise choice or not.

My specs are as follows
80GB hard drive
1GB of RAM
64MB of embedded graphics memory
Pentium 4 2.80GHZ CPU 

I just want a straight up opinion not a link to a spec page ive checked the specs i know what they are im just curious if upgrading would really be any benefit or not.

If everything is working, there is little reason to upgrade right now.  In April of next year, the next LTS will be available, and you can upgrade directly from one LTS to the next.  If you upgrade to 10.10 now, you will have to either do a clean install of 12.04, or upgrade step-by-step (first to 11.04, then to 11.10, and finally to 12.04).

---

### Post by TheRacerX on 2011-10-10
only problem being ive tried 11.04 on this computer and it wont run it at all keeps saying my system doesnt have the required hardware to support Unity and when it reverts back to the old classic look the taskbars flicker and disappear so you cant even click on anything.

---

### Post by grahammechanical on 2011-10-10
That message about not having the required hardware could be the truth but on my machine it referred to the need to install a proprietary video driver. 

In 11.10 the fall back mode for machines like your one will be Unity 2D. It looks similar to Unity 3D which does require more powerful hardware but it uses different libraries and needs lower hardware requirements.

Regards.

---

### Post by Old_Grey_Wolf on 2011-10-10
TheRacerX,

I would recommend staying with 10.04.03 LTS. If you upgrade to 10.10, it will complicate upgrading to the 12.04 LTS. If your computer is working, then 10.10 really doesn't have advantages for you except for newer versions of applications that you may not care about. I have similar hardware and 11.04 was just to demanding for my old hardware. If you wait for 12.04 LTS, I would advise using a live CD/USB to test it before upgrading. If it works on your hardware great; if not, you may want to look at Xubuntu, Lubuntu, Kubuntu, or a different distro; such as, Debian stable instead. 

I know you may not like it; but, if you want to run the newer releases of many of the distros you will need newer hardware. I myself find that the distros that run on my old Dell laptop with a single core 2.4 GHz processor, 1 GB RAM, 60 GB HDD, and integrated graphics just don't satisfy me. Sadly, I am recycling my old Dell laptop. May it Rest-In-Peace (RIP) as it served me well for a long time.

If the nagging about upgrading is annoying, you can turn that off. Using the menus select "System" > "Administration" > "Update Manager". Then click on the "Settings..." button. Then where it says at the bottom "Release upgrade" select "Long term support releases only" from the menu. It will stop nagging you after you save those settings.

---

### Post by PayPaul on 2011-10-12
I have a similar question about whether to upgrade or not to upgrade. I see all this talk of LTS releases vs the other kind and wonder what the difference is. Would I also experience any difference between running a LiveCD of say, the 10.04 linux as a liveCD on my current machine as opposed to actually installing it? Would I be able to get an idea of how the new release, 11.10 would act on this machine or the older laptop I also have? Do some people simply run Ubuntu continuously doing their usual tasks from the LiveCD?

---

### Post by snowpine on 2011-10-13
> **PayPaul said:**
> I have a similar question about whether to upgrade or not to upgrade. I see all this talk of LTS releases vs the other kind and wonder what the difference is. Would I also experience any difference between running a LiveCD of say, the 10.04 linux as a liveCD on my current machine as opposed to actually installing it? Would I be able to get an idea of how the new release, 11.10 would act on this machine or the older laptop I also have? Do some people simply run Ubuntu continuously doing their usual tasks from the LiveCD?

LTS releases are supported 36 months (3 years) and released at 2-year intervals.

Regular releases are supported 18 months and released at 6-month intervals.

That's the main difference, so it's simply a question of how frequently you like to update your system. Do you want a stable system for 2 years, or do you want more frequent updates so you can have the latest software?

The problems with running from the Live CD all the time are 1) it's a lot slower than a hard drive install; 2) you lose your work each time you reboot.

---

### Post by PayPaul on 2011-10-13
> **snowpine said:**
> LTS releases are supported 36 months (3 years) and released at 2-year intervals.

Regular releases are supported 18 months and released at 6-month intervals.

That's the main difference, so it's simply a question of how frequently you like to update your system. Do you want a stable system for 2 years, or do you want more frequent updates so you can have the latest software?

The problems with running from the Live CD all the time are 1) it's a lot slower than a hard drive install; 2) you lose your work each time you reboot.

What if you run it with persistence? Use the F6 key when you click the "Try Ubuntu" button? I've also seen that there is a DVD version and CD version, the DVD version being larger. Is the DVD Version better or more packed with goodies? I'm planning on doing something like that to see what it looks like first. But if it's slower that's only going to show me what the interface looks like and how navigating the new release will be. I'd also would like my new install to have the ability to flip over to the "classic" or non-unity mode. I'm not that versed in it all yet to make a distinction between the two interfaces. I only want to see what the differences are.

Update: I was just taking a look at the tour and have they really renamed "The Trash"? They called it "Rubbish bin" in the video. I love that!! How wonderfully British!!

---

