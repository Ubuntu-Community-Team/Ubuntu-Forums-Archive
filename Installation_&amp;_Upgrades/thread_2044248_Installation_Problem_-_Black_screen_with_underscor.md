---
title: "Installation Problem - Black screen with underscore"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by Scorched912 on 2012-08-19
Hello,

I burned Ubuntu 12.04 LTS 64bit on to a DVD and proceeded to reboot in to the install menu, I get up to the Install choice menu, and select 'Install Ubuntu' but after I select that, it just has a black screen with a flashing underscore! This is with nomodeset on, without that on it's just a black screen. :mad:

I used MD5SUM to make sure that it is working and it is all good.
Btw I want to dual boot this alongside Windows 7.
I appreciate any help

- Scorched912

---

### Post by sinukas on 2012-08-19
I am having this same issue on my device-- how can NOMODESET be applied to the normal boot process?

[http://ubuntuforums.org/showthread.php?t=2044147](http://ubuntuforums.org/showthread.php?t=2044147)

---

### Post by Cbjaxx on 2012-08-19
Did you encrypt? Had a similar issue when selecting the encrypt /home folder. I just re- installed since it did not take long and chose not to encrypt during the install and had no issues. Just curious..

---

### Post by sinukas on 2012-08-19
I did not enable any type of disc encryption

---

### Post by oldfred on 2012-08-19
@Scorched912
Welcome to the forums.

I have not tried DVD, but CD or USB have both worked for me. Did you check md5 sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Everyone else, probably best to start your own thead as it gets too confusing to handle multiple issues in one thread. If the OP's issues are identical you can just follow along or show what works.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by Scorched912 on 2012-08-20
Yes I checked MD5SUM and it said it the checksums are the same.
When I burnt it on the DVD-R I made sure verify the disk was ticked, after it burned it said it was done successfully.

I can get up to the little menu that say
- Try Ubuntu without installing
- Install Ubuntu
- Verify disk... thing
etc etc
I press F6 and check nomodeset too. Otherwise if I don't it's only just a black screen no flashing underscore.
I click install Ubuntu and that is where it just stops with a flashing underscore and black background.

Btw when I mean nomodeset 'on' I mean I've checked it with a little X, I've also tried the other options like nodmraid, nolapic and noapic.

---

### Post by Scorched912 on 2012-08-21
Bump.

---

### Post by oldfred on 2012-08-21
Have you tried USB flash or just a CD?

Some have issues with one version or the other and it does not always seem to be a clear issue.

---

### Post by Scorched912 on 2012-08-21
> **oldfred said:**
> Have you tried USB flash or just a CD?

Some have issues with one version or the other and it does not always seem to be a clear issue.

I can try USB flash drive, I'll give that a shot see how that goes. :)

EDIT: Well, I created a bootable flash drive with Ubuntu 12.04 on it, and pretty much same result!, Except this time it's only a black screen.

I boot up from the USB Drive and get up the the menu, I select Install Ubuntu on to a hard disk... then it loads, something idk what but it's a lot of writing, something like what you get when you boot up...

But then it's just a black screen. Could it be my AMD card? Might I have to pull it out when I install Ubuntu? That's what my friend suggested... What do you think?

And I don't have any spare CDs lying around... So I can't try that.

---

### Post by oldfred on 2012-08-21
Is this a dual video system? Those often do have issues. But I do not know AMD systems.

---

### Post by gsudhindra on 2012-08-22
I faced the same problem as well. tried rebooting the system couple of times to start the install all over again, now my system is messed up and not able to boot at all, even with the Win XP.
 
I burned ISO on DVD-R and have AMD too.

---

### Post by Scorched912 on 2012-08-22
Good to know I am not the only one in the same dilemma! And no it's not dual card, just single, it's an Sapphire HD Radeon 7870 Ghz OC Edition.

---

### Post by Scorched912 on 2012-08-23
Bump.

---

### Post by Scorched912 on 2012-08-23
Bumpety bump, any other suggestions?

---

### Post by oldfred on 2012-08-23
The Alternate iso is another option as it does not use the slideshow and is text based.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Some need other settings also:
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Sometimes forcing the generic works:
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)

---

### Post by Scorched912 on 2012-08-23
> **oldfred said:**
> The Alternate iso is another option as it does not use the slideshow and is text based.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Some need other settings also:
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Sometimes forcing the generic works:
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)


Cheers for the links, I'll check em out

---

### Post by cheluna on 2012-09-26
Hi!! I was wondering if you managed to solve your problem. I've been having that black screen issue for a long time. It also happens with other Linux distributions, it's not an Ubuntu issue. It's a real pain in the neck. 
I dislike it because if you are new to linux and you install Ubuntu and get that problem, you will feel disappointed and probably it will discourage you to install or tray it again. :(
So... did you manage? If yes, what did you do? Thank you!

---

