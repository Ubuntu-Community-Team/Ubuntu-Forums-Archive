---
title: "Is there any word on when 10.04 will be able to be installed in Windows?"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gigarath on 2010-03-09
Does anyone know when this is going to happen? I saw the release schedule, but it didn't say.

---

### Post by Giwex on 2010-03-09
> **gigarath said:**
> Does anyone know when this is going to happen? I saw the release schedule, but it didn't say.
I don't understand the question

---

### Post by d3v1150m471c on 2010-03-09
Do you mean via wubi? Wubi is bad juju, I'd use a live cd.

---

### Post by gigarath on 2010-03-09
Yes, via Wubi. I use the live CD for my laptop, but I need Wubi for my Netbook, because I don't have an external CD drive. Also I am lazy, and don't want to format a USB drive to be able to boot from.

---

### Post by Lunx on 2010-03-09
> **gigarath said:**
> Yes, via Wubi. I use the live CD for my laptop, but I need Wubi for my Netbook, because I don't have an external CD drive. Also I am lazy, and don't want to format a USB drive to be able to boot from.

If you're lazy, I'd do yourself a favour and forget wubi. You'll save yourself a lot of time fixing stuff that shouldn't need fixing. The USB Startup Disc Creator is quick and simple to use.

That's my thoughts anyhow

:)

---

### Post by jppr on 2010-03-09
> **Lunx said:**
> If you're lazy, I'd do yourself a favour and forget wubi. You'll save yourself a lot of time fixing stuff that shouldn't need fixing. The USB Startup Disc Creator is quick and simple to use.

That's my thoughts anyhow

:)

Use Unetbootin, install it synaptic. Unetbootin is easier and quicker than usb-creator. In Unetbootin you can choose a direct what distro you want install and there is also direct latest live-cd. Unetbootin search and download the ubuntu one time a usb stick

---

### Post by phenest on 2010-03-09
> **jppr said:**
> Use Unetbootin, install it synaptic. Unetbootin is easier and quicker than usb-creator. In Unetbootin you can choose a direct what distro you want install and there is also direct latest live-cd. Unetbootin search and download the ubuntu one time a usb stick

The OP is using Windows.

> **Lunx said:**
> If you're lazy, I'd do yourself a favour and forget wubi. You'll save yourself a lot of time fixing stuff that shouldn't need fixing. The USB Startup Disc Creator is quick and simple to use.

That's my thoughts anyhow

:)

The USB Startup Creator is currently broken in Lucid, so I would use a Karmic Live CD for this.

---

### Post by jppr on 2010-03-09
He said... I use the live CD for my laptop... So, he can do Unetbootin installation in his laptop, then install ubuntu in usb his laptop and then install it in netbook. If I understand right that he is ubuntu in his laptop. :)

---

### Post by Sophont on 2010-03-09
> **d3v1150m471c said:**
> Do you mean via wubi? Wubi is bad juju, I'd use a live cd.

Why is Wubi "bad juju" in your opinion?
That statement, without giving any reasons, ain't worth much.

Live CDs are great - for temporary use of Linux in some situations. But for the advantages it provides you pay with much reduced performance and some restrictions in functionality (stuff - like proprietary 3d drivers - that needs rebooting has a problem with live CDs). There's also considerably longer boot times.

I short live CDs are great for *some* things - but if you want to use Linux a lot it will suck a lot.

Wubi OTOH allows people - not ready to switch completely away from windows yet - to try out Linux easily and under almost normal conditions (the cost of using a fake HDD is negligable in desktop practice) - without dabbling in scary stuff like resizing partitions.

IMHO it's genius.

It allowed me to convert someone to full time Linux use. A live CD would not have done that.

---

### Post by MacUntu on 2010-03-09
> **phenest said:**
> The USB Startup Creator is currently broken in Lucid

Nope, it's working fine.

---

### Post by whitefort on 2010-03-09
Um... just since Wubi is being badmouthed, I want to jump in and say that just for the record, I've always used it on my Windows machine, have installed it for nervous Windows-using friends who want to play with Ubuntu, and have never had any problems with it at all.

I would also like to see a Wubi option for 10.04.

---

### Post by phenest on 2010-03-09
> **phenest said:**
> The USB Startup Creator is currently broken in Lucid, so I would use a Karmic Live CD for this.

> **MacUntu said:**
> Nope, it's working fine.

Going on this [thread]("http://ubuntuforums.org/showthread.php?t=1418127"). Seems it's working again. But, I'd still use something more stable, like the version in Karmic.

---

### Post by leorolla on 2010-03-10
> **Sophont said:**
> Why is Wubi "bad juju" in your opinion?
That statement, without giving any reasons, ain't worth much.

Live CDs are great - for temporary use of Linux in some situations. But for the advantages it provides you pay with much reduced performance and some restrictions in functionality (stuff - like proprietary 3d drivers - that needs rebooting has a problem with live CDs). There's also considerably longer boot times.

I short live CDs are great for *some* things - but if you want to use Linux a lot it will suck a lot.

Wubi OTOH allows people - not ready to switch completely away from windows yet - to try out Linux easily and under almost normal conditions (the cost of using a fake HDD is negligable in desktop practice) - without dabbling in scary stuff like resizing partitions.

IMHO it's genius.

It allowed me to convert someone to full time Linux use. A live CD would not have done that.

Exactly!!!

My ears hurt when I see people preaching their anger against Wubi.

