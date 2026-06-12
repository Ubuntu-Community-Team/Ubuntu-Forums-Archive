---
title: "backing up MBR using dd"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by yotamoo on 2011-09-18
Hi, I came across this [guide]("https://help.ubuntu.com/community/WindowsDualBoot") as I wish to install windows along side my currently installed ubuntu. So, to back up my MBR I need to use dd command. I read the manual but failed to understand something:
if I run this command [PHP]dd if=/dev/sda of=/mbr.bin bs=446 count=1[/PHP] to back up my MBR, where will the back-up file be?
The command doesn't specify. To recover, I saw that I need to run [PHP]dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1[/PHP], but after running the first command there was no file in there. 
So as I said, my question is where is the back up file, and also after recovering MBR, will grub automatically load the boot menu screen?
Hope I am clear enough, thanks!

---

### Post by Hakunka-Matata on 2011-09-18
of=/mbr.bin translates to : out file = /mbr.bin
mbr.bin is the filename and [B]EDIT: disregard text in red, it's incorrect.
[/B][COLOR=Red]it's in whatever directory you were in when you ran the above command.

[COLOR=Black]Corrected: mbr.bin is the filename, and as the / suggests, it is located in the root '/', directory[/COLOR]
[/COLOR]

---

### Post by YesWeCan on 2011-09-18
A warning: dd is a very primitive unix command and is very dangerous. I'd advise not to use it unless you have read and understood the man page: [http://linux.die.net/man/1/dd](http://linux.die.net/man/1/dd) or you are being advised by someone who understands it.

You should not need to back up and restore the Grub boot code in the MBR because you can just as easily reinstall Grub using the live CD/USB after you have installed Windows. See: [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

---

### Post by ottosykora on 2011-09-19
>dd if=/dev/sda of=/mbr.bin bs=446 count=1  <

in such case the dd will try to write the of (=output file) to the root of your linux partition you are running this command from.

If you do this from installed ubuntu then this may have problem, as you have no write rights to this position, you would need to include sudo before.

Otherwise you can specify also some path you can write to, like 
of=/home/yourname/...

If you try to make a backup of original mbr before installing anything over it (grub) then you need to give it some other place where you can write to, of=/dev/sda2 might work in case of w7, or similar.

To make a backup of mbr is certainly good idea, as grub installation does not do that and you need windows boot disk to fix it in case you want remove linux later for example.

But in your case when you are installing windows *after* linux, then yes, it might be more efficient to reinstall grub after the windows installation.

There are also utilities in net which do it all automatic, I remember one called savembr, this did work well , but stored the mbr file on a floppy ;-)

---

### Post by srs5694 on 2011-09-19
> **Hakunka-Matata said:**
> of=/mbr.bin translates to : out file = /mbr.bin
mbr.bin is the filename and it's in whatever directory you were in when you ran the above command.

A small but important correction: The slash (/) character in Linux is a directory separator, and when it comes at the beginning of a filename, it means to read the path beginning from the root (/) of the filesystem tree. Thus, /mbr.bin means the mbr.bin file *in the root directory*, no matter what directory you were in when you issued the command.

It looks to me as if the guide author omitted a step (copying the file to /media/sda) or edited the procedure incompletely during the writing process.

---

### Post by Hakunka-Matata on 2011-09-19
> **srs5694 said:**
> A small but important correction: The slash (/) character in Linux is a directory separator, and when it comes at the beginning of a filename, it means to read the path beginning from the root (/) of the filesystem tree. Thus, /mbr.bin means the mbr.bin file *in the root directory*, [COLOR=Red]no matter what directory you were in when you issued the command.[/COLOR]

It looks to me as if the guide author omitted a step (copying the file to /media/sda) or edited the procedure incompletely during the writing process.

@srs5694:  Thanks for the correction, and reminder:
post# 2 has been corrected

---

