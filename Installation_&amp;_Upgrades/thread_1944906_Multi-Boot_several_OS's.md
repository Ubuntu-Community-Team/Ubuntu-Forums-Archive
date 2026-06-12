---
title: "Multi-Boot several OS's"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by Questionario on 2012-03-22
Hi,

I am trying to install multiple OS's on one drive.
The problem with this is, most of them are ubuntu derivates but partly use different kernels.
One OS would be non-ubuntu (OpenElec-linux)
One would be XBMCBuntu (based on Lubuntu)
One would be 64bit standard Ubuntu
One would be a 32bit ?buntu

I want each of these to keep their kernels.
I tried installing them one after another which works but then I get a huge list of kernels and the option to start each of the ?Buntu's with each of the kernels without much description.

I think the best would be if each of these would be on their own partition and I have a separate boot partition where the boot manager would only boot the partition, that way each ?Buntu system can update their kernels and boot menu's as they like?

How would I go at doing this?

Thanks!

---

### Post by darkod on 2012-03-22
I don't understand. They are on their own partition, or it sounds like it.

Are you talking about a /boot partition that all OSs will use? I don't think you can share a /boot partition easily, so you better let every OS keep it's files in a boot folder on /, as it is.

As for kernels, you can avoid having a large list if you want 4 or even more OSs. You can remove older kernels if you want to, which will shrink the list a bit.

Alternatively, you can use custom entries in 40_custom instead of the standard os-prober and that way for example you can drop the recovery mode entry for every OS and copy just the standard entry in 40_custom.

---

### Post by ajgreeny on 2012-03-22
You want to do what I already do without a problem.

As darkod says let each OS keep its own boot folder in root.  Decide which OS you wish to be your main one, ie the one that provides the grub boot loader files, and if it is one that is already installed boot to it and run the command ```
sudo grub-install /dev/sda
``` assuming sda is the priority boot device.  Niote that the device is just /dev/sda, not sda1 or sda2 etc;  grub needs to be in the MBR of a disk, not a partition.

Now when you install the other OSs use the "Something else" option for manual partitioning and you can then choose to put grub for all the other OSs on each's root partition, not normally what is needed, but as you already have a good working grub, no need to worry.  After eah new OS is installed you will need to boot again to your main OS and run ```
sudo update-grub
``` to add the new ones to the old grub menu system.

Do that for each new OS.  If you want to only have one kernel show for each of the new OSs you need to copy the first menuentry from grub.cfg of each new OS to the custom_40 file in your main OS's /etc/grub.d folder.  In my case this is, for example:-
```
menuentry 'Bodhi 1.3.0, sdb5' --class bodhi --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e24a3854-4c5e-4e47-98ce-d080201a88ab
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e24a3854-4c5e-4e47-98ce-d080201a88ab ro   splash quiet pcie_aspm=force
    initrd    /boot/initrd.img-3.0.0-12-generic
}
```Note that it starts with the word menuentry and finishes with the } on its own line.  Do not change any of the formatting of the paragraph or it will not work, but you can change the kernel info line entry to the OS name, as I show with '**Bodhi 1.3.0, sdb5**' to help you know which OS is which.  Once you have edited that file for all new OSs, run ```
sudo chmod +x /etc/grub.d/40_custom
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```which will make sure that the 40_custom file is executable, the 30_osprober file is no longer executable, and that grub is updated to include the changes.  Every time one of your secondary OSs has a kernel update you will need to re-edit the custom_40 file and run *"sudo update-grub* again.

You can easily check what will show in your grub menu with ```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by Questionario on 2012-03-22
Thanks,
ajgreeny's method sounds like it would work.
 
My preference though would be to have each OS store the boot in the root and create a separate boot partition (this one would have the boot flag) which would then just chainload/redirect booting to the partition I want to boot from.
 
e.g.
I have these boot entries:
Ubuntu 32bit
hd0,2
Ubuntu 64bit
hd0,3
Lubuntu 32bit
hd0,4
Other Linux OS
hd0,5
 
and not even store any kernels on this partition.
 
My guess would be I could disable os-probing by removing the executable flag on each OS, do an update-grub on each so they will only have info about "themselves".
That way I would never need to edit any files when upgrading the kernels.
 
I think this should work, shouldn't it?

---

### Post by ottosykora on 2012-03-22
Interesting, as I am thinking to do something similar in near future, was just given a cheap notebook to try.

