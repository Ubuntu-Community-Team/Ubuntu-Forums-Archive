---
title: "Can't boot windows after upgrading to 12.04"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by markcoronado on 2012-08-25
I just upgraded to 12.04 from 10.04 LTS and now I can't boot into my 2 other windows partitions.
When I select my windows 7 using grub v1.99 it wants me to restore my windows 7 op system.

I need help please.

---

### Post by zombifier25 on 2012-08-25
Try running this command:
```
sudo update-grub
```

---

### Post by markcoronado on 2012-08-26
Here is what I get when I try to run sudo update-grub

mark@mark-laptop:~$ sudo update-grub
Generating grub.cfg ...
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 77
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
mark@mark-laptop:~$

---

### Post by darkod on 2012-08-26
It reports syntax errors. Did you have any manual entries in the grub2 config files? Anything that could have a wrong syntax?

Also, note that the recovery partition on the hdd has its own entry too. So there will be two different win7 entries, one will boot win7 the other will boot the recovery partition. That's normal.

Try to undo any changes to the files in /etc/grub.d/ if you were doing any, or in /etc/default/grub.

---

### Post by markcoronado on 2012-08-26
I ran a program called boot repair and now I have my 2 Windows 7 partitions back and I'm able to boot into each of them as though nothing has happened.

My only problem now is that it seems that grub is gone and ubuntu is gone from the boot menu.

How do I get it back?
Does grub have to be reinstalled? 
If it does how do I go about doing that.
It's been years since I originally installed ubuntu & grub and I've totally forgot how I did it.
I must be getting old. lol

Or can I add ubuntu to the windows boot manager and do away with grub?

---

### Post by oldfred on 2012-08-26
If you have Boot-Repair, run the BootInfo report and post the link it creates. Then we can see all the details of your system.

---

### Post by markcoronado on 2012-08-26
Here is my Boot info report link.

