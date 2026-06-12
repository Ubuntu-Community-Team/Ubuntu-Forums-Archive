---
title: "HDD install - USB Flash Drive Boot Disk"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by Obitus on 2005-05-18
Hey people,

first time UBUNTU and it really rocks!

I thought I would have a simple question but nobody seems to have put an answer to the www anywhere or I was just to searching the wrong words... So here we go:

System:
IBM Thinkpad T42p
60 GB HDD
128 MB Fire GL
Atheros Wifi
all necessary devices are detected and running (as far as I can see).

I partitioned my HDD as following:
Win XP Pro partition
backup partition
datashare partition
Ubuntu and finally
swap partition

Because I had some trouble under Knoppix with MBR, GRUB, partitions and stuff I want run Win XP by default from the internal HDD. I want to install Ubuntu on that HDD but only boot into Ubuntu when my USB Flash Drive (Cosair Flash Voyager) is plugged in. The Flash Drive is so to say some kind of boot disk. Windows should not see anything from Linux, so in principal I think I wouldn't need to boot with bootloader.

It is no problem to fresh install both systems (XP and Ubuntu) I probably have to do this anyway (messed up!). I found plenty of HowTos for dual boot install (both way round GRUB and Windows Bootloader) and small installations on Flash Drives but nothing comparable to my wishes or I just couldn't see it. I found HowTos for Boot CDs but no Boot Flash Drive. :???: 

Any links, comments and help appreciated!

---

### Post by SFN on 2005-05-18
Just completely off the top of my head (I'm neither a USB key expert nor a grub expert) but I would think that the way to do this would be to have grub on your USB key. The only option in grub would be Ubuntu, say on /dev/sda1. You could even change the timeout to 0.

So grub should look something like this

# Boot automatically
timeout 0

# By default, boot the first entry.
default 0

# Fallback to the first entry.
fallback 0

# For booting Linux
title  Linux
root (hd0,0)
kernel /boot/vmlinuz-2.2.17 root=/dev/sda2



I'm not positive about timeout being able to use "0" and the kernel entry is just an example but I think you get the idea.

Of course, I could be WAY off here.

---

### Post by Obitus on 2005-05-18
Hey SFN

hm, well I know what you mean but can't get it work ](*,)  I thought it would be that easy but it seems not to be so!?

Do I need a partition an that (256 MB) USB Flash Drive? Which format ext2, ext3, reiserfs...? What size? Mount as /boot or anything? Set a boot flag?

If anybody needs further information please, please ask! I'm sure some people out there are also keen for an answer (or HowTo!?)!!

---

### Post by SFN on 2005-05-18
Well, this is a _huge_ YMMV situation. I've never done this before so I'm just guessing.

You'd definitely need to have a partition on there. At least /boot. The alleged requirements for that are 5-10MB. I've always used reiserfs (in Ubuntu and others) and it requires more space (50MB, I think) so I've always given it 65MB. If you do ext3, then I'd imagine that you can probably get away with 10MB. Someone else may have more info on that.

Many people have reported problems working with reiserfs. I've seen it everywhere. However, I've never had problem one.

Now, will /boot be enough? I dunno. That's what I would try and if it didn't work, I'd add a / partition of 256MB. Of course, I don't know what size your flash drive is but if it can handle the 256MB plus 65MB, you might go for those sizes in ext3, just to be safe. If you do that though, you'll need to point grub at your flash drive instead of the HDD. If you did that and it worked, you'd need to leave the flash drive in the slot the entire time that you are using Ubuntu.

As I said before, I'm just guessing. If anybody out there knows that I'm way off (or even a little bit off) feel free to chime in. 

I have to ask though, why don't you just set it up the normal way and have grub multiboot? You say that you had problems with "Knoppix with MBR, GRUB, partitions and stuff" but if you set it up right, it's a breeze. I'm dual-booting Ubuntu and XP on my notebook (SONY Vaio A140P) (I must have XP for business - just kills me) and I have no problems with it.

---

### Post by SFN on 2005-05-18
I just re-read that and realized that I could have been a lot more helpful with the comment about multibooting with grub.

If you do a fresh install of XP followed by a fresh install of Ubuntu, rather than letting Ubuntu partition the drive for you, manually partition the drive. Set any drives already set up for Windows to "do not use". Format the remaining drive space in two parts. One should be double the size of your memory (i.e. you have 256MB of RAM, make the partition 512MB) and format it as a swap partition. The other partition should be the remaining size of the drive. Format it as ext3 and label it /. 

If you do that, when you are done you will find that grub is set up to boot to either XP or Ubuntu.

There's a whole lot more you could do like making a separate /home partition or using reiserfs but this will get you running quickly and cleanly.

I apologize if you already know this. Just thought it might help.

---