Previously, I did such more complex installs with separate partition for the actual bootmanger. From there all is chainloaded without any direct reference to particular kernel.
Therefore the initial menu remains the same all the time and need to be changed only when new os is added or one removed.


In each partition, there is a bootloader, in windows partitions their native one and in linux it is done either with grub legacy or in one case of fedora with grub2.

I have so some 6 or 7 os , grub legacy jumping from mbr to the dedicated partition and from there chainloading all the rest.

But now I am kind of confused after read the grub2 manual number of times.

The problem is, that if there is grub2 detected in the mbr, the grubs installer forbids to install other grub2 into any pbr.
This is not very nice for such experiments, as there is no way to add , the delete and add again some os as long as grub2 is in mbr.

If there is grub legacy in the mbr however, grub2 can be installed where ever apparently. Or at least in my case this does work.

However, in those cases anyway it is needed to replace the grub2 with grub legacy (when installed in pbr) as grub2 in pbr breaks often during upgrades etc.

So my procedure when I set up my multiboot computer was:
install grub legacy to mbr and edit the menu by hand completely.

Install the os in specific partitions, let them install its bootloader into the partition (pbr)

With ubuntu etc I replaced then later the grub2 with grub legacy 

the whole thing is about like this:
w98se, w7, xp, ubuntu, fedora, debian and two 'variable' or temporary os in form of knopix for example.

The grub legacy was installed to its dedicated partition with the aid of the super grub disk.

I am planning try similar with grub2, but it looks as this is not possible with it.


It is dead easy with grub legacy however.


BTW: boot partiton and bootmanager partition are two different things
Boot partition will contain also the contents of a boot folder of a particular os, that means also kernels etc, while bootmanager partition is not associated with any of the installed os on that computer. It works completely on its own and does not interfere with any of the os directly.

---

### Post by oldfred on 2012-03-22
With grub legacy I used chainloading and had a totally separate grub legacy boot partition. Every grub legacy was installed to the partition and I chainloaded everything. At first I did not like grub2 and grub2 did not like installing to a partition as then it converts to blocklists. Blocklists are unreliable as the have to hard code the location of the grub files and if an update moves the file you have to reinstall the grub2 to the PBR to get it to work again.

But grub2's os-prober is one of the best things about grub2, grub legacy often could not even find Windows. Also it still is easy to add custom entries to 40_custom. Ubuntu also has links in / (root) to the most recent kernal so you do not have to update the entry on every kernel update in the other install.

So I do like ajgreeny, turn off os-prober, and put an entry into 40_custom. But I use the links, so I do not boot a specific kernel.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by ajgreeny on 2012-03-22
That's an interesting way to do it oldfred, but does it tell you what the OS actually is if you use that method.

I have ubuntu 10.04 as my main OS but then four other newer versions of the ubuntu family which includes the Bodhi I showed in my last post, so not really in the ubuntu family, and the problem with that is that the grub.cfg in all of the OSs just says "ubuntu with linux <number> and does not discriminate between Kubuntu, Xubuntu, Lubuntu or Bodhi.  Very confusing in the grub menu if you let the system pick up that from the menuentry in grub.cfg.

I prefer my way!  it means my grub menu contains
```
'Ubuntu, with Linux 2.6.35-32-generic' 
'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' 
'Ubuntu, with Linux 2.6.35-31-generic'
'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)'
'Ubuntu, with Linux 2.6.32-40-generic' 
'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)'
'Ubuntu, with Linux 2.6.32-39-generic' 
'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)'
"Memory test (memtest86+)"
"Memory test (memtest86+, serial console 115200)"
'Bodhi 1.3.0, sdb5'
'Xubuntu 11.10, sdb6' 
'Lubuntu 11.10, sdb7'
'Kubuntu 11.10, sdb8'

```much more friendly, I think, and kernel updates are not that frequent.

Note I have two disks, so I put grub from all the secondary OSs on /dev/sdb, meaning I always have a fallback if one grub goes to worms, from whixh I can boot any of the OSs, as they all use grub2, so much better than legacy grub, in my opinion.

---

### Post by oldfred on 2012-03-22
Mine is not really different as I change the sda13 to a name that means something to me. I have so many entries I added some spacers and I use grub to loopmount boot ISOs. This reminds me that I mean to houseclean out some old kernels. :)

