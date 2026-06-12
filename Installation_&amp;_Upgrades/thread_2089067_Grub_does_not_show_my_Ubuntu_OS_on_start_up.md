---
title: "Grub does not show my Ubuntu OS on start up"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by DoktorA on 2012-11-28
I have a dual boot Win XP and Ubuntu system.

It was working fine with 12.04.

Yesterday I upgraded to 12.10. Along the way I said "keep" whenever it asked me if I wanted to keep my old config settings.

Now when it boots up I only get two options - Windows, or Win Recovery - in Grub. Can anyone help me recover Grub so that it "sees" my Ubuntu OS please.

Thanks,
Neil

---

### Post by darkod on 2012-11-28
If it asks about grub upgrade, that's not about keeping old settings, you need to tell it to 'use package maintainers version' or similar.

Do you know which one is your root partition? If you do, it might be easier to boot it from the grub command line. Or if not, you can boot the computer into a live session with the ubuntu cd and try it from there.

---

### Post by DoktorA on 2012-11-28
Thanks,

I booted to a live CD and I can see the partitions:

/dev/sda1 - ntfs 2GB
/dev/sda2 - ntfs 38GB boot - I think this is Windows
/dev/sda3 - ext3 11GB      - I think this is Ubuntu
/dev/sda4 - linux-swap


But I am not sure where to go from here. Can I edit grub from the live CD and change my login settings?

---

### Post by oldfred on 2012-11-30
Best to use Boot-Repair. The keep or package maintainers is a lost cause if you have customized whatever it is updating. You almost always have to have package maintainers version to work correctly with the new version, but then lose any custom settings. I stopped upgrading and just do new installs. But I learned that if modifying any system file to separately back that up and then always accept version offered. Then I could go back to my save file and add settings if needed.

         Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

