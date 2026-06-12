---
title: "No Video / Stuck at Boot / Tried first thread  / No Luck"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by bmcgonag on 2012-05-08
Below is the original question.  It is resolved in thread reply #11 page 2.

> I have an HP Pavilion DV6700. 

Worked fine on 11.10, but after upgrading to 12.04 the graphics won't work.  I went back and did a clean install from Live DVD to 12.04, still no luck.  I find it odd though that the DVD works fine on the system, but once loading natively from internal drive I get Unity crashes and such. 

I've tried the steps on the first thread in this forum, I got the Grub menu, edited the line to get a verbose boot, and the kernel booted...tried to boot into recovery mode, but it failed. 

I'm getting frustrated, but understand new versions will have problems.  Am running apt-get update and apt-get upgrade in command line now, but am not holding my breath.  If anyone has any suggestions or ideas, I would greatly appreciate it.

Brian

---

### Post by darkod on 2012-05-09
When you edit the line and delete the 'quiet splash' that will try to boot showing text along the way. You can see where it stops, what is bothering it.

---

### Post by bmcgonag on 2012-05-09
What I had initially on that line didn't say quiet splash.  after the ro it had 'remote nomodeset'.  I changed that to what it said in the tutorial, and watch it run through a text boot, but just ended up at the terminal window.

When I went back to change it back to 'remote nomodeset' I saw it had 'quiet splash' in place of what I had entered.  

Is that odd, or is it just the system changing it for me to appropriate values in that file?

Anyway, I'll run it again tonight when I get home and re-post where it stops if it stops.

Thanks,

---

### Post by darkod on 2012-05-09
Are you sure you didn't select the recovery entry? The recovery would have nomodeset by default. The normal entry should have 'quiet splash'.

PS. Maybe that's why it ended in terminal prompt. Recovery will usually boot you into command prompt.

Try without quiet splash at home and make sure you try the normal entry, not recovery. Also, try the normal entry by adding nomodeset, with or without the quiet splash (better without so you can watch the text).

---

### Post by bmcgonag on 2012-05-09
I actually do think that I did it with recovery mode.  I'll try it again with your suggestions for normal mode when I get home.  Thanks for the clarification and pointers.

---

### Post by bmcgonag on 2012-05-10
ok, tried the methods suggested, and the kernel boots.  I actually get the Ubuntu splash screen when booting, and when the splash screen goes away I get a black screen with the mouse cursor.  Occasionally if I move the mouse around a bit I get the normal Ubuntu background to come up momentarily, but no unity topbar or sidebar, and really nothing else on the desktop.  I can always get into a terminal window and move around fine without X session.  

I tried editing the /etc/default/grub file, and the /etc/grub.d/00_header file, but still no luck. 

The only thing in the tutorial that I haven't really tired is downloading the drivers in the terminal, but only because i have no idea what kind of graphics card is installed on this laptop.  Any way to get that info from the terminal?  And then how do I find the apt-get package for ther hardware even if I do figure out what it is?

I really appreciate all of your help,

---

### Post by bogan on 2012-05-11
Hi!, **bmcgonag**,

From a terminal, run:
```
lspci -nnk | grep -ie VGA 
``` Post the results here in a 'New Entry', [Highlight them and press the '#' symbol in the edit box toolbar.]

That will tell you the make and model of video card/cards you have.

What you do next depends on the result.

You Posted:>    I can always get into a terminal window and move around fine without X session.   So on the offchance , try```
 sudo nvidia-installer --latest
```This is only informative and will not alter anything, but may tell you what driver is installed, and available.

Chao!, **bogan**.

---

### Post by bmcgonag on 2012-05-11
```
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
```

When I type this:
> ```
sudo nvidia-installer --latest
```

I get
```
command not found
```

So I'm guessing that it doesn't know anything about the nvidia installer.  

How would I go about installing the nvidia drivers for this card through the terminal?

Thanks for the great help.

---

### Post by thatsmyboy on 2012-05-11
Hi Brian,
I don't know if it will help, but I found that my 10.04 to 12.04 transition was also bumpy. One problem included the fact that somehow my driver preference (Nvidia proprietary) was carried across. I tried a fresh install to avoid this, but who knows. The free drivers work (or at least passably) which might explain the live DVD working well. 


> **thatsmyboy said:**
> I already went ahead with apt-get update, apt-get upgrade. I ended up deactivating the restricted nvidia driver which seems to work well for my use. For those who want to know how it's under "system settings > Additional drivers" A search for "driver" in dash should do the trick.

---

### Post by bmcgonag on 2012-05-11
> **thatsmyboy said:**
> Hi Brian,
I don't know if it will help, but I found that my 10.04 to 12.04 transition was also bumpy. One problem included the fact that somehow my driver preference (Nvidia proprietary) was carried across. I tried a fresh install to avoid this, but who knows. The free drivers work (or at least passably) which might explain the live DVD working well.

I appreciate it.  I initially did an upgrade, but then just did a clean install from DVD with the same result.  

It seems the system now doesn't have the nvidia drivers, and that may be what i need.  I'm just trying everything people suggest at this point.  If it comes down to it, I'll go back to 11.10, but I'm hoping something will resolve here in a week or so.

---

### Post by darkod on 2012-05-12
I hope this can help:
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

And I hope it gets the latest drivers. I use ATI so don't know much about the exact nvidia commands. That shows the terminal installation.

---

### Post by bmcgonag on 2012-05-12
> **darkod said:**
> I hope this can help:
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

And I hope it gets the latest drivers. I use ATI so don't know much about the exact nvidia commands. That shows the terminal installation.


Darkod --- you RULE!  That fixed it.  I am so appreciative of all the help. Great Job.

---

### Post by darkod on 2012-05-12
No problem, glad you got it going.

I know it's frustrating when things don't work out of the box but I strongly believe that we need to appreciate the effort developers put in open source even if sometimes they don't have full cooperation of manufacturers and the attention those same manufacturers would pay to MS.

---

### Post by bogan on 2012-05-12
Hi!, **darkod**,

Thanks for Posting the Link for the xswat updates Ubuntu nvidia driver.
[http://www.noobslab.com/2011/09/nvid...0-oneiric.html]("http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html")

It successfully installed nvidia-current version " 295.49-0ubuntu1~precise~xup1".

As far as I can tell, with a GT 7650 card on 12.04 LTS, it works exactly the same as 295.49 downloaded from Nvidia downloads.

To add to the confusion: Additional Drivers now shows four versions of nvidia-current, though as it does not identify the version numbers at all clearly and which video cards each support is very vague; that is no help at all.

Chao, **bogan**.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

