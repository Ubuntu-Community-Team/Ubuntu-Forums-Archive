---
title: "Trying to install with LUKS &amp; LVM on VirtualBox with EFI"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2017-02-14
In anticipation of getting a new computer, I'm using VirtualBox to try to understand how to use LUKS and LVM with EFI. Even using the automatic installer, I am sadly having no luck.

What I did:
[LIST]
[*]For the VirtualBox machine, I enabled EFI, because of course the new computer will have EFI.
[*]In the Ubuntu installer, I chose the default "Erase disk and install Ubuntu".
[*]I also chose "Encrypt the new Ubuntu installation for security", which automatically selects "Use LVM with the new Ubuntu installation".
[/LIST]
So far, so good. This is all as expected.

However, once the installation has completed and I restart the computer, I get what I presume is an EFI error screen. It looks like the attached screenshot.

I also tried using Lubuntu instead of Ubuntu, but I had the same result.

At this point, I have absolutely no clue how to proceed.

What have I done wrong, and how can I fix it, please?

---

### Post by sudodus on 2017-02-14
I am not sure you did something wrong. I think that VirtualBox works well with the virtual machines running in BIOS mode. I have done some small tests in UEFI mode, and I am 'not sure that it works well'. It is much easier(!) to boot and install in UEFI mode in real machines, at least some machines.

Do you intend to dual boot with Windows? If this is the case, and you want to use the preinstalled Windows, you will also get preinstalled UEFI mode, and have to learn it.

