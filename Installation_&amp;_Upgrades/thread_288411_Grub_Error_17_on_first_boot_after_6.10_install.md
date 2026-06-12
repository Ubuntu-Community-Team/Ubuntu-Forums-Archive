---
title: "Grub Error 17 on first boot after 6.10 install"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Flash604 on 2006-10-29
Hi there
I am a noob to Linux, but fairly computer savvy.  I have wanted to experiment with Linux, but I have not had time to experiment so far, and won't until Christmas time.  My wife's computer needed redoing and she decided she wanted a dual boot to Win XP and Ubuntu.

Knowing that a new version of Ubuntu was coming out, we only installed Win XP last weekend, and then added 6.10 today.  Keep in mind our noob status.

Upon reboot after the install, she gets a Grub Error 17.

Looking over the forums, I have learned a bit already, but still am stumped.  I have learned enough to figure out you will need to following info, and to figure out how to get it (I'm currently booted to the live CD).

The computer is a P3 866 on a Asus CLUS2-C motherboard with the latest BIOS (though that is still several years old).  The main HDD that we have installed both O/S's to is a 250 gig IDE drive that has been operating in the computer for 2 years no problem, until last week when it decided that it no longer wanted to work as a master unless it is set as Cable Select.  The second drive is a 320 gig IDE drive just being used for data.

sudo fdisk -l gives:

> 
Disk /dev/hda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       15935   127997856   17  Hidden HPFS/NTFS
/dev/hda2   *       15936       25148    74003422+  83  Linux
/dev/hda3           25149       25421     2192872+  82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12790   102735643+   7  HPFS/NTFS
/dev/hdb2           12791       38913   209832997+   f  W95 Ext'd (LBA)
/dev/hdb5           12791       25852   104920483+   7  HPFS/NTFS
/dev/hdb6           25853       38913   104912451    b  W95 FAT32



Following TiredBird's instructions [here]("http://www.ubuntuforums.org/showpost.php?p=1654511&postcount=18") (substituting hda as appropriate) resulted in a success message, but made no difference when I rebooted.  There didn't seem to be anything in the menu.lst that was wrong; below is the uncommented portion:

> 
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


I found reference to the Grub Super Disk and tried it out; but when I attempt to have it automatically reinstall Grub to the MBR, I got an error (sorry I can't remember the exact error, I'll recreate it if necessary).  I did successfully boot into Win XP using that disk.

I'm struggling through a lot of other stuff, but my lack of knowledge is making me a little hesitant to just jump in.  Any suggestions?

Flash

---

### Post by jd65pl on 2006-10-29
I'm fairly sure that you shouldn't have had to substitue anything in the tutorial you posted. What exactly did you try? Where you in recovery mode?

---

### Post by Flash604 on 2006-10-29
I was substituting hda for hdc, as my install is on hda and that user's install was on hdc (check my fdisk -l output versus his).  Should I not have done so?

---

### Post by jd65pl on 2006-10-29
The instructions that the person has provided apply to a linux partition installed on hda partition 1 (assuming 0 is start) try again using the exact commands the user posted.

---

### Post by Flash604 on 2006-10-29
Perhaps I should have been more specific, I did follow the directions in post 18 of that chain exactly.  It was the first instruction in post 20 where I substituted, but I did just try it without substitution.  Doing so, I get:
> 
ubuntu@ubuntu:/mnt/boot/grub$ sudo mount -t ext3 /dev/hdc2 /mnt
mount: special device /dev/hdc2 does not exist

When I do substitute hda2 for hdc2, I am successful and can get into grub folder.

---

### Post by nimrod_abing on 2006-10-29
> **Flash604 said:**
> I was substituting hda for hdc, as my install is on hda and that user's install was on hdc (check my fdisk -l output versus his).  Should I not have done so?

You have the following lines in your menu.lst:

```
 map        (hd0) (hd1)
map        (hd1) (hd0)

```Did you put them there or did grubinstall do it? Because what this does is switch your two drives before booting (your windows install). Check your BIOS and make sure that your primary master is indeed the 250GB drive. If it's not, then you have to configure your machine so that it sets the 250GB drive as your primary master.

You can try and boot up grub and then press 'e' while your Linux menu item is highlighted. Then edit the lines:

```
root (hd0,1)

```and change to:

```
root (hd1,1)
```and then:

```
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
```change that to say:

```
 kernel        /boot/vmlinuz-2.6.17-10-generic root=**[COLOR=Red]/dev/hdb2[/COLOR]** ro quiet splash
```Then press 'b' to boot. If it works then your drives setup is messed up. So either correct it in your BIOS or make those above edits permanent by changing your menu.lst to the above changes.

Once you have the setup correct, change menu.lst as follows:

Look for the line that says something like:

```
# groot=(hd1,0)
```and change it to whatever you have your root grub option is.

Then look for the line that says something like:

```
# kopt=root=/dev/hda1 ro lapic
```and change it to whatever you have in your kernel line (not including the quiet splash options).

This is so that subsequent kernel upgrades will use your current grub options and settings.

---

### Post by Flash604 on 2006-10-29
> **nimrod_abing said:**
> You have the following lines in your menu.lst:

```
 map        (hd0) (hd1)
map        (hd1) (hd0)

```Did you put them there or did grubinstall do it?
I did not put them there, grubinstall must have done so.  Would this be from the Ubuntu install, or from the Super Grub Disk?
> Check your BIOS and make sure that your primary master is indeed the 250GB drive. If it's not, then you have to configure your machine so that it sets the 250GB drive as your primary master.
Since I had all of the issue with that HDD being seen as a master, I did just check in the BIOS.  The 250GB is the primary master.  Should I still try what you have specified?

---

### Post by nimrod_abing on 2006-10-29
> **Flash604 said:**
> I did not put them there, grubinstall must have done so.  Would this be from the Ubuntu install, or from the Super Grub Disk?

Since I had all of the issue with that HDD being seen as a master, I did just check in the BIOS.  The 250GB is the primary master.  Should I still try what you have specified?

Yes, your drives are getting mixed up somehow at boot time. Error 17 does not give you the Grub menu, correct? If you are able to reach the grub menu then you should try editing the menu options right there first and try to find what works for you.

Grub is not able to mount your root partition (the one containing your /boot directory). Which is why you get an Error 17. This could be that your BIOS does not correctly report your hard disk setup. I've read that you are using CS (cable select) this could be the cause of all your problems and is probably why grubinstall found it necessary to insert the map options for your Windows install.

Good luck!

---

### Post by Flash604 on 2006-10-29
Ok, I'll give it a try, her computer is just finishing booting back into the Live CD.  And yes, your are correct, I'm not reaching the Grub menu.  I'll remount the drive when booted to the Live CD and edit the menu.lst there.

---

### Post by nimrod_abing on 2006-10-30
> **Flash604 said:**
> Ok, I'll give it a try, her computer is just finishing booting back into the Live CD.  And yes, your are correct, I'm not reaching the Grub menu.  I'll remount the drive when booted to the Live CD and edit the menu.lst there.

If you still haven't gotten it to work, do:

```
cat /boot/grub/device.map
```

Although this file is used by grub-install only, it may explain why grub has trouble finding the correct hard disk partition where you have your /boot directory.

Mine says:

```
(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
```


Yours will probably have hd0 and hd1 mixed up somehow. You may need to fix this so that the next time you use grub-install, it will correctly install grub. When grub-install probes for your hard drives, it may be confused if you are using cable select on your setup. If that is the case, then you may have to re-install grub using the grub shell.

```
sudo /sbin/grub
```

Or if you're on a live CD, mount your Linux partition first (e.g., /tmp/mnt-linux), then do:

```
sudo /tmp/mnt-linux/sbin/grub
```

Then from the grub shell:

```
find /boot/grub/stage1
```

This will tell you where your /boot/grub/stage1 file is located. It should output the drive and partition number where the file can be found. You then do the following (you're dual-boot so I'm assuming you want to install on to your MBR of your primary master):

```
root (hdXX,YY)
setup (hd0)

```

Change XX and YY to the correct numbers reported by the find command above. Lastly:

```
quit
```

And reboot.

HTH. Good luck!

---

### Post by Flash604 on 2006-10-30
Still not in... I mounted the root drive, went into menu.lst, and made the edits you suggested.  Same result on boot.  I therefore put it back the way it was, but without that reference to (hd1,0), as I figured out that the second HDD has a windows folder on it (the entire main drive was copied to this secondary drive during data recovery), and that was likely why grub was pointing to it.  Still the same results however.

I decided I needed to get her into Windows at least, and I booted to the recovery console and ran fixmbr and fixboot.  This left the computer totally unbootable!  I started a Windows repair, as it could see the partition, but Windows setup copyied the necessary files over and rebooted the machine, it would still not boot up.

Booting first to a Linux system recovery DVD I have, and then back to the live CD; I was able to figure out that the first (windows) partion was now hidden and the Linux partition was the boot partition.  I reset the flags, and the Windows repair has continued (something I probably didn't have to do, but I hadn't figured out the issue with the flags before I committed).

After that finishes and I'm booting into Windows again, I'll boot to the live CD and see if the above can allow me to reinstall Grub.

Thanks for the help!

---

### Post by Bigbluecat on 2006-10-30
A little late to the party but maybe some help for next time.

I had a problem where my drives were getting mixed up causing boot isssues. 

I used super grub disk and then Hermans guide for using grub command line to manually boot the kernel.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Click the link to Grubs command line interface.

The real power here is that you use grub commands to find exactly which drives and partitions all the important files are on and it reports back in grub terms. So no need to guess at what may be getting switched. You simply take the drive specs reported back and use them in your menu.lst. After that you can set groot and kopt appropriatley.

Hope you'll be back in Ubuntu soon.

---

### Post by nimrod_abing on 2006-10-30
> **Flash604 said:**
> The main HDD that we have installed both O/S's to is a 250 gig IDE drive that has been operating in the computer for 2 years no problem, until last week when it decided that it no longer wanted to work as a master unless it is set as Cable Select.

By any chance, is this 250GB HDD a Seagate or Maxtor drive?

](*,) I failed to notice this before but I think it's high time you replaced this HDD. Just a few weeks back, I bought a new HDD with similar problems: it would not function unless I set it to CS mode. This was a new HDD and the store has a return policy wherein they will not accept returns as long as the HDD is detected by the BIOS (ridiculous I know, but what can I do).

