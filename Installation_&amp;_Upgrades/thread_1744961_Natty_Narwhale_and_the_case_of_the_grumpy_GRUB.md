---
title: "Natty Narwhale and the case of the grumpy GRUB"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Non-lucky on 2011-04-30
This story starts like so many others with someone who aught to know better attempting to use the built in system upgrade; which of course failed, leaving poor Natty blind without a GUI in sight. Luckily Lynx is a friend to the blind and allowed Natty to download an iso to create a liveCD.

But here is where the story takes a twist: If 11.04 is installed with access to the Internet it goes off without a hitch but then boots to a blinking cursor on a black screen with no other tty open. If 11.04 is installed offline the error

```
The 'grub-efi' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.
```appears.

The system installation is supposed to be going into 4 partitions: 

sda1 formatted for /boot
sda2 swap
sda3 formatted for /
sda4 for /home

With the MBR going on sda

Apparently 11.04 has made some sort of change to GRUB to GRUB2 and now involves and 'EFI' so the older posts may not be as helpful as they should be.

Help?

---

### Post by drs305 on 2011-04-30
If you have had no previous experience or need for EFI, it's possible you are getting this error merely because it is just the first thing the system is trying to be installed.

If it's actually to EFI, you can stop reading here. I don't know much about EFI...

If it's just a generic loading problem and you have the Natty disk, we can try to reinstall Grub 2 by mounting your Ubuntu partitions and reinstalling Grub2.

```
sudo mount /dev/sda3 /mnt
sudo mount /dev/sda4 /mnt/home
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```
Note you do NOT use the partition number in the last command.

Also, the --boot-directory switch is new to Grub 1.99/Natty. It's a bit different than the old one (--root-directory) we use in Grub 1.98.

After running those commands, try rebooting and see if it boots. If this doesn't work, we can try to completely purge and reinstall all Grubs on your system.

---

### Post by Non-lucky on 2011-04-30
No dice, it just boots to a grub prompt and when installing grub as per the instructions it spits out

```
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

I tried something very similar to your instructions before I posted and got similar results, the only difference was that my hard drive was named after it's uuid (I think) and was under /media

I guess it's time to purge grub

Should I follow your instructions here?

 [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by drs305 on 2011-04-30
The error message you posted sounds like you were trying to install grub to the partition instead of the MBR. This would have happened if you had put a partition number ("sdaX") in the last command instead of "sda". Also did you mount all the Ubuntu partitions?

If that wasn't the reason, rerun the commands and as the last command run:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
which is the old command but still works for Grub 1.99.

The link to purge/reinstall was the correct one, although the grub-setup error message is a bit worrisome if you haven't been trying to install it to a partition.

---

### Post by Non-lucky on 2011-04-30
Unfortunately there was no way for me to make a mistake since I did a straight copy+paste and those are all the partitions I have.

Running the new command last gives me the same 3 error messages as before. It is an oldish computer, perhaps the hard drive is giving out? A bad MBR sector?

Should I attempt to purge now?

---

### Post by drs305 on 2011-04-30
> **Non-lucky said:**
> Should I attempt to purge now?

You can try it but I can't guarantee it will work. The MBR error has something to do with hardware I believe and not with Grub (other than that Grub should be trying to write to the MBR). But you can try to run the purge/install. If your system isn't booting now, all you will risk is your time.

---

### Post by Non-lucky on 2011-04-30
It didn't work. But the errors in the console 

```
grub-probe: error: cannot stat `aufs'.
```

lead me to this

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009")

Which according to some of the comments it still seems to be an issue. I'll attempt to try reinstalling with the alternate disk like they did.

---

### Post by drs305 on 2011-04-30
> **Non-lucky said:**
> It didn't work. But the errors in the console 

```
grub-probe: error: cannot stat `aufs'.
```

lead me to this

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009")

Which according to some of the comments it still seems to be an issue. I'll attempt to try reinstalling with the alternate disk like they did.

Thanks for pointing out that bug report. I hadn't seen it but will keep it in mind. 

I did see that at least one person was successful at using chroot to install it but often it takes longer to troubleshoot than a fresh install when nothing needs to be preserved.

Please let us know how the installation from the alternate CD works out for you.

---