[http://paste.ubuntu.com/1168154/](http://paste.ubuntu.com/1168154/)

---

### Post by oldfred on 2012-08-26
Very strange. Script did not output any UUIDs?

It seemed to find you 12.04.1 install but did not give you the option to reinstall grub2's boot loader. Also your grub.cfg looks like your old manual entry as it has 10.04 referenced and a boot to Windows in sda1 which looks like the recovery partition. If you started to run recovery maybe it erased UUIDs?

You have boot files bootmgr & BCD in the recovery, normal hidden 100MBR boot/recovery & the main install. Windows normally just has those boot files in the 100MB partition, but you can add them to main install. But boot flag is on sda2 or the hidden 100MB boot/repair partition.

Since it looks like grub did not install correctly I might try the chroot reinstall. Boot-Repair has a helper screen that all but automates it. But I do not know how to restore all the UUIDs which you probably should do first if they really are missing.

Post this:
# To clear cache and get new view:
sudo blkid -c /dev/null -o list

If UUIDs are really missing you may be able to recreate with this, but you will have to update fstab and maybe a few other places.

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid



From liveCD

---

### Post by markcoronado on 2012-08-26
Thanks for the help.

I didn't try to run the recovery.

I don't know what UUIDs are or any of that other technical stuff you are talking about so you will need to help me through most of this.

First thing is I can't boot into 12.04 any longer after running boot repair so How do I get in to run boot repair again?
Will I need a live cd?
I have the 10.10 cd will that work or will I need to create a 12.04 cd?

---

### Post by oldfred on 2012-08-26
You can boot the 10.10 in an emergency, but now grub2 needs the current version to repair correctly. So download 12.04.1.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by markcoronado on 2012-08-26
OK I'll download the 12.04 and boot with it.

What is my next step.

Should I run boot repair next and have it install grub?

---

### Post by oldfred on 2012-08-26
Post the list of UUIDs, just to see if there was an issue with the report from Boot-Repair. It may just have been because you ran it from the older verison, but even that should have been ok.

sudo blkid -c /dev/null -o list

---

### Post by markcoronado on 2012-08-27
Here is what I get when I run sudo blkid -c /dev/null -o list 

ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
ubuntu@ubuntu:~$

---

### Post by darkod on 2012-08-27
UUID is a unique string assigned to all partitions when they are formatted, and it doesn't change until you format it again. Somehow it seems during the upgrade they were lost and they don't display any more.

Since grub2 works with UUIDs, this could be a reason it doesn't boot windows. On top of that you have a little bit confusing situation because you have win7 boot files on both sda2 and sda3. They should be on only one partition.

According to the size, it seems that sda2 is the System Reserved partition with the boot files.

If your ubuntu boots correctly, try this:
Make the os-prober not executable:
```
sudo chmod -x /etc/grub.d/30_os-prober
```Open the file 40_custom with:
```
gksu gedit /etc/grub.d/40_custom
```In it add an entry like:
```
menuentry "Windows 7 loader on /dev/sda2" {
insmod part_msdos
insmod ntfs
set root=(hd0,2)
chainloader +1
}
```Save and close the file. After that run in terminal:
```
sudo update-grub
```If you can't run ubuntu after running the boot-repair, first tell us that because you need to run something before running all of this above.

---

### Post by markcoronado on 2012-08-27
The only way I'm able to get into 12.04 now is by using a live cd and selecting try out.

When I first upgraded from 10.04 to 12.04 grub was still available when I turned the laptop on, but after running boot repair and selecting(recommended) grub is gone when starting up and windows boot manager is there which allows me to boot into my 2 windows partition and not 12.04. It's like grub and 12.04 are gone.

By booting from the live cd I'm not booting into my ubuntu partition just the live cd.

Should I try to boot from the live cd and run boot repair again this time selecting the option to install grub?

---

### Post by oldfred on 2012-08-27
I do not think running Boot-Repair should hurt anything. But I do not think it updates UUIDs as having those missing is very unusual. 

If it does not work or your UUIDs are still missing.

Then run this on every partition, but we still will have to manually update fstab with new UUIDs.

Change sdaX to sda1, sda2 etc thru sda8 to create a new UUID for each & every partition. Then rerun teh sudo blkid to get new list and we can suggest how to edit fstab.
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by markcoronado on 2012-08-27
I ran boot repair again but this time it's telling me that No OS has been found on this computer.

New link is,  [http://paste.ubuntu.com/1170649/](http://paste.ubuntu.com/1170649/)


You ask me to do this,
"Then run this on every partition, but we still will have to manually update fstab with new UUIDs.

Change sdaX to sda1, sda2 etc thru sda8 to create a new UUID for each  & every partition. Then rerun teh sudo blkid to get new list and we  can suggest how to edit fstab.
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid"

I'm not sure how to do that, could you explain it to me please.

Once again thank you and everyone else for your help.

---

### Post by oldfred on 2012-08-27
sudo tune2fs -U random /dev/sdaX

Run the above command 8 times changing X from 1 thru 8, or once each for every partition.

---

### Post by darkod on 2012-08-27
I am surprised by the part of grub.cfg that says you have 06_custom file, but it doesn't seem to run the 10_linux and 30_os-prober.

Were you doing some kind of customization in 10.04 by creating 06_custom with one entry for ubuntu 10.04 and one entry for windows? Maybe to avoid the whole bunch of kernels to show in the menu?

I can't see why even 12.04 is not detected, but if 10_linux is not running, that would explain it. If the above assumption about making custom entry for 10.04 is correct, note that it can't boot 12.04 unless the commands used are correct for 12.04 too.

On top of that, if you look at the list of files loaded by grub on sda6, there is no initrd.img which should be there and is needed in order ubuntu to boot.

This really looks like a mess, not sure if because of a failed update or it also has some thing you did in the 10.04 installation.

One way to proceed, probably, is to boot inti live mode (that's the only thing you can do), enter the installation with chroot, reinstall the kernel so that it creates the initrd.img file (or run some command to recreated that file), and purge and reinstall grub2. Purging will remove all of this messed up configuration and install the default one.
Later if you want to, you can cutomize it.

Oldfred, what do you think?

---

### Post by oldfred on 2012-08-27
I have not seen a system without UUIDs. I think once or twice I saw one partition. So I am just guessing that the missing UUIDs are causing all sorts of issues. So even if we have to manually add them we need to try. But I am concerned on why they were erased as that is very unusual.

---

### Post by markcoronado on 2012-08-27
I did customize the entries.
Here is my custom entry.

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Ubuntu Lucid 10.04 LTS" >&2 
cat << EOF
menuentry "Ubuntu Lucid 10.04 LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash*End of Note
        initrd /initrd.img
}
EOF
echo "Windows 7 Ultimate Edition = 1 Home Edition = 2" >&2 
cat << EOF
menuentry "Windows 7 Ultimate Edition = 1 Home Edition = 2 (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01CA88BEEDE74180
    chainloader +1
}
EOF
/etc/grub.d/06_custom


I made a backup before making changes if that will help.

---

### Post by oldfred on 2012-08-27
I am not sure how it processes with the cat & EOF. I always left the echo, cat & EOF out. But with two EOF's I am not sure it processes the second. I really think those are the instructions for typing the commands at the terminal so that they get added to a file or from another script. But the cat & EOF was how many suggested doing it.

Not sure what this does:
linux /vmlinuz root=/dev/sda6 ro quiet splash[COLOR=Red]*End of Note[/COLOR]

When I had some typos in my 40_custom it just did not update.

---

### Post by darkod on 2012-08-28
> **markcoronado said:**
> I did customize the entries.
Here is my custom entry.

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Ubuntu Lucid 10.04 LTS" >&2 
cat << EOF
menuentry "Ubuntu Lucid 10.04 LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash*End of Note
        initrd [COLOR=Red]/initrd.img[/COLOR]
}
EOF
echo "Windows 7 Ultimate Edition = 1 Home Edition = 2" >&2 
cat << EOF
menuentry "Windows 7 Ultimate Edition = 1 Home Edition = 2 (on /dev/sda3)" {
    insmod ntfs
    set root='[COLOR=Red](hd0,1)[/COLOR]'
    search --no-floppy --fs-uuid --set 01CA88BEEDE74180
    chainloader +1
}
EOF
/etc/grub.d/06_custom


