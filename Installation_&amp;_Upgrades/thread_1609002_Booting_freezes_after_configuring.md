---
title: "Booting freezes after configuring"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Pumpaw on 2010-10-29
I use a 2008 Intel 64 (x86-64) dual-core Gateway desktop PC running 32-bit XP SP3, and just started exploring Ubuntu (my first foray into Linux). I installed 10.10 live (persistent) on an 8GB USB flash (4GB for persistence). (Figuring out what program to use to add persistence took a very long time searching your forums and experimenting with several installers.) After many more hours of searching and experimenting, I got it to boot after adding "noapic" to the default boot command. (It also boots with "nolapic", but in uniprocessor mode.)

I configured the desktop, etc., and updated all software (which produced an error message about a "linux-image" subprocess script returning a "2" error), and rebooted. It complained about problems loading several applets (all of which had disappeared), so I reconfigured them, and rebooted. Finally, there were no error messages, so I spent several hours doing more Ubuntu configuring, and added my normal (XP) Firefox environment via FEBE. Firefox said that about 10% of my add-ons were not compatible with the latest Firefox release, even though those add-ons are accepted without complaint in the same version of Firefox under XP.

On the next boot, Ubuntu loading hung at the splash display (with the progress dots changing), with the last "terminal" message stating "Begin: live session user..." I waited 40 minutes. I tried this several times. No joy.

Why did I have these problems? What must I do to avoid them?

I thought I might have better luck actually "installing" Ubuntu. I've reinstalled Ubuntu live on a 2GB flash (1GB for persistence), and, without updating, configuring, adding, modifying, etc., want to install it to my 8GB flash (in another USB port). Is this possible? Will this result in fewer errors? Will it still hang after I update it?

I tried the boot install option, but it gave no feedback, so I quickly powered-down the PC. Ubuntu's installation wizard frightened me. There is no indication of what it is doing, and it must not write anything to my hard drive. (After a few interactions with it, it still had not requested an installation destination and had long scary pauses.) The only documentation I could find ([https://help.ubuntu.com/6.06/book/ubuntubook-ch7-kubuntu/official-Ubuntu-Book-Kubuntu-Chapter.html](https://help.ubuntu.com/6.06/book/ubuntubook-ch7-kubuntu/official-Ubuntu-Book-Kubuntu-Chapter.html)) implies that it supports installation only to a fixed internal drive. Is this true? If so, can this be overridden?

What do you suggest?

Thank you for your help.
[SIZE=2]
[/SIZE]

---

### Post by mikewhatever on 2010-10-30
If it takes too long to find something, just ask. After all, people are here to help. Information on both persistence and installation can be found at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download).
What exactly do you mean by 'configured the desktop'? What did you do?
Installing Ubuntu requires writing to the installation partition. If you don't want that, then you can install.

---

### Post by Pumpaw on 2010-10-30
Thank you for your speedy reply and your willingness to help. I'm sorry I  didn't ask sooner. (This is the first time I've joined a forum;  usually, I can find answers myself, or I'll find another program. This  time, from what little exposure I've had to Ubuntu when it was  (re-)booting, I've been extremely impressed and think my efforts to get  it to work properly will be worth it.)

