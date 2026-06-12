---
title: "I am trying to install Ubuntu to my CR-48. . .I don't have a 64-bit capable computer."
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by ~~Tito~~ on 2010-12-22
What should I do? All I need is chroot? I downloaded and sync'd the Chromium OS dev environment ONLY for the chroot since that is all I need, and I cant use it since it only works on 64 bit. I cant get it to work after trial and tribulation either lol. Its a big PITA, its just chroot, nothing else. Everything else is either entered from the CR-48's terminal, or from native linux. Any input here? I really want a lightweight Linux box, especially one like this!

I am following this guide:
[http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48)

I used this guide to try and get chroot:
[http://www.chromium.org/chromium-os/developer-guide](http://www.chromium.org/chromium-os/developer-guide)

---

### Post by ~~Tito~~ on 2010-12-23
I solved it by ssh'ing the CGPT file into my chroot/bin folder. Then meshed these two guides together to make things simple and quick. Make sure you mostly follow the first guide, then use the 2nd guide for things that don't work for you.

Use this for a basic chroot, then place the CGPT file in the /var/chroot/bin folder. Make sure you note where the chroot temp directory is, since that is where your .bin, and .vdi's will be, not in the Chromium OS chroot folder as the 1st guide says.

[http://help.ubuntu.com/community/BasicChroot](http://help.ubuntu.com/community/BasicChroot)

[http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48)

[http://bbs.archlinux.org/viewtopic.php?id=110208&p=1](http://bbs.archlinux.org/viewtopic.php?id=110208&p=1)

---

### Post by ~~Tito~~ on 2010-12-23
Oh, when you are editing the kernal, follow the guide on the chromium OS site, and get the files you need from the arch forums.

---

### Post by ~~Tito~~ on 2010-12-23
One more thing, make sure you use the USB stick method of delivering the rootfs.bin. Just mount the USB stick on the CR-48, then do the dd flash command. It takes a long while, maybe a good 10 - 15 min.


Maybe later on I will make a mashed together guide with the steps I used.

---

### Post by bwhite82 on 2010-12-23
I look forward to seeing your guide for this. I attempted but ran into not having a 64 bit computer.

---

### Post by ~~Tito~~ on 2010-12-23
**_[SIZE="1"]Okay, this is just a mashed together guide between the [SIZE="3"][Chromium OS site]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48")[/SIZE], and a [SIZE="3"][guide a user posted on the Arch Linux forums]("http://bbs.archlinux.org/viewtopic.php?id=110208&p=1")[/SIZE]. Also referring to the [SIZE="3"][setting up a basic chroot guide]("http://help.ubuntu.com/community/BasicChroot")[/SIZE][/SIZE]_**

[SIZE="4"]First things first: Things you will need![/SIZE]
[LIST]
[*]Having a 2gb+ USB stick, or memory card reader with a 2gb+ card on it
[*]Having an 8gb+ Usb stick, or memory card reader with a 8gb+ card on it
[*]Set Up a  basic chroot
[*]Setting up a recovery stick for the CR-48 incase you screw up partitions
[*]Setting up an ssh partner ship between the CR-48 and your linux box
[*]SSH'ing the required file to be able to do the chroot commands
[*]Time
[*]Patience and some linux knowledge
[*]Virtual Box installed
[*]Ubuntu installation image for 10.10, this can be any linux distro as well.
[/LIST]

[SIZE="4"]Peparations[/SIZE]
This is mostly taken from the guides from above.

[INDENT]**Creating a chroot**[/INDENT]

Install the ```
dchroot
``` and ```
debootstrap
``` packages.
As an administrator (i.e. using sudo), create a new directory for the chroot. In this procedure, the directory ```
/var/chroot
``` will be used. To do this, type ```
sudo mkdir /var/chroot
``` into a command line.

As an administrator, open /etc/schroot/schroot.conf in a text editor. Type ```
cd /etc/schroot
```, followed by ```
gksu gedit schroot.conf
```. This will allow you to edit the file.

Add the following lines into schroot.conf and then save and close the file. Replace your_username with your username.
```
[lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
```
Open a terminal and type:
```
sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
```

This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded.
Note: You can replace lucid with the Ubuntu version of your choice.
Note: You must change the above mirror.url.com with the URL of a valid archive mirror local to you.
A basic chroot should now have been created. Type sudo chroot /var/chroot to change to a root shell inside the chroot.
Setting-up the chroot
There are some basic steps you can take to set-up the chroot, providing facilities such as DNS resolution and access to /proc.

Note: Type these commands in a shell which is outside the chroot.

Type the following to mount the /proc filesystem in the chroot (required for managing processes):
```
sudo mount -o bind /proc /var/chroot/proc
```
Type the following to allow DNS resolution from within the chroot (required for Internet access):
```
sudo cp /etc/resolv.conf /var/chroot/etc/resolv.conf
```
Very few packages are installed by default in a chroot (even sudo isn't installed). Use apt-get install package_name to install packages.

Open another Terminal and type the following to enter the chroot:
```
sudo chroot /var/chroot
```

[I][SIZE="3"]
Now that you have the chroot set up you have to set up a recovery stick in case you ever screw up. This allows you to restore everything to how it was when you first got your CR-48. You will need another USB stick, 2gb is the perfect size. Just refer to this section to when ever you screw up then start over and go to the point you where at before you screwed up, then continue. When you run the script, don't delete the temp files, it saves you loads of time!
[LIST]
[*]Follow the instructions here:
[http://www.google.com/support/chromeos/bin/answer.py?answer=1046510](http://www.google.com/support/chromeos/bin/answer.py?answer=1046510)
[/LIST][/SIZE][/I]

[INDENT]**Setting up SSH**[/INDENT]
Assuming you have wifi, and have knowledge of SSH, and both the CR-48 and the Linux box you will be doing this from are connected to the same wifi network:

Switch to VT2 (press [ Ctrl ] [ Alt ] [ --> ]), and log in as user ```
chronos
``` (no password required), then run ```
sudo bash
```

*You don't need to set up a password for chronos, that locks you out of login in as root with no password.

Connect to your linux box by entering:
```
ssh {Your User name for your linux box}@{The local ip the linux box has, IE 192.168.xxx.xxx}
```

Then follow the dialogs, and type yes when necessary to connect. Ignore the warnings.

Now that you are connected type ```
exit
``` and it should go back to the chronos user. Type ```
sudo bash
``` to get permissions again.

[INDENT]**SSHing the required file**[/INDENT]
Now that we can use ssh we have to send the CGPT file to your linux box in order to do the chroot part of the guide later.

Make sure you are still logged in and have the proper permissions still.

Type on the CR-48
```
scp /usr/bin/cgpt user@ubuntuHost:/var/chroot/bin
```

Once it transfered successfully type this on your linux box in a terminal
```
chmod a+rx /var/chroot/bin/cgpt
```

When that is done now we can start setting up the ubuntu image for the CR-48.

**[SIZE="4"]Virtual Box and Setting it up to copy to the CR-48 directly[/SIZE]**

First, although the Cr-48 CPU and BIOS is 64-bit, the kernel and rootfs are presently 32-bit. Since you're reusing the Chrome OS kernel, you'll download and use the 32-bit ubuntu-10.10-desktop-i386.iso from an Ubuntu CD mirror.  For example:

wget [http://mirror.anl.gov/pub/ubuntu-iso/CDs/10.10/ubuntu-10.10-desktop-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs/10.10/ubuntu-10.10-desktop-i386.iso)

Second, even in developer mode, the Cr-48 will only boot external drives that are signed by Google. That means we can't (easily) use the normal Ubuntu live installer. Instead, create an empty disk image file with a 5G partition on it, and use VirtualBox to install into that. Then transfer that raw partition onto the Cr-48 once you set up the partitions.

To install VirtualBox (and its command line management tool, VBoxManage) on Ubuntu:

```
sudo aptitude install virtualbox-ose
```

Create the file inside the chroot so I can use the cgpt tool, but run VirtualBox from outside. 
You need our disk image to be a little larger than 5G so it has room for the GPT headers.

So, do the following, open a terminal, open chroot then enter this

```
cd /tmp
```
```
rm -rf test.bin
```
```
dd if=/dev/zero bs=512 seek=10486015 count=1 of=test.bin
```
```
cgpt create test.bin
```
```
cgpt boot -p test.bin
```
```
cgpt add -b 128 -s 10485760 -t data -l ubuntu test.bin
```

From outside the chroot, translate the binary into a virtualbox disk:

```
cd /var/chroot/tmp
```
```
VBoxManage convertdd test.bin test.vdi --format VDI
```

Launch the VirtualBox GUI (virtualbox) and create a new virtual machine with 2G of RAM(**It is unnecessary to specify that amount of ram unless your machine can handle it. Specify the amount your machine will handle**). Configure test.vdi as the existing hard disk (SATA port 0), and attach the Ubuntu .iso as the IDE secondary master. Everything else can be left as default.

Boot the virtual machine and install Ubuntu onto /dev/sda1.  The Chrome OS kernel does not use swap memory, so be sure to specify partitions manually.  Select the middle /dev/sda1, and format it for ext2, and mount on /.  The ubuntu installer should warn you that you have no swap partition, and it will therefore disable swap.  This is what we want.

Once Ubuntu is installed, working and updated, shut the virtual machine down and convert the .vdi image back into a binary:

```
VBoxManage internalcommands converttoraw test.vdi test_new.bin
```

Now, we'll extract just the Ubuntu rootfs partition from the binary file:

```
dd if=test_new.bin bs=512 skip=128 count=10485760 of=rootfs.bin
```

Transfer the resulting file onto the USB 8gb+ flash drive or Card reader with an 8gb+ card in it. Then have it ready when you need it for the next section.

---

### Post by ~~Tito~~ on 2010-12-23
**[SIZE="4"]Making Partitions and setting up ubuntu[/SIZE]**
Remember the Recovery stick that was made earlier in the guide? This is where it comes in handy, these commands change the partition sizes on the SSD of the CR-48 and if you screw up you can reboot and it tells you to use a recovery stick. That is why you have to make it, plus it is handy if you just want Chrome OS back for good. Since you did the preparations before hand you can just jump right in to resizing the partitions and continuing if you ever mess up.

First go to the CR-48 terminal, then login as ```
chronos
``` as usual and type ```
sudo bash
```.

To prevent the lock screen from logging you out of VT2, leave Chrome OS parked on the login screen. To prevent the backlight from dimming while in VT2, run ```
sudo initctl stop powerd
```.

Take a look at the SSD layout. It should be something like this (the UUID values will all be different, of course):

```
localhost ~ # cgpt show /dev/sda
     start      size    part  contents
         0         1          PMBR (Boot GUID: 045E5C92-6F57-9B46-BDCC-99BFF876E469)
         1         1          Pri GPT header
         2        32          Pri GPT table
    266240  22622208       1  Label: "STATE"
                              Type: Linux data
                              UUID: 1844A16D-AEC9-7C4B-9553-C3EB4814F6BB
      4096     32768       2  Label: "KERN-A"
                              Type: ChromeOS kernel
                              UUID: D176DC60-81F1-654E-8953-E3D28019738C
                              Attr: priority=3 tries=0 successful=1
  27082752   4194304       3  Label: "ROOT-A"
                              Type: ChromeOS rootfs
                              UUID: 0193CA51-DA12-9847-A715-C90433E55F60
     36864     32768       4  Label: "KERN-B"
                              Type: ChromeOS kernel
                              UUID: F1A2C65C-CC22-FF4A-A8BC-67BA233F3D40
                              Attr: priority=0 tries=15 successful=0
  22888448   4194304       5  Label: "ROOT-B"
                              Type: ChromeOS rootfs
                              UUID: B3361FB5-4DAC-9344-B7E5-870B7AC5FEA1
        34         1       6  Label: "KERN-C"
                              Type: ChromeOS kernel
                              UUID: B6954485-4295-9749-956A-C315B01FB684
                              Attr: priority=0 tries=15 successful=0
        35         1       7  Label: "ROOT-C"
                              Type: ChromeOS rootfs
                              UUID: 5B5202B5-F74B-714E-9538-ADE56B2E5662
     69632     32768       8  Label: "OEM"
                              Type: Linux data
                              UUID: 84971802-0D1C-504B-9CB5-DEA896F0AD3F
        36         1       9  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 77375DA6-8F07-704A-BBF4-2BCA662BFDFF
        37         1      10  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 6880F478-EB05-8B4B-B951-94A96076263E
        38         1      11  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 12DDC236-8FDF-4049-9A2D-10FAB17D3AA9
    233472     32768      12  Label: "EFI-SYSTEM"
                              Type: EFI System Partition
                              UUID: 045E5C92-6F57-9B46-BDCC-99BFF876E469
  31277199        32          Sec GPT table
  31277231         1          Sec GPT header
```

The units are 512-byte disk sectors.

On Chrome OS there are several bootable images, each composed of a kernel and a root filesystem (rootfs).  For a given image, the kernel and rootfs are stored on a pair of consecutive partitions.  Two of these images, Image-A and Image-B, are for official Chrome OS:
KERN-A and ROOT-A on partitions /dev/sda2 and /dev/sda3
KERN-B and ROOT-B on partitions /dev/sda4 and /dev/sda5
When the Chrome OS autoupdater downloads a new image (every six weeks or so, as new versions are pushed out), it alternately stores it in Image-A and Image-B - whichever image isn't currently running.  The autoupdater even runs in developer mode, as long as we are running an official Chrome OS image.

For Ubuntu, we'll use the currently unassigned Image-C, composed of KERN-C and ROOT-C on partitions /dev/sda6 and /dev/sda7, respectively.

However, initially they are too small so, first we need to grow them by stealing from the upper half of the stateful partition, STATE (/dev/sda1).  Initially, STATE is 22622208 512-byte sectors, or just under 11 GB.  From this we'll set aside 16 MB for KERN-C, and 5 GB for ROOT-C.

```
umount /mnt/stateful_partition
```
```
cgpt add -i 1 -b 266240    -s 12103680 -l STATE   /dev/sda
```
```
cgpt add -i 6 -b 12369920  -s 32768    -l KERN-C  /dev/sda
```
```
cgpt add -i 7 -b 12402688  -s 10485760 -l ROOT-C  /dev/sda
```

Using these values ensures that only the original STATE partition is affected.

Now the partition table should look something like this (changes in bold):

```
localhost ~ # cgpt show /dev/sda
     start      size    part  contents
         0         1          PMBR (Boot GUID: 045E5C92-6F57-9B46-BDCC-99BFF876E469)
         1         1          Pri GPT header
         2        32          Pri GPT table
    **266240**  **12103680**       1  Label: "STATE"
                              Type: Linux data
                              UUID: 1844A16D-AEC9-7C4B-9553-C3EB4814F6BB
      4096     32768       2  Label: "KERN-A"
                              Type: ChromeOS kernel
                              UUID: D176DC60-81F1-654E-8953-E3D28019738C
                              Attr: priority=3 tries=0 successful=1
  27082752   4194304       3  Label: "ROOT-A"
                              Type: ChromeOS rootfs
                              UUID: 0193CA51-DA12-9847-A715-C90433E55F60
     36864     32768       4  Label: "KERN-B"
                              Type: ChromeOS kernel
                              UUID: F1A2C65C-CC22-FF4A-A8BC-67BA233F3D40
                              Attr: priority=0 tries=15 successful=0
  22888448   4194304       5  Label: "ROOT-B"
                              Type: ChromeOS rootfs
                              UUID: B3361FB5-4DAC-9344-B7E5-870B7AC5FEA1
  **12369920**     **32768**       6  Label: "KERN-C"
                              Type: ChromeOS kernel
                              UUID: B6954485-4295-9749-956A-C315B01FB684
                              Attr: priority=0 tries=15 successful=0
  **12402688**  **10485760**       7  Label: "ROOT-C"
                              Type: ChromeOS rootfs
                              UUID: 5B5202B5-F74B-714E-9538-ADE56B2E5662
     69632     32768       8  Label: "OEM"
                              Type: Linux data
                              UUID: 84971802-0D1C-504B-9CB5-DEA896F0AD3F
        36         1       9  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 77375DA6-8F07-704A-BBF4-2BCA662BFDFF
        37         1      10  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 6880F478-EB05-8B4B-B951-94A96076263E
        38         1      11  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 12DDC236-8FDF-4049-9A2D-10FAB17D3AA9
    233472     32768      12  Label: "EFI-SYSTEM"
                              Type: EFI System Partition
                              UUID: 045E5C92-6F57-9B46-BDCC-99BFF876E469
  31277199        32          Sec GPT table
  31277231         1          Sec GPT header
```


At this point we should destroy the STATE partition contents, because otherwise at the next boot the startup scripts may notice that it's corrupted and will erase it using the old size (obtained from dumpe2fs) and not the new one. Best to be safe and just zap it now. This will take a couple of minutes to run:

```
dd if=/dev/zero of=/dev/sda bs=131072 seek=1040 count=47280
```

To speed up SSD access, we use a block size of 131,072 bytes (128 KB), which aligns with the SSD erase size.

And now reboot so that the startup script recreates the required files in the stateful partition. This will do a safe wipe first, so you'll have to wait a bit (again).

Once it boots enter the terminal, then connect the USB Flash drive or Card reader with the card in it.

First find what drive it is before you mount it
```
dmesg | tail
```
When you find the drive name, mount it
```
mount /dev/xxx /media
```

Then flash the rootfs by typing in this DD command, remember if you ever screw up you can always restore it with the USB restore stick.

```
dd if=/media/rootfs.bin of=/dev/sda7
```

Once it completes, unmount the drive

```
umount /dev/XXX /media
```

then take it out.

You can see that it worked by mounting the new rootfs and looking around:

```
mkdir /tmp/urfs
```
```
mount /dev/sda7 /tmp/urfs
```
```
ls /tmp/urfs
```

While we're looking, let's copy the cgpt tool into Ubuntu's rootfs. Make sure it's executable. We'll need this later.

```
cp /usr/bin/cgpt /tmp/urfs/usr/bin/
```
```
chmod a+rx /tmp/urfs/usr/bin/cgpt
```

We'll need to copy all the kernel modules too.

```
cd /lib/modules
```
```
cp -ar * /tmp/urfs/lib/modules/
```

That should do it.

```
umount /tmp/urfs
```

You can now move on to editing your kernal and booting into Ubuntu or the linux distro of your choosing.

**[SIZE="4"]Configure the kernel[/SIZE]**
Continue on from the last step, this is still from the CR-48.

The next step is to copy the currently running Chrome OS kernel to KERN-C (/dev/sda6).  Remember, an image consists of a kernel and a rootfs on consecutive partitions.  So, to figure out which kernel is running, we can check which partition is currently mounted as the rootfs:

```
rootdev -s
```

If this prints ```
/dev/sda3
``` (ROOT-A), then our kernel is on /dev/sda2 (KERN-A).
If this prints ```
/dev/sda5
``` (ROOT-B), then our kernel is on /dev/sda4 (KERN-B).
Assuming our kernel is on ```
/dev/sda2
``` (KERN-A), copy it to /dev/sda6 (KERN-C):

```
dd if=/dev/sda2 of=/dev/sda6
```

Now we need to change the kernel command line to use our Ubuntu rootfs instead of a Chrome OS rootfs. For this, we'll use make_dev_ssd.sh, located [here]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/make_dev_ssd.sh&q=package:chromiumos&d=0").  The latest version has options to change individual kernel command lines. You also need to haev the common.sh file. So download it [here]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/common.sh&q=package:chromiumos&d=0"). Make two blank files in a folder of your choosing, then paste the code for each file. Then name them appropriately. **(IE, the file with the script for common.sh is named common.sh)**

Use scp to copy it from your host to the stateful partition of the Cr-48.
**NOTE THE "." after the directory**
```
cd /mnt/stateful_partition
```
```
scp USER@HOST:/some/path/to/latest/make_dev_ssd.sh .
```
```
scp USER@HOST:/some/path/to/latest/common.sh .
```

Extract the existing kernel command line from KERN-C, and save it to a file named foo.6 (the .6 extension is added by the script):

```
sh ./make_dev_ssd.sh --partitions '6' --save_config foo
```

The default Chrome OS kernel command line looks something like this:

```
quiet console=tty2 init=/sbin/init add_efi_memmap boot=local rootwait ro noresume noswap i915.modeset=1 loglevel=1 cros_secure kern_guid=%U tpm_tis.force=1 tpm_tis.interrupts=0 root=/dev/dm-0 dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="vroot none ro,0 1740800 verity /dev/sd%D%P /dev/sd%D%P 1740800 1 sha1 50adbfb72bb1efda0c1a86dcd1c1d6a0b46726d1" noinitrd
```

The only editor on the Cr-48 is qemacs, so open foo.6 with qemacs:

```
qemacs foo.6
```

Edit the file to look like this:

```
console=tty1 init=/sbin/init add_efi_memmap boot=local rootwait ro noresume noswap i915.modeset=1 loglevel=7 kern_guid=%U tpm_tis.force=1 tpm_tis.interrupts=0 root=/dev/sda7 noinitrd
```

Then save (Ctrl-x Ctrl-s) and exit (Ctrl-x Ctrl-c). qemacs occasionally gets confused, so double-check to be sure you have the right content:

```
cat foo.6
```

Finally, use make_dev_ssd.sh to replace the kernel command line in KERN-C:

```
sh ./make_dev_ssd.sh --partitions '6' --set_config foo
```

The kernel command line is part of the kernel partition, and the entire partition must be cryptographically signed in order to work. We can't replace the command line part without affecting the entire kernel partition. The script will save a backup copy before replacing the partition content, but we shouldn't need it.

**[SIZE="4"]Setting boot priority[/SIZE]**

At this point we should have the following situation:

Image-A is an official Google Chrome OS which can boot either in normal mode or dev-mode.
Image-B is (or will be after the first autoupdate) another official Google Chrome OS which can boot either in normal mode or dev-mode.
Image-C is Chrome OS kernel with a modified command line and an Ubuntu rootfs, which can only boot in dev-mode.

Next, we adjust the priority among the images so we can try out our Ubuntu image. The image priority is an attribute of its kernel partition.  Run ```
cgpt show /dev/sda again
```, to see the kernel priorities:

**NOTE THIS WONT BE THE ONLY THING THAT SHOWS UP**
```
localhost ~ # cgpt show /dev/sda
...
      4096     32768       2  Label: "KERN-A"
                              Type: ChromeOS kernel
                              UUID: D176DC60-81F1-654E-8953-E3D28019738C
                              Attr: priority=3 tries=0 successful=1
...
     36864     32768       4  Label: "KERN-B"
                              Type: ChromeOS kernel
                              UUID: F1A2C65C-CC22-FF4A-A8BC-67BA233F3D40
                              Attr: priority=0 tries=15 successful=0
...
  12369920     32768       6  Label: "KERN-C"
                              Type: ChromeOS kernel
                              UUID: B6954485-4295-9749-956A-C315B01FB684
                              Attr: priority=0 tries=15 successful=0
```

The priority determines the order in which the BIOS tries to find a valid kernel (bigger is higher, zero means don't even try). The tries field is decremented each time the BIOS tries to boot it, and if it's zero, the kernel is considered invalid (this lets us boot new images without looping forever if they don't work). The successful field overrides the tries field, but is only set by the OS once it's up and running.

Let's change the priority of KERN-C to 5:

```
cgpt add -i 6 -P 5 -T 1 -S 0 /dev/sda
```

This makes KERN-C the highest priority, but only gives us one chance to boot it. That way if it doesn't work, we're not completely stuck.

If you reboot now, you should come up in Ubuntu!  Note that Computer Science Standard Answer #1 applies: It Works For Me&#8482;

If something went wrong and Ubuntu crashes or you powered off, the tries field for KERN-C will have been decremented to 0 and you'll fall back to booting Chrome OS.

Assuming that Ubuntu booted and you could log in, go to Applications->Accessories->Terminal to get a shell, and run

```
sudo cgpt add -i 6 -P 5 -S 1 /dev/sda
```

This will mark the Ubuntu kernel as valid, so it will continue to boot next time.

Now you can switch back and forth between the official Chrome OS release and Ubuntu just by flipping the dev-mode switch. Going from dev-mode to normal mode erases STATE (/dev/sda1), but much more quickly. Going from normal to dev-mode again would normally do a slow erase of /dev/sda1, but since we're booting Ubuntu that doesn't happen.

This works because although KERN-C has the highest priority, it isn't signed by Google. In dev-mode that's okay, but in normal mode it will be rejected by the BIOS. Since we've set the successful flag to 1, the BIOS won't mark it invalid but will just skip it each time. This makes the normal-mode boot time slightly longer, but only by a second or two. 

Of course you could also switch between images from within dev-mode just by manually setting the priorities with cgpt before rebooting.

Note that if the normal image autoupdates, it will probably change the kernel priorities so that Image-C is no longer the highest and the next time you switch to dev mode, you will
  a) have a long wait, 
  b) still be running Chrome OS, and 
  c) have to use cgpt to raise the KERN-C priority again. 

But, because autoupdate only switches between Image-A and Image-B, the Ubuntu kernel and rootfs shouldn't be affected.

---

### Post by C.S.Cameron on 2010-12-23
I've only been running chromeos on my Eee PC.
With the Hexxeh image I ran sudo apt-get update ubuntu-desktop.
It seemed to run OK but it ran out of space.
When I tried to expand the partitions gparted would crash.

---

### Post by ~~Tito~~ on 2010-12-24
The CR-48 has 16gb on an internal SSD. This is a dual booting method. The install should have about 6gb free space, and thats plenty for a small linux box.

EDIT: I meant there is 6gb available to install too. Which is plenty for a small linux box.

---

### Post by okdok on 2010-12-24
@Tito,

Replying to this thread using 10.10 Netbook edition from my CR-48. Everything worked out of the box as you detailed. I can confirm that it works for me too! :D

Thanks for taking the time to organize the mashup in a sensible way. I had no difficulty whatsoever.

Look forward to enjoying my dual boot while testing the Chrome OS and keeping another productive foot in my Ubuntu environment.

---

### Post by ~~Tito~~ on 2010-12-24
Awesome! :D

Have you had any luck in getting the touch pad to work correctly?

---

### Post by dizzysoul on 2010-12-25
I seem to be stuck on the following part:
```
cgpt create test.bin
```I'm able to:

[LIST]
[*]Connect to my linux desktop using ssh user@host.
[*]Successfully scp /usr/bin/cgpt into the /var/chroot/bin/cgpt directory.
[*]chroot to that directory, see the 'cgpt' file and set permissions.
[/LIST]
However, when I try to call on 'cgpt' as a command, I get:
```
bash: cgpt: command not found

```

EDIT: I found the problem. Apparently, there's a typo in one of the commands used in the original post. Replace:

```
scp /usr/bin/cgpt user@ubuntuHost:/var/chroot/bin/cgpt
```
With:
```
scp /usr/bin/cgpt user@ubuntuHost:/var/chroot/bin
```

The former places cgpt inside the '/var/chroot/bin/cgpt' directory, which is wrong. It's suppsed to be inside the '/var/chroot/bin' directory. 
I'll leave my post here as a reference, in case others run into the same problem I did![FONT=monospace]
[/FONT]

---

### Post by okdok on 2010-12-25
> **~~Tito~~ said:**
> Awesome! :D

Have you had any luck in getting the touch pad to work correctly?

Ahhh, the touchpad.. 8-[

In it's current state at initial load, it can be finicky. Once I located the best places on the pad to use for 'left-click', 'right-click', and 'scroll' all was reasonable considering my expectations.

That being said, I would like either 1. see if I can get it to respond identical to the inputs in Chrome OS. or 2. get it to be a bit better on response and performance. 

Meh; I am a happy camper at the moment. Batter life seems great and most of my goals have been achieved considering I sync most of my stuff in the cloud.

I am considering the thought of buying a larger SSD and using say DD to clone the current drive to a larger one. Either that or increasing the overall volume size by utilizing the SD slot. Thoughts?

---

### Post by dizzysoul on 2010-12-25
> **okdok said:**
> Ahhh, the touchpad.. 8-[

In it's current state at initial load, it can be finicky. Once I located the best places on the pad to use for 'left-click', 'right-click', and 'scroll' all was reasonable considering my expectations.

That being said, I would like either 1. see if I can get it to respond identical to the inputs in Chrome OS. or 2. get it to be a bit better on response and performance. 

Meh; I am a happy camper at the moment. Batter life seems great and most of my goals have been achieved considering I sync most of my stuff in the cloud.

I am considering the thought of buying a larger SSD and using say DD to clone the current drive to a larger one. Either that or increasing the overall volume size by utilizing the SD slot. Thoughts?

I'm replying to you using my CR48 running 10.10. That guide was extremely helpful!

I want to host my rootfs.bin and the two .sh files in a torrent, so that people can download it and skip 90% of the installation process. It would be even better if I could image the entire drive without physically taking it out of the computer (even though it's pretty easy to do). How would you apply the image to a vanilla cr48? Does chromeos and it's limited linux back-end have some way of overwriting everything with another drive image?

I'm looking to upgrade the SSD as well, however the existing SSD is pretty small, so I think I would need to buy an SSD that has a removable cover and fits on a single PCB.

Also, the CR48 seems to have bluetooth hardware (which Ubuntu picked up), but I don't think there's any way to utilize the bluetooth in chromeos. Maybe in a future update? I'm also looking to configure the verizon 3g modem within Ubuntu. Does anyone have any luck with that?

---

### Post by ~~Tito~~ on 2010-12-25
> **dizzysoul said:**
> I seem to be stuck on the following part:
```
cgpt create test.bin
```I'm able to:

[LIST]
[*]Connect to my linux desktop using ssh user@host.
[*]Successfully scp /usr/bin/cgpt into the /var/chroot/bin/cgpt directory.
[*]chroot to that directory, see the 'cgpt' file and set permissions.
[/LIST]
However, when I try to call on 'cgpt' as a command, I get:
```
bash: cgpt: command not found

```

EDIT: I found the problem. Apparently, there's a typo in one of the commands used in the original post. Replace:

```
scp /usr/bin/cgpt user@ubuntuHost:/var/chroot/bin/cgpt
```
With:
```
scp /usr/bin/cgpt user@ubuntuHost:/var/chroot/bin
```

The former places cgpt inside the '/var/chroot/bin/cgpt' directory, which is wrong. It's suppsed to be inside the '/var/chroot/bin' directory. 
I'll leave my post here as a reference, in case others run into the same problem I did![FONT=monospace]
[/FONT]
Ahhhhhh, I will fix that right away! Thanks!

---

### Post by ~~Tito~~ on 2010-12-25
> **dizzysoul said:**
> I'm replying to you using my CR48 running 10.10. That guide was extremely helpful!

I want to host my rootfs.bin and the two .sh files in a torrent, so that people can download it and skip 90% of the installation process. It would be even better if I could image the entire drive without physically taking it out of the computer (even though it's pretty easy to do). How would you apply the image to a vanilla cr48? Does chromeos and it's limited linux back-end have some way of overwriting everything with another drive image?

I'm looking to upgrade the SSD as well, however the existing SSD is pretty small, so I think I would need to buy an SSD that has a removable cover and fits on a single PCB.

Also, the CR48 seems to have bluetooth hardware (which Ubuntu picked up), but I don't think there's any way to utilize the bluetooth in chromeos. Maybe in a future update? I'm also looking to configure the verizon 3g modem within Ubuntu. Does anyone have any luck with that?

Hmmm, would't the roofs.bin have to be set up generically not with your own info? Like your name and such? I was thinking of pulling the touch pad drivers and loads of other stuff from the chrome OS, and merging it with ubuntu and making everything work 100%. Then I could install ubuntu over the whole SSD. Then when ever I needed chrome os, it would be simple since I could restore everything with the restore stick. Anyone down to experiment with me? I have little knowledge in linux driver and kernal mods, I am willing to be the guinea pig(recovery stick can save us).

---

### Post by okdok on 2010-12-25
> **~~Tito~~ said:**
> Hmmm, would't the roofs.bin have to be set up generically not with your own info? Like your name and such? I was thinking of pulling the touch pad drivers and loads of other stuff from the chrome OS, and merging it with ubuntu and making everything work 100%. Then I could install ubuntu over the whole SSD. Then when ever I needed chrome os, it would be simple since I could restore everything with the restore stick. Anyone down to experiment with me? I have little knowledge in linux driver and kernal mods, I am willing to be the guinea pig(recovery stick can save us).

Count me in. While I am going to be integrating the testing of Chrome OS into my development team and using this hardware to test and provide feedback, I am completely on board with  expanding size on the SSD provided I can roll into Chrome using either the SD or USB slots. 

Let me know how I can help. I am especially interested in the touch-pad improvements.. :P

---

### Post by ~~Tito~~ on 2010-12-25
> **okdok said:**
> Count me in. While I am going to be integrating the testing of Chrome OS into my development team and using this hardware to test and provide feedback, I am completely on board with  expanding size on the SSD provided I can roll into Chrome using either the SD or USB slots. 

Let me know how I can help. I am especially interested in the touch-pad improvements.. :P

Did you make a recovery stick? That really eliminates all need for worrys. ;) {edit} misread what you meant. if we use the whole SSD then chrome can be restored via the recovery stick anytime, but if we wanted Ubuntu again we would probably have to repartition and such and then install it again.

What we could do is have someone with kernal knowledge so they can break down the kernal, then someone else with driver knowledge etc. .then we can see what we don't have on a regular linux install the push what we need, then viola, perfect ubuntu. Then we can partition it just for ubuntu and then we can go on out merry way with out ultra awesome CR-48's. Then we can expand from there, like how the community grows and stuff.

The main thing that will probably be hardest is the row of special keys at the top. We might have to change something deep to make them work 100%.

---

### Post by pheonix7117 on 2010-12-25
With regards to the top row of buttons: 
They're currently picked up as Esc and F1-F10, and the fake caps lock is seen as a Super_L or Mod4 key. In light of that, I used the keyboard shortcut Mod4+F8/F9/F10 for mute, lower, and raise volume. 

For the brightness keys, I tried using xbacklight to change the brightness, but found that binding keyboard shortcuts to "xbacklight -dec/inc 10" didn't work for some reason. My workaround was the following quick and dirty python script:
[http://pastebin.com/gDEvFjua](http://pastebin.com/gDEvFjua)
To use it, bind a keyboard shortcut for raising the brightness (I'm using Mod4+F7) to run this script with the argument "up".
For example: /home/user/pyChangeBrightness.py up
And for lowering brightness: /home/user/pyChangeBrightness.py dn
Don't forget to replace "user" with your username, assuming you've saved the script in your home directory as pyChangeBrightness.py
I do find that it normally takes a few more times to raise the brightness the same level as decreasing it, but it's probably a bug in my script. Also, the script will take a preset brightness level to change from, but that's irrelevant for this use.

The rest of the top row of keys I'm just using as regular F1-F6 keys without any extra use.

What I'm really interested in is getting the touchpad working. Right now I have it working so far as moving the mouse normally, tap to left click, 'hard' clicking on it anywhere NOT near the bottom right corner is left click, and 'hard' clicking it near the bottom right corner is right click. No scrolling, no multi-touch. Has anyone gotten further, and if so, how?
I was trying to use the synaptics-dkms package from [https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch) because of this bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all) and specifically comments #115 and #116 (I'm pulling this all from [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch) ) but because it's based on dkms, it needs to recompile the kernel modules after installation. With our setup on the CR-48, we're using the Chrome OS kernel and I haven't found a way to install the headers for it.
The other option is to somehow port the Synaptics driver from Chrome OS (which is the proprietary driver 'syntp' that Synaptics is selling to OEMs), which is *mostly* located under /opt/Synaptics in Chrome OS (with a few other files here and there, run ```
find / | grep -i syn
``` to find them all)
*phew* So that's what all my investigating has led to. Either trying to install the linux-headers for the Chrome OS kernel in Ubuntu, or porting the 'syntp' driver from Chrome OS to Ubuntu.
Any other ideas? I've hit a road block :)
:popcorn:

---

### Post by pheonix7117 on 2010-12-25
> **okdok said:**
> Ahhh, the touchpad.. 8-[

In it's current state at initial load, it can be finicky. Once I located the best places on the pad to use for 'left-click', 'right-click', and 'scroll' all was reasonable considering my expectations.

That being said, I would like either 1. see if I can get it to respond identical to the inputs in Chrome OS. or 2. get it to be a bit better on response and performance. 


Does this mean you have scrolling working on the touchpad in Ubuntu??? If so, please share! :D

---

### Post by suprman2020 on 2010-12-26
Thank for this excellent guide. I somehow managed to install Maverick. Would installing updates break the Ubuntu install?

---

### Post by pheonix7117 on 2010-12-26
I've been doing Ubuntu updates without a problem, but I suspect any kernel related updates won't really have an effect. I haven't noticed any Chrome OS updates but then again they're supposed to be automagic in the background :D But if it does update....

> **~~Tito~~ said:**
> Note that if the normal image autoupdates, it will probably change the kernel priorities so that Image-C is no longer the highest and the next time you switch to dev mode, you will
  a) have a long wait, 
  b) still be running Chrome OS, and 
  c) have to use cgpt to raise the KERN-C priority again. 

But, because autoupdate only switches between Image-A and Image-B, the Ubuntu kernel and rootfs shouldn't be affected.

So either way you should be ok.

---

### Post by ~~Tito~~ on 2010-12-26
I didn't create the guide, only make one by combining two that where very good and making installation easy and simple. I added in a few details and worded a few things differently, all credit goes to the people who made them. There are links at the top of the guide with the sources.

---

### Post by dizzysoul on 2010-12-26
> **~~Tito~~ said:**
> Hmmm, would't the roofs.bin have to be set up generically not with your own info? Like your name and such? I was thinking of pulling the touch pad drivers and loads of other stuff from the chrome OS, and merging it with ubuntu and making everything work 100%. Then I could install ubuntu over the whole SSD. Then when ever I needed chrome os, it would be simple since I could restore everything with the restore stick. Anyone down to experiment with me? I have little knowledge in linux driver and kernal mods, I am willing to be the guinea pig(recovery stick can save us).

That's exactly what I did, using user/password. Once a person loads into the Ubuntu installation, they just have to configure their timezone, keyboard layout (if not English), and create their own account.

Also, I've been reading that there's is a bug with Ubuntu 10.10 detecting Synaptic touchpads. They get registered as PS/2 devices with touchpad options disabled. This seems to be exactly what I'm experiencing. Because of this, multi-touch is disabled, and tap-to-click is stuck on by default.

Another problem: When I normally click a mouse button, my finger rolls forward slightly to overcome the tactile resistance of the button 'click'. Because the mouse buttons and touchpad are combined, this means every time I 'click' it causes the mouse cursor to move away from what I'm clicking on!

Usually devices have something called a 'dead-zone' or 'sensitivity' where slight movements that are below a certain thresh hold get discarded. This eliminates jerkiness and smooths out the controls. However, because my touchpad isn't being detected properly, the sensitivity controls are scaled back to accommodate a physical mouse, which isn't what I'm using.

Is anyone else experiencing these issues? The touchpad seems to be the biggest, if not only problem on the cr48 laptop. Fixing the touchpad issues would be awesome!

Edit: This is what information I could gather about the trackpad. The issues I'm experienced are documented here:
[http://ubuntuforums.org/showthread.php?t=1554974](http://ubuntuforums.org/showthread.php?t=1554974)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1546730](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1546730)
[http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad](http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad)
[http://ubuntuforums.org/showthread.php?t=1607361](http://ubuntuforums.org/showthread.php?t=1607361)
[http://ubuntuforums.org/showthread.php?t=1640557](http://ubuntuforums.org/showthread.php?t=1640557)

There seems to be a dirty fix to this solution described [here]("http://ubuntuforums.org/showpost.php?p=9824402&postcount=4"):
> 1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

The problem being, Ubuntu doesn't boot off the cr48 using Grub, but the chromeos boot loader! Is there any way to incorporate these changes into the chromeos bootloader, or into Ubuntu itself?

---

### Post by pheonix7117 on 2010-12-26
> **pheonix7117 said:**
> 

What I'm really interested in is getting the touchpad working. Right now I have it working so far as moving the mouse normally, tap to left click, 'hard' clicking on it anywhere NOT near the bottom right corner is left click, and 'hard' clicking it near the bottom right corner is right click. No scrolling, no multi-touch. Has anyone gotten further, and if so, how?
I was trying to use the synaptics-dkms package from [https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch) because of this bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all) and specifically comments #115 and #116 (I'm pulling this all from [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch) ) but because it's based on dkms, it needs to recompile the kernel modules after installation. With our setup on the CR-48, we're using the Chrome OS kernel and I haven't found a way to install the headers for it.
The other option is to somehow port the Synaptics driver from Chrome OS (which is the proprietary driver 'syntp' that Synaptics is selling to OEMs), which is *mostly* located under /opt/Synaptics in Chrome OS (with a few other files here and there, run ```
find / | grep -i syn
``` to find them all)
*phew* So that's what all my investigating has led to. Either trying to install the linux-headers for the Chrome OS kernel in Ubuntu, or porting the 'syntp' driver from Chrome OS to Ubuntu.
Any other ideas? I've hit a road block :)
:popcorn:

With regards to the touchpad: 

[INDENT]- From what I can tell, it's being detected as a "PS/2 Synaptics TouchPad" as opposed to the usual "SynPS/2 Synaptics TouchPad". This is due to the CR-48 using a newer synaptics touchpad. Currently, if I understand correctly, Chrome OS is using the proprietary Synaptics driver called 'syntp', currently only shipped to Synaptics' OEM customers.

- According to the beginning of this article [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad), you can normally get around this issue to some degree by following the link [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all) and taking a peek at comments #115 and #116 (although if you look further on there are more up-to-date packages available for download). However, this package 'synaptics-dkms' depends on dkms and having the linux-headers package for the currently running kernel installed. As this dual-boot scenario depends on our using the Chrome OS kernel to boot, I have no found a way to install linux-headers successfully in such a way that 'synaptics-dkms' will succeed.

- The options I see are:
[INDENT]-Port the proprietary 'syntp' driver from Chrome OS to Ubuntu (and I don't know how easy that may be) or
-Install the correct linux-headers for the Chrome OS kernel to get the synaptics-dkms package installed correctly or
-Wait until someone creates an open source driver to replace the proprietary 'syntp' driver (since I have no idea how to do it :D)[/INDENT][/INDENT]

If anyone has any suggestions, please let me know! I eagerly await any progress :-)
:popcorn:

---

### Post by okdok on 2010-12-26
> **~~Tito~~ said:**
> Did you make a recovery stick? That really eliminates all need for worrys. ;) {edit} misread what you meant. if we use the whole SSD then chrome can be restored via the recovery stick anytime, but if we wanted Ubuntu again we would probably have to repartition and such and then install it again.

What we could do is have someone with kernal knowledge so they can break down the kernal, then someone else with driver knowledge etc. .then we can see what we don't have on a regular linux install the push what we need, then viola, perfect ubuntu. Then we can partition it just for ubuntu and then we can go on out merry way with out ultra awesome CR-48's. Then we can expand from there, like how the community grows and stuff.

The main thing that will probably be hardest is the row of special keys at the top. We might have to change something deep to make them work 100%.

Yep, I kept that recovery image on one of my USB keys... ;)

I'm a little weak on the Kernel side, but would not mind doing a deep dive. That being said if someone already has that lane, I can work the driver side confidently.

As mentioned by a note I just glanced at, I concur that the top row is still functioning as traditional F keys.

---

### Post by okdok on 2010-12-26
> **pheonix7117 said:**
> What I'm really interested in is getting the touchpad working. Right now I have it working so far as moving the mouse normally, tap to left click, 'hard' clicking on it anywhere NOT near the bottom right corner is left click, and 'hard' clicking it near the bottom right corner is right click. No scrolling, no multi-touch. Has anyone gotten further, and if so, how?

I was trying to use the synaptics-dkms package from [https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch) because of this bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+index?comments=all) and specifically comments #115 and #116 (I'm pulling this all from [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20True%20Multitouch) ) but because it's based on dkms, it needs to recompile the kernel modules after installation. With our setup on the CR-48, we're using the Chrome OS kernel and I haven't found a way to install the headers for it.
The other option is to somehow port the Synaptics driver from Chrome OS (which is the proprietary driver 'syntp' that Synaptics selling to OEMs), which is *mostly* located under /opt/Synaptics in Chrome OS (with a few other files here and there, run ```
find / | grep -i syn
``` to find them all)
*phew* So that's what all my investigating has led to. Either trying to install the linux-headers for the Chrome OS kernel in Ubuntu, or porting the 'syntp' driver from Chrome OS to Ubuntu.
Any other ideas? I've hit a road block :)
:popcorn:

I like the idea of porting the drivers. I suspect that we could directly port them from one image to the other without much difficulty. I am on holiday through Wed but will see what I can do on the touchpad driver now.

---

### Post by okdok on 2010-12-26
> **pheonix7117 said:**
> Does this mean you have scrolling working on the touchpad in Ubuntu??? If so, please share! :D

I'd did, but as I am on holiday and balancing other duties as assigned I forgot. I recall doing this while holding a left click area of the pad and another motion. I can't replicate at the moment and currently rely on the keyboard. Will be sure to post when I remember or even better, update the driver. ;)

---

### Post by pheonix7117 on 2010-12-26
Ahah! Your reply gave me hope. If you install the package 'gpointing-device-settings' it will add a menu entry to System > Preferences called Pointing Devices.
It *should* list a device called "PS/2 Synaptics TouchPad".
What I did was enable wheel emulation and changed it to button 3 (which I believe is right click) and enabled vertical scroll. I left timeout and inertia default (inertia seems to be 0, timeout is fairly short) and left middle button emulation unchecked. This enables a regular right click when doing a 'hard' click in the bottom right corner without lingering, and if you hold the right click you can swipe a finger up or down to scroll. Granted, this isn't using the touchpad driver at all as this is supposed to be used for regular mice, but it's a start for getting by for now.

---

### Post by dizzysoul on 2010-12-26
I've had one hell of a time trying to get the brightness keys to work.

10.10 still doesn't give the option of binding keys to increase/decrease brightness, even though gnome-power-manager works just fine through the GUI. xbacklight works for decreasing the brightness, but not increasing it.

I've googled extensively for information on how to hook into gnome-power-manager with hotkeys or scripts, to no avail.

Edit: Apparently, xbacklight -inc 10 doesn't work, but 'xbacklight -inc 15' does work, even though it's still only 10% increments (not 15%), and 'xbacklight -dec 10' works like normal. Weird bug.

You can bind 'xbacklight -inc 15' and xbacklight -dec 10' to the F6 and F7 keys using xbindkeys:

```
sudo apt-get install xbindkeys xbindkeys-config
xbindkeys --defaults > ~/.xbindkeysrc
xbindkeys-config

```
The last line launches a graphical interface where you can bind any key combination to execute a command.

---

### Post by pheonix7117 on 2010-12-26
> **pheonix7117 said:**
> 
For the brightness keys, I tried using xbacklight to change the brightness, but found that binding keyboard shortcuts to "xbacklight -dec/inc 10" didn't work for some reason. My workaround was the following quick and dirty python script:
[http://pastebin.com/gDEvFjua](http://pastebin.com/gDEvFjua)
To use it, bind a keyboard shortcut for raising the brightness (I'm using Mod4+F7) to run this script with the argument "up".
For example: /home/user/pyChangeBrightness.py up
And for lowering brightness: /home/user/pyChangeBrightness.py dn
Don't forget to replace "user" with your username, assuming you've saved the script in your home directory as pyChangeBrightness.py
I do find that it normally takes a few more times to raise the brightness the same level as decreasing it, but it's probably a bug in my script. Also, the script will take a preset brightness level to change from, but that's irrelevant for this use.


This should take care of it. You can make custom shortcuts in Keyboard Shortcuts (System>Preferences>Keyboard Shortcuts). I just assigned the fake caps lock (comes up as Mod4) + F6/F7 as stated above using the script. Feel free to ask for more details if you have trouble getting it working. Works fine for me except making it brighter takes a few extra taps :)

Sidenote: I had the same issue with xbacklight -inc so I worked around it in this script by first getting the current brightness (xbacklight -get) and using xbacklight -set to set it manually to a higher brightness.

---

### Post by dizzysoul on 2010-12-26
> **pheonix7117 said:**
> This should take care of it. You can make custom shortcuts in Keyboard Shortcuts (System>Preferences>Keyboard Shortcuts). I just assigned the fake caps lock (comes up as Mod4) + F6/F7 as stated above using the script. Feel free to ask for more details if you have trouble getting it working. Works fine for me except making it brighter takes a few extra taps :)

Sidenote: I had the same issue with xbacklight -inc so I worked around it in this script by first getting the current brightness (xbacklight -get) and using xbacklight -set to set it manually to a higher brightness.

In case you missed my edit, xbacklight is bugged but 'xbacklight -inc 15' should work instead, and it still uses 10% increments.

---

### Post by pheonix7117 on 2010-12-26
If you look at my script, it uses xbacklight -get/-set, never does it use -dec or -inc because I had issues with those parameters as you seemed to.

---

### Post by dugopark on 2010-12-27
> **~~Tito~~ said:**
> The CR-48 has 16gb on an internal SSD. This is a dual booting method. The install should have about 6gb free space, and thats plenty for a small linux box.

Thanks for posting mash up guide on installing Ubuntu Tito.  It was helpful.

One thing I noticed was that the install I have only has 1.5G of free space after installing the OS.  What does the command 'df -h' show in your installation?

Mine shows the following, which is nowher near the 6gb free space that you mentioned.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             5.0G  3.2G  1.5G  69% /
devtmpfs              944M  244K  943M   1% /dev
none                  944M  284K  944M   1% /dev/shm
none                  944M  124K  944M   1% /var/run
none                  944M     0  944M   0% /var/lock

What was the size of your final rootfs.bin file?

---

### Post by ~~Tito~~ on 2010-12-27
> **dugopark said:**
> Thanks for posting mash up guide on installing Ubuntu Tito.  It was helpful.

One thing I noticed was that the install I have only has 1.5G of free space after installing the OS.  What does the command 'df -h' show in your installation?

Mine shows the following, which is nowher near the 6gb free space that you mentioned.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             5.0G  3.2G  1.5G  69% /
devtmpfs              944M  244K  943M   1% /dev
none                  944M  284K  944M   1% /dev/shm
none                  944M  124K  944M   1% /var/run
none                  944M     0  944M   0% /var/lock

What was the size of your final rootfs.bin file?

I read the size wrong, I am getting similar results.

---

### Post by dragonmule on 2010-12-28
To make an image from an existing full hard disk just do e.g.

sudo dd if=/dev/sda of=/media/external-drive/imagefile.img

I've done this with the beta and developer Chrome images on Cr-48, don't see why it wouldn't work with ubuntu install.

---

### Post by exodeity on 2010-12-28
Hey guys, I don't really mean to hijack the thread here, but I've been trying to install ubuntu on this for the past few days, and I've restarted each guide, and always get to this part:

mount /dev/sda7 /tmp/urfs
mount: you must specify the filesystem type

I've tried them all, and I've looked around google and found this thread, hopefully you guys can call me an idiot and tell me a quick fix.

Thanks, appreciate it.

---

### Post by pheonix7117 on 2010-12-28
> **dragonmule said:**
> To make an image from an existing full hard disk just do e.g.

sudo dd if=/dev/sda of=/media/external-drive/imagefile.img

I've done this with the beta and developer Chrome images on Cr-48, don't see why it wouldn't work with ubuntu install.
Are you suggesting to try this to make it soley Ubuntu? I don't see how the BIOS would boot it though, as it's a custom BIOS if I understand correctly....

> **exodeity said:**
> Hey guys, I don't really mean to hijack the thread here, but I've been trying to install ubuntu on this for the past few days, and I've restarted each guide, and always get to this part:

mount /dev/sda7 /tmp/urfs
mount: you must specify the filesystem type

I've tried them all, and I've looked around google and found this thread, hopefully you guys can call me an idiot and tell me a quick fix.

Thanks, appreciate it.

Quick check, did you dd the rootfs image to /dev/sda7? Apologizes if this seems to be rudimentary, but sometimes the simplest things are the issue ;)

---

### Post by exodeity on 2010-12-28
> **pheonix7117 said:**
> 
Quick check, did you dd the rootfs image to /dev/sda7? Apologizes if this seems to be rudimentary, but sometimes the simplest things are the issue ;)

The command to get the rootfs onto sda7, was:

"ssh USER@HOST cat /path/to/rootfs.bin | dd of=/dev/sda7" (with my info, obviously :P)

So, unless that's not the right way to do it, I'm pretty sure I did. Not too familiar with linux as far as deep terminal stuff, I use ubuntu pretty much daily, but rarely use the terminal, less it's just a few apt-gets :P

Thanks.

---

### Post by pheonix7117 on 2010-12-28
I suspect that either the dd became corrupted because of a network blip or something like that, or a mistake happened along the way in the chroot or VirtualBox.... I actually installed Ubuntu from the guide at [https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48) and not the guide in this thread, but you say you have the same error using either one?

---

### Post by exodeity on 2010-12-28
> **pheonix7117 said:**
> I suspect that either the dd became corrupted because of a network blip or something like that, or a mistake happened along the way in the chroot or VirtualBox.... I actually installed Ubuntu from the guide at [https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48) and not the guide in this thread, but you say you have the same error using either one?

Well, the first one I tried was the chromium projects one, I cam across this one, and the only real difference I see is using a usb drive, I've tried both ways, and it always gives me that error when I get to the mounting part.

---

### Post by pheonix7117 on 2010-12-28
Unfortunately I'm not really sure where the error may have happened....The most efficient way to trouble shoot it is to go completely back to a clean slate and try it again, making sure there are no typos or anything....I would suggest toggling the developer's switch as well to hopefully (maybe?) do a clean of the stateful partition, though I don't think you have to go as far as to re-partition it back to the original sizes. I WOULD make sure that they are set up properly, however.
As it is more the 'official' guide (and the one I used succesfully) I would recommend using the Chromium guide (not that the guide in this thread is doubtful, just in your cases the less variables the better).
A couple 'doh!' checks to make sure it isn't something silly:
Did you use the 32bit Ubuntu iso?
When you created the Chromium chroot, did you use the 'minimal' layout or the 'full' layout? I believe I had to use the full one because the minimal didn't have something necessary, causing it to fail, but I could be remembering the situation incorrectly. It may be good to 'sync' the Chromium build environment again to make sure it's up to date, as well.
Are you sure the partition sizes are exactly correct?
(This is an ABSOLUTE dummy question, though it would be nice if this was this issue :D) Were you running the SSH command on the CR-48? I'm assuming you were as this issue happened while using the USB dongle from this guide as well, however can't hurt to check :-/

Any more detailed information you can provide would be wonderful :-) Maybe a "cgpt show /dev/sda" as root from Chrome OS:
```
# cgpt show /dev/sda > /home/chronos/cgpt_dump.txt
```

Good luck! I hope we can sort this out as Ubuntu opens up a lot of doors on the CR-48 :)

---

### Post by xak on 2010-12-28
> **dizzysoul said:**
> There seems to be a dirty fix to this solution described [here]("http://ubuntuforums.org/showpost.php?p=9824402&postcount=4"):


The problem being, Ubuntu doesn't boot off the cr48 using Grub, but the chromeos boot loader! Is there any way to incorporate these changes into the chromeos bootloader, or into Ubuntu itself?

I tried adding these boot flags (i8042.reset i8042.nomux i8042.nopnp i8042.noloop) to the input file (foo.6) used by **make_dev_ssd.sh**, but it didn't seem to make any difference. I restored my KERNEL-C partition back to the way it was before. Oh well, worth a try.

---

### Post by exodeity on 2010-12-28
> **pheonix7117 said:**
> Unfortunately I'm not really sure where the error may have happened....The most efficient way to trouble shoot it is to go completely back to a clean slate and try it again, making sure there are no typos or anything....I would suggest toggling the developer's switch as well to hopefully (maybe?) do a clean of the stateful partition, though I don't think you have to go as far as to re-partition it back to the original sizes. I WOULD make sure that they are set up properly, however.
As it is more the 'official' guide (and the one I used succesfully) I would recommend using the Chromium guide (not that the guide in this thread is doubtful, just in your cases the less variables the better).
A couple 'doh!' checks to make sure it isn't something silly:
Did you use the 32bit Ubuntu iso?
When you created the Chromium chroot, did you use the 'minimal' layout or the 'full' layout? I believe I had to use the full one because the minimal didn't have something necessary, causing it to fail, but I could be remembering the situation incorrectly. It may be good to 'sync' the Chromium build environment again to make sure it's up to date, as well.
Are you sure the partition sizes are exactly correct?
(This is an ABSOLUTE dummy question, though it would be nice if this was this issue :D) Were you running the SSH command on the CR-48? I'm assuming you were as this issue happened while using the USB dongle from this guide as well, however can't hurt to check :-/

Any more detailed information you can provide would be wonderful :-) Maybe a "cgpt show /dev/sda" as root from Chrome OS:
```
# cgpt show /dev/sda > /home/chronos/cgpt_dump.txt
```

