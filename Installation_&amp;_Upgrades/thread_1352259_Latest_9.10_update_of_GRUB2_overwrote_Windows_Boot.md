---
title: "Latest 9.10 update of GRUB2 overwrote Windows Boot on a separate drive"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by noob12 on 2009-12-11
I just ran update manager this morning and the latest 9.10 update seems to have included changes to GRUB2 that silently overwrote my Windows MBR and boot loader on a separate hard drive!  I had been running 9.10 with dual boot happily until now.

This is really terrible behavior. I can only say that after lots of goodexperience with Ubuntu since 6.x, I am really disappointed with GRUB2 in 9.10.  It is just not ready for prime time and should not have been adopted.  The rest of 9.10 is just great.

The following page has tips on how to fix your MBR and boot sector using the bootrec.exe tool on the original Windows installation CD/DVD.
[URL="http://support.microsoft.com/kb/927392"]
http://support.microsoft.com/kb/927392[/URL]

I was able to recover after running both
```

bootrec.exe /FixMbr

```
and 
```

bootrec.exe /FixBoot

```

I only hope this doesn't keep happening on every GRUB2 update.  Perhaps there are ways to get back to good old GRUB.

---

### Post by phillw on 2009-12-11
Slightly puzzled that you would be running 2 boot loaders & not really surprised that they don't get along !!

To have a win area live happily with Grub, or grub2 --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  Is the place to head.

Regards,

Phill.

---

### Post by HandLotion on 2009-12-11
I haven't rebooted since this upgrade just happened.  Is there a way to tell if Ubuntu ****** with my MBR?  Can someone confirm that grub is overwriting the hard drive's MBR without my damn permission? I also use the Windows bootloader and I would be very pissed to discover this VIRUS has infected my MBR.  But if it has, I'd prefer to fix it now while I can still slip a CD into my CD/ROM drive to fix it.

---

### Post by darkod on 2009-12-11
> **HandLotion said:**
> I haven't rebooted since this upgrade just happened.  Is there a way to tell if Ubuntu ****** with my MBR?  Can someone confirm that grub is overwriting the hard drive's MBR without my damn permission? I also use the Windows bootloader and I would be very pissed to discover this VIRUS has infected my MBR.  But if it has, I'd prefer to fix it now while I can still slip a CD into my CD/ROM drive to fix it.

I wouldn't like to contradict the OP but lets not make an issue of it, since you don't even know if it will happen. First of all, even if it does, grub2 still allows you to boot windows so you will not end up with unusable system. I agree it's not supposed to overwrite anything and it depends whether there are curcumstances to do that.
Like is your grub2 hdd first in boot order in BIOS? Don't forget, bootloaders go to the first drive in BIOS (windows bootloader does that too) so that might be part of the "problem".

---

### Post by PRC09 on 2009-12-11
I think I saw an update recently that asked something to the effect in regards to Grub "Do you wish to install the package maintainers version or keep the locally installed version" so maybe that is what happened,but it does ask that specifically so  you do have to choose which one.I selected to keep the installed version and everything stayed as it was.Triple boot
10.04,win7 and xp on seperate drives.Dont know if thats what happened in your case.

---

### Post by darkod on 2009-12-11
> **PRC09 said:**
> I think I saw an update recently that asked something to the effect in regards to Grub "Do you wish to install the package maintainers version or keep the locally installed version" so maybe that is what happened,but it does ask that specifically so  you do have to choose which one.I selected to keep the installed version and everything stayed as it was.Triple boot
10.04,win7 and xp on seperate drives.Dont know if thats what happened in your case.

It might have been, and if the windows drive was first in boot order, the bootloader went there which is to be expected. On the other hand, if grub2 is your main bootloader, why is the windows MBR disk first in boot order?
I am only saying this assuming the above happened.

---

### Post by oldfred on 2009-12-11
Just yesterday I saw where someone installed grub to the PBR and did not want his MBR overwritten.

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by HandLotion on 2009-12-11
> **oldfred said:**
> Just yesterday I saw where someone installed grub to the PBR and did not want his MBR overwritten.

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

I'll remember to do this to prevent this possibility of grub infestation from here on out.
I guess I should simply avoid any updates with the word "grub" in it. 

 I have grub for Ubuntu 9.04 installed in its own partition, same for grub2 for Ubuntu 9.10 installed in its own partition.  So I have assumed that the MBR is safe and inviolate from any version of grub(2) updates. I have purposely avoided any rendition of grub from infecting the MBR of the hard drive where I keep a triple boot of XP/Ubuntu 9.04 and Ubuntu 9.10.  All of my installed O/S are on the first hard drive, which I believe is the only hard drive the BIOS knows about.

As no one has confirmed the OP assertion I have no idea if my MBR is okay or has been infested.  As a safety play, I'll "fix" the MBR with the Windows bootloader whether it needs fixing or not on my next reboot cycle.

---

### Post by presence1960 on 2009-12-11
```
sudo dpkg-reconfigure grub-pc

```

This will choose which MBR GRUB2 should be installed to during updates.
If you run that command and choose which device to have GRUB2 on, all updates to GRUB2 will go to that device only. Please note you must use the arrow keys to move up or down and the space bar to select a device(s).

This will solve the problem of GRUB2 updates going to incorrect MBR.

Sorry oldfred, didn't see you had posted the same already. There must be an echo in here!:)

---

