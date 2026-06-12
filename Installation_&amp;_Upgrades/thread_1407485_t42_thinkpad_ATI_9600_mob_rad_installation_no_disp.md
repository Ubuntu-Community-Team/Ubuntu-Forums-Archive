---
title: "t42 thinkpad ATI 9600 mob rad installation no display"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by irus on 2010-02-15
hi guys i have been trying to install 10.04 daily builds via unetbootin/usb stick and everytime i select normal/safe graphics and proceed with installation im greeted with a blank screen which continously becomes brighter until it is totally fuzzy yellow. linux works on the background but there is no display except the yellow screen.

my thinkpad t42 has an ATI mobility radeon 9600 chip. earlier i used to be prompted for working in a low resolution environment but  now i dont get any such prompts. is there some solution to this problem because i want to shift over the ubuntu asap on the laptop after having shifted to it on the desktop.

thanks !!

---

### Post by irus on 2010-02-15
bump some help will be much appreciated:popcorn:

---

### Post by irus on 2010-02-15
bump

---

### Post by irus on 2010-02-15
bump

---

### Post by witwicki on 2010-02-15
Irus,

I am experiencing similar issues with my T43P (which also has a 9600 mobility radeon).  I don't see yellow though, I just see a blank (black) screen.

Oddly enough, if I plug in an external monitor and run Lucid off of the Live DVD, the desktop displays correctly on the external monitor but not on the laptop LCD. 

Karmic worked fine, but Lucid seems to have this problem, perhaps 
something wrong with Xorg.  I just opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/522394](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/522394)

Does the external monitor trick work for you?  If so, go to my bug report and click "This bug effects me".  Also, commenting that you're experiencing the same problem with your T42 may help to get the bug noticed.

-Stefan

---

### Post by mcoleman44 on 2010-02-15
If you can, I would just use jaunty or Karmic.
They are more likely to work with ATI.

Lucid has been having problems with ATI.

Did you mess with the xorg.conf before this problem occurred?

---

### Post by irus on 2010-02-16
@witwicki thats exactly whats going on here! supporting the bug now. ive run the installation by plugging it into the desktop monitor now running the update manager. fingers crossed maybe this will work!

---

### Post by irus on 2010-02-16
> **mcoleman44 said:**
> If you can, I would just use jaunty or Karmic.
They are more likely to work with ATI.

Lucid has been having problems with ATI.

Did you mess with the xorg.conf before this problem occurred?

i didnt mess with anything this seems to be an OS bug! infact older versions are now showing the same bug for some weird reason so all versions have become unusable (9.04 and 9.1)

---

### Post by irus on 2010-02-16
ok i installed ubuntu 10.04 using the vga cable from laptop to desktop and fn+f7 and ran update manager and rebooted. 2d is working fine!:popcorn:

---

### Post by witwicki on 2010-02-16
The thinkpad monitor is working for you?

I ran the update-manager in 10.04 (Lucid) just now, installed all available updates,  and rebooted.  Still no display on my T43P screen.

I've tried Fn-F7 as well as both mirror and side-by-side modes in System->Preferences->Display.  But all my thinkpad monitor displays is blackness.

-Stefan

---

### Post by irus on 2010-02-17
> **witwicki said:**
> The thinkpad monitor is working for you?

I ran the update-manager in 10.04 (Lucid) just now, installed all available updates,  and rebooted.  Still no display on my T43P screen.

I've tried Fn-F7 as well as both mirror and side-by-side modes in System->Preferences->Display.  But all my thinkpad monitor displays is blackness.

-Stefan

yes the thinkpad monitor is working. i also went into synaptics manager and searched for 'ati' and installed few pckages like diplay driver, driver wrapper, kernel module and those automatically selected with these packages. that worked. im getting full 1400x1050 sxga+ display.

please post your results.

thanks
irus

---

### Post by witwicki on 2010-02-17
Can you be a bit more specific?

Currently, I have the following packages installed:

xserver-xorg-video-ati
xserver-xorg-video-radeon
radeontool
xserver-xorg-video-mach64
xserver-xorg-video-r128
fglrx-modealiases
jockey-gtk

