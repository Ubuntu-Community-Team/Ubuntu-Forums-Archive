---
title: "broken karmic install."
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by justborn on 2009-10-11
i did install Ubuntu Karmic Koala two days ago, and then it collapsed after the first update.


the error occurs at boot itself,so there is no chance of getting into the shell([COLOR="Red"]recovery mode[/COLOR]) and repairing the system. 


the error was as such```
Loading Grub....  [COLOR="Red"]#process fails,I don't get bootloader[/COLOR]
flesystem block missing   [COLOR="Red"]#someting like this[/COLOR]
filesystem block missing
press any key to continue... 
``` 
after pressing any key,the same this is repeated.


I had put on all the backup data on the system(from my jaunty jacklope),and [COLOR="RoyalBlue"]don't wanna lose them[/COLOR]. 


at present I'm treading this post using my live-cd.
please suggest how to recover using the same live-cd(karmic-desktop),or any other method,by using [COLOR="Red"]grub rescue cd[/COLOR] or something else.

---

### Post by justborn on 2009-10-12
i can actually get the bootloader now,but it's no good.this is what i get when i try to boot([COLOR="Red"]also in recovery mode[/COLOR]).
```
mount: mounting /sys on /root/sys failed : no such file or directory
mount: mounting /dev on /root/dev failed : no such file or directory
done
mount: mounting /sys on /root/sys failed : no such file or directory
mount: mounting /proc on /root/proc failed : no such file or directory
target filesystem doesn't have /sbin/init
no init found. try passing init=bootarg

```
and then it enters busybox
```
busybox xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx. [COLOR="Blue"]#"xxx...,refres to details like version"[/COLOR]

[initramfs]
```

---

### Post by ranch hand on 2009-10-12
OK, fun times.

Can you read your files from the live CD?  Does everything look all right as far as you can see?

---

### Post by justborn on 2009-10-12
> **ranch hand said:**
> OK, fun times.

Can you read your files from the live CD?  Does everything look all right as far as you can see?

yes,of course,in fact i am writing this post using  my live cd.

as already mentioned the 1st post,I had the problem only after the first update and not after installation

---

### Post by ranch hand on 2009-10-12
If your installation looks good, before we try something hard (my standard practice is to make everything harder than needed) lets try to get into your installation through the boot menu.

You need to know the partition that is your / partitions (root).  If you are on one partition that is the one we want.

You can double check if needed by using gparted on the LiveCD.

This is the type of entry that you need to try;
```

         set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img

```Write that down, along with the partition information, and reboot.

Highlight the menu entry and hit e.  This will get you to the editing function of Grub2.

Put in my entry suitably edited to your installation.  If you are familiar with grub-legacy the drive is numbered like that.  The partition uses the same number as gparted does.  Basically, if thisis on your first drive and first partition the entry will be (hd0,1).  Drives counted starting with 0 and partitions counted starting with 1.

Make sure you edit both places where the partition is mentioned.

When finished typing that in hit Ctrl x to boot.

I think that will get you in.

---

### Post by justborn on 2009-10-12
> **ranch hand said:**
> If your installation looks good, before we try something hard (my standard practice is to make everything harder than needed) lets try to get into your installation through the boot menu.

You need to know the partition that is your / partitions (root).  If you are on one partition that is the one we want.

You can double check if needed by using gparted on the LiveCD.

This is the type of entry that you need to try;
```

         set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img

```Write that down, along with the partition information, and reboot.

Highlight the menu entry and hit e.  This will get you to the editing function of Grub2.

Put in my entry suitably edited to your installation.  If you are familiar with grub-legacy the drive is numbered like that.  The partition uses the same number as gparted does.  Basically, if thisis on your first drive and first partition the entry will be (hd0,1).  Drives counted starting with 0 and partitions counted starting with 1.

Make sure you edit both places where the partition is mentioned.

When finished typing that in hit Ctrl x to boot.

