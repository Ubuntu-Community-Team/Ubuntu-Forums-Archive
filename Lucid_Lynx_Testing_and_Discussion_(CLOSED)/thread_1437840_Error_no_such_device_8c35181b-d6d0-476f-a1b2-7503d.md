---
title: "Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7. grub rescue"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hoboy on 2010-03-24
After installation I was asked to restart.
I go automatically to
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.
grub rescue>
when I use ls
it show (hd0)
please help
When I launch the computer then press down SHIFT, i get the same error message.
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.

---

### Post by VMC on 2010-03-24
> **hoboy said:**
> After installation I was asked to restart.
I go automatically to
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.
grub rescue>
when I use ls
it show (hd0)
please help
When I launch the computer then press down SHIFT, i get the same error message.
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.
That looks like a UUID number. Boot with Livecd and output ```
sudo fdisk -l **and** sudo blkid
```

---

### Post by hoboy on 2010-03-24
> **VMC said:**
> That looks like a UUID number. Boot with Livecd and output ```
sudo fdisk -l **and** sudo blkid
```

Here is the result:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b322a47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1176     9437184   27  Unknown
/dev/sda2   *        1176       26247   201388032    7  HPFS/NTFS
/dev/sda3           26247       38914   101743616    7  HPFS/NTFS
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="9E84FE3384FE0E11" LABEL="WinRE" TYPE="ntfs"
/dev/sda2: UUID="98D844ACD8448B08" LABEL="System" TYPE="ntfs"
/dev/sda3: UUID="74081645081606B0" LABEL="Data" TYPE="ntfs"
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2010-03-24
I do not see a Ubuntu or Linux partition on your drive?

---

### Post by hoboy on 2010-03-24
> **lindsay7 said:**
> I do not see a Ubuntu or Linux partition on your drive?

I have used wubi to install ubuntu.
I was using dual booting with vista
before I started to upgrade I asked.
and now i can not even get into the windows

[http://ubuntuforums.org/showthread.php?t=1437755](http://ubuntuforums.org/showthread.php?t=1437755)

---

### Post by lindsay7 on 2010-03-24
I would guess that something went wrong with this  

>  Re: I have 9.10 wubi installation can I upgrade 10.04 ?
to upgrade I have used.
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
But
It seemed like my machine hangs on:
Found linux image: /boot/vmlinuz-2.6.32-17-generic
any suggestion ?

I do not know much about wubi installation so I can not help you.  Can you just reinstall your old version of ubuntu with wubi and then wait until 10.4 is out before updating? I would use the "update-manager -d" way to do it.

---

### Post by hoboy on 2010-03-24
> **lindsay7 said:**
> I would guess that something went wrong with this  



I do not know much about wubi installation so I can not help you.  Can you just reinstall your old version of ubuntu with wubi and then wait until 10.4 is out before updating? I would use the "update-manager -d" way to do it.

Mnnnn the problem is that I can not even get to the windows, when _I launch the computer it goes directly to the grub rescue>

---

### Post by andrewthomas on 2010-03-24
> **hoboy said:**
> Mnnnn the problem is that I can not even get to the windows, when _I launch the computer it goes directly to the grub rescue>
This should help you.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-03-24
> **andrewthomas said:**
> This should help you.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

No, it won't help with a Wubi install!

Edit: I may have spoken too soon, sorry. It can't hurt to try restoring the windows mbr.

@hoboy, do you have a Windows disc to restore the Win MBR?

---

### Post by kansasnoob on 2010-03-24
I haven't tried a Wubi install of Lucid yet but from the release notes:

> Wubi as included on the ISO images is unable to enter its second stage of installation, so you will not be able to install inside Windows using just an ISO image in this beta release. As a workaround, users who are installing the Ubuntu Desktop Edition can download the stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed for 10.04 LTS Beta 2. (541607) 

The bug they are referring to:

Lucid: Wubi drops immediately into grub shell on reboot  

[https://bugs.launchpad.net/wubi/+bug/541607](https://bugs.launchpad.net/wubi/+bug/541607)

---

### Post by andrewthomas on 2010-03-24
> **kansasnoob said:**
> No, it won't help with a Wubi install!
Sorry, how about.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by hoboy on 2010-03-24
I have no choice but to reinstall vista, well that is beauty of testing new softwares.

---

### Post by kansasnoob on 2010-03-24
> **hoboy said:**
> I have no choice but to reinstall vista, well that is beauty of testing new softwares.

Did you try just restoring the Windows MBR?

---

### Post by TunaCanTommy on 2010-03-24
Look at TestDisk to see if it might be of some help.
It's in the respositories.

---

### Post by cariboo on 2010-03-24
You shouldn't have to reinstall Vista, have a look [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") for recovery solutions.

---

### Post by hoboy on 2010-03-25
bump

---

### Post by andrewthomas on 2010-03-25
> **kansasnoob said:**
> Did you try just restoring the Windows MBR?
+1 
You are not going to get much help if you don't at least answer the questions of those trying to help you.

---

### Post by hoboy on 2010-03-25
> **andrewthomas said:**
> +1 
You are not going to get much help if you don't at least answer the questions of those trying to help you.

Thanks very much.
I have tried everything suggested in the answers, they didn't worked for me.
I have just finished reinstalling vista.

---

### Post by tilixibr on 2010-03-27
I got the same message(but not the same UUID, of course) , the difference is that I upgraded my Ubuntu installed in an external hard drive, and after the upgrade, I can only boot to an OS if i have that external hard drive connected....:(
The weird part is that grub is still installed in my laptop's hard drive!:confused:
I solved the problem by reinstalling grub from synaptic...

---

