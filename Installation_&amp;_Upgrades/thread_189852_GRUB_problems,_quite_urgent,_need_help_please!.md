---
title: "GRUB problems, quite urgent, need help please?!?"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by tazzik on 2006-06-05
Ok, straight to business,
I installed dapper fine, formatted my 5.10 fine went OK, got everything running.
BUT THEN, went to XP and got a massive load of viruses from a website, very hastily reinstalled XP, now GRUB won't appear, I've had this problem before but a magic command fixed it. But I've lost the commands and I get lots of errors. I have this layout:

/dev/hda = 4gb windows
/dev/hda5 = swap 576mb
/dev/hda6 = 6gb linux 

I get errors such as : 
grub-install /dev/hda6
Could not find device for /boot: Not found or not a block device.
AND
> find /boot/grub/stage1

Error 15: File not found
 Please help, don't just ignore it. I really need help
tazzik

---

### Post by tazzik on 2006-06-05
BUMP Please help

---

### Post by Joeb on 2006-06-05
Check out: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

You most likely want to scroll down to the Troubleshooting section and then to the Recovering Grub Automatically directions (at least that would be my guess).

---

