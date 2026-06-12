---
title: "Quad Boot OS with separate boot partition"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Mr_JMM on 2012-11-13
Hi, So out of bordom I thought I'd see how to take advantage of having a separate /boot partition using an old laptop for experimentations. I know many will say don't bother but please, let's accept I want one.
Set up so far:

[IMG]http://i1169.photobucket.com/albums/r504/COB76/Screenshotfrom2012-11-13113849-2.png[/IMG]

Whilst I have allocated some partitions for other Linux OS's they're not all installed yet. I tried to install Lubuntu but messed up somewhere to do with how to deal with /boot during install. Lubuntu grub wouldn't see Ubuntu. Recreated /boot using a backup image and now boot into Ubuntu but now grub can't see Lubuntu.

So, question: When I install other OS's, what is the proper way of dealing with the /boot partition? SHould I always mark it as /boot and format it with each install (I did this before and caused errors)?

Sorry for being so long-winded.

Thanks in advance.

---

### Post by Mr_JMM on 2012-11-14
Bump.

Additional: Each time I install a new distro it replaces grub. All other distro's are missing from the grub menu and all attempts to update grub fail.

---

### Post by arpanaut on 2012-11-14
So it appears that each installation is replacing all the files in /boot with it's own.
Thus os-prober is unable to find any other /boot files for other installations.

I presume that the use of a universal /boot directory is not possible for a multiboot system.
I do not know for sure but it seems logical.
There may be other ways to configure this but by default each install would write its own files to /boot.

I know; not much help.

---

### Post by Mr_JMM on 2012-11-14
Odd as from what I've read, a shared boot is ideal when there's multiple distros. I'm guessing there is something I am doing wrong when I install each distro - marking the boot partition and formatting it.

So I guess what I need to know is: Now that I've installed all four OS's, how do I get grub to see the two missing Linux distros? All it see are the newest Linux and Windows Vista.
Updating grub via a live CD doesn't work, in that it never picks up the other distros.

Alternatively, I'd like to know how I should install the three linux distros (if I delete them and start again) so that the /boot partition idea works as expected.

Many thanks.

---

### Post by arpanaut on 2012-11-14
I have seen that too but there seems to be issues:
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=%22+shared+%2Fboot%22&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=%22+shared+%2Fboot%22&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

Edit:
If you are formatting the /boot part. on each install, then there are no files related to the previous installs for os-prober to find.
I would think the other installs would be unbootable without their /boot files. there must be a way as I too have seen this advised, but I don't know as I have never tried.

---

### Post by Mr_JMM on 2012-11-14
Thanks for that link. Seems that grub2 may not play nicely with a separate boot.
Also, I see your point about overwriting boot each time. I just figured that grub would find the other distros just as it would if each distro had it's own boot file.

Unless anyone can correct me on the above thoughts I guess I'll either have to learn to edit grub custom files or remove the separate boot. Or go back to grub 1... Dang.

---

### Post by oldfred on 2012-11-14
I have never seen anyone say a shared /boot should work. And several that have posted who tried all failed. The only place now that you do have a shared boot is with UEFI, but that is totally different.

You can have a shared grub partition, but that does not have any system kernel files, just grub. That worked better with grub legacy as you could install grub to a PBR - partition boot sector and chain load each install. I used that with grub legacy and at first did not like grub2 as chain loading did not really work with grub2.

But with grub2 you can have the one install you primarily boot in charge and with a sudo update-grub add in all the other installs. But updates in each install required updates to main install also. Often better to manage other installs yourself and manually edit grub2's 40_custom and turn off os-prober.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by Mr_JMM on 2012-11-14
Hi Oldfred,
Thanks for the info.
It does seem like I'm making hard work for myself, it was just something I saw and thought I'd give it a try.
Could you help me out then with one last thing then so that I can go back to a more standard install? If I installed Ubuntu first but want it to remain the "boss" of grub, can I just update grub from the Ubunti live CD (DVD) after all other distros are installed? alternatively, is there a way I can achieve this during the install of other distros so that they don't take over grub?

Many thanks again.

---

### Post by chuck_theobald on 2012-11-14
Cool idea, I am working on a similar configuration on my home machine, five partitions on a 1 TB disk, five operating systems.

