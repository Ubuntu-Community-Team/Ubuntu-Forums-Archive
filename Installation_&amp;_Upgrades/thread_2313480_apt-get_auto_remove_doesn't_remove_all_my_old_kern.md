---
title: "apt-get auto remove doesn't remove all my old kernels"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by lazloman on 2016-02-12
The title says it all. After a new kernel install, I'm typically told that the previous version is no longer needed and prompted to remove it, but there are still kernels and their other associated images and maps going back, maybe three years. How do I get rid of them? They're clogging up my /boot partition. Do I need to do it manually?
Thanks

---

### Post by lisati on 2016-02-12
What happens when you run...?
```
sudo apt-get autoremove
```
Do you get any error messages?

---

### Post by ian-weisser on 2016-02-13
Please show us the output of:
```
uname -r
ls -l /boot
dpkg -l linux*
```

---

### Post by jsavga on 2016-02-13
From [https://wiki.ubuntu.com/KernelTeam/removing-old-kernels](https://wiki.ubuntu.com/KernelTeam/removing-old-kernels)
> Apt, and by extension, synaptics and other package handlers, are able to  autoremove packages that are considered to be no longer needed.  Normally, these older kernels would be tagged and removed from the users  system by this mechanism. Problem solved. NO! We cannot remove old  kernels because we have no idea which kernels are the one(s) that the  user needs or doesn't need. There's nothing saying that the newest X  number of kernels actually work, or whether the user has even booted  into them. **So apt has an exception to not tag linux-image-* packages for  autoremoval.**

---

### Post by ian-weisser on 2016-02-13
> **jsavga said:**
> From [https://wiki.ubuntu.com/KernelTeam/removing-old-kernels](https://wiki.ubuntu.com/KernelTeam/removing-old-kernels)

That page seems last edited in 2008.
Since then, Ubuntu has added a method to identify stale kernels and mark them eligble for autoremoval. See /etc/kernel/postinst.d/apt-auto-removal.

---

### Post by ubfan1 on 2016-02-13
Nevertheless, autoremove for old kernels simply does not work for many people. See :[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1175637](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1175637)    Yes the correct seeming kernel autoremove file is present in the above mentioned directory, but does nothing for me when I invoke autoremove.  Simply purge the old kernels manually:
1)Get a directory of /boot to see which kernels you want to delete.
2) Get a list of all the packages with the kernel number (seems sufficient to limit just to kernel packages, but you will get a confirmation before the purge).  For instance using kernel 3.13.0-71:   apt-cache pkgnames |grep 3.13.0-71
3)Check the list for just the kernels (never failed for me), and reuse the apt-cache line to regenerate the list in the purge command (or cut and paste).   sudo apt-get purge `!!`
4)Confirm the list of package to delete and one old kernel will be completely removed.
Repeat as necessary.  You won't gain much time with wild cards to get multiple kernels simultaneously, I just do them one at a time and check carefully.

---

### Post by ian-weisser on 2016-02-13
> **ubfan1 said:**
> Simply purge the old kernels manually
Yes, this is the direction we were heading in Post #3.
I think it's prudent to verify that the problem really is old kernels and not something else. There are several possibilities.
We have seen more than a few users destroy their systems by jumping to conclusions.

---

### Post by pfeiffep on 2016-02-14
I know many folks posting here will disagree with my method, but I find after a software upgrade requiring a reboot I use nautilus (gksudo nautilus) to display the contents of /boot and then delete all but the 2 highest numbered files containing the kernel version (example **3.13.0-76-generic)**. I find this method easy and straight forward. I don't go navigating around with nautilus launched in this manner I exit after I've deleted the files. 

Immediately after exit I execute sudo update-grub.

---

### Post by lazloman on 2016-02-14
No errors. I'm either prompted to remove what is seen as removable or nothing.

---

### Post by ian-weisser on 2016-02-14
> **pfeiffep said:**
>  I use nautilus (gksudo nautilus) to display the contents of /boot and then delete all but the 2 highest numbered files containing the kernel version (example **3.13.0-76-generic)**.

Well, you are correct about disagreeing. I do not recommend that method, and would not myself use it under any circumstances.

It is **most unwise** to manually delete files placed by the package manager.
This will surely break your package management at some unpredicatable point in the future, requiring much repair (using confusing, arcane shell voodoo) or a complete reinstall.

Always use the package manager to remove files that were placed by the package manager.

---

### Post by ian-weisser on 2016-02-14
> **lazloman said:**
> No errors. I'm either prompted to remove what is seen as removable or nothing.

