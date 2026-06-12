---
title: "grub blowup"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2011-12-28
I am having issues with a multi boot compuer. I have grub installed on the MBR of a drive with Ubuntu. I have windows XP on another drive. Windows was hanging while booting, so I was checking to see if there was an issue with the motherboard. I unplugged all of the drives except the windows drive, forgetting the grub2 was on one of the drives I unplugged. I got a device not found error. I plugged the drive with ubuntu back in, but now I get "error: symbol not found: 'grub_putchar'.

I have tried the drive in every sata port, including in a new sata pci card that I know works. I am currently at a grub rescue prompt. What in the world do I do to get this going again?

LMHmedchem

---

### Post by darkod on 2011-12-28
How many drives do you have?

You might have been booting not from the drive you thought, but from another one. And if that one is unplugged, it won't work.

You can either continue with trial and error, or connect all disks and run the boot info script from the link in my signature. The instructions are there. Post the results and also add the booting sequence of the disks, or at least what you think is the booting sequence.

---

### Post by LMHmedchem on 2011-12-28
I definitely had the drive plugged in that has grub on it. It is possible that the sata controller on my board is going or is going. I decided to try again with the windows drive and linux drive plugged into the sata pci card. I put in a supergrub2 CD and tried to boot from that.

I did, find any grub2 config file, and it found one. I loaded the file and was able to boot into windows. I presume I will also be able to boot into ubuntu that was as well. I will be leaving things in the sata card for now, so how do I get the grub menu to appear normally at boot again (without having to use the supergrub disk)?

Should I boot into ubuntu and run the boot script, can I just try update grub, or do I need to re-install grub, etc?

LMHmedchem

---

### Post by LMHmedchem on 2011-12-29
I tried to do update-grub from inside ubuntu and it did find all the installed OSs. When I restart, I still get a grub rescue prompt, but I can boot using the supergrub2 CD.

I'm not sure what to do next. Is there an issue with the boot drive being connected via a pci sata card? I can't think of what that would do, but who knows. Do I need to uninstall grub and the reinstall, or do I need to see if there is something wrong with the MBR of the drive where grub is installed?

I will go back into ubuntu and run the boot script and post it. My motherboard doesn't have a boot sequence for the available hard drives. I can set a generic device, like CD, HDD, etc, but not the specific hard drive. I will look a bit more at the, but I have never seen an option to specify a boot order among the available drives.

LMHmedchem

---

### Post by LMHmedchem on 2011-12-29
I have attached the results from the boot info script here.

LMHmedchem

---

### Post by darkod on 2011-12-29
I can't see anything wrong except this:
You have grub2 on both /dev/sdc and /dev/sdd. The one on sdc is looking for the config files on sdc1, your ubuntu root partition which is correct.
But the one on sdd says it is looking at sdd1 which is your XP partition. That looks like broken grub2.

Most boards since few years ago would have separate option for the order of the HDDs, just because more and more people have multiple disks. In that case, selecting only HDD as boot device means nothing, you need to specify which HDD.

If you are sure that there is no option to select which HDD to boot from, to avoid the possibility of errors I suggest installing grub2 on all of your disks. It might be an overkill, but at least you know you have it there regardless which disk you boot from.

To do this from live mode do:
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --root-directory=/mnt /dev/sdd

After that you have grub2 from your ubuntu install on the MBR of all HDDs. Reboot and see if it helped.

---

### Post by LMHmedchem on 2011-12-29
My motherboard is about 3 years old. Maybe there is a hdd order option in the boot menu (as opposed to the bios).

While I was waiting for responses, I tried using boot-repair,

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

by downloading the boot repair iso, burning to a CD, and then booting with the CD.

I did re-install grub and forced the location for grub to hdc (the drive where the ubuntu install is). I presume this means the mbr of hdc, since the default option was hdc1 which I took to mean that partition and not the mbr. This worked and I have my grub menu back when I restart.

I thought I removed all the installations of grub and just left the one on the mbr of sdc before, so I'm not sure why there is still another grub hanging around.

