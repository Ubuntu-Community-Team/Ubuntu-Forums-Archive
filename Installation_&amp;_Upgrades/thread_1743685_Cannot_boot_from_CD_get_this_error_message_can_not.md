---
title: "Cannot boot from CD get this error message: can not mount dev/loop0 (/cdrom/casper/f"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ricethins on 2011-04-29
I burned 3 CDs with the iso image of Ubuntu 11.04 at least 2 of the CDs appeared to burn just fine. But when I tried to install from them, the Ubuntu starts kind of normally, but then the screen goes black and I get this:

[I][B]busybox v1.17.1 (ubuntu 1.17.1-10ubuntu1) built-in shell (ash)
enter 'help' for a lsit of built-in commands.

(initramfs) mount: mounting/dev/loop0 on//filesystem.squashfs failed: input/output error
can not mount dev/loop0 (/cdrom/casper/filesystem.squashfs)on //filesystem.squashfs[/B][/I]

I've tried both CDs on 2 different machines HP dv9000 (they are slightly different). In both of them 10.04 ran fine. On one of them I tried updating to 10.10 and it was a disaster. I lost the ability to boot up at all. I aborted the update to 10.10 on my second laptop. That's when I tried to install 11.04 from the CDs and got the error message.
Can anyone help me?

thanks

---

### Post by eriknyk on 2011-05-03
I got the same... :(

---

### Post by ricethins on 2011-05-03
I actually solved this problem. It seems to be an issue of the CD burning software/hardware. I tried burning the ISO file using an iMac instead of the HP laptops and the resulting disc worked.
However, other issues have arisen. The 11.04 release seems to work but if left unattended for a while, the screen turns white and although you can see the cursor move, nothing works, not even Ctrl-Alt_Delete. I have to turn off the power to reboot my laptop.
I am not installing 10.10 or 11.04 in any other machine until I find a solution to this problem.

---

