---
title: "Bricked my upgrade 13.04-&gt; 13.10"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by mr_si on 2013-10-21
:mad:

I started an upgrade via ssh from my laptop. The laptop powered down and broke something mid install... now the Ub13 box wont boot. 

Grub pops up (it never used to) and Advanced Options / Check for file system errors runs fsck. Apparently /etc/default/rcS is not a file or directory. Had a little more disk activity then (# files / # blocks) ... nothing

What can I do to recover my OS? I'm happy to boot from USB / CD or whatever it needs (don't really want a fresh install as I can't remember how I sorted out the USB TV card thingy).

Ta.

---

### Post by Norway719 on 2013-10-21
I had what sounds like a similar issue yesterday, and I've found through the forums that the first quick fix that everyone seems to jump to for this kind of thing is a thing called "boot repair". You run a live CD session, connect to the internet, download it and install it from terminal, and then run it. It fixed me up in a jiffy and it was easy! Unfortunately, I can't find off-hand the thread that I used yesterday, but I'm positive it was on ubuntuforums.org. I hope this helps...

---

### Post by oldfred on 2013-10-21
After errors grub pops up so you can boot into recovery mode which may get you to to terminal to run repairs.

Often of full fsck is required, but if half upgraded you may need to chroot into system from live installer and run other repairs.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If you cannot boot at all, Boot repair may fix it, but if in a half upgraded state, it may not be able to:
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

