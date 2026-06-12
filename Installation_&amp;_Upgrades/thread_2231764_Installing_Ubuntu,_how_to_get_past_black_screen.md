---
title: "Installing Ubuntu, how to get past black screen"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by ggg2 on 2014-06-27
Hello all,
i tried to install ubuntu14.04 -32bit-  on my PC put i have this problem [here ]("http://www.4shared.com/download/xECIwGV8ba/IMG__.jpg?lgfp=3000")how can i solve it?? 
i tried to boot it from flash but it didn't work and i tried to boot it from DVD using bios even that didn't work
please try to use easy language  I AM BEGINNER & not good at english i am on fire waiting your answer.

---

### Post by Bucky Ball on 2014-06-27
Welcome. You are trying to install Wubi. Wubi is no longer supported by Canonical. Much better to go with a dual-boot, one OS per partition. Please read here:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Feel free to stay with Wubi, but you may not have much success getting help with it.

---

### Post by hakuna_matata on 2014-06-27
First of all, I don't recommend Wubi.

But if you want to know the reason for the error message, some information from your log file is necessary. 

The name of the log file is in your attached picture.

---

### Post by ggg2 on 2014-06-28
ok
it looks like i doing it wrong.
to do it correct i must:
1- download ubuntu iso.
2- burn it on dvd.
3- put the DVD in the driver.
4- booting my copmuter from the bois.
is the previous true?

---

### Post by Bucky Ball on 2014-06-28
> **ggg2 said:**
> ok
it looks like i doing it wrong.
to do it correct i must:
1- download ubuntu iso.
2- burn it on dvd.
3- put the DVD in the driver.
4- booting my copmuter from the bois.
is the previous true?

In a nutshell, yes, true. When you burn the ISO to DVD you want to make sure you are creating a bootable disk and not just copying the ISO from one place to another. Your can alsoburn the ISO to USB. 

Boot from the Ubuntu DVD/USB and 'Try Ubuntu'. Make sure things are looking ok there and no problems (wireless might not work, but that should be fixable once installed to the hard drive). You can then either use the 'Install' icon on the desktop to install or launch Gparted and make sure you have the free space to install to or create some. 

Do not resize the Win7/8 partition using Gparted. ALWAYS boot to Win and use the default software there. 

If you decide on a dual-boot install I will change the title of this thread to increase your chances of support (as the current one has nothing to do with installing Ubuntu as a dual-boot :)).

Good luck. ;)

---

### Post by ggg2 on 2014-06-29
i try to do this:
1- download ubuntu iso.
2- burn it on dvd.
3- put the DVD in the driver.
4- booting my copmuter from the bois.

after that it gave me black screen in it "opereating system not found"

---

