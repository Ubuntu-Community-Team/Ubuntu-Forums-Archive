---
title: "Dual booting win7 and ubuntu"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Beastlicker on 2009-12-10
I have two hard drives. One 120gb and one 40gb. I already have windows 7 64 bit on the 120gb hard drive. I plan on having 32 bit ubuntu 9.10 (The reason for 32 bit is because I have intel). I have tried this before, but windows 7 was not showing up on the grub boot list. Is there any way I can install Ubuntu along with Windows so that Windows will show up in the boot list (Windows 7 primary boot preferably)?

---

### Post by Bucky Ball on 2009-12-10
Because you have intel??? AMD64 version of Ubuntu is for ALL processors, AMD and intel. You should be using 64bit Ubuntu.

---

### Post by Beastlicker on 2009-12-10
Ah. Okay. Well, I wasn't sure whether AMD worked on Intel or not, so I just stayed safe and went with 32 bit. While I download it, is there anyway I can install it while keeping windows 7 in grub bootlist?

---

### Post by oldfred on 2009-12-10
If it is a clean install it is grub2 and that is very good at finding other operating systems. It should have found it, but you can rerun this to see if it finds it now:

sudo update-grub

---

### Post by Bucky Ball on 2009-12-10
Go for manual partitioning when you get to that section and just avoid the Windows partition. Should be picked up automatically and written into the grub.

... and yes, like oldfred said ...

---

### Post by Beastlicker on 2009-12-10
Alright. I just dl'd and burned 64 bit. I'll just put it in and install it to the 40 gig. So let's hope grub finds it. haha.

---

### Post by Beastlicker on 2009-12-10
I am using the option "Erase and use entire disk" and chose my 40gb drive. If I select this, with both windows and ubuntu show up in boot screen?

---

### Post by Bucky Ball on 2009-12-10
If you are using a disk with nothing on it you want to keep, go ahead. You might not like the partition sizes you get which is why I always manually partition. You can size as you want, add your own partitions, and the ones you need are defaults for selection:

/
/home
/swap

... and whatever else you fancy.

/music
/vid

Whatever.

Should pick up Windows. If it doesn't it is an easy fix. Run oldfred's command from a couple of posts ago. (Applications->Accessories->Terminal and paste in the command, hit return). If that doesn't work, let us know.

---

### Post by Beastlicker on 2009-12-10
When it asks where to add bootloader for the advanced options, should I put it at the default (hd0) or windows loader/windows hdd/ubuntu hdd?

---

### Post by oldfred on 2009-12-10
You need to install grub to the boot disk unless you plan on changing the boot order in BIOS. If windows is your current boot then you have to overwrite the windows in the MBR. That can be fixed if you ever want to go back.:(

---

### Post by Beastlicker on 2009-12-10
Alright thanks. So using the option erase and use whole hdd should work (I am not installing over windows. I am using spare hdd)? And just install the boot loader in the default (hd0) and grub should detect windows and ubuntu?

---

### Post by Beastlicker on 2009-12-10
It works perfectly. Thanks for all of your guys' help. I'll ask again if I have any more problems.

---

### Post by Bucky Ball on 2009-12-10
Good news. Welcome and have fun.

---

