---
title: "Ubuntu will not install using any method"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by Muramasa on 2012-02-17
I have been trying to install Ubuntu for awhile now with no luck no matter how i attempt it, i have attempted to install it from a CD, USB stick and also running it from windows using Wubi, each failing to work in different ways.

**CD:**

when attempting to burn the CD using the Windows disc image burner i get the following message after the disc has been created:

"the disc image didn't burn successfully because an error occurred. the disc did not pass burn verification and may contain corrupt data or be unusable. (error code: 0xC0AA0007)" 

**USB:**

after following the instructions i had no problems putting Ubuntu onto a USB stick, however after booting from USB i get a black screen with the following message:

"SYSLINUX 4.02 2010-07-21 EDD Copyright (C) 1994-2010 H. Peter Anvin et al"

once this message appears i am unable to do anything.

**Wubi:**

i had no problems setting up Ubuntu using the Wubi windows installer, however after rebooting the computer and selecting Ubuntu at start up i am presented with a blank purple screen for about 30-40 seconds, after this i get a black screen (unlit as far as i can tell).

i am running windows 7 (64-bit) and attempting to install Ubuntu 11.10, please ask if you need any other information.

if you could provide some help to fix even one of these methods it would be a huge help, thanks in advance :)

---

### Post by wolfen69 on 2012-02-17
> **Muramasa said:**
> 
"the disc image didn't burn successfully because an error occurred. the disc did not pass burn verification and may contain corrupt data or be unusable. (error code: 0xC0AA0007)" 

Try burning at a slower speed, and use a different disc if possible.

---

### Post by bcbc on 2012-02-17
Try [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, I'd run an md5check on the ISO you downloaded  - it sounds like it isn't good. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Other than that, follow the instructions from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (step 2, select cd/usb, then click 'show me how')

---

### Post by Muramasa on 2012-02-17
Thanks for the fast response :)

The burn speed was set to fastest, after attempting to burn the disc slowly it still failed however this time i have received a different message

"The disc image didn't burn successfully because an error occurred. The write failed because the drive returned error information that could not be recovered from. (error code: 0xC0AA0301)"

I have been looking into the MD5check quite abit today, however if im honest i dont really understand exactly how to do the check, even after reading that link you provided.

As for the instructions you provided for making a CD/USB they are the same instructions i am already using :)

---

### Post by bcbc on 2012-02-17
The blank screen sounds like a graphics card issue - try that wubi install with the nomodeset override since it's already installed. Even once you get the CD/USB you'll need the same graphics workaround.

---

### Post by Muramasa on 2012-02-17
Okay, its currently 4:15am so i will pick this up again tomorrow, however some progress has been made.

after following the instructions on post #8 of the nomodeset link you provided i managed to boot into Ubuntu (wubi), however this is only for the first boot, as the link you provided says.

i wanted to test if it is a graphics card issue so after rebooting the computer and getting the same blank purple screen (completely blank) followed by a black screen i typed in the password and could hear the login theme that plays.

any help on what to do next would be a big help :) 

thanks in advance and ill check back in the morning.

---

### Post by bcbc on 2012-02-17
> **Muramasa said:**
> Okay, its currently 4:15am so i will pick this up again tomorrow, however some progress has been made.

after following the instructions on post #8 of the nomodeset link you provided i managed to boot into Ubuntu (wubi), however this is only for the first boot, as the link you provided says.

i wanted to test if it is a graphics card issue so after rebooting the computer and getting the same blank purple screen (completely blank) followed by a black screen i typed in the password and could hear the login theme that plays.

any help on what to do next would be a big help :) 

thanks in advance and ill check back in the morning.
Okay that post #8 works for the wubi 1st boot (install) but then after that you need to override it one more time for the normal boot (see post #1 - it says 'not for wubi' but it's the same after installing). Then once you have it running, look for 'additional-drivers' and install the graphics card driver.

As I said, you'll also need this later for when you want to install with the CD/USB.

---

### Post by Muramasa on 2012-02-18
Okay after following the instructions for permanently setting the boot options and restarting i still get the same problem (purple screen followed by a black screen) 

i also can not find any graphic drivers (or any drivers) when looking for additional drivers.

EDIT: i just tried plugging in an external monitor and i am able to see the screen fine, not fixing the problem, but at least i have access now.

i have also just noticed that it must be a back light issue, as in a well lit room i am able to just about see the laptop screens display, i have tried increasing the brightness level but it did not help.

---

### Post by Muramasa on 2012-02-18
Bump.