We will happily review the proposed removals, if you wish. We would need to see the output.

---

### Post by lazloman on 2016-02-14
```
lorenzot@Hedley:~$ uname -r
3.13.0-77-generic

ls -l /boot
total 851548
-rw-r--r-- 1 root root   730039 Apr 10  2011 abi-2.6.38-8-generic
-rw-r--r-- 1 root root   730770 Nov 21  2011 abi-3.0.0-14-generic
-rw-r--r-- 1 root root  1165277 Jan 20 06:07 abi-3.13.0-77-generic
-rw-r--r-- 1 root root   791326 Jun 14  2012 abi-3.2.0-26-generic
-rw-r--r-- 1 root root   791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r-- 1 root root   791446 Aug 24  2012 abi-3.2.0-30-generic
-rw-r--r-- 1 root root   791446 Sep  7  2012 abi-3.2.0-31-generic
-rw-r--r-- 1 root root   792532 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r-- 1 root root   792532 Oct 18  2012 abi-3.2.0-33-generic
-rw-r--r-- 1 root root   792587 Nov 15  2012 abi-3.2.0-34-generic
-rw-r--r-- 1 root root   792715 Dec  5  2012 abi-3.2.0-35-generic
-rw-r--r-- 1 root root   792767 Jan  8  2013 abi-3.2.0-36-generic
-rw-r--r-- 1 root root   792767 Jan 24  2013 abi-3.2.0-37-generic
-rw-r--r-- 1 root root   792830 Feb 19  2013 abi-3.2.0-38-generic
-rw-r--r-- 1 root root   792830 Feb 27  2013 abi-3.2.0-39-generic
-rw-r--r-- 1 root root   794933 Mar 25  2013 abi-3.2.0-40-generic
-rw-r--r-- 1 root root   794996 Apr 24  2013 abi-3.2.0-41-generic
-rw-r--r-- 1 root root   794996 May 14  2013 abi-3.2.0-43-generic
-rw-r--r-- 1 root root   795146 May 16  2013 abi-3.2.0-44-generic
-rw-r--r-- 1 root root   795146 May 29  2013 abi-3.2.0-45-generic
-rw-r--r-- 1 root root   795365 Jun  6  2013 abi-3.2.0-48-generic
-rw-r--r-- 1 root root   795365 Jun 18  2013 abi-3.2.0-49-generic
-rw-r--r-- 1 root root   795365 Jul 24  2013 abi-3.2.0-51-generic
-rw-r--r-- 1 root root   795365 Jul 26  2013 abi-3.2.0-52-generic
-rw-r--r-- 1 root root   795539 Aug 22  2013 abi-3.2.0-53-generic
-rw-r--r-- 1 root root   795539 Sep 10  2013 abi-3.2.0-54-generic
-rw-r--r-- 1 root root   795686 Oct  2  2013 abi-3.2.0-55-generic
-rw-r--r-- 1 root root   795686 Oct 23  2013 abi-3.2.0-56-generic
-rw-r--r-- 1 root root   795751 Nov 12  2013 abi-3.2.0-57-generic
-rw-r--r-- 1 root root   795751 Dec  3  2013 abi-3.2.0-58-generic
-rw-r--r-- 1 root root   795751 Jan  7  2014 abi-3.2.0-59-generic
-rw-r--r-- 1 root root   795743 Feb 18  2014 abi-3.2.0-60-generic
-rw-r--r-- 1 root root   795743 May  2  2014 abi-3.2.0-61-generic
-rw-r--r-- 1 root root   795911 May 15  2014 abi-3.2.0-63-generic
-rw-r--r-- 1 root root   795911 Jun  4  2014 abi-3.2.0-64-generic
-rw-r--r-- 1 root root   795911 Jul  4  2014 abi-3.2.0-65-generic
-rw-r--r-- 1 root root   795963 Jul 15  2014 abi-3.2.0-67-generic
-rw-r--r-- 1 root root   130313 Apr 10  2011 config-2.6.38-8-generic
-rw-r--r-- 1 root root   135131 Nov 21  2011 config-3.0.0-14-generic
-rw-r--r-- 1 root root   165918 Jan 20 06:07 config-3.13.0-77-generic
-rw-r--r-- 1 root root   140454 Jun 14  2012 config-3.2.0-26-generic
-rw-r--r-- 1 root root   140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r-- 1 root root   140432 Aug 24  2012 config-3.2.0-30-generic
-rw-r--r-- 1 root root   140459 Sep  7  2012 config-3.2.0-31-generic
-rw-r--r-- 1 root root   140488 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r-- 1 root root   140488 Oct 18  2012 config-3.2.0-33-generic
-rw-r--r-- 1 root root   140505 Nov 15  2012 config-3.2.0-34-generic
-rw-r--r-- 1 root root   140505 Dec  5  2012 config-3.2.0-35-generic
-rw-r--r-- 1 root root   140505 Jan  8  2013 config-3.2.0-36-generic
-rw-r--r-- 1 root root   140505 Jan 24  2013 config-3.2.0-37-generic
-rw-r--r-- 1 root root   140488 Feb 19  2013 config-3.2.0-38-generic
-rw-r--r-- 1 root root   140488 Feb 27  2013 config-3.2.0-39-generic
-rw-r--r-- 1 root root   140586 Mar 25  2013 config-3.2.0-40-generic
-rw-r--r-- 1 root root   140622 Apr 24  2013 config-3.2.0-41-generic
-rw-r--r-- 1 root root   140622 May 14  2013 config-3.2.0-43-generic
-rw-r--r-- 1 root root   140622 May 16  2013 config-3.2.0-44-generic
-rw-r--r-- 1 root root   140622 May 29  2013 config-3.2.0-45-generic
-rw-r--r-- 1 root root   140622 Jun  6  2013 config-3.2.0-48-generic
-rw-r--r-- 1 root root   140622 Jun 18  2013 config-3.2.0-49-generic
-rw-r--r-- 1 root root   140629 Jul 24  2013 config-3.2.0-51-generic
-rw-r--r-- 1 root root   140629 Jul 26  2013 config-3.2.0-52-generic
-rw-r--r-- 1 root root   140629 Aug 22  2013 config-3.2.0-53-generic
-rw-r--r-- 1 root root   140629 Sep 10  2013 config-3.2.0-54-generic
-rw-r--r-- 1 root root   140629 Oct  2  2013 config-3.2.0-55-generic
-rw-r--r-- 1 root root   140629 Oct 23  2013 config-3.2.0-56-generic
-rw-r--r-- 1 root root   140629 Nov 12  2013 config-3.2.0-57-generic
-rw-r--r-- 1 root root   140629 Dec  3  2013 config-3.2.0-58-generic
-rw-r--r-- 1 root root   140629 Jan  7  2014 config-3.2.0-59-generic
-rw-r--r-- 1 root root   140612 Feb 18  2014 config-3.2.0-60-generic
-rw-r--r-- 1 root root   140612 May  2  2014 config-3.2.0-61-generic
-rw-r--r-- 1 root root   140640 May 15  2014 config-3.2.0-63-generic
-rw-r--r-- 1 root root   140640 Jun  4  2014 config-3.2.0-64-generic
-rw-r--r-- 1 root root   140640 Jul  4  2014 config-3.2.0-65-generic
-rw-r--r-- 1 root root   140641 Jul 15  2014 config-3.2.0-67-generic
drwxr-xr-x 5 root root    12288 Feb 12 19:13 grub
-rw-r--r-- 1 root root 12942759 Jan  1  2012 initrd.img-2.6.38-8-generic
-rw-r--r-- 1 root root 14225784 Jul  8  2012 initrd.img-3.0.0-14-generic
-rw-r--r-- 1 root root 19737459 Feb 10 07:05 initrd.img-3.13.0-77-generic
-rw-r--r-- 1 root root 14587695 Aug 17  2012 initrd.img-3.2.0-26-generic
-rw-r--r-- 1 root root 14597425 Sep  1  2012 initrd.img-3.2.0-29-generic
-rw-r--r-- 1 root root 14598641 Sep  7  2012 initrd.img-3.2.0-30-generic
-rw-r--r-- 1 root root 14603988 Oct  3  2012 initrd.img-3.2.0-31-generic
-rw-r--r-- 1 root root 14604897 Nov  2  2012 initrd.img-3.2.0-32-generic
-rw-r--r-- 1 root root 14605191 Nov 16  2012 initrd.img-3.2.0-33-generic
-rw-r--r-- 1 root root 14605714 Nov 30  2012 initrd.img-3.2.0-34-generic
-rw-r--r-- 1 root root 14606656 Dec 19  2012 initrd.img-3.2.0-35-generic
-rw-r--r-- 1 root root 14606350 Jan 18  2013 initrd.img-3.2.0-36-generic
-rw-r--r-- 1 root root 14611609 Feb  8  2013 initrd.img-3.2.0-37-generic
-rw-r--r-- 1 root root 14599941 Mar 15  2013 initrd.img-3.2.0-38-generic
-rw-r--r-- 1 root root 14601656 Mar 29  2013 initrd.img-3.2.0-39-generic
-rw-r--r-- 1 root root 14642937 Apr 12  2013 initrd.img-3.2.0-40-generic
-rw-r--r-- 1 root root 14644164 May  3  2013 initrd.img-3.2.0-41-generic
-rw-r--r-- 1 root root 14645385 May 17  2013 initrd.img-3.2.0-43-generic
-rw-r--r-- 1 root root 14645270 May 24  2013 initrd.img-3.2.0-44-generic
-rw-r--r-- 1 root root 14644961 May 31  2013 initrd.img-3.2.0-45-generic
-rw-r--r-- 1 root root 14644314 Jun 14  2013 initrd.img-3.2.0-48-generic
-rw-r--r-- 1 root root 14645129 Jul  5  2013 initrd.img-3.2.0-49-generic
-rw-r--r-- 1 root root 14644881 Aug 23  2013 initrd.img-3.2.0-51-generic
-rw-r--r-- 1 root root 14645290 Aug 23  2013 initrd.img-3.2.0-52-generic
-rw-r--r-- 1 root root 14645350 Sep  6  2013 initrd.img-3.2.0-53-generic
-rw-r--r-- 1 root root 14646270 Sep 27  2013 initrd.img-3.2.0-54-generic
-rw-r--r-- 1 root root 14648432 Oct 25  2013 initrd.img-3.2.0-55-generic
-rw-r--r-- 1 root root 14648264 Nov 22  2013 initrd.img-3.2.0-56-generic
-rw-r--r-- 1 root root 14649786 Dec  6  2013 initrd.img-3.2.0-57-generic
-rw-r--r-- 1 root root 14650436 Jan 24  2014 initrd.img-3.2.0-58-generic
-rw-r--r-- 1 root root 14652195 Feb 21  2014 initrd.img-3.2.0-59-generic
-rw-r--r-- 1 root root 14652236 Apr  4  2014 initrd.img-3.2.0-60-generic
-rw-r--r-- 1 root root 14650352 May  9  2014 initrd.img-3.2.0-61-generic
-rw-r--r-- 1 root root 14653212 Jun  3  2014 initrd.img-3.2.0-63-generic
-rw-r--r-- 1 root root 14651358 Jun  6  2014 initrd.img-3.2.0-64-generic
-rw-r--r-- 1 root root 14635886 Jul 11  2014 initrd.img-3.2.0-65-generic
-rw-r--r-- 1 root root 15218312 Aug 20  2014 initrd.img-3.2.0-67-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  2654256 Apr 10  2011 System.map-2.6.38-8-generic
-rw------- 1 root root  2696015 Nov 21  2011 System.map-3.0.0-14-generic
-rw------- 1 root root  3393097 Jan 20 06:07 System.map-3.13.0-77-generic
-rw------- 1 root root  2881851 Jun 14  2012 System.map-3.2.0-26-generic
-rw------- 1 root root  2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw------- 1 root root  2883362 Aug 24  2012 System.map-3.2.0-30-generic
-rw------- 1 root root  2883401 Sep  7  2012 System.map-3.2.0-31-generic
-rw------- 1 root root  2884076 Sep 26  2012 System.map-3.2.0-32-generic
-rw------- 1 root root  2884306 Oct 18  2012 System.map-3.2.0-33-generic
-rw------- 1 root root  2885127 Nov 15  2012 System.map-3.2.0-34-generic
-rw------- 1 root root  2885822 Dec  5  2012 System.map-3.2.0-35-generic
-rw------- 1 root root  2886319 Jan  8  2013 System.map-3.2.0-36-generic
-rw------- 1 root root  2886103 Jan 24  2013 System.map-3.2.0-37-generic
-rw------- 1 root root  2887333 Feb 19  2013 System.map-3.2.0-38-generic
-rw------- 1 root root  2888361 Feb 27  2013 System.map-3.2.0-39-generic
-rw------- 1 root root  2890703 Mar 25  2013 System.map-3.2.0-40-generic
-rw------- 1 root root  2891358 Apr 24  2013 System.map-3.2.0-41-generic
-rw------- 1 root root  2891358 May 14  2013 System.map-3.2.0-43-generic
-rw------- 1 root root  2891931 May 16  2013 System.map-3.2.0-44-generic
-rw------- 1 root root  2891931 May 29  2013 System.map-3.2.0-45-generic
-rw------- 1 root root  2893287 Jun  6  2013 System.map-3.2.0-48-generic
-rw------- 1 root root  2893287 Jun 18  2013 System.map-3.2.0-49-generic
-rw------- 1 root root  2893555 Jul 24  2013 System.map-3.2.0-51-generic
-rw------- 1 root root  2893555 Jul 26  2013 System.map-3.2.0-52-generic
-rw------- 1 root root  2894361 Aug 22  2013 System.map-3.2.0-53-generic
-rw------- 1 root root  2894535 Sep 10  2013 System.map-3.2.0-54-generic
-rw------- 1 root root  2895053 Oct  2  2013 System.map-3.2.0-55-generic
-rw------- 1 root root  2895053 Oct 23  2013 System.map-3.2.0-56-generic
-rw------- 1 root root  2895166 Nov 12  2013 System.map-3.2.0-57-generic
-rw------- 1 root root  2895308 Dec  3  2013 System.map-3.2.0-58-generic
-rw------- 1 root root  2895419 Jan  7  2014 System.map-3.2.0-59-generic
-rw------- 1 root root  2895229 Feb 18  2014 System.map-3.2.0-60-generic
-rw------- 1 root root  2895229 May  2  2014 System.map-3.2.0-61-generic
-rw------- 1 root root  2896164 May 15  2014 System.map-3.2.0-63-generic
-rw------- 1 root root  2896724 Jun  4  2014 System.map-3.2.0-64-generic
-rw------- 1 root root  2896866 Jul  4  2014 System.map-3.2.0-65-generic
-rw------- 1 root root  2896997 Jul 15  2014 System.map-3.2.0-67-generic
-rw------- 1 root root     1368 Apr 10  2011 vmcoreinfo-2.6.38-8-generic
-rw------- 1 root root     1367 Nov 21  2011 vmcoreinfo-3.0.0-14-generic
-rw------- 1 root root  4523936 Apr 10  2011 vmlinuz-2.6.38-8-generic
-rw------- 1 root root  4660944 Nov 21  2011 vmlinuz-3.0.0-14-generic
-rw------- 1 root root  5827168 Jan 20 06:07 vmlinuz-3.13.0-77-generic
-rw------- 1 root root  4960080 Jun 14  2012 vmlinuz-3.2.0-26-generic
-rw------- 1 root root  4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw------- 1 root root  4963280 Aug 24  2012 vmlinuz-3.2.0-30-generic
-rw------- 1 root root  4963792 Sep  7  2012 vmlinuz-3.2.0-31-generic
-rw------- 1 root root  4966768 Sep 26  2012 vmlinuz-3.2.0-32-generic
-rw------- 1 root root  4966896 Oct 18  2012 vmlinuz-3.2.0-33-generic
-rw------- 1 root root  4967632 Nov 15  2012 vmlinuz-3.2.0-34-generic
-rw------- 1 root root  4968400 Dec  5  2012 vmlinuz-3.2.0-35-generic
-rw------- 1 root root  4969392 Jan  8  2013 vmlinuz-3.2.0-36-generic
-rw------- 1 root root  4969072 Jan 24  2013 vmlinuz-3.2.0-37-generic
-rw------- 1 root root  4968592 Feb 19  2013 vmlinuz-3.2.0-38-generic
-rw------- 1 root root  4971472 Feb 27  2013 vmlinuz-3.2.0-39-generic
-rw------- 1 root root  4974672 Mar 25  2013 vmlinuz-3.2.0-40-generic
-rw------- 1 root root  4975248 Apr 24  2013 vmlinuz-3.2.0-41-generic
-rw------- 1 root root  4974640 May 14  2013 vmlinuz-3.2.0-43-generic
-rw------- 1 root root  4976368 May 16  2013 vmlinuz-3.2.0-44-generic
-rw------- 1 root root  4975696 May 29  2013 vmlinuz-3.2.0-45-generic
-rw------- 1 root root  4978416 Jun  6  2013 vmlinuz-3.2.0-48-generic
-rw------- 1 root root  4978416 Jun 18  2013 vmlinuz-3.2.0-49-generic
-rw------- 1 root root  4978960 Jul 24  2013 vmlinuz-3.2.0-51-generic
-rw------- 1 root root  4978224 Jul 26  2013 vmlinuz-3.2.0-52-generic
-rw------- 1 root root  4980336 Aug 22  2013 vmlinuz-3.2.0-53-generic
-rw------- 1 root root  4980272 Sep 10  2013 vmlinuz-3.2.0-54-generic
-rw------- 1 root root  4981456 Oct  2  2013 vmlinuz-3.2.0-55-generic
-rw------- 1 root root  4980752 Oct 23  2013 vmlinuz-3.2.0-56-generic
-rw------- 1 root root  4981040 Nov 12  2013 vmlinuz-3.2.0-57-generic
-rw------- 1 root root  4983216 Dec  3  2013 vmlinuz-3.2.0-58-generic
-rw------- 1 root root  4983888 Jan  7  2014 vmlinuz-3.2.0-59-generic
-rw------- 1 root root  4981616 Feb 18  2014 vmlinuz-3.2.0-60-generic
-rw------- 1 root root  4982576 May  2  2014 vmlinuz-3.2.0-61-generic
-rw------- 1 root root  4985488 May 15  2014 vmlinuz-3.2.0-63-generic
-rw------- 1 root root  4986832 Jun  4  2014 vmlinuz-3.2.0-64-generic
-rw------- 1 root root  4987152 Jul  4  2014 vmlinuz-3.2.0-65-generic
-rw------- 1 root root  4986960 Jul 15  2014 vmlinuz-3.2.0-67-generic
```


