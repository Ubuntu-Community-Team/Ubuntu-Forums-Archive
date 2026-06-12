---
title: "Can't install Lubuntu 16.04 (USB key): &quot;usb usb1-port7: over-current condition&quot;"
date: 2016-07-08
forum: Installation &amp; Upgrades
---

### Post by pubalapoub on 2016-07-08
Hi everyone,

I'm trying to install Lubuntu 16.04 i386 from an USB key (that proved to be working normally with Kubuntu & Xubuntu 16.04 installers) on an old Pentium 4 / 2 GB RAM PC.

At boot, I can select my language and get to the options menu, but as soon as I select **any** of the options (like "Try Lubuntu ..."), it looks like the installer freezes for ~ 1 min (still displaying the options menu), then displays a black screen, followed by a short message - too fast for me to read, then displays a blinking cursor at the top left.

When I switch to display tty1, I can see several errors (read below) for a short time, followed by the login prompt, but everything soon disappears, until I press Ctrl+Alt+F1 again, same messages appearing and disappearing, etc. etc. Consequence: **I'm unable to login** to gather more information from logs.

```
usb usb1-port7: over-current condition
[drm:intel_parse_bios [i915]] *ERROR* Child device config size 27 is too small.
[drm:i915_gem_init_stolen [i915]] *ERROR* conflict detected with stolen region: [0x7f800000 - 0x7ffe0000]

Ubuntu 16.04 LTS lubuntu tty1

lubuntu login: _
```

I took a look at BIOS options but don't want to test each and every of them (or so... ^^) since my current BIOS configuration is working well with Kubuntu & Xubuntu 16.04. However I tried disabling an APIC E/S option, with no improvement on Lubuntu's installer.

The sole similar error I could find is in this [thread]("http://ubuntuforums.org/showthread.php?t=2301216") ("*[drm:intel_parse_bios [i915]] *ERROR* Child device config size 27 is too small.*") but I'm not facing anything relating to 'fsck'.

Note: I checked the MD5 sum of my downloaded ISO and it looks OK: 1b5dc31e038499b8409f7d4d720e3eba  lubuntu-16.04-desktop-i386.iso

Thanks in advance for your opinions.

In the meantime I'll dig the 2nd part of the errors ("*[drm:i915_gem_init_stolen [i915]] *ERROR* conflict detected with stolen region*").

---

### Post by pubalapoub on 2016-07-08
Ok, focusing on the 2nd part led me to a solution :)

Thanks to this [comment]("http://askubuntu.com/questions/783039/cant-reinstall-ubuntu-from-livecd-16-04-after-deleting-it#comment1172802_783039"), I tried passing 'nomodeset' to the kernel via F6 and Lubuntu finally booted. The options menu was still frozen for a while, but then Lubuntu booted...

So I'll set this thread to Resolved.

However I'm surprised by the **slowness** of LXDE when dragging windows over the screen... I would have expected at least as much reactivity as with XFCE (Xubuntu). Could it be due to this 'nomodeset' parameter?...

---

### Post by DuckHook on 2016-07-09
Your problem may only be half-solved, in the sense that you have a working system but with degraded graphics. You can set the thread back to unsolved in the same way that you tagged it solved.

If you can now boot, you may want to write the nomodeset parameter into /etc/default/grub so that you won't have to edit your boot parameters every time you boot.

The nomodeset parameter is a video parameter. It has nothing to do with fsck, though I suppose that a corrupted disk might in a convoluted way lead to a video problem. Although nomodeset gives you graphical output, it does so by rendering your images through your CPU, which, in a system as old as yours, will cause the degraded performance that you note.

You have done admirably trying to research a solution yourself. It obviously allowed you to come across the nomodeset parameter. And now that you can boot, you can also provide more info. Please post the output of:```
lspci -vk | grep -iA13 vga
```I have a sneaking suspicion of what the problem is, but we need the output from that command.

---

