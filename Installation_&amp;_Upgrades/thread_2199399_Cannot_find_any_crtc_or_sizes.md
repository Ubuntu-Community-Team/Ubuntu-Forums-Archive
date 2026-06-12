---
title: "Cannot find any crtc or sizes"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by arnold_layne2 on 2014-01-13
**EDIT: I booted using nomodeset, and now the issue is that Ubuntu always starts in 'Software Rendering Mode'. As I said, my AMD card is faulty and I don't want to use it. In windows, I've disable the AMD card and I've installed the Intel HD3000 card's drivers and Windows works very well with no problems.  I want to achieve the same in Ubuntu. I'm sure there would be a way to do that in Ubuntu if I can do it in Windows. Any advice?**

I urgently need advice on how to achieve the same in Ubuntu, i.e. running it off the Intel HD3000 card, and completely disabling/ignoring the AMD card or it's drivers. There is no option to disable the AMD card in my BIOS.

This screen appears when I try to boot via a live USB: 
It simply hangs after this. No signs of any progress or any other errors. Simply this. I don't really know what other details to give, but this is basically it. I don't know what to do.

HP DV6 6121tx : Intel i7 2.0GHz, 4GB RAM, AMD HD6770M + Intel HD3000.

I should mention, my AMD card *does* probably have some issues. I've disabled it in Windows 8.1 and installed simply the Intel drivers. I don't know if it's relevant or not, but I thought I should mention it.

I *never* used the AMD card in my previous Linux installations. I always switched it off in /sys/kernel/debug/vgaswicheroo/switch. So I just need to get a working Linux installation that can work with my Intel card! How do I get past this strange error?

[IMG]http://i.imgur.com/NO17aGu.jpg[/IMG]

---

### Post by ubfan1 on 2014-01-13
At the grub menu choice, try adding nomodeset to the linux boot line.  If you are on a UEFI machine, you will have to edit the grub commands with an editor (type e, inst on screen at bottom).  Otherwise, you should have function key menu additions, one of which should be nomodeset.

---

### Post by papibe on 2014-01-13
Hi arnold_layne2.

I would try to disable to disable the card on the BIOS, if possible.

Just a thought.
Regards.

---

### Post by arnold_layne2 on 2014-01-15
> **ubfan1 said:**
> At the grub menu choice, try adding nomodeset to the linux boot line.  If you are on a UEFI machine, you will have to edit the grub commands with an editor (type e, inst on screen at bottom).  Otherwise, you should have function key menu additions, one of which should be nomodeset.

Okay using nomodeset, I was able to boot the live CD and install Ubuntu. I always have to boot with 'nomodeset' to make it work. The issue is that Ubuntu always starts in 'Software Rendering Mode'. As I said, my AMD card is faulty and I don't want to use it. In windows, I've disable the AMD card and I've installed the Intel HD3000 card's drivers and Windows works very well with no problems. 

I urgently need advice on how to achieve the same in Ubuntu, i.e. running it off the Intel HD3000 card, and completely disabling/ignoring the AMD card or it's drivers. There is no option to disable the AMD card in my BIOS.

---

### Post by ubfan1 on 2014-01-15
You can edit the file /etc/default/grub and add the nomodeset to the line:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset splash"
Then run sudo update-grub to update the grub.cfg file.

---

### Post by arnold_layne2 on 2014-01-15
I suppose I didn't make myself clear.

With 'nomodeset', Ubuntu boots into Software Rendering Mode. I want to make it run off my Intel HD3000 card and ignore/disable the AMD card (as I have done in Windows).

---

### Post by ubfan1 on 2014-01-15
Take a look at [http://forums.linuxmint.com/viewtopic.php?f=59&t=142280](http://forums.linuxmint.com/viewtopic.php?f=59&t=142280)
May take a another kernel release, but  try some more options for Video problems:

i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

---

### Post by arnold_layne2 on 2014-01-17
> **ubfan1 said:**
> Take a look at [http://forums.linuxmint.com/viewtopic.php?f=59&t=142280](http://forums.linuxmint.com/viewtopic.php?f=59&t=142280)
May take a another kernel release, but  try some more options for Video problems:

i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Nope, all of these still give me the same problem at boot :(

---

