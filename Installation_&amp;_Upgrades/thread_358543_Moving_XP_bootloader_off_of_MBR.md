---
title: "Moving XP bootloader off of MBR"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by PartitionMagician on 2007-02-11
I have recently managed to install Ubuntu Edgy 6.10, dual booting with Windows, and I am very happy with it.

I followed the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=56723) to dual boot using Windows' bootloader, which works well. I only have one problem: XP's hibernation. It works, that is not the problem -- it works too well. I hibernate XP, and on resume it loads without displaying the Windows/Linux boot menu. [This Wikipedia article](http://en.wikipedia.org/wiki/Windows_NT_Startup_Process#Boot_Loader_Phase) sheds some light on the reason:
> The boot loader then reads the contents of boot.ini to locate information on the system volume.

At this point, the screen is cleared, and in the Windows 2000 or later versions of NTLDR and IA64ldr which support system hibernation, (Windows 2000 or later), the root directory default volume as defined in boot.ini is searched for a hibernation file, hiberfil.sys. If this file is found and an active memory set is found in it, the contents of the file (which will match the amount of physical memory in the machine) are loaded into memory, and control is transferred into the Windows kernel at a point from which hibernation can be resumed[1]. The file is immediately being marked as non-active, so that a crash or similar doesn't load that outdated memory state anymore. If a state resume fails, the next time NTLDR runs it will ask the user whether to try resuming again or to discard the file and proceed with normal booting.

If boot.ini contains more than one operating system entry, a boot menu is displayed to the user, allowing the user to choose which operating system is to be loaded.
In other words (as I read it), if hiberfil.sys is marked active, boot.ini is ignored.

The problem is, I want to be able to boot Ubuntu even if I hibernated XP the last time I shut off the computer. The scheme I thought up would go something like this:
- Copy XP's bootloader off the MBR, i.e.
dd if=/dev/hda of=xpboot.bin bs=512 count=1
I already did that.
- Move GRUB onto the MBR so it's loaded at boot every time.
dd if=ubuntu.bin of=/dev/hda bs=512 count=1
I most definitely did not do that.
- Configure GRUB to advise it of the new location of XP's bootloader.
I don't know how to do this.

Note that per the post linked above, during the Ubuntu install I installed GRUB to a floppy, and (unexpected by me) GRUB detected Windows XP. So I currently have a boot floppy that does what I want. However, it seems unsound to entrust such a critical process such as booting to a floppy disk, that being an outdated and not incredibly reliable technology, intended only for emergencies.

I hope I've explained my question adequately.  To sum it up: Is it possible to run XP's bootloader if it is not in the MBR? If so, how would I set up GRUB's menu.lst to facilitate this?

---

### Post by Herman on 2007-02-11
> Is it possible to run XP's bootloader if it is not in the MBR? If so, how would I set up GRUB's menu.lst to facilitate this? Yes, because XP's bootloader is not actually situated in the Master Boot Record at all. Only a small area of code is there to point to it.
All you need to do is get grub to replace that tiny bit of code with another tiny bit of code that will make the MBR point instead to the larger part of Grub, in the Ubuntu filesystem, (the Ubuntu partition).
The MBR is only able spare room for a tiny amount of code for the bootloader because the MBR is only 512 bytes in size itself, and some other stuff needs to be able to fit in there too. They call these tiny bits of bootloader code the first stage for a bootloader, or stage1.
NTLDR has a stage1 code, grub has a stage1 code, and so probably too GAG Boot Manager and LiLo bootloaders.

When you have grub written to MBR, which is an abbreviated way of saying grub's stage1 will be written to the appropriate area of the MBR. This overwrites the first stage code of whatever other bootloader might be there at the time. That will basically switch the MBR to point to the greater part of Grub in the Ubuntu partition.
XP's bootloader will not be touched, and neither will anything else in your Windows filesystem (partition).

The Master Boot Record is not part of the Windows partition. If you don't believe me, try doing 'sudo fdisk -lu' in a terminal and look closely at the output. The first partition never begins until sector number 63. The first track of the hard disk is empty except for the MBR, which is situated in the first sector, and when you install grub, the next fifteen sectors are normally embedded with grub's stage1_5.

Many people confuse the first sector of the Windows partition, called the bootsector, with the MBR. Windows bootsector does belong to the Windows partition and writing any code there that doesn't belong there will damage Windows. It's a shame that people get these two terms mixed up. Some people use them interchangeably and it leads to such misunderstandings that others get confused and install grub to the wrong location, which gives grub a bad name through no fault of its own.

Grub can, however be installed to any Linux partition quite happliy, and in fact, it can be a good idea to do so.

If you install grub's stage1 to MBR, your MBR will point to your ubuntu partition where grub's stage2 will load your grub menu from your menu.lst file. For those uf us who install Grub to MBR when we install Ubuntu in the first place, we automatically have a Windows entry that we can just select, which directs grub to the first sector of the Windows partition, where it 'chainloads' (hands over control) to NTLDR.
If you select Ubuntu, then grub will load ubuntu. This arrangement works very well for the majority of dual or multiboot computers.

To write grub's stage1 to MBR, you can use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") or any installed operating system or LiveCD or floppy disk that has grub.
Here's the way I do it,                                                  [Re-install Grub with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
It should be fairly safe to install grub using a grub shell, as the first task is to verify where you are going to install to, and then if you still make a mistake and try to install to the Windows partition it will refuse and give you an error message.
I do not recommend the grub-install command as misinformed users can get into trouble with that one, it will do exactly as it is told to. So avoid using that one, I can't think of any need for it anyway. 

Regards, Herman.

---

### Post by Herman on 2007-02-11
> how would I set up GRUB's menu.lst to facilitate this?You can type your own in by hand, but it would be much quicker and easier to copy and paste someone else's in. That saves a lot of typing and possible typing errors
Now, it will depend on what kind of partitioning setup you have in your machine. The example below will suit most standard installations where Windows XP is situated in partition number 1, and there is only one IDE hard disk. If the Windows installation is on a non-first hard disk, it would be necessary to add more commands. If you have an IDE disk, or the Windows partition is not number1, you can easily edit menu.lst with some minor changes. I or someone here will probably help you with that if requested.
Warning: If Windows is a second Windows install in a logical partition, and someone deleted the first Windows install, that Windows users call their 'boot partition', (another strange use of terminology), the second Windows will probably never be able to boot again, at least I don't know how.

Here is a typical Windows entry for the bottom of the menu.lst file. You can just copy it and paste it there. 
```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                              
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                                 
                                                                 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```When you open your menu.lst file, you must open it with terminal commands using 'sudo' or you will not be able to save the changes.
Here is the command to sue for opening your menu.lst, in case you or someone else reading this might need to know that. You can just copy and paste this to your own terminal too. 
```
sudo gedit /boot/grub/menu.lst
```
Before playing with bootloaders you should make a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")
because it will get you out of most kinds of trouble if something goes wrong.
Regards, Herman :)

---

### Post by PartitionMagician on 2007-02-11
That worked perfectly. Thanks Herman for the great GRUB reference!

---

