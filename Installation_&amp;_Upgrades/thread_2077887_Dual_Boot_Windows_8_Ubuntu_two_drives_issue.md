---
title: "Dual Boot Windows 8 Ubuntu two drives issue"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by BatPenguin on 2012-10-29
Hello everybody,

I'd really appreciate some help...I have two hard drives, sda and sdb, and I had a nicely working Ubuntu install going on sda. Now, I went and installed Windows 8 Pro onto sdb and got myself a nicely running Windows 8 install, losing ability to boot to Ubuntu (which I knew). Now I wanted to get a dual-boot, so I was hoping this great utility would help me do that, but so far it only restored ability to boot to Ubuntu, but the Windows 8 option only reboot the machine again. I'd really appreciate any help, I'd really not like to lose either install, so if somebody could help me set this straight, it'd be great.

Boot-repair gave me this: [http://paste.ubuntu.com/1315867/](http://paste.ubuntu.com/1315867/)


Thanks!

---

### Post by oldfred on 2012-10-29
Moved to your own thread. Boot-Repair thread is more for issues with Boot-Repair. Many users have somewhat different issues and best to handle in a separate thread.

Have you tried booting from sdb? Some recently have had issues with the drive mapping. But your Windows boot stanza does show drivemap command for Windows boot stanza. Grub picks up from BIOS the boot drive as hd0 even if booting from sda or sdb. I think Windows wants to be the boot drive as reported by BIOS so that is why grub adds the drivemap to make Windows think it is on BIOS boot drive. 

Usually Windows is in sda, but it really should not matter.

If that does not work. Does installing the Windows boot loader into sdb and directly booting from BIOS boot Windows correctly. Some have just had issues with grub and have made it work that way.

---

### Post by BatPenguin on 2012-10-30
> **oldfred said:**
> Moved to your own thread. Boot-Repair thread is more for issues with Boot-Repair. Many users have somewhat different issues and best to handle in a separate thread.

Have you tried booting from sdb? Some recently have had issues with the drive mapping. But your Windows boot stanza does show drivemap command for Windows boot stanza. Grub picks up from BIOS the boot drive as hd0 even if booting from sda or sdb. I think Windows wants to be the boot drive as reported by BIOS so that is why grub adds the drivemap to make Windows think it is on BIOS boot drive. 

Usually Windows is in sda, but it really should not matter.

If that does not work. Does installing the Windows boot loader into sdb and directly booting from BIOS boot Windows correctly. Some have just had issues with grub and have made it work that way.

Thanks so much for the reply and moving this to a proper thread!

Yes, I've tried booting from sdb and now I'm getting further. I received some email help from boot-repair and thanks to that, I'm at the point where by setting the computer to boot from sdb, I get into Windows (no boot menu shown, grub or Windows, just straight boot to Windows), and booting from sda, I get Ubuntu. But the sda boot menu option for launching Windows causes just a reboot.

I was adviced to do this:

Please:
1) run Boot-Repair, answer YES when asked if sda is removable, then click "Recommended Repair".
2) reboot the PC, setup your BIOS to boot the Windows disk

And that's how I got this far. I'm at work now, so my troubleshooting last night was left sort of unfinished, the last thing I was asked to do is run Boot-Repair --> Create BootInfo and provide new bootinfo URL but I haven't gotten around to that, I'll do it tonight. The person helping me via email, Yann, sounded like this is a bug and should be reported to grub, so I'm unsure whether it's even possible to fix this properly. 

So basically I'm now confident that both OS's boot, but looks like I have a broken menu so I need to change between them with BIOS. Would be great to be able use a boot menu, grub or windows, to switch between them and not go through BIOS.

---

### Post by YannBuntu on 2012-10-30
Hello

original Boot-Info: [http://paste.ubuntu.com/1315490](http://paste.ubuntu.com/1315490)

> **BatPenguin said:**
> 1) run Boot-Repair, answer YES when asked if sda is removable, then click "Recommended Repair".
2) reboot the PC, setup your BIOS to boot the Windows disk

This restored a generic MBR in the Windows disk (sdb). 

> **BatPenguin said:**
> The person helping me via email, Yann, sounded like this is a bug and should be reported to grub

To summarize:
- booting BIOS --> sdb MBR (generic MBR) --> starts Windows
- booting BIOS --> sda MBR (GRUB) --> Ubuntu entry --> starts Ubuntu
- booting BIOS --> sda MBR (GRUB) --> Windows entry --> does not start Windows

