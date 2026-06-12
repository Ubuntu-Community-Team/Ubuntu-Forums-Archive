---
title: "Ubuntu + Windows 8.1 on 2 HDDs, one Intel SRT'd"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by jari.begus on 2014-05-24
Hello!
Please forgive me if this has already been posted/answered, but I could not find it.

Now, to my issue:
I would like to dual-boot Ubuntu 14 LTS and Windows 8.1 on two hard drives, the latter OS running with Intel's SRT enabled.
The Ubuntu HDD would be an old 120GB drive, the Windows one a 500GB one with a 60GB SSD.
But I can't get Ubuntu's installer to realize that there is in fact a second OS installed. And I'd rather not risk the data stored on my main 500GB disk. To avoid that, I disconnected the SSD and the main HDD (physically disconnected the SATA cables) and installed Ubuntu as a stand-alone OS. After the installation, I plugged the two back in. (Another thing that happened was that Ubuntu started derping completely and displaying all sorts of visual artifacts on the screen so nothing was readable, but it was still responding, only to be solved by a reboot. I'll make a thread about this one day.)
But the only way to select the OS to boot is by selecting the boot device in the BIOS, which is time-consuming and tedious. Much more work than just pressing up/down and Enter.
So, I formatted the smaller HDD and moved away from Linux for a while. What I unknowingly did with this was that if I disconnected the smaller drive, Windows would refuse to boot (again something I'll one day make a thread about as it's really irritating).

Now, I need Ubuntu again, and I'm really not sure where to begin. I do have a 14.04 amd64 iso on my hard drive, and a USB drive and a bunch of DVDs handy to make it to the installer.
But what after it (or *on* it, even)? Is there even a way to do this or am I doomed to use either SRT+W8.1 or put W8.1 on the SSD to use Ubuntu normally?
And is there a way to do this without both OSs going harlem shake on me?

PC specs, if that provides any details:
GA-H87m-D3H motherboard
Intel i5-4440 CPU
4GB DDR3 1600MHz Crucial Ballistix Sport RAM
Gigabyte GTX660 GPU
LG 23EA63 IPS 1080p display via HDMI to the GPU
Kingston V300 60GB SSD
A Hitachi 500GB 2.5" HDD (meant for laptops, but it was cheap at the time, so I went with it).
A way-old 120GB HHD that I found in an old build of mine

Thanks for any help!
--755

---

### Post by oldfred on 2014-05-24
You need to convert old drive to gpt and install in UEFI boot mode.
If both systems are not in UEFI boot mode you can only boot from UEFI/BIOS menu as UEFI & BIOS/CSM are not compatible and once you start booting or are at grub menu, you cannot change to the other boot mode.

And you want an efi partition on your 120GB drive. Installer may default to install to Windows efi partition, but better to have it on the Ubuntu drive. Only with Something Else will you have option on where to install grub2's boot loader.

If you have fast boot on in Windows Ubuntu will not see Windows. And the Intel SRT uses RAID which often the installer did not see correctly, although I now see some reports that new version does see it, just still not install grub correctly.

I thought Intel SRT just speed up boot. It was/is a Windows requirement to have fast booting and many vendors put small mSATA drives of 16 to 32GB and only used part of that mSata drive for the cache. I have seen users install Ubuntu on the rest of the mSata drive when they have the larger SSD drive.

You could have Windows in 40GB and Ubuntu in 20GB and have both systems work fast. Then have all data on hard drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

See also two drive sub-section in link in my signature.

---

### Post by jari.begus on 2014-05-26
Thanks for the speedy reply (and sorry for mine being so late).

I realized a few moments after posting that my Windows install may not have been UEFI. Didn't take long to fix, but I'll always feel like an idiot for it. xD
Anyways, my installation went relatively smoothly, except for the fact that the installer did again not see Windows, but I went around that and installed on my smaller drive (thanks for the links and tips, helped a ton since this was my first time doing the partitioning manually).

