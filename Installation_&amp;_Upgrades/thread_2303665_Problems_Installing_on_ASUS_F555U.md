---
title: "Problems Installing on ASUS F555U"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by aem0512 on 2015-11-20
Hello all,

I'm having a pretty tough time trying to install on my new ASUS F555U. It has a i7-6500u processor with integrated graphics. 

I want to install ubuntu in dual boot with Windows 10. I've allowed Windows to do all of its updates, made the restore discs, etc. The HDD is already partitioned into a Windows system partition plus a storage partition by default, so I shouldn't have to mess with that part too much at this point. 

I've changed the BIOS settings as suggested: disabled Secure Boot and Fast Boot. Left CSM disabled.

I wanted to install Linux Mint, but after booting into the usb and selecting "try linux mint" or whatever at the grub screen it just threw garbled errors at me and never booted into the DE. I had to hard shutdown with the power button.

Then I tried Ubuntu 14.04 and I can boot into that just fine, but I get an error saying "this computer has only 0 bytes disk space remaining". As a result, I get a "failed to add/activate connection" error when trying to connect to wifi. I'm using a 16GB usb drive so I have plenty of space. Also my touchpad doesn't work in the livecd so I had to use a usb mouse. Once I tried to install but got a "ubi-partman failed with exit code 10" error. I tried to shutdown but I had to shutdown with the power button again. Argh.

Thinking it may be best to use the newest kernels with the latest drivers, I tried Ubuntu 15.10...but when I try to boot into that, I just get a blank screen...and again have to turn off the system with the power button.

Here is the garbage Ubuntu 14.04 throws at me when I try to shutdown from the livecd. (I eventually have to just hit the power button.) I think this is the same garbled stuff I got trying to boot into Mint.
[ATTACH=CONFIG]265690[/ATTACH]

Thanks for reading and thanks in advance for your assistance!

---

### Post by ubfan1 on 2015-11-20
Getting to the grub menu means a successful boot.  Try the below option on the kernel line (vmlinuz...)  in the grub menu (edit by typing e,  then boot with ctrl-X or f10)
Skylake needs this (15.04...):
i915.preliminary_hw_support=1

---

### Post by aem0512 on 2015-11-20
Hmmm...that doesn't appear to be working. I'm trying this on Ubuntu 15.10 and I've added the i915.preliminary_hw_support=1 both before quiet splash and after, but no luck. Are you supposed to put it before the --- or after the --- at the end? 

I tried pci=nomsi and that got me in and ready to install. My wifi and touchpad both work also. I'll report back if successful.

---

### Post by aem0512 on 2015-11-20
Looks like everything works ok under Ubuntu 15.10 with boot option pci=nomsi added to the grub config.

I have googled this option and msi, but I can't really determine whether I'm missing out on anything by not using it...do I need it? Is it somehow preferable?

---

### Post by oldfred on 2015-11-20
I had to look as I do not know either.

Something new (in 2003) Message Signalled Interrupts, related to PCI which every version of kernel has changes as PCI keeps changing.

[https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt)
>     nomsi        [MSI] If the PCI_MSI kernel config parameter is
                enabled, this kernel boot option can be used to
                disable the use of MSI interrupts system-wide.


The MSI Driver Guide HOWTO
[URL="https://lwn.net/Articles/44139/"]https://lwn.net/Articles/44139/

[http://electronics.stackexchange.com/questions/76867/what-do-the-different-interrupts-in-pcie-do-i-referring-to-msi-msi-x-and-intx](http://electronics.stackexchange.com/questions/76867/what-do-the-different-interrupts-in-pcie-do-i-referring-to-msi-msi-x-and-intx)
[/URL]

---

### Post by dutara on 2016-05-17
> **aem0512 said:**
> Hmmm...that doesn't appear to be working. I'm trying this on Ubuntu 15.10 and I've added the i915.preliminary_hw_support=1 both before quiet splash and after, but no luck. Are you supposed to put it before the --- or after the --- at the end? 

I tried pci=nomsi and that got me in and ready to install. My wifi and touchpad both work also. I'll report back if successful.

Bravo!  I got an F555U nearly a month ago, and have put a lot of time into trying to get 16.04 to run.  **pci=nomsi**  did the trick, along with **nodmraid** . It's curious that with all the searching and sifting I did I hadn't found this thread sooner.

For the sake of clearing up confusion regarding grub command syntax, put the switches, single-space delimited, to the left of the "---"

Actually the install didn't complete because there is some issue with booting: I'm trying to go dual-boot with Win10.  I may have complicated things by converting the GPT to a MBR partition.  If you have experience you'd care to relate on this particular model I'd appreciate it.  I'm taking a day or off from this before I start going through oldfred's links.

---

### Post by oldfred on 2016-05-18
@dutara
If you have issues best to start your own thread. 
I also am a proponent of gpt. And started converting from the 35 year old MBR to gpt with my install of 10.10. All new drives or reformatted drives are now gpt.

---

### Post by Matthew_Abd-El-Aha on 2016-06-12
Could I please get a written example of where the nomsi command fits?

---

### Post by oldfred on 2016-06-12
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)

You add pci=nomsi like nomodeset in these examples:

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 


 [http://ubuntuforums.org/showthread.php?t=2327103&p=13502963#post13502963](http://ubuntuforums.org/showthread.php?t=2327103&p=13502963#post13502963)

---

### Post by muddymillipede on 2016-07-07
just write pci=nomsi to the left of quite slash

---

