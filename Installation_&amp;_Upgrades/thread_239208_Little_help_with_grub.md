---
title: "Little help with grub"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by nightmare03 on 2006-08-18
Hey, it's late, im tired so ill post this quick.

I have two hard drives, 40gb master and a 20gb slave, after trying out ubuntu on the 20gb i wanted to put it onto the 40gb master.

I still needed to keep XP so here is how i did my install:

Formatted both hard drives.
Install XP on the 20gb slave hard drive, it also put its MBR on the master hard drive.
Installed ubuntu on the 40gb, removing XP's bootloader in the process.

Now, when my computer boots up i get grub but no option for booting XP, is there anyway i can add this with my setup or did i mess up? ](*,) 

Thanks!

---

### Post by scxtt on 2006-08-18
look in your /boot/grub/menu.lst -- it tells you how to add an entry for windows ...

specifically:
```
[font=courier]#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#[/font]
```you'll just have to change (hd0,0) to (hd1,0) ... i won't insult you by reminding you to remove the #s ;)

---

### Post by zxee on 2006-08-18
You can boot to ubuntu right? Open a terminal and type > sudo gedit /boot/grub/menu.lst

Create or copy paste this title WinXP
                          rootnoverify (hd1,?)
                          chainloader +1

I don't know what the partition # is for your windows install so where I have "?" you'll need to supply the actual #  e.g if windows is the 1st and only partition then maybe it's (hd1,0) which is normally seen as /dev/hdb1
but grub counts from(including) 0. So hdb1=(hd1,0) get it?
Hope that helps.

---

### Post by nightmare03 on 2006-08-19
Hey, thanks for the posts but neither of them seem to do anything when i select them :(

I googled around and found this :
```

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

```

Now i think that works but when i select it i get "NTLDR IS MISSING" from XP.

What should i do? :o

---

### Post by a-man on 2006-09-01
I had the same problem when I installed Ubuntu on 1 of the 2 drives (both IDE) in my PC. The primary drive was XP which I replaced with Ubuntu. The second drive was another XP I wanted to keep. After the install, I booted in Ubuntu, messed around, then did what I thought I needed to do in grub to get the XP drive to boot. I could never get the XP drive to boot for a long time and I almost gave up. I always got "NTLDR is missing" and I noticed a lot of people had the same problem but I never saw a fix. I was able to mount the XP drive in Ubuntu and grab files from it so I knew it was still there and working fine.

Then recently I ran across something and I got it so I could boot into XP. There is a new error with the boot.ini being corrupt but at least XP would boot up and I could worry about the boot.ini later on. Here's what I tried:

Boot with XP CD.

Press R to load the Recovery Console.

(for the next step D: would be the CD drive with the XP CD)

Type:
copy D:\i386\ntldr C:\
copy D:\i386\ntdetect.com C:\


(two other files needed - just in case)

Type:
attrib -h -r -s C:\boot.ini del C:\boot.ini

Type:
bootcfg /rebuild

this should get rid of any damaged boot.ini, search the disk for systems and make a new one. This might even result in a damaged windows reappearing; but gives another chance of getting at the repair.

Anyway, this worked great for me except for the boot.ini error while booting but now that I can boot XP I will get that fixed next when I get the chance. I've only done this "fix" once so I don't know if it would work every time on any PC. 

Good luck getting it fixed and I hope this might help.

---