I made a backup before making changes if that will help.

Well, as I said, your bootinfo results show that initrd.img doesn't exist from what ever reason. So, the above ubuntu entry wouldn't work. I guess the initrd.img was not correctly created during the upgrade.

Also, the windows entry looks wrong since you have (hd0,1) which means partition #1. But according to the results #1 is the recovery partition, not your partition with the windows boot files. That is #2. So it looks like the windows entry should be (hd0,2).

On top of this, you have syslinux on the MBR of the disk right now, and not grub2.

What I would do:
1. Install grub2 to the MBR. Boot with a 12.04 cd (make one if you don't have it) and in terminal install grub2 to the MBR with:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should install grub2 to the MBR. Restart and see do you get a grub menu when booting. Note that it might not work because of the above mentioned errors but do you at least get the menu?

2. If you are getting the grub2 menu, since I suspect the entries in it are wrong, you can press 'c' when in the menu so that grub command prompt will show. After that try booting ubuntu with something like (executing them one by one, there should be no errors reported):
```
insmod part_msdos
insmod ext2
set root=(hd0,6)
linux /boot/vmlinuz-3.2.0-29-generic root=/dev/sda6 ro quiet splash
initrd /boot/initrd.img-3.2.0-29-generic
boot
```

Does that get you into your 12.04?

If it does, post the output of:
```
ls /etc/grub.d
```

so we can see which of the grub files exist in /etc/grub.d and which don't.

If you restart note that the above procedure will need to be run on every boot so you can boot your ubuntu until you fix grub permanently.

---

### Post by markcoronado on 2012-08-28
Your suggestions got me in.

Here is the output.

mark@mark-laptop:~$ ls /etc/grub.d
00_header        06_custom  20_linux_xen   30_os-prober  41_custom
05_debian_theme  10_linux   20_memtest86+  40_custom     README
mark@mark-laptop:~$

---

### Post by darkod on 2012-08-28
OK. So, both 10_linux and 30_os-prober exist but are not executed, probably you disabled them.

Do you remember how? Did you touch anything in /etc/default/grub or you removed the execute bit from the files?

If you only made them unexecutable, lets make them executable and in return disable 06_custom temporarily:
```
sudo chmod +x /etc/grub.d/10_linux
sudo chmod +x /etc/grub.d/30_os-prober
sudo chmod -x /etc/grub.d/06_custom
sudo update-grub
```

The above should list the ubuntu 12.04 kernel found and maybe 3 win7 versions found.
One is the recovery partition on sda1, the second on sda2 seem to be the correct one, and the third on sda3 seems to be wrong. But boot files exist and os-prober will find them and create entry for them. Forget about win7 for the moment.

If on the other hand, you were changing options in /etc/default/grub, undo them and then run update-grub instead of the above group of commands.

If all goes well, when you restart you should see grub menu with one ubuntu 12.04 and three win7. Selecting ubuntu should boot the 12.04 without the need to use the manual commands you did last time. See if that works out.

---

### Post by markcoronado on 2012-08-28
I just tried booting into my windows partitions and I'm back to the original problem where it takes me to the restore partition instead of giving me the choice of my 2 windows op systems.

I'm able to boot into 12.04 now but how do I get my windows partitions to boot?

I was writing this before I read your last post.
Does this change anything or should I try what you just posted?

---

### Post by darkod on 2012-08-28
> **markcoronado said:**
> I just tried booting into my windows partitions and I'm back to the original problem where it takes me to the restore partition instead of giving me the choice of my 2 windows op systems.

I'm able to boot into 12.04 now but how do I get my windows partitions to boot?

Which windows partition you tried to boot?

PS. And which option for 2 windows systems you expect to get? The results show only win7 on sda3 but it does say it can't read correctly sda5 so you might have another windows there.

PPS. Does the grub menu look better and can you boot ubuntu without the manual commands? If you still use the manual commands you need to run something similar to what I suggested to make things better. Hold on a little, you are trying too fast and we are cross-posting :) I said to forget about windows for a while, don't be too attached to it. :)

