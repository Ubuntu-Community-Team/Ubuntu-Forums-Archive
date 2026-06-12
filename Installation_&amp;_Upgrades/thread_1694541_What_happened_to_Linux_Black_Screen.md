---
title: "What happened to Linux? Black Screen"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by ltcolfury on 2011-02-24
I am not posting this to be difficult, just looking for any sort of help. I am also curious as to the the widespread issues currently with Linux & i7 Intel HD Graphics.

I used Linux for a long time in the past mainly Ubuntu, Debian, Red Hat, Suse, and other flavors without any difficulty. I decided to install Ubuntu on my laptop along side W7 Prof. (Tried that is... along with 6 other flavors and same result.)

Here is the problem: What is with the black screen after installing/booting?!! 

I've tried Wubi, virtualbox, Windows Virtual PC, partitioning, etc, with the same result. The only thing I can ever boot to is Fedora 14 "Live disk" using the safe boot option. Tried to install and...black screen, no matter what I did.

I've tried searching this issue and nothing I have found remedies this problem. Why should anyone have to configure a simple installation? I've found solutions to Nvidia and ATI though.

Here are my specs: Dell E6510, Intel i7 M620 @ 2.67GHz x4, 8GB RAM, 64 bit, i7 Intel HD Graphics.

Thanks much for any assistance.

---

### Post by Rubi1200 on 2011-02-24
Is Ubuntu currently installed on the laptop in question?

At boot, as the GRUB menu comes up and the entry for Ubuntu is highlighted press "e" to edit.

Navigate using the arrow keys and find the line that ends with > quiet splash

Add this after quiet splash; i915.modeset=1

The line should then look like this:

> quiet splash i915.modeset=1

"Ctrl" + "x" to boot.

Let us know if this gets you to the desktop.

If yes, post the output of this command from the terminal:

```
lspci | grep VGA
```

---

### Post by ltcolfury on 2011-02-24
You are amazing and thank you for the assistance. I was able to get to the desktop using your commands.

Here is the output to the lspci | grep VGA command:

*00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)*

I followed this to make it permanent. It wouldn't boot again using =1 so I used =0.
[B][I]
[I]GRUB

You&#8217;ll want to change these settings in GRUB so they&#8217;ll automatically be applied on each reboot. To do so, follow the steps below:

   1. Edit the /etc/default/grub file. You will need Admin privileges to do so (sudo)
   2. Find this line: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
   3. Replace with: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash <option>&#8221;[/I][/I][/B]

Thanks again, much obliged!

---

### Post by Rubi1200 on 2011-02-25
No problem, you are more than welcome.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

