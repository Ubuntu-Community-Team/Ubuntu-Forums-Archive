---
title: "Boot hangs at kjournald"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rdoolen on 2010-04-04
I upgrade to Lucid 64-bit by running update-manager -d. Things seemed to go smoothly until I rebooted. Now every time I reboot it only gets to the following step:

EXT3 FS on sda2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting. Commit interval 5 second

I does this for each of my partitions, ~6, then it just stops doing anything. It doesn't seem to be accessing the drive. I can't get a login screen on any other terminals (ctrl-alt-FX). 

The computer has a KVM. If I switch to the other computer, the information about the keyboard disconnecting shows up on the screen, so it doesn't seem to be locked. However, it doesn't seem to resume booting.

I am not really sure what to even try.

Any help would be greatly appreciated.

---

### Post by jac_tict on 2010-04-10
Same problem after upgrading from karmic netbook remix!

---

### Post by jac_tict on 2010-04-11
rdoolen, look at [http://ubuntuforums.org/showthread.php?t=1441810&page=4](http://ubuntuforums.org/showthread.php?t=1441810&page=4)

---

### Post by rdoolen on 2010-04-14
Thanks, that was it.

---

