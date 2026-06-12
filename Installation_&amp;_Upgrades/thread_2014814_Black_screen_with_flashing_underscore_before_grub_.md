---
title: "Black screen with flashing underscore before grub menu"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by Jakob45 on 2012-07-02
Trying to install Ubuntu 10.04 (also tried 11.10 same problem) from a live cd I have no trouble booting into live cd and install seems fine (installing to clean HDD) when the time to reboot comes I reboot and all that happens after bios hardware check is a black screen with flashing underscore.
If I try to get GRUB menu with shift key on startup then I simply get the message
GRUB loading.
_
On a black screen

---

### Post by darkod on 2012-07-02
Do you have multiple disks? This sounds like you have a broken grub that you are booting. Your working grub might be on another disk.

---

### Post by cbanakis on 2012-07-02
Yes, I experienced a similar problem with multiple hard drives.

What had happened, was... 

1. I installed Ubuntu on drive A.
2. I set drive A as the boot drive in my bios.
3. I discovered that for some reason Ubuntu installed the bootloader on drive B.
4. Setting drive B as the boot drive in my bios resolved the issue.
5. The next time I re-installed Ubuntu, I physically disconnected drive B during setup as a precaution.

---

### Post by Jakob45 on 2012-07-02
No single disk 
sda1 sector is ext4 format with and sda2 extended partition containing sda5 swap area
sda1 has boot flag

---

### Post by darkod on 2012-07-02
OK. Boot with the cd in live mode and try to reinstall grub2 in terminal with:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will reinstall it on the MBR of the disk, /dev/sda.

If that doesn't work, there are other options to try.

---

### Post by Jakob45 on 2012-07-02
Already tried this made no difference

---

### Post by darkod on 2012-07-02
OK then. Boot into live mode and install boot-repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can try the recommended repair immediately, or you can only create the bootinfo results and post the link it gives you so we can have a look.

The results will show more details about the system and the setup.

---

