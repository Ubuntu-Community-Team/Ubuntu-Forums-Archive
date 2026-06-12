---
title: "[SOLVED] Dual Boot - Grub Will Not Show Up"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by sunkssss on 2008-10-25
Hello All,

I've spent all morning and afternoon trying to get a dual boot setup with Windows XP. I have XP installed, and have tried installing Ubuntu four times already, and have a feel it's time to ask for some assistance. I have installed Ubuntu before, and have had dual boot setup on this computer before, however I just can't get it to work this time.

I am a pretty big noob, so from what I'm observing my Ubuntu partitions will just not mount. After installation I'll boot using the live CD (since otherwise it just boots straight to XP) and looking at the partitions they're marked (do not use partition). I don't know why setup is doing this, since I clearly am marking the mount points and file systems correctly.

By correctly, I mean I have 2GB swap and 30GB / ext3 partitions. I have tried having a 50Mb /boot partition along with the other two, and the last time I attempted setup I just tried using "use largest continuous free space" instead of trying a manual partition, however I'm still booting straight to XP. 

Any assistance would be greatly appreciated.

---

### Post by caljohnsmith on 2008-10-25
When you get to the last screen in the installation process where there is an "advanced" button, are you clicking that and changing the default setting of where to install Grub? Also, open up a terminal (applications > accessories > terminal), and please post:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

```
And we can work from there. :)

---

### Post by sunkssss on 2008-10-25
I have not been clicking the advanced button, because I never had to before. Perhaps that has been the problem, however if I'm not going to be using the default setting what should I be changing it to? 

> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25dc25db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81931499    40965718+   7  HPFS/NTFS
/dev/sda2        81931500   234436544    76252522+   5  Extended
/dev/sda5        81931563   228380039    73224238+  83  Linux
/dev/sda6       228380103   234436544     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie "missing operating system"
Missing operating system


---

### Post by caljohnsmith on 2008-10-25
That's really strange, because that second command you ran basically confirms that you do indeed have a Windows MBR (Master Boot Record), so that is why you are booting directly into Windows. But if you aren't changing the default settings with the installer, Grub should get installed to your MBR, so I don't know what happened. Did you get any errors during the installation? Did it say it completed successfully?

If everything was installed OK except for Grub, you could do the following to install Grub to your MBR:
```
sudo grub
grub> find /boot/grub/stage1

```
The command above should return your main Ubuntu partition as (hd0,4), if it does proceed with:
```

grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands, and if all the commands complete successfully, then go ahead and reboot and let me know exactly what you get on start up. :)

---

### Post by sunkssss on 2008-10-25
Is there a chance this is a hardware issue?

So Grub loaded after running the code you gave me, however now I cannot boot either operating system, I only get Error 21... 

> grub>find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)... 16 sectors are embedded. succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2/boot/grub/menu.lst"... succeeded
Done.

grub> quit

---

### Post by bulldog on 2008-10-25
I think I understand your problem,had it myself and was asking why it happened :)

If you go to mount your partitions,by default there's the line 'do not use this partition' or something similar.
Ignore this message and select that line,you will see that it change to use this partition!
Scroll down [if necessary] and select done with this partition.
At the end when all your partitions are mounted correctly and set to format [or not] bootflag enabled and so on,choose in the last part 'write changes to disk [by default no,but select yes] and the install will continue.
Grub will be installed at the end of the install.
Hope this is of some help to you,and if I did understand your problem correct.

---

### Post by sunkssss on 2008-10-25
That's interesting because this is one detail that I was noticing when I booted using the LiveCD and examined the partitions. Is this a bug? Is there any reason that it switches on its own?

So the only way to fix this is to go back and reinstall from scratch? How exactly did you setup your partitions so that I'm sure I'm doing it right?

I'll probably have to reinstall XP too since now the partition is not being recognized, huh?

---

### Post by sunkssss on 2008-10-25
Actually, perhaps I misunderstood what you were saying. By default there is no mount type selected, so perhaps this isn't the same case, but sounds similar because I feel like the partitions are reverting to the "do not use this partition" option.

---

### Post by bulldog on 2008-10-25
If the install continues after you mounted your partitions,your problem isn't the same.
I couldn't get past the partitioner because it refused to mount the partitions as I wished to do so.
After a while I understood what was going wrong,and corrected my mistake.

---

### Post by caljohnsmith on 2008-10-25
> **sunkssss said:**
> Is there a chance this is a hardware issue?

So Grub loaded after running the code you gave me, however now I cannot boot either operating system, I only get Error 21...
That's great news, at least you got the Grub menu, so now it is just a matter of correcting your menu.lst. From your Live CD, do the following:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst

```
And change the Ubuntu lines to use (hd0,4):
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the line that says "# groot=(hdX,Y)" to:
```
# groot=(hd0,4)
```
And then at the bottom of the menu.lst make the Windows entry:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Save, reboot, and let me know what happens when you select each OS.

---

### Post by sunkssss on 2008-10-25
Presto! Ubuntu now boots and things seem to be working smoothly. Only issue is when I do try to boot XP it hangs at "starting..." 

However it may be because I didn't apply that last line correctly. You said to make the entry 
> title Windows XP
root (hd0,0)
chainloader +1

but my code reads
> title Microsoft WIndows XP Professional
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Am I supposed to replace the whole entry? Or is it possible it's something else?

Thanks a lot for your help, I really appreciate it. What could have caused this problem in my system?

---

### Post by caljohnsmith on 2008-10-25
> **sunkssss said:**
> 
Am I supposed to replace the whole entry? Or is it possible it's something else?
Yes, replace that whole Windows with the entry I gave in my last post.
> **sunkssss said:**
> 
Thanks a lot for your help, I really appreciate it. What could have caused this problem in my system? 
Based on some of the info that you've posted, my guess is that you had some other HDD connected when you installed Ubuntu, and that's how Grub maybe ended up in the wrong place. Were there any other drives connected when you installed Ubuntu?

---

### Post by sunkssss on 2008-10-25
Huh, no way. I did have an external 120GB harddrive connected, so that must confirm your theory. I didn't realize that could have that effect. Silly me...

Thank you for your help, you're a genius!

---

