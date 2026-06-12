---
title: "Can't boot Live CD 14.10 - Possible to install?"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by Mallgur on 2014-10-27
Hi,

My laptop (ASUS F5GL) is currently running 12.04.
I would like to make a clean install onto another HDD.

I downloaded both versions of the Live CD (32 and 64 bits) but whenever I try to boot it I get an error related to the Graphics card (GeForce 8200M G/integrated/SSE2 ), something about nouveau error - switching to fbcon and then, after several terminal messages the screen gets all jumbled up and unusable. I've tried all the changes in the F6 menu to see if I could boot it with no luck.

Is there any possibility for me to install 12.10 if I can't boot the Live CD? Is this a solvable issue?

Thanks for any help.

---

### Post by Mallgur on 2014-10-28
I forgot to mention that I'm running and trying to install Xubuntu.

---

### Post by Bucky Ball on 2014-10-28
Do not use 12.10. Not sure if this a typo and you mean 14.10, but 12.10 has reached end-of-life and is no longer supported by Canonical or these forums.

---

### Post by sudodus on 2014-10-28
I think you are right, when you mention the nvidia graphics card. If 14.04 does not play well with it, (I guess you have tried **nomodeset**), you can try with the boot option **text**, and in text mode install a proprietary nvidia driver. After reboot it might work.

Otherwise I suggest that you stay with 12.04 LTS. I'm still using it in my production machine. Xubuntu is supported for another half year, and after that I can recommend two alternatives for old computers, alternatives that promise support until April 2017:

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

[http://lxle.net/](http://lxle.net/)

---

### Post by Mallgur on 2014-10-28
> **Bucky Ball said:**
> Do not use 12.10. Not sure if this a typo and you mean 14.10, but 12.10 has reached end-of-life and is no longer supported by Canonical or these forums.

No typo. I mean 14.10.
I'd like to do a clean install on a new HDD. I think the PC will handle it ok as Xbuntu is faily light and I don't use too intensive software like image processing or video editing.  Mostly it's browsing the net and sometimes a few Office files.

But thanks for the advice.

---

### Post by Mallgur on 2014-10-28
> **sudodus said:**
> I think you are right, when you mention the nvidia graphics card. If 14.04 does not play well with it, (I guess you have tried **nomodeset**), you can try with the boot option **text**, and in text mode install a proprietary nvidia driver. After reboot it might work.

Otherwise I suggest that you stay with 12.04 LTS. I'm still using it in my production machine. Xubuntu is supported for another half year, and after that I can recommend two alternatives for old computers, alternatives that promise support until April 2017:

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

[http://lxle.net/](http://lxle.net/)

I did try nomodeset (no luck) but I don't recall that text option... Are you sure that it exists? 
Could you point me to a thread about installing in text mode and setting up the Nvidia drivers?

I'll keep an eye out for those other options too.

Thanks.

---

### Post by sudodus on 2014-10-28
Yes, I have used the boot option **text**. It is not among the listed options, but you can enter it manually. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

> **F6**. Other Options. ACPI (Advanced  Configuration and Power Interface) and EDD (Enhanced Disk Drive) options  which may help if your computer does not support or has problems with  these systems. Highlight the selection and press the *ENTER* key  or SPACE key to select it. An "X" will appear, indicating selection.  Multiple items can be selected from this popup menu. Hit *ESC* to leave the popup menu. The selections are retained at the time the user presses the *ESC* key. 


[LIST]
[*]
[/LIST]

[LIST]
[*]In  addition to displaying preset boot options, pressing the F6 key also  opens the "Boot Options" line for ***manual editing*** once the popup window  is closed. (See next section).
[/LIST]


---

### Post by Mallgur on 2014-10-29
Thanks again sudodus.

I took a look at lxle (which I am aware is not part of the focus of these forums) but I have the same problem.
It boots and gets to desktop for a short while (without letting me click anything, just shows the wallpaper) but then exists with an error reporting "GPU lockup"... The only advantage is that this system has a VESA option to have a workable desktop environment that probably allows for NVIDIA drivers installation. I guess, as it is based on Ubuntu it uses the same "nouveau" drivers that apparently aren't very good as there is a fair amount of threads about this kind of problem around.
I think Xubuntu and Lubuntu should have such an option as both are reasonable options for older systems. Having a Live CD that fails to boot on systems that are "just" 6 years old is a bit off-putting.

Anyway, just a quick update. I'm still deciding whether to try the text option with Xubuntu or going for the VESA based installation on lxle... I'll post results here after. If I go for the text option I'll try to post complete steps on how it went so as to help others who might be facing the same problem.

---

### Post by sudodus on 2014-10-29
The computer runs well enough with vesa for you to install a nvidia driver, that is good! You may need to try a few of them until you find which one is best for your graphics chip.

---

### Post by Mallgur on 2014-11-19
[Update]

I gave up on installing a new system and opted to transfer my current installation to the new drive.
That too was a bit problematic (essentially grub problems) and I ended up only solving it by using Clonezilla to create an exact replica of the current disk. I then decided to upgrade to 14.04 via the system upgrade/update. That too led to some problems (system boot freezes on loading CUPS) but I'll start a new thread on that.
So, to summarize, lessons learned:

1 - The nouveau drivers don't work properly and that makes it impossible install some variants of Ubuntu (Xubuntu, LXLE)

This seems to indicate a bad choice from canonical to go with such drivers and not offer a fail-safe mode for older systems.

2 - If you wish to transfer a current installation to a new drive, go with clonezilla. Easy, simple and doesn't require any fiddling with an overly sensitive grub.

Thanks for all your help and pointers.

---