I don't know if I *should* make a new thread of this, so I'm posting my next issue here:
I let the installation run and then, in my face comes what is making me hate Ubuntu. Glitches, but they were laid over the entire screen contrary to my previous installation where it only happened in each window separately.
Here's a shot of that with my phone's camera: [http://db.tt/apO7ouVs](http://db.tt/apO7ouVs)
Even if a single pixel moves on the screen (or is supposed to move), the blocks start jittering all around.
I did try Ctrl+Alt+F4 and closing Unity from there (the glitches were not present on the text console), then Ctrl+Alt+F7 returned me to a logon screen (also without the glitches). But, as the installation was not yet finished, I could not log on no matter what I put in as the username and password.
Should I wait for a new release or try an old one instead? I'm blaming my GPU on the issues, but I need it in Windows so I don't plan to switch cabling and all when I switch to the other OS. I've tried all the different drivers available on my previous install but the glitches always came back -- never like this did last night though. ;-;

---

### Post by oldfred on 2014-05-26
Are you using just the Intel internal video or do you have a Video card?

The nomodeset is primarily for nVidia or AMD until you install the proprietary drivers.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

With Intel you often need one or several of the extra parameters in ubufan1's post.

When users were installing 13.10, and had very new hardware, the beta of 14.04 seemed to work better. Now some systems seem to need a still newer kernel & support software. Intel is updating kernel, support software as well as video driver.
      
 New kernels ppa
xorg-edgers PPA
Oibaf PPA discusion  [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
Linux 3.15 Git kernel from the Ubuntu Mainline Kernel PPA while the Oibaf PPA was also loaded for the Mesa 10.3-devel Git master snapshot and xf86-video-ati 7.3.99 Git.

---

### Post by jari.begus on 2014-05-26
Damn you're quick :P

I am using my video card, yes. The GTX660.
My CPU is of somewhere 2013 (Q3 I think) so I think that shouldn't be an issue with being too old/new, same goes for the motherboard.
(I listed my specs in the OP.)

So I try turning on nomodeset?
And I've already tried the proprietary drivers, they just glitch again.

---

### Post by oldfred on 2014-05-26
I have an older nVidia card and just get a blank screen or flashing underscore or monitor turns off but flash drive is still booting. But with nomodeset I can get into low quality graphics and then install the nVidia proprietary driver.
I typically install the most current but have also installed the experimental. You card is not so new that there should not be any issues with the nVidia drivers in the repository. They are pretty current just not the just released version normally. 

Systems with both Intel internal or nVidia cards may boot with one or the other? Can you set that in BIOS. Many laptops now are automatic or muxless(?).

Your motherboard is UEFI/CSM or compatibility mode with BIOS. So you can install either way, but how you install both Windows & Ubuntu is based on how you boot install media. You should have two entries in UEFI menu for flash drive. And best if both are either UEFI or both BIOS.

If you install more than one of the proprietary drivers over the top of another you have issues. You have to totally purge, remove xorg.cong and start over.

---

### Post by jari.begus on 2014-05-27
Actually, I have my Intel GPU disabled (from the BIOS), plus there's the fact that my monitor is plugged into my NVidia card via HDMI, not into the motherboard back I/O.


If nomodeset is not the driver used, what is it, then? During the installation? I'm guessing it's some kind of open-source thing, but that's as far as I'd go.
And how is it possible to install proprietary drivers before/during install? Or will nomodeset be enough to get me through installation, to reboot, and then switch?

Also, with my last installation, the glitches appeared both on the open-source driver and proprietary drivers, even after a clean install.

I am downloading 13.10 on another machine while I give version 14 one last shot with the tricks you proposed.

Thanks again!

---

### Post by oldfred on 2014-05-27
I have ticked install proprietary drivers, but it has not installed nVidia for me. I have to use nomodeset and then install nVidia either from command line or using System Settings.

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

