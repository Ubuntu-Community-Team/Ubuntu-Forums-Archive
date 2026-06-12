---
title: "GRUB looks like not finding Ubuntu"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Filip.Wroclaw on 2010-01-27
Hi.
I bought new Sony VAIO NS31S. It had preinstalled Windows Vista. I wanted to go back to Ubuntu, cause I used it (but never been really understanding how its working) on my previous notebook.

I downloaded Wubi with Ubuntu 9.10, installed, rebooted - everything was fine. I even had connection to the web (what I was very suprised to see, cause I had troubles with that Net provider on my old hardware with U 8.something).

I removed several programs, mainly games or accessories for PalmOS, etc. On the second hand I installed Kadu, Google Chrome (here I couldnt use Software Center, it was installed form downloaded package), Netbeans, and then some errors occured, so I allowed system to get updates. After installing them I switched off computer, and today (the whole story was yesterday and day before) I wanted to boot Ubuntu, but GRUB gives me command line & some info(in a while I swith VAIO off, go to the old machine, and try to rewrite text from GRUB here). I TABbed, and there was a list of commands, so I tried some of them, and It looks like my system is gone. On Windows side I think its all ok - here's my folder hierarchy:
```
/ubuntu
   //disks
      root.disk
      swap.disk
      //boot
         ///grub
   //install
      here is some strange-named file, smth like .fuse_hidden000...
   //winboot
      wubildr
      wubildr.cfg
      wubildr.mbr
   Ubuntu (its an Icon)
   ubuntu-uninstall (and thats a wizard)
```
if there are /'s before files name it means its a directory. else its a normal file. Whitespaces shows what belongs where.

Sorry, if there already has been topic like this. Ive searched this forum for 'wubi' 'vaio' and 'grub' and there was nothing I thought might be simillar.

O! And there's one more thing. Is it possible to switch off double system choosing? I mean Windows gives me choice to boot Windows or Ubuntu, or use some windows recovery tools. If I try to boot Ubuntu, there comes GRUB, which gives second choice of choosing Windows. But this is smaller problem, then nnot booting linux ;)

Thanks to everyone that ever will answer this post ;)

PS. Im form Poland, and I havent spoken english with anyone for 3 or 4 years now, so I can make some mistakes, for whish i apologize ;)


==EDIT==

Ok, so I rebooted once again. Here's what GRUB says:
```
GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command comletions. Anywhere else TAB lists possible device/file completions. ] 
```
So I pressed TAB, found some commands (there's quite lot of them, so as for now I wont write them here).
```
sh:grub> ls
(loop0) (hd0) (hd0,2) (hd0,1)
```
```
sh:grub> linux
error: no kernel specified
```
```
sh:grub> boot
error: no loaded kernel
```

---

### Post by darkod on 2010-01-27
This was common problem with wubi few months ago but it should have been gone by now. I'm not expert in wubi but you could start it with these commands:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=[COLOR=Red]/dev/sda1[/COLOR] loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You should use /dev/sda1 only if your ubuntu folder is on the first partition on the first disk (be careful, even if it is on C: you could have another small recovery partition before C: and C: can be /dev/sda2 in ubuntu terms).
So if you need to use something else instead of /dev/sda1, change it. You can also look at your partitions by booting windows and in disk management (windows button + R, type diskmgmt.msc, hit Enter).

After you have booted into wubi, in terminal do:

sudo update-grub2

As far as I know (because I don't use wubi), that should fix it.

And long term, why don't you suggest runing proper full ubuntu, on it's own partition and filesystem, and not wubi which is only virtual ubuntu. That's why you are seeing windows bootloader first, and then "grub2". There is no way to avoid that. In fact that is not grub2, you don't have grub2, that's only virtual grub2.

---

### Post by meierfra. on 2010-01-27
> As far as I know (because I don't use wubi), that should fix it

This only works is some case and only is a temporary fix, namely the problem might reoccur after the next kernel update. See this link for more details and how to fix it permanently:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Brett.Townsend on 2010-01-27
I would recommend doing a clean full install of Ubuntu and dual booting instead of wubi.

---

### Post by meierfra. on 2010-01-27
> That's why you are seeing windows bootloader first, and then "grub2". There is no way to avoid that. 

 One can install Grub 2 in the MBR and boot Wubi with Grub 2, without  any involvement from Windows boot loader.

> In fact that is not grub2, you don't have grub2, that's only virtual grub2. 
 There is no virtual grub 2 involved in booting Wubi. Wubi uses "wubildr" which is a version of Grub2  tailored towards Wubi. This file resides directly on the  ntfs partition and not inside any of the virtual file system.

---

### Post by darkod on 2010-01-27
> **meierfra. said:**
> One can install Grub 2 in the MBR and boot Wubi with Grub 2, without  any involvement from Windows boot loader.


 There is no virtual grub 2 involved in booting Wubi. Wubi uses "wubildr" which is a version of Grub2  tailored towards Wubi. This file resides directly on the  ntfs partition and not inside any of the virtual file system.

Thanks. You learn something new every day. As I said, I'm far from expert in wubi. I prefer the "real" ubuntu. :)

---

