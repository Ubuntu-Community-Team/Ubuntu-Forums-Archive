---
title: "Day number 10 and I still can't install Hardy Heron on my AMD64 machine"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by getagrip on 2008-08-14
Why is this so difficult? Please somebody tell me what does this software want? I had XP running on the machine for the last 3 years...I tried to install Ubuntu and it completely destroyed XP. 

I  have a 80G Seagate HD and still have the boot disc for the drive. I have used it to completely wipe my HD clean several times now. I've reformatted in NTFS and FAT32/16 and tried to install Ubuntu, I've ran the supergrub routine several times and it still cannot boot. I've downloaded and burned the Iso's several times ...from different machines just to make sure. And when that didn't work I went out and bought a CD.

I've used Windows boot disc and FDISK commands to refresh the HD, and in some instances create partitions. I've tried to allow Ubuntu to control partitioning during the boot from a totally clean HD, I've used Ubuntu to use the greatest free sector to install ...and finally I've tried to use the manual installs...nothing works.

I've tried to use Ubuntu's sudo Fdisk commands and partition the HD from the boot disc .... every time this thing won't boot ...no matter what!! I am not dunce ..I've bought, assembled and  booted nearly every computer I've ever owned .... why can't I boot with Ubuntu?

99% of the time I get the message .."grub loading stage 1.5" ...once I got ...."grub loading stage 2.0"!! 

I've gotten that message so many times I'm beginning to see it in my sleep!! 

I'm here reading again ... the installation instructions from the Ubuntu website ...to see if there is something I've missed! 

They keep saying how Ubuntu is easier to install than Windows ..and I've installed and booted WIN 98, WIN 2000 and XP on new builds. And all the problems I've had in doing so ...combined ...is nowhere near the hell Ubuntu is taking me through right now!!


What does this dam software want??

---

### Post by darco on 2008-08-14
Have you tried  the Alternate cd.....???
good luck

darco

---

### Post by niyonk on 2008-08-14
A quick search suggests that this might be a BIOS problem and maybe you should update it.

And try this when you are at the message:
- grub> root (hd0,0)
- grub> kernel /vmlinuz root=/dev/sda1
- grub> boot

from there it should boot Ubuntu if you installed it on the whole HD

or 
> root (hd0,0)
> setup (hd0)
> exit

to reinstall grub

Good Luck! :)

---

### Post by getagrip on 2008-08-14
My bios is ok ..based on the fact that after Ubuntu destroyed XP, I was able to wipe clean the HD and reformat using the hardware boot CD ..and reinstall XP. 

I've made some changes in the order of boot ..first CD/DVD, then floopy (remember those) ..and lastly the HD. And oh BTW I've uninstalled /deleted XP to ensure there is no complications.

Using Ubuntu boot CD ...from the terminal I did the following:
grub> find/boot/grub/stage1

the result was (hd0,4)

are you telling me to move it?

---

### Post by getagrip on 2008-08-14
when I do 
grub> setup(hd0)
Error 17: Cannot mount selected partition

---

### Post by niyonk on 2008-08-14
then that means you did not install Ubuntu in the bootsector.
You must have installed it in another partition.
Reinstall and choose 'use entire disk' I think...there, you will definately have no problems.

---

### Post by kflorek on 2008-08-15
It looks like you have grub on the MBR, so I imagine what is happening is a confusion in software about which disk is actually hd0. This is (or was) pretty common for motherboads that have multiple hard drive controllers, like both PATA and SATA controllers.

 For general info, here's the way this goes. There are two sorts of boot sectors, (both of which exist outside of any files or file system). One,the MBR or Master Boot Record, is loaded by the BIOS and exists once a hard drive has been partitioned. You have gotten that far, judging by the messages. Then every partition has a boot sector which may or may not have a boot loader put on it. So you can have grub on any of these besides, if you choose, although grub can go directly to a partition without any such (although Windows can't as normally installed).

 What can happen is, after grub receives control, it can have a different idea of which hard drive is designated by hd0 then the BIOS does.(Which is why a BIOS update might fix the problem.) Grub gives a request to the BIOS, I understand, to load off a certain disk, but that disk doesn't happen to be the one that that actually has linux on it, or maybe it isn't even a hard drive but a CD, or doesn't exist at all.

 Grub puts up the the message about loading stage 1.5 as it begins to load a file off the hard disk (such as e2fs_stage1_5) in /boot/grub/, I believe. If the message stays on the screen, it probably means grub crashed there.(Normally it is there so briefly you may not see it.) Which probably means the load (by the BIOS) never happened. What exactly happens in that case depends on stuff that exists in memory at the spot where grub thought the stage 1.5 code was loaded. Usually it would just make the computer crash.

 Putting your hard drive as the first drive on the first cable on the first controller should make the BIOS and grub agree on what is hd0. If not, switching the drive around on different cables could possibly work. OTOH, grub may just switch its idea about hd0 correspondingly to make it still wrong. What you could try is different numbers for the hd like 1 or 2 or ... Like:

- grub> root (hd1,4)
- grub> kernel /vmlinuz root=/dev/sda1
- grub> initrd /initrd.img
- grub> boot

 Unfortunately, when the initial linux starts to load, it may have its own idea of which hard drive it is on, different from grub. That's the function of 

root=/dev/sd1

after /vmlinuz. So it could be perhaps /dev/sd2 or /dev/sd...

---

