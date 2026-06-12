---
title: "Serious issue after updating from  3.5.0-40-generic"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by whitesmith on 2013-12-05
The last version of Ubuntu I am able to run is  3.5.0-40-generic. Everything else produces a kernel panic or an empty (yuppers!) Debian boot screen. I'm sure the reason is that in my zeal to keep a clean system my fingers outran my brain, removing some critical OS component. I hope some kind, thoughtful person can explain how to get my system up to date so that it will run the version now offered by Update Manager. Modules need to be added and others wiped, but I have no idea which ones. I'm running 64-bit AMD on a 100%-pure Linux box. System details:

											Enclosure:		Standard 4U rack mount with 5 fans.
										        Motherboard:	ASUS P9X79
											Processor:		Intel Core i7-3820 CPU @ 3.60GHz with 4 actual cores & 4 virtual (FSB=1200.000 MHz - L2 cache=10240 KB)
											Cooling:		Corsair L60 water-cooled manifold
											RAM:			4 DDR sticks, each 8 GB. Total=32 GB.
											SSD:			OCZ Vertex 3 (Sata 3). Capacity=240 GB + 2 1-TB conventional HDDs.
											HDs:			Two 1 TB Hitachi 3.5 inch drives. 

Getting my system to the current rev level is important to me, so I would be sincerely grateful to anyone who responds. Thank you very much in advance.

---

### Post by jdeca57 on 2013-12-05
I'm also using 12.04 and my kernel is something like 3.2 so either I did something wrong or you're at 13.04 (since I think 13.10 has an higher kernel version) That said, and if you don't trust the GUI (why don't you follow what it proposes?) , what happens with (sudo)
apt-get update
apt-get upgrade
At least you'll get some error messages.

---

### Post by whitesmith on 2013-12-05
Well I do trust the GUI: Update Manager is what I update-upgraded with. I am definitely, absolutely on 12.04 LTS. What I need is a way to restore deleted modules so that the latest kernel will work. Any suggestions? 3.5.0-40-generic is OK, but I want to be current. Bear in mind that I'm 64-bit. Thanks.

---

### Post by jdeca57 on 2013-12-05
Well I'm also on 64-bit but since the start and now I see [http://askubuntu.com/questions/279391/quantal-backported-kernel-in-12-04-2-whats-going-on-there/279392#279392](http://askubuntu.com/questions/279391/quantal-backported-kernel-in-12-04-2-whats-going-on-there/279392#279392) that 3.5 is indeed the latest version.
So sorry, my mistake for noticing my kernel stays at 3.2

---

### Post by oldfred on 2013-12-06
I do not think Ubuntu used to update kernels, but now each point release of 12.04 changes to a newer kernel. I am still at 3.2, but could add the enablement stack to update.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)
And when 12.04.4 comes out in Jan it will be another kernel & grub update.

Are you booting with BIOS or UEFI? Your system looks like it could be either.
Are you able to boot recovery mode? To command line or with older kernel?

