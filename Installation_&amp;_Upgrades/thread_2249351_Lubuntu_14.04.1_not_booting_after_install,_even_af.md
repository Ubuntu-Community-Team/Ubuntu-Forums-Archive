---
title: "Lubuntu 14.04.1 not booting after install, even after grub2 updated..."
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by flooo2 on 2014-10-21
Hi all,
I just installed Lubuntu 14.04.1 64-bit and the problem is that after install (apparently successful), I cannot boot it: it just shows a black screen, sometimes with a blinking cursor top-left. The only response I can get from there is Ctrl+Alt+Del to restart, which prints the time between square brackets and then "Restarting blablabla..." or something like that.

I have a December 2009 laptop, 64-bit ThinkPad SL510, that came with Windows 7: I had immediately installed Ubuntu 9 with Wubi, which I upgraded to 10.04, then 12.04. This dual boot worked like a charm (except the upgrades that progressively destroyed my ubuntu filling it with more and more bugs, but that's another story).
I had removed grub (or set the timer to zero) so that booting was faster, using only the Wubi/Windows Loader defaulting to Ubuntu.
I want to keep my original Windows 7 install as it is.

My plan was to keep my Ubuntu 12.04 and use it if needed during transition, either from wubi or from virtualbox or something. 
Thus, I wanted Lubuntu 14.04 to be my new default, either adding it to the Windows Loader or placing grub before the Windows Loader in the boot sequence.

I used Unetbootin to prepare my installer on a 120GB USB drive.
What happened after install is that when I rebooted, I could not see the new Lubuntu 14.04.1 install... no new grub or anything (just the Windows Loader).
I installed Lubuntu 14 with "Install Alongside Other OS", which created a 58GB extended partition at the end of my 320GB internal drive: the extended partition contains 54GB regular partition for Lubuntu and 4GB for its swap partition.

So, I booted my former Ubuntu 12.04 and tried what I could find in other threads:

First, sudo update-grub, and reboot. No chance. Then sudo install-grub/dev/sda followed by update-grub. No chance (this just added back grub 1.99 after Windows Loader).

Then I tried boot-repair, which installed grub 2 before Windows Loader; so my boot sequence is:
[LIST=1]
[*]Grub2, with choices of Lubuntu 14 or Windows;
[*](if Windows chosen) Windows Loader, with choice of Windows or Ubuntu;
[*](if Ubuntu chosen at step 2) Grub 1.99, with choices of Ubuntu 12.04 and previous versions, Lubuntu 14.04
[/LIST]

Choosing Lubuntu 14 from first boot step sends me to the blinking cursor as described above. 
Choosing Lubuntu 14 from third boot step sends me to a black screen where nothing happens and the only option is to force a hard reboot holding the Power button 5 seconds.

I tried to follow the following thread's instructions, but Ctrl+Alt+F2 does not do anything when I try to boot Lubuntu 14 from either step 1 or step 3... so I cannot try to stop and restart "sudo service lightdm".
[http://ubuntuforums.org/showthread.php?t=1983359](http://ubuntuforums.org/showthread.php?t=1983359)

Here's my boot-info: [http://paste.ubuntu.com/8610291/](http://paste.ubuntu.com/8610291/)

Any help? :)

---

### Post by oldfred on 2014-10-21
It may just be video driver.
Intel has only one video driver but updates it to work with the newest chips. You may not need a setting where before you did not.

You add Intel settings like the instructions for nomodeset, but with Intel usually nomodeset does not work. See ubfan1's suggestions which are mostly for Intel chips.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Note that 12.04 was the last supported version of wubi.

---

### Post by flooo2 on 2014-10-21
Thanks, I tried all your suggestions.
It still does not work, but maybe the following info will help debug:

Removing "quiet splash" boot option shows the boot sequence output: it stalls always at the same place, as you can see on the following picture (just stays there forever with blinking cusor, and remains responsive to Ctrl+Alt+Del but not Ctrl+Alt+F2).
[http://postimg.org/image/jlfcm9weh/](http://postimg.org/image/jlfcm9weh/)

Other options did not change anything (nomodeset, acpi=0, acpi_osi=linux, noalpic, video=1024x768-24@60, etc.), excepted acpi_osi=linux which made Ctrl+Alt+Del no work anymore (a lot of assembly-like instructions rolled out, instead of "Restarting machine", then everything was frozen and I had to force a hard reboot with power button).

I know that Wubi does not support (L)ubuntu 14, but I'm trying to launch it from Grub there... both Grub 1.99 and 2.02 do the same thing here (excepted the trace is a little shorter in 1.99; the one in my picture is from grub 2.02).

Any idea?

For the record, I have a BIOS (not EFI/UEFI) and my whole chipset is Intel (CPU, graphics, sound, network...).

---

### Post by oldfred on 2014-10-22
Is the issue booting Lubuntu or are you trying to boot directly into your wubi from grub?
 Normal wubi boot is into Windows and then from Windows boot into wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

The boot option shown of 1280x1024 is just an example. You have to use your correct monitor X by Y screen size.
With Intel one of the Intel options usually works.

---

### Post by flooo2 on 2014-10-22
My boot sequence is as described above: 

[LIST=1]
[*]Grub2, with choices of Lubuntu 14 or Windows;
[*](if Windows chosen) Windows Loader (Wubi ?), with choice of Windows or Ubuntu;
[*](if Ubuntu chosen at step 2) Grub 1.99, with choices of Ubuntu 12.04 and previous versions, Lubuntu 14.04
[/LIST]

Ideally I want to boot Lubuntu 14 from the first step (grub2.02, before Wubi). I also tried from step 3 (grub 1.99) with same results.
I could get rid of Wubi, but not right now (unless I can find a way to access my current Ubuntu 12.04 ".disk" image (30 GB) that's been created for Wubi).

Anyways, I'm really trying to boot a brand new Lubuntu 14 from a freshly created and updated grub 2.02. 
I've never been able to boot it since the end of install. 
I can see the Lubuntu 14 files on the partition that was created during the install.


I know about the screen size, which is why I used 1024x768 instead of 1280x1024.
What do you mean by "Intel options"? Are there any Intel-specific options I could/should add to the boot command?

Thanks for your help :)

---

### Post by oldfred on 2014-10-22
The option you used with your screen size. But perhaps you need additional  options?
What Intel chip do you have?

 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

You can mount wubi's root.disk from a live installer or once you get Lubuntu booting from it.

---

### Post by flooo2 on 2014-10-22
My intel chipset is:

- VGA-compatible graphic controller and host bridge = Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
- all the rest (USB, audio, PCI, SATA, etc.) = Intel Corporation 82801I (ICH9 Family)
- CPU = Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz

I tried most combinations of one of the above video options and additional settings (acpi, etc.), but still no change: the boot trace always stops after USB detection... then no activity at all (HDD light off, nothing moves even if I wait).

I don't understand what's wrong...

Also, I tried to mount wubi's root.disk from the live installer (my Unetbootin USB Lubuntu 14 drive), but I didn't manage... I even tried with VirtualBox but it doesn't seem possible (I found a few posts about this reporting experiments that might work but are not worth the trouble).
How would you do it?

---

### Post by oldfred on 2014-10-23
i have seen these:
How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by flooo2 on 2014-10-23
Oh ok, this is accessing the files... what I need is running/booting the image.

---

### Post by oldfred on 2014-10-23
This was by the member who created the bootinfoscript. I think he just wanted to prove that you could use grub to boot many things including wubi.

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

You can just boot it from grub2 menu entry also.

---