The grub menu you tried to create looked messy, lets clear it up little. And lets try if the partitions have UUIDs now or not, does this output them:
```
sudo blkid
```

---

### Post by markcoronado on 2012-08-28
When I start my computer I get the grub menu with 2 choices.
Ubuntu 10.04  ( which is now 12.04 )
Windows 7 Ultimate Edition=1 Home Edition=2 (on/dev/sda3)

Grub menu looks the same and I can boot 12.04 without commands.

This is the same as it was before the upgrade to 12.04.
When I would select the option for windows it would take me to another screen where my 2 windows partitions would be listed, but now instead of that happening it takes into the recovery partition.

I tried the sudo blkid in terminal but I got an error saying sorry the application blkid has closed unexpectedly.
I restarted the computer and tried again but now nothing happens when I type sudo blkid in terminal other than it asks for my password and then shows mark@mark-laptop:$

---

### Post by darkod on 2012-08-28
The grub menu you are describing is the wrong one you have in 06_custom. As I said earlier, it's trying to boot windows from (hd0,1) which is the first partition, and that's the recovery partition. That's why the recovery partition starts when you select that entry.

Either edit 06_custom so that the windows entry boots (hd0,2), or disable it altogether and enable the default scripts, as suggested in post #25. Later if you don't like it like that, you can always customize again.

I was trying to make sure you are booting the latest 12.04 (because the ubuntu entry in 06_custom is suspicious too), and having the correct windows entry. Remember, according to the info so far, the correct windows boot files are on /dev/sda2 or (hd0,2).

It's up to you.

---

