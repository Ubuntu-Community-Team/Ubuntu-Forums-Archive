---
title: "I would like to reformat but there is a GRUB error"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by mgear on 2007-10-24
As title says  I would like to reformat but GRUB 1.5 has error 22 and so it will not let me boot.I have also lost all of my disks for Xp Pro and Ubuntu.Can anyone help me?

And yes I have checked things and none help:mad:.

---

### Post by logos34 on 2007-10-24
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by taurus on 2007-10-24
When you first turn on your computer, press F2 or some other key to get into the BIOS.  Then, change the boot order from harddrive first to CD-ROM.  Save the change and reboot.  Now, your machine should boot from the CD-ROM first if there is a bootable media; otherwise, it will bypass CD-ROM and boot from the harddrive.

---

### Post by mgear on 2007-10-24
I really do not get that page as I am not good at computers at all.And if the helps it was on an older laptop called the IBM Thinkpad T-21.

---

### Post by mgear on 2007-10-25
That didn't work at all.

---

### Post by DeadToad on 2007-10-25
mgear,
First, you say you want to reformat your hard drive, right?
Second, you say you cannot boot into Windows, right?

If Yes is the answer to both of these questions, I assume you had Ubuntu installed on your partitioned hard drive with Windows on part of the partition, right?

So, you deleted Ubuntu, right?
And now, when you restart your computer, GRUB is giving you an error message, and not letting you boot into Windows, right?

If this is the case, you have to use SuperGrubDisk to make an .iso boot disk and boot up with it in your Cd-Rom drive.  Once there, choose Language/Windows/Fix Boot Windows to repair the MBR (Master Boot Record) so it removes GRUB (the Linux loader) and allows you to boot to Windows only.

It took me 6 attempts to get mine working again, after removing Linux Ubuntu from part of my partitioned hard drive, and using SuperGrubDisk to repair the MBR, before I could boot back into Windows.

Here's the link to SuperGrubDisk: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Download the .iso CD image and burn it to a CD, or if you have a floppy drive, use the floppy image.
Good luck.
DeadToad

---

### Post by under_it on 2007-10-25
Hey This is the same problem that I had last weekend.  Ok so here is what you do.

Bust out your trusty XP install disk, boot that up, when it finally is done booting there will be and option for the recovery console.  select the recovery console.  From the prompt you need to type fixboot enter.  let it do that then type fixmbr,
It will probably come up asking you if you want to do this and telling you that you risk damaging the system but it will work trust me.  

Grub hosed my system and I was stuck with the same issue.  I also deleted my ubuntu partitions, the swap and the system before I fixed my boot and MBR.

Best of luck to you.

---

### Post by mgear on 2007-10-27
Thanks for all of this help.

---

