---
title: "Windows update broke my grub boot loader"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by sodaa on 2012-12-21
I am currently running windows 7 and ubuntu 12.04 on two separate partitions. The other day I had to use windows for something and it downloaded some updates in the background. When I had finished, I restarted to go back into ubuntu and unfortunately my boot loader wasn't coming up anymore, just a blank screen with a blinking cursor; nothing could be done on this screen accept ctrl+alt+del to restart.

Since I didn't have much on my ubuntu installation, I figured I would just reinstall it and let it set up grub again; however, now the installation process hangs after 'copying files' so I can't reinstall ubuntu 12.04 it seems.

What can I do from here? I can't boot into either OS, I can't reinstall ubuntu. I could just wipe evertyhing and reinstall both, but unfortunately I have a lot of stuff on windows that I can't afford to wipe at this point.

---

### Post by darkod on 2012-12-21
You don't need to wipe windows in any case. If you need to urgently access it, you can use the win7 install dvd or a rescue cd to install the windows bootloader on the MBR and win7 will boot. If you don't have these discs, you can even use linux tools to write a generic MBR that can boot windows.

As for why the ubuntu install stops, you need to make sure the cd or ISO image you used is not corrupted, scratched, etc. You can try making a new cd from a newly downloaded image.

If you really have a proper dual boot on its own partitions (not wubi), windows updates shouldn't break grub. What could break grub is any type of security software that writes/controls the MBR.

---

### Post by sodaa on 2012-12-21
I'm using a thumb drive image; it works fine on my laptop for the installation. 

This is what my drive looks like:

[IMG]http://i1097.photobucket.com/albums/g358/treefingers77/gpart_zpsf3ea5882.png[/IMG]

with the 60GiB partition being my ubuntu 12.04 installation and the 155GiB partition being my windows 7 installation. Can I somehow just reinstall grub somewhere on the drive such that it connects to the two using ubuntu live cd (which I'm in now)?

---

### Post by oldfred on 2012-12-21
You can download Boot-Repair into your live Ubuntu installer.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemic")
    
Is this Windows 7 and did you delete the normally hidden 100MB boot partition that is at the beginning of the drive. You have no boot flag and Windows has to have a boot flag to boot on its own. Grub does not use boot flag and will chain to the boot files, but if you deleted them, then grub has nothing to boot.

       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by darkod on 2012-12-22
Boot-repair can do many things for you automatically, and with a graphics interface.

As for your question about reinstalling grub from live mode, yes you can. Since /dev/sda1 is your root partition, all you need to do in terminal is:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will install grub to /dev/sda which is the MBR of the disk.

Note that oldfred is probably right about the win7 100MB partition. Usually at the start of the disk you have 1MB unallocated space. If you did have the 100MB win7 system reserved partition and deleted it, that might explain why now you have exactly 101MB unallocated space. The numbers match.

That 100MB partition has the win7 boot files on it so you can't boot it right now if you deleted it.

---