### Post by markcoronado on 2012-08-28
How do I edit and what do I need to change in  06_custom so that the windows entry boots (hd0,2

It was back in December 2010 when I made those changes in 06 custom and I totally forget
how I did it.

That would be my preferred solution.

---

### Post by darkod on 2012-08-28
```
gksu gedit /etc/grub.d/06_custom
```

Just replace the (hd0,1) with (hd0,2) in the windows menuentry. Save and close the file.

After that run:
```
sudo update-grub
```

That should recreate new grub.cfg with the change made.

---

### Post by markcoronado on 2012-08-28
I changed the 06_custom like you said and when I update-grub it came up with some kind of syntax error on I think it was line 77.

Then I ran the commands you posted in post 25 and now I get a totally different looking grub screen with 7 entries.

1( ubuntu with linux 3.2.0-29 generic
2( ubuntu with linux 3.2.0-29 generic (recovery mode)
3(previous linux versions
4(windows recovery environment on /dev/sda/
5(windows 7 loader on dev/sda2
6(windows 7 loader on dev/sda3
7(windows 7 loader on dev/sda2

Now I can boot into windows & 12.04, yea were making progress.

The new menu print is very small, is there a way to make it larger?
How can I tweak it & get rid of the unwanted entries?
I'd like to just keep 1 & 5
If there are previous versions of linux still on my computer can I delete them and if so how?

Thanks for all your help.

---

### Post by darkod on 2012-08-28
Previous linux versions doesn't mean previous releases. It means kernels older than the current -29-, they are listed under Previous so that the grub menu doesn't grow with every new kernel update.

To keep only windows sda2 entry, open /boot/grub/grub.cfg with:
```
gksu gedit /boot/grub/grub.cfg
```Then highlight all the text for that particular menuentry, make sure you select all of it. It will say like:
menuentry "windows 7 loader on /dev/sda2" {
........
.......
}

That is the whole entry, from the word menuentry until the }. Copy that text with Ctrl + C.

Then open /etc/grub.d/40_custom and after the existing lines paste the text. Make sure you don't delete the existing lines. Save and close.

Make 30_os-prober disabled and update the grub.cfg file with:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```That should leave you with the ubuntu entries, previous versions and only one win7 entry booting the sda2 partition.

If that syntax error message keeps showing up, open the /etc/default/grub file and check what's in line 77. Post the line if you are unsure where the error is.

---

### Post by markcoronado on 2012-08-29
OK grub seems to be working fine and I'm very thankful for everyone that helped.

I don't know what actually caused the problem but I am now able to boot into 12.04 and both of my windows 7 partitions.

Does anyone know why nothing happens when I run the sudo blkid command?

mark@mark-laptop:~$ sudo blkid
[sudo] password for mark: 
mark@mark-laptop:~$ 

Hopefully I'll never need it but it would be nice if it worked.

---

### Post by oldfred on 2012-08-29
Try this command.

ls -l /dev/disk/by-uuid/

If system is booting, you just about have to have UUIDs as grub & fstab use UUID. Perhaps your blkid command is bad?

---

### Post by YannBuntu on 2012-08-29
> Perhaps your blkid command is bad? 

I have created a bug report: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1042230](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1042230)
Feel free to complete/correct it.
I hope devs will help make us understand what happened. And hopefully they fix it so that it won't happen again.

---

### Post by markcoronado on 2012-08-29
> **oldfred said:**
> Try this command.

ls -l /dev/disk/by-uuid/

If system is booting, you just about have to have UUIDs as grub & fstab use UUID. Perhaps your blkid command is bad?

That command worked.

mark@mark-laptop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Aug 29 12:50 01CA88BEEDE74180 -> ../../sda3
lrwxrwxrwx 1 root root 10 Aug 29 12:50 01CA9139036B2F80 -> ../../sda8
lrwxrwxrwx 1 root root 10 Aug 29 12:50 45d19630-1318-4213-9201-b6278fb20a31 -> ../../sda7
lrwxrwxrwx 1 root root 10 Aug 29 12:50 921C18621C18441F -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 29 12:50 949e41a5-ba07-454e-a091-0d07a0012fac -> ../../sda6
lrwxrwxrwx 1 root root 10 Aug 29 12:50 DAA41C49A41C2B11 -> ../../sda1
mark@mark-laptop:~$ 

Is there any way to repair the blkid command?

---

### Post by oldfred on 2012-08-29
In synaptic it shows as libblkid1.

So try this.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall libblkid1

Then see if this works.

# To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by YannBuntu on 2012-08-30
(fixed link in Post #36 )

---

### Post by markcoronado on 2012-08-30
> **oldfred said:**
> In synaptic it shows as libblkid1.

So try this.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall libblkid1

Then see if this works.

# To clear cache and get new view:
sudo blkid -c /dev/null -o list


I ran all the commands in terminal and after running the last one "
mark@mark-laptop:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
mark@mark-laptop:~$ 

I received the message, Systen Program Detected.
Sorry the application blkid has closed unexpectedly.

I tried to copy the details but it won't let me C&P.

---

### Post by YannBuntu on 2012-08-30
> **markcoronado said:**
> I tried to copy the details but it won't let me C&P.

Maybe you can take a screenshot, and attach it here.

---

### Post by markcoronado on 2012-08-31
I'm sorry but I had already closed that window.

I ran the command again but this time no error message.

mark@mark-laptop:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
mark@mark-laptop:~$

---

### Post by oldfred on 2012-08-31
I am grasping at straws. Somewhere it said it is part of this package, so maybe another supporting file is not correct. 

```
sudo apt-get install --reinstall util-linux
```

---

### Post by markcoronado on 2012-08-31
I ran that command and then this one again.
mark@mark-laptop:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
mark@mark-laptop:~$ 

Then I got the error message again so I attached the 3 screen shots of it.

Hope it helps.

I just noticed that in my home folder only one of my 2 windows partitions is showing so I'm only able to access files on the one that is showing.

There is something good, I am able to access my desktop through the network and I wasn't able to do that before upgrading to 12.04

---

### Post by oldfred on 2012-08-31
Did you send error report? If not attach screen shots to bug report. As near as I can tell version looks correct, but there must be something in the upgrade that is not correct.

---

### Post by markcoronado on 2012-08-31
Yes I sent the error report.

---

