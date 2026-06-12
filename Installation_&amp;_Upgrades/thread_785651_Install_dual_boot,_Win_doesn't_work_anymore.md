---
title: "Install dual boot, Win doesn't work anymore"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Sathors on 2008-05-07
So I've reinstalled Heron yesterday, and I had already Gutsy so I've formated the partitions with Gutsy, I resized some things (Win for instance), and I reinstalled Heron on newly created partitions.

Ubuntu and Vista are on the same disk, and vista is supposed to be the main partition.

My problem is : when I boot the computer, I access the grub, Heron works (more or less ^^), but when I choose Vista, the computer thinks just a second, and reboot directly.


I think I've done something wrong during the installation/desinstallation of ubuntu.

One more precision : to do the operation, I used Gperted and it took nearly 2 hours to resize the windows partition, for it had unmovable files in it.
And now when I open Gparted, Ubuntu can't read the NTFS partition, I mean there a little sign of warning and I can't even know the space available in them.

Thanks for your help !

(sorry for the mistakes, I'm french and I don't have much means to practice ^^)

---

### Post by genbuntu on 2008-05-07
umm.. I'm not that *nix knowledgeable to be able to guide you to change GRUB 's entry  but here is something you can definitely give a shot.

Burn a Super Grub Disk and boot with it. The instructions are pretty simple and try to let it automatically repair the boot-loader(s) . 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Sathors on 2008-05-07
I've burned the livecd, but the computer doesn't boot on it ant takes me to the grub once more ....

---

### Post by genbuntu on 2008-05-07
> **Sathors said:**
> I've burned the livecd, but the computer doesn't boot on it ant takes me to the grub once more ....

Maybe you already did this but just to confirm:  Did you change the boot setting in your system BIOS to "boot from cd-rom" first ?

---

### Post by Sathors on 2008-05-08
Yeah I did it, and when I put the cd in the drive during my Ubuntu session, an error window tells me there's a problem of mounting the device, something like that.

---

### Post by Herman on 2008-05-08
> One more precision : to do the operation, I used Gperted and it took nearly 2 hours to resize the windows partition, for it had unmovable files in it.
And now when I open Gparted, Ubuntu can't read the NTFS partition, I mean there a little sign of warning and I can't even know the space available in them.:) That means your Vista partition needs a file system check.
I don't know very much at all about Windows Vista, but I guess you need to boot your Windows Vista 'Installation' CD and boot it into a 'recovery console' of some kind and run CHKDSK with some options, likely the /f or /r switch. 
It is recommended at the GParted website to run CHKDSK on an NTFS partition after resizing it as a good thing to do whether you need it or not. It looks like on this occassion it is needed.
I think it is a good idea to run CHKDSK before resizing an NTFS partition too, GParted can work a lot easier then.

If you don't have a WIndows Vista installation CD, (because your computer didn't come with one), you can go to this website, [NeoSmart Windows Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), and get one.

---

### Post by Sathors on 2008-05-08
Thanks for your advice, I'll try it, but in fact I have one more problem ^^
I've used testdisk following a thread about the grub, and I'e rewrited the MBR so now I think I don't have grub anymore so it boots on Vista, and as Vista does not work it keeps rebboting endessly ...

---

### Post by Herman on 2008-05-08
:( Oh, I see.

Microsoft has tied Vista hopelessly to the hard disk signature in the hard disk's MBR, if you read this link you will understand, [Vista's MBR Disk Signature]("http://www.multibooters.co.uk/mbr.html").
I am afraid that probably TestDisk will have written a new Disk Signature along with the new MBR.

I think you can still fix Vista if you want though, if have your Windows Vista Installation CD. 
Even if you don't, you can still fix Vista by going here, [NeoSmart Windows Vista Recovery Disk Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download a Windows Vista Recovery CD.
You will need to boot it to some kind of recovery console and enter some commands probably. As I don't use Windows Vista, I don't know the exact commands yet, but I will try to find out for you.

You can re-install GRUB to your hard disk's MBR any time you like, GRUB does not harm the disk signature in the MBR.

---

### Post by CLomax on 2008-05-08
Sorry to hijack the thread but it is relevant.

Does this mean that I can write over MBR with grub to solve the problem here?
[http://ubuntuforums.org/showthread.php?t=786505](http://ubuntuforums.org/showthread.php?t=786505)

---

### Post by Herman on 2008-05-08
:) Hello CLomax,
I think your problems are a little different
> Does this mean that I can write over MBR with grub to solve the problem here?
[http://ubuntuforums.org/showthread.php?t=786505](http://ubuntuforums.org/showthread.php?t=786505)I'm not sure, I'll think about it. I bet we can fix yours too but I'm out of time right now and I have to go in a hurry, but I'll be back later on. :)

---

### Post by CLomax on 2008-05-08
> **Herman said:**
> :) Hello CLomax,
I think your problems are a little different
I'm not sure, I'll think about it. I bet we can fix yours too but I'm out of time right now and I have to go in a hurry, but I'll be back later on. :)

Awesome, thank you, reply whenever you like, I'll be on stand by :).

---

### Post by Sathors on 2008-05-09
For my part everything is resolved, I've runned the recovery cd of Vista which enabled me to boot with Vista, and I used the terminal of the Heron livecd to reinstall the grub, so now I can access both Vista and Ubuntu.

Thanks to all of you !!!

---

### Post by Herman on 2008-05-09
:) Okay, very good, well done Sathors. :)

For others who may be browsing Ubuntu Web Forums looking for answers about problems with dual booting with Vista, here is a good website to look in, [Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/").
That's the web site I will be studying this weekend to try to learn how to help Vista users better in the future. I think most of the answers can be found somewhere in that website, it just requires some time to read and mentally digest all that information.

Sathors I'm happy that yours is fixed and thanks for letting me know. 

Regards, Herman :)

---