It's a _brand new_, _full_, _true_, Ubuntu install, with everything except hibernation.
It takes 25 minutes to install, while you have a coffee.
It takes 17 seconds to uninstall and get your PC right where it was before.

Even with a proper install Ubuntu 9.10 on a proper partition, I have entered Windows just to install and re-install a Wubi version Ubuntu 9.10 just for the purpose of doing tests.

I would never re-size and re-format a computer to install a Linux distro before I can see it running on a full install. Actually the existence of wubi makes it harder for me to try distros without a wubi-equivalent.

Without wubi, I wouldn't have edited wikis, filed bugs or collected my first beans at this forum. I guess I wouldn't be using linux yet.

Live who???
- I prefer a permanent install, with everything it comes with. I prefer the ability of configuring sound and rebooting to see how it is, and of updating kernel and rebooting.
- With Wubi I don't need any hardware, USB, nor CD. Just mount the .ISO virtually and choose "install inside windows".

By the way...
I'm eager to test Lucid.
[B]
Is there any word on when 10.04 will be able to be installed in Windows?[/B]

---

### Post by rajeev1204 on 2010-03-10
> **leorolla said:**
> Exactly!!!

My ears hurt when I see people preaching their anger against Wubi.

It's a _brand new_, _full_, _true_, Ubuntu install, with everything except hibernation.
It takes 25 minutes to install, while you have a coffee.
It takes 17 seconds to uninstall and get your PC right where it was before.

Even with a proper install Ubuntu 9.10 on a proper partition, I have entered Windows just to install and re-install a Wubi version Ubuntu 9.10 just for the purpose of doing tests.

I would never re-size and re-format a computer to install a Linux distro before I can see it running on a full install. Actually the existence of wubi makes it harder for me to try distros without a wubi-equivalent.

Without wubi, I wouldn't have edited wikis, filed bugs or collected my first beans at this forum. I guess I wouldn't be using linux yet.

Live who???
- I prefer a permanent install, with everything it comes with. I prefer the ability of configuring sound and rebooting to see how it is, and of updating kernel and rebooting.
- With Wubi I don't need any hardware, USB, nor CD. Just mount the .ISO virtually and choose "install inside windows".

By the way...
I'm eager to test Lucid.
[B]
Is there any word on when 10.04 will be able to be installed in Windows?[/B]

Probably with beta 2 :confused: The problem i have seen with wubi is detecting all my partitions from windows.

---

### Post by zoomy942 on 2010-03-11
cant you just install 9.10 through wubi then do a distro upgrade?

---

### Post by Starks on 2010-03-11
> **phenest said:**
> The OP is using Windows.



The USB Startup Creator is currently broken in Lucid, so I would use a Karmic Live CD for this.Unetbootin has a windows version.

---

### Post by leorolla on 2010-03-12
> **zoomy942 said:**
> cant you just install 9.10 through wubi then do a distro upgrade?

How long does a distro upgrade take?

How often does it lead to problems you wouldn't have otherwise?

How many more keys do you have to type (and text you need to read) instead of the 5 mouse clicks you make for a direct wubi install?


I know this is maybe the best (only?) solution in the abscence of wubi, but still not nice.

---

### Post by mdurham on 2010-03-12
Please correct me if I'm wrong. I think 'USB Creator' allows for persistence of user data and new prog installs but UNetbootin doesn't.

---

### Post by leorolla on 2010-03-12
> **mdurham said:**
> Please correct me if I'm wrong. I think 'USB Creator' allows for persistence of user data and new prog installs but UNetbootin doesn't.

About USB creator you are right, at leas partly.
Programs that you install persist, the Desktop and shortcuts persist.
But I'm not sure if the hardware settings persist as well.

You can use a Karmic Wubi install to create a Lucid live USB ;-)

Don't knwo about UNetbootin.

---

### Post by DeltaUK on 2010-03-19
> **zoomy942 said:**
> cant you just install 9.10 through wubi then do a distro upgrade?

Has anybody tried it? I was about to do this with 9.10 to 10.04 beta 1

---

### Post by zoomy942 on 2010-03-19
> **DeltaUK said:**
> Has anybody tried it? I was about to do this with 9.10 to 10.04 beta 1

i ended up just dual booting but if you want to try ti i would love to know how it goes.  thats be awesome

---

### Post by DeltaUK on 2010-03-19
> **zoomy942 said:**
> i ended up just dual booting but if you want to try ti i would love to know how it goes.  thats be awesome

It didn't work :(
When will we have wubi for 10.04!?

---

### Post by jppr on 2010-03-19
> **DeltaUK said:**
> It didn't work :(
When will we have wubi for 10.04!?
    
Wubi as included on the ISO images is unable to enter its second  stage of installation, so you will not be able to install inside Windows  using just an ISO image in this beta release. As a workaround, users  who are installing the Ubuntu Desktop Edition can download the  stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed  for 10.04 LTS Beta 2. (541607)
    *

---

### Post by DeltaUK on 2010-03-19
> **jppr said:**
> Wubi as included on the ISO images is unable to enter its second  stage of installation, so you will not be able to install inside Windows  using just an ISO image in this beta release. As a workaround, users  who are installing the Ubuntu Desktop Edition can download the  stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed  for 10.04 LTS Beta 2. (541607)
    *

Thanks, wish i knew about that 2 hours ago! just wasted a lot of time :P

---

