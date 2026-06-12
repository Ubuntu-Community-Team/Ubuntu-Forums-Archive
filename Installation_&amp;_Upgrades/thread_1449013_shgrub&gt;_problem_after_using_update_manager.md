---
title: "sh:grub&gt; problem after using update manager"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by heus33 on 2010-04-07
I've been using Karmic 9.10 for a few months now with no issues.  Just updated via update manager and required a reboot.  Now I get the following message:

GNU GRUB version 1.97~beta4

[B][ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions. ]

sh:grub>[/B]

I've done some searching and found that this is a common problem with those using wubi and a dual boot system.  I am not using wubi and this is not a dual boot system (unbutu only).

I've tried recovering grub2 by using the live CD and these instructions: [http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html) however this resulted in no change.

Anyone got any ideas?

TIA

Tom

---

### Post by oldfred on 2010-04-07
From the liveCD you can download this so we can see if there is anything obvious in the boot process:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by heus33 on 2010-04-08
> From the liveCD you can download this so we can see if there is anything obvious in the boot process:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


Thanks but I can't access the internet through the live CD, my NIC isn't recognized and the driver for it wont load.  Anything else I can try?

---

### Post by drs305 on 2010-04-08
First, my apologies. I got into your post somehow and made an unintentional change. I restored it but not quite to the original content.


When you tried to reinstall Grub2 via the LiveCD, did all the commands run without errors? Did you specify the drive and not the partition (sda, sdb, etc vs sda1, sdb5)?

Have you tried booting from the G2 command line?
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

---

### Post by heus33 on 2010-04-08
> **drs305 said:**
> First, my apologies. I got into your post somehow and made an unintentional change. I restored it but not quite to the original content.


When you tried to reinstall Grub2 via the LiveCD, did all the commands run without errors? Did you specify the drive and not the partition (sda, sdb, etc vs sda1, sdb5)?

Have you tried booting from the G2 command line?
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Yes the commands ran without errors.  Here's what was returned:

[B]Installation finished.  No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not.  If any of the lines is incorrect, 
fix it and re-run the script 'grub-install'.

(hda0)    /dev/sda

[/B]Is this any cause for concern?

---

### Post by heus33 on 2010-04-08
Also - when I try to use CLI to boot and enter in this line:

[B]linux /vmlinuz root=/dev/sd[I]a1 ro

[/I][/B]I get an error - [B]error: file not found

[/B]Here are my settings, under [B]set

?=22
color_highlight=
color_normal=
pager=
prefix=(hd0,1)/boot/grub
root=hd0,1

[/B]under [B]ls:

(hd0) (hd0,1) (fd0)
error: no such disk
[/B]

---

### Post by drs305 on 2010-04-08
heus33,

From your last two posts:

Assuming your Ubuntu partition is on the first drive's first partition (sda1), the device map contents do not look correct: **[COLOR="Red"](hda01) /dev/sda[/COLOR]**
The normal entry would look like:  **(hd0) /dev/sda**
From the LiveCD you can mount your normal Ubuntu partition and edit /*mountpoint*/boot/grub/device.map.

From the grub prompt, try setting root like this:
```
set prefix=(hd0,1)/boot/grub
set root=/dev/sda1
```
Then run "ls (hd0,1)/boot/grub". You should see the grub files, including lots of .mod files. If you see the files:
```
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

---

### Post by heus33 on 2010-04-08
Thanks drs305.  

I set up the root just like you said and ran ls (hd0,)/boot/grub and recieved a list of mod files and grub files but when I try and run **linux /vmlinux root=/dev/sda1  **I get [B]error: no such disk

[/B]Thanks for helping me - got any other ideas?

---

### Post by drs305 on 2010-04-08
heuss33,

Apologies for the typo. It was correct in the initial instructions but not in the latter one, which I've now corrected.

It's **vmlinuz**, not [COLOR="Red"]vmlinux[/COLOR]
```
linux /vmlinuz root=/dev/sda1 ro
```

I didn't notice it until I saw it in your post.

---

### Post by heus33 on 2010-04-08
linux /vmlinuz root=/dev/sda1 ro

still returns **error: no such disk**

---

### Post by heus33 on 2010-04-08
Solved - ended up being a problem with the search line.  Needed to be edited to fix.

 [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

BIG thanks to drs305 for helping me out.  :)

---

