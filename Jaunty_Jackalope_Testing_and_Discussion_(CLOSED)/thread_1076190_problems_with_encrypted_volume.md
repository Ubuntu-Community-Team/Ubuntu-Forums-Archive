---
title: "problems with encrypted volume"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skeve on 2009-02-21
Hi!
After updating my system this morning I cannot start it.
My harddisk is encrypted (lvm+luks) and after booting I see a list of these messages:
/sys/devices/virtual/block/dm-0 (#######)
and constant disk activity.
Does anyone know what is going on? Is it safe to interrupt the process or should I wait?
Thank you

---

### Post by AlterEgo on 2009-02-21
me too. I guess there's something wrong with one of the latstes updates. I decide to let it run for now (many hours).

I'll keep you posted on progress.

---

### Post by skeve on 2009-02-21
I'd been waiting for hours, but the proccess seemed to be endless... I interrupted it and managed to boot from Clonezilla disk. It appears at least the data on the harddrive  is safe.

---

### Post by skeve on 2009-02-22
ok, it seems to me that the problem is connected with this bug: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/332270](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/332270)

---

### Post by AlterEgo on 2009-02-22
I found that bug report too. I did not help me much though.
Bug # 325690 offered some help.

I got back to a working situation by downgrading to kernel 2.6.28-7-generic.
This allows me to use ctrl-alt-del to get into my system.
Then, I downgraded to udev-137-1 and dmsetup 2:1.02.27-3ubuntu2, followed by update-initramfs -c -k all

Layout: 
/boot (ext3)
enctypted LVM container, containing / (ext3); /home (ext3) and swap)

---

### Post by skeve on 2009-02-23
I downgraded too: dmsetup 1.02.27-4ubuntu3 and udev 137-2, so now kernel 2.6.28-8 boots ok
I used Clonezilla disk to boot and then mountd my encrypted lvm volume, chroot-ed into the old system and then downgraded

---

### Post by AlterEgo on 2009-02-23
Ik found chrooting impossible until I realised ext4 wasn't part of any bootdisk I used......

---

### Post by WorldTripping on 2009-02-23
Afternoon,

I too am having this problem.

Could someone please tell me how I go about downgrading so that I can at least get to my lvm.

Cheers.

---

### Post by AlterEgo on 2009-02-23
> **WorldTripping said:**
> Afternoon,
Could someone please tell me how I go about downgrading so that I can at least get to my lvm.
Cheers.

I'll try.

1) boot into kernel 2.7.28-7. If the Grub bootmenu is hidden, you can make it visible by pressing the "escape' button just after startup. If you do not have an older kernel than 2.6.28-8 available in the Grub menu, you have to 'chroot' into your system. This procedure is not difficult, but you'll have to Google for help.
2) after booting the right kernel, you'll notice the neverending harddisk activity. Briefly press ctrl-alt-del, and you will end up in your system. Probably, the GUI is not functioning properly, so open a console screen by pressing ctrl-alt-F2. Log in as root, or login as yourself and use sudo for every following step.
3) Check if your root system is mounted read/write (it is probably mounted readonly) by typing 'mount' and check the "/" line. It should look similar to this: /dev/mapper/volgroup-root on / type ext3 (rw,relatime,errors=remount-ro).
The RW indicates that all is well. RO means it is mounted readonly. "mount -o remount, rw / " will change this into read/write.
4) Find the right files: they should be here: /var/cache/apt/archives/udev_137-1_amd64.deb and /var/cache/apt/archives/dmsetup_1.02.27-3ubuntu2_amd64.deb (assuming amd64 is your architecture).
Install them by typing 'dpkg -i /path/to/the/file.deb'
5) If you do not have these files, then you have to get them, which requires a working networking connection. My networking was not functioning. I had to: '/etc/init.d/networking restart' (this gave an error message), followed by 'ifconfig eth0 down', and 'ifconfig eth0 up'. Now download these files: 'wget [http://launchpadlibrarian.net/21574508/udev_137-1_amd64.deb'](http://launchpadlibrarian.net/21574508/udev_137-1_amd64.deb') and  'wget [http://launchpadlibrarian.net/18745354/dmsetup_1.02.27-3ubuntu2_amd64.deb](http://launchpadlibrarian.net/18745354/dmsetup_1.02.27-3ubuntu2_amd64.deb)' (again assuming AMD64 is your architecture) and install them by typing 'dpkg -i /path/to/the/file.deb'.
6) Reboot into the same kernel you succesfully booted into in step 1, and your system shold be up and running again.

If you have any troubles, please be very specific in explaining where things go wrong. I'll try and help you as much as I can.

Regards, AE

---

### Post by WorldTripping on 2009-02-23
OK.

Thanks for the reply this is as far as I have gotten.

So I set if off running in 2.6.28-8-generic (recovery) as this is the only kernel I have.

I get to 'Enter Passphrase' which decrypts the disk with the message;
'key slot 0 unlocked.'

Then blinking '_'
Eventually messages come back saying;

'Command Successful'
'File descriptor 3 left open'
'2 logical volume(s) in volume group "laptop-dell" now active'
'cryptsetup: sda1_crypt setup successfully'

Then back doing its unstoppable merry scrolling text.

However if I edit the grub text to read;
'kernel  /vmlinux-2.6.28-8-generic ro single'

It does everything up to to the unstoppable part, instead saying;
'Done.'
'Begin: Waiting for root file system... ...'
'Gave up waiting for root device'

More info that it could not find root or boot args or some modules and that it is dropping into a shell.

And now I'm in BusyBox v1.10.2

I guess that this is the bit where I have to start reading up on 'chroot' ??

Cheers.

---

### Post by WorldTripping on 2009-02-23
BINGO !

I have a solution that works for me.

Booted using a live CD.

Noticed that my Grub partition still had all the old Linux 2.6.28x-generic heahers in it.

They were just not showing on my boot menu.

Manually changed menu.lst, booted into a recovery mode as I guessed that X would need repairing.

Worked like a treat and I got straight back into my lvm.

Only issue now is that 'kcryptd' and 'udevd' are running like crazy and hogging the CPU.

But that resolution is tomorrows problem.

Cheers for all the inputs.

---

