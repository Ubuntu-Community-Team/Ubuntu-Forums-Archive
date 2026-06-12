---
title: "/boot on USB - One USB for Multiple Machines? - Possible?"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2014-12-12
Hi all.  I'm trying to build a few machines, each of which I would like to have /boot on a USB stick.  I am wondering if it's possible to use a single USB for multiple machines?  I have seen discussions of how to add live-USB images as boot choices, but it it possible to have options for multiple machines (at least 4)?

Forgive me if this is somehow obvious.  I'm no expert in this area.

/DA

---

### Post by ian-weisser on 2014-12-12
Upgrades and security updates may become problematic, with mismatched versions between /boot and the rest of the system....and missing files when the package manager looks for /boot.

---

### Post by DiagonalArg on 2014-12-12
Thanks, Ian.  You're saying there's no way to set this up so that it works with grub menu entries pointing to the various kernels/initramfs's, and grouped by machine?

Alternatively, is there some way to have multiple partitions on the USB, and then chain-load the bootloader, starting with some code that provides a menu: machine1/partition1; machine2/partition2; ...

(Feeling in the dark here, thanks for putting up with me!)

/DA

---

### Post by oldfred on 2014-12-12
Keep the /boot folder in each system.

On a flash drive just install grub and manually create your own grub.cfg file.
This assumes each system is BIOS, and you do not have to have any special boot parameters.

 If you happened to have every system with the same partitions.


 menuentry "Boot Install on sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}

Or you can create 4 entires like this, using  each systems UUID which are preferred. Each then could have different boot parameters.


        
 menuentry "Boot System 1" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

[http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484)       

 Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

---

### Post by DiagonalArg on 2014-12-13
Ok, @OldFred - Thanks for your input.  Will have to study in detail tomorrow, but one question.  
> [COLOR=#000000]Keep the /boot folder in each system.[/COLOR]

 Does this present any difficulty if the system is encrypted (as they all will be)?  We can just put the /boot folder on a separate partition on the USB, correct?

/DA

---

### Post by sudodus on 2014-12-13
If you want encryption, I'd suggest encrypted disk and encrypted home, something like what is described in the following instruction for testing (iso-testing during the developement cycle)

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results)

-o-

If you want a portable system, that works in all your computers, keep everything in an external drive (USB pendrive or external (SSD or HDD) (eSATA or USB3)). It works as long as you use no (and need no) proprietary drivers. So install your favourite Ubuntu flavour into an external drive.

---

### Post by oldfred on 2014-12-13
You cannot share /boot partitions, so not so easy to have on USB.
Normal full drive encryption uses LVM and has to have a separate /boot. That normally is not and does not need encryption and is outside the LVM.
If you just encrypt /home then that is more like a normal install.

---

### Post by DiagonalArg on 2014-12-15
Thanks guys, but I don't think you're getting to the issue, here.  I'm going to propose an approach which might work. Let's just consider two installations with one USB stick. 


(1) USB is formatted MBR and has two partitions, labeled BOOT1 (for machine1) and BOOT2 (for machine2)