I think that will get you in.
can I not edit the grub entry from this live cd session itself ,without rebooting?

---

### Post by ranch hand on 2009-10-12
You could try to do that.  You would need to edit the /boot/grub/grub/cfg file.  This file is not really smart to edit because it is over written every time update-grub is run.  The permissions for it have it as read only for root so you will have to change that to edit it.

To try it you will have to reboot.  For me, it would just be easier to edit the menu when it comes up.

---

### Post by justborn on 2009-10-12
> **ranch hand said:**
> You could try to do that.  You would need to edit the /boot/grub/grub/cfg file.  This file is not really smart to edit because it is over written every time update-grub is run.  The permissions for it have it as read only for root so you will have to change that to edit it.

To try it you will have to reboot.  For me, it would just be easier to edit the menu when it comes up.


to inform u i have linux on /dev/sda(/dev/sda1 my ext4 partition),so does that change the boot entry?

---

### Post by ranch hand on 2009-10-12
If I have your info right, then your entry would be;
```

        set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 so quiet splash
        initrd /initrd.img

```
This is a "symbolic" menuentry that is one of the standard entries that can be used in grub2 custom files.  I use it for all my installs as you never have to update it for the kernel.

---

### Post by justborn on 2009-10-12
> **ranch hand said:**
> If I have your info right, then your entry would be;
```

        set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 so quiet splash
        initrd /initrd.img

```
This is a "symbolic" menuentry that is one of the standard entries that can be used in grub2 custom files.  I use it for all my installs as you never have to update it for the kernel.

will try it and revert back in some time.

---

### Post by justborn on 2009-10-12
dude, actually the probo was qiute small,when i pressed e to edit the boot path ,i saw that it was set to boot from sdb1,instead of sda1,i just corrected that and now i am posting this from my system install itself.

u helped me in a way,thanks a lot.dude but how do i make this permanent.(i.e sdb1 to sda1 ,for both normal and recovery mode)

---

### Post by ranch hand on 2009-10-12
The question is why is grub2 seeing your drive as sdb instead of sda?  That is strange.

Do you have a second drive?

The first thing I would do is run "sudo update-grub" and see what comes up in your /boot/grub/grub.cfg file.  You will have to "gksudo gedit /boot/grub/grub.cfg" to get into it as that is a root owned file.

That may get things right.

You can also put the correct menuentry in your /etc/grub.d/40_custom file.  That will need editing for the correct kernal unless you use the entry I gave you.  I would save the file to a different name like "06_custom" to put it at the top of your menu.

From one of my custom files;
```

 #!/bin/sh
# This file is an example on how to add custom entries

echo "Adding DailyGrub on sda22" >&2
cat << EOF
menuentry "Adding DailyGrub on sda22" {
        set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img
}
EOF

```It needs to look like that.  The stuff between the { and } is what you are actually using to boot.  The stuff between the " " on the "adding" line is what you see in terminal when you run update-grub.  The stuff between the " " on the "menuentry" line is what you see on the screen menu.

You need to run
```

sudo update-grub

```
to get this into your /boot/grub/grub.cfg file.

Yes I know I need to remove the "adding" on the menuentry line in this example.  So I cut and paste.  I am real good at typos.

---

### Post by justborn on 2009-10-12
update-grub output
```
arpit@arpit-desktop:~$ sudo update-grub
Your /usr is broken, please fix it before call this wrapper!
```

---

### Post by ranch hand on 2009-10-12
Well, that is interesting.  This probably explains the sdb thing.

I think that I would go to synaptic and do a search for grub.  Find grub2 (meta package for grub2), grub-common and grub-pc.  Mark the buggers for reinstallation and apply.  See if that does not fix it.

Make sure that you do not have any grub-legacy stuff still installed while you are there.  If it is remove it first.  Grub-legacy is "grub .097"  grub2 is 1.97beta3.

There has been some problems with the installer and grub2 recently.  You have probably been lucky enough to get it.

Do not reboot until this is straight.

---

