---
title: "[SOLVED] Grub / XP issue"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by AMESSIER on 2008-10-19
My apologies if this is a common issue, but I haven't found my exact problem in the forums. I have a laptop with XP installed on one partition of a single disk. I install Ubuntu and divide up the rest of the disk into a "/" + "/boot" (EXT3) and a swap. Ubuntu boots fine, and Windows boots fine. However after I boot Windows for the first time grub seems to be blown away. I see the text "GRUB" flash on the screen after the bios runs and then the machine reboots (this loop will happen again and again). 

I have found lots of similar posts, but it seems that usually this only happens when XP is re-installed .. I'm just running it and it seems to kill grub. It seems to me that perhaps grub stage1 is running but it can't find stage2 (which is odd since the /boot partition should not be visible to XP). Or perhaps Windows is messing with the MBR itself. I noticed that in the Ubuntu installation there was an option about where to install grub with hd0 being the default. I've tried a few things there with no change in the behavior I've described above. 

Any and all help would be most appreciated.

---

### Post by caljohnsmith on 2008-10-19
I've come across at least one other thread in these forums that claimed exactly the same thing that you do, namely that Windows seems to somehow overwrite Grub in the MBR just by booting Windows. My guess is that you might have some special antivirus/anti-malware software in Windows that detects the change in the MBR and "fixes" it since it thinks it is malware. What antivirus type programs are you running in Windows? 

The next time Windows boots and replaces the MBR, after that try booting your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And if your drive is different than sda, change that above. If the above command returns "GRUB", then Grub is in the MBR, and if it returns "Missing operating system", you have a Windows MBR. If the command returns nothing, you have a different MBR that most likely works the same as the Windows MBR (it may be a special MBR from the antivirus program for example). Let me know what it returns. :)

---

### Post by AMESSIER on 2008-10-19
It returns GRUB. In XP I have McAfee ant-virus and Sygate security agent. I'll try to disable these and reinstall Ubuntu to see what happens. However, if this is my problem I'm in trouble because my place of work is very stric about running these things all the time.

Thanks for your reply by the way.

---

### Post by caljohnsmith on 2008-10-19
Interesting that it does return Grub. By the way, you shouldn't need to reinstall Ubuntu as long as Windows did not mess with your Ubuntu partitions. Before I help you reinstall Grub again though, please do the following:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.bin.gz
```
That will create a "sda.bin.gz" file on your desktop which will have the first 20 sectors of your HDD, so it will contain the MBR. Attach that to your next post and I'll look at it, because I'm curious if the stage1.5 file is being overwritten or what exactly is happening.

---

### Post by AMESSIER on 2008-10-19
Here's the attachment (deleted). Thanks for helping.

---

### Post by caljohnsmith on 2008-10-19
Looking at that file you sent, it tells me that your /boot partition is sda2, is that correct? It looks like part of your sda beginning sectors might be corrupt though. How about doing the following to restore Grub to your MBR: 
```
sudo grub
grub> find /grub/stage1
```
The above command should return (hd0,1), and if it does, proceed with:
```

grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
If the above commands complete successfully, then do:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda_uncorrupted.bin.gz
```
And attach that to your next post. Next reboot, make sure you can boot into Ubuntu first, and if you can, reboot and try to boot into Windows. Let me know exactly what happens. :)

---

### Post by AMESSIER on 2008-10-19
sda2 does make sense. sda1 is my NTFS partition, sda1 is boot and sda2 is root. I did what you suggested. Here's a message from GRUB, not sure if this is helpful

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/grub/stage2 /grub/menu.lst"... succeeded
Done.

```

I rebooted to Ubuntu (fine) and then Windows (fine), but after that the same thing happens (grub->BIOS loop). I took a closer look at what Grub flashes on the screen though .. it is looking for stage 1.5 right before the PC resets.

---

### Post by caljohnsmith on 2008-10-19
OK, so as I described in my PM to you, there is definitely something writing to the first sectors of your HDD. I have a workaround though that I think will save you from having to worry about what is actually writing to those sectors. Since whatever is writing to those sectors is leaving the MBR untouched (the first sector), we can install Grub to the MBR without embedding its stage1.5 file after the MBR. That way Grub will look in your /boot partition for its stage1.5 file, and it won't matter if that other software modifies the sectors after the MBR.

Try this from your Live CD:
```
sudo grub
grub> root (hd0,1)
grub> install /grub/stage1 (hd0) /grub/stage2 p /grub/menu.lst
grub> quit
```
Post the output of the above commands, reboot, go into Windows, reboot, and see if Grub successfully loads after that. Let me know how it goes. :)

---

### Post by meierfra. on 2008-10-20
caljohnsmith's solutions will work (of course), but has the disadvantage that Grub's  stage1.5  will not be used. (Usually you don't need stage1.5, but  it can provided valuable error messages in case of  booting problems)

So instead of omitting stage1.5,  I suggest to install  stage1.5 just a little bit further down on the hard drive:


```
sudo dd if=/boot/grub/e2fs_stage1_5 of=/dev/sda seek=20 count=16
```

Next you have to make sure that grub is aware of the new location of stage1.5


```
sudo grub
```

and at the grub prompt:

```
root (hd0,1)

install /grub/stage1 (hd0) (hd0)20+16 p  /grub/stage2  /grub/menu.lst

quit
```

---

### Post by AMESSIER on 2008-10-20
Thanks for all your help ... for others reading this my problem was indeed a Windows virus checker modifying some fields right after the MBR of the disk. It's interesting that it didn't try to restore the Windows boot-loader (I guess it wouldn't know how) but instead just basically self-destructed the system.

---

