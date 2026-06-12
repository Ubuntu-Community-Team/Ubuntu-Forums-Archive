---
title: "Ubuntu 10.10 showing only 1 core instead of 4"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by tekkenlord on 2011-03-10
Hello all,

I have a Dell precision workstation with an Intel Xeon W3570 quad-core processor. I recently tried to install Kubuntu 10.10 (64-bit) on the box, which currently has Kubuntu 10.04 (64-bit). 

I first encountered an error while booting from the LiveCD, saying 
"Unable to find a medium containing a live file system", and the computer would just stuck there. After searching the forums, I added "acpi=off" to the kernel boot options and it worked.

The problem now is that the system is showing only one core instead of four, and I cannot figure out why. On Kubuntu 10.04, it shows all cores.

The LiveCD was burned properly (checked MD5sums, integrity etc) and I also tried Ubuntu and even Linux Mint -- always the same problem as described above.

Any help would be appreciated!

---

### Post by realzippy on 2011-03-10
It will not help you,but I am quite sure that your issue is due to the boot option acpi=off....

---

### Post by tekkenlord on 2011-03-10
is there any other option to avoid the "unable to find medium..." problem apart from the "acpi=off"?

---

### Post by tekkenlord on 2011-03-10
You are definitely right about the "acpi=off" causing the incorrect display of number of cores. I tried booting my 10.04 with "acpi=off" and resulted in the system showing only 1 core. 

So, I guess it comes down to finding a way to boot the LiveCD without "acpi=off"... anyone?

---

### Post by akand074 on 2011-03-10
> **tekkenlord said:**
> You are definitely right about the "acpi=off" causing the incorrect display of number of cores. I tried booting my 10.04 with "acpi=off" and resulted in the system showing only 1 core. 

So, I guess it comes down to finding a way to boot the LiveCD without "acpi=off"... anyone?

Umm, I believe you can press 'esc' as the Ubuntu live CD just starts to boot, it will cancel and drop to a menu where you choose your language then it will give you options to either install ubuntu, try ubuntu without installing and also an option to set certain things including acpi and noapic etc.

---

### Post by tekkenlord on 2011-03-10
Yes, I am aware of that. The problem is that if I do not set the acpi=off option, then I get the "Unable to find a medium..." error.

On the other hand, if I set acpi=off option on, then the system only shows 1 core out of 4.

---

### Post by owiknowi on 2011-03-10
is it possible for you to create a bootable usb stick with the ubuntu 10.10 x86_64 iso?
and see if the problem still occurs (bios must be able to boot from usb as you've probably already guessed)

---

### Post by tekkenlord on 2011-03-10
Hehe, I was actually just reading instructions on how to boot Ubuntu from a LiveUSB. I will post back when I have something. Thanks

---

### Post by tekkenlord on 2011-03-10
Yep, it seems that the system boots up fine from the USB, and recognises all 4 processors! I will install it now, and mark the thread as SOLVED if all goes smoothly. Thanks everyone for their help!

---

### Post by tekkenlord on 2011-03-10
Hehe, another problem now. The processors are all shown, but when I am about to install the system, it cannot find my hard drive. That is, there is no device being shown in the partition manager.

Once again, booting with "acpi=off" results in the detection of the hard drive, as well as the loss of the 3 cores.... back to square one.

I will try using the alternate CD installer and see what happens...

---

### Post by realzippy on 2011-03-10
acpi=ht

might be an option instead of acpi=off,if you have no luck with the alternateCD.

*"Impact Deactivates the ACPI system almost completely; only the components required for hyper threading will be used. "*


[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) gives a few more noacpi varieties...

---

### Post by tekkenlord on 2011-03-10
Thanks realzippy, but no luck with the alternate CD nor the acpi=ht...

---

### Post by realzippy on 2011-03-10
..also tried other acpi varieties from that link?

Until someone knows what to do I would install the system,run all updates (there are some kernel updates..),then try booting without noacpi...fingers crossed.

---

### Post by tekkenlord on 2011-03-10
Yes, I tried other varieties too with no success... I found this:

[http://forums.opensuse.org/archives/sf-archives/archives-hardware/340548-intel-core-2-quad-shows-only-one-core-cpuinfo.html](http://forums.opensuse.org/archives/sf-archives/archives-hardware/340548-intel-core-2-quad-shows-only-one-core-cpuinfo.html)

which suggests adding "pci=nommconf" and presumably worked for some users. 

I tried it that too but still does not work...

---

### Post by matt_symes on 2011-03-10
Hi

Have you tried 10.04 ? Does the same thing happen ?

From

[http://www.lesswatts.org/projects/acpi/debug.php](http://www.lesswatts.org/projects/acpi/debug.php)

> acpi=ht
the most like "acpi=off", disables all of ACPI except what is needed to enumerate processors. 
If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code

What do you make of that ?

Kind regards

---

### Post by realzippy on 2011-03-10
give

pci=nocrs

a shot please if you have not already...   ;-)

..from

[http://ubuntuforums.org/showthread.php?t=1595809&page=4](http://ubuntuforums.org/showthread.php?t=1595809&page=4)

which seems to be interesting.

---

### Post by tekkenlord on 2011-03-10
> **matt_symes said:**
> 

Have you tried 10.04 ? Does the same thing happen ?



Yes, I have tried 10.04 and everything works perfectly there. It is only with Maverick that I get these problems.

Very interesting webpage the one you suggested. It does seem that acpi=off boots my system, but acpi=ht does not. So, maybe there is something wrong with the SMP code?


[QUOTE=realzippy]
Until someone knows what to do I would install the system,run all updates (there are some kernel updates..),then try booting without noacpi...fingers crossed. 

[/QUOTE]

I just finished installing and upgrading the system, but still no success... 

The good news though, is that I tried adding pci=nocrs to the boot options, and the system boots up and shows all 4 cores!!!

The only thing that worries me is that the effects (minimisation, etc) seem to be very choppy now, but this could be due to the graphics drivers. I will install the proprietary drivers from NVIDIA and post back.

Thank you very much realzippy and matt_symes!

---

### Post by matt_symes on 2011-03-10
Hi

Glad it's working.

Nicely done realzippy. :popcorn: 

I know what i will be reading up on for the next hour.

Kind regards

---

### Post by tekkenlord on 2011-03-10
Just installed the NVIDIA driver, and everything seems to be smooooth!! Thanks a lot again for your help!

---

