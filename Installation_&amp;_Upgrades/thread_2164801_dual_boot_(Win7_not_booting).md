---
title: "dual boot (Win7 not booting)"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by soumen08 on 2013-08-01
Hello!

I just installed Kubuntu 12.04 alongside Win7. I have done exactly this before, but my hard drive had to be replaced (unrelated reasons) and I had to start again.

Install went through smoothly, I rebooted the system,  when I press enter on the Win7 entry, the splash screen comes up but freezes on 'Starting Windows'.

Kubuntu boots fine.

Running 'bootrec /fixmbr' from the Win7 DVD fixes the MBR and Win7 boots fine after that, suggesting no corruption on Win7.

Something GRUB is doing(Im guessing near the boot) is preventing Windows from booting properly.

Can someone please help me figure out what could be wrong?

Thanks,
Soumen

---

### Post by oldfred on 2013-08-01
When Windows boots the Windows boot loader in the MBR looks for the partition with the boot flag and jumps to that partition boot sector or PBR to continue to boot. All grub does is jump to the same PBR to continue Windows booting. Some have had issues with Windows when it was hibernated? Were you hibernated?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by soumen08 on 2013-08-02
No, I was not hibernated.

I tried boot repair, and I got to the same place. So I reinstalled the MBR from the Win 7 DVD, installed kubuntu on a flash drive, and only ran the bootinfo summary. Here it is [http://paste.ubuntu.com/5940429/](http://paste.ubuntu.com/5940429/)

Thanks!
Soumen

---

### Post by oldfred on 2013-08-02
Boot-Repair can only do limited things with Windows and just shows if it looks like it is configured correctly. Or has correct partition layout and boot files.
Sometimes Windows will not boot from grub when it needs chkdsk, but then from its own boot will auto run the chkdsk. Do you have any other special software with DRM or even some virus checkers have interfered with grub.

A few do use EasyBCD, but most find grub2 works. With EasyBCD you have to compromise grub by installing it to a partition PBR or partition boot sector. That is not really large enough, so it converts to blocklists or hard coded addresses to find the rest of grub in the Ubuntu partition. When grub gets updated it address may change and you have to reinstall grub so then have liveCD/DVD/flash available to fix grub.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by soumen08 on 2013-08-02
When I booted windows after fixing the MBR (using the Win7 DVD) a checkdisk was not performed; at least not explicitly. I didn't understand DRM(digital rights management?), so Im guessing I dont have DRM software that interferes with the boot. I have Comodo Internet Security, and Ive used that forever, so it is a little unlikely that is messing up something.
Are you suggesting I use easy BCD? I remember that as some sort of boot tool. I'd prefer to stay with grub if possible.

---

### Post by oldfred on 2013-08-02
I do not suggest EasyBCD, its just some give up and use it. Most seem to be able to use grub with Windows 7.

There may be something in BIOS as a setting, which we cannot see. Did you change any BIOS settings or update BIOS as that resets everything back to defaults? What computer and BIOS?

---

### Post by soumen08 on 2013-08-03
Nothing changed in BIOS. The computer is Alienware M14XR1. This is the first time I have tried to install ubuntu alongside a windows install made from the DVD that came with the system. Earlier, I had dual booted with whatever version of win7 that the computer came pre-imaged with. At that time, everything had gone quite smoothly.
Are there different versions of Win7? Could this be a problem?

---

### Post by oldfred on 2013-08-04
If your DVD is from the installed version, I would think it should be the same. Often versions of Windows do have special drivers for specific hardware.

---

