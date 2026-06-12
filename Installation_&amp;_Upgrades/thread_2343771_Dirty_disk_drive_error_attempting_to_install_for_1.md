---
title: "Dirty disk drive error attempting to install for 1st time"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by juntjoo2 on 2016-11-18
My drive and DVD are new and clean. But it looks like it's running off the DVD. Should I just download the disc image file again and run the installation off the image from the Ubuntu os I'm running off the dvd?

---

### Post by Bucky Ball on 2016-11-18
*Thread moved to **Installation and Upgrades**.*

You'll get better support here and we're a friendly mob so we'll be gentle. :)

Confused. What are you trying to do? Install Ubuntu? If so, what is the problem specifically? When you boot from the install media, USB or DVD, if it has been created correctly you should get to a list of options. If you choose nothing then you would possibly be taken to 'Try Ubuntu' which is Ubuntu running from the install media. If you choose 'Try Ubuntu', then same. 

So possibly yes, you do have Ubuntu running from the DVD in which case you should have an icon on the desktop which says 'Install Ubuntu' or something like it. You just click that. Without more detail, hard to suggest much more. ;)

* Just a note: if you are intending to install, do you have a 'plan of action'? Do you know what you're going to put where and are you dual-booting with Windows? If a dual-boot, there are a few considerations.

---

### Post by juntjoo2 on 2016-11-18
> **Bucky Ball said:**
> *Thread moved to **Installation and Upgrades**.*

You'll get better support here and we're a friendly mob so we'll be gentle. :)

Confused. What are you trying to do? Install Ubuntu? If so, what is the problem specifically? When you boot from the install media, USB or DVD, if it has been created correctly you should get to a list of options. If you choose nothing then you would possibly be taken to 'Try Ubuntu' which is Ubuntu running from the install media. If you choose 'Try Ubuntu', then same. 

So possibly yes, you do have Ubuntu running from the DVD in which case you should have an icon on the desktop which says 'Install Ubuntu' or something like it. You just click that. Without more detail, hard to suggest much more. ;)

* Just a note: if you are intending to install, do you have a 'plan of action'? Do you know what you're going to put where and are you dual-booting with Windows? If a dual-boot, there are a few considerations.

Thanks. "Plan of action". Lol. I'm too ignorant in this to have a plan. It automatically took me to the CD trial I guess after failing to install. I guess I need a plan because after I get this all set up and going good eventually I will want to remove windows since it's using the majority of my hard drive like 350gb whereas this Ubuntu would be likeb178gb. Once I remove windows will I be able to expand the unbuntu partition? 

As far as installing should I go the install from hard drive route. I just saw it somewhere in the files so I don't know the process. Do I just run the disc image off this temp os? I'll look maybe tonight otherwise tomorrow but if you happen to have any advice feel free to share. Thanks!

Is this dirty disk error common and does it probably just mean a bad download?

---

### Post by mörgæs on 2016-11-19
If you want to remove Windows it's much easier to erase the entire hard disk during install than to do a dual boot and remove Windows later. 

Have you considered installing from USB in stead of DVD?

---

### Post by Bucky Ball on 2016-11-19
Still not sure what the 'dirty drive' error is.

You are going to need free space to install Ubuntu to so suggest you boot into Windows, work out how much data is on the drive currently, defragment the partition you're going to shrink several times and then shrink it to leave some free space if you don't have any.
 
Ubuntu can exist on a 20Gb partition and you can put your personal data elsewhere. There are options, but the bottom line is you are going to need free space to install Ubuntu. 

What exactly is happening when you boot from the DVD? It is not clear. You are getting a screen of options with 'Try Ubuntu' 'Install Ubuntu' etc???

Please try and be as specific as possible and give us your procedure from the start to where the problem occurs and the exact problem. If you are getting to the desktop, there's an icon that says 'Install Ubuntu'. ;)

As mörgæs has brought up, easier to install straight Ubuntu. If you are dual-booting, all good, just a few things you need to know first and you definitely do need to have a plan of action for that.

You'll need to know if Windows is booting in UEFI or BIOS mode for starters.

---

### Post by juntjoo2 on 2016-11-19
> **Bucky Ball said:**
> Still not sure what the 'dirty drive' error is.

You are going to need free space to install Ubuntu to so suggest you boot into Windows, work out how much data is on the drive currently, defragment the partition you're going to shrink several times and then shrink it to leave some free space if you don't have any.
 
Ubuntu can exist on a 20Gb partition and you can put your personal data elsewhere. There are options, but the bottom line is you are going to need free space to install Ubuntu. 

What exactly is happening when you boot from the DVD? It is not clear. You are getting a screen of options with 'Try Ubuntu' 'Install Ubuntu' etc???

Please try and be as specific as possible and give us your procedure from the start to where the problem occurs and the exact problem. If you are getting to the desktop, there's an icon that says 'Install Ubuntu'. ;)

As mörgæs has brought up, easier to install straight Ubuntu. If you are dual-booting, all good, just a few things you need to know first and you definitely do need to have a plan of action for that.

You'll need to know if Windows is booting in UEFI or BIOS mode for starters.

Thanks. I'll have to look into your last question in the morning. Or afternoon by the time I wake up(new York time). 

Anyway, I bet it's just a corrupt download. I'll figure out how to install from hard disk. 

As far as dual booting and partition space, right now there is a 178gb one available. My question is if later after I delete windows and it's partition is free, will I be able to expand my current 178 GB Ubuntu partition into that empty space. Basic question I don't know the answer to. Hopefully it's simple yes or no. 

On another note, as I was about to open a new tab to search for the Ubuntu download page from my dvd Ubuntu trial suddenly the screen turned off and since then the hate drive has been working on something. I have no idea. That was a couple hours ago. It's going. Any idea what this could be about? Maybe doesn't matter and I just need to figure out if I'm wasting my time installing on this 178 GB partition if ultimately I'll want it larger. But like the other poster said I could just keep my files on the other old windows position. Okay, makes sense. I did this type setup years ago. This is feasible once in get unbuntu installed right? Thanks

---

### Post by Bucky Ball on 2016-11-19
> **juntjoo2 said:**
> My question is if later after I delete windows and it's partition is free, will I be able to expand my current 178 GB Ubuntu partition into that empty space.

Yes. Or you can put a data partition there and access that from Ubuntu. Probably easier for backups.

> **juntjoo2 said:**
> ... figure out if I'm wasting my time installing on this 178 GB partition if ultimately I'll want it larger. But like the other poster said I could just keep my files on the other old windows position. Okay, makes sense. I did this type setup years ago. This is feasible once in get unbuntu installed right? Thanks

Like I said, you don't need anything like 178Gb to install Ubuntu to if your personal data is stored elsewhere. You can resize your Ubuntu partition anytime, doesn't matter. Wouldn't consider waiting until you decide whether you want it larger a reason to not install. Doesn't make sense. How you going to decide that if you haven't got Ubuntu installed anywhere in the first place? :)

---

### Post by juntjoo2 on 2016-11-19
Thanks!

---