Good luck! I hope we can sort this out as Ubuntu opens up a lot of doors on the CR-48 :)

Thanks for the trouble shooting, appreciate it, this has been buggin' the crap out of me for a while now >.<

Also, I got the whole chromium OS, synced it, updated it, etc. I then made a chroot, did all that that first time. Second time, I deleted it all, started over, re-downloaded the whole thing, it's been an arduous journey for me, haha =/.

As for the cgpt;

```
     start      size    part  contents
         0         1          PMBR (Boot GUID: BD41DC2C-3B89-D04A-BF8C-5F3D870FC175)
         1         1          Pri GPT header
         2        32          Pri GPT table
    266240  12103680       1  Label: "STATE"
                              Type: Linux data
                              UUID: 29005688-5888-CF45-B9C2-564910781A70
      4096     32768       2  Label: "KERN-A"
                              Type: ChromeOS kernel
                              UUID: 6BD053C8-4440-5B4E-9528-A4F8CAE9C458
                              Attr: priority=2 tries=0 successful=1
  27082752   4194304       3  Label: "ROOT-A"
                              Type: ChromeOS rootfs
                              UUID: 5D21829E-16B0-614E-9F98-3DF614F77BAE
     36864     32768       4  Label: "KERN-B"
                              Type: ChromeOS kernel
                              UUID: C75B4998-DB71-D44D-A667-418967379828
                              Attr: priority=3 tries=0 successful=1
  22888448   4194304       5  Label: "ROOT-B"
                              Type: ChromeOS rootfs
                              UUID: 3BC44314-75A2-8546-9EBF-408AB876D8A2
  12369920     32768       6  Label: "KERN-C"
                              Type: ChromeOS kernel
                              UUID: 1E333F57-73DF-7349-8123-4F7E50C6F4CE
                              Attr: priority=0 tries=15 successful=0
  12402688  10485760       7  Label: "ROOT-C"
                              Type: ChromeOS rootfs
                              UUID: 271017F7-2C42-5B40-9278-37176688AE42
     69632     32768       8  Label: "OEM"
                              Type: Linux data
                              UUID: 2DB6F91B-21B0-054D-A3E1-BE436A11C3B5
        36         1       9  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 12A2BD2B-96BE-B74E-A57F-AC481351450F
        37         1      10  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 820E32F6-E6EB-C940-A310-29886F8CBED0
        38         1      11  Label: "reserved"
                              Type: ChromeOS reserved
                              UUID: 9DA903CF-F147-6340-8C0E-65FDBF584A6A
    233472     32768      12  Label: "EFI-SYSTEM"
                              Type: EFI System Partition
                              UUID: BD41DC2C-3B89-D04A-BF8C-5F3D870FC175
  31277199        32          Sec GPT table
  31277231         1          Sec GPT header

```

