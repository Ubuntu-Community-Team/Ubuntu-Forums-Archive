---
title: "Nvidia driver issues with Ubuntu 11.04"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2011-08-07
After being on Ubuntu(x86) for the past 5 years, I decided to buy a new laptop (64 bit). I am doing a dual boot with Windows 7.

This morning I installed the dual boot-peace of cake! Now as I enabled the Nvidia propriety drivers(the recommended one) from Additional Drivers. Problems starting cropping up. First of all, as I restarted, it gave an error: the disk drive for /dev/mapper/cryptswap1 cannot mount or something.

It also fails to load plymouth, and then show the error message that Unity cannot load and that my Nvidia driver is active but not in use.

I am doing this for the past 8 hours(excluding lunch and occasional coffee breaks). Could someone please help sort this out?

Thanks a million!

---

### Post by 2uRcJQ34G1 on 2011-08-07
UPDATE: I reinstalled Ubuntu(again) and I didn't see the cryptswap1 message again. Moreover, after I installed nvidia driver the plymouth message showed up again. So I uninstalled that and the plymouth message disappeared. Now, my only problem is:
How do I install the Nvidia driver, without breaking my system?

---

### Post by 2uRcJQ34G1 on 2011-08-07
UPDATE: So I ran failsafeX and then updated the system. Now when I restarted the screen just stays blank. I can't even run the console with Ctrl+Alt+F1. Any help would be appreciated.

---

### Post by 2uRcJQ34G1 on 2011-08-07
UPDATE: So now I uninstalled the nouveau driver and now I can't even run failsafeX. Time to reinstall and do everything again. *Sigh*

---

### Post by 2uRcJQ34G1 on 2011-08-07
**THIS IS PATHETIC!! I GIVE UP(for now, at least). I can't use Ubuntu without Nvidia drivers and I can't do anything with. So much for user friendly computing. I am going to continue using my 32 bit old pc, until some has an idea.**

---

### Post by frankie1234 on 2011-08-07
A friend of mine had a similar problem with his wireless card drivers on a 64 bit machine. We resolved this by using a different distro. Not sure if it'll work but it is what I would try next

good luck!

---

### Post by MAFoElffen on 2011-08-07
> **gore_grinder said:**
> **THIS IS PATHETIC!! I GIVE UP(for now, at least). I can't use Ubuntu without Nvidia drivers and I can't do anything with. So much for user friendly computing. I am going to continue using my 32 bit old pc, until some has an idea.**
read this post and see if it would help you...
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

---

### Post by areeda on 2011-08-07
I had some issues with the latest NVidia drivers from NVidia but I'm running systems with a GTX 560, GT240 and 3100m they are all using veresion 275.09.07 I think.

Are you getting your drivers from canonical or NVidia?

Joe

---

### Post by MAFoElffen on 2011-08-08
> **areeda said:**
> I had some issues with the latest NVidia drivers from NVidia but I'm running systems with a GTX 560, GT240 and 3100m they are all using veresion 275.09.07 I think.

Are you getting your drivers from canonical or NVidia?

Joe
On my high end machines, all from NVidia.  That's what I wrote those instructions for.  On my low end machines, from the Ubuntu Repo's.

---

