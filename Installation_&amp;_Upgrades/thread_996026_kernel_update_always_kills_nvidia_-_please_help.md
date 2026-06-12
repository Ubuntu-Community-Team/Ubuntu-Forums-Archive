---
title: "kernel update always kills nvidia - please help"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-11-28
I'm running Hardy. For the past 6 months, on every kernel update, I have a problem with my nvidia driver. This should not be happening, but I cannot figure out a permanent resolution. Here is how I resolve the issue after each kernel update:
[LIST=1]
[*]update manager notifies me of a kernel update & I install it
[*]restart the computer
[*]upon bootup I'm notified that **_Ubuntu is running in low graphics mode!_**
[*]I choose continue and login
[*]I start EnvyNG & provide sudo password
[*]EnvyNG installs drivers using automatic hardware detection
[*]this time Envy installed 3 new packages: nvidia-glx-new-envy, -dev-envy & -kernel-source-envy
[*]the operation completes and I'm back in business
[/LIST]

According to the EnvyNG FAQ, I should not have to do the above. I left a question on Alberto's blog about 4-6 months ago and didn't get a response. Can anyone here help me?

[http://albertomilone.com/envyngfaq.html#F](http://albertomilone.com/envyngfaq.html#F)
**F) What happens if the kernel is upgraded (e.g. via system updates)?**

[INDENT]You won't have to do anything at all. DKMS will automatically install the module for your new kernel. NOTE: make sure that the kernel headers (linux-headers) for that kernel are also installed. [/INDENT]

---

### Post by MountainX on 2008-11-28
I sent Alberto and email and he responded instantly. I will keep this thread updated as I proceed to work on this. 

[INDENT]Alberto said:
If you use the -generic kernel you will have to install "linux-headers-generic" (or linux-headers-server if you use the -server flavour) so that the relevant headers are installed every time the kernel is updated.[/INDENT]

I do have "linux-headers-generic" installed. See below. 

~$ uname -r
2.6.24-22-generic

~$ dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.24.22.24
Depends: linux-headers-2.6.24-22-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.

---

### Post by steveneddy on 2008-11-28
Just install the nvidia driver from the repos and you won't have that issue.

I know that on your system you can tell the difference, but I can't on my laptop.

I don't game, though, so maybe my opinion doesn't count in this argument.

I do watch a lot of movies on my laptop and they look great full screen.

---

### Post by MountainX on 2008-11-28
The problem does not seem to be caused by EnvyNG. Envy is just the quickest way to resolve it each time I update my kernel. I had the same problem when I used the other two nvidia drivers I tried (the one from the repos and the one directly from nvidia).

---

### Post by wandalalakers on 2008-11-29
My kernel was updated either last night or this morning to 2.6.24-22 generic.
I had envyng 173.14.12 working with 2.6.24-21 but it won't work with 2.6.24-22.
I'm reinstalling envyng 96.43.05 to see if it will work with 24-22.

---

### Post by wandalalakers on 2008-11-29
Manually installing 96.43.05 using envyng fixes my booting problem.  I'm not sure why 173.14.12 doesn't work anymore but I'm in business again.  The envyng driver is the only one that will work with my opengl screensavers.  In the past, the one from the repos wouldn't work with my opengl screensavers.

---

### Post by MountainX on 2008-11-29
> **pcdoctor said:**
> My kernel was updated either last night or this morning to 2.6.24-22 generic.
I had envyng 173.14.12 working with 2.6.24-21 but it won't work with 2.6.24-22.
I'm reinstalling envyng 96.43.05 to see if it will work with 24-22.

envyng 173.14.12 is working with 2.6.24-22 for me. I just don't like having to manually reinstall the driver after kernel updates, but I guess that's better than the problem you had.

---

### Post by MountainX on 2008-11-29
btw, i'm still looking for help. thanks

---

### Post by markbuntu on 2008-11-29
The problem is that envy does not remove the nvidia kernel modules from the previous driver when it installs the new one so when the new kernel tries to build it sees multiple module versions and so does not install any and leaves it up to you to do it manually which is the best that can be expected. 

You will see a message to this effect if you watch the terminal while the new kerne is installing. The best way to avoid this in the future would be to remove all the old nvidia driver kernel modules.

It is the same with the ati fglrx drivers.

After all, they are "unsupported".

---

### Post by MountainX on 2008-11-30
> **markbuntu said:**
> The problem is that envy does not remove the nvidia kernel modules from the previous driver when it installs the new one so when the new kernel tries to build it sees multiple module versions and so does not install any and leaves it up to you to do it manually which is the best that can be expected. 

