---
title: "Input Not Supported (Error Message)"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by and003 on 2011-05-27
I recently tried to upgrade from Ubuntu 10.10 to 11.04. At first, the installation seemed to go smoothly, but when I tried to boot up, my screen displayed the following error message:

Input Not Supported

I am unsure how this is happening, since I was able to install 10.10 successfully. To better assist, I am attaching detailed information about my computer system.

---

### Post by Hedgehog1 on 2011-05-28
The 'input not supported' message is coming from your monitor.

The default resolution that Natty has selected to too high (or just too different) for your monitor to display.

Is this only happening during the GRUB menu?  Are you able to press enter and boot up?

**IF IT IS ONLY HAPPENING IN GRUB** and you can boot into Ubuntu then please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by and003 on 2011-05-30
When I tried to install Natty on my computer, I set the installation process to take over the entire hard drive. The installation process worked like it was supposed to, with no apparent errors.

When I tried to boot up, the information about the motherboard appeared, as always, but it was shortly thereafter that the 'Input Not Supported' error message appeared. The booting process stopped at that point. I couldn't even get into GRUB, nor could I press enter and boot up.

---

### Post by and003 on 2011-06-07
Yesterday I discovered something about Ubuntu 11.04. When I attempted a second effort at installing Natty, the 'Input Not Supported' error came up, as usual ... but after a few seconds, the message disappeared and Ubuntu booted up.

I'm thinking that perhaps I just needed to be patient and wait. In any case, I'll try to look into this matter further.

---

### Post by and003 on 2011-06-07
As I promised in my last post, I looked further into this issue. In my case, the 'Input Not Supported' error message only stays on the screen for 22 seconds or less before it disappears and the Ubuntu screen comes up. I don't know if this behavior applies to other monitors, but I thought I'd post this information for anyone who's interested.

---

### Post by wildmanne39 on 2011-06-07
> **Hedgehog1 said:**
> The 'input not supported' message is coming from your monitor.

The default resolution that Natty has selected to too high (or just too different) for your monitor to display.

Is this only happening during the GRUB menu?  Are you able to press enter and boot up?

**IF IT IS ONLY HAPPENING IN GRUB** and you can boot into Ubuntu then please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***
:KSHi Hedge, you are awsome this fixed my problem, I have been trying to fix it with xrandr with no luck, I have not seen my boot screen since I installed natty during beta testing, and I have post the problem with no answers, thank you I appreciate your help.

---

### Post by Jerry Story on 2011-10-23
> **Hedgehog1 said:**
> The 'input not supported' message is coming from your monitor.

The default resolution that Natty has selected to too high (or just too different) for your monitor to display.

Is this only happening during the GRUB menu?  Are you able to press enter and boot up?

**IF IT IS ONLY HAPPENING IN GRUB** and you can boot into Ubuntu then please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

I have a "input not supported" problem. It doesn't get to where I can do something, no recovery mode. All I can do is use the live CD.

This is what happens:
$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
$ 

Can this problem be solved?

---

### Post by warmaster4z2 on 2013-03-13
Hopefully someone can benefit from my late solution to this problem:

1. Download Grub Customizer from Synaptic Package Manager.

2. Go to System Tools and open the program.

3. Right below the "Save" button on the upper left hand side of the screen you should see three tabs (List Configuration, General Settings, Appearance Settings)
   click on Appearance Settings and use the drop down arrow to select one of the resolution sizes, I used 1024x768x16. Now maybe if you're lucky this will solve your problem.
 
4. Now click "Save", exit the program, and restart your computer to see if the problem is fixed.                 
 

The reason why this works might be because your monitor (like mine) uses a resolution that isn't included in the drop down list of Grub Customizer. Changing the resolution in Grub Customizer however does not affect your desktop resolution so give it a try!

---

