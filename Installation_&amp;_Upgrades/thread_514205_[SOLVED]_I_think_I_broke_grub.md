---
title: "[SOLVED] I think I broke grub"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Cikrum on 2007-07-31
Hello, 
As the title says, I think I have broken my grub. I have installed Ubuntu on 3 primary partitions along side of Windows (is this bad) one partition is for /home, one for / , and one for swap. At first it had the boot flag on the windows partition and after I installed Ubuntu and restarted it just booted into Windows, So I changed the boot flag from the windows partition to the Linux and restarted. This gave me a boot error. So then I restored the grub using this 


> 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.


This brought up a grub menu but it wouldn't boot into any of them. So instead of doing step 6 to the specific partition I tried doing it to the whole drive. (hd1)
I now have a grub menu come up, but it is not neat like any other grubs I have seen ( not sure if this is important). Anyways if I try to boot into any of the operating systems I get error saying "Error 22: No such partition. Is this just a problem which I have to simple tell grub where to look. If so how do I do this.



Thanks a lot
Cirkum

---

### Post by be4truth on 2007-07-31
Can you post what exactly the command 

```
find /boot/grub/stage1
```

shows?

---

### Post by merlinus on 2007-07-31
You can also try SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Cikrum on 2007-07-31
Well My situation is getting worse. I tried changing the menu.lst because I thought grub just couldn't find the right partition. But I changed Windows from (hd1,0) to (hd1,1). Now that I think of it grub had it right before. anyway I also changed linux from hd1, 2 to hd1, 3. Now I still get grub, and it still doesn't work but my live cd now won't boot. I doubt these two things are related but thats all I did in the times between. Also when I did the 

Find /boot/grub/stage1

I used to get (hd1, 2) but now (because the live cd doesn't work) I use the command line option at the grub, when I do

Find /boot/grub/stage1

I get (hd0, 2)

I am complete out of ideas of what too try...and I don't want to just try randomly anymore because it hasn't worked for me yet.
Anyone got a clue what I did and how to fix it
Thanks so much
Cikrum

---

### Post by Cikrum on 2007-07-31
Just an update. I have my live cd working again, I had an old one sitting around so I tried that and presto. Still can't use grub to boot yet. Still thinks the partitions don't exist.
thanks 
Cikrum

---

### Post by Cikrum on 2007-07-31
I have decided to give up trying to fix it instead I am just going to reinstall ubuntu and hope for the best. Thanks for all the help.
Cikrum

---

### Post by be4truth on 2007-07-31
Hi Cikrum,
don't worry about that. I reinstalled Linux in the beginning as often as I did with windows before! The day came I had an old box around with which I messed around without touching my work computer. That was good. I did everything with GRUB and repartitioning etc without any hesitation of loss. Since then I don't reinstall any more only repair - the Linux way ...

Have fun

---

