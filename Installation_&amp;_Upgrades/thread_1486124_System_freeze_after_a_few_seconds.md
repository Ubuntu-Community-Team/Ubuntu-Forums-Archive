---
title: "System freeze after a few seconds"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by yaxoft on 2010-05-17
Hi.
[I'm not sure if this is the right forum. This is the closest I've found].

I've installed Ubuntu 10.04 LTS (dual boot with Windows XP SP3).
After Ubuntu starts, it takes about 10 seconds, and the computer halts. No screen/mouse/keyboard activity.
If I start Ubuntu under Recovery Mode, with failsafeX, it doesn't happen.

In the Windows all is fine...

What did I wrong?

[My CPU is: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz, if it matters...]

---

### Post by ronparent on 2010-05-17
You have probably not done anything wrong. Most likely you will have to append **nomodeset** to you grub boot line, Hit 'e' to edit the boot line and append this parameter to the linux kernel boot line. If that works, you will have to add that parameter to the **/etc/default/grub** file to make it permanent. If that doesn't work there are other thing you can try. Post your progress here.

---

### Post by yaxoft on 2010-05-17
Hi, thanks for the quick answer...

I tried "nomodeset" now, and my problem isn't solved.
I've edited /etc/default/grub by changing GRUB_CMDLINE_LINUX (I didn't forget running update-grub, of course....)
[I can see the new parameter now, when I hit 'e' on my wanted (probably all) option(s)]

When starting "normal" mode, Ubuntu still freezes after about 10 seconds. :confused:

---

### Post by davidmohammed on 2010-05-17
what's your graphic card?

lspci | grep VGA

---

### Post by ronparent on 2010-05-17
In an older system you might need **noapic nolapic**. There are more. For the more common ones look on the main menu of the live cd under f6. It sound like maybe related to kernel panic. What is your display when it freezes?

---

### Post by yaxoft on 2010-05-18
It is not an older system...
When it freezes, nothing changes. The screen shows the last frame forever.

---

### Post by yaxoft on 2010-05-18
the output of lspci is:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

---

### Post by yaxoft on 2010-05-18
I've tried the topic in (from the recovery mode, failsafeX): [http://ubuntuforums.org/showthread.php?p=8578246]("http://ubuntuforums.org/showthread.php?p=8578246").

I don't know whether it's related to my problem or not.

I did the 1,2,3 steps. I can't do step 4, because the "Indirect Rendering" is disabled...

I need your help, please.

---

### Post by pradeepthundiyil on 2010-05-18
Hi,

Its working perfect.. My issue was with my hard disk..

---

### Post by arvindp3 on 2010-05-18
> **yaxoft said:**
> I've tried the topic in (from the recovery mode, failsafeX): [http://ubuntuforums.org/showthread.php?p=8578246]("http://ubuntuforums.org/showthread.php?p=8578246").

I don't know whether it's related to my problem or not.

I did the 1,2,3 steps. I can't do step 4, because the "Indirect Rendering" is disabled...

I need your help, please.
This looks like the Intel video driver issue which prevents working with compiz.  I am waiting for this resolution, but not sure whether and when it will come.  For now, you could try the following before your screen freezes -- go to preferences-->appearance-->visual effects and set it to No effects.   It might stop this problem -- it did for me.  What you won't get though is compiz special effects, but everything else will work normally.  If this works for you then the only thing you can do is to change the video card to nvidia etc. or wait for the bug resolution.

---

### Post by pradeepthundiyil on 2010-05-18
Hi;

Ubuntu 10.04 freezes..... Planning to switch to openSUSE or fedora, till ubuntu rectifies the problem...



:guitar:

---

### Post by davidmohammed on 2010-05-18
Hi there,
  other intel 945 users have reported that you should boot with
i915.modeset=0

That should fix your graphics issues.


If it doesn't I would recommend you create the file
/etc/X11/xorg.conf

with the following contents:

```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"   "UXA"
EndSection
```

then reboot

---

### Post by yaxoft on 2010-05-21
Hi.

I did both "i915.modeset=0" and /etc/X11/xorg.conf.
I've thought that the problem is solved, because I was able to work about 15 minutes (instead of 20 seconds, before these changes).

But after 15 minutes, **it freezed again**.  It happened after a right-click near the "quick icons". a context-menu of the panel was appeared, and the system freezed.

Is this problem known? am I the first to report this issue?

---

### Post by Catharsis on 2010-05-21
Try "i915.powersave=0".

Also, you might want to try the mainline kernel.
32-bit:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
```

64-bit:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
```

---

### Post by yaxoft on 2010-05-27
Is the mainline kernel risky?
Can it fail somehow?

---

### Post by yaxoft on 2010-05-27
the "powersave" options didn't fix the freese problem...

---

### Post by Catharsis on 2010-05-28
Have you tried disabling compiz per comment #10? Seriously, this is a really easy test and is actually responsible for a good number of freezes.
> **yaxoft said:**
> Is the mainline kernel risky?
Can it fail somehow?
Sure, I guess there's a chance that it can fail. I've never seen it happen though. And even if it does, all you have to do is select a different kernel in grub and you'll be fine.

---

### Post by yaxoft on 2010-05-28
comment #10 works :)
thank you all for your assistance.

Is this bug going to be fixed in a future version of Ubuntu?

---

### Post by Catharsis on 2010-05-28
> **yaxoft said:**
> Is this bug going to be fixed in a future version of Ubuntu?

Only if you report it
```
ubuntu-bug compiz
```

---

