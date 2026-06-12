---
title: "Deleting old kernels"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by cle-ziskind on 2015-02-04
I have, when running update-grub, a bunch (30? 40?) old kernels listed. I'd like to clean them up.

Problem is, some of them are listed:

Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic

But don't seem to exist in dpkg:

# dpkg -l | grep linux-image-|grep "2.6"
#

How is that even possible? Am I heading for a train wreck? How do I bring the two back into sync?

Thanks!

---

### Post by mörgæs on 2015-02-04
Please post the output of **uname -a**.

---

### Post by cle-ziskind on 2015-02-04
Linux geulah 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i
686 i686 GNU/Linux


(Don't think it matters, but the latest kernel in the system is 3.13.0-45; i.e., the system needs rebooting.)

---

### Post by mörgæs on 2015-02-04
Yes. 
After that please run ```
sudo apt-get autoremove
``` and let the system rest for as long as the command takes.

---

### Post by cle-ziskind on 2015-02-04
Nothing;

# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
#

---

### Post by mörgæs on 2015-02-05
Please post the output from ```
sudo update-grub
``` in CODE tags.

---

### Post by cle-ziskind on 2015-02-05
> **mörgæs said:**
> Please post the output from ```
sudo update-grub
``` in CODE tags.

```
# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-42-generic
Found initrd image: /boot/initrd.img-2.6.32-42-generic
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
#
```

---

### Post by mörgæs on 2015-02-05
That is... interesting. 
What happens if you try to boot one of the 2.6.32 kernels?

---

### Post by cle-ziskind on 2015-02-05
Dunno. Server is headless, and I really try to avoid rebooting it.

Question: the cited kernels live in /boot. Would I hose my system if I removed them, them ran update-grub?

---

### Post by mörgæs on 2015-02-07
You need to test that a server comes up again after a reboot. Some day there will be a power loss.

---

### Post by cle-ziskind on 2015-02-08
Easy for you to say. :-) I just bite my fingernails and hope for the best. 

But, back to my question: am I asking for trouble by deleting /boot/[old-stuff], and updating grub? Is this (relatively) safe?

---

### Post by Illydth on 2015-02-08
Same problem here.  In /boot I have an abi, config, initrd.img, System.map and vmlinuz file for 2.6.38-12-generic.  However dpkg -l does not show a 2.6.38 kernel installed or any packages from 2.6.38.  

I always assumed this was some kind of default "if all else fails" kernel installed with Ubuntu, but then again I think my 12.04 -> 14.04 upgrade will be the 3rd upgrade for this system without a reinstall, so maybe this came from somewhere back along the line.

Same question here:  If I were to remove the files from /boot, what would that do to grub?  As to your question of "does it boot" the answer is: Yes, and very well too.  Looks like NVIDIA drivers are still in the kernel, it grub's right in (if you hold shift and tell it to do old kernels, etc.) and even my MythTV Frontend comes right up.

--Doug

---

### Post by mörgæs on 2015-02-09
Please post all outputs required earlier in the thread.

---

### Post by Elfy on 2015-02-09
You upgraded to 12.04 from 10.04 I assume, that would explain the kernels still sitting in /boot.

Is that correct? 

The 3.2's are old 12.04 kernels.

What do you get if you 

```
dpkg-l linux-image*
```

That will show what is properly installed, if there are orphans in /boot I would remove them, then run update-grub.

But you're going to have to reboot at some point if you want to use the newer kernel.

---

### Post by cle-ziskind on 2015-02-09
> **mörgæs said:**
> Please post all outputs required earlier in the thread.

Sorry, which outputs did I miss? I posted `uname -a`, I posted `apt-get autoremove`, and I posted `update-grub`. The only thing I did not try so far is rebooting. 

Did I miss something?

---

### Post by mörgæs on 2015-02-09
It was meant for Illydth. If he has a similar problem we could take a look at that at the same time.

The results from Elfy's command (in CODE tags) would be interesting to see for both of you.

---

### Post by cle-ziskind on 2015-02-09
> **Elfy said:**
> You upgraded to 12.04 from 10.04 I assume, that would explain the kernels still sitting in /boot.

Is that correct? 

Yes.
> **Elfy said:**
> 

The 3.2's are old 12.04 kernels.

What do you get if you 

```
dpkg-l linux-image*
```

That will show what is properly installed, if there are orphans in /boot I would remove them, then run update-grub.

But you're going to have to reboot at some point if you want to use the newer kernel.

I get:

```
# dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
rc  linux-image-3. 3.13.0-34.60 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-35.62 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-36.63 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-37.64 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-39.66 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-40.69 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-43.72 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-44.73 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-45.74 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-29.46  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-30.48  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-32.51  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-36.57  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-37.58  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-38.61  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-44.69  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-49.75  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-51.77  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-58.88  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-67.101 i386         Linux kernel image for version 3.
rc  linux-image-ex 3.13.0-34.60 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-35.62 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-36.63 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-37.64 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-39.66 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-40.69 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-43.72 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-44.73 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-45.74 i386         Linux kernel extra modules for ve
ii  linux-image-ge 3.13.0.45.52 i386         Generic Linux kernel image
ii  linux-image-ge 3.13.0.45.52 i386         Transitional package
#

```

---

### Post by Elfy on 2015-02-10
> **cle-ziskind said:**
> Yes.


I get:

```
# dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
rc  linux-image-3. 3.13.0-34.60 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-35.62 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-36.63 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-37.64 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-39.66 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-40.69 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-43.72 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-44.73 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-45.74 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-29.46  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-30.48  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-32.51  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-36.57  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-37.58  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-38.61  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-44.69  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-49.75  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-51.77  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-58.88  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.2.0-67.101 i386         Linux kernel image for version 3.
rc  linux-image-ex 3.13.0-34.60 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-35.62 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-36.63 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-37.64 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-39.66 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-40.69 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-43.72 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-44.73 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-45.74 i386         Linux kernel extra modules for ve
ii  linux-image-ge 3.13.0.45.52 i386         Generic Linux kernel image
ii  linux-image-ge 3.13.0.45.52 i386         Transitional package
#

```
Remove the 2.6's from /boot run update-grub

You should be able to do the same with the 3.2's.

---