---

### Post by Muramasa on 2012-02-18
I have found a strange workaround for the back light issue, if i adjust the back light during the boot process it will stay on when Ubuntu starts.

---

### Post by bcbc on 2012-02-18
Do you have an intel graphics card? (full specs: brand/model/graphics card(s)). That will help narrow it down.

There were backlight issues with some intel cards - my one was stuck on full bright, some people had the backlight stuck off. Hopefully running all possible updates will fix it, otherwise there is likely some instructions or maybe even a PPA to workaround the problem.

---

### Post by Muramasa on 2012-02-18
It is an Intel chip, windows device manager lists it as "Mobile Intel 4 Series Express Chipset Family"

as i posted before i have found a strange workaround to the back light problem, i can get it to stay on if i adjust the back light during boot up, i can also plug an external monitor into the laptop and it displays perfectly.

---

### Post by bcbc on 2012-02-18
Okay - I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893)

It seems you'll have issues if you suspend etc. This bug is on Natty (11.04) but it sounds like it hasn't been resolved yet (someone mentioned it's still present on the development release - 12.04 so likely the same on 11.10).

---

### Post by MAFoElffen on 2012-02-18
> **bcbc said:**
> Okay - I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893)

It seems you'll have issues if you suspend etc. This bug is on Natty (11.04) but it sounds like it hasn't been resolved yet (someone mentioned it's still present on the development release - 12.04 so likely the same on 11.10).
Look under the Laptop Section of the first post of my sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 
> 
Steps:
1) edit rc.local     
```

gksudo gedit /etc/rc.local

```2) Add the command before EXIT 0
```

setpci -s 00:02.0 F4.B-0

```3) Reboot.

Works for 11.04, 11.10 and 12.04. Sets the brightness settings to the brightest setting during boot up.

Also, a high percentage of laptops that have this problem also seem to have the function/hot-keys for dimming/brightening the screen- reversed. This is true for one of my 4 laptops.

---

### Post by Muramasa on 2012-02-19
Okay, i have added that command to rc.local, however after saving and closing the following appears in the terminal:

(gedit:2688): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7SYDAW': No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.CG0Z9V': No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GK509V': No such file or directory

(gedit:2688): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

----

I have also checked the downloaded Iso with MD5SUM, and everything matched perfectly.

---

### Post by Morozov on 2012-02-19
Hi,
Sorry I miss the part, did you manage to install Ubuntu or still strugling with installation from CD ? If you failing on installing from CD install image to USB using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
I've had not long time ago same problem some mirrors in Ubuntu crashing iso when putting them on CD. I've install 64bit 11.10 first option to try without installing then when Ubuntu loaded install drivers for network card if will not be recognized, then when connected to the network (do not do reboot as sejested) do installation from there
Regards

---

### Post by Muramasa on 2012-02-19
I have finally been able to get Ubuntu onto a disc (currently running Ubuntu from that disc) by using Ubuntu (wubi) to burn the disc rather than windows, i ran the md5check on the ISO and the disc after it was created, all the hashes matched perfectly.

So i now have Ubuntu on a disc, i am not too sure what to do next, i could install Ubuntu now from this disc, however its not really worth it without a permanent fix for the back light issue.

Do you think i would get the same problem that i posted in post #15 if i tried it on a full install rather than using the Wubi install?

---

### Post by MAFoElffen on 2012-02-19
You said you could do this:
> **Muramasa said:**
> I have found a strange workaround for the back light issue,[COLOR=Red] if i adjust the back light during the boot process it will stay on when Ubuntu starts.[/COLOR]
With that, you could install... Did you?

With people that can't do that, I tell them to use "Try", then use an external monitor, use a flashlight or other light to see their screen (if a backlight is turned off) until they can get to a desktop session... Where there they can open a terminal session and enter:
```

autorun "setpci -s 00:02.0 F4.B=00"

```The screen setting would then be set to it's brightest setting- temporarily. (It would now just be in memory until reboot.) They could then install from the desktop normally...

Then after the install and the subsequent reboot, they would again have to use those workarounds until they get to the desktop of the installed system, where they could apply the fix I posted.

The fix I gave in the earlier post is applied once the system is installed... Which I assumed when you said you had with the above workaround.  If you try to apply it on the Live Image of the LiveCD or LiveUSB, they are not persistent and you would get the errors you got.  I am assuming that is what you did to receive those errors. Otherwise the error would have been a permissions problem of creating a recently used file tag in your own user home directory and not that of the live image filesystem's directory structure... ??? 

