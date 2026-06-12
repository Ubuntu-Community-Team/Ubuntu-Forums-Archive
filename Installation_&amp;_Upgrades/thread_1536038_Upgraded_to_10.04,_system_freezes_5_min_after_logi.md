---
title: "Upgraded to 10.04, system freezes 5 min after login"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by muzincs on 2010-07-21
I cannot stop the X server either, I have to restart the computer.  

It is a 3-year old Dell Optiplex 745 with an 82Q963/Q965 Intel Integrated Graphics Controller.  (I think this is the source of the problem.)

I booted it in safe mode and the root shell prompt is blinking away.

Help, please!

---

### Post by davidmohammed on 2010-07-21
try booting with either i915.modeset=1 or i915.modeset=0 as your grub boot option.

---

### Post by muzincs on 2010-07-21
Do I add i915.modeset=1 as a separate (5th) line after "quiet"?  (Sorry, I've never dealt with grub boot options before..)

---

### Post by davidmohammed on 2010-07-21
add the option BEFORE quiet splash...

the line should read something like

..... i915.modeset=0 quiet splash --

---

### Post by muzincs on 2010-07-21
Now it freezes in under a minute.  :(
Any other ideas?  Should I remove that option from grub?

---

### Post by davidmohammed on 2010-07-21
editing grub is a temporary thing - you'll notice the next time you boot the boot option has vanished.

Have you tried  booting with i915.modeset=0 and i915.modeset=1 (not both together :D )?

---

### Post by muzincs on 2010-07-21
No, I tried with =0 only...  Will try =1 (and you are forgiven for the cautionary parenthetical comment :) ).

---

### Post by davidmohammed on 2010-07-21
... its possible that some other component other than your graphics is causing your issue.

you could try the following boot options (i.e. options can be entered together BEFORE quiet splash)

i915.modeset=0 noapic
i915.modeset=0 nolapic
i915.modeset=0 noapic nolapic
i915.modeset=0 noacpi
i915.modeset=0 acpi=off

---

### Post by muzincs on 2010-07-21
i915.modeset=1 does not fix it.  I'll try these other ones.  If one of them does fix the problem, what do I do then?  (I ask because the options vanish...)

---

### Post by davidmohammed on 2010-07-21
type in a terminal

sudo nano /etc/default/grub

add your boot parameters to GRUB_CMDLINE_LINUX

save

sudo update-grub

---

### Post by muzincs on 2010-07-21
Great.  Thanks.  Will keep working on it and post back if it is fixed.

---

### Post by muzincs on 2010-07-22
I tried all the permutations suggested but the problem persists.
Does anyone have another idea of a possible fix?  Downgrade to the 2.6.31 kernel?  If yes, how is that done?
Help, please!

---

### Post by muzincs on 2010-07-22
Additional inormation: The entries in the grub menu look strange (considering I upgraded from Karmic to Lucid):
Ubuntu 9.10, kernel 2.6.31-22-generic
ditto recovery mode
Ubuntu 9.10, kernel 2.6.28-18-generic
ditto recovery mode
Ubuntu 9.10, memtest86+
And then the lines for Windows XP

Shouldn't it say Ubuntu 10.04?
Last, when I boot into 2.6.28-18 it doesn't freeze up (at least not in the first 10 min) but it is slow as molasses and the cube is gone, the awn dock is gone, etc.

---

### Post by davidmohammed on 2010-07-22
Your last post is worrying - are you saying you dont have a lucid kernel to boot with? - lucid kernels end with .32-xx  - the current one is .32-24

If you do have a lucid kernel - then the others you mention are just your legacy ones from karmic/jaunty etc.  You can delete this using something like Ubuntu Tweak.


....


now that you've confirmed that this is an upgrade not a fresh install - some more ideas.

do you have a file called /etc/X11/xorg.conf?
if so rename it to something else - this may have some legacy entries that are interfering with lucid graphics.

---

### Post by muzincs on 2010-07-22
That's right.  Somehow the upgrade must have gone haywire!  If I delete the karmic kernels then I'm left with nothing...  How can I install the Lucid kernel?  (Shouldn't this have happened automatically!?!)  Btw, the upgrade went perfectly smoothly, and I had a clean install of Karmic (from when it was first released, meaning I had never upgraded the system on this machine, I had always done clean installs).  What a mess.  :(


Yes, there is an /etc/X11/xorg.conf file but it is the default one.  Also there is an identical file named xorg.conf.dist-upgrade-201007211204 and both files were written yesterday around the time I upgraded the OS.

---

### Post by davidmohammed on 2010-07-22
...  after you've done the below - you might want to give the xorg.conf stuff I added above a go.

can you confirm you dont have any files ending with .32-xx-generic in /boot 

/boot should contain files such as 
abi-2.6.32-20-generic         memtest86+.bin
abi-2.6.32-21-generic         System.map-2.6.32-20-generic etc.

yes - to your question - it should have done the kernel update automatically...
if you don't have a lucid kernel - goto synaptic manager

look for the packages linux-headers-2.6.32.-24,
linux-headers-2.6.32-24 generic
linux-headers-generic
linux-image-2.6.32.24-generic
linux-image-generic

they should be "green" indicating they have been installed.

if they are not - close synaptic manager

run

sudo apt-get update
sudo apt-get dist-upgrade

these should complete with no errors.  Check if your lucid kernels have been installed now.

---

### Post by tuxsun on 2010-07-22
> **davidmohammed said:**
> ... its possible that some other component other than your graphics is causing your issue.

you could try the following boot options (i.e. options can be entered together BEFORE quiet splash)

i915.modeset=0 noapic
i915.modeset=0 nolapic
i915.modeset=0 noapic nolapic
i915.modeset=0 noacpi
i915.modeset=0 acpi=off

Where are these (and other) boot options explained; especially the options regarding Xserver and Intel graphic chipsets? (reference source) 

Thanks in advance!

tuxsun

---