in the list of packages that come up by searching for "ati" in synaptic.

Which additional ones do you have marked as installed in your list?

---

### Post by witwicki on 2010-02-17
I figured it out.  I needed to install fglrx-kernel-source.

I'm not quite sure why this fixed the problem, but I'll add this information to the bug report.

Thanks for you help!

---

### Post by irus on 2010-02-17
Most welcome, however desktop effects do not yet work on the laptop, kindly confirm and modify bug report accordingly.

thanks

---

### Post by tgalati4 on 2010-02-18
I'm sticking  with Jaunty on  my  t43p until this is sorted out.  I'm running the open  drivers.

---

### Post by witwicki on 2010-02-18
I've added info to the bug. 


tgalati4,

As of 2-3 months ago, Karmic Kaola was running great on my T43P with the stock drivers.  Though I can't comment on the most recent updates to 9.10 (since I hadn't used this laptop for a while, before doing a clean install of Lucid Lynx Alpha).

---

### Post by irus on 2010-02-18
great lets hope for a quick resolution! ill be following the bug report.

@tgalati its a good idea to keep alpha versions away from production machines! please support the bug on launchpad so it gets assigned faster to some competent coder!

---

### Post by witwicki on 2010-02-18
Ok, thanks to some replies in the bug report ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/522394](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/522394)), there are some workarounds.  Let me summarize and clarify...

1. First of all, that workaround that irus and I used to get the thinkpad display to work was actually using the wrong driver (fglrx-kernel-source) : not intended for the 9600 mobility radeon.  That's why we couldn't get visual affects to work.  So if you want visual effects to work at all, remove the package via "sudo apt-get remove fglrx-kernel-source".

2. A better solution is to load an older version of the appropriate ati driver.  This can be done by booting your ubuntu kernel with the option "radeon.modeset=0".   Test this out by holding down the SHIFT key during the boot process.  You should be confronted with the Grub2 boot menu.   At this point, highlight your "Ubuntu, Linux 2.6.32..."  kernel and press E to edit the boot commands.  Add the text " radeon.modeset=0" without quotes right after where it says "quiet splash".  Then press Ctrl-X to boot.

If you want to make it boot this way everytime, you can change your Grub2 configuration to this effect.  Briefly, "sudo gedit /etc/default/grub".  Change the line that reads:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
and save and close.  Be careful editing this file.  Afterwards, run the command "update-grub".  For more info on Grub2, see [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2).

With this method (2), your thinkpad display should work.  The only problem with this method is that, while visual effects seem to work fine now on just one screen (either the thinkpad screen or a cloned external monitor), there are problems if you use both screens at once.  If, like me, you always have your desktop spread across two monitors, you will see badness when you enable your visual effects.

Irus, can you confirm?

In any case, (2) seems to be an improvement over (1).  There might be hope of this bug getting fixed, so stay tuned for a better solution.

-Stefan

---

### Post by irus on 2010-02-20
@witwicki the solution no.1 also did not last long i'm getting garbled display with multicolored vertical lines now.

also i've tried the latest daily build of 19th feb and this bug is still outstanding!

im using windows7 till this gets resolved.

---

### Post by witwicki on 2010-02-20
> The only problem with this method is that, while visual effects
> seem to work fine now on just one screen (either the thinkpad
> screen or a cloned external monitor), there are problems if you
> use both screens at once. If, like me, you always have your
> desktop spread across two monitors, you will see badness when
> you enable your visual effects.

Update: I discovered that my problems using two monitors with display effects is not an Ubuntu issue per se, but a hardware issue related to my use of too large a virtual screen size.

> also i've tried the latest daily build of 19th feb and this 
> bug is still outstanding!

Irus,

Did you try my solution #2?  As I said, solution #1 uses an incorrect driver. 

Further, in the bug report, I didn't say that the bug was fixed in the latest daily build.  I said that I wasn't experiencing the issue using the mainline build (which is an experimental version of the kernel): [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)
The mainline kernel isn't supported by the Ubuntu development team, so I personally wouldn't recommend it others.  But the fact that it is working here is a good indication that it will be fixed at some point in the Lucid release.