So i think that the Windows entry in grub.cfg is incorrect. This must be reported to GRUB devs.

grub.cfg will probably be the same as in the original Boot-Info, but i prefer to confirm via the new Boot-Info that BatPenguin will provide.

---

### Post by BatPenguin on 2012-10-30
> **YannBuntu said:**
> Hello

original Boot-Info: [http://paste.ubuntu.com/1315490](http://paste.ubuntu.com/1315490)



This restored a generic MBR in the Windows disk (sdb). 



To summarize:
- booting BIOS --> sdb MBR (generic MBR) --> starts Windows
- booting BIOS --> sda MBR (GRUB) --> Ubuntu entry --> starts Ubuntu
- booting BIOS --> sda MBR (GRUB) --> Windows entry --> does not start Windows

So i think that the Windows entry in grub.cfg is incorrect. This must be reported to GRUB devs.

grub.cfg will probably be the same as in the original Boot-Info, but i prefer to confirm via the new Boot-Info that BatPenguin will provide.

OK, here we go: [http://paste.ubuntu.com/1318137/](http://paste.ubuntu.com/1318137/)

Yes, the summary you pasted is exactly right. Thanks for help again!

---

### Post by YannBuntu on 2012-10-30
ok.
So the incorrect entry is:
```
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 8A62D54B62D53C9F
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

Your problem may be similar to [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281)

Please type:
```
gksudo gedit /boot/grub/grub.cfg
```
in a terminal to add the following entry in your /boot/grub/grub.cfg file:

```
menuentry 'Windows on /dev/sdb1 MANUAL' {
   insmod part_msdos
   insmod ntfs
   set root=(hd1,1)
   chainloader +1
}
```

then reboot the pc, and tell me if the 'Windows on /dev/sdb1 MANUAL' entry loads Windows or not.

---

### Post by BatPenguin on 2012-10-30
> **YannBuntu said:**
> 
Your problem may be similar to [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281)

Please type:
```
gksudo gedit /boot/grub/grub.cfg
```
in a terminal to add the following entry in your /boot/grub/grub.cfg file:

```
menuentry 'Windows on /dev/sdb1 MANUAL' {
   insmod part_msdos
   insmod ntfs
   set root=(hd1,1)
   chainloader +1
}
```

then reboot the pc, and tell me if the 'Windows on /dev/sdb1 MANUAL' entry loads Windows or not.

Thanks again.

Alright, I tried this - added the entry, rebooted and selected it, but unfortunately the effect is the same as before: blank screen for a moment and then reboot.

---

### Post by YannBuntu on 2012-10-30
ok.
I have no other idea.
Please report the bug to GRUB developpers:
1) Create your [Launchpad]("https://launchpad.net/") account if you haven't yet
2) Login to your Launchpad account
3) From your Ubuntu, open a terminal, and type:
```
ubuntu-bug grub2
```
Press Enter.
This will gather information, and open a new internet window.
4) Fill in the bug title, eg "invalid Windows entry in GRUB1.99 menu"
5) Fill in the bug description, eg > "Ubuntu12.04 and Windows8 dualboot on 2 different disks. Default Windows entry in GRUB menu fails to load Windows:
```
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 8A62D54B62D53C9F
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

Original thread: [http://ubuntuforums.org/showthread.php?t=2077887](http://ubuntuforums.org/showthread.php?t=2077887)
6) then finish the bug report, and indicate us (here) the link (URL) to the report so that we can follow-up.

---

### Post by BatPenguin on 2012-10-31
> **YannBuntu said:**
> 
6) then finish the bug report, and indicate us (here) the link (URL) to the report so that we can follow-up.

Alright, done, bug is here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073630](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073630)

Hopefully something can be figured out to fix the situation later, I'll be using my BIOS to switch for the time being.

Thanks for the help YannBuntu!

---

### Post by Gimmemabrewski on 2013-04-15
Ran across this thread while having similar issues.  I have Linux Mint 14 installed on an ssd and have just recently installed Windows 8 on my secondary hdd.  Windows booted fine from grub with the default entries until Windows was updated.  Then it would start to boot Windows then suddenly the pc would restart.  I decided to try Yannbuntu's suggestion and YAY! it worked.  I decided to further investigate and found that simply removing the option "--class os" windows would then boot.  I am using burg.cfg rather than grub.cfg if that is relavent.  Not sure what the class options are for.  Maybe someone will enlighten me :)

---