### Post by Jakob45 on 2012-07-02
Ok so the boot info gave me this
[http://paste.ubuntu.com/1071888/](http://paste.ubuntu.com/1071888/)

---

### Post by cbanakis on 2012-07-02
did you install from a cd, or a flash drive?

I had it install the bootloader on the flash drive 1 time (somehow)

Burning a cd, and reinstalling solved the problem

---

### Post by darkod on 2012-07-02
I can't notice anything wrong. You do have grub2 on the MBR of the disk, so that is correct.

The only thing I can see is that you have added the nomodeset parameter twice, but that shouldn't be the issue.

Did you try the recommended repair procedure of boot-repair? It might work. But I can't guarantee it since I can't even see anything wrong.

---

### Post by Jakob45 on 2012-07-02
No but I have tried this before I added the nomodeset to try to negate a dirver issue (i'm running nvidia chipset) but no joy

---

### Post by YannBuntu on 2012-07-05
Hello
You have customized /etc/default/grub, and you have "nomodeset" twice in your GRUB entry. I don't know if this causes problems, but you should at least remove one. If i were you, i would:
1) purge and reinstall GRUB (="Purge GRUB" option in Boot-Repair)
2) try this: [http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

---

### Post by Jakob45 on 2012-07-05
Already done this but thanks for the reply
Only thing left to try is step two of the thread you posted I shall update this post when i've tried it

---

### Post by Jakob45 on 2012-07-07
> **YannBuntu said:**
> Hello
You have customized /etc/default/grub, and you have "nomodeset" twice in your GRUB entry. I don't know if this causes problems, but you should at least remove one. If i were you, i would:
1) purge and reinstall GRUB (="Purge GRUB" option in Boot-Repair)
2) try this: [http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

Tried all the things you have suggested still no change any further ideas?
Thanks

---

### Post by drs305 on 2012-07-07
And you have tried purging/reinstalling grub either via Boot Repair's assistance or by [running the commands manually with chroot]("http://ubuntuforums.org/showthread.php?t=1581099")?

And you are still at a blinking cursor immediately after booting? i.e. no Grub menu, and there isn't enough time for it to have actually automatically booted and failed after the OS was running (video problem).

---

### Post by Jakob45 on 2012-07-07
> **drs305 said:**
> And you have tried purging/reinstalling grub either via Boot Repair's assistance or by [running the commands manually with chroot]("http://ubuntuforums.org/showthread.php?t=1581099")?

Yes tried both

---

### Post by drs305 on 2012-07-07
I can think of two things to try. Both involve editing grub.cfg from a LiveCD. Rather than chroot, we can keep it simple by just editing the grub.cfg file directly. If things don't work (good chance) we'll just restore the original.

Boot a LiveCD, mount your Ubuntu partition, make a backup copy of grub.cfg and open for editing:
```

sudo mount /dev/sda1 /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub.cfg.orig
gksu gedit /mnt/boot/grub/grub.cfg
```

We'll make 2 changes. First, we'll change the graphics mode to just boot to a console. Since you are seeing a blinking cursor, I don't think it's a GRUB video issue, but I know there have been some positive changes since 10.04 that enhance booting.

Find this section of grub.cfg:
> 
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7ef40819-3841-4c9c-8f99-fd363bcb1a59
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi

Replace with:
```

terminal_input console
terminal_output console
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7ef40819-3841-4c9c-8f99-fd363bcb1a59
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=5
else
  set timeout=5
fi
```
**[COLOR="DarkRed"]EDIT: Typo corrected.[/COLOR]**

Save the file and try rebooting. No need to run update-grub.


We are replacing the gfxmode with console mode in case that is interfering with the menu display. Secondly, we are asking GRUB to boot even if it didn't boot successfully on the previous attempt (recordfail). By changing the value from -1 even if the menu can't be seen, if GRUB now loads it's going to boot.

I'm not highly confident this is going to produce positive results but since purging/reinstalling GRUB didn't work I'm not sure what else to try.

If it doesn't work, you can restore your original grub.cfg file by remounting /dev/sda1 and deleting the newer grub.cfg and renaming grub.cfg.orig, using "gksu nautilus /mnt/boot/grub".

---

### Post by Jakob45 on 2012-07-08
Tried suggestion made by drs305 not made any difference (I think I may have produced this config before by uncommenting the console line in /ect/default/grub/grub) 
It may help you to know that I have tried three other linux based installs 
Ubuntu 11.10 - Same problem exactly
Ubuntu 8.04.4 - Rather than a blinking cursor on black screen at reboot a line is displayed which reads GRUB loading stage 1.5. 
Fedora 16 - Same problem exactly

I am wondering if it is a driver issue as I am running an nvidia card (G 105M) However I don't know how to install a driver to the installed system from the live CD any thoughts would be great.

---

### Post by drs305 on 2012-07-08
> **Jakob45 said:**
> Tried suggestion made by drs305 not made any difference (I think I may have produced this config before by uncommenting the console line in /ect/default/grub/grub) 
It may help you to know that I have tried three other linux based installs 
Ubuntu 11.10 - Same problem exactly
Ubuntu 8.04.4 - Rather than a blinking cursor on black screen at reboot a line is displayed which reads GRUB loading stage 1.5. 
Fedora 16 - Same problem exactly

I am wondering if it is a driver issue as I am running an nvidia card (G 105M) However I don't know how to install a driver to the installed system from the live CD any thoughts would be great.

The 'console' option should preclude driver issues unless your BIOS settings have been altered somehow. There are various kernel options such as "nomodeset" that can help with driver problems but those relate to OS issues and not problems with the initial boot screen. You might check your BIOS settings dealing with displays to see if there is anything you can change.

A rarely discussed option on the Ubuntu forums is installing *and configuring* the lilo bootloader. We often us lilo to reset the MBR but seldom recommend actually using it as the bootloader.

It's been a while since I tested lilo, but here are my notes on my experience. Note: Since you can't "Boot to Desktop" of your real installation, you would have to boot the LiveCD and  use the *chroot* procedure first before running the commands below (and wouldn't use 'sudo' with any of the commands below once 'chrooted'). If you can't get anything else to work it might be worth attempting. At the least it would either confirm Grub was the issue or rule it out as the problem.

> 	
Boot to Desktop.
sudo apt-get purge grub-common
**sudo apt-get update**  # Added per OP's comment below
sudo apt-get install lilo
sudo liloconfig
 Complains if / fstab not identified as /dev/sdXY
 Writes to PBR
 Writes to MBR
 Boot flag on /dev/sdX
 Asks to choose one of 4 boot background images.
 Stores configuration file in /etc/lilo.conf
Here is what a lilo entry looks like:

image=/boot/vmlinuz-2.6.31-21-generic
	label="Lin 2.6.31img1"
	initrd=/boot/initrd.img-2.6.31-21-generic
	read-only


---

### Post by Jakob45 on 2012-07-08
Install of lilo was successful just to point out to anyone following this thread I had to add the line apt-get update to you instructions as below
> **drs305 said:**
>  Boot to Desktop.
sudo purge grub-common
[COLOR=Red]**sudo apt-get update**[/COLOR]
sudo apt-get install lilo
sudo liloconfig
But when I get to the boot load menu and select the Lin_2.6.32img0 all I get is  a black screen which reads
Lin_2.6.32img0.........
The cursor moves across the screen simply adding full stops and the system will not boot.

---

### Post by drs305 on 2012-07-08
I just installed lilo on a Lucid VM. I accepted the default answers (Yes) at all points and rebooted successfully.

When I selected the menu item, it returned me to a black screen. The first message was "BIOS data check OK". Did you get that message?

Then the dots appeared, it stalled at an scsi check for about 15 seconds, and then resumed and booted to the Ubuntu Desktop.

It appears to me that we have ruled out GRUB being the issue. If you didn't get the "BIOS data check OK" message that might be an indicator of a BIOS issue, but I'm not sure what it would be.

You can reverse the steps if you wish and return the boot back over to GRUB if you wish by chrooting from the LiveCD and:
```

apt-get update
apt-get purge lilo
apt-get install grub-pc

```
Although it is recommended not to put GRUB on a partition, it works (at least initially). Perhaps installing it to the partition (sda1) rather than the MBR may make a difference. You can always reinstall it back to the MBR later.

---

### Post by Jakob45 on 2012-07-12
Any ideas what sort of BIOS issue it may be my bios is fairly minimalistic so not alot of options for changing setup I have tried most things that are there however all to no effect.

---

### Post by drs305 on 2012-07-12
> **Jakob45 said:**
> Any ideas what sort of BIOS issue it may be my bios is fairly minimalistic so not alot of options for changing setup I have tried most things that are there however all to no effect.

We are getting well past my area of understanding, but an Internet search of "lilo BIOS data check" revealed that the check can be turned off via the lilo.conf setting.

I have no idea what is happening on your system. If it is some sort of BIOS issue then perhaps turning off this check may help. To do that, you would need to alter the lilo.conf settings by booting the LiveCD, mounting your Ubuntu partition and then editing the file:
```
sudo mount /dev/sda1 /mnt
sudo gedit /mnt/etc/lilo.conf

```
Remove the # symbol from the ***# compact*** line. Save the file and try rebooting. One post said you would get a warning about having the 'compact' mode enabled, but I don't know specifically what the message is.

Again, I'll emphasize I have no idea if your problem is with your BIOS or not.

---

### Post by Jakob45 on 2012-07-14
Ok thanks i'll give it a go any idea which catagory I should start a thread in to get some further help with this?

---

