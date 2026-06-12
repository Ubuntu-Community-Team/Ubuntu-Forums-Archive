---
title: "Encryption and Manual partitioning"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by wunderbar101 on 2012-12-28
Hey all, i was hoping someone could shed some light on a problem i'm having while installing 12.10

Maybe i'm just not seeing the option somewhere, but it seems like if i choose to encrypt the whole disk during installation, i am unable to also manually partition my hdd...

If i choose the 'something else' option, i can manually partition the drive as i want to, but then the installation continues and doesn't seem to give me the whole disk encryption option, i only get the 'encrypt home directory' option later on.

So my question is, how do i choose the whole disk encryption option, while also being able to manually partition my drive?

Thanks

---

### Post by oldfred on 2012-12-28
Welcome to the forums.

I have not used encryption, but I thought whole disk encryption was only available with the alternative installer. You have to use LVM which is not part of the desktop installer. And 12.10 has done away with the alternative installer as they hope to have everything in the Desktop gui version, but do not yet.

This is to a USB flash drive but shows the install process.
       Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

Correction, it is supposed to work?
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> Users who were installing using the alternate CD to install with LVM or  full-disk encryption can now use the desktop image for this

---

### Post by Herman on 2012-12-28
I'm not sure whether it works or not. When I had a look the option appeared to be there in 12.10 but clicking on it didn't seem to do anything. I didn't spend very much time with it though, as I was installing for somebody who wanted a plain, standard install in a single partition. Maybe I should try again sometime and see if I can find out if there's any trick to it or if I was just unlucky that time.

If you find you cannot install 12.10 in the way you want, you should be  able to install 12.04 instead and then upgrade to 12.10 afterwards  whenever you are ready.

I do know that we can use the 12.04 Alternate CD for encrypted lvm installations and the option to 'use entire disk and set up encrypted lvm' is quite straightforward. That will install Ubuntu with a separate /boot (not encrypted) with an encrypted / in a single partition.

I also know that if you want to install with separate /home and maybe even further divide your installation up into a lot of separate partitions for some reason, it is/was possible to do that using the Alternate installation CD.
Before you start you must get rid of any swap areas in the disk and in other disks that may be plugged in to the computer, (unplug them).
You start off installing normally and choose 'manual' partitioning instead of  'use entire disk'. 
Then you create your /boot partition. 
With the remaining free space, set 'physical volume for encryption' as the file system, and proceed to set up the encrypted volume with a passphrase.
You then modify the encrypted volume with the logical volume manager to creat a volume group, (call it 'root' or whatever you want). You can select one or more devices for the volume group.
Now you can create all your new LVs, as many as you like, you can have separate /usr , /usr/local, /opt, /tmp,  /var, /swap , /home , and whatever others you like and of course / (root).
Set up a file system in each of your new LVs and save the changes.

There was a website about how to install Ubuntu as described above but the last time I found it was back when Lucid Lynx came out. The site is no longer available. It's not easy to explain it all in a few words, and even with the help of now non-existing web site the procedure was not simple even for a person with a lot of experience using the Alternate CD.

I am looking forward reading about someone who can confirm the 12.10 (or later) Desktop CD will work for setting up an encrypted LVM and especially from someone who has used it to create an installation across several logical volumes, and/or across multiple disks. I may try again myself when time allows.

---

### Post by wunderbar101 on 2012-12-29
Thanks for the replies

I may try installing 12.04 and then upgrading, my only concern is that at this point it seems like the full disk encryption option doesn't support multiple partitions or something like that? So i would guess that the upgrade from 12.04 wouldn't offer the full disk encryption option.

As well as the encryption option, i can also choose the LVM option, is it possible that due to whatever limitations that the full disk encryption has, i'm only able to use LVM for partition management once the install is complete?

I did do an install with the LVM option ticked, and inside the install i ended up with 3 partitions as follows : 

[I]/dev/sda1   boot   Linux  
/dev/sda2            Extended
/dev/sda5            Linux[/I]

It then tells me after the information about each partition, the following 3 errors : 

[I]Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table
Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table[/I]

I'm not sure what those mean exactly, but i also get this during boot up : 

*The disk drive for /dev/mapper/ubuntu-swap is not ready yet or not present*

So again, i'm not sure if its setup correctly or what, but either way it isn't making the partitions how i want them which is a separate partition for root, home and swap area.

Is it possible that the full disk encryption option is limited in a way that doesn't allow for partitions to be setup in any other way than what it does by default, and is shown above in my fdisk results?

And are those errors simply a result of how it is forced to set up the partitions under full disk encryption?

---

### Post by wunderbar101 on 2012-12-29
I found this link which seems to confirm that if you want full disk encryption, you have to let it do its default partitioning scheme which is as i listed above : 

