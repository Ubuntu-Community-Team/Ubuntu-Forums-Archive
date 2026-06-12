---
title: "Need a little help with Grub please"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by Catsworth on 2006-07-31
Ok, here's the story so far:

1.  Laptop HDD is 60Gb in size
2.  Partitioned HDD into:
[LIST]
[*]35Gb (NTFS)
[*]12Gb (Ext3)
[*]12Gb (Ext3)
[*]1Gb (/swap)
[/LIST]
3.  Installed Windows XP Pro
4.  Installed Ubuntu
5.  Everything's working ok at this point and dual-booting nicely.  I even managed to edit the Grub bootloader so that the default wasn't saved, the time before it took the default option was shorter, and the order/wording was slightly different.
6.  Installed Back|Track
7.  Rebooted machine to find that Back|Track has installed its own bootloader (Lilo) over the top of the Grub one and that my laptop now will only boot directly into Back|Track.  Not only that but the bloody thing won't recognise my wireless card so I can't get online to search for answers/help.
8.  Manage (after 3 hours of searching and fiddling and borrowing other people's computers) to get the Lilo editor to work, and some how manage to add XP to the boot options so I can now boot into Windows again and access the internet.
9.  Other than the install CD I have no way of booting into Ubuntu.

So, that's where I am now.

What I'd really like to do is:

a) Get Grub re-installed.  I've tried a couple of methods I found using the search facility here and neither of them have worked (from the command line, and using the 'rescue' facility on the install disc).
b) Add Back|Track to Grub so that I am triple-booting.

If someone could please help me accomplish this I would be very grateful 'cause at the moment I'm starting to get really miserable.  I enjoy a challenge as much as the next person, but this is getting me down now.

Thanks.

---

### Post by Paerez on 2006-07-31
Well, for (A) do this:

-Boot ubuntu's livecd (the install cd you used to install ubuntu)
-Open a terminal and run:
```
sudo grub-install (hd0)
```

If that doesn't work, you need to run:
```
sudo grub
root (hd0,1)
setup(hd0)
quit
```
to manually set grub.

I don't know what back|track is, but if I figure it out I can help you with B.

---

### Post by Catsworth on 2006-07-31
Thanks, I'll try that now.

Back|Track is a pentesting distro, more details here:

[http://www.remote-exploit.org](http://www.remote-exploit.org)

Thanks again.

---

### Post by Catsworth on 2006-07-31
> **Paerez said:**
> 
```
sudo grub
root (hd0,1)
setup(hd0)
quit
```

Ok, fantastic!!!  That worked a treat, I now have access to my Ubuntu installation :D   You're an absolute :KS thank you so much :)

I've got menu.lst edited again so that it reflects how I like things setup.

I've tried adding Back|Track to it but I can't seem to get it right.  Any thoughts on that would be greatly appreciated :)

---

### Post by adrian15 on 2006-07-31
If you come across the same problem again you can try my tool: Super Grub Disk which reinstalls grub into the MBR automatically and if you do not want to loose backtrack lilo you can Boot your OS again to boot Ubuntu from that and fix whatever it is from ubuntu.

Check [http://adrian15.raulete.net/grub/](http://adrian15.raulete.net/grub/)

adrian15

---

### Post by adrian15 on 2006-07-31
> **Catsworth said:**
> 
I've tried adding Back|Track to it but I can't seem to get it right.  Any thoughts on that would be greatly appreciated :)

Can you copy-paste Back|Track lilo.conf so that I can help you editing your menu.lst ?

adrian15

---

### Post by Catsworth on 2006-07-31
Hi Adrian,

I think that this is the section of the lilo.conf that controls the Back|Track boot:

```
# Linux bootable partition config begins
image = /boot/vmlinuz
root = tmpfs
label = Linux
read-only
# Linux bootable partition config ends
```

Thanks for your help with this, I really appreciate it.

---

### Post by Paerez on 2006-07-31
ah I didn't realize that Auditor had become backtrack, I see.

Isn't this a livecd? So you don't really need to have an entry in grub, since bootable cd detection happens before grub.

---

### Post by Catsworth on 2006-07-31
Hi :)

Yeah, it's a live CD but there's also an option to do a HDD install (which installs the Lilo bootloader.....which is how I got into this mess :(  ).

The HDD install runs faster and also gives you the opportunity to upgrade the various applications as new versions become available - that's why I went down the install route.

Thanks.

---

### Post by Paerez on 2006-07-31
The lilo entry was really weird because it mentioned the tmpfs...

check out this:
[http://forums.remote-exploit.org/showthread.php?t=168](http://forums.remote-exploit.org/showthread.php?t=168)
but adjust it to the correct partitions.

---

### Post by Catsworth on 2006-08-01
Excellent, thanks for the link - I'll take a look at that tonight and let you know how I get on.

Cheers,

Cats

---

### Post by Catsworth on 2006-08-01
Ok, I added the following:

```
title Backtrack
root  (hd0,3)
kernel  /boot/vmlinuz rw root=/dev/hda
```

to my '/boot/grub/menu.lst' and now I get the following error message when I try to boot to Back|Track:

```
Kernel Panic - Not Syncing
VFS:Unable to mount root fs  on unknown-block(3,0)
```

Any thoughts?

---

### Post by Catsworth on 2006-08-02
Sorry to be a pain but does anybody have any more thoughts on this?

Thanks

---

### Post by Catsworth on 2006-08-02
Sorry - double post, please delete.

---

### Post by Family_Guy on 2006-08-14
I've got the same problem except I don't have windows installed. Just Ubuntu and Back|Track. When I installed backtrack, it installed lilo and now it boots into backtrack. 

I've tried the commands above and they both failed...

sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.

sudo grub-install (hd0)
bash: syntax error near unexpected token `('

sudo grub
root (hd0,1)
Filesystem type unknown, partition type 0x5
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1

---

### Post by adrian15 on 2006-08-15
> **Catsworth said:**
> Ok, I added the following:

```
title Backtrack
root  (hd0,3)
kernel  /boot/vmlinuz rw root=/dev/hda
```

to my '/boot/grub/menu.lst' and now I get the following error message when I try to boot to Back|Track:

```
Kernel Panic - Not Syncing
VFS:Unable to mount root fs  on unknown-block(3,0)
```

Any thoughts?

Sorry about not answering sooner. Try with this:

```
title Backtrack
root  (hd0,3)
kernel  /boot/vmlinuz rw root=/dev/hda4
```

The strange thing about backtrack is the lack of an initrd file.

If it does not wor... you can try [Super Grub Disk]("http://adrian15.raulete.net/grub/") latest version. Boot Other Oses -> Boot Gnu/Linux and try to boot it but it will quite difficult because this option presumes there's an initrd.

adrian15

---

### Post by iSkylla on 2007-03-20
I don't know how old this thread is, but I too am having this kernel/boot problem with BT2.

---

