---
title: "Ubuntu 10.04 for Toshiba Machines"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by c00lwaterz on 2010-03-24
I want to get reviews on ubuntu 10.04  with Toshiba machines.

If anyone who tried to install or experience the lucid with Toshiba machines. Pls post here your experiences with ubuntu 10.04 so I can decide if I will install ubuntu 10.04 on my laptop.

My machine is toshiba m900 core 2 duo 2.2ghz with 3gb memory.
using windows and ubuntu karmic. It's great but some problem with high temperature and wireless issues.

I tried many tips on google but it won't give me luck. Hope lucid is the answer to my problems. :popcorn:

Any tips are welcome.

Thanks in advance

---

### Post by Mark Phelps on 2010-03-24
You would get better response if you had posted this to the correct forum, in this case, Development & Programming, Lucid Lynx Testing.

---

### Post by seenthelite on 2010-03-24
I have a Toshiba  P500 Laptop with 10.04 installed and I have no hardware compatibility issues. But that's not to say it will be the same for you, the components in your Toshiba are most likely different. Temperatures are okay and the wireless worked without any issues . The card is a Intel wifi Link 5100 AGN. Usually if you use the live CD and install with no changes to your computer (live) you can see if the wireless will work.

---

### Post by c00lwaterz on 2010-03-24
I have realtek Network card here in toshiba. Realtek for wireless Lan and realtek for PCIe. I have tried the koala karmic installed but no luck fixing the issues. I'm waiting for lucid for now and reading reviews if the heat issues and wireless had been solve. Still checking and waiting for final version of 10.04.

I have read that many people have common issues with the high temperature and wireless. I need luck.

Thanks

---

### Post by c00lwaterz on 2010-03-26
waiting for updates of ubuntu 10.04 and experiences from users who tried lucid.

---

### Post by Paddy Landau on 2010-03-26
I think that you'll have to wait until after Canonical has released Lucid to get much feedback. My family has four Toshibas, but I won't upgrade until the dust from Lucid's release has settled.

---

### Post by c00lwaterz on 2010-03-26
i'm also waiting for the final release. i have heat issues and I cannot see any network in my wireless. im using wpa2. i read that karmic don't support wpa2. im using toshiba m900 with realTEK WIRELESS LAN and I want to fix the high temp issue

---

### Post by edfoxx36 on 2010-04-30
Im using  a toshiba L510. Posted a problem with wifi that seems to not be a unique issue. [http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510](http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510)

---

### Post by c00lwaterz on 2010-04-30
> **edfoxx36 said:**
> Im using  a toshiba L510. Posted a problem with wifi that seems to not be a unique issue. [http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510](http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510)

Hi,

Do you have High temperature issue and fan issue?
I worry my laptop will get burn. It is really overheating using linux. Do you experience same as mine?

---

### Post by 73ckn797 on 2010-04-30
Toshiba Satellite M115-S3094. Intel Core Duo T2050 2Gib Ram, Intel GMA 950 video.

Ubuntu has always "just worked" on this laptop.

---

### Post by c00lwaterz on 2010-04-30
I don't have luck fixing my linux on toshiba portege m900.
I feel hopeless on using linux. If there is a chance, I'd be happy.
Until now I feel sad because it did not work on my laptop:confused:

---

### Post by kleskjr on 2010-04-30
Satellite L100 - no problems so far :)

---

### Post by Matthew T. on 2010-05-03
This got the cooling fan to work for me on my Satellite L305-S5955. YMMV

Change appropriate line in /etc/default/grub to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux", then run sudo update-grub.

---

### Post by mo79 on 2010-05-03
I installed on a Toshiba NB100 netbook without a hitch. Then again, this machine has an Ubuntu Certified case sticker anyway. :)

---

### Post by 73ckn797 on 2010-05-03
> **c00lwaterz said:**
> i'm also waiting for the final release. i have heat issues and I cannot see any network in my wireless. im using wpa2. i read that karmic don't support wpa2. im using toshiba m900 with realTEK WIRELESS LAN and I want to fix the high temp issue


wpa1/2 has always worked with Karmic, for me on my Toshiba.

---

### Post by c00lwaterz on 2010-05-03
> **73ckn797 said:**
> wpa1/2 has always worked with Karmic, for me on my Toshiba.

