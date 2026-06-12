---
title: "Cannot boot to Ubuntu?"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by Andrew_Paulus on 2013-10-14
Hello,

A couple months ago, I downloaded Ubuntu v12.04 and I made it duel-boot with Windows 8. I have Windows 8 to boot automatically, and I would have to press F12 to go to Ubuntu (I wanted it that way). It worked fine and I used Ubuntu for a few days. For a couple months, I stopped using Ununtu completely and now I want to use it again.... the thing is that when I try to boot to Ubuntu, a black page pops up saying: 

"GRU GRUB version 1.99-21ubuntu3.9 / Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else / TAB lists possible device or file completions. / grab> _ "

I tried pressing TAB and entered a few random selections like "Linux" and "Boot" but it did nothing.

On Windows 8, I still can see the 25GB I used for Ubuntu. It still says "unallocated".

So what do I do now? I have two options on my BIOS to boot up Ubuntu -- they look identical (I think it is called the BIOS.... I am talking about the page that comes up when I press F12 when I turn my laptop on). When I click the top one, it brings me to the black page, when I click the bottom one, it just boots to Windows 8 even though it is labeled Ubuntu (followed by numbers and letters).

Thanks a lot. Any help is much appreciated.

---

### Post by UltimateCat on 2013-10-15
Hi: ;)

 Since you set Windows 8 to boot automatically:-
It sounds like you don't have the GNU GRUB Menu !? Or am I wrong and you have a black screen with just a prompt?

When you boot up your computer do you have the choice to use the arrow keys to either choose to boot to Windows or Ubuntu?

>  It still says "unallocated".

Unallocated means that (that space) is not partitioned. Did you create a "ext4 journaling file system" partition for Ubuntu and create a "swap" partition as well?
So you would have to create a partiton from that "unallocated" space.


To be sure what is going on with your system you may want to use a Live Linux CD (the one you have with Ubuntu on it should work) and post the output of:
AS ROOT
```
fdisk -l

```\\
Small letter L:-

---

### Post by Elfy on 2013-10-15
*Thread moved to **Installation & Upgrades**.*

not sure why this was in other o/s with a pclinuxos prefix

---

### Post by oldfred on 2013-10-15
Windows will not see Linux partitions, so that is normal.

May be best to see details. You can run this from your live installer flash drive or DVD or download a new CD version repair disk.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Andrew_Paulus on 2013-10-15
@UltimateCat

Thanks for reply.

Anyways, yes, it is a black screen with a prompt. I do have to use the keys to choose whether to boot to Windows 8 and Ubuntu but ONLY when I click F12 when I first power on my laptop. And yes, I did create the swap partition.

---

### Post by UltimateCat on 2013-10-16
Your Welcome: Andrew_Paulus
It's my pleasure to assist you and others here in the forum.

> Anyways, yes, it is a black screen with a prompt.


In that case you can try typing:
```
starx

```
At the prompt and see if that boots you into Ubuntu.
If not, try:
```
Ctrl+Alt+F1

```
And that should give you a way to log in (in commandline mode)
If you are able to log in and still have a black screen with white letters and your in console mode than try: **"startx"**

Another way to boot from a prompt is to know what the output of "ls boot" is. That's usually the boot (grub) partition.
```
ls/boot 

```
If you can get to your /boot/grub/grub.cfg file that would reveal some good infornation too. 

If none of that works than it could very well be that you need Boot Repair. ( A part of Grub or your Master Boot Record needing repair)
Post the link to the BootInfo report that this creates. Is part of Boot-Repair: that our Moderator oldfred advised-;)

---

### Post by BlinkinCat on 2013-10-16
Hi,

I believe the command UltimateCat meant to relay was -

```

startx

```

Cheers - :)

---

### Post by Andrew_Paulus on 2013-10-16
I tried the following commands and nothing happened each time (other than it saying "Unknown command"): starx, startx, ls/boot, lsboot, ls boot, and I tried Ctrl+Alt+F1....