```
fred@fred-MavericDT:~$ cat /boot/grub/grub.cfg  | grep menuentry
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry " " {
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
menuentry " " {
menuentry "Kubuntu, Natty 11.04 (on /dev/sdc14)" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, (on /dev/sdd3)" --class gnu-linux --class gnu --class os {
menuentry " " {
menuentry "Puppy 511" {
menuentry "Chainboot hd2" {
menuentry " " {
menuentry "Chainboot hd1" {
menuentry "Chainload Other Systems Grub Menu on sdc1" {
menuentry "Uubuntu 12.04 Precise ISO 64bit" {
menuentry "Uubuntu 11.04 Natty ISO 64bit" {
menuentry "Kubuntu 11.04 Natty ISO 64bit" {
menuentry "gparted (Boot ISO Image via Grub2) " {
menuentry "Reboot" {
menuentry "Halt" {
fred@fred-MavericDT:~$ 

```

---

### Post by ottosykora on 2012-03-22
@ajgreeny

so where do you in fact keep the grub2 files?

I mean the mbr part of the grub has to jump somewhere first. Is this jumping to one of the os or into a dedicated grub partition?

And how did you manage to install the different os when the grub2 forces one to install it to mbr if it is in mbr already and wants point it to its current installation.

This the part I do not understand from the grub2 manual.
Example:
I install ubuntu, fine, the grub2 in mbr and my ubuntu partition
I install debian, now the grub2 installer forces me to install the rest in the debian partition and will point the mbr part to that position
etc.
I am now not able to remove the debian, as this will definitely make the whole computer unbootable.

So in this situation, how do I add an os and remove it again if I do not like it?

---

### Post by ottosykora on 2012-03-22
> **oldfred said:**
> 
 Ubuntu also has links in / (root) to the most recent kernal so you do not have to update the entry on every kernel update in the other install.

So I do like ajgreeny, turn off os-prober, and put an entry into 40_custom. But I use the links, so I do not boot a specific kernel.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}


hmmm, those links, did not notice them so far, are they simply on the root ?

Do other distros have them too or can I create them?

I mean, the menuentry without some kernel and uuid etc is nice and would in fact be solution for dedicated grub2 partition.

What I would like to avoid is to have all kernel entries from all distros installed in one single menu.

The problem would come up when one of the other kernels might be needed one day, then it will become more complex to boot.

And how do you manage to install other distro and have all that menuentries preserved? They are on the last installed distro after all.

---

### Post by oldfred on 2012-03-22
With manual install or Something Else you can choose where to install the grub2 boot loader. Just install it to the partition (even if not recommended) just as a throwaway, that you will never use.

If you do install it to the MBR, and can boot into your primary install just reinstall grub to the MBR from inside that install. You can install to any MBR from inside your working system.

sudo grub-install /dev/sda

But grub does remember where to reinstall, so you may want to run this to get it to remember not to install to the MBR.

#To see what drive grub2 uses see this line - grub-pc/install_devices & if part5 shown then it reinstalls to that drive sdX5:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not normally choose partitions

Once you get more than one or two installs, you really have to run the boot info script to keep track of what is where. I run it before and after every install now, just to be sure I did what I really wanted to do.

---

### Post by oldfred on 2012-03-22
I reuse my 40_custom as I save a copy in /home so it gets backed up.

 My older version had a typo (missing ending } ) on one stanza that I did not use much and did not notice the old versions did not show only that stanza. With grub 1.99 all of sudden my entire 40_custom would not work. It gave an error message on grub update and wrote it to a error file.

I think the links are in Debian versions, not sure about anyone else. There is also a link .old which is the previous version. You should see in / (root) vmlinuz & initrd.img and they will say link. We also use these for manual booting as it is a bit easier than typing the entire line, although tab complete does also.

Once you create a partition boot you can totally reinstall anything with the links to that partition and the partition boot will still boot.

---

### Post by ottosykora on 2012-03-23
>With manual install or Something Else you can choose where to install the grub2 boot loader. Just install it to the partition (even if not recommended) just as a throwaway, that you will never use.
<

hmm, so you mean that his still works?
I did not try myself exactly this way so far, only from the manual of grub2 I found that when there is mbr grub2 detected during the install, then any other install of grub2 e.g. into pbr is blocked and not possible. But it could be that there is some trick in the ubuntu installer to overcome this.
So this is where my confusion comes from.
Did you sometimes try to install grub2 to pbr (even as dummy) while grub2 start part is already in mbr? Did that really work?