some people help me with wifi issue and it was solved. Unfortunately the heat issue and fan issue is not yet fix and every solution I tried and people help me it has no success.

Portege m900

---

### Post by 73ckn797 on 2010-05-03
> **c00lwaterz said:**
> some people help me with wifi issue and it was solved. Unfortunately the heat issue and fan issue is not yet fix and every solution I tried and people help me it has no success.

Portege m900

Cannot help you on that one. I have not experienced the heat issue.

---

### Post by nicocarbone on 2010-05-03
I have a Toshiba M305-S4820. Lucid works perfectly out of the box. No complains.

---

### Post by Dave Gravox on 2010-05-04
> **edfoxx36 said:**
> Im using  a toshiba L510. Posted a problem with wifi that seems to not be a unique issue. [http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510](http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510)

I'm using an L510 (PSLGXA-002002) and I can't even get the 10.04 Live CD to boot, it doesn't even get to the selection menu. The 9.10 Live CD is only slightly better, but I can't start a session with that either. The images are good for both.

Not sure what to do next.

---

### Post by kecek on 2010-07-03
> **c00lwaterz said:**
> I don't have luck fixing my linux on toshiba portege m900.
I feel hopeless on using linux. If there is a chance, I'd be happy.
Until now I feel sad because it did not work on my laptop:confused:

hay, sorry can i ask you? you have same as my laptop, i have M900 too, with NVIDIA Dedicated VGA. can u tell about temperature with this ubuntu 10.04, i don't have idea with 9.10, because i want try this version, what do you thing?

---

### Post by kaosent on 2010-07-11
I have a Toshiba Satellite A505-S6030 Core i-7 running Ubuntu 10.04 LTS 64-bit.  I LOVE THIS LAPTOP.  My experience has been (and the posts in this thread prove) that Toshiba support can be hit or miss.  As a brief summary, here is the pain I experienced, I provide this because I feel it is the best example of the worst semi-functional situation you may face...

My laptop shipped with v.1.20 of the H20 Insyde BIOS, I used the windows installer (WUBI.exe) to install Lucid alongside windows 7, it seemed to work, but the regular install failed badly.  Ubuntu would not install or run live, but would eventually freeze hard.  In order to install, I had to take note of the following:

**To INSTALL:**
If the BIOS is v.1.10 or v.1.20, then you MUST press F6 at the first install menu and select ACPI=off [SIZE=1][*I also had to use the "alternative" installer, no fancy GUI... that may actually help you @*[Dave Gravox]("http://ubuntuforums.org/member.php?u=791412") *with your installation issues, like me, you probably are having video driver conflicts*][/SIZE]
If you BIOS is v.1.30, you MUST downgrade to v.1.20 or lower (at least I had to), then do the above...

**To BOOT:**
For v.1.10 and v.1.20 you MUST have a grub option set to either: noapic OR acpi=noirq OR acpi=ht OR acpi=ht (tested all of them, noapic is the least problematic).
For v.1.30 you must have grub options: noapic AND acpi=ht  (my experience).  AND to make it more fun, you can only successfully boot IF you are restarting the machine.  If you are starting up cold, then you must press F2 to enter the BIOS setup at boot, and press F10 then ENTER (no changes, just cycle the BIOS), then the laptop would actually start up without freezing or soft-locking after disabling IRQ#10.

I lived this way for a while.  No battery support, no ability to dim the screen, fan was iffy, some of the FN keys didn't work.  The Toshiba kernel modules would not load, and would throw an error if you attempted modprobe... fnfxd and toshutils provided little help, and dmesg showed errors from fnfxd that stated the kernel was not compiled to support those tools.  A minor pain, but...

It ALL goes away if you compile a new kernel and set the config options which include the word TOSHIBA to yes, (especially CONFIG_TOSHIBA=y).  Ubuntu now realizes that my A505-S6030 is actually a laptop and behaves accordingly and boots properly with no funky grub options, and with the v.1.30 BIOS.  I am thrilled at its performance, it out runs my 6 month old desktop by a long shot.

If I had one wish relative to this, it would be that either the stock kernel supported the Toshiba options, or that there was a prebuilt officially supported one that did.  I don't want to have to run a custom kernel, and I don't want the pain of rebuilding to support updates.

