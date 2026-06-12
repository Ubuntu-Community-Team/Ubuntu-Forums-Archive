---
title: "[SOLVED] BusyBox Error."
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by hippyguy7 on 2008-07-26
**_PROBLEM:_** I put this in the installation section because technically, I have never been able to run it so far.

This same exact error would happen when I tried to either run the OS off a live CD, or install off of the live CD.

My System would boot up as usual. I get a screen telling me to press delete to enter BIOS or Tab to continue. 
I press Tab and I am presented by a screen of text with some system info(the screen that shows before an OS boots. On this screen it gives me a few seconds to press ESC and enter GRUB before booting into the GUI. 
The Ubuntu icon with the orange bar shows at the bottom. It takes an unusually long time(like 5-10mins) before displaying the following error on a text screen.

Here's the error:

"Busybox v1:1.13 (Debian 1:1.1.3-5 ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands"

This is on a brand-new PC. As the initial OS.

I am using the 64 bit OS, regular Ubuntu.

For hardware I am using a Intel Quad Core Q6600, ATI HD4850 GFX card, 2 sticks or 2g G. Skill RAM, Western digital 500gb HDD, and a Biostar P43 Motherboard.

Can anyone help please?
[B][U]
SOLUTION:[/U][/B] 
> 
Folks,
I think I have a great news to fix this initramfs issue. Here is what I did.

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally.
Above worked successfully and I hope your case is working fine.

---

### Post by hippyguy7 on 2008-07-26
Bump.

---

### Post by damis648 on 2008-07-26
> **hippyguy7 said:**
> Bump.

Please do not bump your posts so frequently. Anyway, on boot at the GRUB menu (press Esc. to get to is if you are not dual booting) press "e" on the default boot option (usually the top one). Now go to the second line and press "e" again. In the line that opens up, use backspace to remove the words "quiet" and "splash" from the end of that line. Now press enter and then "b". Wait until you get to the busybox. Tell us what error preceded right before it.

---

### Post by hippyguy7 on 2008-07-26
> **damis648 said:**
> Please do not bump your posts so frequently. Anyway, on boot at the GRUB menu (press Esc. to get to is if you are not dual booting) press "e" on the default boot option (usually the top one). Now go to the second line and press "e" again. In the line that opens up, use backspace to remove the words "quiet" and "splash" from the end of that line. Now press enter and then "b". Wait until you get to the busybox. Tell us what error preceded right before it.

Alright. I did what you said(sorry about the bumps), and this is my result:

[B][U]"Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/013f89a7-33a1-44ce-9cf8-8776df74e62b does not exist. Dropping to a shell!"[/U][/B]

This text is shown directly above the busybox.

Thanks for the helpful responses so far! I hope I can get this resolved soon =).

---

### Post by damis648 on 2008-07-26
Okay, try this:
Boot up again, doing the same thing as before, and removing "quiet" and "splash". Now, also scroll left a bit and look where you see
root=UUID=[some random stuff]
and remove "UUID" and the random stuff to the right of it. Only "root=" should be left from that parameter. Now, after root=, put the partition Ubuntu is installed on (ie. /dev/sda1 /dev/hdb2, etc.) and press enter and "b" again. Does it boot up fine, or give you another error?

---

### Post by hippyguy7 on 2008-07-26
> **damis648 said:**
> Okay, try this:
Boot up again, doing the same thing as before, and removing "quiet" and "splash". Now, also scroll left a bit and look where you see
root=UUID=[some random stuff]
and remove "UUID" and the random stuff to the right of it. Only "root=" should be left from that parameter. Now, after root=, put the partition Ubuntu is installed on (ie. /dev/sda1 /dev/hdb2, etc.) and press enter and "b" again. Does it boot up fine, or give you another error?

Doing this now. Will let ya know how it turns out.

---

### Post by hippyguy7 on 2008-07-26
I have a quick question. My Hard Drive is a SATA drive, but is configured to look like an IDE drive. I have already tried replacing the "UUID-xxxxxxxxxxxxxx" with "/dev/hda1" to no avail. It simply says the same error but now targeting the "/dev/hda1" directory.