```
dpkg -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version           Architecture      Description
+++-========================-=================-=================-=====================================================
un  linux-doc-2.6.38         <none>            <none>            (no description available)
un  linux-doc-3.0.0          <none>            <none>            (no description available)
un  linux-doc-3.13.0         <none>            <none>            (no description available)
un  linux-doc-3.2.0          <none>            <none>            (no description available)
ii  linux-firmware           1.127.20          all               Firmware for Linux kernel drivers
ii  linux-generic            3.13.0.77.83      amd64             Complete Generic Linux kernel and headers
un  linux-headers            <none>            <none>            (no description available)
un  linux-headers-2.6        <none>            <none>            (no description available)
ii  linux-headers-2.6.38-8   2.6.38-8.42       all               Header files related to Linux kernel version 2.6.38
ii  linux-headers-2.6.38-8-g 2.6.38-8.42       amd64             Linux kernel headers for version 2.6.38 on x86/x86_64
un  linux-headers-3          <none>            <none>            (no description available)
un  linux-headers-3.0        <none>            <none>            (no description available)
un  linux-headers-3.13.0-34- <none>            <none>            (no description available)
un  linux-headers-3.13.0-35- <none>            <none>            (no description available)
un  linux-headers-3.13.0-36- <none>            <none>            (no description available)
un  linux-headers-3.13.0-37- <none>            <none>            (no description available)
un  linux-headers-3.13.0-39- <none>            <none>            (no description available)
un  linux-headers-3.13.0-40- <none>            <none>            (no description available)
un  linux-headers-3.13.0-43- <none>            <none>            (no description available)
un  linux-headers-3.13.0-44- <none>            <none>            (no description available)
un  linux-headers-3.13.0-45- <none>            <none>            (no description available)
un  linux-headers-3.13.0-46- <none>            <none>            (no description available)
un  linux-headers-3.13.0-48- <none>            <none>            (no description available)
un  linux-headers-3.13.0-49- <none>            <none>            (no description available)
un  linux-headers-3.13.0-51- <none>            <none>            (no description available)
un  linux-headers-3.13.0-52- <none>            <none>            (no description available)
un  linux-headers-3.13.0-53- <none>            <none>            (no description available)
un  linux-headers-3.13.0-54- <none>            <none>            (no description available)
un  linux-headers-3.13.0-55- <none>            <none>            (no description available)
un  linux-headers-3.13.0-57- <none>            <none>            (no description available)
un  linux-headers-3.13.0-58- <none>            <none>            (no description available)
un  linux-headers-3.13.0-59- <none>            <none>            (no description available)
un  linux-headers-3.13.0-61- <none>            <none>            (no description available)
un  linux-headers-3.13.0-62- <none>            <none>            (no description available)
un  linux-headers-3.13.0-63- <none>            <none>            (no description available)
un  linux-headers-3.13.0-65- <none>            <none>            (no description available)
un  linux-headers-3.13.0-66- <none>            <none>            (no description available)
un  linux-headers-3.13.0-67- <none>            <none>            (no description available)
un  linux-headers-3.13.0-68- <none>            <none>            (no description available)
un  linux-headers-3.13.0-71- <none>            <none>            (no description available)
un  linux-headers-3.13.0-73- <none>            <none>            (no description available)
un  linux-headers-3.13.0-74- <none>            <none>            (no description available)
un  linux-headers-3.13.0-76- <none>            <none>            (no description available)
ii  linux-headers-3.13.0-77  3.13.0-77.121     all               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77- 3.13.0-77.121     amd64             Linux kernel headers for version 3.13.0 on 64 bit x86
ii  linux-headers-3.2.0-57   3.2.0-57.87       all               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-g 3.2.0-57.87       amd64             Linux kernel headers for version 3.2.0 on 64 bit x86 
ii  linux-headers-3.2.0-58   3.2.0-58.88       all               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-g 3.2.0-58.88       amd64             Linux kernel headers for version 3.2.0 on 64 bit x86 
ii  linux-headers-generic    3.13.0.77.83      amd64             Generic Linux kernel headers
un  linux-image              <none>            <none>            (no description available)
un  linux-image-2.6          <none>            <none>            (no description available)
ii  linux-image-2.6.38-8-gen 2.6.38-8.42       amd64             Linux kernel image for version 2.6.38 on x86/x86_64
un  linux-image-3.0          <none>            <none>            (no description available)
ii  linux-image-3.0.0-14-gen 3.0.0-14.23       amd64             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.13.0-34-ge 3.13.0-34.60      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-35-ge 3.13.0-35.62      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-36-ge 3.13.0-36.63      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-37-ge 3.13.0-37.64      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-39-ge 3.13.0-39.66      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-40-ge 3.13.0-40.69      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-43-ge 3.13.0-43.72      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-44-ge 3.13.0-44.73      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-45-ge 3.13.0-45.74      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-46-ge 3.13.0-46.79      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-48-ge 3.13.0-48.80      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-49-ge 3.13.0-49.83      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-51-ge 3.13.0-51.84      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-52-ge 3.13.0-52.86      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-53-ge 3.13.0-53.89      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-54-ge 3.13.0-54.91      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-55-ge 3.13.0-55.94      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-57-ge 3.13.0-57.95      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-58-ge 3.13.0-58.97      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-59-ge 3.13.0-59.98      amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-61-ge 3.13.0-61.100     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-62-ge 3.13.0-62.102     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-63-ge 3.13.0-63.103     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-65-ge 3.13.0-65.106     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-66-ge 3.13.0-66.108     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-67-ge 3.13.0-67.110     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-68-ge 3.13.0-68.111     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-71-ge 3.13.0-71.114     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-73-ge 3.13.0-73.116     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-74-ge 3.13.0-74.118     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
rc  linux-image-3.13.0-76-ge 3.13.0-76.120     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
ii  linux-image-3.13.0-77-ge 3.13.0-77.121     amd64             Linux kernel image for version 3.13.0 on 64 bit x86 S
ii  linux-image-3.2.0-26-gen 3.2.0-26.41       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-29-gen 3.2.0-29.46       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-30-gen 3.2.0-30.48       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-31-gen 3.2.0-31.50       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-32-gen 3.2.0-32.51       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-33-gen 3.2.0-33.52       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-34-gen 3.2.0-34.53       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-35-gen 3.2.0-35.55       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-36-gen 3.2.0-36.57       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-37-gen 3.2.0-37.58       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-38-gen 3.2.0-38.61       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-39-gen 3.2.0-39.62       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-40-gen 3.2.0-40.64       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-41-gen 3.2.0-41.66       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-43-gen 3.2.0-43.68       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-44-gen 3.2.0-44.69       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-45-gen 3.2.0-45.70       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-48-gen 3.2.0-48.74       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-49-gen 3.2.0-49.75       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-51-gen 3.2.0-51.77       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-52-gen 3.2.0-52.78       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-53-gen 3.2.0-53.81       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-54-gen 3.2.0-54.82       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-55-gen 3.2.0-55.85       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-56-gen 3.2.0-56.86       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-57-gen 3.2.0-57.87       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-58-gen 3.2.0-58.88       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-59-gen 3.2.0-59.90       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-60-gen 3.2.0-60.91       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-61-gen 3.2.0-61.93       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-63-gen 3.2.0-63.95       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-64-gen 3.2.0-64.97       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-65-gen 3.2.0-65.99       amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
ii  linux-image-3.2.0-67-gen 3.2.0-67.101      amd64             Linux kernel image for version 3.2.0 on 64 bit x86 SM
rc  linux-image-extra-3.13.0 3.13.0-34.60      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-35.62      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-36.63      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-37.64      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-39.66      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-40.69      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-43.72      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-44.73      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-45.74      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-46.79      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-48.80      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-49.83      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-51.84      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-52.86      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-53.89      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-54.91      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-55.94      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-57.95      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-58.97      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-59.98      amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-61.100     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-62.102     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-63.103     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-65.106     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-66.108     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-67.110     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-68.111     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-71.114     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-73.116     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-74.118     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
rc  linux-image-extra-3.13.0 3.13.0-76.120     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
ii  linux-image-extra-3.13.0 3.13.0-77.121     amd64             Linux kernel extra modules for version 3.13.0 on 64 b
ii  linux-image-generic      3.13.0.77.83      amd64             Generic Linux kernel image
un  linux-initramfs-tool     <none>            <none>            (no description available)
un  linux-kernel-headers     <none>            <none>            (no description available)
un  linux-kernel-log-daemon  <none>            <none>            (no description available)
ii  linux-libc-dev:amd64     3.13.0-77.121     amd64             Linux Kernel Headers for development
un  linux-restricted-common  <none>            <none>            (no description available)
ii  linux-sound-base         1.0.25+dfsg-0ubun all               base package for ALSA and OSS sound systems
un  linux-source-2.6.38      <none>            <none>            (no description available)
un  linux-source-3.0.0       <none>            <none>            (no description available)
un  linux-source-3.13.0      <none>            <none>            (no description available)
un  linux-source-3.2.0       <none>            <none>            (no description available)
un  linux-tools              <none>            <none>            (no description available)
un  linux32                  <none>            <none>            (no description available)
```