(2) Install Ubuntu to the second machine, with /boot in BOOT2.  core.img will be installed to the sectors right after the MBR.  (see [https://en.wikipedia.org/wiki/GNU_GRUB#GRUB_version_2_.28GRUB.29](https://en.wikipedia.org/wiki/GNU_GRUB#GRUB_version_2_.28GRUB.29))


(3) Install Ubuntu to the first machine, with /boot in BOOT1.  grub2 will be installed to the sectors right after the MBR, overwriting the first core.img.  This core.img will point to BOOT1


(4) The grub.cfg in BOOT1 will have a menu entry that looks something like (copying the machine I'm on now):


```
   menuentry 'Boot machine1' {
        set root='(hd0,msdos1)'
        linux   /vmlinuz-3.2.0-74-generic root=/dev/mapper/root ro   quiet splash $vt_handoff
        initrd  /initrd.img-3.2.0-74-generic
   }

```

Here, hd0 should be the USB, and "msdos1" is pointing to the first (BOOT1) partition.  


So, I will add a menuentry that looks something like:


```
   menuentry 'Boot machine2' {
        set root='(hd0,msdos2)'
        linux   /vmlinuz-whatever-generic root=/dev/mapper/root ro   quiet splash $vt_handoff
        initrd  /initrd.img-whatever-generic
   }

```

This second menuentry says to use BOOT2 as the location to find the linux kernel and the initramfs.


(5) Copy this _same_ grub.cfg into BOOT1


-----


I believe this can work, because even if core.img is updated, it will still do the work of accessing one of the partitions (BOOT1 or BOOT2), and presenting the menu.  The key is that I will have to be careful to pick the menu entry properly, or I'll end up booting the kernel and initramfs for the wrong machine.


Does anyone see any problem with this?


Is there any way that I might be able to put in a failsafe so that I don't stupidly boot the wrong menuentry?

---

### Post by DiagonalArg on 2014-12-15
@OldFred.  Regarding your first response.  I see you've taken this from an [askubuntu question]("http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484"), but this doesn't get to my question.  (And notice that --root-directory is an old option.  It's now --boot-directory.)

Regarding your second response:
>    You cannot share /boot partitions, so not so easy to have on USB.

I'm not suggesting to share /boot partitions.  I'm suggesting many boot partitions, one for each machine, all on the one USB.

>    Normal full drive encryption uses LVM 
Inside the crypt, that's possible, yes, but not necessary.

>    and has to have a separate /boot. That normally is not and does not need encryption
Must not be encrypted.  You need it to unlock the crypt.

>    and is outside the LVM.
You can have /boot in another LVM.

>    If you just encrypt /home then that is more like a normal install.
No, don't want to do that.

---

### Post by ian-weisser on 2014-12-15
> **DiagonalArg said:**
> I'm not suggesting to share /boot partitions.  I'm suggesting many boot partitions, one for each machine, all on the one USB.

Ah, I had misunderstood the intent, then.

I suppose it's possible to load multiple /boot-red-machine /boot-blue-machine /boot-plaid-machine dirs onto a USB.
The first problem you run seems organization: Recognizing which physical machine maps to which boot dir in the menu. You will need a handy naming scheme for that.

You will need a backup of the USB key, in case an update-grub script overwrites your naming scheme, incidentally making all your machines unbootable. Grub assumes a single dir called "/boot" so you may discover some hardcoded logic that must be overcome.

Each machine's /etc/fstab will need to be edited to locate the appropriate /boot dir.

You might need a script to automatically unmount /boot when boot completes. Otherwise, you will need to manually unmount /boot every time.

You might consider a udev rule to mount the /boot-correct-machine upon insertion to the each machine. Else you will manually mount the wrong /boot on the wrong machine at some point and cause big problems for *two* machines at once...possibly making one un-bootable and the other un-decryptable. Fun!

Updates may be a pain. Obviously, you should only run updates that regenerate initramfs while the USB drive is inserted. That means automatic security updates should be disabled, and you will need to schedule weekly time for this chore on each machine.

---

### Post by oldfred on 2014-12-15
It probably can be done. Each fstab will refer to a different UUID that is then a different partition on the flash drive. And that install would not care nor default mount the other /boot partitions.

But it is more a user issue of keeping track of which /boot belongs to each install. While in that system it should be ok. And you can only use one computer at a time unless you make several identical copies of the flash drive. And having copies would be a good idea as flash drives do not last forever and once it fails all 4 systems then are unbootable. But keeping the copies in sync is then also an issue.

Why must the /boot partition not be on each system, on on flash drive?
 I still think each system still having /boot partition, but have grub on flash drive would be easier to manage.

---

### Post by DiagonalArg on 2014-12-16
> [COLOR=#000000]Grub assumes a single dir called "/boot" so you may discover some hardcoded logic that must be overcome.[/COLOR]
This doesn't appear to be the case.  Grub can install the images in any directory, using the --boot-directory option.

> [COLOR=#000000]Each machine's /etc/fstab will need to be edited to locate the appropriate /boot dir.[/COLOR]
Fine.

> [COLOR=#000000]You might need a script to automatically unmount /boot when boot completes. Otherwise, you will need to manually unmount /boot every time.[/COLOR]
I don't see this.  Why?

> [COLOR=#000000]You might consider a udev rule to mount the /boot-correct-machine upon insertion to the each machine.[/COLOR]
Ok, here's something else I'm not familiar with.  Do you have a good intro that you can point me to?

> [COLOR=#000000]Updates may be a pain. Obviously, you should only run updates that regenerate initramfs while the USB drive is inserted. That means automatic security updates should be disabled, and you will need to schedule weekly time for this chore on each machine.[/COLOR]
I won't be taking the stick out while the machine is running.

------

It seems that there is something like this going on at project "[Bootless]("https://bootless.sarava.org/")".  See the first and the "Design" section.  They are doing it for the same reasons I need to.

/DA

---

### Post by DiagonalArg on 2014-12-16
> ... [COLOR=#000000]you will manually mount the wrong /boot on the wrong machine at some point and cause big problems for *two* machines at once...possibly making one un-bootable and the other un-decryptable. Fun![/COLOR]
*What I need to do here is in the initramfs, somehow add a check that I am looking at the right machine. Since I'm going to be unlocking a LUKS crypt, if the password is different then I'm fine since the luksOpen will fail.  If the password is the same, then it might just be a matter of fstab using the UUID of the proper root & boot devices, which would then fail out if that initramfs is not the appropriate one for the machine that I'm on (since the fstab will have the wrong UUID's).

> [COLOR=#000000]Updates may be a pain.[/COLOR]
The only issue I can see here is that on any kernel update, the new grub.cfg will have to be propagated to the other boot partitions.  I wonder if there may be some way to have this done automatically...

/DA.

*Edited to correct my confusion.

---

### Post by sudodus on 2014-12-16
You have been warned that there may be problems. But your idea might be better than we understand. I think you really want to do this, so go ahead, and please tell us about it, when you have something interesting to report :-)

Finally, encryption makes it extra important to take regular backups, and to remember the password or passphrase.

---

### Post by oldfred on 2014-12-16
To avoid the issue of grub in MBR getting out of sync of grub in each boot partition, create another grub only partition. Install grub to flash drive and to grub only flash drive. That version of grub will never be updated so it will not get out of sync.

Then create a grub.cfg in the grub only partition. Each entry as shown in post #4, except the set root will always be hd0 as boot drive is always hd0, and each partition then becomes the partition entry.  Because it is encrypted you will have to load the lvm module and the root= line will have to refer to the lvm which I am not exactly sure how but something like root=/device/mapper/.... But each install must be unique.

---

### Post by DiagonalArg on 2014-12-17
Again, I'm being a bit thick.  The LUKS header has the UUID of the disk in it.  If my cryptab identifies the disk by UUID, then choosing the wrong menu entry will end up with an initramfs that contains a crypttab whose UUID doesn't match the UUID of the disk that I'm trying to unlock.  So boot will fail without doing any damage.

... except, under one condition.  I'm using an external header, so that there's nothing but (apparently) random data on the disk.  That header is located in the initramfs along with the crypttab.  So here I do have a problem.  The wrong header will be associated with the disk, and cryptsetup will attempt to unlock it - disaster.

For my use case, I'll need another solution.

---

### Post by DiagonalArg on 2014-12-19
This discussion is continuing, here:

[http://lists.gnu.org/archive/html/help-grub/2014-12/msg00045.html](http://lists.gnu.org/archive/html/help-grub/2014-12/msg00045.html)

/DA

---

### Post by DiagonalArg on 2015-01-12
The proper approach is to install grub on the USB by hand, and use that to chain-load the core.img from the boot partition associated with the machine you want to boot.  To identify which machine you're on and thereby make it idiot-proof, you can use the "hwmatch" command in grub, which is only available in Ubuntu.

Details are at the link in my previous post.  I'm now marking this thread "solved".

*Edit: It was pointed out that the approach I initially suggested in that thread:
[http://lists.gnu.org/archive/html/help-grub/2014-12/msg00045.html](http://lists.gnu.org/archive/html/help-grub/2014-12/msg00045.html)

would not work.  They are right, but you could do it more like this (see that thread):

```
[COLOR=#000000][FONT=Verdana] If (this is my laptop) then (run the core.img file in Partition 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]   else if (this is my desktop) then (run the core.img file in Partition 2)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]   else (run the core.img file in Partition 3)[/FONT][/COLOR]

```
Though I was generally discouraged from pursuing that approach, someone else proposed doing the same thing for a different reason.  They were encouraged to submit patches to make the OS update transparent:
[http://lists.gnu.org/archive/html/help-grub/2014-12/msg00072.html](http://lists.gnu.org/archive/html/help-grub/2014-12/msg00072.html)

I thought I'd comment that anyone interested might want to keep their eye out for the patches.  Let us know if it appears and if you try it out!

---

### Post by ian-weisser on 2015-01-12
Thanks for following up and letting us know the solution!

---

