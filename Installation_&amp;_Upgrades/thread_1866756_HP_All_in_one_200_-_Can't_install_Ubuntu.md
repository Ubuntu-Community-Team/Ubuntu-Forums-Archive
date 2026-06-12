---
title: "HP All in one 200 - Can't install Ubuntu"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by heehaw00 on 2011-10-21
I am new to Ubuntu, and have a question pertaining to 11.04 and 11.10 install. I am unable to install either onto my new HP All in one 200 pc. Has anyone installed, or does anyone know of a way to install Ubuntu onto this pc? I have tried both the USB and CD install, and under both options, my screen turns black. I have checked both options on my laptop and they both work fine. The screen turns black during the loading portion when you would normally see the Ubuntu 11.04/11.10 and then the four dots underneath. I was able to install 10.10, but was not able to successfully acquire a wireless signal.
 
Any help would be appreciated.

---

### Post by jjcv on 2011-10-21
I suggest you do a google search on

"Install Ubuntu on HP <whatever model number>"

---

### Post by heehaw00 on 2011-10-22
Already tried that with no luck. Thanks though.

---

### Post by bijur on 2011-10-22
Hi,

I'm also trying to do that.

Se that post:
[http://ubuntuforums.org/showthread.php?p=11372647#post11372647](http://ubuntuforums.org/showthread.php?p=11372647#post11372647)

That's my final findings.

Bumped, also :(

If you select the "nomodeset" in the F6 options on the boot menu, it will work, but with non-accelerated video drivers.

With the accelerated video drivers, is a no-show.

If anybody have some clue, please.

Att,
Daniel

---

### Post by T.J. on 2011-10-22
Try disabling APIC on startup.  Some motherboards, like ASUS - suffer from firmware bugs that can be bypassed by disabling APIC.

When you boot the ubuntu CD, hit ESC to get the menu, then F6 for boot options.  Check "apic=off" and "noapic"  then simply run the installer from the menu.

After you install, you might be required to add them to your boot parameters, but we can cross that bridge later if that's the problem.

Best Wishes!

---

### Post by bijur on 2011-10-24
That didn't work, either.

Anyway, I had already tried ALL the options from the F6 menu.

Still looking for a solution.

Att,
Daniel

---

### Post by bijur on 2011-10-24
Just for the record: That is not a specific Ubuntu problem. I've already tried many distros, and not a single one of them worked out correctly.

I'm already looking into upstream (freedesktop.org's Bugzilla xorg section) to see what else I can find out.

Att,
Daniel

---

### Post by drillerccg on 2011-11-24
This worked great for me, use the [B]NOMODESET

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


works with 11.10 also.
[/B]

---

### Post by bijur on 2012-02-08
Hi, guys.

I think I found the solution.

Please, test it.
For me (I have an HP Omni 200-5320br All-in-one Series) it worked perfectly.
I describe the solution with more detail at [https://bugs.freedesktop.org/show_bug.cgi?id=43171](https://bugs.freedesktop.org/show_bug.cgi?id=43171)

Below is a link to debian packages, using the latest kernel tree (3.3.0-rc2):
[http://www.rapido.net.br/debs_hpomni200/](http://www.rapido.net.br/debs_hpomni200/)

Use it at your own risk ;)

Att,
Daniel

---

### Post by snafu_az on 2012-03-01
i think this might work for me, but i don't even know where to start with the patch

---

### Post by elcorazondelator23 on 2012-03-27
Thanks a lot, I proved the kernel from
[http://www.rapido.net.br/debs_hpomni200/](http://www.rapido.net.br/debs_hpomni200/)
and it worked,
but then I choosed to compile only the single module i915 with the patch and to replace the original 
module in my kernel

If someone is interested in compile only the module, when I have time I would make a tutorial.

regards
(sorry if I have some mistakes, I'm learning English)

---

### Post by snafu_az on 2012-03-29
Wow, this worked on my touchsmart 610 (i5 clarkdale w/ironlake graphics)

This is the first time i've been able to come up in anything but VESA mode using nomodeset.  It came up in 1920x1080.  Of course I have other issues now like the touch screen not working.

Any help on applying the patch from [https://bugs.freedesktop.org/attachment.cgi?id=56796]("https://bugs.freedesktop.org/attachment.cgi?id=56796")

I could apply it to the stock kernel, i just don't know how.

---

### Post by elcorazondelator23 on 2012-03-29
[FONT=Arial]
* F[SIZE=1]irst you have to download the kernel source and some tools

[/SIZE]  [/FONT][SIZE=1][B]bash:$ sudo apt-get install build-essential kernel-package
bash:$ sudo apt-get install linux-source 

[/B][/SIZE][FONT=Arial][SIZE=1]* then in /usr/src

[/SIZE][/FONT][FONT=Arial][SIZE=1]**bash:/usr/src$ sudo tar jxvf linux-source-X.X.X.X.tar.bz2**[/SIZE][/FONT][SIZE=1]

* now you can copy the source to your desktop, it is useful

[/SIZE]  [FONT=Arial][SIZE=1]**bash:$  **[/SIZE][/FONT][SIZE=1]**cp /usr/src/linux-source-3.0.0  /home/user1/Desktop**


*put in a txt file ,  the patch from [/SIZE]  [SIZE=1][https://bugs.freedesktop.org/attachment.cgi?id=56796](https://bugs.freedesktop.org/attachment.cgi?id=56796)
*only you have to copy the next part :
[/SIZE]     [SIZE=1]
SINCE:
[/SIZE][SIZE=1][I]diff --git a/drivers/gpu/drm/i915/intel_display.c b/drivers/gpu/drm/i915/intel_display.c index f02f86a..62bcbfd 100644 --- a/drivers/gpu/drm/i915/intel_display.c +++ b/drivers/gpu/drm/i915/intel_display.c

[/I][/SIZE] [SIZE=1]UNTIL:
[/SIZE][SIZE=1]*+    if (!intel_lvds_supported(dev)) +        return false; +      /* Skip init on machines we know falsely report LVDS */      if (dmi_check_system(intel_no_lvds))          return false;*


*I suppose you put the patch on "patch.txt" 

*now go to [/SIZE] [FONT=Arial][SIZE=1]/home/user1/Desktop/linux-source[/SIZE][/FONT][SIZE=1]

[/SIZE]  [FONT=Arial][SIZE=1]**bash:$  **[/SIZE][/FONT][SIZE=1]**cd  /home/user1/Desktop****/linux-source-3.0.0**

*now , apply the patch[/SIZE]  [SIZE=1]
[/SIZE] [FONT=Arial][SIZE=1]**bash:**[/SIZE][/FONT][SIZE=1]**/home/user1/Desktop****/linux-source-3.0.0**[/SIZE][FONT=Arial][SIZE=1]**:$ **[/SIZE][/FONT][SIZE=1][B]patch -p1 < /home/user1/Desktop/patch.txt

[/B][/SIZE][SIZE=1]*then go to cd linux-source-3.0.0/drivers/gpu/drm/i915/

[/SIZE]  [FONT=Arial][SIZE=1]**bash:$  **[/SIZE][/FONT][SIZE=1]**cd  /home/user1/Desktop****/linux-source-3.0.0/drivers/gpu/drm/i915/**

*and add at the end of the file Makefile the next lines, but before   
* {tab} is the space->be careful with the copy paste-> it is useful the program vi-> vi Makefile -> you can see the errors  ( apt-get install vim)
* now add the next lines at the end of the file Makefile:
[/SIZE][INDENT][INDENT]obj-m += i915.o

all: 
{tab}make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules 

clean: 
{tab}make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[SIZE=1]

[/SIZE] [/INDENT][/INDENT][SIZE=1]*( the next steps, you have to do them, with your system in the kernel version that you will use, use "nomodeset" to init your system if it is necessary, you can probe the "uname -r" command , you will understand the reason) 

*then in /i915 execute "make clean" , and "make"
**[FONT=Arial] bash:[/FONT]**[/SIZE] [SIZE=1]** /home/user1/Desktop****/linux-source-3.0.0/drivers/gpu/drm/i915/ $: make** [B]clean

[/B]**[FONT=Arial] bash:[/FONT]**[/SIZE][SIZE=1]** /home/user1/Desktop****/linux-source-3.0.0/drivers/gpu/drm/i915/ $: make** 

*now , if it is all rigth , you would have the file **"i915.ko"**
*that it is de new module

*finally , you have to copy i915.ko to the place where it is the original module of your kernel in use[/SIZE][SIZE=1]
*in my case , was the next dir : /lib/modules/3.0.0-12-generic/kernel/drivers/gpu/drm/i915$ 

(first do a backup)
**bash:$ sudo cp /lib/modules/3.0.0-X-generic/kernel/drivers/gpu/drm/i915/i915.ko     **[/SIZE] [SIZE=1]**/lib/modules/3.0.0-X-generic/kernel/drivers/gpu/drm/i915/i915.ko.old**

[/SIZE]  [SIZE=1]**bash:$sudo cp **[/SIZE][SIZE=1]**/home/user1/Desktop****/linux-source-3.0.0/drivers/gpu/drm/i915/i915.ko      ** **/lib/modules/3.0.0-X-generic/kernel/drivers/gpu/drm/i915/**

*the X is the version of your kernel in use.

*restart your system 
[/SIZE]
good luck [SIZE=1]
regards[/SIZE]

---

### Post by snafu_az on 2012-03-30
I added these lines to the Makefile

obj-m += i915.o

all: 
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules 

clean: 
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

When I run make clean I get: 

make: Nothing to be done for `clean'.

When I run make I get: 

make: Nothing to be done for `all'.

---

### Post by snafu_az on 2012-03-30
I figured it out with the help of another forum.

I had to add tabs to the commands

obj-m += i915.o

all: 
{tab}make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules 

clean: 
{tab}make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

---

### Post by elcorazondelator23 on 2012-03-30
Sorry, you are right, I lost the "tab" with the "copy paste"

its always useful use vi

vi Makefile

it shows the errors

Regards

---

