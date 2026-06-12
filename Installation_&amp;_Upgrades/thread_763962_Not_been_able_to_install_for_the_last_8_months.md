---
title: "Not been able to install for the last 8 months"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by svamppi on 2008-04-23
I bought a brand new desktop PC about 8 months ago. I bought it with Vista and thought about dual-booting with Ubuntu. I already had trouble with 7.10 (I can't remember if I tried 7.04 before that as well) but didn't have time to worry about it too much then.

Recently I've really wanted to be able to install Ubuntu on my PC so I tried again, first with 8.04 beta. The Live CDs usually boot fine. But the install process has not worked a single time. Except for the parallels workstation virtual installation of Ubuntu I had up until I re-installed Vista and then was not able to get parallels to run at a non-widescreen resolution with Ubuntu.

When installing from the Live CD I always get the dreaded errno 5 eventually. Which tells me there is something wrong with the disc, the disc reader or the hard drive. I've burned many discs already. Always checking first the md5 and then running the CD selfchecking software. But even the times when both of them succeed the installation craps out with errno 5. I tried installing from an external USB DVD writer but it seemed to give me errno 5 at the same point in the installation. So I figured it was my hard drive that had a problem. So I took it back to the shop where I bought my PC. Waited for three weeks. Got a new one today and tried installing the 8.04 RC. First checked md5 as usual. Then CD selfcheck. No problems. Live CD runs fine. But when installing... yes errno 5. So I tried the alternate install CD. The md5 was fine. However the cd selfcheck failed on my internal disc reader. But it succeeded on my USB DVD writer. So I tried installing from that. Naturally the install fails. But the alternate install CD does not seem to report the problem as errno 5 but actually mentions the file that it thinks is corrupt. Now I'm not sure but I think it failed on different files the two times I tried installing it. Once with both of my SATA 500 GB WD drives in. And once with only one of them inserted.

Well no installation succeeded for 8 months. Waited for my hard drive for three weeks. This is driving me nuts. What hardware problems could be causing it when I've tried two different hard drives. Two different CD readers. Many different CDs...

---

### Post by dstew on 2008-04-24
Your description suggests you are having trouble with your CD's. I don't think there is any problem with your system or your hard drive.

Burning an image to a CD is very taxing for some hardware. The image has to have every single bit readable in order to work properly. The fact that the alternate install CD failed to check in one reader, but checked OK in another, suggests that it has some bits that are borderline readable. The error you were getting on the Live CD is probably something else, maybe a hardware driver issue.

I suggest you try again with the Alternate Install CD. Use good-quality CD-R media, not CD-RW, and burn the image at a slow speed, 4x at most. Do not try to burn at a higher speed. Then, check the CD integrity in the same drive you burned it in. If it checks out OK, install from that drive. If you get errors, even though the CD checked out OK, try to install Ubuntu on a different computer using the same disk. If it can install OK on another computer, then it must be some kind of hardware-driver issue on your first computer.

---

### Post by svamppi on 2008-04-24
Hmm, maybe I forgot to mention it. But earlier when I tried installing 8.04 beta live CD burned with my internal DVD writer it gave me errno 5. But installing on my older P3 600MHz worked just fine. So I actually think these CDs do work (and yes I do burn them at the slowest speed, and yes I do not use CD-RW). And also I've tried maybe 4 or 5 different burned CDs already with no luck. Anyway if the CD checks out with the selfcheck it shouldn't report the input/output error when you install from the same reader?

I'm thinking about trying another distro to see if they also have problems or if it's just ubuntu for some weird reason. I was able to re-install vista from my internal reader a while ago. So that seems to indicate that it should work.

---

### Post by dstew on 2008-04-24
It seems that the Live CD is OK, since the same disk installs on another computer. It must be that the Live CD system is having trouble with your hardware. You can try to get it to work using kernel parameters. You enter these at the end of the kernel line, and you get to that by pressing F6 at the opening menu. There are lots of kernel parameters, and without going through your kernel messages to try to figure out what the problem is, you can try **noapic nolapic acpi=off**.

Usually, when the Live CD has hardware trouble, the Alternate Install CD will work. From your first post, it seemed the Alternate Install CD you made might have some burn issues. Have you tried that Alternate Install CD on another computer too, or just the Live CD?

---

### Post by svamppi on 2008-04-27
Had some time to try some more stuff today:

Took the old DVD-reader from my old pc and put it in the new PC and ran CD integrity check: FAIL

Put the old DVD-reader with the same CD in it back in the old PC and ran integrity check: SUCCESS

Tried using the IDE cable from my old PC also with the old reader in my new PC. Then it immediately fails on the integrity check. So now I've tried many different CDs, 3 different readers (old internal DVD-reader, new internal DVD-writer, not as new but not old external USB DVD-writer) and two different IDE cables.

What's next? Is it the motherboard's fault? Another interesting thing is that it doesn't seem to fail on the same file every time. So it seems it might work fine for a while then suddenly go down the ditch.

---

### Post by svamppi on 2008-04-27
Almost there now. After a long tricky procedure I managed to update my bios. At first the install didn't work. Then I tried it again with the noapic nolapic and acpi=off flags. The install went on for a while. Except the end failed. Installing grub to /target/. now I guess I just need to manually install grub to my second hard drive (to which I installed ubuntu) and then I would be able to use some crappy boot loader for vista on my first hard drive that would either load vista right away or load the grub from hard drive 2.

But I am having trouble. I booted up my live CD. Went into a terminal and started trying various commands I could find in the ubuntu wiki and so on. sudo grub, find <press tab> no partitions show up.
Tried sudo grub-install /dev/sdb but I get:
Could not find device for /boot: Not found or not a block device

---

### Post by dstew on 2008-04-27
> What's next? Is it the motherboard's fault?Probably the motherboard/BIOS/chipset is having some trouble handling the DVD drive interface.> The install went on for a while. Except the end failed. Installing grub to /target/. now I guess I just need to manually install grubI think is is more serious than that. Installing grub to /target/ is referring to putting the initial grub package onto the hard disk I think, and not to what we usually think of as installing grub as a boot loader. You probably have an incomplete installation on that hard disk. When you boot the live CD, do you see on the desktop an icon for the second hard disk, or for the hard disk Ubuntu partition? If so, you can look in there to see if the /boot/grub directory is present. If you don't see a disk icon on the desktop, open a terminal and enter```
sudo fdisk -l
```Post the result to the forum.

---

### Post by svamppi on 2008-04-27
I was able to mount the sdb1 that I unsuccessfully tried installing ubuntu to. Seemed to contain quite a lot of files but /boot/grub only had one file that I can't remember what it was called right. Maybe something with scheme in it.

It seems I gotta study up on grub a bit. Any hints what I should do next?

---

### Post by svamppi on 2008-04-27
Ok now I booted up the Live CD and here's the output of fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00a8efff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15936   128000000    7  HPFS/NTFS
/dev/sda2           15936       60802   360384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052794

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   83  Linux
/dev/sdb2            6080       24315   146480670   83  Linux
/dev/sdb3           24316       24801     3903795    5  Extended
/dev/sdb4           24802       60801   289170000    b  W95 FAT32
/dev/sdb5           24316       24801     3903763+  82  Linux swap / Solaris

```

So I just set up this easybcd software in vista that should hopefully let me boot grub from /dev/sdb1 Exactly what needs to be in /boot/grub on that partition?

---

### Post by dstew on 2008-04-27
> Exactly what needs to be in /boot/grub on that partition?I don't have any direct experience with easybcd, but I think it chainloads grub. To chainload grub, you need to install the boot loader into the partition, instead of the MBR, and you need to have a menu.lst file in /boot/grub to boot the linux kernel. However, to install grub, there first needs to be a stage2 file in the /boot/grub directory. If you don't find one there, I am not sure you can continue. You might also need to have stage1, and the stage1.5 files also. So, I think your Ubuntu system is at present mis-installed.

Anyway, if you want to try to install grub into the Ubuntu partition, you can boot a Live CD, open a terminal, and get a grub command line by entering grub. On the grub command line, enter```
root (hd1,0)
setup (hd1,0)
quit
```However, with an empty /boot/grub directory, this won't help you boot your system. If your /boot/grub directory is empty after an installation, then the installation failed. You should try to install again. Maybe try the Alternate Install CD.

---

### Post by svamppi on 2008-04-28
I did use the alternate install CD already. Is there no other way to get the stage1 - 2 boot files to the hard drive than to run the installer? And why would everything finally proceed smoothly up to that point and then finally installing grub breaks? Does installing grub require some other hard drive operations than the installation of the other files?

---

### Post by dstew on 2008-04-28
There is nothing special about the grub package, it is just like the others. I think you are having hardware problems with your DVD drive, so installation is dodgy. [Here]("http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB") is how to install the grub package from a tarball. If you can boot your Ubuntu partition, using the grub command line and the root, kernel, initrd and boot commands, then you could install grub using the synaptic package manager.

---

### Post by svamppi on 2008-04-28
Ok. So I just put in my alternate install CD again. Tried the "rescue a broken system", went to a shell in /dev/sdb1 and ran sudo apt-get install grub. It seemed to run fine but there is no grub dir in /boot now.

Aha I noticed something funny when trying to run sudo grub-install /dev/sdb1 in the rescue shell. It says Probing devices to guess BIOS drives. This may take a long time.
/dev/disk/by-uuid/../../sdb1 does not have any corresponding BIOS drive.
Is this because I'm trying to install grub to a "non-main" SATA drive or something?

---

### Post by dstew on 2008-04-28
Did you try the "Reinstall GRUB boot loader" from the rescue mode menu? It might work better than the grub-install shell command. The shell command is apparently confused by the BIOS and operating system mappings. These things can be corrected using grub **device** or **map** statements. But try the reinstall menu command first. If you still want to chainload Ubuntu using easybcd, you need to pick (hd1,0) as the "Device for boot loader installation".

---

### Post by svamppi on 2008-04-28
I'm getting so f**king annoyed now. I feel like I've ran the installer a hundred times now. I just tried booting the alternate install CD with noapic nolapic acpi=off on the rescue a broken system option.

Tried running a shell in /dev/sdb1 but it didnt work. Even though i think it did work on another CD or something. I cant keep track of all the different ways it keeps failing anymore...


:mad: Who to blame? Asians for making shitty hardware?

---

### Post by dstew on 2008-04-28
What motherboard do you have? Vista works fine, I assume. Maybe it is the DVD drive interface, or the second hard disk interface, or both.

There is also a way to install over the internet, without using a CD or DVD drive. It is called [unetbootin]("http://unetbootin.sourceforge.net/"). You install it in Windows, and when you re-boot it gives you the option of installing. After you are done, the unetbootin installer removes itself (supposedly -- you can probably find cases where after this the Windows OS was not bootable). You can also use [Wubi]("http://wubi-installer.org/") to install Ubuntu into a Windows file system folder.

---

### Post by svamppi on 2008-04-28
Asus P5K.
Isn't there some kind of hardware test live CD that could try all features that should be expected of the motherboard or something and report if something fails for it. Well I guess not everything can be tested but, anything that can be done would be helpful. I'm really kind of annoyed that a computer bought less than a year ago can have these kinds of problems. Shouldn't these motherboard interfaces and stuff be standardized?

---

### Post by svamppi on 2008-04-28
Asus P5K.
Isn't there some kind of hardware test live CD that could try all features that should be expected of the motherboard or something and report if something fails for it. Well I guess not everything can be tested but, anything that can be done would be helpful. I'm really kind of annoyed that a computer bought less than a year ago can have these kinds of problems. Shouldn't these motherboard interfaces and stuff be standardized?

Bah, didn't mean to double post and even though the edit button says edit/delete I can't figure out how to delete it...

---

### Post by svamppi on 2008-04-28
Here's another interesting/weird thing. I load the alternate install CD, chose CD integrity check. It succeeds. The PC reboots loading the CD menu again. Now I chose install. Edit all the options for the hundredth time again. Then it fails with a corrupt file during install base system. So then I get sent to the long menu where I can chose to retry any step of the installation. I chose CD integrity from here. And to my surprise (or not) this time it fails on the same file it just said was corrupt when installing base system. So not fail when running cd check from the boot menu. But fail when running it from the menu inside the installer. What gives?

As I was writing this post I tried running the CD integrity check again from the boot menu... but this time it failed the md5 verification on a different file than the one that the installer failed on just a minute before...

Also here are some funny bios options (and their possible values) that might be related to all of this ****:
ACPI Version: Disabled/Enabled, #Additional tables as per ACPI 2.0 specs
ACPI APIC Support: Disabled/Enabled #Include ACPI APIC table pointer to RSDT pointer list
SATA Config: Disabled/Compatible/Enhanced
J-Micron eSATA/PATA Controller: Enabled/Disabled
Controller mode RAID/IDE/AHCI

---

### Post by dstew on 2008-04-28
> I'm really kind of annoyed that a computer bought less than a year ago can have these kinds of problems. Shouldn't these motherboard interfaces and stuff be standardized?Actually, the newer the hardware, the more likely you are to have trouble with Ubuntu. The hardware manufacturers are in league with Microsoft, and they work closely together to make sure their hardware works with Windows. The manufacturers do not pay much attention to Linux, so sometime Linux developers have to write drivers and other software using reverse engineering and educated guesswork. This takes time. You often see that older hardware works better with Linux for this reason.

I have seen some [other threads]("http://ubuntuforums.org/showthread.php?t=607664") regarding this motherboard. One person said he could not get the SATA drives to work right unless there was also an IDE drive plugged in. Somebody else recommended BIOS updates.

EDIT: I see your new post about your BIOS settings. You might try to change some of these, one-by-one, and see if it works better. But I don't have any specific advice for you.

---

### Post by svamppi on 2008-04-28
Yep, already tried the BIOS update. Man this is really annoying. So does it seem like the motherboard is crap? And you wouldn't expect asus to be that linux hostile. The asus eee pc was only available with linux for a while when it came out.

Also I keep trying again with noapic nolapic acpi=off anytime it fails just to see if that would help. But what are the disadvantages to running the kernel during the install with those flags? Surely there must be some drawback or the installer would go with the most compatible options by default?

---

### Post by dstew on 2008-04-28
There is very little disadvantage with those kernel options during the installation phase. They disable the Advanced Programmable Interrupt Controller and the Advanced Configuration and Power Interface. With the APIC disabled, the interrupts fall back to the older PIC, and there is some slowdown in some situations with lots of interrupts, like gaming, or working lots of hardware, but it still will work. I haven't really figured out all that the ACPI does, but I have read that it is not well-implemented in many motherboards (see the [Wikipedia article]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface"), Criticisms). I think it gives the software hooks to power-saving features. Probably it is not very important unless you have a notebook.

None of the kernel parameters used to boot the installation CD will have any effect on the installed system. You can use the parameters on the installed system (if you ever get one working) by adding them to the kernel line in /boot/grub/menu.lst

---

### Post by svamppi on 2008-04-29
So I guess I'm back to the earlier question. Is it possible to find out exactly which part is failing and help somebody in finding out exactly why it's failing and then finally somebody could fix the code that goes wrong? If there was a set of unit tests for the motherboard or the HD or DVD interface that you could run from a live cd or something. But it seems a bit hopeless when the file that fails the integrity check seems to be different every time.

---

### Post by dstew on 2008-04-29
I don't think it is a plain old hardware failure, but a failure of the Live CD or Alternate Install CD software to interact well with the hardware. My guess is that any hardware testing would show it is OK. And, Windows works fine on it, correct? So it must be some software issue with the Live CD/Alternate Install CD.

Consider again using unetbootin to install. You could also consider doing a minimal install using floppies if you have a floppy drive. You could install a [minimal Debian system]("http://www.debian.org/distrib/netinst"), and use that to get the rest of Ubuntu from the internet. At least that way you would avoid using the troublesome DVD-ROM interface.

---

### Post by svamppi on 2008-04-29
Ok, I just gave unetbootin a shot, but it failed by not being able to recognise the "CD drive". Where would I file a bug for this? I don't really know what's failing and why.

---

### Post by dstew on 2008-04-29
Did you successfully install unetbootin? That is, you downloaded the file in Windows, and ran it from there, rebooted, and got the menu with the choice to boot Windows or do the Ubuntu install? Did it fail after that? I did not  think the CD was involved at all with a unetbootin install, but I could be wrong.

---

### Post by svamppi on 2008-04-29
Yeah, but I tried to use the option of installing it from a pre-downloaded .iso. Not sure if it would make any difference if I actually specifyed a url or something. It might still "emulate" the CD like it seemed to try to do when I used it.
Now where would be a good place to report my installer bug?

---

### Post by dstew on 2008-04-30
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by svamppi on 2008-08-25
All right, if anybody else is having similar problems as the one I described in this thread. The whole problem was easily solved by buying a cheap SATA reader to replace my PATA reader and disable my jmicron PATA controller in the bios...

I can't believe it took me a whole year to get Ubuntu on this PC because of this stupid shitty jmicron controller.

Here are the symptoms I was having in the syslog with the jmicron controller enabled:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871)

---

