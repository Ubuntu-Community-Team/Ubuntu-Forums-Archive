---
title: "GRUB- error: no such partition grub rescue&gt;"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by Lottie82 on 2011-11-16
[B]GRUB- error: no such partition   grub rescue>
The following error has been plaguing me.
So here goes:
I had a sony vaio laptop with windows on one partition and ubuntu which was in use on the other. I had enough and restarted my laptop to load windows at the bottom of the screen after pressing the options button during reload. Then from there had the message as above, have read so many threads its unreal as nothing is helping me. I have no disk and no usb with anytging to load or boot from. I am complete novice, i have done as follows [/B]
grub> rootnoverify (hd0,0)
grub> makeactive 
grub> chainloader +1
grub> boot
rootverify did nto work so replaced with set root=(hd0,0) which does work but as soon as i type make active i get unknown command
also it does not say grub it says
grub rescue>

and my ls details are 
(hd0)(hd0,2)(hd0,1)
i have tried all sudo,lido,mbr and any others i come across and they all say unknown command

 Pls can someone understand my rambling and help me?
anything else needed or i can do without the standard get a boot cd??
thank you peeps
peace

---

### Post by drs305 on 2011-11-16
Lottie82,

Welcome to the Ubuntu forums. Sorry about the issue which brought you here.

Did you uninstall Ubuntu? I'm having difficulty understanding what you did when you 'had enough'.

If Ubuntu is still installed on either sda1 (hd0,1) or sda2 (hd0,2), we may be able to get it to boot. If it's not on either of those partitions, you aren't going to be able to do anything from the Grub rescue prompt.

The prompt means that the Grub information found by the BIOS points to a partition or files which Grub cannot find. It can't load modules to boot itself or other OS's unless it can find those files.

You can see what is on sda1 and sda2 but running the following commands:
```
ls (hd0,1)/
ls (hd0,2)/
```

If you don't have a valid Ubuntu installation, you are going to need a CD or bootable thumb drive of some sort (Windows, Ubuntu LiveCD, Boot Repair CD, SuperGrub, SystemRescue CD, etc).

---

### Post by Lottie82 on 2011-11-16
yes i think it was un-installed, i tried both commands and both say unknown filesystem,
so can i down load them apps Windows, Ubuntu LiveCD, Boot Repair CD, SuperGrub, SystemRescue CD, etc) to a usb and then put the usb into the laptop with the grub message and what from there?
as i say i am a super novice and have no idea what bios etc etc means, does, wants to do or might do in the future under duress! again sorry about the rambling
And than you for your reply drs 305, i can see you are very well respected on this site

---

### Post by darkod on 2011-11-16
Did you install proper dual boot or just wubi inside windows? Just two partitions sounds too little.

Does the laptop have a cd-rom, can you boot with a cd? If yes, do you have the ubuntu cd to try and boot it into live mode (the Try Ubuntu option)?

---

### Post by Lottie82 on 2011-11-16
yeah i think your right it may have be more partitions(maybe 3) but i didn't do it. yeah it does have a cd rom but i dont have the ubuntu cd to boot from(or any except a downloaded version of windows 7). cheers

---

### Post by drs305 on 2011-11-16
With the Win 7 CD, you may be able to repair the MBR to point back to Windows. If the Windows boot folder/files are still intact, the repair function should help you get Windows booting again.

I'm not a Windows user, but this post should help:
[http://ubuntuforums.org/showpost.php?p=10049238&postcount=4]("http://ubuntuforums.org/showpost.php?p=10049238&postcount=4")
I believe what you need to run is the 'fixmbr' repair tool.

I don't think you will need to run the commands after the 'fixmbr' one but someone more familiar with Windows can probably provide that answer.

---

### Post by darkod on 2011-11-16
Win7 is actually more advanced than XP for this matter. Boot the dvd and when the first menu appears instead of selecting Install look towards the bottom there will be Repair This Computer option.
In most cases it will detect your win7 and make the necessary repair on the MBR.

In cases this doesn't work there are option to run commands from command prompt but try the automatic option first.

---