[http://www.linuxbsdos.com/2012/09/04/full-disk-encryption-and-lvm-configuration-in-ubuntus-graphical-installer/](http://www.linuxbsdos.com/2012/09/04/full-disk-encryption-and-lvm-configuration-in-ubuntus-graphical-installer/)

It also shows that if you want to install 12.10 along side another OS install, it won't let you choose to encrypt the whole disk, which makes me believe that if you want to upgrade from 12.04 you are probably also unable to encrypt the whole disk, it seems like a limitation with the option that requires it to repartition in its default scheme from scratch

Oh well, i will just be installing it and letting it do the partitions automatically, i'll keep reading up on why exactly it can't encrypt the partitions you make yourself, i'm not too knowledgeable on how whole disk encryption works and what the limitations are really

---

### Post by Herman on 2012-12-29
Well I don't know about the new Ubiquity yet for 12.10 thanks for the link, it looks like it is worth another try, the author of that web page must have definitely it working.

I'm typing to you right now from a USB stick which has Ubuntu Lucid Lynx installed in it in LUKS encrypted LVM. It has a separate /tmp,  /swap, /var, /home, /root, and /usr. This was installed using the Ubuntu 'Alternate' CD.


[IMG]http://members.iinet.net/~herman546/index_files/Screenshot-Logical%20Volume%20Management.png[/IMG]

---

### Post by Herman on 2012-12-29
> I may try installing 12.04 and then upgrading, my only concern is that  at this point it seems like the full disk encryption option doesn't  support multiple partitions or something like that? So i would guess  that the upgrade from 12.04 wouldn't offer the full disk encryption  option. What I meant was, if you install 12.04 in encrypted lvm (using the Alternate CD, then you can install how you want and then upgrade to 12.10 later. (not install alongside).

EDIT: I am taking a look into the 12:10 installation process and I have found out that after we choose 'Something Else' from the "Installation Type" frame, we are able to set the file system type as 'physical volume for encryption', and I have managed to perform an encrypted installation with separate /boot (not encrypted of course), and encrypted /root and /home quite easily.  I am not happy with the LVM side of things and will try again to see if there are some options I missed.

EDIT2: I tried but was not able to find out how to create an installation over separate logical volumes in 12.10 and ended up just installing with standard default   /root, /boot and swap.
At least I confirmed that the 12.10 installer does have the ability to install in LUKS encrypted LVM, which is very good. Later I stretched the / LV out over three other USB flash memory sticks so now I have a 64 GB USB flash memory installation on a USB hub, Cool!  
Possibly Ubuntu could be installed as normal and /home  could be moved  later after the installation is complete to a separate logical volume  and etc/fstab could be edited, if a person wanted a separate /home badly enough.

EDIT3: This link looks interesting, [https://help.ubuntu.com/community/StripedVolumeHowTo](https://help.ubuntu.com/community/StripedVolumeHowTo), among other thing it says that when the LVM is already set up prior to beginning the installation from the Desktop LiveCD, the installer is able to recognise the Logical Volumes and install into them, and that dates back as far as Jaunty Jackalope. It doesn't mention anything about LUKS file system encryption though, it's about LVM. 
The Lucid Lynx muilti partition encrypted installation I showed a screen  cap of earlier was an experiment to see if I could do it for one thing,  and also to see if having the reiser file system in some partitions  made the operating system faster as some Arch forum members were  claiming in these forums. Thinking on it a little more, I am wondering if there's actually any point in creating a separate /home with an encrypted installation for the purposes of preserving the users files and settings over a re-install? Will the Desktop installer be able to re-install a new OS in the /boot and root with the ability to mount the existing /home when it has been uniquely encrypted in a previous installation?

EDIT4: We just need to run 'sudo cryptsetup luksOpen /dev/sda2 crypt1' (or whatever disk and partition number applies), and type the encryption passphrase for the installer to recognize our older LUKS encrypted LVM installation. Then when we open the installer and select 'something else', we can see a graphical representation of all of our logical volumes. I haven't tried reinstalling yet but it should be quite do-able.
Intead I went back and tried to upgrade instead, but received an error message about some of my file systems being less than 2.6 GB, which I ignored and then installer crashed after almost completing the upgrade. I then enabled universe repository and installed system-config-lvm for resizing my Lucid Lynx multiple partition installation's logical volumes. (The command line name for Logical Volume Manager as shown in the screen cap above  is system-config-lvm).

EDIT 5: The failed upgrade has borked my system to the point where further attempts to upgrade are not completing either. I'm re-installing in the same logical volumes. I was right in guessing that it's no problem to select the already created logical volumes and assign various file systems and mount points for each, and to decline to format /home. All appears to be going well again.
 I found this link while I am waiting for the re-install to complete which I think goes pretty close to providing a workaround for a person wanting a separate /home in LVM, [**HowTo: Setup Ubuntu Desktop with LVM Partitions**]("http://ubuntuforums.org/showthread.php?t=1782296") by ruffEdgz. The only other thing needed would be to create a LUKS encrypted partition for the LVM.

EDIT 6: The installation completed okay but so far it can only half boot as it can't open /dev/mapper/lvm-root, no such file, (but there is). I'm getting tired and I'll continue some other time.

EDIT 7: It's working properly now, I just had to chroot and add an /etc/crypttab file,  edit /etc/initramfs-tools/modules and rebuild the ramdisk, roughly in accordance with the following how-to: [final preparation]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Final_preparation")  - Ubuntu Community Docs. That link is part of a page called '[Encrypted Filesystem LVM How-to]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")' - Ubuntu Community Docs, see also '[EncryptedFilesystemsViaUbiquity]("https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity").

Given the information in the links above, it should be possible for a person who wants to use the Ubuntu 12.10 CD for installing a LUKS encrypted installation in LVM with a custom partitioning scheme to be able to go ahead and do so.  GParted and  Logical Volume Manager can be substituted for some of the command line tools to make the process a little easier.

---

