---
title: "Fresh instal - Is Lubuntu well supported ?"
date: 2017-08-12
forum: Installation &amp; Upgrades
---

### Post by oygle on 2017-08-12
Doing a fresh installtion, and as this desktop is 9 yrs old, considering using Lubuntu. Have been using Kubuntu for about 4 years after many years on Ubuntu.

Is Lubuntu supported "as well as" kubuntu, in terms of updates, backports, new releases,etc,etc ?

---

### Post by Bashing-om on 2017-08-12
oygle' Hey again .

Short answer Yes .

The kernel is the kernel is the kernel.
All family members share the same software repository and the only difference in these members is the desktop and default installed applications.

(l)ubuntu's desktop is "light" and easy on resources .

[INDENT][INDENT]do it
[/INDENT][/INDENT]

---

### Post by DuckHook on 2017-08-12
Your question can only be answered with a great deal of ambiguity. Lubuntu and Kubuntu are different desktops with different teams of maintainers. However, they share the same Ubuntu foundation. Since this foundation makes up the majority of the code, you will get the same kernel, system and infrastructure updates. However, they bundle different desktops and apps, so the timeliness of these elements will depend on the maintainers, both upstream and downstream. For these elements, it's comparing apples to oranges.

I've used Lubuntu for years on my old or low-end machines and am quite happy with it. But because so many of the bundled apps are unique to Lubuntu alone, I find it quite meaningless to wonder about "timeliness" of support. Sylpheed is different than Thunderbird, Abiword cannot be compared to LibreOffice, etc. I'm not aware enough of the upstream release schedules to compare the elapsed times to distro updates, which would be necessary to measure "timeliness". Nor would I wish to conduct such a study. If the releases are reasonably timely and cover off the security holes, that's good enough for me.

---

### Post by oygle on 2017-08-12
> **Bashing-om said:**
> 
Short answer Yes .

The kernel is the kernel is the kernel.
All family members share the same software repository and the only difference in these members is the desktop and default installed applications.

(l)ubuntu's desktop is "light" and easy on resources .

Okay thanks, and thanks for your help in those other threads. It was a case of try this and that, but in the end, do a new backup of all the data and fresh install. I guess the ram may well be 'suspect', although I can boot fine to a live usb. I'm assumimg the disk errors were caused by the "dodgy" ram, but of course not entirely sure. I will endeavour to find some new ram, 4 x 2GB, but need to be aware of how much $$$ I put into that old mobo. I saw a new one for AUD $125, so just ram and cpu to add. Fortunately, the old mobo ( ASUS P5QL PRO - [https://www.asus.com/Motherboards/P5QL_PRO/specifications/](https://www.asus.com/Motherboards/P5QL_PRO/specifications/) ) has an ESATA port, so the backups are not taking too long. Just finishing off the compares now (Beyond Compare is great).  :)

> **DuckHook said:**
> Your question can only be answered with a great deal of ambiguity. Lubuntu and Kubuntu are different desktops with different teams of maintainers. However, they share the same Ubuntu foundation. Since this foundation makes up the majority of the code, you will get the same kernel, system and infrastructure updates. However, they bundle different desktops and apps, so the timeliness of these elements will depend on the maintainers, both upstream and downstream. For these elements, it's comparing apples to oranges.

I've used Lubuntu for years on my old or low-end machines and am quite happy with it. But because so many of the bundled apps are unique to Lubuntu alone, I find it quite meaningless to wonder about "timeliness" of support. Sylpheed is different than Thunderbird, Abiword cannot be compared to LibreOffice, etc. I'm not aware enough of the upstream release schedules to compare the elapsed times to distro updates, which would be necessary to measure "timeliness". Nor would I wish to conduct such a study. If the releases are reasonably timely and cover off the security holes, that's good enough for me.

Thanks, I'm sure there is a lot more to it than my term 'well supported'. The only "K" I need is KMyMoney. Was using KMail for many years, but the akonadi backend made KMail unusable. Now use light weight Claws mail. The only other major applications I use are Firefox, Filezilla, VLC, OpenOffice, KeePassX, Dolphin, Konsole, Kate, Beyond Compare and a handful of tools. On the laptop, I do use Oracle VM Virtual Box , but only once every few months to run Win 9 to d/load stats from an inverter. So I don't think there is much there that is departing from the 'norm', whatever that is.  :D

---

### Post by DuckHook on 2017-08-12
Based on the apps you've listed, you use enough "K" apps (KMyMoney, Dolphin, Konsole, Kate) that you'll drag in a lot of KDE overhead into your Lubuntu install anyway. While there is nothing strictly "wrong" with doing so, it does defeat the point of using Lubuntu—at least, to my way of thinking. I'll be the first to admit that this is a personal aesthetic of mine—there is no rule that prohibits the mixing of different desktop elements, and lots of people do it.