I just tried booting from my 2GB flash (on which I've made no  modifications) to make a list, per your request, of some of the  configuration modifications I made to my 8GB version (e.g., customizing  the mouse, task-bar, system-bar, theme, various options in applets,  system programs, etc.). The 2GB flash stopped booting at exactly the  same place the 8GB did! So, now my assumption is that there's something  about having a persistent store on the flash that results in failure  after some number of boots or some amount of time. Could that be true?  If so what could cause that, and why?

The link in your reply points to the starting point I used when trying  to find answers to my questions. Most of my frustration results from the  apparent insertion of "or" operators between search words. Is there  some way to selectively change them to "and"s (or use some simple  "grep"-type search)?

I'm sorry, but I don't understand your last two sentences. Can my "installation partition" be my other USB flash drive? Why would the installation process not write to the "installation partition"?

Perhaps I should start my questioning again and focus on one problem at a time, starting with the failure of both flash drives to boot, even though they both have been able to successfully boot several times.

Why does booting stop with the last "terminal" message "Begin: live session user... ..." and the splash progress indicators sequencing normally? What information do you need to help me, and how should I obtain it?

Many thanks.

---

### Post by mikewhatever on 2010-10-31
> **Pumpaw said:**
> ...


The link in your reply points to the starting point I used when trying  to find answers to my questions. Most of my frustration results from the  apparent insertion of "or" operators between search words. Is there  some way to selectively change them to "and"s (or use some simple  "grep"-type search)?

The link I posted has info on how to put the iso on usb with persistence. I don't know anything about anyone inserting things between search words. Do you mean Google, ubuntuforums...?

> I'm sorry, but I don't understand your last two sentences. Can my "installation partition" be my other USB flash drive? Why would the installation process not write to the "installation partition"?
All I said was, 'if you want to install, you must allow the installer to write to the installation partition, otherwise, you can't install'. Sorry if that was obvious.

> Perhaps I should start my questioning again and focus on one problem at a time, starting with the failure of both flash drives to boot, even though they both have been able to successfully boot several times.

Very good idea.
I've never stumbled on that particular problem and so can't be of any practical help.

---

### Post by Pumpaw on 2010-10-31
Thank you very much for another speedy reply.

> I don't know anything about anyone inserting things between search words. Do you mean Google, ubuntuforums...?

I mean if I wish to search for "Stops booting after 'Begin: live session user... ...'", instead of getting hits for 250 threads with the words "stops" or "booting" or "after" or "begin" or ..., I'd like to search for _all_ of the words in the search box, or at least all in the "Begin..." line.

> ...if you want to install, you must allow the installer to write to the installation partition..

Thank you; I couldn't imagine it being otherwise! So, is it possible to install from one USB flash drive (persistence-type or not) to another? If so, will my fixed/hard drive be written to without my permission?

> I've never stumbled on that particular problem and so can't be of any practical help.

Thank you, mikewhatever, for being so responsive, and for getting me started. What do you suggest I do to get help?

---

### Post by mikewhatever on 2010-10-31
> **Pumpaw said:**
> 

I mean if I wish to search for "Stops booting after 'Begin: live session user... ...'", instead of getting hits for 250 threads with the words "stops" or "booting" or "after" or "begin" or ..., I'd like to search for _all_ of the words in the search box, or at least all in the "Begin..." line.> 

Really don't know. When I search for "Begin: live session user", only your thread turns up.



[quote]Thank you; I couldn't imagine it being otherwise! So, is it possible to install from one USB flash drive (persistence-type or not) to another? If so, will my fixed/hard drive be written to without my permission?

I think so, yes, and I don't see why the installer should write to the hdd. It doesn't even automount partitions.


[quote]Thank you, mikewhatever, for being so responsive, and for getting me started. What do you suggest I do to get help?

Hm..., the problem is so vague, I am not sure. I'll certainly post if I think of something.

---

### Post by Pumpaw on 2010-11-01
Thank you for your answers.

Your last response, implying that you've never heard of the boot loader failing the way it has been for me, leads me to believe that the program I've been using to create the persistent USB flash images (LinuxLive USB Creator ("Lili") version 2.6, Compatibility List 2.6.5, which includes several Ubuntu 10.10 versions) is incompatible with Ubuntu 10.10. What program and what version should I use?

Thank you.

---

### Post by mikewhatever on 2010-11-01
The link I posted earlier (#2) has the info on the recommended program for Windows. Another one I know of is Unetbootin.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

PS: Just looked at LinuxLive USB Creator, the site looks good.

---

### Post by Pumpaw on 2010-11-01
Thank you for your suggestions. I'll try them over the next week or so...

---

### Post by Pumpaw on 2010-11-18
After much more research, I think I know why I was having so many problems booting my persistent flash, and after reading a lot more about potential boot loader conflicts between the Vista and Linux-Grub boot loaders, I decided that the only way for me to evaluate Ubuntu is to install it on my 8GB flash drive.

I tried the installation from within Ubuntu (running on my 2GB live persistent flash), but after trying a lot of combinations of options (even resorting to using GParted, which crashed a few times), was unsuccessful.

Running the installer from the Grub menu appeared to be successful, although it provided no opportunity to custiomize the installation (e.g., it created a swap partition even though I do not need one). But, the 8GB flash will not boot. The last error message is:
[INDENT]Gave up waiting for root device. Common problems:
    ...
ALERT! ldev/disk/by-uuid/<UUID> does not exist.
Dropping to a shell!
BusyBox...
   ...
(initramfs)
[/INDENT]At this point, the keyboard is completely dead, and I must power-cycle to reboot.

Your documentation says to try uncommenting the "GRUB_DISABLE_LINUX_UUID=True" statement in etc/default/Grub, and running update-grub. Eventually, I figured out how to edit the line from my 2GB persistent flash version, which changed the file name to "grub". I could not figure out how to run update-grub on the 8GB flash from the 2GB flash.

The 8GB's etc/default/Grub file has been replaced by the modified file, now named "grub", but it still won't boot, behaving exactly as before. Choosing "recovery mode" from the Grub menu resulted in the same error information, followed by more error output and a frozen keyboard.

Choosing "e" from the Grub menu produced the following:

[INDENT]recordfail
ismod part-msdos
ismod ext2
set root = '(hd0, msdos1)'
search --no-floppy --fs-uuid --set <UUID>
linux /boot/varlinuz-2.6.35-22-generic-pae root=UUID=<UUID. ro quiet splash
initrd Root/initd.img-2.6.35-22-generic-pae
[/INDENT]I don't know what this means, but it does not look right. The installation created two partitions on the 8GB flash, and said that at least the main file system was ext4, so why does it say "ext2"? Why are there "msdos" references? Why "hd0"? Shouldn't it be "sda"?

The 2GB live flash needs the "noapic" option on my PC. Could that be a problem with the installed version on the 8GB flash? If so, how can I add that option?

Thank you for your help.

---