You will see a message to this effect if you watch the terminal while the new kerne is installing. The best way to avoid this in the future would be to remove all the old nvidia driver kernel modules.

It is the same with the ati fglrx drivers.

After all, they are "unsupported".

This faq seems to contradict what you are saying: [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

And what do you mean by "unsupported"?

---

### Post by markbuntu on 2008-11-30
All I know is that ENVYng never worked properly for me and caused problems with leftover kernel modules during kernel upgrades.

"unsupported" by definition means packages not directly available in the Ubuntu repositories. While Envyng may be supported the drivers it installs may not be. This means that accomodations for them are not necessarily included by other teams, like the kernel update team.

---

### Post by MRGt on 2008-12-02
> **markbuntu said:**
>  **The best way to avoid this in the future would be to remove all the old nvidia driver kernel modules**.

It is the same with the ati fglrx drivers.

After all, they are "unsupported".

How can i do that?

Remove the old nvidia driver kernel modules?

is there some How To?

---

### Post by MountainX on 2008-12-04
I'm still unable to solve my problem. How can I get help? I'm even willing to pay for a support ticket or something in order to get help. I tried contacting Canonical and I got no response. 

Maybe I should reinstall from scratch. I'm even thinking about getting a new motherboard because I have the USB-2.0 bug too. It sure would be nice to solve all my outstanding issues (I have about a dozen of them I cannot solve). Anyone want to earn a few bucks helping me?

---

### Post by jerrykenny on 2008-12-04
If its such a big problem, you mark your current kernel (assuming it HAS got nvidia working) as being manually installed.

And deselect linux-kernel-generic.

As linux kernel generic depends on the latest available kernel etc, it will always be replaced every time there is a new kernel.

I dont use ENVY or module assistant, but "usually" kernel upgrades are fine for me

---

### Post by jerrykenny on 2008-12-04
Whats also handy, is to make an almost-carbon-copy of your xorg.conf file and save it as 

xorg.conf.failsafe

BUT  !   you must change the driver from "nvidia" to "nv" . . . .and comment out "#" the "load glx" entry in modules.

If you then have a good working xorg.cof.failsafe, then in future when nvidia borks again (sigh) you'll at least still have good working resolution and a comfortable environment in which to do your troubleshooting

---

### Post by sdennie on 2008-12-05
If you know how to install the drivers directly from the nvidia website, do that and then follow this guide (only test on 8.04) to have them automatically update after new kernel releases: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by MountainX on 2008-12-05
> **vor said:**
> If you know how to install the drivers directly from the nvidia website, do that and then follow this guide (only test on 8.04) to have them automatically update after new kernel releases: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

Thank you. Yes, I have installed the drivers directly from the nvidia website before. It isn't hard.

Your HOWTO looks great! Thanks for sharing it.

Theoretically, I now have two options for installing the latest nvidia drivers (your method and EnvyNG) and both should support upgrading the kernel easily. 

I will try your method, and it may be the best for me because it gives me complete control and it is easy to understand.

But I still wonder what is making EnvyNG not work correctly for me when it appears to work for most people. Looking back at the EnvyNG FAQ, we have this entry:

[http://albertomilone.com/envyngfaq.html#F](http://albertomilone.com/envyngfaq.html#F)
F) What happens if the kernel is upgraded (e.g. via system updates)?

    "You won't have to do anything at all. DKMS will automatically install the module for your new kernel. NOTE: make sure that the kernel headers (linux-headers) for that kernel are also installed."

---

### Post by tseliot on 2008-12-05
The problem is described [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816").

I provided a fix but it looks like the packages are still in the hardy-proposed repository. Only one person wrote to confirm that the fix solves the problem. Please try the driver in hardy-proposed and report either success or failure [there]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816"). The more the reports the sooner the fix will enter the stable repository.

---

### Post by MountainX on 2008-12-05
> **tseliot said:**
> The problem is described [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816").


Thank you!

Here are my steps:
Synaptic Package Manager -> Settings -> Repositories -> Updates, Checked "Pre-releasedd updates (hardy-proposed)" and closed dialog.
Searched for "envy" in Synaptic Package Manager.
Selected & marked for upgrade the following:
1. NVIDIA binary XFree86 4.x/X.Org 'new' driver development files
2. NVIDIA binary XFree86 4.x/X.Org 'new' driver
3. NVIDIA binary 'new' kernel module source
Applied.
Then changed repository settings back to the original.

Upon the next kernel update I will report whether my original problem is solved.

---

### Post by MountainX on 2009-02-02
> **MountainX said:**
> 

Upon the next kernel update I will report whether my original problem is solved.

Today I updated to 2.6.24-23-generic. It seems my problem is resolved. :)

---