Otherwise, if you intend to run only Ubuntu (or a flavour of Ubuntu), you can still select BIOS mode alias CSM or legacy mode in most computers, and the installation will be easier. It might also be easy to install in UEFI mode (depending on the computer's BIOS/UEFI system). Unfortunately some UEFI systems do not comply to the UEFI standard.

-o-

What kind of computer are you planning to buy? I think you can get good tips here - that will help you more than struggling with UEFI in VirtualBox.

Have you considered buying a professional class refurbished computer (maybe 2-3 years old)? This way linux has had time to catch up with the hardware and will work well.

---

### Post by Paddy Landau on 2017-02-14
Thank you for your reply, @sudodus.
> **sudodus said:**
> [COLOR=#000000]Do you intend to dual boot with Windows?[/COLOR]
The computer will almost certainly come with Windows 10 (as they nearly all do). However, I intend to wipe the disk and use Ubuntu, running Windows 10 within VirtualBox, because I hardly ever need to use Windows. (I've already contacted Microsoft about the licensing implications, and they've told me that I can transfer the license to VirtualBox as long as it remains on the original machine.)
> **sudodus said:**
> Unfortunately some UEFI systems do not comply to the UEFI standard.
How can I tell if the prospective computer adheres to standard EFI? Would it be enough to take an Ubuntu installation disk into the showroom and see if it boots successfully (that's what I've done before)?
> **sudodus said:**
> It is much easier(!) to boot and install in UEFI mode in real machines, at least some machines.
It's a shame that it doesn't work on VirtualBox, because I was wanting to check that I understood correctly how to use it.

[COLOR=#000000]Where should I raise a bug report?[/COLOR]
> **sudodus said:**
> What kind of computer are you planning to buy? … Have you considered buying a professional class refurbished computer…?
I haven't yet decided which computer to buy, but I want one that will last me a long time. I don't use the computer for gaming, so it doesn't have to be that powerful, but it will need sufficient RAM to run Windows in a virtual machine. Modern machines are so expensive, though![COLOR=#000000]
[/COLOR]

---

### Post by sudodus on 2017-02-14
> **Paddy Landau said:**
> Thank you for your reply, @sudodus.

The computer will almost certainly come with Windows 10 (as they nearly all do). However, I intend to wipe the disk and use Ubuntu, running Windows 10 within VirtualBox, because I hardly ever need to use Windows. (I've already contacted Microsoft about the licensing implications, and they've told me that I can transfer the license to VirtualBox as long as it remains on the original machine.)
OK> 
How can I tell if the prospective computer adheres to standard EFI? Would it be enough to take an Ubuntu installation disk into the showroom and see if it boots successfully (that's what I've done before)?
It is a good idea to take an Ubuntu installation disk into the showroom and see if it boots successfully. And ask here at our Ubuntu Forums :-)> 
It's a shame that it doesn't work on VirtualBox, because I was wanting to check that I understood correctly how to use it.

Where should I raise a bug report?
I don't know - Maybe via Launchpad, maybe directly via the VirtualBox web page> 
I haven't yet decided which computer to buy, but I want one that will last me a long time. I don't use the computer for gaming, so it doesn't have to be that powerful, but it will need sufficient RAM to run Windows in a virtual machine. Modern machines are so expensive, though!

---

### Post by Paddy Landau on 2017-02-15
Thanks, @sudodus. I'll ask on the VirtualBox forum, and decide where to raise a bug after that.

---

### Post by Paddy Landau on 2017-02-15
I have posted a [query on the VirtualBox forum]("https://forums.virtualbox.org/viewtopic.php?f=3&t=81844").

---

### Post by sudodus on 2017-02-15
I hope you get good support at the VirtualBox forum :-)

-o-

Have you decided if you want a laptop or a desktop computer? Depending of the kind of computer, I think we are many people who can suggest suitable brand names and models (including both new consumer class computers and refurbished profession class computers).

---

### Post by Paddy Landau on 2017-02-15
> **sudodus said:**
> Have you decided if you want a laptop or a desktop computer? Depending of the kind of computer, I think we are many people who can suggest suitable brand names and models (including both new consuder class computers and refurbished profession class computers).
Thank you for the advice. I haven't yet decided, but probably desktop because it's cheaper for the same hardware. I shall post back on the forum when I have a computer in mind.

---

### Post by Paddy Landau on 2017-02-16
I received a solution on the [VirtualBox forum thread]("https://forums.virtualbox.org/viewtopic.php?f=3&t=81844"). It seems to be a bug with the Ubuntu installer, so I have [raised a bug report]("https://bugs.launchpad.net/ubuntu/+bug/1665329").

I have a new problem — I can't enter the password for the LUKS disk — but that's a topic for a new query.

---

### Post by sudodus on 2017-02-16
I'm glad that you received good help at the VirtualBox forum :-)

It seems to me that there is a missing link to make Ubuntu boot in UEFI mode in VirtualBox. Ubuntu has made a system that works in computers, and VirtualBox has made a system that works with some linux distros, and both think that the other guy should make the missing link.

If would be very valuable, if you ***describe the details of your solution here***: the extra steps necessary to make things work to boot Ubuntu in UEFI mode in VirtualBox.

---

### Post by Paddy Landau on 2017-02-16
> **sudodus said:**
> *describe the details of your solution here*: the extra steps necessary to make things work to boot Ubuntu in UEFI mode in VirtualBox.

[LIST]
[*]You can identify the EFI partition, because it is formatted as FAT32 and contains a folder [FONT=courier new]EFI[/FONT], which contains a folder [FONT=courier new]ubuntu[/FONT], which contains some files.
[*]Ignore those folders and files; instead, on the root of that EFI partition, create a file named [FONT=courier new]startup.nsh[/FONT].
[*]The file [FONT=courier new]startup.nsh[/FONT] should contain the following single line:```
\EFI\ubuntu\grubx64.efi
```
[*]Now, you can boot.
[/LIST]
If, on booting, you receive a prompt for the LUKS password where you cannot type anything, that is a bug, apparently with Plymouth. There is a complicated workaround for now, entailing setting Grub to [FONT=courier new]nosplash[/FONT].

---

### Post by sudodus on 2017-02-16
Thanks for sharing your solution :-)

---

