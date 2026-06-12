---
title: "[ARM] Updating to Natty on Toshiba AC100"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by staalmannen on 2011-05-10
Hi all

I am running ubuntu on the Tegra2-based Toshiba AC100, flashed to the internal eMMC (instructions: [http://ac100.gudinna.com/internal/ac100-10D-16GB/](http://ac100.gudinna.com/internal/ac100-10D-16GB/)) and with a 512MiB swapfile.

I really like this machine :)
In accordance with the instructions linked above, I also have a bootable SD card system (far slower), where I can go in as chroot for my eMMC-flashed system if needed (depending on what people suggest).

Yesterday evening I tried to dist-upgrade to Natty but it stopped during installation/configuration at python2.7-minimal.
This package (or python-minimal (default)) seems to be in conflict with a few other packages (unity and some other mystery packages named "ubuntu" something).

I am now at a half-updated system that spits out lots of errors while trying to load the new desktop (X starts, but basically just a purple background). I will try logging in to an alternative DE (LXDE) this evening when I get back from work.

If anyone has experience with this already and know how to get through it I would be grateful :)

---

### Post by staalmannen on 2011-05-10
OK I cheated and downloaded the last maverick .deb:s from my chroot environment. Apparently the problem was that I had not updated before dist-upgrade and python2.7 needed the latest python2.6 package.

I am currently updating and will give an update here if it works. If people from tosh-ac100.wetpaint.co m, kotlett.no or ac100.gudinna.com are reading these forums it might be interesting for them to know how well Natty is working on Tegra2 :)

---

### Post by casbahdk on 2011-05-12
I have been interested in purchasing a Toshiba AC100-10D, but I have been holding off as there seem to be a number of serious, outstanding problems - among them no sound and no Flash. Has there been any movement on sorting out the outstanding issues? There doesn't seem to have been any new developments in the past seven months.

---

### Post by miahfost on 2011-06-04
I would wait a while longer. The software for the AC 100 is not yet mature.

---

### Post by casbahdk on 2011-06-05
Cheers.

---

### Post by pibach on 2011-07-07
Does anybody use the new tegra drivers and can report regarding performance, battery, video playback? Does this work fine?

---

### Post by vickoxy on 2011-07-13
Hi,
i would also like to know if there is some Ubuntu Version working well with AC100? I saw some 10.10 Instructions, but there are lots of Bugs...

Another question: is it possible to upgrade RAM to 1 or 2 GB?

---

### Post by Flymo on 2011-08-02
> **vickoxy said:**
> Hi,
Another question: is it possible to upgrade RAM to 1 or 2 GB?

'Possible', maybe. Practical for me? No.  Ours has a many-legged sub-miniature surface mount RAM soldered in, sadly. No obvious signs of anywhere else to add it. <sigh>

My days of piggy-backing RAM chips and hanging a leg out to select the high order address were over when they stopped using chips whose legs I could see.  Long time ago now.

Your mileage may vary - especially if you know anyone doing SMD rework then they may be able to help.  S'pose I should ask around too, since extra RAM is always good.

---

### Post by louigi600 on 2011-08-20
Ok I got one of these things as a present and here are the things I experienced on it:
Android 2.1 on a netbook without touchscreen is pretty much pointless (I spend 40 minutes fiddling with opera and zoom to read 2 emails from yahoo). Not sure if android 3 is any better on netbooks but in my opinion android is only really menat for smartphones.

I got frustrated with Android and tryed Ubuntu 10.10 following instruction son wetpaint ... I got frustrated with 10.10 too because it crashed too often to do anything usefull on the ac100 and also my usb ethernet dongle did not work properly.
I tried multibooting with kexec enabled 2.6.29 kernel in partition 5 but all I could manage is a amchine halt.
I gave up multibooting and tried natty replacing content on partition 6 for the natty boot kernel.

Unfortunately even after having done an upgrade to latest packages avalible I keep on experiencing touchpad/keyboard jams that keep me from doing anything usefull with the netbook.
It does not do it as often ad it did with 10.10 , and usb ethernet dongle started working but still it's too unstable to use it as an intel based netbook replacement.