Is that what happened?

---

### Post by Muramasa on 2012-02-19
The only install of Ubuntu i have is from Wubi, as i was not able to get Ubuntu on disc or boot from USB, that is what i was using when i received those errors.

Since then i have been able to get Ubuntu on a disc and i can now install, after i do install Ubuntu from the disc your fix should work, correct?

---

### Post by Morozov on 2012-02-19
Are you able to boot from this disk? There will be boot menu, you can choose try Ubuntu. By doing so you'll load OS then with desktop up and running check propritary drivers then you can continue with installation, just a sejestion to partition drive creating /home partition (your document folder) (it will be easy to do upgrages later. New 12.04 LTS will be available soon)
Regards

---

### Post by Muramasa on 2012-02-19
I can boot from the disc, yes.

i am currently running Ubuntu without installing, viewing the screen on an external monitor, i have opened a terminal and input this code: (exactly how it looks in the terminal)

```
ubuntu@ubuntu:~$ autorun "setpci -s 00:02.0 F4.B=00"
```however i am told the command is not found.

---

### Post by Morozov on 2012-02-19
You won't be able to see because ubuntu is not installed on your hasd drive yet. Sorry if I ask to go back a little (trying to figure out what went wrong that you are on external monitor. Correct me here... Let say you had windows installed and it was working, then you got image from web and tyed to install from CD booting from CD (direct install)?, then I gues you crash few times trying diffent way to install Ubuntu?...
Can you still go back to Windows and you have you monitor up and running as it was?
Regards

---

### Post by MAFoElffen on 2012-02-19
> **Muramasa said:**
> The only install of Ubuntu i have is from Wubi, as i was not able to get Ubuntu on disc or boot from USB, that is what i was using when i received those errors.

Since then i have been able to get Ubuntu on a disc and i can now install, after i do install Ubuntu from the disc your fix should work, correct?
Yes.

As for the last poster's comment- On the upcoming 12.04 LTS, I'm testing dev 12.04 alpha2 now. We are all trying to break it, find work-arounds, submit bugs and other data so that patches and fixes can be implemented. Some changes make things work because the kernel is newer.  As I'm also on the Linux Kernel Dev List- My understanding on what is going on with laptop issues- Around 11.04, a lot of graphics changes and other things shifted to the Kernel.  APM and other Laptop specific functions started shifting there (backlighting was one). ACPI was to take on the brunt of those past functions. About v3.2.x started with some improvements from lessons learned. Parallel to this, the newest XServer-xorg has up-to-date Intel Video support (Intel shares its linux opensource video driver code with Xorg) and I'm testing that new version of XServer now. Neither of those are officially released yet and both are upstream changes to Ubuntu.  So at the moment, saying that 12.04 LTS will fix all ills may be premature.  I'm still hopeful that it comes close...  

I always figure any release of any Operating System is a snapshot of what is current and best at that point in time. After a release, the development and work on patches and fixes continue onward. I think after we finished testing 11.10 the night before release, it was released... and we were already testing for 12.04 3 days later.

---

### Post by MAFoElffen on 2012-02-19
> **Muramasa said:**
> I can boot from the disc, yes.

i am currently running Ubuntu without installing, viewing the screen on an external monitor, i have opened a terminal and input this code: (exactly how it looks in the terminal)

```
ubuntu@ubuntu:~$ autorun "setpci -s 00:02.0 F4.B=00"
```however i am told the command is not found.
What happens if you instead use:
```

sudo setpci -s 00:02.0 F4.B=00

```But that would be unneeded. You said you got there using an external monitor... Why is it that you are not continuing to install from there? You see the screen right?

EDIT-- If this was on chat/IM this might be shorter fix...

---

### Post by Muramasa on 2012-02-19
Nothing at all happens when i try that code.

The reason i have not yet installed Ubuntu is because i wanted the back light issue sorted first, however i will install now, ill post back after i have installed and tried a few fixes posted here.

---

### Post by Morozov on 2012-02-19
MAFoElffen, 
 
I so you are testing Xorg, can you please check my post
**Dell Studio xps 1340 HDMI not visible**
[COLOR=black]I'm strugling[/COLOR] to get HDMI port working so may be with the next 12.04 I'll get my video card working as it should (was under win7)
regards
Alex

---

### Post by MAFoElffen on 2012-02-19
> **Morozov said:**
> MAFoElffen, 
 
