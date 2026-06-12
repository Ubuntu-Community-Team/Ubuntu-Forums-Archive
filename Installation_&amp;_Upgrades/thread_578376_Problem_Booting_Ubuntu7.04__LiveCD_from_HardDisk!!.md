---
title: "Problem Booting Ubuntu7.04  LiveCD from HardDisk!!"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2007-10-17
Hello All,

           I  want to store the Ubuntu7.04  LiveCD  iso on hard disk  and boot  the same  from hard disk.I have done the following procedures but  some problems arises.Here's  what i've done.

            I   created an iso image of Ubuntu 7.04  and stored it in my root  directory on Redhat Enterprise Linux 4. I have *extracted  (vmlinuz and  initrd.gz from /casper from theLiveCD.)Then i  created a folder named "Ubuntu" in /boot directory and copied the  *extracted  file into this directory.

After this i have added the following lines to grub


kernel      /boot/Ubuntu/vmlinuz
root (hdb 0,7)/root/ubuntu7.04.iso rw
initrd  /boot/initrd.gz


And booted this entry.And booting starts up(showing it found vmlinuz and initrd) and goes on  displaying it detected harddisk ,cdrom,dvd .

At this point it says" check root=args or modules missing cat  /proc/modules ---- does not exists!!

and drops to a console like below

(initramfs)

My System Specification is:
intel celeron processor,192 Ram,Samsung ATA Hard disk,Samsung CD-ROM,Sony DVD-Writer.
(At this Configuration,i had earlier successfully installed Ubuntu7.04 )

My root partition of Redhat is on /dev/hdb8 and swap space is 512MB  on /dev/hdb9

Any help will be appreciated.

Thanks in advance...

---

### Post by PmDematagoda on 2007-10-17
Did you extract and copy everything from the Live CD .iso? Did you also copy the hidden files?

---

### Post by logos34 on 2007-10-17
> **ivikas said:**
> I  want to store the Ubuntu7.04  LiveCD  iso on hard disk  and boot  the same  from hard disk.I have done the following procedures but  some problems arises.Here's  what i've done.

I   created an iso image of Ubuntu 7.04  and stored it in my root  directory on Redhat Enterprise Linux 4. I have *extracted  (vmlinuz and  initrd.gz from /casper from theLiveCD.)Then i  created a folder named "Ubuntu" in /boot directory and copied the  *extracted  file into this directory...

You can't boot and run the livecd from hard disk.  The most you can do is use the desktop .iso for an install from hard disk (see [this howto]("https://help.ubuntu.com/community/Installation/FromLinux")).  Even so you need to create a separate 'holding' partition for the contents.

You might check into running Feisty in a Virtual machine--VMPlayer or VMWare Server.

---

### Post by PmDematagoda on 2007-10-17
I tried what you were trying to do myself but weren't able to, I believe it doesn't work since you are not using the Live CD properly, the outside components may be clashing with those of the Live CD as the Live CD focuses on running on RAM but the normal kernel or startup files do not. 

So it would be easier for you if you tried it by burning the iso to a CD at 4X and installing it.


Btw, where did you find these instructions? They may not work now, but may be if I did some tinkering about they may.:)

---

### Post by ivikas on 2007-10-18
i have seen about the article from the following website:

[http://linuxfromscratch.org/pipermail/livecd/2007-July/004495.html](http://linuxfromscratch.org/pipermail/livecd/2007-July/004495.html)

                          Moreover, i have seen a live demo of booting LiveCD OS' from hard disk at my college.A person came from  US, stays here in india, not a programmer, he tests almost all Linux flavours and makes a living from it.He stored about 7 to 9 OS (LiveCD--Linux) and booted from hard disk.I  requested him to show the  grub configuration but he refrained from it by saying it's "Trial and Error" method and some boots from iso whereas other boots from the folder(Directory) Locations.

                            Reading the above post and having seen the demo i felt that it can be done.I think that hard disk  is only a storage location(like CD) and if boot succed then all contents will be loaded into memory.OR Still may be we have to edit some codes to make it boot from harddisk(without installing) like when we finish the live session "we are prompted to remove the media"  Putting all this what you feel.??

---

### Post by logos34 on 2007-10-18
Ok, I had a look at the link as well as the LFS website and my suggestion is to try this first with the LFS livecd (Stable x86 iso: lfslivecd-x86-6.2-5.iso) to see if it works as advertised.  *IF* it does, then (and only then) you can start thinking about adapting it for ubuntu.  It would be really neat if it did.

---