### Post by Elfy on 2014-06-29
> **ggg2 said:**
> get every thing like it was
i did not decide that[-X:x

Given that buckyball's statement was 

> If you decide on a dual-boot install I will change the title of this thread to increase your chances of support (as the current one has nothing to do with installing Ubuntu as a dual-boot ).

and not 

> As you have decided on a dual-boot install I will change the title of this thread to increase your chances of support (as the current one has nothing to do with installing Ubuntu as a dual-boot ).

There's no point in you posting what you did - so I have Jailed it.

---

### Post by Elfy on 2014-06-29
> **ggg2 said:**
> i try to do this:
1- download ubuntu iso.
2- burn it on dvd.
3- put the DVD in the driver.
4- booting my copmuter from the bois.

after that it gave me black screen in it "opereating system not found"

I would suspect that you've not burnt the image to DVD properly then. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ggg2 on 2014-06-29
> **Elfy said:**
> I would suspect that you've not burnt the image to DVD properly then. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

no my freind i read almost every thing before installing ubuntu. + i read what you want me to read and do it as they say exactly.
it is not my first time to burn on a disc #-o i am shure from what i did 
i don't now where is the problem, i think i am going to surrender.







and for this 

[B][COLOR=#ff0000]Given that buckyball's statement was 

[/COLOR][/B]**[COLOR=#ff0000]     [/COLOR]****[COLOR=#ff0000]         [/COLOR]****[COLOR=#ff0000]                                           If you decide on a dual-boot install I will change the title of this  thread to increase your chances of support (as the current one has  nothing to do with installing Ubuntu as a dual-boot ).                      [/COLOR]**
**[COLOR=#ff0000]     [/COLOR]**

[B][COLOR=#ff0000]and not 

[/COLOR][/B]**[COLOR=#ff0000]     [/COLOR]****[COLOR=#ff0000]         [/COLOR]****[COLOR=#ff0000]                                           As you have decided on a dual-boot install I will change the title  of this thread to increase your chances of support (as the current one  has nothing to do with installing Ubuntu as a dual-boot ).                      [/COLOR]**

**[COLOR=#ff0000]     [/COLOR]**

**[COLOR=#ff0000]There's no point in you posting what you did - so I have Jailed it.[/COLOR]**


i did not uderstand what you say even with google transation the only thing that i understood is jailing my post.
i feel that you enforce dictatorial just for my objection.

---

### Post by bapoumba on 2014-06-29
Please keep it to your install subject, thanks.
Any other comment (in particular regarding moderation actions) is better suited as a new thread in the Resolution Center : [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by Vladlenin5000 on 2014-06-29
> it is not my first time to burn on a disc #-o i am shure from what i did

It's easy to check just by opening the DVD in any file manager (any operating system will do) and looking at its contents:

1 - You see folders and files -> CORRECT
2 - There's only one ISO file inside -> INCORRECT (not bootable, wasted DVD)

In a nutshell, you DON'T burn the ISO file to a DVD-ROM. You select the "burn image..." (or equivalent option) option in your burning software instead.

---

### Post by Bucky Ball on 2014-06-29
> **Vladlenin5000 said:**
> 

In a nutshell, you DON'T burn the ISO file to a DVD-ROM. You select the "burn image..." (or equivalent option) option in your burning software instead.

^^^
This ... is what you're doing? Burn image, not 'drag and dropping' the ISO onto the DVD or creating a data disc?

---

### Post by ggg2 on 2014-07-01
you tell me does it true or false?
[here]("http://www.4shared.com/download/6CoL5UiLba/ubuntu.PNG?lgfp=3000")
i searched little some peopole say it mabye from somthing call uefi or uffi or somthing like this 
can u help?

---

### Post by sudodus on 2014-07-01
> **ggg2 said:**
> you tell me does it true or false?
[here]("http://www.4shared.com/download/6CoL5UiLba/ubuntu.PNG?lgfp=3000")
i searched little some peopole say it mabye from somthing call uefi or uffi or somthing like this 
can u help?

It looks good, I think you have made a good DVD boot disk :-)

-o-

You may have problems because your system is set in UEFI mode and you are trying with a 32-bit version of Ubuntu. If this is the case, please download and try the 64-bit version of Ubuntu 14.04 LTS or 12.04 LTS! It should work well both from USB and DVD.

 Do you know how Windows is installed (BIOS or UEFI)? Which version of Windows is it?

See this link for some more details and tips

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sudodus on 2014-07-01
The thread is in the forum [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333"), and I have changed the title so that it should attract people interested in your problem.

Good luck :-)

---

### Post by ggg2 on 2014-07-02
> **sudodus said:**
> It looks good, I think you have made a good DVD boot disk :-)

-o-

You may have problems because your system is set in UEFI mode and you are trying with a 32-bit version of Ubuntu. If this is the case, please download and try the 64-bit version of Ubuntu 14.04 LTS or 12.04 LTS! It should work well both from USB and DVD.[COLOR=#0000ff] my RAM=480mb will 64bit work? my PC is very old i don't think it will be able to run from  USB.
[/COLOR]
 [COLOR=#ff0000]Do you know how Windows is installed (BIOS or UEFI)? Which version of Windows is it?[/COLOR]
[COLOR=#0000ff] [/COLOR][COLOR=#0000ff]no, windows xp [/COLOR]
See this link for some more details and tips

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")
my answers in blue

---

### Post by sudodus on 2014-07-02
With a very old computer and only 480 MB RAM, you should not use a 64-bit version of Ubuntu.

1. Ubuntu needs much more RAM. Use a flavour with an ultra-light desktop environment instead.

2. Use a 32-bit version (even if the CPU might work with a 64-bit operating system), because 64-bit systems are more greedy for RAM (running the corresponding programs).

So I suggest that you download (or even better, get via torrent) some iso files and try them live before installing

- [Lubuntu desktop]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"): lubuntu-14.04-desktop-i386.iso

[Check also this link]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods")

- A community re-spin of Ubuntu 12.04 LTS

***Bento, Bodhi*** or ***LXLE ***(supported until April 2017)

-o-

Finally, have a look at the following links
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
[/URL][Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

