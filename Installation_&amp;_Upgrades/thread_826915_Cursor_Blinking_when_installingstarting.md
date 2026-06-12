---
title: "Cursor Blinking when installing/starting"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by joeabiraad on 2008-06-12
Hi

I have been using linux for over 1 year now and i have it running on both of my PCs at home (alone without windows) 

anyway i was trying to install it on my PC at work.

My PC is : 

DELL - OPTIPLEX 320 
RAM: 1 GB
HDD: 80 GB
VGA: ATI 512 MB 


Here is the problem:
I was trying to install ubuntu 8.04.
I booted the CD like i do always and chose "Install Ubuntu now"
Then the cursor starts to blink and nothing happens.

I also tried the alternate version... same result.

....

Then i plugged in the hard disk into another PC and installed ubuntu 8.04 on it.

Everythg worked fine. the installation went smoothly and on reboot i started with ubuntu :D

I removed the HDD and replugged it into my PC; Grub started and when i chose Ubuntu 8.04 the cursor started to blink again and nothing happened.

What could be the problem  ? ?

Note that i also tried installing 7.10 (same problem) 

// Jo

---

### Post by dstew on 2008-06-12
The problem is that the kernel is not compatible with the hardware of that PC for some reason. To debug the problem, boot the Live CD again, but instead of choosing Install, hit F6 to get different boot options. Try Safe Graphics mode. You can also modify the kernel line to see error messages, by removing **quiet splash**. After you modify the kernel line, hit return, and continue to boot. Then, you will be able to see more clearly what the problem is.

Once you have a good idea as to the reason the kernel is having a problem with your PC, you can add parameters to the kernel line to try to get it to boot.

---

### Post by joeabiraad on 2008-06-12
Hi, 
i did remove quiet splash and here is what i got.

It also stopped and the cursor blinked as usual.
the last 3 messages be4 freezing are:

```

[91.330860] PNP: No PS/2 controller found. Probing ports directly
[91.333588] serio: 8042 KBB port at 0x60,0x64 irq 1
[91.333644] serio: 8042 AUX port at 0x60,0x64 irq 12

```

After those 3 msg the cursor blinked again and the process was stopped...

any idea why this is happening ?

---

### Post by joeabiraad on 2008-06-12
I found this thread here [http://ubuntuforums.org/showthread.php?t=94686](http://ubuntuforums.org/showthread.php?t=94686)

it seemed like my problem but then again i disabled USB from BIOS and Ubuntu didnt boot. also the LIVE CD didnt boot either.

...

// Jo

---

### Post by dstew on 2008-06-12
Try to look up higher on the messages to see if there is any line flagged with "error". Maybe alt-PageUp can get you up a screen.

The lines listed show no error. This might mean that when the ports were probed, the system locked because of an interrupt conflict, or other problem handling interrupts.

One way to clean up interrupt handling is to use kernel parameters to turn off the advanced programmable interrupt controller (APIC). Press F6 at the first screen again, remove quiet splash, but now add the following to the kernel line: **noapic nolapic**. Hit enter and continue to boot. Any better? If not, there is one more thing to try.

---

### Post by joeabiraad on 2008-06-15
Thank you for your reply and sorry for being late.

Ok after doing what you've just suggested smthg changed but the loader still stops at the following:

```
...
iomem range could not be reset (there were a lot of them)
...
IO window: disabled
PREFETCH window: disabled
NET: Registered protocol family 2
```

It is also worth noting that the keyboard is not responding when i am arriving at this stage.

are we getting somewhere ?

---

### Post by dstew on 2008-06-16
I don't know if we are getting anywhere. Those messages are normal kernel output, not errors. It seems that the system is just dying without giving any errors. Could it be a hardware problem? Does that PC work with another operating system?

One more thing to try is the kernel parameter **acpi=off**. This turns off the Advanced Configuration and Power Interface, which is implemented poorly on some PC's, and the Linux kernel cannot make it work properly. See this [Wikipedia article]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface"), Criticism, at the bottom.

---

