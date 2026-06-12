---
title: "Quick Question Regarding dual boot Windows 8 and Ubuntu"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by Genxi on 2013-06-21
Hi guys,

I was reading a help page on how to dual boot Windows 8 and Ubuntu, but I encountered some vagueness in the guide, so I would like someone to clear it up for me. 

The link to the guide is: 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When I got to step 4 where it says: "Install Ubuntu from the Live CD/DVD or Live USB in the usual manner, then reboot the PC." What does it mean by "in the usual manner" because there are two options: Install Ubuntu alongside Windows 8 or something else. 

Lastly, if I have secure boot disable, fastboot disable and the intel srt disable, should I expect any types of errors?


Thanks!


Genxi

---

### Post by oldfred on 2013-06-21
If you want to dual boot, you want the side by side install. Although I never trust auto installs and manually partition in advance. You can use Something else and manually partition during install. Only with manual partition do you get the option to add /home or other than the default / (root) and swap. Also you must boot Ubuntu live installer in UEFI mode to install in UEFI mode.

More details in link in my signature. 

Be sure to shrink Windows first from inside Windows and reboot so it can run its repairs and chkdsk to update internals with new size. That avoids lots of issues or the perception of Windows issues from resizing by gparted or the installer.

Best to make Windows repair flash drive and backup. Details in link in my signature.

---

### Post by ajgreeny on 2013-06-21
I agree it is a bit vague, to say the least, and luckily I don't dual boot having ditched windows a long time ago.

I know some users who wanted to dual boot have inadvertently wiped their windows as they did not use the "Something Else" option when installing, which now appears to be the only safe way to do it if you want both windows and ubuntu together on the same disk.

I recommend first that you backup all your personal files, and then use the windows utility to produce recovery DVDs, or whatever is needed if you don't have a windows intallation DVD.  Having done that, now shrink your main windows partition using windows own disk management tool leaving the space unallocated, then run chkdisk a couple of times at least, to make sure windows will still boot without a problem.

Now when you use the ubuntu installer choose "Something Else" at the partitioning stage and in that unallocated space you can make new partitions for root, swap and if you want it separate, for /home. With GPT partitions there is not the 4 partition limit of previous msdos partition tables, so you will not have a problem as long as the unallocated space is sufficient.

I have installed using UEFI, and had no major problems once fastboot and secure boot was checked to be disabled, so I think your setup should be relatively simple, and I have never installed using the "install alongside another OS" so can not give you any real help about that option, hence my choice of "Something Else", which I feel is the safest option to use; others may tell you to use the "Install alongside --" option, and if you are happy to do that after learning about it from others it may be perfectly OK.

---

### Post by Genxi on 2013-06-21
Thank you for all the replies. I shall choose "something else" as my dual boot option. :)


Thanks,


Genxi

---

### Post by oldfred on 2013-06-21
As part of Something else is the option on where to install grub2's boot loader. That really applies to BIOS as with UEFI, grub is installed to efi partition. I think with UEFI it will default to efi partition no matter what you select.

With BIOS install you never install to a Windows formatted partition, so UEFI is different.

---