If you are using a common /boot partition among different distro installations, you definitely do not want to reformat it with each install. If you do so, then all previously installed kernel files will be gone.

A problem I can see in trying to implement your scheme is that each distro does not identify these kernel files (vmlinuz, initrd, System.map) uniquely. Note the following naming:
```

RHEL:
config-2.6.18-308.16.1.el5
initrd-2.6.18-308.16.1.el5.img
symvers-2.6.18-308.16.1.el5.gz
System.map-2.6.18-308.16.1.el5
vmlinuz-2.6.18-308.16.1.el5

Mint:
abi-3.2.0-23-generic
config-3.2.0-23-generic
initrd.img-3.2.0-23-generic
System.map-3.2.0-23-generic
vmlinuz-3.2.0-23-generic

Debian:
config-2.6.32-5-amd64
initrd.img-2.6.32-5-amd64
System.map-2.6.32-5-amd64
vmlinuz-2.6.32-5-amd64

```
There is no guarantee that you will not run into naming conflicts between distributions. Analyzing the contents of /boot would be quite a task. Organizing using a directory heirarchy would be the way I would go, but then you are looking at manually maintaining each entry in grub.cfg so that it refers to the correct sub-directory for each distro. But, this would break aptitude (Update Manager for you GUI people) updates to the kernel.

It would seem that each distro assumes that it has exclusive control over /boot.

I admire the idea of having a shared /boot, it is do-able with some effort, though it may be easier to make sure you have a shared grub configuration instead.

---

### Post by Mr_JMM on 2012-11-14
> **chuck_theobald said:**
> Cool idea, I am working on a similar configuration on my home machine, five partitions on a 1 TB disk, five operating systems.
Glad I'm not the only one. I just figure if you want to try out other distros or have a backup version then why not use multiple partitions rather than mess about with VM's.
I personally like to have a duplicate of the main distro for testing, especially upgrades, Lubuntu for when I want a fast OS or run intensive software like Skype on an older system and I like to try out alternatives.

> **chuck_theobald said:**
> There is no guarantee that you will not run into naming conflicts between distributions. Analyzing the contents of /boot would be quite a task. Organizing using a directory heirarchy would be the way I would go, but then you are looking at manually maintaining each entry in grub.cfg so that it refers to the correct sub-directory for each distro. But, this would break aptitude (Update Manager for you GUI people) updates to the kernel.

It would seem that each distro assumes that it has exclusive control over /boot.
I didn't think of that, it's a good point. The more I read about shared boot with grub2 the more I wonder if it's an old idea that no longer serves a purpose / is a usable idea. But then, it is STILL recommended for server distros. But I guess the hassle of maintenance is less of an issue in that environment.

> **chuck_theobald said:**
> I admire the idea of having a shared /boot, it is do-able with some effort, though it may be easier to make sure you have a shared grub configuration instead.
As you say, it is a lot of hassle and I the main reason for trying it, apart from learning for when I set up a server environment was to simply upgrades / installs etc and it seems that this isn't going to be the case. I think I'll undo it all and reinstall the OS's using their own internal boot directory. I'll keep the partition though for future use should things change.
Thanks again for your comments.

---

### Post by oldfred on 2012-11-14
Some installs give a choice on where to install grub2's boot loader. You can then not install, if an option or install to a partition (Ubuntu's only other option). The install to a partition will never be used and is  just to keep your main install's grub2 in the MBR.

If your second install overwrites the MBR but gives the option to boot into Ubuntu your can easily reinstall Ubuntu with this:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

If it gets to the point you need a liveCD to reboot.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Or you can have Boot-Repair, Supergrub or other boot alternatives.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I also install grub2 directly to a flash drive and manually configure a grub.cfg to boot several other drives either MBR, or to a partition.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by Mr_JMM on 2012-11-14
Thanks again.

I seem to have fixed it by leaving Ubuntu using the boot partition and reinstalling the other distros as normal (without assigning a separate boot). Then updated grub from Ubuntu. Used Grub Customiser to change the order and rename them.

Thanks for all your help. Whilst I don't think this achieved everything I set out to do I'll mark this as solved as for now at least, it is the best way I can see of successfully using a separate boot partition.

I have since borked the disk causing errors with gparted but I'll start a new thread on that.

---