What now? :(

---

### Post by Bashing-om on 2013-10-16
Andrew_Paulus; Hi !

We are trying to find out where you are in the boot process.
When you are at that prompt, what returns from the simple command:
```

ls

```
That return will give us the indication of  where you are in that process. Whether grub has loaded and if you have got past grub.

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by UltimateCat on 2013-10-16
> **Andrew_Paulus said:**
> I tried the following commands and nothing happened each time (other than it saying "Unknown command"): starx, startx, ls/boot, lsboot, ls boot, and I tried Ctrl+Alt+F1....

What now? :(

Try:
```
ls

```
by it's self and see if it gives you any output. Post that output here.
If that only gives you "unknow command" than I am suspicious that your boot partition is missing.
If indeed your boot partition is missing than you will have to re-install Grub to the Master Boot Record.

ls/boot is for to see what the kernel and intrd files are.
Than you can manually boot with the linux intrd commands.
Once we find where "/boot" is than you can boot with something like ([B]this is just an example)
linux (hd?, gpt?) /boot/<name of kernel> root =dev?[/B]

Can you get the output of the command with a Live CD?
It would really help if you can. This way we can see all the partitions on the computer to determine what you have and what is missing.
```
fdisk -l  (small letter L) 

```

---

### Post by UltimateCat on 2013-10-16
Thanks, [**[COLOR=#000000]BlinkinCat-[/COLOR]**O:)]("http://ubuntuforums.org/member.php?u=1392276")

---

### Post by UltimateCat on 2013-10-16
When you installed Ubuntu Andrew; did you by chance have to use gpt partitioning because you have a drive 2.2 TB (hard drive) or larger?
The second link is a picture that I found so you can look at it of what the ls command can provide you with.
This is just an example but in that picture you can see the hard drives, partitions and the kernel that is being used.

[URL="http://www.rodsbooks.com/efi-bootloaders/grub2.html"]http://www.rodsbooks.com/efi-bootloaders/grub2.html

[http://s1052.photobucket.com/user/Ultimatecat/media/lsoutput.png.html](http://s1052.photobucket.com/user/Ultimatecat/media/lsoutput.png.html)

[/URL]

---

### Post by Andrew_Paulus on 2013-10-17
Nope, my HHD is only 750GB. I made a partition with only ~25GB.

Also, when I entered 'ls', this came up:

"(hd0) (hd0, gpt6) (hd0, gpt5) (hd0, gpt4) (hd0, gpt3) (hd0, gpt2) (hd0, gpt1) (hd1) (hd1, gpt3) (hd1, gpt2) (hd1, gpt1) (cd0)"

---

### Post by Andrew_Paulus on 2013-10-17
Hello, I went back to the black screen and typed in 'ls'. Once I hit enter, the following line came up:

"(hd0) (hd0, gpt6) (hd0, gpt5) (hd0, gpt4) (hd0, gpt3) (hd0, gpt2) (hd0, gpt1) (hd1) (hd1, gpt3) (hd1, gpt2) (hd1, gpt1) (cd0)"

---

### Post by Bashing-om on 2013-10-17
Andrew_Paulus; Hey,

Good deal, you are booting to the grub prompt, and grub can not find the final stage of the boot code.
I have limited experience with Windows8 and UEFI booting and will bow out and let those with the experience advise you further.
A number of options to effect the repair exist.

[INDENT][INDENT]I sometimes have no need to know
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-17
That still is grub.

If you have installed then it may be best to run this. You are showing two gpt partitioned drives. Is this an Ultrabook with a small SSD? Those often use Intel SRT which has RAID and grub does not install from a Desktop installer. Actually you do not want a RAID install of grub anyway as that may interfere with the SRT.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Andrew_Paulus on 2013-10-17
I really appreciate your time for helping me solve this issue. Thanks a lot.

And no, I have a regular laptop but it only has 32GB of SSD. I have never used it and it says it has 19.5GB out of 19.6GB of space left, which confuses me because when I bought my laptop it was 32GB.

Can I just completely delete Ubuntu off of my laptop and start again from scratch? I feel that would be easier. If it would be, how would I go about that and just completely remove all of Ubuntu from my hard drive and taking it off of my BIOS?

Thanks again.

---

### Post by oldfred on 2013-10-17
If you did an auto install, it allocated part of it to swap?

You can just reinstall. Or use gparted from live installer to delete current partitions.

---

### Post by UltimateCat on 2013-10-18
Looking at the output like Oldfred said (there are 2 gpt partitioned drives) do you know which one is your boot partition? 
It's hard to tell which is your boot partition--

Either it's (hdo,gpt1) or it could be (hd1,gpt1) ?
This command should show you which partition is your /boot:
[B]ls/boot

What version of the kernel are you using?
To find out you can run: uname -a
It will look something like this:
> Linux ultimatecat-MS-7501 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


[/B]
You could just reinstall Ubuntu but you would have to delete the right partitions. Use G-parted like Oldfred said.
Without seeing the output of "fdisk -l" I couldn't tell you the correct partitions to delete -

---

### Post by UltimateCat on 2013-10-18
In post #5 OP mentioned that he created a swap partition-;)

---

### Post by Andrew_Paulus on 2013-10-18
Here is a screen shot I took on Windows of my partitions. Can I just delete my Ubuntu partition and call it quits for now? Will that disk space just be added to my partition with Windows?

[IMG]http://oi42.tinypic.com/oupb28.jpg[/IMG]

---

### Post by UltimateCat on 2013-10-18
> Can I just delete my Ubuntu partition and call it quits for now? 

Yes-

> Will  that disk space just be added to my partition with Windows?

No-
It will just be free space.  That's what you can use in the future to create a partition for Linux or whatever you wish.

The highlighted blocks that you mentioned that you don't know what they are; from left to right;  is:
```
the 500 MB Healthy (EFI System) This is the Extensible Firmware Interface Partition
that your Windows 8 uses to funtion (files that are required to be launched)

```

```
the 40 MB partition
Healthy Partition is associated with your Windows OS 

```

```
the 500 MB
Healthy Recovery is your Windows 8 Recovery Partition to recover your Windows 8 should if crash.

```

```
this 300 MB Healthy Recovery Partition
If I had to guess is your Recovery Media that you can burn to several CD's

```

And the 7.47 GB Healthy Recovery Partition- I don't know what that is- Sorry

You should consider burning your Recovery Media to DVD/CD.

---

### Post by Dimarchi on 2013-10-19
This is my experience with 13.10, with similar symptoms. This may help, or not at all.

I had both Windows 7 Pro 64-bit and 13.04 64-bit installed. My motherboard has the following modes for boot: Legacy (that is, BIOS), EFI, or try both. I had set it for both, and by default the computer booted to Ubuntu. In order to access Windows I had to interrupt booting and select the disk to boot from. During the 13.04 installation the installer could not make any sense of the operating systems and I never could get to the menu where I could select which OS to start. Inconvenient, really.

Time for installing 13.10! I hoped that the mess would be sorted out by now. A clean installation, custom partitioning (Windows has its own drive, Ubuntu likewise). Install grub to EFI partition. Proceed with the rest. Oh, could not install grub. Restarting...The same process but install grub to Ubuntu drive. Reboot. End up with grub prompt. Eh...

After surfing this forum and reading about these install problems, in the end being not that much wiser, I decided to switch my boot mode to EFI. I tested that I could still boot to Windows, at least. Another try at installation, with grub installed to Ubuntu drive. This time it worked. And not only that, I got the working OS switch menu back.

In short, check out your computer's BIOS/UEFI/EFI settings. It may help.

---

### Post by oldfred on 2013-10-19
Because your second drive is smaller is it an SSD using Intel SRT or similar technology. Ultrabooks use that. The Intel SRT uses RAID (somehow) and that confuses grub on where to install. Normally with RAID grub is to install inside the root of the RAID, but the desktop installer does not have RAID drivers and it is not standard RAID. Or you would not want grub installed inside it anyway. Most turn off SRT & remove RAID meta-data and then grub installs just fine. And reimplementing SRT restores it.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by Andrew_Paulus on 2013-10-19
So then how do I completely remove what is on my Ubuntu partition? Do I do it straight from Windows 8?

---

### Post by oldfred on 2013-10-19
Have you run Boot-Repair?And its rename function?
If not you should just be able to go into UEFI menu and directly boot Windows.

---

### Post by Muhammad_Mudassir on 2013-10-19
dear i think u will have to repair your boot. for which you have to install boot repair[URL="https://help.ubuntu.com/community/Boot-Info"]

https://help.ubuntu.com/community/Boot-Info[/URL]

---

