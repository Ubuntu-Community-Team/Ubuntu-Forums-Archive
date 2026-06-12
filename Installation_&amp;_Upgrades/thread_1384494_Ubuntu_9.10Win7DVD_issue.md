---
title: "Ubuntu 9.10/Win7/DVD issue"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Turbojoe on 2010-01-18
Bear with me and I'll try to give the best picture I can of what is happening:

Was using 9.04 and Win XP dual boot with no problems. Then I "upgraded" to Win 7 and now no IDE DVD in Win 7. Also lost the boot loader and it boots straight to Win 7. The DVD was an older drive so I bought a new SATA DVD. Now boot fails with grub error 22 if the DVD is plugged in. I can unplug the DVD and it will boot normally to Win 7 but no DVD operation and no Ubuntu. I was going to format the entire drive and start all over with XP/Ubuntu. I'm going to lose way too much if I do that though. I need to fix this.

Here's what I've got on one drive: 
Win 7 is on sdb1
Ubuntu 9.04 (failed install) is on sdb7 swap on sdb8
Ubuntu 9.04 (Artistx distro) is on sdb5 swap on sdb6 (worked)

I used the 9.10 live disk and formatted the old failed install sdb7 and sdb8 partitions and installed 9.10 to that partition. Install went fine and system restarted. On restart after about 30 seconds at "grub loading" it came up "error: no such disk". I hit enter and it came up grub rescue>. I'm lost at this point. I obviously messed up something during the install.

Grub is not working since Win 7 but is still getting in the way of the DVD operation in Windows. If I can get a working boot loader I'm certain that my troubles will be over and I can use both operating systems without a complete reformat. I'm open to suggestions on how to fix the mess that I've created for myself.

Joe

---