I got to the point where I was able to successfully format the new drive, but a few hours later while copying my Linux install to it, everything came to a screeching halt. Checking /var/log/messages there were unrecoverable errors from this new drive. On reboot, the drive disappeared completely :(

As grub has a more "primitive" IDE probing, it's not able to catch serious errors and is just likely to work around them (like swapping between your installed HDD's).

Try mounting your Linux partition again, then cd to where your /var/log directory is on this partition. Then do:

```
grep UncorrectableError messages
```or

```
grep 'SeekComplete Error' messages
```If you get a couple of lines with these errors then chances are, your hard disk is failing albeit silently. Even if there are no errors detected by the Linux kernel, the fact that you have to do something unusual (won't work unless you set it to CS mode) just to get your HDD to work is a dead giveaway that it is failing. Personally, I would not trust my system to a failing hard disk.

[COLOR=Red]EDIT: Also the fact that Windows fails to boot properly is another hint that your HDD is failing. Windows is very touchy as to where it is installed and with your current HDD setup. I guess you have MS to thank for making an OS that thinks it's the only OS that you should have on your system :D[/COLOR]

---

### Post by Flash604 on 2006-10-30
[QUOTE=nimrod_abing;1688509]By any chance, is this 250GB HDD a Seagate or Maxtor drive?-[/QUOTE

It's a Western Digital, and is actually already a replacement drive.  Originally it was a 200GB that failed, and the 250GB is what Western Digital sent as a replacement.  I'm already ordering another replacement from them (they require no error codes, just type in a description of your problem), and will copy this drives contents over to the replacement using imaging software.

I don't think that's the issue, though.  After I successfully got the machine booting into Windows yesterday, I reinstalled Ubuntu just to insure it wasn't a bad install of Grub.  Same results. The menu.lst was identical.  I got into the device.map, and it is:
```

(hd0)   /dev/hda
(hd1)   /dev/hdb

```
It seems, from what I'm learning thanks to your help, that Grub is correctly detecting which drive is which.  Instead, some of the things that I saw in Super Grub Disk are instead making me think I'm having the 1024 issue, despite the fact that my BIOS supports LBA.

Therefore, the last thing I did last night was to use the SGD to boot into Windows, and the used Partition Manager to move the Windows Partition over slightly in order to make a 50MB partition at the beginning in which I'll create a /boot folder.  Upon reboot, I used SGD to boot into Windows again, Partition Manager then took over on the boot and started chugging away on that, and I headed to bed.  I realize now that I was too tired to remember if I made it a primary or extended partition, I'll find that out in a while.

This morning the computer was booted to the SGD disk.  I used it to boot into Windows, and my wife is surfing with her morning coffee.  We have to go out most of today, and just before we do I will tell Ubuntu to reinstall, but this time with the boot folder in this new partition.  It will probably be at least 8 hours before I'm back to report on the results.

---

### Post by Flash604 on 2006-10-30
That solved it, it was the 1024 issue.  Thanks to everyone that offered suggestions, and even others that have posted in other threads; it was only through reading and follow a lot of your suggestions that I got a mini-course in Linux and was able to figure out what the issue was and resolve it!

---

### Post by AreEK on 2006-11-02
I have just read this whole thread because I have a quite, but alas, not completely similar problem.
Cred to the both of you for clear, comprehensive and friendly postings. It's a real plesaure to be part of this type of community!

---

