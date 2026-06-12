---
title: "Black screen after upgrade to 10.04"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by Ceresetta on 2011-12-15
I've read a million posts on this already but most of them go over my head, and I'm probably just making things worse by trying to follow their instructions. I recently upgraded from Ubuntu 9.10 (because it isn't supported anymore) to 10.04 LTS (or something similar, I can't see the computer screen anymore). When I boot the computer, I get to the point where the screen is purplish and there are five blinking dots and then "zap!" it all goes black and unresponsive. 

I have a Compaq nx9030.

Is there a patient soul out there who knows how to speak the language of the layman?

---

### Post by foresthill on 2011-12-15
Have you tried increasing brightness using the special keys on your keyboard?

---

### Post by nhasan on 2011-12-15
Hi Ceresetta,

Probably the only thread you need to read and understand is the following one from MAFoElffen: [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

I would suggest following the Troubleshooting Flow Chart which is presented in that post.

~nhasan

---

### Post by BC59 on 2011-12-15
I suggest you as well to install Ubuntu 11.10. Usually on the latest versions are included the latest workarounds to known bugs and problems.
Before this, you can select Try Ubuntu instead of Install, to check if it's working in your computer or not.

---

### Post by MAFoElffen on 2011-12-15
> **nhasan said:**
> Hi Ceresetta,

Probably the only thread you need to read and understand is the following one from MAFoElffen: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I would suggest following the Troubleshooting Flow Chart which is presented in that post.

~nhasan
@nhasan - Thank you... True. That's what that sticky is meant for. Of all threads in this forum, posts there are my #1 priority.

@Cersetta - And I can speak to the level of "user," customizing instructions for that user and the problem.

I can tell you that it is most likely what you described is one of two problems. But they center around that same thing... You have:
> Integrated  Intel Extreme Graphics 2 with up to 64MB of shared system memory for graphics- If you hold down the shift key after the BIOS messages, your Grub Menu should appear. (Tell me if it doesn't) 
- Press the "e" key. It should go into an edit mode 
- Arrow down until you get to the line that starts with "linux"
- Arrow right until after the "queit splash" and insert the text "nomodeset"
- Press the key combination <cntrl><x>.
- It will try to boot....

Tell me if that boots you into the Desktop.

EDIT-- Just looked at the Memory Spec's on that Laptop. How much Memory (RAM) is installed in yours? 2004- 7 yrs. ago.  Some came with 128MB... It's BIOS can handle 2GB w/ OEM 1024MB x 2 DDR SDRAM. Memory for that now is still available, but the price is a bit spendy.

---

### Post by Ceresetta on 2011-12-16
Thank you MAFoElffen. I tried editing the Grub menu by adding "nomodeset" but it didn't make any difference. I still get to the Ubuntu screen with the five dots and the video cuts out with a click. The screen is lit (it's black but not dead) but there is no cursor and otherwise no sign of life. 

So you are thinking it could be a hardware problem? Not enough RAM? This is a "junk" computer that a friend gave me. I use it for odd jobs, for my kids, and to get acquainted with Ubuntu. I was actually perfectly happy with 9.10 but got spooked because it isn't supported anymore. I can boot from the 9.10 disk and the computer works fine. Is there a problem using the outdated OS?

If the problem is RAM, it doesn't sound like installing 11.10 is going to be a solution.

EDIT: I booted from the 9.10 disk, opened terminal and typed sudo lshw -C memory and got:

[...]
memory
description: System Memory
physical id: a
slot: System board or motherboard
size: 2GiB
capacity: 2GiB
*-bank:0
description: DIMM DDR Synchronous
physical id: 0
slot: J5G3
size: 1GiB
width: 64 bits
(and then there's bank:1 which is the same except it's in slot J5G2

---

### Post by MAFoElffen on 2011-12-16
> **Ceresetta said:**
> Thank you MAFoElffen. I tried editing the Grub menu by adding "nomodeset" but it didn't make any difference. I still get to the Ubuntu screen with the five dots and the video cuts out with a click. The screen is lit (it's black but not dead) but there is no cursor and otherwise no sign of life. 

So you are thinking it could be a hardware problem? Not enough RAM? This is a "junk" computer that a friend gave me. I use it for odd jobs, for my kids, and to get acquainted with Ubuntu. I was actually perfectly happy with 9.10 but got spooked because it isn't supported anymore. I can boot from the 9.10 disk and the computer works fine. Is there a problem using the outdated OS?

If the problem is RAM, it doesn't sound like installing 11.10 is going to be a solution.

EDIT: I booted from the 9.10 disk, opened terminal and typed sudo lshw -C memory and got:

[...]
memory
description: System Memory
physical id: a
slot: System board or motherboard
size: 2GiB
capacity: 2GiB
*-bank:0
description: DIMM DDR Synchronous
physical id: 0
slot: J5G3
size: 1GiB
width: 64 bits
(and then there's bank:1 which is the same except it's in slot J5G2
It seems ti have enough RAM. I've ran Ubuntu with Less- and you have what they recommend. 

Let's try this another from another route.

First, get back to the Grub menu.
- Press "e" to get into edit mode.
- Arrow down until you get to the linux boot line (starts with "linux"
- Arrow right to where it says "quiet splash" and replace with the text "--verbose text"
- Press the key combination <Cntrl><Alt><x> to boot.

It should boot into a tty text console... Why am I having you do that?  The reason is to confirm that the kernel is booting to completion without errors. Check the messages. You can scroll back or forward with <Shift><PageUp> or <Shift><Page Down>

This next part you could do from the command prompt (If it booted the kernel with above directions. 
- Login.
```

sudo nano /etc/default/grub

```
Find the line that says 
```

# GRUB_GFXMODE=640x480

```
And change it to 
```

GRUB_GFXMODE=1024x768x16

```
Then, in the same file, go to the line that says
```
[FONT=monospace]
[/FONT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
And change it to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=791 1915.modeset=0"

```
Save and Exit... <cntrl><s> then <cntrl><x>

Pick up those changes in grub
```

sudo update-grub

```
Shut down the system and reboot
```

sudo shutdown -r now

```
If it doesn't come up after all that, try booting from a 10,04 LiveCD and see if the graphics do come up on the LiveCD.  If it doesn't boot up from the 9.x LiveCD you said worked and look at the filesystem where your OS iinstalled, Look for /var/log/Xorg.0.log and post it.

---

### Post by Ceresetta on 2011-12-19
OK, did that. Something changed. Now when I power on, I don't get the initial HP screen with the f10 and f12 options. The screen is blank all along. The only difference is that after the HDD has stopped working (at least after the little blue light is off) I get a greenish band about 6 mm high across the top of the screen, which is otherwise as blank as it was before.

I'm not sure if something went wrong when I edited grub. First of all, is that supposed to be "1915" before modeset=0 or "i915" (which I have seen elsewhere)? Second, when I hit ctrl s to save it it gave me some message with "XOFF" and "IGNORE" (as I recall). Then when I hit ctrl x to exit it asked me for a name to save the file. I just hit return.

I do want to thank you for all the time you are dedicating to me. I really appreciate it.

OK, the initial HP screen is back, I can get back into grub. I changed "1915" to "i915" but it didn't make any difference

---

### Post by MAFoElffen on 2011-12-19
> **Ceresetta said:**
> OK, did that. Something changed. Now when I power on, I don't get the initial HP screen with the f10 and f12 options. The screen is blank all along. The only difference is that after the HDD has stopped working (at least after the little blue light is off) I get a greenish band about 6 mm high across the top of the screen, which is otherwise as blank as it was before.

I'm not sure if something went wrong when I edited grub. First of all, is that supposed to be "1915" before modeset=0 or "i915" (which I have seen elsewhere)? Second, when I hit ctrl s to save it it gave me some message with "XOFF" and "IGNORE" (as I recall). Then when I hit ctrl x to exit it asked me for a name to save the file. I just hit return.

I do want to thank you for all the time you are dedicating to me. I really appreciate it.

OK, the initial HP screen is back, I can get back into grub. I changed "1915" to "i915" but it didn't make any difference
Let me make that easier to see:
[SIZE=4]**i915.modeset=0**[/SIZE]

But that's a mood point. First test those options from the grub menu. **IF** those options work, THEN use the instructions following that to make it permanent. 

Did the options work for you?

---

### Post by Ceresetta on 2011-12-20
The options did not work. 

Description of what happened:
entered grub, changed "quiet splash" to "--verbose text"
typing <cntr><alt><x> does nothing
if I type <cntr><x> I get lines and lines of text ending with:

Ubuntu 10.04.3 LTS rubunt tty1
rubunt login: 
(and I can't scroll back up to look at all those lines and lines of text)

I log in and get:
robert@rubunt: (with a tilde and dollar sign)

I type <sudo nano /etc/default/grub>

I make the two modifications

<cntr><s> gives me "[ XOFF ignored, mumble mumble ]"

<cntr><x> gives me "Save modified buffer (...)?"
I type <y>
I get "File  name to write: /etc/default/grub"
I hit <enter>
back to "robert@rubunt: (with a tilde and dollar sign)"

I type <sudo update-grub>
I get "Generating grub.cfg...
Found linux image: (...)
Found initrd image: (...)
Found linux image: (...)
Found initrd image: (...)
Found memtest86+ image: (...)
done"

I type <sudo shutdown -r now>
I get lots of lines, then the screen goes blank. When the HDD has stopped working I still have a totally blank screen (no cursor, no mouse) with the sole exception of a green band about 6 mm high across the top of the screen.

I shut down by pushing on the power button. Go back to grub (GNU GRUB version 1.98-1ubuntu12) and this is what it looks like:

recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set (a bunch of alphanumeric characters)
linux /boot/vmlinuz-2.6.32-36-generic root=UUID=(the same bunch of alphanumeric characters) ro   quiet splash vga=791 i915.modeset=0
initrd /boot/initrd.img-2.6.32-36-generic

I hit <cntr><x> and get the blank screen ending up with a green band across the top.



If you're like me, you probably really want to figure out what's going on and fix it. I would, however, like to ask this question: since I do not have a live CD of ubuntu 10.04 and would have to download it anyway, and given that I apparently have plenty of RAM, would it be an option to download the most recent version of Ubuntu and just try installing it directly?

---

### Post by MAFoElffen on 2011-12-20
> **Ceresetta said:**
> The options did not work. 

Description of what happened:
entered grub, changed "quiet splash" to "--verbose text"
typing <cntr><alt><x> does nothing
if I type <cntr><x> I get lines and lines of text ending with:

Ubuntu 10.04.3 LTS rubunt tty1
rubunt login: 
(and I can't scroll back up to look at all those lines and lines of text)

I log in and get:
robert@rubunt: (with a tilde and dollar sign)

I type <sudo nano /etc/default/grub>

I make the two modifications

<cntr><s> gives me "[ XOFF ignored, mumble mumble ]"

<cntr><x> gives me "Save modified buffer (...)?"
I type <y>
I get "File  name to write: /etc/default/grub"
I hit <enter>
back to "robert@rubunt: (with a tilde and dollar sign)"

I type <sudo update-grub>
I get "Generating grub.cfg...
Found linux image: (...)
Found initrd image: (...)
Found linux image: (...)
Found initrd image: (...)
Found memtest86+ image: (...)
done"

I type <sudo shutdown -r now>
I get lots of lines, then the screen goes blank. When the HDD has stopped working I still have a totally blank screen (no cursor, no mouse) with the sole exception of a green band about 6 mm high across the top of the screen.

I shut down by pushing on the power button. Go back to grub (GNU GRUB version 1.98-1ubuntu12) and this is what it looks like:

recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set (a bunch of alphanumeric characters)
linux /boot/vmlinuz-2.6.32-36-generic root=UUID=(the same bunch of alphanumeric characters) ro   quiet splash vga=791 i915.modeset=0
initrd /boot/initrd.img-2.6.32-36-generic

I hit <cntr><x> and get the blank screen ending up with a green band across the top.



If you're like me, you probably really want to figure out what's going on and fix it. I would, however, like to ask this question: since I do not have a live CD of ubuntu 10.04 and would have to download it anyway, and given that I apparently have plenty of RAM, would it be an option to download the most recent version of Ubuntu and just try installing it directly?
Yes, meaning download the LiveCD and "try" the LiveCD Live Image.  If it works, then make a decision to reinstall or not.

What is confusing with this is that your video Chipset is supported by the default installed generic video drivers.... It should be working without installing anything special and without having to use a boot parameter or option.

---