Is any one else having these issues with touchpad/keyboard ?
Has anyone any idea how to eliminate or further reduce the issue ?

I See that the ac100 documentation is no longer avalible on Toshiba site. Does it mean that even Toshiba recognizes that this hardware/software recepie is a flop ?

---

### Post by louigi600 on 2011-09-06
> **casbahdk said:**
> I have been interested in purchasing a Toshiba AC100-10D, but I have been holding off as there seem to be a number of serious, outstanding problems - among them no sound and no Flash. Has there been any movement on sorting out the outstanding issues? There doesn't seem to have been any new developments in the past seven months.

It's now 2011 and things have not changed much:
Still audio is not workin and toshiba no longer has the ac100 amongst the products in the home page.
Ubuntu often crashes all onboard input devices in a way that requires a reboot to put things right.
It's unclear how much of the patches for tegra have gotten into vanilla kernel and I've been unable to download sources for the ubuntu 2.6.38 kernel for AC100.
But you can have a number of linux distributions running on the AC100 internal flash now but appart from ubuntu all require setting up a kernel that is not shipped with distro.

The original android is really too restrictive to be of any use so this is what I've done with my AC100:
Custom kernel and initrd (modified from ubuntu 2.6.38 image) in partition 5 (HOME + POWER) to boot ARMedslack on internal eMMC,
Ubuntu natty on SD card booting from partition 6 (ordinary boot).

---

### Post by pibach on 2011-09-12
> **louigi600 said:**
> It's now 2011 and things have not changed much:
Still audio is not workin 

here is stated that, according to which kernel you are using, most of the HW is now supported: 
[http://linad.org/index.php?title=Toshiba_AC100#Issues](http://linad.org/index.php?title=Toshiba_AC100#Issues)

And here is a howto from markit to uprade to Natty:
[http://markit.dyndns.org/ac100/32/howtos/upgrade_to_natty.txt](http://markit.dyndns.org/ac100/32/howtos/upgrade_to_natty.txt)

And here is a PPA so that kernel updates etc should work.

I did not test is myself yet but most features such as HW acceleration, flash, sound, and suspend seems to work. Isn't it?

---

### Post by freechelmi on 2011-09-19
> **pibach said:**
> 
I did not test is myself yet but most features such as HW acceleration, flash, sound, and suspend seems to work. Isn't it?

Just tested the 11.10 daily rootfs : Works great apart from sound and HW acceleration.

---

### Post by pibach on 2011-09-19
Is suspend/resume working? And does WLAN reconnect after suspend? This is the bigges downfall of the rom I am currently using (Markus' patched pph's 2.6.32 kernel).

---

### Post by freechelmi on 2011-09-20
> **pibach said:**
> Is suspend/resume working? And does WLAN reconnect after suspend? This is the bigges downfall of the rom I am currently using (Markus' patched pph's 2.6.32 kernel).

Nope , it just stays stuck when you try to suspend .....

---

### Post by pibach on 2011-09-27
I switched to the daily rootfs Ubuntu Oneiric image and did some tests. I moved away from Unity and installed lubuntu-desktop. After latest updates of today, including a new kernel. It runs fast and reliable. 

Still some issues:

* flash doesn't work as explained in the ac100 Wiki by just downloading libflashplayer.so to the plugin folder. Seemingly it is not recognized
* no suspend (it actually does suspend with flashing power light but the does not wake up afterwards)
* no sound via speakers

Lubuntu makes it a fantastic little companion. I appreciate the responsiveness. For example, scrolling in Firefox or Chromium is much faster compared to Ubuntu (although I could see a good performance on Gnome+Openbox). Plus offers all the goodies of a fully fledged distro.

---

### Post by Brendantb on 2011-10-03
Hi, 

I have a Toshiba AC100 on which I would be keen to install Ubuntu. Does anyone know if the suspend and resume issue will be sorted out soon? That is the only thing holding me back at the moment.

---

### Post by pibach on 2011-10-03
> **Brendantb said:**
> Hi, 

I have a Toshiba AC100 on which I would be keen to install Ubuntu. Does anyone know if the suspend and resume issue will be sorted out soon? That is the only thing holding me back at the moment.

Actualy it is already sorted. Problem was old parameter of Ubuntu invoking the kernel. There are two ways to fix:

a) use old android 2.1 bootloader, this does seemingly ignore the parameter. 
b) change that parameter (delete)