You just need to be aware that you may not save as much resources as you anticipate. Dolphin is especially heavy on KDE elements. You may wish to use apt with the -s switch (trial run) before doing an actual install. This will simulate the install with all of the dependencies, but not actually install anything. You can then decide beforehand whether you wish to drag in all of those extra dependencies into your pristine Lubuntu environment.

---

### Post by oygle on 2017-08-12
> **DuckHook said:**
> Based on the apps you've listed, you use enough "K" apps (KMyMoney, Dolphin, Konsole, Kate) that you'll drag in a lot of KDE overhead into your Lubuntu install anyway. While there is nothing strictly "wrong" with doing so, it does defeat the point of using Lubuntu—at least, to my way of thinking. I'll be the first to admit that this is a personal aesthetic of mine—there is no rule that prohibits the mixing of different desktop elements, and lots of people do it.

You just need to be aware that you may not save as much resources as you anticipate. Dolphin is especially heavy on KDE elements. You may wish to use apt with the -s switch (trial run) before doing an actual install. This will simulate the install with all of the dependencies, but not actually install anything. You can then decide beforehand whether you wish to drag in all of those extra dependencies into your pristine Lubuntu environment.

Hmmm, okay thanks. Considering the fresh install is the solution to a broken computer at present, and there _may_ be ram/disk problems, and chewing on what you said, I think I would be wise to install Kubuntu (a known distro on that computer) for now. Then later down the track, look at Lubuntu again. Thanks.  :)

( 'Broken' computer refs - [https://ubuntuforums.org/showthread.php?t=2368270](https://ubuntuforums.org/showthread.php?t=2368270)  and [https://ubuntuforums.org/showthread.php?t=2368519](https://ubuntuforums.org/showthread.php?t=2368519) )

---

### Post by vasa1 on 2017-08-12
> **oygle said:**
> ...
Is Lubuntu supported "as well as" kubuntu, in terms of updates, backports, new releases,etc,etc ?
No.

The Lubuntu team is much smaller.

The team is trying to get LXQt ready for 18.04, maybe.

But most of Lubuntu's specific applications are not under active development and so unlikely to break if they're in working condition :)

On a machine with "lower" specs, I'd install Lubuntu and think long and hard before installing other software, KDE or anything else, on it. Just to be clear, some GTK apps can be heavy as well.

---

### Post by oygle on 2017-08-12
> **vasa1 said:**
> No.

The Lubuntu team is much smaller.

The team is trying to get LXQt ready for 18.04, maybe.

But most of Lubuntu's specific applications are not under active development and so unlikely to break if they're in working condition :)

On a machine with "lower" specs, I'd install Lubuntu and think long and hard before installing other software, KDE or anything else, on it. Just to be clear, some GTK apps can be heavy as well.

Okay thanks, sounds like it is a good move to stay clear of Lubuntu. There are some KDE apps that I need day to day, like KMyMoney, so am downloading the Kubuntu 17.04 iso now.

---

### Post by oygle on 2017-08-13
The Kubuntu 17.04 install (from a live usb) is hanging, it seems. Over 1 hour now stuck on the same screen (see attachment). I pressed ctrl+F1+esc and the system activity showed gsettings using 25% of the cpu ?

One partition of the 1st hard drive had to be reformatted (root), but that was only 20Gb. By using file manager, I can see root 'looks' all installed okay.

The live usb was created with mkUSB and I used the 'persistant live' option.

---

### Post by vasa1 on 2017-08-13
Why did you make a persistent Live USB? I use mkusb to make a simple Live USB if I intend to install on a hard disk.

---

### Post by oygle on 2017-08-13
> **vasa1 said:**
> Why did you make a persistent Live USB? I use mkusb to make a simple Live USB if I intend to install on a hard disk.

It was the option for Debian/Ubuntu, so I assumed that was the correct one. Screen dump shows options. Which option should I take please ?

[ATTACH=CONFIG]276384[/ATTACH]

.... later, I did it again (mkUSB) and used option 'l' , so it's now installing again.  :)

---

### Post by vasa1 on 2017-08-13
> **oygle said:**
> ... later, I did it again (mkUSB) and used option 'l' , so it's now installing again.  :)
That's what I use as well.

I hope things go well for you!

@sudodus, while I'm sure each option is described in detail elsewhere, if it's possible and if you think it's useful, could you include a brief description of each option so that when users see the image that oygle posted, they could know what to choose more easily?

---

### Post by oygle on 2017-08-14
> **vasa1 said:**
> That's what I use as well.

I hope things go well for you!


Thanks for your help.  :)

---

### Post by oygle on 2017-08-14
Was able to do a clean install of Kubuntu 17.04 from a live usb. Thanks  :)

---