Just my $0.02, your experience with the above may be met with success, or not.  I really love this laptop, Lucid is amazing on it.  If anyone else has a similar laptop, I would be interested in hearing their results for comparison...

---

### Post by VAB on 2010-07-13
> **c00lwaterz said:**
> I want to get reviews on ubuntu 10.04  with Toshiba machines.

If anyone who tried to install or experience the lucid with Toshiba machines. Pls post here your experiences with ubuntu 10.04 so I can decide if I will install ubuntu 10.04 on my laptop.

My machine is toshiba m900 core 2 duo 2.2ghz with 3gb memory.
using windows and ubuntu karmic. It's great but some problem with high temperature and wireless issues.

I tried many tips on google but it won't give me luck. Hope lucid is the answer to my problems. :popcorn:

Any tips are welcome.

Thanks in advance
Hi, 
For the moment my old Toshiba satellite is almost dead because of upgrade ...
The previous release was working fine...
I forgot the old wise advice "do not fix it if it's not broken"
I am going to downgrade or see if netbook edition will do 
but I'll try it first from a usb-drive.
That's my experience so far, let's see ...

---

### Post by Dave Gravox on 2010-09-06
> **kaosent said:**
> 
It ALL goes away if you compile a new kernel and set the config options which include the word TOSHIBA to yes, (especially CONFIG_TOSHIBA=y).


Great! Now I'm just stuck on this bit. I've followed the instructions here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

And have the kernel downloaded and ready for modification, but I'm not sure how to modify it. A search reveals 338 references to 'TOSHIBA' in the kernel directory. Could someone please tell me how and exactly what to modify in the config options?

---

### Post by tmzy on 2010-09-10
I have a toshiba netbook NB250 running on ubuntu, works lovely except  for adjusting brightness.

---

### Post by Bucky Ball on 2010-11-03
Without compiling a custom kernel:

Use kernel 2.6.35.* (at this point Maverick Meerkat 10.10)
Press ESC at purple screen with two icons down the bottom.
F6, choose 'acpi=off' by selecting it, hitting 'enter' then ESC.
Select 'Try Ubuntu without installing'.

If all goes well and you are sitting at a Ubuntu desktop, hit icon on desktop and install. Reboot and at grub menu list at startup:

Select kernel and hit 'e'
At the kernel line ending with 'quiet splash' **_DON'T_** add 'acpi=off' as it loses fan control and other things, but make it end like this:

```
quiet splash acpi=copy_dsdt
```This will boot up with fan control and a few other things depending on the machine. I have the Satellite Pro L510. You can use acpi=off but the fan, for me, stays on constantly and the machine runs quite hot. The alternative is much better and my Toshiba now works like a dream, _except_ wireless is totally erratic rendering it unusable ... for now.

If this all works you can make the change permanent by editing /etc/default/grub. Find the line that reads (or add it if it isn't there):

```
 GRUB_CMDLINE_LINUX=""
```... and change it to:

```
 GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```Then:

```
 sudo update-grub
```If you don't do this last step the change to /etc/default/grub won't stick. Reboot without editing kernel to make sure it all worked. Enjoy.

---

### Post by ulfj on 2010-11-03
Iv'e been using ubuntu only on Toshiba laptop since it was new with no problems that I didn't cause(I can be a moron at times)running 10.04 now.

---

### Post by Bucky Ball on 2010-11-03
> **ulfj said:**
> Iv'e been using ubuntu only on Toshiba laptop since it was new with no problems that I didn't cause(I can be a moron at times)running 10.04 now.

How old is it? My fix is specifically for very new machines (the L510 for instance). If you have no problems running kernels other than 2.6.35.* and above, fantastic! It is not the case with some of the newer models.

---

### Post by GHerzog on 2011-07-28
I have a Toshiba NB250 with 10.04 Netbook version installed as a dual boot. The other side is the original W7 Starter that came with the machine.

The only problem are the FN+function key selections - must don't work due to what appears to be an incompatible BIOS from Toshiba.

Still, I can live without toggling all those keys and use the computer daily when I am out and about via wifi hot spots. So 'in general' it works fine.

Laptops and notebooks are always more problematic than desktops. I made the mistake of buying before checking if any Linux was an easy install on this particular model. And it isn't perfect.

---