Then you get suspen/resume fully working.

All news and links are collected here:

[http://ac100.grandou.net/start](http://ac100.grandou.net/start)

Enjoy! Peter

Edit:

For those who speak German: I have collected a huge amount of all infos around AC100 with install guide and much more on my wiki here: [http://wiki.informatik.hu-berlin.de/nomads/index.php/Erfahrungsbericht_Toshiba_AC100](http://wiki.informatik.hu-berlin.de/nomads/index.php/Erfahrungsbericht_Toshiba_AC100)

---

### Post by Brendantb on 2011-10-08
Hi, 

I installed Oneiric on the AC100 today. However, I didn't manage to change the lp0_vec in the bootimg.cfg file, and the machine won't wake from sleep. Can I edit this string now? Is it just a matter of commenting out the beginning of the line? 

I also tried to download Skype from their website, but it wouldn't install, warning that I had the wrong architecture version: i386. 

Has anyone got Skype to work on Ubuntu for Arm? 

Thanks,

---

### Post by freechelmi on 2011-10-08
> **Brendantb said:**
> Hi, 

I also tried to download Skype from their website, but it wouldn't install, warning that I had the wrong architecture version: i386. 

Has anyone got Skype to work on Ubuntu for Arm? 

Thanks,

Isn'it obvious that skype won t work on ubuntu other than x86?

---

### Post by pibach on 2011-10-08
skype: There might be some port of the Meego version of skype. But until now it doesn't work.

Suspend: remove lp0_vec option from cmdparam line in /boot/bootimg.cfg
Editing the parameter for suspend is quite simple, just delete, save and update&upgrade and abootimg will put new image in place.

---

### Post by Brendantb on 2011-10-29
Thank you for your advice. I've had Ubuntu running for a couple of weeks now, and it is now stable and functional; I can email, use the software update, and have Abiword running. There are no longer any crashes, especially with the updater. 

However, I still don't have any sound or alert sound, even from a fresh start-up. Sometimes closing the lid will not put the unit into suspend. Adobe flash doesn't work in Firefox, despite putting the Adobe files in /.mozilla/plugins as recommended in the wiki. 

All in all, though, it is now much more functional than the android implement on the original. 

My thanks to all those who helped in making the port to Arm. 


Brendan

---

### Post by pibach on 2011-10-29
I do recommend LXDE over Unity.
Flash works in Chromium, which is also faster.
Newer Firefox version should work with flash as well (did not test).
For sound use newer kernel, from Oneiric proposed.
Lid close event is not stable yer. But just put suspend on a hotkey.

---

### Post by maureenc on 2012-03-13
Not sure If I am allowed to add to a Solved Thread but people may still be tracking this so here goes:

Installing "session-fallback" enables Gnome Classic at login..... Much, much more useable than Unity and not quite as drastic as the move to Lubuntu/LXDE! I though about that Pibach and chickened out when I saw the list of commands to remove and update packages.... Scarey when I don't feel that secure at doing it.

I have a feeling that the lid-closing problem lies with the fact that the login screen doesn't come up when it is opened.... Normal Suspend/Resume brings this up and all is well.

I still can't get Flashplayer to work..... Have ditched the bloated Firefox because the rapid versioning is preventing addons and extensions from working.... To do with the Extensions.checkCompatibility.....

Don't like Chrome and hate the way it tries to track everything I do......Don't want to be that close to Google!

Midori works beautifully, has Speed dial..... But can't get Flashplayer working there either...... Despite your wonderful Instruction Manual Pibach!

---

