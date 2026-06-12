---
title: "Ubuntu Netbook 10.10 Installation Issue and Solution"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by jaboobie on 2010-12-27
I recently upgraded my HP mini 1000 from Netbook 10.04 to 10.10 using the online upgrade tool.  It worked fine for a few hours but while I was downloading some torrents, everything froze up.  Then it refused to reboot only displaying the 'initramfs' prompt and it wouldn't let me run a disk check (i think it said "disk in use").  I tried to re-install from a USB stick but the install just hung forever and wouldn't go past the first page.  I could run Netbook 10.10 from the Try Ubuntu button, but I couldn't access any disk utility tools.  It wouldn't let me delete any partitions or format or even run any tests on the hard drive.  I was thinking the drive must have failed.

Just to try it out I ran Puppy Linux from a USB and that let me delete partions using gParted.  Then I partioned the drive to install Puppy and that was a success. I would have left it there but I couldn't get wireless to work (Broadcom issues).  So I was thinking that being able to partion the drive may have made installing Netbook 10.10 possible so I tried installing that again and it worked this time.

I'm not sure whether I really did anything useful or what actually worked but I saw a lot of posts describing the same problems and this was a work around that worked for me.

---