---

### Post by ian-weisser on 2016-02-14
You are running a 3.13-series kernel, so it should be safe enough to try:
```
sudo apt-get remove linux-image-3.2.0* linux-headers-3.2.0*
sudo apt-get remove linux-headers-2.6* linux-headers-3.0* linux-image-2.6* linux-image-3.0*
sudo apt-get autoremove
```

See if that makes a difference for you.

A few of the older kernels had headers. Those could not be eligible for autoremove until the headers had been removed.

---

### Post by grahammechanical on 2016-02-14
If we want to do it through a GUI, then install Synaptic Package Manager. And after getting a list of the kernels search in Synaptic for the kernel. For example, from the list given by the OP, search for linux 3.2.0-26 and that will come up with some of the kernel files related to kernel 3.2.0-26.

we will will see this

linux-headers-3.2.0-26
linux-headers-3.2.0-26-generic
linux-image-extra-3.2.0-26-generic
linux-image-3.2.0-26-generic

Select linux-image and right click and select Mark for Complete Removal. That should also remove any other kernel related files not found by the search criteria. Then click apply.

With Synaptic we can queue up several kernels for removal before clicking apply. Or do it one at a time. Just do not remove all the kernels. Save at least 2. To test if we are keeping a working kernel use Grub boot menu Advanced options for Ubuntu to load into earlier kernels to see if we get to a working desktop.