Note: Too be honest, I'm hoping it's something simple, and just my own stupidity, which if it is, sorry for wasting your time :P

Thanks for the help, I do appreciate it! :D

---

### Post by damis648 on 2010-12-28
Don't waste your time with the chroot, you really don't need it. You can get the required scripts from here:
[make_dev_ssd.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/make_dev_ssd.sh&q=package:chromiumos&d=0")
[common.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/common.sh&q=package:chromiumos&d=0")

Anything else can be done without the chroot. Just copy the cgpt binary to another computer if you need that.

---

### Post by okdok on 2010-12-28
> **exodeity said:**
> Hey guys, I don't really mean to hijack the thread here, but I've been trying to install ubuntu on this for the past few days, and I've restarted each guide, and always get to this part:

mount /dev/sda7 /tmp/urfs
mount: you must specify the filesystem type

I've tried them all, and I've looked around google and found this thread, hopefully you guys can call me an idiot and tell me a quick fix.

Thanks, appreciate it.

During my install, I came across this error and simply specified the FS type in the command line for the mount assuming I used ext2.

---

### Post by ~~Tito~~ on 2010-12-29
If you guys make a Recovery Stick, any problems that arise during the install process can be wiped away. It literally takes 5 min to restore and return where you left off.

---

### Post by suprman2020 on 2010-12-29
Any progress on getting the touchpad to work properly?

---

### Post by pheonix7117 on 2010-12-29
> **suprman2020 said:**
> Any progress on getting the touchpad to work properly?

Not that I know of, all I came up with is what I said in previous posts, and the temporary work around of an emulated mouse wheel....

---

### Post by exodeity on 2010-12-29
> **okdok said:**
> During my install, I came across this error and simply specified the FS type in the command line for the mount assuming I used ext2.

Tried that, but when I did it errors out with:

"wrong fs type, bad option, bad superblock on /dev/sda7 missing codepage or helper program, or other error in some cases useful info is found is syslog, try dmesg | tail or so"

The cmd I used was "mount -t ext2 /dev/sda7 /tmp/urfs"

---

### Post by ~~Tito~~ on 2010-12-29
> **damis648 said:**
> Don't waste your time with the chroot, you really don't need it. You can get the required scripts from here:
[make_dev_ssd.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/make_dev_ssd.sh&q=package:chromiumos&d=0")
[common.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/common.sh&q=package:chromiumos&d=0")

Anything else can be done without the chroot. Just copy the cgpt binary to another computer if you need that.

I Specify in the guide where to get those files, they are in the exact place you linked.

---

### Post by okdok on 2010-12-29
> **suprman2020 said:**
> Any progress on getting the touchpad to work properly?

I myself have not had time but will try this week and report back. 

Note another user reported progress using a specific Chrome build. While I have not read to far into the response, this may be useful: 

[http://ubuntuforums.org/showpost.php?p=10290380&postcount=392](http://ubuntuforums.org/showpost.php?p=10290380&postcount=392)

---

### Post by okdok on 2010-12-29
> **exodeity said:**
> Tried that, but when I did it errors out with:

"wrong fs type, bad option, bad superblock on /dev/sda7 missing codepage or helper program, or other error in some cases useful info is found is syslog, try dmesg | tail or so"

The cmd I used was "mount -t ext2 /dev/sda7 /tmp/urfs"

Sorry about that. I recall the error, but will have to try and reproduce this week. I'll report back.

---

### Post by Krogen on 2010-12-29
I also can't seem to mount the image for some reason. 

```

localhost usb # mount /dev/sda7 /tmp/urfs
mount: you must specify the filesystem type

localhost usb # mount -t ext2 /dev/sda7 /tmp/urfs
mount: wrong fs type, bad option, bad superblock on /dev/sda7
missing codepage or helper program, or other error
In some cases useful info is found in syslong - try dmesg | tail or so

localhost usb # dmesg | tail
(other stuff here)
[ 3248.672083] VFS: Can't find an ext2 filesystem on dev sda7

```

I have followed the guide on [sites.google.com]("https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48"). I used VirtualBox OSE from Mint package manager (should be the same as Ubuntu...), and the partition inside the image was ext2. I am on 64-bit Linux Mint 9.

Also, I tried transferring the image using a flash drive and through Wi-Fi. Same issue.

---

### Post by dizzysoul on 2010-12-29
Apparently there's an automated script that installs everything for you [here]("http://www.chromeoslounge.com/cr-48-chrome-notebook/548-easy-way-install-ubuntu-cr-48-a.html").

---

### Post by dizzysoul on 2010-12-29
I'm having a hell of a time trying to disable tap to click.

Apparently the scripts in /usr/share/X11/xorg.conf.d are being completely ignored, and gconf-editor is of no use either. Installing gsynaptics doesn't do anything, and I'm not sure what else to do sans building an entire xorg.conf file (which could break everything).

Has anyone had any luck in taming the wild touchpad? At least getting configurations to stick? How do you check which driver or config file is being used by the device?

---

### Post by pheonix7117 on 2010-12-29
> **dizzysoul said:**
> I'm having a hell of a time trying to disable tap to click.

Apparently the scripts in /usr/share/X11/xorg.conf.d are being completely ignored, and gconf-editor is of no use either. Installing gsynaptics doesn't do anything, and I'm not sure what else to do sans building an entire xorg.conf file (which could break everything).

Has anyone had any luck in taming the wild touchpad? At least getting configurations to stick? How do you check which driver or config file is being used by the device?

The reason you can't get anything to stick is that it all depends on the kernel loading the synaptics driver for the touchpad. As of yet, it isn't so the only settings that will likely stick are generic mouse settings from System>Preferences>Mouse or from the pointing-device-settings package I mentioned earlier :-/

---

### Post by dizzysoul on 2010-12-29
> **pheonix7117 said:**
> The reason you can't get anything to stick is that it all depends on the kernel loading the synaptics driver for the touchpad. As of yet, it isn't so the only settings that will likely stick are generic mouse settings from System>Preferences>Mouse or from the pointing-device-settings package I mentioned earlier :-/

Is there any to inject some of the touchpad settings into the generic mouse setting? Like tap_to_click to false or something similar?

---

### Post by Krogen on 2010-12-30
I'm not sure if this was mentioned already.

There is a program (daemon) out there called mouseemu (package is available in synaptic). It lets you bind keys. For example,

lCtrl + tap = right click
lAlt + slideTap = scroll

It works really well, if only the sensitivity was a tad better. I got used to it extremely easily. It can be easily reconfigured for other keys.

Some lines have to be uncommented:
file: /etc/default/mouseemu
```
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
SCROLL="-scroll 56"              # Alt key
```

> **dizzysoul said:**
> Apparently there's an automated script that installs everything for you [here]("http://www.chromeoslounge.com/cr-48-chrome-notebook/548-easy-way-install-ubuntu-cr-48-a.html").

Worked like a charm... But dang, that download was big!

---

### Post by pheonix7117 on 2010-12-30
Thanks for the tip about mouseemu! I agree about the sensitivity though, is there any way to adjust it?

By the way, no need to tap to activate the shortcuts. I have scrolling using mouseemu by holding Alt and just sliding my finger across the touchpad.

---

### Post by DarkNovaGamer on 2010-12-30
> **okdok said:**
> I myself have not had time but will try this week and report back. 

Note another user reported progress using a specific Chrome build. While I have not read to far into the response, this may be useful: 

[http://ubuntuforums.org/showpost.php?p=10290380&postcount=392](http://ubuntuforums.org/showpost.php?p=10290380&postcount=392)

In regards to my post regarding progress. 

It seems that the kernel that you use from your current Chromium/Chrome OS install to put into KERN-C is what caused my touchpad to work better in Ubuntu.

I had the best outcome using the 27th's kernel from the link below, the latest I've tried is the 28th's which caused the touchpad to flip out when used for me.

I hope this helps even in the slightest. :)


[http://www.duh.org/chromiumos/cr-48/](http://www.duh.org/chromiumos/cr-48/)

---

### Post by pheonix7117 on 2010-12-30
> **DarkNovaGamer said:**
> In regards to my post regarding progress. 

It seems that the kernel that you use from your current Chromium/Chrome OS install to put into KERN-C is what caused my touchpad to work better in Ubuntu.

I had the best outcome using the 27th's kernel from the link below, the latest I've tried is the 28th's which caused the touchpad to flip out when used for me.

I hope this helps even in the slightest. :)


[http://www.duh.org/chromiumos/cr-48/](http://www.duh.org/chromiumos/cr-48/)

Interesting, as the driver loaded in Chrome OS for the touchpad is (presumably) not even used when booting Ubuntu, so I'm not sure what would help the touchpad. Perhaps a fall-back driver built into the Chrome OS kernel? I (think) I'm currently using 28th's kernel, will have to check, but it hasn't been flipping out, just is sort of a pain to use....

---

### Post by DarkNovaGamer on 2010-12-30
> **pheonix7117 said:**
> Interesting, as the driver loaded in Chrome OS for the touchpad is (presumably) not even used when booting Ubuntu, so I'm not sure what would help the touchpad. Perhaps a fall-back driver built into the Chrome OS kernel? I (think) I'm currently using 28th's kernel, will have to check, but it hasn't been flipping out, just is sort of a pain to use....

Perhaps I should rephrase what I stated.

When I said flip out, I should have said when attempting to do a two-finger click/tap it would cause the pointer to go haywire.

I'm currently about to test out the 30th's image. I will post my results afterwards. :)

---

### Post by pheonix7117 on 2010-12-30
When I try two finger anything, it just sort of ignores the second finger, no haywire business. Granted, I still have to check which image I'm using haha.

Good luck with the 30th's image :-)

---

### Post by DarkNovaGamer on 2010-12-31
The kernel from the 30th worked well as well. :)

---

### Post by ~~Tito~~ on 2010-12-31
Hmm so what you are saying is, new kernel = multitouch for ubuntu?

---

### Post by DarkNovaGamer on 2010-12-31
> **~~Tito~~ said:**
> Hmm so what you are saying is, new kernel = multitouch for ubuntu?

Well. It gives me the default touchpad features right now. Which is progress over the default 'Chrome OS' kernel.

---

### Post by ~~Tito~~ on 2010-12-31
> **DarkNovaGamer said:**
> Well. It gives me the default touchpad features right now. Which is progress over the default 'Chrome OS' kernel.

What do you mean?

---

### Post by DarkNovaGamer on 2010-12-31
> **~~Tito~~ said:**
> What do you mean?

Whenever I used the kernel from the official image, I didn't have the 'touchpad' option under mouse in the System > Preferences (I believe) menu. While now I do, which allows me to enable things such as horizontal scrolling or two finger scrolling. :)

---

### Post by pheonix7117 on 2010-12-31
What is this new kernel based on? Is it an update for Chrome OS (thus leading to an updated kernel for Ubuntu)? Or is it a custom kernel...? I'm envious of your multitouch abilities! :-)

---

### Post by DarkNovaGamer on 2010-12-31
> **pheonix7117 said:**
> What is this new kernel based on? Is it an update for Chrome OS (thus leading to an updated kernel for Ubuntu)? Or is it a custom kernel...? I'm envious of your multitouch abilities! :-)
 
Uncertain. I'd gladly upload the image or host it elsewhere for others to use/play around with it if I could manage to figure out how to get it off the drive.
 
Any ideas? I'm still rather new to Linux so forgive me, as I am trying. I've tried using the following command,
 
```
dd if=/dev/sda2 of=/home/chronos/user/Downloads/kernel.bin
```
 
I've tried kernel.bin, .iso, .zip, all will not work. The command is successful of course but the file itself doesn't give me anything I can use. I cannot mount the partition either, not even with Ubuntu. So if someone could provide me with a method of ripping the kernel off of /dev/sda2, that'd be great.

---

### Post by suprman2020 on 2010-12-31
How would I go about trying the image from the 30th?

---

### Post by suprman2020 on 2010-12-31
> **DarkNovaGamer said:**
> In regards to my post regarding progress. 

It seems that the kernel that you use from your current Chromium/Chrome OS install to put into KERN-C is what caused my touchpad to work better in Ubuntu.

I had the best outcome using the 27th's kernel from the link below, the latest I've tried is the 28th's which caused the touchpad to flip out when used for me.

I hope this helps even in the slightest. :)


[http://www.duh.org/chromiumos/cr-48/](http://www.duh.org/chromiumos/cr-48/)


Does using one of these recovery images delete the Ubuntu install?

---

### Post by ~~Tito~~ on 2010-12-31
Those images work by functioning like the recovery stick. So everything is erased then reinstalled, I believe that you have to redo everything all over again, but when you install the kernal and such things will be different.

---

### Post by DarkNovaGamer on 2010-12-31
When you use a recovery stick to put either the original version or a custom version of Chrome/Chromium OS, it wipes the SSD and repartitions it to what it would be by default (without Ubuntu).

---

### Post by pheonix7117 on 2010-12-31
> **DarkNovaGamer said:**
> Uncertain. I'd gladly upload the image or host it elsewhere for others to use/play around with it if I could manage to figure out how to get it off the drive.
 
Any ideas? I'm still rather new to Linux so forgive me, as I am trying. I've tried using the following command,
 
```
dd if=/dev/sda2 of=/home/chronos/user/Downloads/kernel.bin
```
 
I've tried kernel.bin, .iso, .zip, all will not work. The command is successful of course but the file itself doesn't give me anything I can use. I cannot mount the partition either, not even with Ubuntu. So if someone could provide me with a method of ripping the kernel off of /dev/sda2, that'd be great.

One issue could be that you're trying to extract the data from a mounted partition, while using it. Perhaps boot into Ubuntu to create the .bin file? I'm also not 100% sure here but just tossing ideas around. <-- DISCLAIMER :D

---

### Post by DarkNovaGamer on 2010-12-31
> **pheonix7117 said:**
> One issue could be that you're trying to extract the data from a mounted partition, while using it. Perhaps boot into Ubuntu to create the .bin file? I'm also not 100% sure here but just tossing ideas around. <-- DISCLAIMER :D

Some suggestions are better than none. I just did a new recovery on it, reinstalling Ubuntu.

Will try some more things with it and report back.

---

### Post by DarkNovaGamer on 2010-12-31
The problem is GParted doesn't even recognize a filesystem on /dev/sda2 or any KERN-A/B/C. It says its unformatted or unknown. :|

---

### Post by suprman2020 on 2010-12-31
DarkNovaGamer, everytime you try a new Chrome OS recovery image you have to setup Ubuntu again? Do you use that script and download the files every time? Or is there a shortcut?

---

### Post by DarkNovaGamer on 2010-12-31
> **suprman2020 said:**
> DarkNovaGamer, everytime you try a new Chrome OS recovery image you have to setup Ubuntu again? Do you use that script and download the files every time? Or is there a shortcut?

Yes everytime I have to reinstall Ubuntu. Currently I just run the script provided by someone else.

```
 sudo wget -O - http://goo.gl/DlmZS | sh -
```

Run that, it will do some things then reboot, run it again, it'll start to download things and then reboot when its done. If it boots Ubuntu sucessfully then you can run the following command to make sure Ubuntu boots again next time.

```
sudo cgpt add -i 6 -P 5 -S 1 /dev/sda
```

Afterwards you can use my script to switch back and forth without having to switch the developers switch on and off.

[http://ubuntuforums.org/showpost.php?p=10291341&postcount=393](http://ubuntuforums.org/showpost.php?p=10291341&postcount=393)

---

### Post by ~~Tito~~ on 2011-01-02
Hey guys check this out [http://forums.somethingawful.com/showthread.php?threadid=3373297&pagenumber=6&perpage=40#post386324138](http://forums.somethingawful.com/showthread.php?threadid=3373297&pagenumber=6&perpage=40#post386324138)

Its a method on installing the default bios. Meaning, we can just install ubuntu on the whole drive, with out needing the Chrome OS kernel. Check it out. Also, refer to Endagdet or Gizmodo.

Anyone dare to experiment? I will read up on methods to return to the original state, and look up prices on bigger SSD's that will fit on the CR-48, I could possibly have a reasonable Dual Boot with more space. It also appears that installing a linux distro the normal way allows the trackpad drivers to function.
This:
[http://forums.somethingawful.com/showthread.php?threadid=3373297&pagenumber=6&perpage=40#post386349604](http://forums.somethingawful.com/showthread.php?threadid=3373297&pagenumber=6&perpage=40#post386349604)

---

### Post by pheonix7117 on 2011-01-02
This looks quite exciting :-) I'm assuming there is only space for one HD in the cr-48....I wonder if it would accept >2GB of RAM? :)
I may experiment in the coming week, though first I may try getting the touchpad working from this guide:
[http://cr-48.wikia.com/wiki/Getting_the_Trackpad_Working_in_Ubuntu](http://cr-48.wikia.com/wiki/Getting_the_Trackpad_Working_in_Ubuntu)

---

### Post by ~~Tito~~ on 2011-01-02
> **pheonix7117 said:**
> This looks quite exciting :-) I'm assuming there is only space for one HD in the cr-48....I wonder if it would accept >2GB of RAM? :)
I may experiment in the coming week, though first I may try getting the touchpad working from this guide:
[http://cr-48.wikia.com/wiki/Getting_the_Trackpad_Working_in_Ubuntu](http://cr-48.wikia.com/wiki/Getting_the_Trackpad_Working_in_Ubuntu)

OOOO! NICE!! Hmmm, I meant buying a bigger SSD for the CR-48 and then installing. Check the tear down guides for the CR-48. I am not to sure if I recall seeing a ram slot though.

---

### Post by ~~Tito~~ on 2011-01-03
Okay, so I installed the OEM BIOS. WOW! It is awesome. ATM I am installing Linux Mint to it! Really cool, USB booting and all. Just take your time and such when opening your precious CR-48.

---

### Post by pheonix7117 on 2011-01-03
Any other precious tips for cracking it open? :)

---

### Post by dizzysoul on 2011-01-03
The stock BIOS seems to fix a lot of driver issues. I installed Windows 7 on my cr48, and I was able to download the latest drivers for all my devices, including the synaptics touchpad. I now have full multi-touch and gesture support, and everything works beautifully.


My next step is to buy a 32GB SDHC card and use that for extra storage, and so I can dual-boot windows and ChromeOS.

---

### Post by ~~Tito~~ on 2011-01-06
> **dizzysoul said:**
> The stock BIOS seems to fix a lot of driver issues. I installed Windows 7 on my cr48, and I was able to download the latest drivers for all my devices, including the synaptics touchpad. I now have full multi-touch and gesture support, and everything works beautifully.


My next step is to buy a 32GB SDHC card and use that for extra storage, and so I can dual-boot windows and ChromeOS.

The bios has nothing to do with the drivers. The problem we where having with the drivers was using the Chrome OS kernel.

---

### Post by ~~Tito~~ on 2011-01-06
> **pheonix7117 said:**
> Any other precious tips for cracking it open? :)

Open it from the front then go to the back from where the hinges are. :guitar:

---

### Post by cookieofdoom on 2011-01-06
Whenever I try to run```
sh ./make_dev_ssd.sh --partitions '6' --save_config foo

```I get this message: ```
/common.sh't open .
```and nothing seems to happen. Any ideas?

EDIT: I got tired of this problem and decided to flash the BIOS. My problem is gone now. Ubuntu runs really well on the CR-48.

---

### Post by dugopark on 2011-01-06
> **~~Tito~~ said:**
> Okay, so I installed the OEM BIOS. WOW! It is awesome. ATM I am installing Linux Mint to it! Really cool, USB booting and all. Just take your time and such when opening your precious CR-48.

In the somethingawful forum, the original poster mentioned that he couldn't get the 3G modem working in windows.  Were you able to get the 3G modem working in Mint or Ubuntu after the BIOS update?

---

### Post by dugopark on 2011-01-07
> **dugopark said:**
> In the somethingawful forum, the original poster mentioned that he couldn't get the 3G modem working in windows.  Were you able to get the 3G modem working in Mint or Ubuntu after the BIOS update?

I installed Mint 10 on the cr-48, and it looks like it doesn't recognize the 3G modem.

I got the two finger scrolling working by installing the synaptics-dkms package as suggested earlier in this thread:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/156](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/156)

At this point, the cr-48 is getting to be a full fledged linux laptop that I can use for general computing.

---

### Post by pheonix7117 on 2011-01-08
Was this after re-flashing the BIOS to stock or still with the Google Chrome OS BIOS?

---

### Post by dugopark on 2011-01-08
> **pheonix7117 said:**
> Was this after re-flashing the BIOS to stock or still with the Google Chrome OS BIOS?

This was after flashing the bios to the stock version.  When I tried using synaptics-dkms with the chrome bios, two finger scrolling didn't work.

The other thing is to make sure you have the gsynaptics package installed.  You can find it in the package manager.

I had some trouble at first with my palms always messing with the touchpad while typing, but tweaking the settings in the "pointing device settings" resolved most of them.

---

### Post by dugopark on 2011-01-10
> **dugopark said:**
> This was after flashing the bios to the stock version.  When I tried using synaptics-dkms with the chrome bios, two finger scrolling didn't work.

The other thing is to make sure you have the gsynaptics package installed.  You can find it in the package manager.

I had some trouble at first with my palms always messing with the touchpad while typing, but tweaking the settings in the "pointing device settings" resolved most of them.

In order to get hibernation working correctly, I had to re-install the OS but do manual partitioning this time to make sure that the swap partition was at least 2G (2048MB).

After the re-install, I found that you don't need synaptics-dkms for two finger scrolling.  You only need the gsynaptics package installed.

---

### Post by pheonix7117 on 2011-01-10
That would make sense (referring to the hibernation bit) because I think the swap file/partition has to be at least the size of the RAM so that the state can be saved properly. With such a small amount of space to begin with I may forgo the hibernation option to gain that extra 2gb of space. Or I may try something crazy and try to hibernate it to a SD card or flash drive that's 2gb large and just do a 'swapon' on the card/drive when it's plugged in :D I wonder if that would even work....

---

### Post by dizzysoul on 2011-01-12
> **~~Tito~~ said:**
> The bios has nothing to do with the drivers. The problem we where having with the drivers was using the Chrome OS kernel.

The problem, ultimately, was that we were forced to use the Chrome OS kernel, because we had no control over the BIOS or boot loader.

With the stock BIOS installed, you can use GRUB to boot into Ubuntu using the standard kernel, which supports the required parameters for getting the synaptic touchpad drivers to work properly.

---

### Post by ~~Tito~~ on 2011-01-17
> **dugopark said:**
> In the somethingawful forum, the original poster mentioned that he couldn't get the 3G modem working in windows.  Were you able to get the 3G modem working in Mint or Ubuntu after the BIOS update?
I haven't tried that yet, I haven't even tested the modem in Chrome OS.

---

### Post by danaff37 on 2011-02-07
I've got ubuntu installed on my cr48, but I have no wireless...  it says no drivers installed.  I've tried it twice with the same results.  Any ideas on what I can do to resolve this issue?  I'm somewhat a linux newb, but not horribly so.

---

### Post by pheonix7117 on 2011-02-07
> **danaff37 said:**
> I've got ubuntu installed on my cr48, but I have no wireless...  it says no drivers installed.  I've tried it twice with the same results.  Any ideas on what I can do to resolve this issue?  I'm somewhat a linux newb, but not horribly so.

Are you using the BIOS google shipped with it or the original (stock) BIOS that is now available?

---

### Post by avatarmonkeykirby on 2011-02-11
Hello, I'm sorry to interrupt this discussion but I'm not sure where else to go.

I've done everything up to the point where the two shell scripts (common.sh and make_dev_ssd.sh) are required. When I try to use make_dev, I get an error

```

: not foundssd.sh: 9:
/common_minimal.sh.

```

I interpreted this to mean that it could not find the required shell script file "common_minimal.sh", so I found the copy hosted in the same directory as the other files ([common_minimal.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/common_minimal.sh&q=package:chromiumos&d=0")). I duplicated this file and moved it into the same directory as the others, however I still get the same error. Is there something I'm overlooking or not doing? Thanks.

Edit: Also if this is just a weird new version of these files, would it be possible for someone to send me the older versions?

---

### Post by avatarmonkeykirby on 2011-02-13
> **avatarmonkeykirby said:**
> Hello, I'm sorry to interrupt this discussion but I'm not sure where else to go.

I've done everything up to the point where the two shell scripts (common.sh and make_dev_ssd.sh) are required. When I try to use make_dev, I get an error

```

: not foundssd.sh: 9:
/common_minimal.sh.

```

I interpreted this to mean that it could not find the required shell script file "common_minimal.sh", so I found the copy hosted in the same directory as the other files ([common_minimal.sh]("http://codesearch.google.com/codesearch/p?hl=en#wZuuyuB8jKQ/src/platform/vboot_reference/scripts/image_signing/common_minimal.sh&q=package:chromiumos&d=0")). I duplicated this file and moved it into the same directory as the others, however I still get the same error. Is there something I'm overlooking or not doing? Thanks.

Edit: Also if this is just a weird new version of these files, would it be possible for someone to send me the older versions?

Found a the solution to my own problem. I changed my CR-48's package channel from beta to developer and it loaded loaded working scripts in it's own /usr/shared/vboot/bin folder.

---

### Post by avatarmonkeykirby on 2011-02-17
Me again. As far as this track pad business goes, it seems to still be able to click and right click as it did before. For scrolling, mine works if I drag a single finger up and down the right edge of the pad. Anyone else able to do this?

---

### Post by inimitablesikh on 2011-02-27
> **avatarmonkeykirby said:**
> Me again. As far as this track pad business goes, it seems to still be able to click and right click as it did before. For scrolling, mine works if I drag a single finger up and down the right edge of the pad. Anyone else able to do this?

HOw do you get scrolling with the trackpad working? Also, I have xbindkeys installed, but it's not working...any ideas?

---

