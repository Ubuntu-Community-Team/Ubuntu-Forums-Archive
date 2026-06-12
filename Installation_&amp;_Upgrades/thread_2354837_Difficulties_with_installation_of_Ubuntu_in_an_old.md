---
title: "Difficulties with installation of Ubuntu in an old machine"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by denis.positron on 2017-03-07
Information about the machine: Laptop Acer Aspire 4720Z, HD 160 GB, RAM 2GB (old machine).
Aim: Install Ubuntu 16.04 preserving the pre-installed Windows (It is Windows XP, I think)

Hi,

I am trying to install Ubuntu 16.04 in a laptop with Windows. So I created a bootable USB stick. When I try to install Ubuntu the installation produces the following message

gfxboot.c32: not a com32r image
boot:

I searched on the internet and it is ease to work around using the procedure 

Press tab
Type 'live'
Press enter

After the installation I restarted the system and I received the following message in my screen:

error: unknown filesystem
grub rescue>

Again I searched on the internet and I found some instructions that hypothetically would fix this problem:

The command 

grub rescue> ls

returns

(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)

The command 

ls (hd0,msdos4)/

returns some folders, between them I have boot/, home/, opt/, root/, usr/.

So msdos4 is the partition that I must regard. The next steps occur with no problem:

set prefix=(hd0,4)/boot/grub

set root=(hd0,4)

and the command

ls /

returns the same folders boot/, home/, opt/, root/, usr/, etc. above. But when I try the command

insmod normal

I am informed with the message

error: file not found.

After this command I was supposed to use the command normal, Ubuntu would be loaded and I would install grub2. I searched on the internet about this but I am with difficulties in proceed.

Then I decided to use the bootable USB stick in order to repair the grub or even reinstall Ubuntu. But when I do this I get the message

end kernel panic - not syncing vfs unable to mount root fs on unknown-block(2,0)

I can not boot from USB stick, so I can not repair the grub neither reinstall Ubuntu.
I am not able to move forward in this matter.
Please, any help will be appreciated.

Best regards,

Denis

---

### Post by mörgæs on 2017-03-07
First of all I would suggest L/Xubuntu, not Ubuntu for a computer of this age.
Does it work better with one of these?

---

### Post by SeijiSensei on 2017-03-07
Are you sure you're using the right architecture, probably 32-bit on a machine of this vintage?

Try this link for 32-bit Lubuntu 16.04.2: [http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/lubuntu-16.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/lubuntu-16.04-desktop-i386.iso)

---

### Post by mörgæs on 2017-03-07
I don't think so. It is were a 64 bit ISO failing because of 32 bit hardware the install would not have proceeded that long and original poster would have received an explicit error message.

---

### Post by SeijiSensei on 2017-03-07
> **mörgæs said:**
> I don't think so. It is were a 64 bit ISO failing because of 32 bit hardware the install would not have proceeded that long and original poster would have received an explicit error message.

Now that I recall, the installer should have complained pretty much at the outset.  Guess that's not the issue.

---

### Post by denis.positron on 2017-03-08
Hi guys,

Thank you for the suggestions and comments you provided so kindly. 

The system is now installed and operating. However I would appreciate your opinion about a question I have. 
But before I must explain my actions that resulted in failures and the actions that allowed the adequate installation of the OS. 

At first I tried to create the following partitions in my disk (the Windows, Vista, was already in a separated partition)

/boot - primary - 1GB
swap  - logical - 4GB (twice the RAM)
/     - primary - 50GB
/home - logical - the remaining

and I marked the installation of boot in the corresponding /boot partition (in my case it was hda2). 
I tried the 32 bits ISO of both Lubuntu and Xubuntu. 
All the times I did this partitioning I had the 'error: unknown filesystem' and the 'grub rescue>' I described before. 
Then I tried a different partition scheme: 1- a partition for swap area and 2- a partition for / (the Windows partition 
was untouched) and I marked the installation of boot in hda. This is the procedure that worked. So the question is, 
what was my mistake in the former installations? I will be grateful if you can help me understand the source of my error 
that lead me to loss a significant amount of time. As a last question, should I try a 64 bit OS in my Intel T2330?

Regards,

Denis

---

### Post by mörgæs on 2017-03-08
I abandoned Windows ten years ago so I can't advise you regarding a dual boot. 
If you have 2 GB of memory there is not much gained by switching to 64 bit.

---

### Post by denis.positron on 2017-03-09
Ok, thank you very much!

---

