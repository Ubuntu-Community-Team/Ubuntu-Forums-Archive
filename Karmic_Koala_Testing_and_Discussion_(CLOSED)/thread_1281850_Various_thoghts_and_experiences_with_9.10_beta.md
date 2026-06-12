---
title: "Various thoghts and experiences with 9.10 beta"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tony_clifton on 2009-10-03
My system had been a dual boot with Jaunty and XP, and I decided to try out the beta release of Karmic.  My plan was to get rid of Windows entirely by replacing that partition with the beta.

During the install I saw the infamous "ACPI Invalid PBLK length [5]", the bug that keeps on giving.   I also get this on every boot with both 9.04 and 9.10 and [have reported it as a bug in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/441339").  Personally I think if they're not going to fix it they should just suppress the error message, but that's just my two cents.

The recommended system set up was a triple boot with XP, 9.10, and 9.04.   Here I ran into what turned out to be a problem: the recommended partition size for 9.10 was only 2.5GB (all taken from the Windows partition), which seemed low (it is).  I decided to keep XP for now as I had never resized a Windows partition and wanted to see what would happen.  I keep no data on that drive and had already given up on Gatesware so I had nothing to lose.  I ran with it.

Everything went fine with Karmic until system restart after a successful and uneventful installation.  Instead of rebooting the system hung and intermittently flashed the background image.  I pushed the manual reset button on my tower to restart.  Rather than being a new problem with the beta I believe that this, like the "Invalid PBLK length" error, is [an old bug that I have previously reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366682").  As with 9.04 when I restart the system hangs and displays the message such as "[ 2642.044650 ] Restarting system."  

I haven't been able to try out the "reboot=b" workaround for the restart issue as with the new Grub setup menu.lst is no longer used and I don't understand how to manually change boot options.

Somewhere in there I decided to boot into Windows.  It ran through a chkdsk automatically and booted fine, so the resize was no real problem.  A nice surprise there as I'd always read doom and gloom regarding any potential resize on a Windows drive.    

On the next boot into 9.10 I was greeted, warmly, by a pleasant message informing me that my system drive was on the verge of failing.  According to the Palimpsest Disk Utility the drive has 192 bad sectors and must be replaced post haste.  I dutifully then spent hours and hours and hours running chkdsk on Windows, disk manufacturer disk utility, etc, all in a vain attempt to further diagnose what I now believe to be a non-problem.  Every other scan tells me the disk is healthy and has zero bad sectors.  I'll go so far as to agree it has 192 reallocated sectors, but as far as I can tell the disk is working fine.  I've been eyeing a new 2TB drive for more storage space, but if I do get it it won't be because I believe this drive is failing.  Unless it does, of course.  

Back into general use and testing on 9.10 I ran into the problem with having only 2.5GB on the beta partition.  That's the minimum system requirement, so as soon as I did anything, in this case install the NVIDIA driver, I got a warning stating I only had 95.4MB of space left in my file system.   

Now, I suppose I should have known better, but shouldn't the install system have too?   2.5GB is not adequate if you want to do any modifications, probably not even enough to browse the web.  No space to install new packages, drivers, plugins, anything.  I used GParted Live CD to resize the Windows partition, again, and roughly doubled the 9.10 partition.  Windows booted normally after another automatic chkdsk and appears to be no worse off (which isn't saying much).

All in all, everything seems to be fine.  I have, as I see it, three bugs, two of which I lived with in 9.04, and another which appears to be someone somewhere who is much more anal than I when it comes to reallocated sectors.  I've begun modifying Firefox to my likes, no issues, and I need to get my Windows drives to auto mount (I haven't looked into this yet), but so far so good.  The triple boot is pretty cool.

---

### Post by raiwo on 2009-10-03
my experience:

-updated from 9.04, everything went smooth expect questions about menu.lst where i had to choose something and because i was not sure i went on default. This caused that new kernel line was not written in menu.lst so i had to manually edit it. As for 9.10 it's much faster than 9.04 which in my case must be related to new intel video driver which sucked on 9.04.had to install manually grub2 which went fine expect now i don't know how to edit grub!?! Overall i am satisfied with 9.10

---

### Post by Mike_IronFist on 2009-10-03
As far as I can tell, the obnoxious disk utility and its pathetically WRONG diagnoses (such as telling people with good drives that "One of your hard disks is failing) has been fixed so it doesn't behave that way anymore.

> **tony_clifton said:**
> 

Back into general use and testing on 9.10 I ran into the problem with having only 2.5GB on the beta partition.  That's the minimum system requirement, so as soon as I did anything, in this case install the NVIDIA driver, I got a warning stating I only had 95.4MB of space left in my file system.   

Now, I suppose I should have known better, but shouldn't the install system have too?   2.5GB is not adequate if you want to do any modifications, probably not even enough to browse the web.  No space to install new packages, drivers, plugins, anything.  I used GParted Live CD to resize the Windows partition, again, and roughly doubled the 9.10 partition.  Windows booted normally after another automatic chkdsk and appears to be no worse off (which isn't saying much).

All in all, everything seems to be fine.  I have, as I see it, three bugs, two of which I lived with in 9.04, and another which appears to be someone somewhere who is much more anal than I when it comes to reallocated sectors.  I've begun modifying Firefox to my likes, no issues, and I need to get my Windows drives to auto mount (I haven't looked into this yet), but so far so good.  The triple boot is pretty cool.

Yeah, 2.5 GB isn't the minimum, it's the amoount of space the install occupies.

For auto-mounting NTFS partitions, I recommend the NTFS Configuration tool. (Available at the Ubuntu software center). Once you install it, you can just open it, check off the drives you want auto-mounted, click a couple of OK buttons, and those drives will auto-mount forever. For some reason it gets installed under the Administration menu, but it works just fine all the same.

---

### Post by tony_clifton on 2009-10-03
NTFS configuration tool worked great, thank you.

---

### Post by tony_clifton on 2009-10-03
As far as the obnoxious disk utility, it isn't fixed from where I'm sitting.

---

### Post by tony_clifton on 2009-10-03
Figured out how to add "reboot=b" to /boot/grub/grub.cfg.

```
sudo gedit /etc/default/grub
```

change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=b"

save and exit file

```
sudo update-grub
```

and you're done.

to check, run ```
sudo gedit /boot/grub/grub.cfg
```  (just to ensure changes were made, but file should not be edited directly).

---

