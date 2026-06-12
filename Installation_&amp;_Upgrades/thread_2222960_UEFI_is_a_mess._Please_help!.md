---
title: "UEFI is a mess. Please help!"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by x34460 on 2014-05-08
Last fall, I bought a new computer with Win8 preinstalled. This would be my first time using UEFI.

I waited a while but finally got around to installing LinuxMint alongside of Windows.
Being my first time using UEFI, it seemed like a lot just to get Linux installed but regardless... it worked. 
Since that time last fall I have been enjoying Mint and when necessary, can boot into Windows on the very rare occasion that I need to.

Recently, I wanted to experiment with OSX86.
I had an older, unused AMD64 HP laptop to use so I tinkered a bit.
Technically, the install was successful but it was far from perfect and really could not be used in any practical sense.
I tried several different versions but only one would work.

Insatiably curious to play around with OSX, I knew my new laptop was much more compatible with the OSX86 project so against my better judgement, I pulled the HDD out, as to prevent any chance of data corruption or loss, and used the USB drive from the HP I had already installed OSX86 on.
I ran the installer and went thru all of the steps again but the installation failed and would not work at all.

I'd had enough and put my HDD back into the "new" Intel and from there all I got was a grub2 prompt.
No more OS choices.
No more booting.

I attempted to run the same "boot repair disc" I had used when installing mint late last year but it would not work.
I later discovered that with each attempt I was making, the repair disc kept using AMD64 files for repair.
That wont work because the HDD resides in an Intel environment.
I have recently learned that UEFI uses settings from last session in NVRAM?
If this is true, then the UEFI must think it's in an AMD64 environment due to the OSX86 install attempts?

I have attempted to resolve this issue myself, using search, videos, community and in another thread here, all to no avail.

My experience with UEFI is extremely limited.
Prior to trying to solve this issue, the only other time I have interacted with EUFI is when I installed Mint last fall and compared to this, it was "easy".

I have made several attempts to follow instructions [here]("https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell"), [here]("http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD") and [here]("https://software.intel.com/en-us/articles/efi-shells-and-scripting/") but I am not having success with these methods.

What little help I have received has been either either too simplified or too complicated.

Is there anyone out there that has the knowledge and ability to help but is also able to communicate it clearly and simply in a way that this hobbyist can understand?

Any help from a fellow user is greatly appreciated.

Thanks.

---

### Post by oldfred on 2014-05-08
Is this thread different than your other threads?
We all are volunteers tying to help others and need to know what has been tried to not duplicate effort.
[http://ubuntuforums.org/showthread.php?t=2222472](http://ubuntuforums.org/showthread.php?t=2222472)

I understand a sense of frustration. 
But UEFI is relatively new only 10 years old, but only actively used since Macs started with the change to Intel chips and new PCs with Windows 8. UEFI for PCs is currently AMD64 or 64 bit only. Not sure about Mac as they use an old UEFI version.

Also you cannot be a new user if you installed so many different operating systems.
I do not know about OSX, but your agreement to abide by the Ubuntu forum code of conduct is that we do not support that as a violation of another companies terms of use.

thread closed, see previous thread.

---

