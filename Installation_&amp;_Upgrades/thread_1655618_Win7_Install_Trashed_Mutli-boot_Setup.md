---
title: "Win7 Install Trashed Mutli-boot Setup"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by MonsoonNewZealand on 2010-12-29
Hello.  I've searched through many posts and solutions where Windows 7 wipes out the existing MBR and boot config in place on a system with no regard to what is there.  That's happened to me but the solutions haven't solved my problem.  I've tried most of them.

In may case I had a WinXP/Ubuntu 10.04 with a Grub2 multi-boot on a 2 disk system.  Used it happily with no problems.  WinXP is on Hd0.  Ubuntu is on Hd1.  When Windows 7 was installed on its own partition, its boot loader replaced Grub and I can't get back to Ubuntu now.

Booting from the Ubuntu LiveCD and follow the instructions to reinstall grub goes well until the step:

sudo grub-install /mnt /dev/sdb

this gets several warnings and an error about using "blocklists".  Adding --force finishes with no error, but changes nothing.  Machine still boots into Win7.

Using the CHROOT method to reinstall grub goes well with no errors, but nothing changes.  Machine still boots into Win7.

MY QUESTION IS:

with the command "grub-install /mnt /dev/sdb" the disk where Ubuntu is loaded is specified in the second parameter.  **Should that 2nd parameter be /dev/sda**, which is the first disk in the system?  This is the first disk examined when the system boots and if it has the Windows boot loader then it's no wonder Windows always boots.  I need to overwrite the Windows boot loader.

Thanks in advance...

---

### Post by Herman on 2010-12-29
The instructions you're trying to follow are either wrong or at least they're out of date, maybe they're for Legacy GRUB, (the old grub).

You probably don't need the grub-install command, because you need to chroot for that and that's extra work. You should be able to use the grub-setup command, it will be a lot easier.

Take a look at this thread,[ **     [COLOR=#980101][B][ubuntu]**[/COLOR] Computer won't boot to 9.10; No Grub Menu[/B]]("http://ubuntuforums.org/showthread.php?t=1306900")
 
That method should work for you.

 > **Should that 2nd parameter be /dev/sda**, which is the first disk in the system?Yes, /dev/sda is your first hard disk and that's normally the best place to install GRUB, unless there's some reason why not like some kind of full disk encryption in Windows. In that case you should switch hard disks to make your Ubuntu hard disk the first, then install GRUB to that hard disk's MBR. The BIOS will only boot the first hard disk's MBR unless you are prepared to do the extra work of pressing your F8 or F12 or whatever key it is for the BIOS boot menu, where you can direct it to some other disk at boot time. That's not so convenient though, you'll get tired of that pretty quick.

---

### Post by MonsoonNewZealand on 2010-12-29
I'm sure this system is using grub2.

I couldn't wait and tried the commands that I suspected would work, which were:

sudo mount /dev/sdb6 /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/

sudo mount -B /dev/ /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/dev/
sudo mount -B /dev/pts /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/dev/pts
sudo mount -B /proc/ /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/proc/
sudo mount -B /sys/ /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/sys/

sudo chroot /media/c86aa59e-ff1e-4f8f-9ddb-f6d5b060f7a0/

grub-install /dev/sda

-- after rebooting I got my "old" grub menu back.

issuing the command:

update-grub2

rescanned the system and now the boot menu displays "Windows 7 (Loader)" instead of the old "Windows XP".  When I select the Windows 7 entry it runs that loader which displays Windows 7 and Windows XP.

So I have the system the way I want it now.  I hope these instructions might help people in the same situation with multi-disks and multi-OS's using grub2.  None of the instructions I saw before explained the meaning of the parameters in the grub-install command very well.  (and I didn't bother to read about them!)

This is a very good forum.

---

### Post by supershin on 2010-12-29
This is THE place for a lot of info about grub2 stuff.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2")

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by presence1960 on 2010-12-29
We need precise detailed info about your setup.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

This will give insight as to exactly what you have on your machine and how to solve your issue(s)

---