I'm sorry my post in the bug report caused you to try to reinstall Lucid.  I actually didn't reinstall anything.  I installed the mainline kernel alongside the official Lucid kernel (so I can dual boot and play around with both).  See the above link for instructions.

You shouldn't have to resort to W7!

---

### Post by irus on 2010-02-20
i didnt know about the mainline kernels therefore i did a minimal install (12 mb iso) of ubuntu 9.10 to keep things going (windows 7 just doesnt feel right going back to) ;-) 

i did try the #2 method but by then #1 method had failed for me #2 could not salvage anything for the installation!

i will try the mainline kernel, may i ask which of the 5 mainline kernels is everything working ok with? 

besides the big video issue i'm getting intermittent audio problems as well with the default ubuntu installs (both 9.10 and 10.04) therefore have to fall back on windows7 unfortunately.

i'm relieved to hear that this is expected to be resolved!

---

### Post by irus on 2010-02-21
hi witwicki i installed the mainline kernel and the issue is resolved. i'm curious is there a way to have the minimal install cd use the mainline kernel? thanks!

---

### Post by irus on 2010-02-21
ok 9.10 with kernel 2.6.32.14 or 2.6.33.999 seems to have major gnome memory leaks in various components so i decided to move to 10.04 via minimal install cd while on first boot both displays (dual display) worked fine and i got full compiz effects; but the next boot was back to a blank screen. :(

i tried 10.04 with gnome 2.29.90 (to avoid the memory leaks) and latest mainline kernel 2.33.999 while the blank screen problem disappeared and i got compiz effects but the fresh problems which cropped up were 100% cpu usage for some reason and no wireless connection! :(:(

atm 9.10 is usable but things like pulseaudio and gnome settings daemon and volume control applet are leaking too much memory in 2.28. (100-150 mb each). 2.29.90 does seemingly fix these at first look.

now im wondering is there a way to install gnome 2.29.90 straight from minimal install cd or even the desktop of 2.28?

other option would be to hunt for another distro (likely fedora/debian) or go back to windows 7 as i am on right now.

---

### Post by SeePU on 2010-02-21
irus, are you trying Ubuntu 10.04 Alpha 2?   The last time I tried the Live CD, I could boot up okay.  I tried it with a Thinkpad T41 and it has an ATI Mobility Radeon 9000 (RV250).  I can't do the same with 9.10 Karmic.  I have to edit xorg.conf just to boot up or I have to disable desktop effects.  I still don't know what settings I should have in the xorg.conf file.   I thought I'd wait for the Lucid release before I install Ubuntu on it.

---

### Post by irus on 2010-02-22
hi i was using ubuntu 10.04 daily builds. try mainline kernel 2.6.33.999 to see if it solves your problem. it is a good solution suggested by witwicki.

you can also see this for reference [http://ubuntuforums.org/showthread.php?t=1270875&highlight=ati+9600](http://ubuntuforums.org/showthread.php?t=1270875&highlight=ati+9600)

---

### Post by SeePU on 2010-02-22
> **irus said:**
> hi i was using ubuntu 10.04 daily builds. try mainline kernel 2.6.33.999 to see if it solves your problem. it is a good solution suggested by witwicki.
How?   Upgrade 2.6.32 kernel?

Use something like?:  # apt-get install linux-image-x.x.x-xx

---

### Post by irus on 2010-02-22
all details of how to do it are given here 

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

i'm using 9.10 with this kernel 2.6.33.999 but u can use it with 10.04 also in combination with the 2nd solution suggested by witwicki (refer to radeon.modeset=0 post earlier in this topic)

---

### Post by witwicki on 2010-02-23
> **irus said:**
> ok 9.10 with kernel 2.6.32.14 or 2.6.33.999 seems to have major gnome memory leaks in various components so i decided to move to 10.04 via minimal install cd while on first boot both displays (dual display) worked fine and i got full compiz effects; but the next boot was back to a blank screen. :(

i tried 10.04 with gnome 2.29.90 (to avoid the memory leaks) and latest mainline kernel 2.33.999 while the blank screen problem disappeared and i got compiz effects but the fresh problems which cropped up were 100% cpu usage for some reason and no wireless connection! :(:(

atm 9.10 is usable but things like pulseaudio and gnome settings daemon and volume control applet are leaking too much memory in 2.28. (100-150 mb each). 2.29.90 does seemingly fix these at first look.

now im wondering is there a way to install gnome 2.29.90 straight from minimal install cd or even the desktop of 2.28?

other option would be to hunt for another distro (likely fedora/debian) or go back to windows 7 as i am on right now.

I've been using Ubuntu 10.04 (and gnome 2.29.90) for a few days now with the mainline 2.33.999 kernel and haven't experienced any memory leaks or cpu thrashing or wireless problems.

Have you tried to diagnose the cpu problem?  What is the offending process?

For wireless, have you tried toggling Fn-F5?  If that doesn't help perhaps try installing wicd (an alternative to the network-manager).  On a different laptop, I was having a lot of wireless problems and they all went away when I switched to wicd. (sudo apt-get install wicd).

As for tweaking the a minimal install, I'm not sure.  I've never gone that route.  Info on this page might help: [http://knol.google.com/k/ubuntu-minimal-desktop-installation-guide#](http://knol.google.com/k/ubuntu-minimal-desktop-installation-guide#)

---

### Post by irus on 2010-02-24
@witwicki

try the minimal install. with minimal install ive got the full system(as per my requirements) installed and it is consuming only 90 mb ram out of 1.5gb at idle and running very cool at 43-47 C! if u need a quick practical guide ill you know :)

ill try 10.04 again next weekend and see how it goes!

---

### Post by irus on 2010-03-06
update: tried the daily build as of today of 10.04 and compiz is working, dual display is good, wireless is fine and cpu usage is not spiking either! i guess this problem is solved. kindly confirm.

---

### Post by witwicki on 2010-03-12
> **irus said:**
> update: tried the daily build as of today of 10.04 and compiz is working, dual display is good, wireless is fine and cpu usage is not spiking either! i guess this problem is solved. kindly confirm.

I confirm that the display problem is now fixed in Ubuntu Lucid with Kernel "2.6.32-16-generic".  Ubuntu now displays on the laptop monitor without having to alter any settings or drivers.

Note:  I had been running Lucid since Alpha 2, and in order to apply this fix, I had to use the command "sudo apt-get dist-upgrade".  The Update Manager GUI alone did not grab the fix.

---

### Post by oserdavid on 2010-04-24
I've been using Lucid very successfully for a while on my old HP Compaq Nx5000 laptop which has a Mobility Radion display (unfortunately I've not been successful in finding out which, and, confusingly the spec just says: Integrated Intel Extreme Graphics 2 up to 64MB shared system memory). But I've been away for two weeks, and when I came back and updated Lucid - all I got on reboot was a brief, larger than usual splash, which disintigrated into a black screen. Thinking it was a glitch just with one item in update, I've reinstalled 9.10, where the display works just fine, and then run 'update-manager -d' back to Lucid. But still no display at all. No key combination seems to help me to get back to anything I can operate with to download any fixes.

There seem to be some related bug reports, but nothing identical, and some confusion whether they are allegedly 'fixed' or not. Well, they are not for me.

Does anyone have any idea what I can do to fix this, given that I cannot actually seem to get into operating mode with Lucid? Any trick that will get me a text-only display? And then, what should I do anyway, even if I got to text-only?

In the meantime still working with 9.10, and in fear of upgrading again... Ho hum... I was so pleased with Lucid until this uh...regression(?)

Best
David

---

### Post by witwicki on 2010-04-24
> **oserdavid said:**
> I've been using Lucid very successfully for a while on my old HP Compaq Nx5000 laptop which has a Mobility Radion display (unfortunately I've not been successful in finding out which, and, confusingly the spec just says: Integrated Intel Extreme Graphics 2 up to 64MB shared system memory). But I've been away for two weeks, and when I came back and updated Lucid - all I got on reboot was a brief, larger than usual splash, which disintigrated into a black screen. 
...

Does anyone have any idea what I can do to fix this, given that I cannot actually seem to get into operating mode with Lucid? Any trick that will get me a text-only display? And then, what should I do anyway, even if I got to text-only?

In the meantime still working with 9.10, and in fear of upgrading again... Ho hum... I was so pleased with Lucid until this uh...regression(?)

Best
David

David,

Have you gone through this thread and tried the tricks other have used to try to get around the problem?  For instance,

1. Try plugging in an external monitor and rebooting.  I believe that, upon boot, Ubuntu should automatically use the second monitor (cloning the display, or perhaps spreading your desktop across both?).  A few months ago, this was the only way I was able to use Lucid.  Though not ideal, it allowed me to experiment and file a bug report with useful data, and eventually try option #3 below.

2. Try loading your kernel with the option "radeon.modeset=0".  Hold  down the SHIFT key during the boot process.  You should be confronted  with the Grub2 boot menu.   At this point, highlight your "Ubuntu, Linux  2.6...."  kernel (which should be the first entry) and press E to edit the boot commands.  Add the text  " radeon.modeset=0" WITHOUT quotes right after where it says "quiet  splash".  Then press Ctrl-X to boot.

3. Try installing an alternate kernel, specifically the latest "Mainline" kernel (which is completely different from the latest release that you would obtain by updating/upgrading your current install).
See [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) for instructions. 

Hope this helps.  It's unfortunate that you're have problems this close to the official release of Lucid.

-Stefan

---

### Post by oserdavid on 2010-04-24
> **witwicki said:**
> 
1. Try plugging in an external monitor and rebooting.  I believe that, upon boot, Ubuntu should automatically use the second monitor (cloning the display, or perhaps spreading your desktop across both?).  A few months ago, this was the only way I was able to use Lucid.  Though not ideal, it allowed me to experiment and file a bug report with useful data, and eventually try option #3 below.

2. Try loading your kernel with the option "radeon.modeset=0".  Hold  down the SHIFT key during the boot process.  You should be confronted  with the Grub2 boot menu.   At this point, highlight your "Ubuntu, Linux  2.6...."  kernel (which should be the first entry) and press E to edit the boot commands.  Add the text  " radeon.modeset=0" WITHOUT quotes right after where it says "quiet  splash".  Then press Ctrl-X to boot.

3. Try installing an alternate kernel, specifically the latest "Mainline" kernel (which is completely different from the latest release that you would obtain by updating/upgrading your current install).
See [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) for instructions. 

Hope this helps.  It's unfortunate that you're have problems this close to the official release of Lucid.

-Stefan

Thanks Stefan - that's interesting. Item 1, I can't try, no alternative monitor; item 2 did not work (I left 'quiet splash' in place after "radeon.modeset=0" - hope that was right); I will now look at item 3 and let you know what happens. 

But in the meantime I selected the next Ubuntu Linux 2.6... down - and, after a bit of blind fiddling (enter key, escape key - shoulda kept a note -) it loaded. But I'm not quite sure what exactly I have loaded!! Looks like I got 9.10 back again, plus modifications (eg latest Firefox...)- Although the closedown splash is definitely Lucid...and, of course, it won't restart in the normal way.

Nevertheless, many thanks - and I will report back.

Best
David

---

### Post by oserdavid on 2010-04-24
OK Stefan - on rebooting again with shift, then edit mode, I notice that not only did " radeon.modeset=0" not work, but it appeared not to stick - it's gone. Did it again and removed 'quiet splash' - no help (and also did not stick). Starting with the same (ie 2nd one down, not 3rd) Linux version, but in recovery mode, allows me to choose low graphics - which works just fine. I think I'll stick with that until some fix, further down the line, allows me to use normal graphics mode. Your suggestion for item 3 looks like too much hard work for the time being!

You have however been very helpful indeed - so thank you very much.
Best
David

---