### Post by nativehound on 2011-08-08
First read
 [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

After you reinstall if you're met with a black/purple screen
and can't crtl+alt+f1 to a login prompt 

reboot and hold shift down if necessary to get to the grub menu then
plush e 
look for a line like this 

linux /boot/vmlinuz-2.6.38.8-generic  and so on  til   quiet splash  vt handoff=7

delete the part that says 
quiet splash  vt handoff=7

and replace it with

nosplash –-verbose text

do a normal reboot to x
it'll stop but not crash
crtl+alt+f1 to a prompt

sudo apt-get update
sudo apt-get upgrade

reboot

add

nosplash --verbose text to grub again

sudo apt-get update
apt-cache showpkg linux-headers 
apt-cache search linux-image

pick image and headers 2.6.38.10 or above

then 

sudo apt-get install linux-image-2.6.38.xx  linux-headers-2.6.38.xx

reboot to X 

if still no X. Boot to failsafeX and download from Nvidia the 280.13 x64 driver
remember where you put it.
Reboot out of failsafe
you shouldn't have to add nosplash –verbose text to grub, the header update should have fixed that

get back to a login prompt

sudo stop gdm

cd to the driver and run

sudo sh ./NVIDIA-Linux-x86_64-280.13.run 

sudo start gdm

you should have X
if still no X
check /var/log/ Xorg and kern logs for errors (EE)
or use failsafeX  when the menu pops up and asks what would like to do chose 
troubleshoot view the logs for errors (EE)  

if you find an API MISMATCH between the kernel and the nvidia driver reinstall the driver before trying a new header.

these steps basically came rite out of my terminal cache.  
 I'm running 2.6.38.10 with the 280.13 driver.
just updated over the weekend so may differ from a full install.

Hope this helps.

---

### Post by ShowMeGrrl on 2011-08-08
When I got a new high-end desktop computer (with 64-bit Lucid and the latest and greatest NVIDIA graphics), I was having hard freezes. Finally, support told me to go to System -> Preferences -> Appearance -> Visual Effects and change the setting from "Normal" to "None." Once I did that, I had no further problems. (And I did not notice any difference in how my computer looked, either.)

---

### Post by MAFoElffen on 2011-08-08
> **nativehound said:**
> First read
 [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

ROTFLMFAO!!!

Thank You-->  You realize that the refered link is to my own Sticky right? [B][B]
Sticky:[/B][/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") ?

I'm currently in the process of retesting and updating all of the workarounds that are located throughout that thread... and planning on either incorporating them into the first 3 posts, or making a table of contents page (in the first 3 pages), with links to those workarounds.

---

### Post by realzippy on 2011-08-08
> **gore_grinder said:**
> decided to buy a new laptop 

Nobody asked yet...
Which laptop?
Guess it has optimus technology.
Run:

```
lspci |grep VGA
```

If you see 2 devices,you are a member of the optimus club.
See:
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

### Post by MAFoElffen on 2011-08-08
> **realzippy said:**
> Nobody asked yet...
Which laptop?
Guess it has optimus technology.
Run:

```
lspci |grep VGA
```If you see 2 devices,you are a member of the optimus club.
See:
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)
Check the first post... User had already posted the lspci data... Optimus is NVidia, but yes--> same technology = Hybred Swiched Video.... ATI and ATI video chipsets.  (Look at my first response to him.)

The correct proprietary ATI driver (crysalis) will get him going with the correct ATI Linux utitlities for settings and switching.

What is important with all that, is that he uses the correct driver and follows the instructions I linked to... There are some workarounds in those instructions that matter in how things get installed and workout..

---

### Post by realzippy on 2011-08-08
> **MAFoElffen said:**
> Check the first post... User had already posted the lspci data... 

I usually check whole thread before I post,hate it when someone jumps in
posting obsolete stuff because being too lazy to read the thread.
Can 't find any lspci output in the whole thread...please show me.
Apologise if I am too blind....

---

### Post by MAFoElffen on 2011-08-08
> **realzippy said:**
> Nobody asked yet...
Which laptop?
[COLOR=Red]Guess it has optimus technology[/COLOR].
Run:

```
lspci |grep VGA
```[COLOR=Red]If you see 2 devices,you are a member of the optimus club.[/COLOR]
See:
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)
Check the first post... User had already posted the lspci data... 

Comment on that in red... No.  He does have Hybred Switched Graphics, but...

Sort of...Yes--> same technology = Hybred Swiched Graphics.... ATI and ATI video chipsets.  (Look at my first response to him.) But not Optimus.

Opimus is a chipset combination that has Nvidia Chipsets that's "Name" is Trademarked, that uses the technology of Hybred Switched Graphics.  So Optimus is Hybred Switched Graphics.  Hybred Swiched Graphics is not Optimus.  If it was Optimus, I would have referred him to "Bumblebee." ([http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html](http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html))

The hybred gambit that I've seen so far includes Intel/Sandy Bridge, Intel/Nvidia, Intel/ATI, ATI/ATI... Those that have a switch option in the BIOS, those that don't, where the acpi_call switcheroo kernel switch option could help... 

ATI, even though they have a disclaimer signing off this support for Linux for this technology-- Does support it in their drivers.  No opensource drivers yet support it.  So they are in reality saying what... we support it but expect it might not be perfect.

The correct proprietary ATI driver (crysalis) will get him going with the correct ATI Linux utilities for settings and switching.

What is important with all that, is that he uses the correct driver and follows the instructions I linked to... There are some workarounds in those instructions that matter in how things get installed and workout..

---

### Post by realzippy on 2011-08-08
> **MAFoElffen said:**
> Check the first post... User had already posted the lspci data..
So **where** is that posted output?
Why don 't you tell me instead of writing stories about optimus? :confused:

---

### Post by MAFoElffen on 2011-08-08
> **realzippy said:**
> So **where** is that posted ouput?
Why don 't you tell me instead of writing stories about optimus? :confused:
I honestly apologize... I really f'ed up! I got lost between threads that I was helping in... and on retesting some graphics workarounds before I update the instructions for them.

::really embarassed:: >> I wasn't even commenting on the same GPU!  No wonder I confused you!  Sorry about that... Looking back and rereading, he hasn't posted that data. You are right on that.

---

### Post by realzippy on 2011-08-08
Thanks.
I started to doubt my sanity....:D

...but I know myself that it is sometimes hard to multitask between threads,especially when they are about similar issues...

---

### Post by 2uRcJQ34G1 on 2011-09-03
I apologise for the late reply. But here is the output to lspci | grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dd6 (rev a1)

---

### Post by cbowman57 on 2011-09-03
You might want to look at the info in this link [http://askubuntu.com/questions/59037/how-to-get-nvidia-driver-working-properly-running-experimental-3d-support](http://askubuntu.com/questions/59037/how-to-get-nvidia-driver-working-properly-running-experimental-3d-support)

---

### Post by 2uRcJQ34G1 on 2011-09-03
After reading the Optimus thread, I am attempting at fresh installing Ubuntu and installing Bumblebee. It seems that I am running the aforementioned Optimus Technology.

---

### Post by jpthank on 2011-09-03
> **gore_grinder said:**
> After reading the Optimus thread, I am attempting at fresh installing Ubuntu and installing Bumblebee. It seems that I am running the aforementioned Optimus Technology.

good luck

---

### Post by 2uRcJQ34G1 on 2011-09-03
Thanks cBowman for that post I am trying that right now.

---

### Post by jpthank on 2011-09-03
> **MAFoElffen said:**
> read this post and see if it would help you...
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

you are a good man

---

### Post by areeda on 2011-09-03
I think that might work.

One thing I found is that mixing drivers from Cannonical and nVidia doesn't work well.  They put libraries and executables in different places and version mismatches does all sorts of subtle nasty things.

I ended up with that problem and some things worked fine others crashed and others just misbehaved.

Uninstalling it all and going with the Ubuntu nvidia-current drivers solved a whole litany of instabilities.

Good Luck.  Let us know if it works.

Joe

---

### Post by 2uRcJQ34G1 on 2011-09-03
So I did a fresh install of Ubuntu, installed bumblebee, it automatically installed nvidia-current. Everything ok. however, the Additional Drivers prompt asked me to install the propriety drivers(the one that bumblebee had supposedly installed). So I checked my packages and IT WAS INSTALLED! The prompt was wrong, but since I am still experimenting, I clicked Activate and re-installed the drivers. Back to Square One, same problem, black screen, unresponsive.
=================================================================================
Attempt 2
=================================================================================
Fresh install Ubuntu, installed bumblebee, followed the procedures from [here]("http://askubuntu.com/questions/59037/how-to-get-nvidia-driver-working-properly-running-experimental-3d-support?answertab=oldest#tab-top").
Surprisingly, even though bumblebee had installed(and I verified) nvidia-current, there was NO nvidia.conf files in the modprobe in etc. So I installed the nvidia drivers from the Additional Drivers found prompt again. However, instead of restarting, I made changes to the nvidia.conf file, which had now been created.
Restarted, back to Square One.
====================================================================================
VERDICT: **BUMBLEBEE DOES NOT WORK!!!**

---

### Post by 2uRcJQ34G1 on 2011-09-03
Solution for now: after a fresh install, installing bumblebee, does not seem to cause any major problems. There is that annoying Additional Drivers found prompt that shows up, but I think that can be ignored. I think it by default, resolves to use Intel graphics card. I haven't tested compiz on this kind of setting yet. But I guess this will have to make do, until someone else has a better idea.

Cheers to all those who are trying to help and courage to those who are sailing in the same boat. :D

---

### Post by 2uRcJQ34G1 on 2011-09-03
I am officially considering a new distro, if this issue gets resolved before that, then no problem. Otherwise, its time to experiment!

---

### Post by 2uRcJQ34G1 on 2011-09-04
For those of you who are still struggling with this issue, try ironhide from the repos, that is bumblebee exclusively for Ubuntu.

---

