---
title: "WinXP MBR linked to Ubuntu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Bigs11 on 2008-11-09
I have a Sata2 HDD with WinXP Pro on it.
I have just installed Ubuntu on a second IDE HDD, with Grub installed on it's root.
When I select to boot WinXP from the Grub menu, (which is on the IDE HDD), it shows the disk as hd0,0.
This is not the case, as my IDE HDD is hd0,0.
For some reason, Grub doesn't see the Sata disk as hd1,0.
Then again, I would have thought the Sata disk would be hd0,0 and the IDE disk would be hd1,0.
Anyhow, I can enter Bios, and select either disk to boot first depending on which OS I want.
But what I would like to know is if, at this stage, I can edit my boot.ini while in Windows, and add a link to the Ubuntu menu.lst,
so that I can access the Windows menu at boot up from my Sata disk?

---

### Post by Bigs11 on 2008-11-09
Ok, what about this?
I just read a post regarding getting WinXp to work on the same disk as Ubuntu,
and the Op was asked to "Copy the Ubuntu boot sector to a file on your Windows partition:"
with the aim to edit boot.ini, and run a boot menu under WinXP.

How can I do this?
Where do I find "ubuntu.bin"?
Or do I have to generate it?

---

### Post by caljohnsmith on 2008-11-09
Fortunately, you don't need to modify your Windows boot.ini to boot Windows from Grub. How about booting into Ubuntu, opening a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And for your Windows entry, replace it with:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, let me know exactly what happens when you select it from the Grub menu on start up, and also post:
```
sudo fdisk -lu
```
Otherwise let me know how it goes.

---

### Post by Bigs11 on 2008-11-09
> **caljohnsmith said:**
> Fortunately, you don't need to modify your Windows boot.ini to boot Windows from Grub. How about booting into Ubuntu, opening a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And for your Windows entry, replace it with:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, let me know exactly what happens when you select it from the Grub menu on start up, and also post:
```
sudo fdisk -lu
```
Otherwise let me know how it goes.

Thanks for your help, but I probably didn't explain myself well.
I wanted to be able to boot from my Sata disk as Disk1.
I made the mistake of installing Grub onto Disk2 (IDE).
Your commands worked fine, remapping Disk2 to Disk1.

What I ended up doing tho, was installing Grub to my Sata disk (Disk1)
linking to stage1 on the IDE disk. Everythings fine.

My initial question tho, was how can I edit my Boot.ini to link to Ubuntu on "hd1,1"?
Obviously doing away with using Grub.

---

### Post by caljohnsmith on 2008-11-09
You mentioned in your original post that you could boot either drive on start up. If that is the case, I think the best solution is to simply boot the Ubuntu drive (make sure Grub is installed to its MBR), and then add an entry to boot Windows to your Grub menu like I gave in my previous post; that way you can easily boot either OS from your Grub menu. Also, if you do it that way, your Windows drive is untouched, and if anything happens to either drive, you will be able to boot the other drive. I don't see any real advantage to booting the Windows drive and adding Ubuntu to the Windows boot loader (boot.ini) since you can boot the Ubuntu drive directly on start up. So I'm just wondering, what is your particular reason to add Ubuntu to the Windows boot loader? Instead of using the Windows boot loader, I would use Grub4DOS since it is a much more robust solution over the Windows boot loader, and it can be used inside of Windows. It's up to you though. :)

---

