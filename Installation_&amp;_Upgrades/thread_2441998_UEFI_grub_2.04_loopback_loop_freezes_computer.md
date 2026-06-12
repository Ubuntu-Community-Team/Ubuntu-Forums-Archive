---
title: "UEFI grub 2.04 loopback loop freezes computer"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by VMC on 2020-04-28
This error has been reported here:
[https://askubuntu.com/questions/1186040/grub-command-loopback-loop-does-not-work-on-ubuntu-19-10](https://askubuntu.com/questions/1186040/grub-command-loopback-loop-does-not-work-on-ubuntu-19-10)

Bug report from Oldfred here:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)

My question is, from the bug report above, post #34 states using an older 2.04 grubx64.efi file.

The link he provided all fail. I found this link of the files, but don't know which deb to download and extract the grubx64.efi file:
[https://mirror.genesisadaptive.com/ubuntu/ubuntu/pool/main/g/grub2/?C=N;O=A](https://mirror.genesisadaptive.com/ubuntu/ubuntu/pool/main/g/grub2/?C=N;O=A)

Has anyone got the hack referred to by post#34 above to work?

---

### Post by oldfred on 2020-04-28
As near as I can tell, he just manually converted to grub 2.02 by changing grubx64.efi.
I made it work just by installing grub 2.02 to another drive, flash drive etc.

My main working install is now 20.04 and grub on main SSD is grub 2.04, so cannot loopmount grub.
But I have older grub on a couple of flash drives & sdb drive. I used 18.04's grub.

---

### Post by VMC on 2020-04-28
I found this link of '[bionic grubx64.efi]("http://archive.ubuntu.com/ubuntu/dists/bionic/main/uefi/grub2-amd64/current/")' and used it. I backed up grubx64.efi and moved bionic grubx64.efi  in its place. It now works. 
All this time, and I didn't know it was loopback error. Finally from grub> prompt, I entered loopback loop etc, and saw that it froze.

---

### Post by ping-wu on 2020-04-29
Will give it a try in the next couple of days.  Thanks a whole lot!

---