Is there are good writeup on how to re-configure the grub menu? I would like to delete the older kernels I won't ever use and re-order some things. You used to just be able to edit the config file, but I seem to remember that you didn't do that with grub2.

I am still trying to figure out if my motherboard sata controller is working or not. That would involve moving some of the drives to different sata ports. If I do that to test, is that going to break grub again? I will probably not move the drive that grub is on, but the ssd that windows is on.

Thanks for the help, I've been in the weeds for almost a week with this and it's nice to be almost back to normal.

LMHmedchem

---

### Post by darkod on 2011-12-29
What exactly you want to change in the grub menu?

I always prefer to use manual changes in the files or permissions, as opposed to any GUI software. But I usually don't need many changes.

For example, if you want to omit the memory test (how often do you test the memory), you just make the file not executable:
sudo chmod -x /etc/grub.d/20_memtest86+

That way you still keep the file, and can make it executable again (+x) when you want to include it in the menu. Of course, with grub2 after every change you do:
sudo update-grub

For getting rid of earlier kernels you need to deinstall them. update-grub will stop locating them and remove them from the menu. You can use Aptitude or do it in command line with apt-get. Make SURE you DON'T remove all of them. You need at least one to boot. :)

If I remember correctly the kernel file is linux-image-2.6.32-xx-generic.

---

### Post by LMHmedchem on 2011-12-29
> **darkod said:**
> What exactly you want to change in the grub menu?

I always prefer to use manual changes in the files or permissions, as opposed to any GUI software. But I usually don't need many changes.

For example, if you want to omit the memory test (how often do you test the memory), you just make the file not executable:
sudo chmod -x /etc/grub.d/20_memtest86+

That way you still keep the file, and can make it executable again (+x) when you want to include it in the menu. Of course, with grub2 after every change you do:
sudo update-grub

For getting rid of earlier kernels you need to deinstall them. update-grub will stop locating them and remove them from the menu. You can use Aptitude or do it in command line with apt-get. Make SURE you DON'T remove all of them. You need at least one to boot. :)

If I remember correctly the kernel file is linux-image-2.6.32-xx-generic.You seem to have covered some of it here. I do usually leave the memtest, but I want to re-order the entries and remove some of the old kernels. I will try apt to get rid of the old kernels, but how do I change the order they appear in the menu?

What do you think (if anything) will happen to grub if I change sata ports on some of the drives (not the drive where grub is installed)?

LMHmedchem

---

### Post by darkod on 2011-12-29
> **LMHmedchem said:**
> You seem to have covered some of it here. I do usually leave the memtest, but I want to re-order the entries and remove some of the old kernels. I will try apt to get rid of the old kernels, but how do I change the order they appear in the menu?

What do you think (if anything) will happen to grub if I change sata ports on some of the drives (not the drive where grub is installed)?

LMHmedchem

It depends, moving disks is OK for ubuntu, but the problem is that the order of the disks can change, and since we are unsure how the computer decides which HDD to boot from, it might not try to boot from the correct one.

As for reordering, the short way has one limit:
ubuntu followed by other OSs or,
other OSs followed by ubuntu

The numbers on the files in /etc/grub.d select the order. Since the ubuntu file 10_linux starts with 10 and the os-prober is 30, ubuntu is at top. I have windows at top this way:
sudo cp /etc/grub.d/30_os-prober 06_os-prober (make a copy with lower number)
sudo chmod -x /etc/grub.d/30_os-prober (make the original not executable but it's still in the folder for future use)

That will change their order in the menu because 06 is read before 10.

The longer way is playing with 40_custom. You can copy the current entries from grub.cfg into 40_custom and then they will be in the order you copy them but if you leave the 40 it's again read after ubuntu (10). If you change the 40 into lower number, it's not very different from the above procedure with os-prober.
If you use the 40_custom file you can disable os-prober and it will not scan for OSs. Also, putting entries into 40_custom is usually for other OSs, I have never read someone putting the ubuntu entry in custom. From that point of view, it's very similar to using only 10_linux and 30_os-prober with eventually changing the numbers.

I have never gone into more complex moves around, and I have only 2 OSs anyway.

---