I also check my fdisk data. I have reformatted twice now but it keeps creating 3 partitions every time even though I ask it for one. Here they are.

hda1 = Linux
hda2 = Extended
hda5 = Linux/ Solaris

So, I'm going to try all of the partitions as well as "sda" versions of them instead of "hda".

Anything else I should know?

---

### Post by hippyguy7 on 2008-07-26
it doesn't seem to be working for me.

I'm almost positive that Ubuntu is on the first partition. I have tried "root=/dev/sda1", and "root=/dev/hda1". 
I have also tried unflagging my SATA drive as an IDE drive. This simply wouldn't allow me to even access the GRUB menu.

I have also reinstalled ubuntu twice. I'm really at a loss here. Please help!

And thanks to damis for all of his help!

---

### Post by hippyguy7 on 2008-07-26
Ok. I have even MORE data for you guys to help me out with.

It seems that if I try to boot a different partition such as in the command "boot=/dev/hda5", if I do not alter the top line to match the partition, it will continue as normal and freeze up with te busybox later on.

If I use the altered code "boot=/dev/hda5", as well as altering the top line to match the partition # (in this case, "(hd0,4)" I am presented with the message saying that this partition cannot be mounted. Though I do know it is there, because entering a false partition number leaves me with a message saying that the partition does not exist at boot.

---

### Post by hippyguy7 on 2008-07-26
Ok. So I tried everything that has been posted about so far (including my own posts). As well as using different install CDs, checking the CDs for integrity, and reinstalling Ubuntu 3 times.

I'm seriously at a loss here. What can I do?

---

### Post by gilch on 2008-07-26
After countless tries to install ubuntu 8.04 I also always get the BusyBox error.
Mine is
"usb 1-1 : device not accepting address 2, error -71"

Can anyone tell me what that is? I have only about 11 hairs left on my head.
Gilles

---

### Post by JS Lemming on 2008-07-26
Give this a shot. It fixed my busybox problems.

> **iqiszero said:**
> Folks,
I think I have a great news to fix this **initramfs** issue.  Here is what I did.

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally.  
Above worked successfully and I hope your case is working fine.

---

### Post by hippyguy7 on 2008-07-27
> **JS Lemming said:**
> Give this a shot. It fixed my busybox problems.

It seems to me that this is a case-by-case issue, but I will try it and report back with my results. Thanks.

---

### Post by hippyguy7 on 2008-07-27
> **JS Lemming said:**
> Give this a shot. It fixed my busybox problems.

WOW! I almost skipped over this thinking that it probably would not work. But Ubuntu now boots thanks to your help! I couldn't thank you enough for linking that info!

---

### Post by JS Lemming on 2008-07-27
I'm glad it worked for you. :)

---

### Post by hippyguy7 on 2008-07-27
> **JS Lemming said:**
> I'm glad it worked for you. :)

Thanks man! Hopefully others who are having the same problem will see this thread as well.

And as a sidenote: this is pretty obvious I thought, but you can boot from a hard disk with this fix as well. Just edit the boot code on the GRUB menu.

---

### Post by gilch on 2008-07-27
I tried that, it only got me back to the dreaded (intramfs) and that did not accept the "modprobe" command.
Gilles

---

### Post by gilch on 2008-07-27
Why does this Thread says SOLVED. It is not solved at all.

---

### Post by confused57 on 2008-07-27
> **gilch said:**
> Why does this Thread says SOLVED. It is not solved at all.
Here's quite an extensive thread that could provide a solution:
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

---

### Post by gilch on 2008-07-28
I have now come to admit that the problem with my machine is that my SATA drives are seen as IDE drives by my Bios. To correct that I have to correct the Bios, which for me is like playing soccer on a land mine field... I also found out that OpenSuse has the same problem with my Bios. So... good bye Linux. I guess LInux is only meant for people who have a machine built for Linux.

---

