---
title: "I need to install Windows and Ubuntu on the same logical partition"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by user541 on 2017-03-23
As part of the business requirements for a new project we need to install Ubuntu and Windows Server 2012R2 on the same logical partition. I understand something will need to be done with grub but I am not sure what.

Any help would be appreciated!

user541

---

### Post by QIII on 2017-03-23
Hello!

Are you sure of that specification?

For one, I am pretty sure that Windows server has to be installed on a primary partition.  For another, I'm not sure how you'd manage getting two OSes on the same partition short of visualizing.

---

### Post by user541 on 2017-03-23
It was given to me in the business requirements, I was assured it is possible

---

### Post by SeijiSensei on 2017-03-23
I've used Linux for a long time now, and every installation I've ever done requires a separate partition for Windows and Linux.  

I'm also puzzled why you would have both operating systems on a single server in a dual-boot arrangement.  Servers are designed to run continuously without intervention.  Why would you want to reboot the server and change operating systems?

You might consider as an alternative creating two virtual machines running Windows and Linux.  The best host OS for this arrangement would be Linux using any of KVM, VMware, or VirtualBox.

---

### Post by user541 on 2017-03-23
Virtualization is a specification specifically disallowed in our project specification.

---

### Post by user541 on 2017-03-23
We are permited to use Windows XP, I have been informed it is possible with this OS

---

### Post by QIII on 2017-03-23
If you can boot from a primary partition, I suppose you could install Windows on a logical drive.  Ubuntu can install to a logical drive.  But they would have to be different partitions.

This does not ring to me as a sound business project that any organization would undertake.   A server would generally have one OS, but others might be installed as virtual machines. Is this an academic assignment?

---

### Post by user541 on 2017-03-23
My expert is telling me is possible with Windows XP, but he doesn't know how.

---

### Post by QIII on 2017-03-23
Forgive me, but I also have to ask what business would make the decision to use XP?

---

### Post by sudodus on 2017-03-23
Why these limits? They do not make sense. Is this some kind of test - to find out what you do, when facing 'mission impossible'?

---

### Post by QIII on 2017-03-23
I am also failing to see the advantage here.

Only one OS can run at a time.  That means that to switch between the two the machine would have to be rebooted.  This would be a very uncommon and nonsensical business specification.  If both are required to run at the same time, this would be accomplished via virtualization.  I can't imagine any business running XP any longer.

This does, however, sound like something one might get as an academic assignment.

Nobody here is an employee of Canonical, but many of us are professionals in the field.  If I got this specification I would probably walk away from the RFP.

---

### Post by user541 on 2017-03-23
It is a legacy application, these are the requirements to maintain security of the application.

---

### Post by SeijiSensei on 2017-03-23
That makes absolutely no sense.  First, Windows XP is hardly "secure," and installing to one partition, even if it were possible which I'm pretty sure it is not, wouldn't make things any more secure.

Whoever created this specification doesn't seem to know what they are talking about.

---

### Post by oldfred on 2017-03-23
I do not think your expert knows Windows & Linux.
Are you sure it is not same drive, not same partition?
Windows users often confuse drives & partitions as Microsoft uses both terms for a partition.

Windows must boot from a primary partition formatted NTFS with the boot flag.
Ubuntu must use Linux formats not Windows formats.
You do not use obsolete and therefore unsecure versions of operating systems, either Windows nor Linux. 
Windows XP is obsolete & Vista soon will be.

 . Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by The Cog on 2017-03-23
Windows and Linux absolutely cannot be installed on the same filesystem. Windows requires FAT or NTFS, and Linux requires a filesystem that supports *nix file properties.

There used to be a product called wubi that installed Linux inside a windows partition by creating a large file that was used as a logical drive. Maybe this is what they were thinking of, but I think it has been discontinued for some time now. It must be possible to recreate whatever setup wubi used - probably a modified version of the bootloader to boot from the logical drive but I'm not sure.

---

### Post by ubfan1 on 2017-03-23
Well, WUBI still might work on an Ubuntu 12.04 install, but that release is only suported until April 2017, a few more weeks.  You probably get the idea the feedback here that something is wrong with the idea of using obsolete software -- think of the security risk if not the lack of support.  If you are a member of a professional society, reread their code of ethics.   Adding to the "this is a test" idea, maybe the correct response is to update your resumee. ;^)

---

### Post by SeijiSensei on 2017-03-23
WUBI was basically just a virtualization solution, right?  In that case it would be better to use a real virtualization platform.

---

### Post by QIII on 2017-03-23
WUBI created a Windows folder mounted as a loop device, so not really a VM.

It was intended to be a way to test drive Ubuntu and kick the tires.  It would certainly not have been an appropriate choice for a business solution.

---

### Post by yancek on 2017-03-23
Installing windows to a logical partitiion isn't difficult at all and you should certainly be able to do it with xp.  I install W2K 15 years ago to a logical partition without problems.  The problems as pointed out above and in my case, the boot files must be on a primary partition.  And obviously, without virtualization or something like the unsupported wubi, they cannot be installed on the same partition.  Someone needs a new expert.  This machine will not be connected to the internet, will it?

---

### Post by The Cog on 2017-03-23
That's right. Windows wasn't running when wubi booted. It was Linux only, just with an odd way of mounting the root partition (a *nix filesystem inside a file in inside a windows filesystem).

---

### Post by ubfan1 on 2017-03-23
Another thought, if the Windows filesystem is FAT32, you could  boot an Ubuntu ISO file, and with a 4G casper-rw and a 4G home-rw, have some room for persistence and updates.  You said nothing about performance, or required disk, ... so maybe that more limited Ubuntu installation would meet your needs.

---

### Post by ajgreeny on 2017-03-23
Have you considered the possibility that whoever asked for this to be done is mixing up an extended partition and a logical partition.

If the boot files for Windows are on a separate primary partition, the OS files themselves for both Linux (Ubuntu) and Windows could be in logical partitions within the one extended partition.

It still appears to me that the "expert" is either asking for the impossible or is not explaining what is wanted properly as a result of his own lack of knowledge of disks/partitions.

---

### Post by user541 on 2017-03-24
I appreciate all of your help, after a bit of trial and error we have it working as needed according to our posted specifications.

Thanks again, this is why I love the Ubuntu community!

user541!

---

### Post by oldos2er on 2017-03-24
If you can please post the solution, I for one would be interested to know what it was. And when you do so you may mark the thread 'Solved' under Thread Tools at the top of the page.

---

### Post by harrygray402 on 2017-03-28
I'm sorry but if someone is telling you that it is possible, they should also be able to tell you how.  I've been in IT for 20+ years and there is no way that I know of to have two OS's be installed on the same partition.  How can that be a requirement?

---