It is wise to have at least 2 working kernels in case a kernel upgrade should break the desktop. Then we can load into one of the previous kernels.

Regards

---

### Post by ubfan1 on 2016-02-14
+1 on ian-weisser's caution.  Some of the kernel packages (like the two headers) leave files in other locations (like /usr/src) too.

---

### Post by pablo-2 on 2016-05-10
This will remove all the kernels except the last one. Remember to boot using the last kernel or bad things could happen (or not):

[FONT=courier new]dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get --dry-run purge[/FONT]

---

### Post by kurt18947 on 2016-05-11
> **grahammechanical said:**
> If we want to do it through a GUI, then install Synaptic Package Manager. And after getting a list of the kernels search in Synaptic for the kernel. For example, from the list given by the OP, search for linux 3.2.0-26 and that will come up with some of the kernel files related to kernel 3.2.0-26.

we will will see this

linux-headers-3.2.0-26
linux-headers-3.2.0-26-generic
linux-image-extra-3.2.0-26-generic
linux-image-3.2.0-26-generic

Select linux-image and right click and select Mark for Complete Removal. That should also remove any other kernel related files not found by the search criteria. Then click apply.

With Synaptic we can queue up several kernels for removal before clicking apply. Or do it one at a time. Just do not remove all the kernels. Save at least 2. To test if we are keeping a working kernel use Grub boot menu Advanced options for Ubuntu to load into earlier kernels to see if we get to a working desktop.

It is wise to have at least 2 working kernels in case a kernel upgrade should break the desktop. Then we can load into one of the previous kernels.

Regards


+ 1 for Synaptic. It hasn't let me do anything I've later regretted yet.

---

