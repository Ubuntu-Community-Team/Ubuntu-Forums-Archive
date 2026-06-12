---
title: "Cannot install on Lenovo S205 because of EFI"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by jingaling on 2011-09-01
Hi Guys,

I've jut bought myself a new laptop and I am having real trouble getting Ubuntu to run on it. After some research I've found that EFI is causing the problem because the linux Kernel doesn't like it apparently. I also ready that Linux Kernel 3 'likes' EFI and can cope with it.

So, I installed 11.06 Alpha 3 (thats Kernel 3 isn't it??) but th machine still won't boot to Ubuntu. When trying 11.04 earlier I just got a re-boot loop when the machine began to POST, however since installing 11.10 Alpha 3 the machine does now boot...just not into Ubuntu. Instead it just boots straight into windows as if Ubuntu isn't even there.

I've seen online that you can downgrade to GRUB legacy and that will work but I really don't want to do that as it's going in the wrong direction as far as I'm concerned.

If anyone can shed any light on how to get this machine working with EFI then I would really appreciate it! I've been using Ubuntu so long that Windows just feel wrong now and is driving me mad.

Thanks guys

Jing

---

### Post by cutekazuya on 2011-09-02
hello mate,

I bought a lenovo s205 aswell and spent entire weekend trying to get it to work and at the end I returned it back to store and got an asus netbook instead.

What I found was:

Dual boot it with Windows 7 -

You have to create 3 partitions: 255MB ext2, xxxGB ext4 and XGB SWAP. You then have to revert to grub legacy for it to work, There is a really good guide on this:

[http://helms-deep.cable.nu/~rwh/blog/?p=177]("http://helms-deep.cable.nu/%7Erwh/blog/?p=177")

I was NOT successful with this method and no matter what, I could not get it to work.

Ubuntu 11.04 only -

Download Ubuntu 11.04 64bit and when you install it, let Ubuntu use the whole HDD. This wont give you boot loops and it will work. I found that after few reboots, it was booting into blank window.

Whatever method you choose, once you get it going there are other issues. shutdown, restart, suspend, WIFI, SDCARD slot, microphone wont work so good luck with that. When i plugged in headphones, the sound was playing in headphones aswell as speakers.

I also tried Ubuntu 10.10 32/64 and it was pretty much the same as 11.04. You have to either revert to grub legacy or use Ubuntu only. Shutdown/restart/suspend worked but wifi and other issues.

Ubuntu 9.04 has the older grub by default so this worked no problems without boot loops. Suspend/restart/shutdowns also worked no problem but graphics and WIFI issues.


Make sure you backup you current Windows + recovery using clonezilla before you attempt anything, in case if you want to return it.

Apparently there is a bug in this netbook bios (UEFI) that causes all this trouble and no idea when Lenovo is to fix it. Its a very good spec netbook for the price but Ubuntu just wont play good at present. 

I exchanged mine for an Asus netbook and everything works out the box : )

Good luck!!

---

### Post by srs5694 on 2011-09-02
> **jingaling said:**
> I've jut bought myself a new laptop and I am having real trouble getting Ubuntu to run on it. After some research I've found that EFI is causing the problem because the linux Kernel doesn't like it apparently. I also ready that Linux Kernel 3 'likes' EFI and can cope with it.

As a general rule, EFI is *not* a problem for Linux kernels. It's conceivable that there's an issue with the Linux kernel and the UEFI implementation in your specific laptop, or with specific kernel compile-time or boot-time options, but overall I think you're on the wrong track with this train of thought.

As evidence, I'm running Ubuntu on three EFI- or UEFI-based systems: a Mac Mini ([booting in EFI mode](http://www.rodsbooks.com/ubuntu-efi/index.html)), a PC with an Intel motherboard that I'm using as a MythTV box, and a VirtualBox installation using VirtualBox's UEFI implementation. I've got other Linux distributions installed on these or other (U)EFI-based systems, too.

What *is* a problem is Linux installation tools, which tend to have poor (U)EFI support. It's also possible that you accidentally installed Windows in UEFI mode and Linux in BIOS mode, or vice-versa, which would complicate your boot options.

> So, I installed 11.06 Alpha 3 (thats Kernel 3 isn't it??) but th machine still won't boot to Ubuntu. When trying 11.04 earlier I just got a re-boot loop when the machine began to POST, however since installing 11.10 Alpha 3 the machine does now boot...just not into Ubuntu. Instead it just boots straight into windows as if Ubuntu isn't even there.

I can't be sure of what's happening without much more diagnostic information. The output of [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) (its RESULTS.txt file) is a start, but it provides limited information about EFI booting. A complete file list of all the files in the EFI System Partition (ESP) would be helpful, too.

> I've seen online that you can downgrade to GRUB legacy and that will work but I really don't want to do that as it's going in the wrong direction as far as I'm concerned.

When booting in EFI mode, a stock GRUB Legacy installation will be useless because GRUB Legacy is a BIOS-only boot loader. Fedora ships with a heavily modifed version of GRUB Legacy with EFI support, so using that version might get the system booting. Alternatively, you could boot the computer in BIOS compatibility mode; but that might necessitate changes to your Windows installation.

---

### Post by jingaling on 2011-09-02
Gents,

Thanks for the info, I really appreciate the comrehensive replies.

I really like this machine, even in windows, I'm starting to get used to it now so I might stick with it and see if I can work around the problem(s). I've seend a [video on youtube]("http://www.youtube.com/watch?v=ij9To78Wt3w") that shows this machine booting to Natty without a problem.

I might give fedora a while, only problem is that I have only ever used debian bases systems so I will be starting from stratch with Fedora...plus GNOME 3 sickens me.....it's all a learning curve though - which is why love linux so much!

You mention that I may have installed windows i UEFI mode and bun2 in BIOS mode or vice verca...I'm extremely competent when it comes to Windows (only been using linux about 2 years) and I didn't know there was a way to pick whether to install as UEFI or BIOS. Could you elaborate on this a little please?

Thanks again guys!!!!

Jing

---

### Post by srs5694 on 2011-09-02
> **jingaling said:**
> You mention that I may have installed windows i UEFI mode and bun2 in BIOS mode or vice verca...I'm extremely competent when it comes to Windows (only been using linux about 2 years) and I didn't know there was a way to pick whether to install as UEFI or BIOS. Could you elaborate on this a little please?

Since the very first IBM PC, it and its clones and descendents and clones' descendents have used a type of firmware called the Basic Input/Output System (BIOS). The BIOS is old and awkward and manufacturers are finally ready to put it out of our misery, as they say. The replacement is known as the Extensible Firmware Interface (EFI), with the latest version of EFI being the Unified EFI (UEFI) -- esssentially, EFI 2.x. The most critical differences between BIOS and UEFI for purposes of this discussion are that they boot in entirely different ways and they require different boot loader code. An average user who buys a computer from Best Buy and never installs any other OS will never know the difference, but if you're setting up a dual-boot computer, it's important that you know whether your computer uses a BIOS or a UEFI. If you don't, you'll be relying on installer programs' intelligence (about that of the average grasshopper) and random chance to get things working right. The title you chose for your thread suggests you already know you're using an EFI, but there's a possible twist....

Most (maybe all) modern UEFI implementations include a BIOS compatibility mode, which enables the computer to boot using the old BIOS-style boot loaders. This feature can help if you're using a UEFI-unaware OS, but in practice, these features are usually poorly labelled in the firmware setup utilities. Typically, there's a "Boot" screen with options, some of which may refer to "UEFI" or "EFI" options to enable the new UEFI-style booting. Most OSes also don't make it clear whether they're booting and installing in BIOS mode or in UEFI mode, so this important detail is often hidden from users.

Also, most manufacturers continue to use the term "BIOS" in reference to their firmware, even though it's UEFI firmware rather than BIOS in a strict sense.

---

### Post by jingaling on 2011-09-04
Thanks SRS I have now admitted defeat and returned the machine.

Cutrkazuya, can you tell me which asus you bought please our can someone recommend an 11.6" high spec netbook please (around 4gb ram, at least 250gb hdd and dual core) as I'm really struggling to find one. Thanks again guys!

Jing

---

### Post by cutekazuya on 2011-09-05
> **jingaling said:**
> Thanks SRS I have now admitted defeat and returned the machine.

Cutrkazuya, can you tell me which asus you bought please our can someone recommend an 11.6" high spec netbook please (around 4gb ram, at least 250gb hdd and dual core) as I'm really struggling to find one. Thanks again guys!

Jing

I chose Asus 1015px for £249.99 as I had 1000h before. 1015px works perfectly even though it has the new EFI. This netbook is Ubuntu certified and you can buy it ubuntu pre-installed from some countries.

[http://www.ubuntu.com/certification/hardware/201103-7432](http://www.ubuntu.com/certification/hardware/201103-7432)

The one I bought came with Windows 7 starter which is absolute rubbish, you cannot even change wallpaper but I have it dual booted with no effort.

I cannot really recommend any other as I could not find a similar spec netbook to S205 with the same price but I am happy with asus and prefer the smaller 10 screen.

Have a look at **Asus 1101HA** 11.6 aswell.

Just shop around, you will definitely find something you like and just search the model with Ubuntu in google and you should get general idea if it works or not.

---

