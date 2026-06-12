---
title: "&quot;Serious errors were found while checking the disk for /&quot; after upgrading to 14.04"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by Vitor_Coimbra on 2014-04-20
Yesterday I attempted to upgrade my Ubuntu 13.10 to 14.04. Everything went okay, up until the point I had to reboot to make the update work.

After that, I cannot boot into Ubuntu due to this error. It says something like "I to ignore, S to skip and M for manual recovery." If I ignore it, then another message pops up saying "[COLOR=#333333][FONT=Georgia]The disk drive for /tmp is not ready yet or not present[/FONT][/COLOR]". If I skip that, then yet another message comes up saying "[COLOR=#333333][FONT=Georgia]An error occurred while mounting /[/FONT][/COLOR]". Once again, if I skip that, I get stuck on a black screen with a frozen white cursor on the top left of the screen and nothing written on it. I can't type anything whatsoever.

On the other hand, if I choose M on the first message (or the other 2, it doesn't really seem to matter), it drops me on a "maintenance root shell," with a message saying "Root filesystem check failed." I have no clue as to what to do there, I've searched all over the internet, but nothing so far has helped. So far I've tried:

- fsck /dev/sda(1, 2, 3)

    Output is:
    ```
fsck from util-linux 2.20.1
fsck: fsck.ntfs not found
fsck: error 2 while executing fsck.ntfs for /dev/sda(1, 2, 3)
```

- ntfsfix /dev/sda(1, 2, 3)

    Output is, for 1 and 2:
    ```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed sucessfully,
Checking the alternate boot sector... OK
NTFS volume version is 3.1
NTFS partition /dev/sda(1, 2) was processed sucessfully.
```

    And for 3:
    ```
Refusing to operate on read-write mounted device on /dev/sda3
```

- I can't install any other boot repair program because apt-get doesn't work. Output for everything is:
```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```

Content for my /etc/fstab is:
```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
```

I've had Ubuntu since 12.10, installed with the Windows installer for 64-bit Windows 7. Upgrades for 13.04 and 13.10 worked wonderfully, yet this one is being a huge headache.

Any help would be greatly appreciated. Thanks in advance.

EDIT: Oh yeah, I also upgraded to 14.04 when a pop-up message asked me if I wanted to. I didn't do any crazy command line manipulation, all I did was click "Confirm."

---

### Post by Vitor_Coimbra on 2014-04-21
To anybody who wants to at least save their data, I was able to get into Ubuntu by holding the Shift key during boot. After choosing Advanced Options, I chose an older kernel version (3.11) and was able to access my things.

My stuff is now safe in my flash drive in case this is never solved or the only solution is reinstalling.

---

### Post by rainymountain on 2014-04-22
Same issue found here. I am wandering if this is because of install from windows? And later, I try to re-install from wubi after wipe out, it still shows same error.

---

### Post by Gilad_Pellaeon on 2014-04-22
> **rainymountain said:**
> Same issue found here. I am wandering if this is because of install from windows? And later, I try to re-install from wubi after wipe out, it still shows same error.

Seeing as wubi was discontinued around the time of Ubuntu 13.04 i'd say you'd be better off to skip wubi entirely.

---

### Post by stefan28 on 2014-04-25
> **Vitor_Coimbra said:**
> To anybody who wants to at least save their data, I was able to get into Ubuntu by holding the Shift key during boot. After choosing Advanced Options, I chose an older kernel version (3.11) and was able to access my things.

My stuff is now safe in my flash drive in case this is never solved or the only solution is reinstalling.

There is one more thing that seems to work. Apparently you can manually edit your GRUB file like this:

**Note:** I am not a Linux expert and I would appreciate if someone more knowledgeable could weigh in and confirm this is a safe temporary solution. Also, here is the [source]("https://answers.launchpad.net/ubuntu/+question/247265") -- all credit goes to the guys that figured this out.


```
gksudo gedit /boot/grub/grub.cfg
```

Now find the line similar to this (search for the **highlighted part**):

```
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=[bunch-of-numbers] loop=/ubuntu/disks/root.disk **ro rootflags=sync**  quiet splash
```

Change the **ro** to **rw **(as in - instead of mounting as read-only, mount for read-write), save and reboot.

This file is actually auto-generated, but this solution has been working for me for the past few days without any issues (I am also dual-booting with Windows 8 -- no problems there either).

And one more link that could be of interest -- someone who seems to be experiencing this issue [filed an official bug report]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1308152"). There is no response yet, but the bug has been "confirmed" and perhaps there will be some useful information posted here soon.

---

### Post by BazBear on 2014-04-26
Thanks! Worked like a charm, with only the caveat being the line needed changing in my particular config file was a bit different than yours. 

Before change of ro to rw mine was....

```
[COLOR=#000000][FONT=Ubuntu Mono]linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=bunchofhexidec loop=/ubuntu/disks/root.disk ro[/FONT][/COLOR]
```

---

### Post by hakuna_matata on 2014-04-28
My solution: [http://ubuntuforums.org/showthread.php?t=2217829&p=12996954#post12996954](http://ubuntuforums.org/showthread.php?t=2217829&p=12996954#post12996954)

---

### Post by KumarAseem on 2014-08-09
1.In ubuntu boot manager press e, it will direct you to edit grub file
2.Find the line below and edit ro(highlighted below and underlined) to rw[COLOR=#000000][FONT=Ubuntu Mono]

linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=bunchofhexidec loop=/ubuntu/disks/root.disk _**ro**_[/FONT][/COLOR]
3.After editing press F10 to enter to desktop
4. Open terminal by pressing Ctrl+Alt+T then type the following code

gksudo gedit /boot/grub/grub.cfg

5. In the file which opens after running above query, find the first line below

linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=[bunch-of-numbers] loop=/ubuntu/disks/root.disk **ro rootflags=sync**  quiet splash

6. Change ro to rw and save the file
7. Restart your system
8. Problem solved

---

### Post by silly2 on 2014-08-18
Thanks KumarAseem, i followed your instructions when i encountered the "serious errors" message after an attempted update. i pressed "e" with the Ubuntu option selected from the boot manager window that i got while holding Shift down during the boot. i changed ro to rw and got my kde desktop up by pressing F10. i differed from your editing advice by editing grub.cfg in a normal shell with sudo vi, exiting with wq!. All was then well. I made sure all my backups were in order, then restarted. The restart checked the disk again, but this time completed the boot and opened kde. 

So thanks, but it sure seems like magic to me:) How could an ro be an error? who needs an rw so they can write to boot files? What triggers the disk check, which takes a long time? 

But no matter, i did the incantations you offered and i am an appreciated supplicant. thank you, thank you

---

### Post by h-h2 on 2014-09-05
The solution is here
[https://www.youtube.com/watch?v=HIKf_uM9FHI](https://www.youtube.com/watch?v=HIKf_uM9FHI)

---

### Post by Mike_Locus on 2014-10-11
Thanks - worked like a charm: had to install gksudo.  since upgrade I noticed that ramdisk is now being loaded at boot.  CPU fan seems to be running faster which means cpu is running fierce.  Because of this there is a decrease performance while browsing web pagges.  If Iwanted my cpu to be running crazy all the time I'd just laod Windows.  Chances are if you're here it's because your recent Ubuntu upload screwed things up then I would tell you to stay away from the upgrade because there seems to be more faults to the OS now, after upgrade than just not being able to boot a later version of Linux.  Thanks again though for the boot fix!

---

### Post by jimi12toes on 2015-06-13
> **KumarAseem said:**
> 1.In ubuntu boot manager press e, it will direct you to edit grub file
2.Find the line below and edit ro(highlighted below and underlined) to rw[COLOR=#000000][FONT=Ubuntu Mono]

linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=bunchofhexidec loop=/ubuntu/disks/root.disk _**ro**_[/FONT][/COLOR]
3.After editing press F10 to enter to desktop
4. Open terminal by pressing Ctrl+Alt+T then type the following code

gksudo gedit /boot/grub/grub.cfg

5. In the file which opens after running above query, find the first line below

linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=[bunch-of-numbers] loop=/ubuntu/disks/root.disk **ro rootflags=sync**  quiet splash

6. Change ro to rw and save the file
7. Restart your system
8. Problem solved

It worked!!!! YAY!!! :D
Edit: after a system software update I did have to repeat the process but it still works. :p

---

### Post by coffeecat on 2015-06-14
Old thread about problems with the long unsupported and obsolete wubi. 

Thread closed.

If anyone needs help about a similar situation, please **backup your personal data before you lose it** and then start a new thread if you need help making a conventional installation of Ubuntu as a dual-boot with Windows.

---

