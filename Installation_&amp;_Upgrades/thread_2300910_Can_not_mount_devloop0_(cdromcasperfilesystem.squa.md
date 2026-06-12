---
title: "Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by RamonB on 2015-10-29
I'm trying to run a live USB pendrive with Ubuntu Desktop 15.10 in my notebook Dell Inspiron 14 5447 with UEFI & Secure Boot. At Windows, I use the options *Settings > Update & Security > Recovery > Advanced Initialization *(I don't know if these are the right names in english because my Windows is in portuguese).

When it boots up and starts to load it, this message shows up:

```
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

Alternatives that I've already tried:
- I tested with other flavors, like Gnome Shell, Xubuntu and even Elementary OS and all of them worked fine. Only Ubuntu Desktop failed.
- I disabled Secure Boot.
- I tried several programs to generate the pendrive (*Live USB Creator* from Fedora & *Rufus*). (I've also tried *uNetBootin* & *Yumi* but they hasn't worked at all and it hasn't booted up neither Ubuntu Desktop nor the other flavors.)
- I checked the MD5SUM of the ISO file and it was OK.
- I downloaded an alternative version of Ubuntu Desktop, its MD5SUM was OK and it also failed.
- I changed the pendrive and made a full formatting.

Nothing worked with Ubuntu Desktop. Does anyone know what's the problem?

Thank you.

---

### Post by mystics on 2015-10-29
> **RamonB said:**
> - I tried several programs to generate the pendrive (*Live USB Creator* from Fedora & *Rufus*). (I've also tried *uNetBootin* & *Yumi* but they hasn't worked at all and it hasn't booted up neither Ubuntu Desktop nor the other flavors.)

Have you tried using dd or mkusb? I've had this issue with some other other distros, and those worked without any problem.

---

### Post by oldfred on 2015-10-29
Another alternative if you want UEFI only.

 Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode, you must choose in UEFI boot tab menu the UEFI:flashdrive entry. Various UEFI may show it differently, but with UEFI only it should be only choice.

Also see details in link in my signature below.

---

### Post by RamonB on 2015-10-29
> **mystics said:**
> Have you tried using dd or mkusb? I've had this issue with some other other distros, and those worked without any problem.

Hi, mystics. I tried with dd & mkusb (with mkusb I had to disable Secure Boot). The same error in both of them. Thanks but it didn't worked.


> **oldfred said:**
> Another alternative if you want UEFI only.

 Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode, you must choose in UEFI boot tab menu the UEFI:flashdrive entry. Various UEFI may show it differently, but with UEFI only it should be only choice.

Also see details in link in my signature below.

Hi, olfred, I also tried this way, it booted up but also failed with the same message.

I forgot to say that I've read in another thread that this problem can occur because of lack of memory. This isn't my case because my Dell has 16 GBytes RAM. And besides that, other distributions (Gnome Shell, Xubuntu, Elementary OS) run OK.

Thank you both.

---

### Post by oldfred on 2015-10-30
If the other flavors work, I would still suspect the down load is not correct. 
The underlying Linux in all the Ubuntu flavors is the same and should boot the same with only the gui being different.
If md5sum is correct, are you using same flash drive as other flavors?

---

### Post by RamonB on 2015-10-31
Hi, oldfred, I've had the same feeling that the problem was a wrong download. So, I've already downloaded the Ubuntu Desktop 3 times. All of them were MD5SUM OK. I also tried 3 different flash drives (including a brand new one from Kingston) and I tested other flavours with the same flash drive.  

So, I've decided to install Gnome Shell although I'd prefer (and I'm accustomed to) Unity. I'm having some difficulties with Gnome 3 but it's good because is a way of learning something new.

Thank you very much.

---

### Post by sudodus on 2015-10-31
In order to check, I cloned **ubuntu-15.10-desktop-amd64.iso** to a USB pendrive with mkusb. I made a live-only pendrive. This is actually cloning with dd under the hood, so you should get exactly the same result with dd (but without 'safety belt'). This pendrive can boot my Toshiba in UEFI mode.

Like *oldfred*, I see no reason why for example Xubuntu should work in your computer, but not Ubuntu. Not with that amount of RAM, and not with that error. Is it the same version of Xubuntu, 15.10-desktop-amd64, or is it another version?

Are you really sure that the Ubuntu iso file that you check with md5sum is the same as the one you use as source when you create the USB boot drive? Could it be that you have saved iso files in different directories, and you happen to test a good one but use a bad one?

Do you arrive at the grub menu? Have you tried the fourth choice in the grub menu, 'Check disc for defects'?

You should see, when the files are checked, and it should finish with 'Check finished: no errors found'.

---

### Post by RamonB on 2015-11-01
Hi, Sudodus,

(1) I've just tested (again, to be really sure) with Xubuntu 15.10-desktop-amd64 and it worked fine (this test was with an UEFI bootable flash drive).

(2) I'm really sure that the ISO file was the correct. I've downloaded it in Windows 3 times, always deleting the old version. Now, I've just downloaded (for the 1st time) a new copy in my new Ubuntu Gnome Shell. I checked the MD5SUM and all of them were OK. A few momentos ago, I created a new UEFI bootable flash drive with this Ubuntu and another one with MKUSB in my Gnome and the same error occurred.

(3) Yes, I arrive at the grub menu. I checked the disc for defects and no errors were reported. When I choose to try Ubuntu without installing, it starts to run and after some seconds with a black screen the typical Unity colour and the word "Ubuntu" appear very quickly (2 seconds or less) then it turns black again and this error message shows up. 

So, for awhile I'm going with Gnome Shell until the next LTS release or until new suggestions about this problem.

Thank you.

---

### Post by sudodus on 2015-11-01
You are really trying, and it seems to me, that you are doing things correctly. Yet standard Ubuntu does not work for you. I'm not sure, but it seems to try with some other driver than Gnome Shell and Xubuntu.

Have you tried yet with some boot option? Try several of them, you can start with nomodeset. See the following link, that explains how to use boot options (live). You should focus on the instructions for grub, but it is worth reading the other links too.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by RamonB on 2015-11-03
Hi, Sudodus,

My problem is really awkward. I've tested also with Kubuntu, Ubuntu Mate, Gnome Shell and Xubuntu. All of them worked. Only the Desktop flavor didn't work.

I looked at your link "Boot options" but I'm not a Linux specialist (many years ago, I used to be an IT professional but from the Jurassic era :)) ...). So, I've decided for an indirect solution: I installed the 15.04, updated everything and without configuring it to "my way", I updated to 15.10. Now everything is alright, working fine.

Thank you very much for your advice (and also thanks to other people that tried to help me).

---

### Post by sudodus on 2015-11-03
You are welcome :-)

I'm glad you found a way to get what you want. Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by ray-worner on 2016-03-25
> **oldfred said:**
> Another alternative if you want UEFI only.

 Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode, you must choose in UEFI boot tab menu the UEFI:flashdrive entry. Various UEFI may show it differently, but with UEFI only it should be only choice.

Also see details in link in my signature below.


Thank you Oldfred, I tried so many options that did not work, lots of initial promise but the system would not boot past a Grub> prompt. The instruction to use 7-zip was exactly what was required! It worked a charm, thank you for getting rid of my endless headaches in installing Linux Mint while I learn about UEFI.

---