I so you are testing Xorg, can you please check my post
**Dell Studio xps 1340 HDMI not visible**
[COLOR=black]I'm strugling[/COLOR] to get HDMI port working so may be with the next 12.04 I'll get my video card working as it should (was under win7)
regards
Alex
Coild you please post the link to it?

---

### Post by Muramasa on 2012-02-19
Okay i have installed Ubuntu now, the second code you gave me works fine, allowing me to see the screen. however i have tried following the instructions in post #14 but still get errors, very similar to those i posted.

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HS819V': No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GDWY9V': No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by Morozov on 2012-02-19
My post link
[http://ubuntuforums.org/showthread.php?p=11700979](http://ubuntuforums.org/showthread.php?p=11700979)

---

### Post by MAFoElffen on 2012-02-19
> **Muramasa said:**
> Okay i have installed Ubuntu now, the second code you gave me works fine, allowing me to see the screen. however i have tried following the instructions in post #14 but still get errors, very similar to those i posted.

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HS819V': No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GDWY9V': No such file or directory

(gedit:1830): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
So it let you open the file, make changes, save changes, then exit... then you saw those messages in the terminal session.

If you opened that file again, are those edits there? I suspect yes. If so, then ignore it.  I use console a lot and see warnings exiting gedit.  I don't even pay attention to them anymore.

But the proof really should be to reboot it and see if it works.

---

### Post by Muramasa on 2012-02-19
Correct, however after rebooting the back light remains off, any ideas?

---

### Post by MAFoElffen on 2012-02-20
> **Muramasa said:**
> Correct, however after rebooting the back light remains off, any ideas?
did you look at /etc/rc.local and see if those edits are there?

---

### Post by Muramasa on 2012-02-20
I looked in the Rc.local file and the edit is there, however i also noticed the code in rc.local was different to the code i can run in the terminal to set the brightness, so i changed this code:

```
setpci -s 00:02.0 F4.B-0
```for this code:

```
setpci -s 00:02.0 F4.B=00
```I still get those error messages in the terminal, however i will ignore them as after a reboot it seems to have worked fine, but after resuming from sleep mode the back light will once again be off, is the code not correct?

---

### Post by Muramasa on 2012-02-20
bump

---

### Post by bcbc on 2012-02-20
Check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893/comments/5)

---

### Post by Muramasa on 2012-02-20
Could you explain a little what im supposed to do with the code in that post?

i have tried afew things but i cant get it to work =/

---

### Post by MAFoElffen on 2012-02-20
@ the OP, yes the code is now right. Sleep/Waking a separate issue. Good job on "bcbc" finding a work-around on that.  
> **bcbc said:**
> Check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740893/comments/5)
That script looks solid... which saws that when the PC comes out of  hibernate or resume, to use the same previous posted code settings to turn the backlight on...

Instructions on that: 

Create a file and open it for edit
```

gksudo gedit /etc/pm/00_video

```Paste this code into it
```

#!/bin/bash

# Hibernate/Suspend Wake Fix
# Credit to talessx (alessandro-tassi)
#

case "$1" in
    hibernate|suspend)
         ;;
    thaw|resume)
        setpci -s 00:02.0 F4.B=00
        ;;
    *)
        ;;
esac
exit $?

```Then make it executable
```
[FONT=monospace]
[/FONT]
sudo chmod +x /etc/pm/00_video

```I'll contact the author to see If I could repost it in my Sticky...

---

### Post by Muramasa on 2012-02-20
Thanks for the instructions, slight problem when i try the code to create/edit, it asks me for my password as normal, but nothing opens after that.

---

### Post by bcbc on 2012-02-20
Try:
```
gksudo **gedit** /etc/pm/00_video
```

Edit: actually I'd create it under sleep.d:

```
gksudo **gedit** /etc/pm/sleep.d/00_video
```

Seems to work either way according to that bug report but this seems like the right place

---

### Post by MAFoElffen on 2012-02-20
> **bcbc said:**
> Try:
```
gksudo **gedit** /etc/pm/00_video
```Edit: actually I'd create it under sleep.d:

```
gksudo **gedit** /etc/pm/sleep.d/00_video
```Seems to work either way according to that bug report but this seems like the right place
LOL, Yes, I edited my first post... went back and saw you had caught it already.

Great job. Please go up to the thread tools and marks this thread as "Solved".

---

### Post by Muramasa on 2012-02-20
Okay i created it in Sleep.d and the back light now turns on after suspending :) thank you all for the help.

i just have one more question, if in the future i update to a new version of Ubuntu will i have to apply all these fixes again? (if the problems are still present in the new version)

---