OK, I found the links. Nice did not know what this is for here.
So this could help in producing menu in dedicated grub partition.

---

### Post by oldfred on 2012-03-23
I, in effect still have a dedicated grub partition on all my flash drives. I just install grub to them and manually edit my grub.cfg on the flash to boot install or ISOs. But I add chainload entries to the MBR's of my hard drives and direct partition boot entries to one or more of my installs as backup boot methods.

I have not recently installed to a PBR, so they may have changed that. I have multiple drives and recently have just used one MBR as the throwaway install and keep booting from my primary drive.

---

### Post by Questionario on 2012-03-23
mhhh, so what would be the best method to achieve this?
install each ?buntu and disable os-probing for each and then update grub after that and once I have installed them all create a small partition just to "chainload" the partitions?

---

### Post by oldfred on 2012-03-23
Grub2 does not like the install to the partition. It uses blocklists that are hard coded addresses, so on a grub update if the files get moved, you have to reinstall grub2's boot loader to the partition.

But you do not have to chainload to the grub in the partition, but just directly boot the kernels in the partition. You can use your main working install and add partition boot entries or create a grub2 only boot partition with just grub and create grub2 partition boot entries. Only if not Debian would you have to do any maintenance.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)

Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

---

### Post by Questionario on 2012-03-24
but if i directly boot the kernels from the partition, i have to keep editing the config file...
i only want to set it up once and afterwards always let them update themselves...
and I also tried directly booting the kernels from other partitions before for a very long time but never was successful... :(

anyhow, to achieve this, what must I do?
downgrade grub to grub-legacy or even replace it by syslinux/extlinux and then boot directly into each partition from a new boot partition?

---

### Post by ottosykora on 2012-03-24
oh I see, it may need the --force to get it there

well then this may not work straight from the ubuntu install, but needs to be done later by hand.

Actually, I have same Q as Questionario.

OK, with grub legacy, the very nice solution with grub partition, never changing menu system there and chainloading all from there.
Tome , it always looked as very clean and stable operation.

When I would like to achieve this with grub2 I have following options:

1.from grub in grub partition, load all kernels directly
how does the update work in this case? has to be done manually every time?
The manual maintenance of the conf/menu is not so easy
2.load the most recent kernel with the aid of the link
nice solution, probably ok with all ubuntu and deb, but not clear if this is possible with other distros

3. chainload all
but in this case the grub has to be somehow installed into pbr, probably somehow manually with the --force command or so, probably not always possible with the os installer itself.
Thereafter replacement of the grub2 in pbr with grub legacy as grub2 will not survive in pbr very long.
Grub legacy will then provide an other menu , kind of local one, with all the kernels belonging to this particular partition.

---

### Post by Questionario on 2012-03-24
hmm,
I am trying right now, I have copied one partition from my old harddrive  to the new one, so the grub there is incorrect (wrong UUID's etc.) and I  have installed the other Buntu's.
Now first, how can I "fix" the grub of the one OS I copied from the old harddrive with a live cd?
Second, what next? lol I guess I need to find a way to boot into each OS  and downgrade grub2 to grub... what should be done next? :-\

EDIT:

I installed extlinux (I am more familiar with extlinux than I am with grub) on the "boot"-partition and chainloaded one of the Buntu's, I only get a grub bash though.
On another Buntu I get the message that the partition is not bootable (it doesn't need to be primary, does it? because all installations are on an extended partition)
I assume I have to boot with a live-cd and somehow replace the grub2 that is installed on there with grub?

Can someone tell me if that's the right way and how to do this?
I tried to find something on the forums but it's always only explained for grub2.

---

### Post by oldfred on 2012-03-24
It has been ages since I used grub legacy, but I chainloaded a lot of entries to other grub entires in the PBR. I had my first grub2 in a PBR and chained to it from grub legacy.

Most of the old distributions used grub legacy so many would install grub legacy to the PBR and then one setting in grub2's 40_custom could chain to that install. But now others are also changing to grub2. I do not know if then when they change to grub2 if they also add the link in / (root) like Debian on not.

I do not recommend downgrading to grub legacy, but if you want to:
HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Few here remember grub legacy, so you will mostly be on your own. I can help you get started if you want or as I prefer help set up grub2.

If you want to post boot info script, so we can see all your isntalls.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or directly run the git/test version that has some improvements:
The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript


```

Uploaded one of my older 40_custom. I had to add a .txt to get it uploaded, but it shows a variety of grub2 custom entries.

---

### Post by Questionario on 2012-03-24
well, whatever works to be honest... if i can get grub2 to work the way I want it I'll do that...
I'll do a live-boot and try to get that boot info script

---

### Post by Questionario on 2012-03-24
a little large but here is the output:

[http://paste.ubuntu.com/898377/](http://paste.ubuntu.com/898377/)

oh and PS: not all Buntu's are installed yet, they are still to come (Ubuntu 11.10 will be installed right now and precise pangolin end of april)

---

### Post by oldfred on 2012-03-24
I do not know syslinux, but script says it wants you to install gawk to be able to calculate what it needs.

You have a Windows partition in a gpt drive. Windows will only boot from gpt if you are UEFI mode not MBR. That would be a huge change. Also grub legacy does not work with gpt drives as I remember. With grub2 and 9.10 or 10.04 I had to add manual settings to get mixed MBR & gpt drives to work. All later versions fixed that issue.

You have both a menu.lst from grub legacy and grub.cfg from grub2. Often that causes confusion as a sudo update-grub may work on the other one than you think. Your menu.lst has no boot entires. You grub2 grub.cfg shows boot stanzas but you do not have grub installed in any MBR or PBR.

Since you have two drives you can have two different boot loaders in each MBR. I normally suggest the MBR boot a system on the drive, so if one drive fails it still boots as everything is on one drive. But you can have a boot loader on one drive and the install on another.

---

### Post by Questionario on 2012-03-24
that "windows" partition is only an ntfs drive used as data storage, its only linux on this system and all OS's are installed to a 60GB SSD drive.

nothing much to know about syslinux, i think its much simpler than grub but can probably not do as much as grub. as I only use it to chainload, it should be fine.

I got 2/4 working so far, XBMCBuntu and Ubuntu are working, only annoying thing is that the boot menu keeps popping up every boot (grub menu)

with openelec I get the error 
---
Operating system load error.

Reboot and Select proper Boot device
or insert Boot Media in selected Boot device and press a key
---
With 64bit Ubuntu 10.04 it doesn't work yet either :(
I tried boot-repair but it only worked on the two that are working now...

edit: i updated the output of boot-repair above...
sdb  is only the live-usb stick i used to run boot-repair. only system hdd is sda
sda8 and sda10 are currently not booting correctly

---

### Post by oldfred on 2012-03-24
I do not see any kernels in sda8 and the grub2 in sda10 is looking for core.img in sector 1 (where it normally is with an MBR install), when it should be a sector at the beginning of the partition if installed to the partition. 

Does Boot-Repair let you --force the install of grub2 to a partition? If so you need to reinstall grub2's bootloader to sda10.

---

### Post by Questionario on 2012-03-24
This output is actually after I did a grub2 reinstall via boot-repair (on sda10)!
Why it is looking at sector 1... I dont know :-\
I tried installing the 32bit version but it gives me the same error "Boot sector signature not found (unbootable disk/partition?)"

sda8... there are only 2 files on the drive, kernel and system (system is a squashfs), it runs with extlinux.
I re-installed extlinux on that partition and now it's working fine...

now only 2 more steps to take, get that one OS working and get rid of the grub menu's (hide) of each OS, just like they are after a standard install.
PS: The working Ubuntu installation can detect the other Ubuntu/BT installation and even boot it... but I want it to boot from its own partition :-\

---

### Post by Questionario on 2012-03-25
I did a grub-install --force from the 11.10 ubuntu installation, which then worked but obviously redirected me to the grub on sda11 instead of sda10.
I also tried all kinds of boot-flags as I read somewhere that a boot_bios flag might be required but I didnt have that flag to choose from, anyhow as expected, none of the flags helped.
now I tried the same thing from within ubuntu 10.04/BT but now it still directed me to sda11. I tried boot-repair again but same thing, it gives me the grub from sda11.
Here is the output from boot-repair now: [http://paste.ubuntu.com/899587/](http://paste.ubuntu.com/899587/)
```

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda10 and looks at sector 77706488 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks for (,msdos11)/boot/grub on this drive.
    Operating System:  BackTrack 5 R2 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```I will now try to delete the partition, recreate it and try to re-install it for like the 5th time :-\

---

### Post by oldfred on 2012-03-25
Are you using LVM for some reason on sda10? You have to add LVM drivers and can only use LVM tools for editing it. That may be why you are having issues with sda10.

Your gpt drive has some sort of sync issue. The gpt partition table looks ok but the protective MBR partition is too large.

/dev/sdb1 ends after the last sector of /dev/sdb

You might try this to see if it will correct the inconsistency.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, 
sudo sfdisk -d /dev/sdb > parts_sdb.txt

Your installs of grub2 into partitions looks ok.

You only need a bios_grub partition on the sdb or gpt partitioned drive.

---

### Post by Questionario on 2012-03-25
hi,

I only tried the flags out of frustration, I don't need them and I only set them for a short period of time...
sdb is actually just a harddrive where I store data on (the important stuff), sda is the only harddrive used to boot from other than booting install media (that computer does not have a cd-rom, only usb).

I do however get a message from boot-repair everytime that says something about having a GPT-partition, which I don't (I think) as I have created a new partition table from within ubuntu installation when I installed the first OS. Maybe that has something to do with having an SSD?

is there anything left that I could even try?

EDIT: exact message from Boot Repair is:
```
GPT detected. You may want to retry after creating a BIOS-Boot partition
(>1Mo,unformatted filesystem,bios_grub flag). Do you want to continue?
```I assume the message is because I have sdb connected though...

one difference I noticed...
on ubuntu 11.10 boot-repair installs grub 1.99
on ubuntu 10.04/BT boot-repair installs grub 1.98

Here is the latest output from boot-repair after I deleted sda10 and re-created it (sda10 and sda11 are switched now because I deleted sda10)
[http://paste.ubuntu.com/899734/](http://paste.ubuntu.com/899734/)
it seems that now there isn't a grub installed at all on sda11 judging from the message... It did still give me the same error of not finding the bootsector, I tried booting into sda11 from sda10 and doing a "grub-install --force /dev/sda11" which ran successfully as always but same problem still... :-\

is there a way to force boot-repair to use the same grub it was using for ubuntu11.10?

---

### Post by oldfred on 2012-03-25
Each version of Ubuntu has different versions of applications including grub so the version difference looks ok. If you want to boot with grub use the newest.

If you create a bios_grub partition on sdb you could install the grub1.99 to the MBR of sdb to boot sda5 or sda11. With grub1.99 you do need to use the same version liveCD to reinstall it or chroot into the Ubuntu install so you are installing from inside the install with the correct version of grub.

I actually believe in having a bootable system on every drive. I have XP on one drive and at least one install of Ubuntu on every other drive. I put two / (root) partitions on my 60GB SSD with gpt so I can alternate versions that are my working or boot one and test another.  

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Questionario on 2012-03-26
sdb is just externally connected, the 60gb ssd is the only harddrive inside the system, in case an OS breaks I have lots of others on the drive and always "live-cd's" on usb.
but back to the "problem" couldn't it be that grub 1.98 is faulty and cannot write correctly to the partition? I mean if I try to write it from a different OS it seems fine... :-\

---

### Post by oldfred on 2012-03-26
The only time I used grub2 in a partition was back with 9.10 and I think that was grub1.97. So I doubt that the version of grub2 is the issue. 

But I am not sure you can correctly install grub2 to a LVM partition. Normally systems with RAID and/or LVM have a separate /boot partition for the boot files so system can read them easily. Some of the new grub2 add in modules now let grub2 directly work with many more types of systems, but I do not know details as I do not use LVM.

---

### Post by Questionario on 2012-03-26
The LVM flag was only set once as I was frustrated and ready to try anything...
It is not set and was only set for not even an hour.
 
The Grub 1.98 seems to fail all the time, it just does not correctly write the boot sector while grub1.99 seems to do it correctly.
Is there a way to force an update to grub1.99?

---

### Post by oldfred on 2012-03-26
How are you writing it? With the --force?

---

### Post by Questionario on 2012-03-26
if I do it manually, yes... otherwise it won't install on a partition (with boot-repair it does a force as well but I only copy/paste what boot-repair says)

if you meant forcing an update to grub 1.99 instead of 1.98 then no, I dont know how to force installing 1.99 instead of 1.98

---

### Post by oldfred on 2012-03-26
I do not know how to update grub to a newer version either. But you do not have to have it installed to every partition as any grub2 will boot all the systems you have installed.

---

### Post by Questionario on 2012-03-27
That is kind of what I want...
kind of... I want my own menu with background etc. and every OS to choose from but without worrying about kernel version, etc. I want the OS to update that automatically...
figured chainloading would be the easiest option.
I will try to replace grub with extlinux on that Ubuntu, maybe that'll work....
anyhow, do you know how I can disable the grub boot menu completely and just let the standard option boot (the way it is configured after a fresh install)?

---

### Post by oldfred on 2012-03-27
I have a lot of installs. I have kept every install since 9.04 since I had a newer 640K drive and only use 20 or 25GB for / (root). But I just set grub2 from the install I use the most to boot from MBR. I turn off os-prober so it does not find my other installs and use my own 40_custom that is set with boot stanzas that boot a partition not a specific kernel so I have no issues with updates.

Is something like this what you want?
Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by Questionario on 2012-03-27
thats what I did, isnt it? just instead of grub2 I used extlinux and dont have an OS on that partition... but I also boot a partition, no?
But when I try to boot the partition of the Ubuntu 10.04/BT, it cannot boot it...

---

### Post by oldfred on 2012-03-27
I really only know grub2 and cannot really help on extlinux.

---

### Post by Questionario on 2012-03-28
Hi oldfred, thanks for all your help so far!
I am fine with extlinux, its grub that I am not familiar with.
With extlinux I do nothing except of what you called boot stanzas... I boot directly into the partition, meaning I would get the same error if I would do the same thing with grub.

---

### Post by oldfred on 2012-03-28
This is from sda11 from you last boot info script, these are just links to the newest kernel:
> 25.809570312 = 27.712815104   initrd.img                                     2   29.446773529 = 31.618232320   vmlinuz                                        1

But both of your installs in sda5 and sda10 do not have both of those files. Those are not normally used to boot, I do use them when booting a partition, but since they are missing it may indicate the install was not complete. Every kernel update rewrites the links to the newest kernel.

You can chroot into the install and repair or reinstall. Not sure if Boot-Repair will update a kernel and run the scripts that install it or not.

---

### Post by Questionario on 2012-04-02
not sure I understand what you're saying but if you mean that the boot sector is not completely/correctly written to sda11.... then that's what I wanted to say... it keeps saying it finished successfully but apparently it does not!
a simple re-install of grub overwrites it from another OS, if I boot into the OS directly (from the grub boot menu of on of the other OS's) and re-install grub it finished successfully but obviously didnt do the job properly...

---

### Post by oldfred on 2012-04-02
If you are able to boot into the system, do not just update grub but update the entire system.

```
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
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
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

```

---

### Post by Questionario on 2012-04-04
tried that without success :(
the last part I replaced /dev/sda with /dev/sda11 and added --force
as for ubuntu-desktop I omitted that part as ubuntu-desktop is not installed

as extlinux is not in the OSs repository I will try to download extlinux and install it manually, it should have the same functionality as when installed with apt-get install, right? I mean it being able to automatically create the configs.
or even updating grub1.98 to 1.99 if thats somehow possible (dont know how).

Thanks!

---

### Post by Questionario on 2012-04-12
any more ideas anyone? :(

---

### Post by oldfred on 2012-04-12
Post the latest bootinfoscript.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Questionario on 2012-04-15
Hi oldfred,

here is the most recent output:
[http://paste.ubuntu.com/931159/](http://paste.ubuntu.com/931159/)

also, do you know how to disable the countdown in grub so it just boots the default?

---

### Post by oldfred on 2012-04-15
I think this is the easiest way to edit grub configs.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

I may have mentioned it several times, but forcing grub2 into the PBR uses block lists which is unreliable. Major updates to grub will break system and you will have to reinstall.

I do not really know syslinux that you have in MBR, but I believe it is like Windows boot loader in that it just jumps to the boot flagged or Windows active partition. You have boot flag on sda. I do not know if it will directly boot a logical partition, lilo does, Windows does not. Syslinux, lilo & Windows are all boot loaders that use boot flag. Grub does not use boot flag.

---

### Post by Questionario on 2012-04-15
can i install grub customizer on a live usb and change the config of all installed OSs?
as for extlinux... as mentioned I only use it to "redirect" booting to each partition with a label... (I think in grub it is called boot-stanzas?)
works great with ubuntu (with grub 1.99) but not with BT (with grub 1.98 ).
not much to understand with extlinux, its the most simple config, a label for each OS-partition and then a chainload into that partition... the real issue seems to be though that grub 1.98 is unable to correctly install on a partition (works fine on mbr)...

sda boots into sda1 where I have nothing but syslinux with a simple config to boot each partition, after that its a boot straight into the selected partition.

EDIT: I think I am not sure what you mean with forcing grub2 into PBR being unreliable... how else would I be able to boot the partition? I dont even know what blocklists are, can I disable them?

---

### Post by oldfred on 2012-04-15
Standard grub2 is large, larger than grub legacy and too large for a PBR. It converts to blocklists which are hard coded addresses of where on the drive the rest of the grub files it needs to boot (instead of code to search a UUID to find file and use it). If using a PBR you have blocklists. If file moves location on drive after and update or even an aggessive filecheck, you will have to reinstall grub to the PBR as address has changed. I did have grub2 in a partition with 9.10 for several months without issues but it depends on when a major update occurs.

I do not think you can use any software in one install to modify another install, unless you chroot into it and run it from that install. Or mount partition and manually edit file.

I think you are forcing syslinux to boot a complex configuration when it is not really designed for that. 

Grub2 does exactly what you want without maintenance for Debian based installs (boot partition not kernel) or will chainload systems with grub legacy without issue.

---

### Post by Questionario on 2012-04-15
but isnt the issue here that grub 1.98 doesnt seem to install at all into the PBR?
extlinux boots the grub2 partitions just fine (it boots all other partitions just fine).
if you really think thats going to help, I'll try to replace extlinux with grub if you tell me how (although I dont think that will help unless the PBR will install correctly)

---

### Post by oldfred on 2012-04-15
Grub2 does not have to chainload. It will directly boot any Debian based install and most Linux installs. The issue is that you have to reboot into the grub2 install to update the entry to a new kernel in other installs. I still have one or two chainload entries in my grub2 40_custom.

Whichever install you use the most, install grub2 to the MBR and then run this:
sudo update-grub

If you can boot into the install you want as your main install, this is all you have to do, install to same drive sda, sdb etc as your install is in and set BIOS to boot that drive:

sudo grub-install /dev/sda
sudo update-grub

That should get you booting everything. A very few installs need manual help. But we can add some things to simplify booting other installs, but lets see it you can boot first.

You can create a grub2 only partition if you want, but then you have to manually add all the entries. 
Herman on separate grub or grub2 partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

---

### Post by Questionario on 2012-04-15
I dont want to be a pain but thats exactly what I didnt want to do...
My goal is to do it with a separate boot partition from where I can boot into each PBR.
Also that way grub2 wouldnt detect the non-ubuntu partition and wouldnt include it in the menu unless I manually add it (which is not what I want to do).

Is there really no way to force an install of grub 1.99 instead of grub1.98?
I really dont think grub2 will be able to boot a defective PBR either...
If you can help me adding a manual entry to grub2 (from one of the OSs (the ubuntu one to be specific) I have already installed) I'll definitely try if grub2 can boot the incomplete PBR

---

### Post by oldfred on 2012-04-15
If you have one Ubuntu that works and one that does not, add this to the 40_custom of the one that does and run sudo update-grub. Change all the 13's to whichever partition number your non-working install is in. This does assume the kernel has installed correctly and updated the links in / (root) to the newest kernel.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
# should not need this
#sudo dpkg-reconfigure grub-pc

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by tealio on 2012-04-19
oldfred, the following just solved my problems.

> menuentry "Daily on sda13" {
set root=(hd0,13)
linux /vmlinuz root=/dev/sda13 ro quiet splash
initrd /initrd.img
} 

I was thinking about starting / hijacking a thread similar to this one, and I decided to do one last search.  First hit, last post.  Lucky me.  I've been trying to install grub-legacy to my debian partition so i could chainload it, in order to achieve what this menuentry achieves.  Thanks Thanks Thanks!  

I've been searching for this very answer for quite a while, and even got some advice from you earlier in the week.  THIS was what i needed.  And now that i see it it seems so SIMPLE!  Using the symlinks that were staring me in the face the whole time!

Again, thanks!

---