Have you tried Boot-Repair? May be best to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by whitesmith on 2013-12-08
Results of running Boot Repair posted at [http://paste.ubuntu.com/6542113/](http://paste.ubuntu.com/6542113/)

After Boot Repair system still will not boot current release of OS (hangs on Debian selection page). Going into Recovery Mode produces a kernel panic. My system flashes something about UEFI BIOS at boot time, so my previous denial of UEFI may have been incorrect.

---

### Post by necromonger on 2013-12-08
I found out the hard way UPDATE or UPGRADE at your own risk.this forum is loaded with problems when you update or upgrade.

---

### Post by oldfred on 2013-12-08
It looks like Boot-Repair ran its auto repair where it installs grub to every MBR. With multiple drives I do not like that as I have different installs on every drive and only want that install's boot loader in the MBR of that drive.
You can do that by unchecking auto repair and in advanced select one system and one drive to install boot loader into.

You are showing a /dev/mapper/nvidia... , are you running "fakeRAID"? Or were you? It only seems to be the one drive.
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Are you booting from the drive that is sda?

---

### Post by whitesmith on 2013-12-09
> **oldfred said:**
> It looks like Boot-Repair ran its auto repair where it installs grub to every MBR. With multiple drives I do not like that as I have different installs on every drive and only want that install's boot loader in the MBR of that drive.
You can do that by unchecking auto repair and in advanced select one system and one drive to install boot loader into.

You are showing a /dev/mapper/nvidia... , are you running "fakeRAID"? Or were you? It only seems to be the one drive.
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Are you booting from the drive that is sda?Before I go further, which could have serious consequences, let me answer your questions to make sure I'm doing it right:

(1) I'm afraid I'm not familiar with the term "fake RAID." If installed, the action was inadvertent. Will ignoring this affect unchecking all but one system and manually repairing that one?
(2) Yes, /boot is on sda1, as can be seen from ```
df: `/root/.gvfs': Permission denied
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       37G  6.8G   29G  20% /
/dev/sdc1      fuseblk   932G  572G  360G  62% /media/Data-SLA360
/dev/sda5      ext4       74G   66G  4.4G  94% /home
/dev/sdb1      ext4      221G  188M  209G   1% /media/HomeAddition
/dev/sdd1      ext3      917G  858G   13G  99% /media/Bkup-CLA332
/dev/sde1      ext4      917G   52G  819G   6% /run/media/me/FreeAgent

```
I ammensely appreciate your help so far.

---

### Post by oldfred on 2013-12-09
But which drive in BIOS is set as default boot drive?

Actually / (root) is on sda1 and you then probably have /boot inside /. I do not suggest a separate /boot partition for most desktops, but RAID, LVM or similar configurations may need a separate /boot partition. Some also make other root folders as separate partitions, but I consider that very advanced and few need it.

Did you or do you still have RAID turned on in BIOS? It should be AHCI or at least LBA or large, not RAID nor IDE for all drives. Some allow setting some one way and others differently.

RAID also leaves meta-data on drives that interferes with grub installs to that drive. Grub sees the meta-data and wants to install in RAID mode. Standard desktop installer does not have RAID drivers, so it does not work.

If really not running RAID and you do not have it on in BIOS.
       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sde
If not sde change to correct drive.

---

### Post by whitesmith on 2013-12-09
> **oldfred said:**
> If really not running RAID and you do not have it on in BIOS.
       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sde
If not sde change to correct drive.

RAID is not turned on. The 1 TB matching drives were once part of a RAID set. Maybe that's where the metadata is coming from. When I run your command, I get ```
no raid disks and with names: "/dev/sde"
```

The exception is sdc, which gave me ```
me@London:~$ sudo dmraid -E -r /dev/sdc
Do you really want to erase "nvidia" ondisk metadata on /dev/sdc ? [y/n] :^C
```I didn't answer before hearing from you. I guess the proper answer is yes, on the assumption that metadata comes from the previous Windows installation the Hitachis were taken from. The primary boot device, according to the BIOS, is sda, the 120 GB OCZ SSD.

---

### Post by oldfred on 2013-12-09
As long as you are not running RAID yes is correct. If two drives were RAID you may need on the other drive or is that the one you already tried?

---

### Post by whitesmith on 2013-12-09
My plan at this point is to Yes the query, and then run Boot Repair manually as you previously suggested -- nothing more. Do you think this is safe?

---

### Post by oldfred on 2013-12-09
Should be.
Of course anytime you start working with major system changes back ups are important. 
With Windows a full image backup, since it can be difficult to reinstall. We have just seen several users with issues where I think they thought the re- install Ubuntu to entire drive meant Windows type "drive" which is a partition where with Linux a drive is a physical drive.

---

### Post by whitesmith on 2013-12-10
Did what I promised but 3.5.44-generic still won't boot -- same symptoms. My recollection is that I was "cleaning house" right before 3.5.41 came out (the first of many kernels that seem to hate my machine). Is there a way to sweep in all the dependencies for the latest version (3.5.44) and give that a shot? I'm at the end of the concrete.

---

### Post by oldfred on 2013-12-10
You can chroot into your system and install the most current kernel and updates.
Boot-Repair has a chroot to totally uninstall grub & grub2 and reinstall grub2. Internet must be working as it has to download new pkg.

       #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

Other examples of chroot.

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by whitesmith on 2013-12-11
Still no joy. I think I'll wait for the forthcoming release (with its shiny new kernel!) and give your many suggestions another try. Thanks a ton for everything. To me, this incident is a perfect example of the inevitability of FOSS gaining traction as time passes. If nothing else, what at first seemed like a tiny problem has proven to be quite a learning experience for me. Cheers and best wishes for the coming year!

---

