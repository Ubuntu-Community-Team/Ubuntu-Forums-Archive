---
title: "Ubuntu 12.04 installer hangs at &quot;Preparing...&quot;"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by dewdrop_world on 2014-04-21
I am trying to install Ubuntu 12.04 on a system that already has Windows 7. I can't blow away Win7 (wish I could) because I have to teach commercial software for my job.

I'm not an early adopter, so I won't be trying 14.04 until this summer at the earliest.

I'm booting from a LiveUSB. The LiveUSB Ubuntu environment is working perfectly -- I'm typing this in that environment now.

Ubiquity lets me choose the language, then there's the "Preparing to install" screen. My disk has over 300 GB free, I'm plugged in, and connected to the internet.

I click "Continue" and... the mouse pointer spins... and spins... and spins... and nothing else happens. The Unity session doesn't totally freeze -- I can keep doing other things -- but the installer process itself just sits there doing nothing.

It's been quite hard to search for this problem here, since everybody seems to have a different installation problem. So, sorry if it's a dupe -- if so, please point me to the right thread.

One solution seems to be to use the alternate installer. I'll do it if I have to, but I already spent one hour tonight downloading the regular ISO and I rather don't relish the thought of another massive download. Any other ideas?

Potentially useful factoid: gparted doesn't recognize the windows partitions at all:

```
/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
```

Could Ubiquity be trying to figure out what partitions are there, getting confused and then failing to handle the error properly?

Thanks.
hjh

---

### Post by dewdrop_world on 2014-04-21
Actually it seems to be the option to download updates while installing. This time I unchecked both boxes and it does actually go ahead now.

However, it claims that there are no operating systems on the machine. Win7 is most certainly there... I must have dual boot for my job, so of course I can't continue with the installation now.

Do I need to start a new thread for the partitioning problem?

Anyway, I give up for tonight. So now I have my old 12.04 environment, which I can boot using a dodgy usb enclosure for my dead laptop's HD -- this keeps freezing randomly, forcing a reboot, so I have to get a working new installation of 12.04 just to get work done. And I have the LiveUSB environment, which won't install for dual boot. Not in a good place yet.

---

### Post by dewdrop_world on 2014-04-22
Last update -- for future readers:

- In my case, the installer always hung on "Preparing to install" if either checkbox was enabled (to download updates during installation, or download proprietary MP3 codecs). It worked only if both boxes were unchecked. I saw online that this didn't help everyone, but it helped me.

- This page fully explained, and provided a complete solution for, the GPT problem. [http://www.rodsbooks.com/gdisk/wipegpt.html](http://www.rodsbooks.com/gdisk/wipegpt.html)

- Then the system wouldn't run GRUB at boot time, instead booting directly to Windows. YannBuntu's excellent boot-repair utility took care of that.

So I'm up and running now.

hjh

---

