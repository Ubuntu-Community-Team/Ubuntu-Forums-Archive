---
title: "Crash of installed 1810"
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by brisch on 2018-11-14
Upon boot:
     First crash
        Message
            Started Detect the available GPUs and deal with any system changes.
     Second crash
         Message
            Started Raise Network interfaces.
     Third crash
         Message
            fsckd-cancel-msg:  Press Ctrl+c to cancel all filesystem checks in progress.
           System locked no keyboard.

Invoke GRUB
       Select advanced options for ubuntu
       Select Ubuntu with Linux 4.18.0-11 generic (recovery mode)

    Recovery menu
      select network
      select root
           enter apt-get update
           enter apt-get upgrade
      exit
      'Select resume
           total system crash
This is after a fresh install of the ISO
and after first boot.

Lets see recovery suggestions

---

