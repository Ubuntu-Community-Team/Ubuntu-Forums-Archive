---
title: "Ubuntu ate Fedora's grub?"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by schmutztaucher on 2010-02-24
I recently had disk problems and had to replace. I currently have one disk. First thing I did was install XP then Vista then Fedora 12. Everything worked great. I then installed Ubuntu (karmic) and I had problems. My problem is that there is no way to boot to Fedora. I can boot to Ubuntu, XP and Vista fine but no Fedora or any remnants of Its boot loader.

So I went to menu.lst in Ubuntu to add fedora there. But my menu.lst was empty. Screen shots attached. I know that I need to point Ubuntu's grub to Fedora but something seems fishy.

Any and all help would be appreciated.

---

### Post by QIII on 2010-02-24
menu.lst no longer exists with GRUB2.

Have you tried

```
sudo update-grub2
```If that doesn't work, you may have to make an entry in 40_custom.  I had to do that for OpenSolaris.  (Now I run it and Fedora in virtual machines...)

Take a look here. 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you have questions (which I am sure you will!) post back.  The section you want to look at is 

**6.  Adding Entries to Grub 2**

---

### Post by schmutztaucher on 2010-02-25
OK. So the easy way didn't work and I took a look at the link. After some consideration, It is my understanding that this is what we are looking for in the custom..
```
#!/bin/sh
exec tail -n +3 $0
```I got this from my grub.d folder. Can you have 2 customs? I realize the increment of 10 and the importance of the sequence of the numbers. So I would make a 50_custom. Now as for the pointing to Fedora I would change the exec tail? So I would perhaps look like

```
#!/bin/sh
exec tial -n +4 $0
```The +4 would coincide with the sda Number? Would I need any more code? as some of the examples had more. Sorry for all the questions.

---

### Post by NefariousNobo on 2010-02-25
I personally think the easiest way of doing that is to use Fedora's GRUB as the main bootloader, and have Ubuntu's loaded by Fedora's.

---

### Post by QIII on 2010-02-25
No.  Use 40_custom (easier than adding another xx_custom) and do NOT modify the "tail" line.

You make custom entries AFTER that line.

Don't do anything right at the moment.  I will need to get home to my Ubuntu machine.

But what you are going to need to do AFTER the "tail" line is add something similar to this:

```
menuentry "Fedora" {
set root=(hdx,y)
chainloader +1
}
```where x is the drive and y is the partition.

---

### Post by schmutztaucher on 2010-02-25
I can wait. My Custom for my Windoze machines looks like this
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 12 Custom" {
set root=(hd0,10)
linux /sysrcd/rescuecd subdir=sysrcd setkmap=us
initrd /sysrcd/initram.igz
} 
```Eventually I would like to turn "Other Operating Systems" Into valid menu entries be for now I want to figure this problem out. Thanks for the help.

---

### Post by oldfred on 2010-02-25
QIII entry will work but you also have to install Fedora's grub to that partition so you have something to chainload to:

See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

---

### Post by QIII on 2010-02-25
Quite right, OldFred.

Thanks for pointing out that important detail.

Sometimes things are so obvious to us that they escape our attention when advising others.

Has to be that way for both Fedora and OpenSolaris.

---

### Post by schmutztaucher on 2010-02-25
Alright so after doing so research an links you guys suggested I think I might have the answer. It involves reinstalling both distros. Let me know what you think...

Install Fedora first but create partitions for Fedora before installation. Fedora creates LVM by default and its a bit tricky to handle LVMs.
Create delete distros and install three partitions using GParted CD.
1. SWAP - 512MB is enough.
2. ext3 -- 45GB for Fedora /
3. ext3 -- 52.6GB for Ubuntu /

Start Fedora installation and assign / mount point to ext3 partition. Installer will detect SWAP itself. Leave other ext3 partition as it is.

Start Ubuntu installation and assign / mount point to second ext3 partition. Ubuntu installer will detect and use same SWAP partition and setup dual boot itself.

After that edit a custom to point to Fedoras grub.

How does that sound?

---

### Post by schmutztaucher on 2010-02-26
Worked like a charm. All is not lost, I will use this knowlege to create custom boot pointers for my windoze partitions.

---

