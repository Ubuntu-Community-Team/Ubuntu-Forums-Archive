---
title: "Installation with full disk encryption"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by Jeroen De Dauw on 2012-10-13
(Not sure if this should be posted here or in the security section.)

I have a new box on which I want to install Ubuntu with full disk encryption (which I've done many times before) next to a Windows install. Does the later cause any problems if I want to have full disk encryption? Anything particular I should keep in mind when installing (for instance, first Windows or first Ubuntu)?

---

### Post by Mark Phelps on 2012-10-13
Have you done this before when Windows was already on the disk?  Full-disk encryption would encrypt the Window partitions as well (if it worked) and that would STOP Windows from booting because it can't boot if the Boot Loader files are encrypted.

---

### Post by Herman on 2012-10-13
:) Full disk encryption works great in Ubuntu, it uses LUKS, ([Linux Unified Key Setup]("http://en.wikipedia.org/wiki/Linux_Unified_Key_Setup") - Wikipedia, [Official LUKS Website]("http://code.google.com/p/cryptsetup/") - code.google.com. The /boot partitition isn't encrypted, and the Linux initrd.img is able to read the LUKS encrypted file system at boot time.

I don't think the Alternate Installation CD installer gives any option to install beside Windows, It offers to erase the entire disk and install Ubuntu with full disk encryption in LVM. If you did that you wouldn't just stop Windows from booting, you would blow Windows away totally. 

You could install Ubuntu in another hard disk, (giving it the entire disk) and set a dual boot with more than one hard disk, that always works fine for me when I do that.

If your computer has a lot of RAM, you could install Ubuntu first, giving it the entire disc, and then install Windows inside Ubuntu. I would not call that kind of an installation 'dual boot', in my definition of the term.  I'd call it a 'virtual' installation. You boot Ubuntu first and then boot your virtual operating system(s).
I have tried it myself once or twice in a plain (not encrypted) installation and I thought it was a wonderful arrangement. It was very convenient because I was able to toggle instantly between Windows and Ubuntu just by swiching desktops. It's great except Windows takes up room in the hard disk and I don't happen to need Windows for anything. I used VMWare Player when I did it, [VMWare Player]("https://help.ubuntu.com/community/VMware/Player") - Ubuntu Community Docs, [VMware Player]("http://en.wikipedia.org/wiki/VMware_Player") - Wikipedia. Right now I don't see VMware Player available in my system's Ubuntu Software Center, although I think I have all the normal repositories enabled. I can see [Qemu]("http://wiki.qemu.org/Main_Page") instead though. 

Those are two relatively easy ways you can do it. 

If you are an advanced user, and you don't mind doing some extra work there might be other ways you could actually do something close to what it is you are asking and install Ubuntu in an encrypted partition with a Windows partition in the same disk.  I don't think it would be technically impossible. I think the difficulty would be the LVM. It's not hard to 'manually' create a partition somewhere with an encrypted file system. The installer would need to be able to write to it. Normally the Ubuntu (CD just needs a few extra packages installed to enable reading and writing to LUKS. I have never tried using the (Desktop) installer in that way. I know the Desktop CD can easily be used to chroot and rescue a broken system in a LUKS file system.  An integrated swap file (within the encrypted file system) should be simple enough to set up afterwards. All of these ideas would need testing and problems may be encountered. Viewed in that context, you have asked an excellent question, worthy of a respectfull answer. Maybe somebody will come along with a proper solution.

---

