---
title: "Update Manager installed old kernel"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by donofrij on 2011-11-23
I have a single 250 GB hhd installed, with the following partitions: sda 1 (Windows os); sda5 (/home-Ubuntu documents-ext4); sda6 (windows documents-ntfs); sda7 (/-Ubuntu os); and sda8 (linux swap). The Windows Documents partition (sda6) shows as D drive in Windows My Computer. I also have several usb flash drives that show as 'F', 'G', and 'H' drives in Windows My Computer, as well as a DVD drive 'E'. 

I installed Ubuntu 11.10, kernel 3.0.0-_13 _on sda 7, weeks ago and it has been working fine. Several days ago I opened/ran Update Manager and installed all of the listed updates. When I booted my computer yesterday, in Grub 2, I saw the following new options:

Ubuntu, with linux 3.0.0-_12_-generic (on /dev/sd_d_5)
Ubuntu, with linus 3.0.0-_12_-generic (recovery mode) (on /dev/sd_d_5)

In Terminal, I ran the following command:

sudo apt-get rm linux-headers-3.0.0-12 linux headers-3.0.0-12- generic.

 When I re-booted and updated Grub, the same two 3.0.0-12 options appeared, but this time on sd_e_5 (instead of sd_d_5)! If I select 3.0.0-12, Terminal opens up, it runs, and I get some kind of recovery option. One of the options is 'Proceed to Normal Boot'. If I select this, then Ubuntu eventually opens up, but from where I don't know. I think it is also the prior version Ubuntu 11.03 (which I had previously updated to 11.10). 

I searched Synaptic Package Manager and uninstalled kernel 3.0.0-12. And it now is NOT marked 'installed'! Yet, it still appears in Grub2 and still opens as described above.

What is going on? Where is this kernel (3.0.0-12) located on my hhd? And how can I remove it, both from my machine and from Grub2?

Thanks

---

### Post by Frogs Hair on 2011-11-23
If you installed the 3.0.0-13 kernel separately , Ubuntu due to the meta packages will update the kernel you are supposed to have and not a kernel installed manually .

Currently by lucky coincidence . you can get the 3.0.0-13 via the update manager by opening settings and selecting pre-released updates and the kernel will update normally . I have been using it for weeks .

Caution ! pre-released updates will make many changes to your system and you will receive a lot of updates   . 

I use the package cleaner in Ubuntu Tweak for removing old kernels , but be sure to use the 11.10 PPA linked on the main page . [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

### Post by donofrij on 2011-11-25
Thanks a lot! I installed Ubuntu Tweak, went to Janitor, and selected and removed old kernels (3.0.0-12). Now, the only installed linux-image that appears as 'Installed' in SPM is the most recent one (3.0.0-13), which is the one I want.

However, at boot, in Grub-2, the following options still appear:

3.0.0-13-generic
3.0.0-13-generic (recovery mode)
3.0.0-12 (generic) (on /dev/sde5)
3.0.0-12 (generic (recovery mode) (on /dev/sde5)

And, in Terminal, when I change directory (cd) to /boot, and then list (ls), I get the following kernels:

3.0.0-13
2.6.38-12
2.6.38-8

(all 3 have abi, initrd, vmlinuz, vmcoreinfo, system map and cofig files)

1) what is /dev/sde5, and where is it located in the file system?
2) why the differences between what appears as installed in SPM, what appears at boot in Grub2, and what shows when I list the contents of Grub2 in Terminal? Ultimately, I simply want to remove the 3.0.0-12 kernel options at boot in Grub2. How do I best and simplest do that? Thanks again

---

