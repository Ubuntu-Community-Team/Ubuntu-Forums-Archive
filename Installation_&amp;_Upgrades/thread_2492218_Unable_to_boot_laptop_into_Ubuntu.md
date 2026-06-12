---
title: "Unable to boot laptop into Ubuntu"
date: 2023-11-03
forum: Installation &amp; Upgrades
---

### Post by gigmx on 2023-11-03
I have a framework laptop that I was running Ubuntu on by itself, this morning when I fired it up it was stuck in this startup loop so I booted up a liveUSB and tried boot-repair, I got a message saying: Error: NVram is locked (Ubuntu not found in efibootmgr). I've been trying different things all day but I'm just not sure what to try now. I was going to try and reset the CMOS battery next. Can someone help me out?

[https://paste.ubuntu.com/p/5RbXfkv9SP/](https://paste.ubuntu.com/p/5RbXfkv9SP/)

```
lsblk
      
loop0                   7:0    0     3G  1 loop  /rofs
loop1                   7:1    0  63.4M  1 loop  /snap/core20/1974
loop2                   7:2    0     4K  1 loop  /snap/bare/5
loop3                   7:3    0  73.9M  1 loop  /snap/core22/858
loop4                   7:4    0 237.2M  1 loop  /snap/firefox/2987
loop5                   7:5    0 349.7M  1 loop  /snap/gnome-3-38-2004/143
loop6                   7:6    0 485.5M  1 loop  /snap/gnome-42-2204/120
loop7                   7:7    0  91.7M  1 loop  /snap/gtk-common-themes/1535
loop8                   7:8    0  12.3M  1 loop  /snap/snap-store/959
loop9                   7:9    0   452K  1 loop  /snap/snapd-desktop-integration/83
loop10                  7:10   0  53.3M  1 loop  /snap/snapd/19457
sda                     8:0    1  58.6G  0 disk  
&#9492;&#9472;sda1                  8:1    1  58.6G  0 part  /cdrom
nvme0n1               259:0    0   1.8T  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part  
&#9500;&#9472;nvme0n1p2           259:2    0   1.7G  0 part  /media/ubuntu/981636c1-7348-4408-9ed7-9a5c54bd1587
&#9492;&#9472;nvme0n1p3           259:3    0   1.8T  0 part  
  &#9492;&#9472;myvolume          253:0    0   1.8T  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0   1.8T  0 lvm   /media/ubuntu/43978b0f-6039-421e-8bff-07f4fbdad6df
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   1.9G  0 lvm
```

---

### Post by MAFoElffen on 2023-11-04
Please go back to your first post, and edit it > Select Advanced Edit > Select the raw output with your mouse > Seclet the "#" Icon to wrap the selected text witin CODE Tags... Forum Policy.

You have Encrypted LVM. You never unlocked your LUKS volume...
```

blkid (filtered): ______________________________________________________________

NAME                  FSTYPE      UUID                                   PARTUUID                             LABEL       PARTLABEL
sda                                                                                                                       
&#9492;&#9472;sda1                vfat        13FA-1B04                              04634ffe-01                          UBUNTU 22_0 
nvme0n1                                                                                                                   
&#9500;&#9472;nvme0n1p1           vfat        2276-8B14                              1477bb0c-9bbf-49bd-87a6-717c2768ec58             EFI System Partition
&#9500;&#9472;nvme0n1p2           ext4        981636c1-7348-4408-9ed7-9a5c54bd1587   2c30d61e-a7b9-463a-9abc-2f77cfba2edf             
&#9492;&#9472;nvme0n1p3           crypto_LUKS 7ba602fe-b5a3-470f-a236-28b06fc0da8d   acd88685-fc45-4b5d-b9f2-3752dc7f043e             
  &#9492;&#9472;myvolume          LVM2_member XlGyMd-g7ol-hhhS-X9pv-CZgA-Jk2v-37RbyX                                                  
    &#9500;&#9472;vgubuntu-root   ext4        43978b0f-6039-421e-8bff-07f4fbdad6df                                                    
    &#9492;&#9472;vgubuntu-swap_1 swap        3b175b36-6f54-4c00-933d-833adcbb7896                                                    

```
Do this please, while booted from a LiveUSB:
```

sudo su -
[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
# If the above does not prompt back "UEFI Firmware mode", then stop right here and post back!
apt update
apt install -y cryptsetup-initramfs

LUKS_VDEV="/dev/nvme0n1p3"
cryptsetup open $LUKS_VDEV dm_crytpt-0
# If you do not get your LUKS Volume unlocked, stop here and post back!

vgchange -a y
LVM_LUKS=$(lvscan | grep 'root' | awk '/ACTIVE/ {print $2}' | sed 's/\x27//g' )

mount $LVM_LUKS /mnt
# If this has any error, stop here and post back

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env /bin/bash --login
mount -a
# If this has error, stop here and post back

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-initramfs -c -k all
update-grub
exit
umount /mnt
reboot

```
Do the commands one-by-one. If, at any time you get an error, stop right there, an post back here to say so, or to ask questions...

---

### Post by gigmx on 2023-11-04
Ok here's an error I got:

```

root@ubuntu:~# LUKS_VDEV="/dev/nvme0n1p3"
root@ubuntu:~# cryptsetup open $LUKS_VDEV
Command requires device and mapped name as arguments.

```

---

### Post by MAFoElffen on 2023-11-04
Edited code in Post #2...

---

### Post by gigmx on 2023-11-04
This one line doesn't seem to execute properly. I'm not sure, it gives me a > prompt:

```
root@ubuntu:~# vgchange -a y
  2 logical volume(s) in volume group "vgubuntu" now active
root@ubuntu:~# LVM_LUKS=$(lvscan | awk '/ACTIVE/ {print $2}' | sed 's/\'//g' )
> 
>

```

---

### Post by MAFoElffen on 2023-11-04
What does this say?
```

echo $LVM_LUKS
lvscan
ls /dev/mapper

```

---

### Post by SeijiSensei on 2023-11-04
```
root@ubuntu:~# LVM_LUKS=$(lvscan | awk '/ACTIVE/ {print $2}' | sed 's/\'//g' )
```

The single quotes are not correctly aligned. Try

```
root@ubuntu:~# LVM_LUKS=$(lvscan | awk /ACTIVE/ '{print $2}' | sed 's/\'//g' )
```

That sed command might also be problematic. Try 
```
sed "s/'//g"
```
if the first correction doesn't solve the problem.

---

### Post by MAFoElffen on 2023-11-04
@SeijiSensei --
That fails with all those... But gave me another idea... Thank you.

@gigmx --
Tested. This works:
```

LVM_LUKS=$(lvscan | awk '/ACTIVE/ {print $2}' | sed 's/\x27//g' )

```
Edited in Post #2

---

### Post by gigmx on 2023-11-04
@[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")
When I ran that updated line, it didn't give me an error but no output and then when I tried this next in the list it came back with 'mount bad usage'

```
root@ubuntu:~# LVM_LUKS=$(lvscan | awk '/ACTIVE/ {print $2}' | sed 's/\x27//g' )
root@ubuntu:~# mount $LVM_LUKS /mnt
mount: bad usage
```

@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")
here's the output from those commands:

```
root@ubuntu:~# echo $LVM_LUKS
/dev/vgubuntu/root /dev/vgubuntu/swap_1
root@ubuntu:~# lvscan
  ACTIVE            '/dev/vgubuntu/root' [<1.82 TiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [<1.91 GiB] inherit
root@ubuntu:~# ls /dev/mapper
control  luks-dev  vgubuntu-root  vgubuntu-swap_1
```

---

### Post by MAFoElffen on 2023-11-04
That was me asking for those... LOL

Set this...
```

LVM_LUKS=/dev/vgubuntu/root

```
Then continue
```

mount $LVM_LUKS /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env /bin/bash --login
mount -a

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-initramfs -c -k all
update-grub
exit
umount /mnt
reboot

```

---

### Post by gigmx on 2023-11-05
It went fine until Grub install:

```
root@ubuntu:~# LVM_LUKS=/dev/vgubuntu/root
root@ubuntu:~# mount $LVM_LUKS /mnt
root@ubuntu:~# mount --make-private --rbind /dev  /mnt/dev
root@ubuntu:~# mount --make-private --rbind /proc /mnt/proc
root@ubuntu:~# mount --make-private --rbind /sys  /mnt/sys
root@ubuntu:~# mount --make-private --rbind /run  /mnt/run
root@ubuntu:~# chroot /mnt /usr/bin/env /bin/bash --login
root@ubuntu:/# mount -a
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi \
>     --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
Installation finished. No error reported.
root@ubuntu:/# update-initramfs -c -k all
update-initramfs: Generating /boot/initrd.img-6.1.0-1024-oem
cryptsetup: WARNING: target 'luks-dev' not found in /etc/crypttab
update-initramfs: Generating /boot/initrd.img-6.2.0-34-generic
cryptsetup: WARNING: target 'luks-dev' not found in /etc/crypttab
update-initramfs: Generating /boot/initrd.img-6.2.0-35-generic
cryptsetup: WARNING: target 'luks-dev' not found in /etc/crypttab
root@ubuntu:/#
```

---

### Post by MAFoElffen on 2023-11-05
Dang... Lets see this...
```

grep . /etc/cryptab

```
I came up with luks-dev, becasue there was no way to look into the locked luks container to see that, at that point.

We may have to back out of the chroot, reboot, and when you do it again, unlock the LUKS partition and map it to whatever the cryptab has for it so that works right we you get back to that...

I'll update the commands when we see that from above.

For example:
```

$ grep . /etc/crypttab

dm_crytpt-0 UUID=8f1c625a-a83c-4836-936a-fff0ffbef2e22 none luks

$ ls /dev/mapper

control dm_crypt-0 ubuntu--vg-ubuntu--lv

```

---

### Post by gigmx on 2023-11-06
Here's what I got back:

```
root@ubuntu:/# grep . /etc/crypttab
nvme0n1p3_crypt UUID=7ba602fe-b5a3-470f-a236-28b06fc0da8d none luks,discard
root@ubuntu:/# ls /dev/mapper
control  luks-dev  vgubuntu-root  vgubuntu-swap_1

```

---

### Post by MAFoElffen on 2023-11-06
Here is the amended commands, based on how things are installed on your system:
```

sudo su -
[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
apt update
apt install -y cryptsetup-initramfs
LUKS_VDEV="/dev/nvme0n1p3"
cryptsetup open $LUKS_VDEV nvme0n1p3_crypt
vgchange -a y
LVM_LUKS=/dev/vgubuntu/root
mount $LVM_LUKS /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env /bin/bash --login
mount -a
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-initramfs -c -k all
update-grub
exit
umount /mnt
reboot

```
To reboot and start over to do what you need to do...

---

### Post by gigmx on 2023-11-06
Just to double check, I'm rebooting after I run all those commands right?

---

### Post by gigmx on 2023-11-07
ok I got this error:

[CODEroot@ubuntu:~# LUKS_VDEV="/dev/nvme0n1p3"

root@ubuntu:~# cryptsetup open $LUKS_VDEV nvme0n1p3_crypt

Enter passphrase for /dev/nvme0n1p3: 

Cannot use device /dev/nvme0n1p3 which is in use (already mapped or mounted).
][/CODE]

---

### Post by MAFoElffen on 2023-11-07
LOL. No... Shutdown.

Then boot from cold, to the "Try" on the LiveUSB >  Connect networking. Open browser to get to that last post with the commands. > Open a terminal > Do the commands in order.

---

### Post by gigmx on 2023-11-10
Ok I was able to run all the commands you gave with no problems. When I tried to restart it looks like you fixed all the problems I caused while trying to fix the original problem, but I still have the original problem. Which is it when it boots up, it loads the screen to enter the password to unlock the encrypted drive but then gives me a progress bar saying 'installing updates' and when that finishes it reboots and won't ever boot the actual OS.

---

### Post by MAFoElffen on 2023-11-10
Let's try this... At the Grub2 screen, choose "Advanced Options > Select a kernel menu item that includes "recovery" > It wil ask you to umlock the drive something in between there > At the recovery menu, select network, then root. > At the root prompt, do 
```

apt update
apt upgrade

```
Tell me if there were any errors with that...

Then do this
```

sudo lspci -nnk | grep -A3 -E 'VGA|Display|3D'

```
Write down what it says ad report that please...

---

### Post by gigmx on 2023-11-16
Ok I took pics with my phone of the outputs:

[https://imgur.com/a/UT8Xm1s](https://imgur.com/a/UT8Xm1s)

---

### Post by MAFoElffen on 2023-11-17
Okay. You ave not working DNS, so networking is broken... 

What does this say?
```

sudo systemctl status systemd-resolved.service

```
We need to see why that is not starting

---

### Post by gigmx on 2023-11-23
```

sudo:unable to resolve host trancer: Temporary failure in name resolution
system-resolved.service - Network Name Resolution
    Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset; enabled)
    Active: inactive (dead)
        Docs: man:systemd-resolved.service(8)
        man:org.freedesktop.resolve1(5)
         https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers/
        https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients/

```

I changed my computer name the other day, looks like my hosts file wasn't correct, I fixed that.

---

### Post by MAFoElffen on 2023-11-24
So now it works?

If so, then visit the "Thread Tools" Link in the upper right of the first page of this thread, and mark your thread as 'Solved', so that others can find what worked for you to solve their similar problems.

---

### Post by gigmx on 2023-11-28
Sorry no, I just meant I noticed the host name wasn't correct in the host file, I corrected that. When I boot into the safe mode root shell I still can't apt update or apt upgrade because of the dns issue. 

```


sudo systemctl status systemd-resolved.servicesudo:unable to resolve host trancer: Temporary failure in name resolution
system-resolved.service - Network Name Resolution
    Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset; enabled)
    Active: inactive (dead)
        Docs: man:systemd-resolved.service(8)
        man:org.freedesktop.resolve1(5)
         https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers/
        https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients/
```

And when I boot normally, at the encrypted volume unlock screen if I press esc, I'm seeing:

```

volume group vgaubuntu not found
cannot process volume group

```

If I unlock the volume, it says it's updating and then restarts and just loops.

---

### Post by MAFoElffen on 2023-11-29
> **gigmx said:**
> Sorry no, I just meant I noticed the host name wasn't correct in the host file, I corrected that. When I boot into the safe mode root shell I still can't apt update or apt upgrade because of the dns issue. 

```


sudo systemctl status systemd-resolved.servicesudo:unable to resolve host trancer: Temporary failure in name resolution
system-resolved.service - Network Name Resolution
    Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset; enabled)
    Active: inactive (dead)
        Docs: man:systemd-resolved.service(8)
        man:org.freedesktop.resolve1(5)
         https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers/
        https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients/
```

And when I boot normally, at the encrypted volume unlock screen if I press esc, I'm seeing:

```

volume group vgaubuntu not found
cannot process volume group

```

If I unlock the volume, it says it's updating and then restarts and just loops.

Well yes. If you press <Esc> at the Unlock prompt, you are not unlocking the LUKS container so it fails. That makes sense to you right?

Do this... At the Grub2 menu... Press the <E> key to get into edit mode. <Arrow-Down> to the line that starts with the work 'linux'. <Arrow-Right> to the words "quiet splash". Replace those works with "-- 3". Press the keys <Cntrl><X> to boot. 
Login with your user name and password.

Do this first
```

rm $HOME/.Xauthority
touch $HOME/.Xauthority
chown $USER:$USER $HOME/.Xauthority
chmod 600 $HOME/.Xauthority

```
Reboot and test...

What Graphics GPU does it have?

---

### Post by gigmx on 2023-12-03
edit

the gpu is a mesa intel graphics ADL GT2

it's a 12th gen framework laptop

If i boot into the usb install, I was able to run those .Xauthority commands, and I changed quiet splash to -3. Once I input the encrypted drive password, the only difference is it boots entirely with text and restarts after 30 seconds or so. I see a failed to start network time synchronization error and a failed to start hostname service error with all the boot up text.

---

### Post by MAFoElffen on 2023-12-03
I have to say something of a disclaimer first.

I have lost faith in Intel's Upstream graphics support for 10th through 13th gen GPU's lately. I have a 13th gen that I have had an upstream support case open for over 3 months now, and still ongoing.

Having said that, first do
```

sudo lspci -nnk | grep -A3 -Ei 'VGA|Display|3D'

```
Take a picture with your phone. Post it as an attachment to a post.

---

### Post by gigmx on 2023-12-04
done:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293155&stc=1[/IMG]

Just wondering, if I just grab what I need from the live boot and do a fresh install, how do I avoid this from happening again? I'm still confused as to what the issue is, if it was something I did or what?

On a side note with the usb live boot, I loaded the (safe graphics) option and it bumped my refresh rate to 90. With the regular ubuntu install it capped out at like 45 or 60...

---

### Post by MAFoElffen on 2023-12-04
To implement that, just add i915.modeset=0 to /etc/default/grub, line GRUB_CMDLINE_LINUX_DEFAULT=, after the words "quite splash" (but within the quotation marks)... Then save, exit, and do
```

sudo update-grub

```
To pick up the changes. Then reboot to test.

---

### Post by gigmx on 2023-12-05
ok I hit e at the grub menu and changed the recovery line to rw, loaded into recovery mode and added i915.modeset=0 to the grub file. 

It started installing a bunch of stuff but got hung up on linux-image-6.1.0-1025-oem 95% I gave it 10+ minutes before ctrl-alt-d to restart.

I can only get into one of the recovery options now, the others are giving me "unable to mount root fs on unknown-block(0,0) Here are the errors:

---

### Post by gigmx on 2023-12-10
I was able to run sudo update-grub in one of the recovery boots and I finally boot into the normal ubuntu boot. But it won't go right into it, I have to go through recovery and/or change the grub parameters to rw instead of ro...

---

