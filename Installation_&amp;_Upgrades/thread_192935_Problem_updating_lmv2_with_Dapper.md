---
title: "Problem updating lmv2 with Dapper"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by bertrand82 on 2006-06-09
While upgrading from Breezy to Dapper, the following error occured:
> Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

The process stopped and now I can't update LVM2. The sound card is not detected anymore and I can't use any Usb device. 
Is it related and is there a way to solve it ? Thanks a lot.

---

### Post by gmc on 2006-06-09
[QUOTE=bertrand82]While upgrading from Breezy to Dapper, the following error occured:


The process stopped and now I can't update LVM2. The sound card is not detected anymore and I can't use any Usb device. 
Is it related and is there a way to solve it ? Thanks a lot.[/QUOTE]


I'm in the process of upgrading two hoary systems and have run into the same problem. Try using a different repository.

Gord

Edited: run dselect and look for lvm2, unselect it, exit out of dselect and re-run apt-get dist-upgrade.

---

### Post by bertrand82 on 2006-06-09
Thank you Gord. 

Actually I have exactly the same problem as the one raised there: [http://www.ubuntuforums.org/showthread.php?p=1080946](http://www.ubuntuforums.org/showthread.php?p=1080946)

I must confess I do not know what the package LVM2 is for, so I do not know if fixing that will help me using my USB hard drive or my sound card. But I will try to use a new repository anyway. 

Thanks!

---

### Post by gmc on 2006-06-09
[QUOTE=bertrand82]Thank you Gord. 

Actually I have exactly the same problem as the one raised there: [http://www.ubuntuforums.org/showthread.php?p=1080946](http://www.ubuntuforums.org/showthread.php?p=1080946)

I must confess I do not know what the package LVM2 is for, so I do not know if fixing that will help me using my USB hard drive or my sound card. But I will try to use a new repository anyway. 

Thanks![/QUOTE]

LVM stands for Logical Volume Manager... it's like a meta disk partitioning package that can do some pretty niffty things with disk partitions. No it wouldn't have any effect on USB HD's or your sound card.

Gord

---

### Post by bertrand82 on 2006-06-09
Thank you! 

I think I got the point, and you''re right, the two problems are not related to each other. 

I have hardware detection problems. I ran an lspci command and could find both the USB ports and the sound card. The dmesg does not say anything about them. 
And, last but not least, a cat /proc/version returned me:

Linux version 2.6.10-5-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Aug 18 22:39:14 UTC 2005

which is really surprising, since I have just switched from Breezy to Dapper. So do you think my problem comes from the fact that the kernel does not correspond? And how does one correct this kernel problem?

Thank you again.

---

### Post by gmc on 2006-06-09
[QUOTE=bertrand82]Thank you! 

I think I got the point, and you''re right, the two problems are not related to each other. 

I have hardware detection problems. I ran an lspci command and could find both the USB ports and the sound card. The dmesg does not say anything about them. 
And, last but not least, a cat /proc/version returned me:

Linux version 2.6.10-5-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Aug 18 22:39:14 UTC 2005

which is really surprising, since I have just switched from Breezy to Dapper. So do you think my problem comes from the fact that the kernel does not correspond? And how does one correct this kernel problem?

Thank you again.[/QUOTE]

Hmm, that's weird. The first thing I would do, is check **/boot/grub/menu.lst** and see what you have set for the **default** kernel to use (should read 0 unless you've changed it). Next I would run 'sudo update-grub' and watch the output to make sure you've got a more recent kernel installed (2.6.15-23?) -- Obviously if you don't have any .15 kernels install, I'd take care of that.

Now as for sound, I found that I had to play with the properties on the speaker on the panel (just right click on it and choose preferences). Now the USB, I'm not sure about! Perhaps (fingers crossed) booting with a newer kernel will sort that out. I do recall that I originally had a problem with my external USB drive but it turned out that the cheap-o USB hub that I was using with my old laptop (USB 1.1) worked, but failed to work with my new laptop (USB 2.0). Since you're comming from Breezy, did it work there?

Gord

---

### Post by bertrand82 on 2006-06-10
Thank you. 

So the menu.lst contains the default set to 0 (I have a double boot with XP). My concern is that 'sudo update-grub' returns (tried twice):

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.10-5-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

So it seems that the kernel is still pretty old (is it the one of breezy), even if I upgraded my version yesterday. I do see the difference between my old version and the new one I've installed, but is it still possible that the kernel has not been updated properly and leads to drivers problems?

In my /boot folder, I can see that the vmlinuz-2.6.10-5-686 file has not been modified or accessed for 10 months, but the initrd.img-2.6.10-5-686 and the memtest86+.bin were modified and accessed yesterday.

Everything was working properly with Breezy (sound, USB, etc). I cannot right click on the panel because of an error 'No volume control GStreamer plugins and/or devices found.', and I do have the GStreamer plugins. So I guess that most of those problems come from the kernel issue. What do you think?

Thank you again.

---

### Post by gmc on 2006-06-10
[QUOTE=bertrand82]Thank you. 

So the menu.lst contains the default set to 0 (I have a double boot with XP). My concern is that 'sudo update-grub' returns (tried twice):

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.10-5-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

So it seems that the kernel is still pretty old (is it the one of breezy), even if I upgraded my version yesterday. I do see the difference between my old version and the new one I've installed, but is it still possible that the kernel has not been updated properly and leads to drivers problems?

In my /boot folder, I can see that the vmlinuz-2.6.10-5-686 file has not been modified or accessed for 10 months, but the initrd.img-2.6.10-5-686 and the memtest86+.bin were modified and accessed yesterday.

Everything was working properly with Breezy (sound, USB, etc). I cannot right click on the panel because of an error 'No volume control GStreamer plugins and/or devices found.', and I do have the GStreamer plugins. So I guess that most of those problems come from the kernel issue. What do you think?

Thank you again.[/QUOTE]

That sounds (excuse the pun) like a reasonable idea. Try **sudo apt-get install linux-686** or if you are using a dual core, **sudo apt-get install linux-686-smp**. Once the new kernel is in stalled try **sudo update-grub**, you should see the new 2.6.15 kernel, the old 2.6.10 kernel and your windows listed. Then reboot, and we'll see if that sorts anything, if not we'll have to try something else. 

Gord

---

### Post by bertrand82 on 2006-06-10
Thank you so much! You were right! Now 'sudo update-grub' returned:

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-23-686
Found kernel: /boot/vmlinuz-2.6.10-5-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

And when booting on 2.6.15-23-686 I could not only hear sound, but also use my USB HD, so my computer got a bit more lively! Not surprisingly, my Internet connections were a bit messed up because they were already working with 2.6.10-5-686 (I don't really know why, actually), so eth0 (Ethernet) became eth2 and eth1 (wifi) became eth3. Is there a way to remove the older kernel properly and to have my previous settings back?

Thank you again for all you did for me, really!

---

### Post by bertrand82 on 2006-06-10
And by the way, while running Synaptic from the new kernel, lvm2 could be installed and now everything is perfectly configured. 

Thank you very much!

---

### Post by gmc on 2006-06-10
[QUOTE=bertrand82]And by the way, while running Synaptic from the new kernel, lvm2 could be installed and now everything is perfectly configured. 

Thank you very much![/QUOTE]

Great to hear! Did installing the new kernel solve the sound/usb problem or was it installing lmv2? 

Gord

---

### Post by bertrand82 on 2006-06-10
That is the installation of the new kernel which solved the problem. Installing lmv2 did not produce anything special, apparently. I will think about a way to remove the other one properly and the problem will be completely solved (I still have a couple of minor problems, for example phpldapadmin does not work any longer, etc., and I guess that it can be solved with that). 

Thank you again, really!

---

