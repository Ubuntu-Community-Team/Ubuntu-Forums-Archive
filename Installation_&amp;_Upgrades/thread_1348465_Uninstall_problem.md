---
title: "Uninstall problem"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by ers11121 on 2009-12-07
[FONT=Tahoma][SIZE=2]Good Morning,[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]I need a little help, I installed Ubuntu 9.10 within Windows using Wubi, I know this isn't the preffered method but it's easier when you are trying to decide which Linux distro you are going to switch to. The problem is the install worked for a day, when I turned the computer on yesterday it showed the dual boot option, I selected Ubuntu & got a message similar to this[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]no wubibuilder[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]sh:grub[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]or something similar. I booted into Windows, went to add/remove progams to uninstall Ubuntu but there was no entry. I tried re-installing, that went fine but now I have 2 boot entries for Ubuntu and 1 for Windows Vista. How do I get rid of the extra Ubuntu entry? I tried uninstalling the new installation but that still left the non-working Ubuntu boot choice. Any suggestions?[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]This will get easier when I replace the HDD, there will be separate partitions for Windows, Ubuntu & Linux Mint. I am desperately trying to learn Linux, I have several customers whose computers I service that will be much better off with Linux then Windows, but I need to be able to fix any problems they have before I suggest they switch.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Thanks in advance,[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Ed[/SIZE][/FONT]
[FONT=Tahoma][SIZE=4][/SIZE][/FONT]

---

### Post by lidex on 2009-12-07
Have a look here:
[http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")

---

### Post by ers11121 on 2009-12-07
Thanks, but it's telling me to go to add/remove programs, there is no entry for Ubuntu there, thats my problem.
Ed

---

### Post by lidex on 2009-12-07
Go here:
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")
Scroll down to Uninstallation section and work your way through the steps.

---

### Post by ers11121 on 2009-12-07
Thank you for your time, thats what I am looking for.
Ed

---

### Post by ers11121 on 2009-12-08
I used EasyBCD to remove the Ubuntu entry. Now my next question is this; since I have Mint installed using Mint4Win (Mint 's version of Wubi) can I install Ubuntu using Wubi next to it?
Ed

---

### Post by darkod on 2009-12-08
You should be able to, but I also wanted to ask is thee any particular reason you want wubi so much? You are aware it's not the same as dual boot right?
In fact, the problem that happened with sh: grub happens with wubi only as far as I have noticed, and when you do the updates (which you will still be prompted for in the new install).
Any particular reason you are so determined to use linux inside windows? Because that way you lose lots of linux functionality.
Of course, you are free to do as you like. Just my humble opinion.

---

### Post by ers11121 on 2009-12-08
Here's the thing, I'm still fairly new to linux. I figure if I screw something up bad enough that I can't fix it I can just uninstall it and start from scratch. Soon I will be replacing the HDD in my laptop, with separate partitions for multibooting Windows, Ubuntu, Mint & a separate data partition for all to share. To me everything functions under a Wubi install better then using Virtual Box or VMWare. Does this sound feasable or am I looking at more problems then it's worth?
Ed

---

### Post by darkod on 2009-12-08
> **ers11121 said:**
> Here's the thing, I'm still fairly new to linux. I figure if I screw something up bad enough that I can't fix it I can just uninstall it and start from scratch. Soon I will be replacing the HDD in my laptop, with separate partitions for multibooting Windows, Ubuntu, Mint & a separate data partition for all to share. To me everything functions under a Wubi install better then using Virtual Box or VMWare. Does this sound feasable or am I looking at more problems then it's worth?
Ed

Well it all comes to personal preference I guess. A new wubi would also prompt you for the updates and doing them has big chance of breaking it again. Is that more problems then it's worth?
As for starting from scratch. In a dual boot with separate partitions there is nothing easier than starting from scratch. You just tell Ubuntu to use the already existing partition from the messed up install and to format it. That deletes all of your messed up install. Similarly like you can tell windows to do clean install with format and that deletes everything on C:.
If you are waiting for a new hdd I would agree that wubi might be better temporary option. Just watch out for the updates. On the other hand, maybe you want to try setting up dual boot on your old hdd and then when your new one arrives you know how to get it right the first time. Repartitioning later and moving data around can be real hassle. It's really all up to you. :)

---

### Post by ers11121 on 2009-12-08
Darko,
Thanks for your time. When I do get the new hdd everything will be new from scratch, actually I had 9.10 working for a day, it seemed go bad after installing KDE desktop. I should have known better, the same thing happened when I did that to 9.04. Hopefully I have learned my lesson. If I can ask another question; when I do get the new drive, how large should I make each Linux partition? I'm planning on a 500gb hdd, for Windows, Ubuntu & Mint plus a partition for the data.
Thanks again,
Ed

---

### Post by darkod on 2009-12-08
> **ers11121 said:**
> Darko,
Thanks for your time. When I do get the new hdd everything will be new from scratch, actually I had 9.10 working for a day, it seemed go bad after installing KDE desktop. I should have known better, the same thing happened when I did that to 9.04. Hopefully I have learned my lesson. If I can ask another question; when I do get the new drive, how large should I make each Linux partition? I'm planning on a 500gb hdd, for Windows, Ubuntu & Mint plus a partition for the data.
Thanks again,
Ed

That's another thing that depends how you use your system. Have in mind that Ubuntu (not sure about Mint) can see and use ntfs partitions, but windows can't see linux partitions. So if you're unsure, you better dedicate big chunk of your hdd to common ntfs data partition that both OSs can use. Also keep in mind that linux is not space demanding as windows.
For example, a clean default install of the new win7 ult is around 17GB while a default install of ubuntu 9.10 is around 2.7GB. You need more space dedicated to windows. Plus take into consideration any windows software you are using that takes much space.
But with 500GB you should have plenty of space for everything. If it helps you, here is my setup on 250GB disk:
65GB ntfs primary win7 system
141GB ntfs primary data
15GB ext4 primary 9.10 /
extended
2GB swap logical
10GB ext4 logical /home

Because 9.10 is my first time with Ubuntu, I wasn't sure how much space is needed but I also need space for win7 so I decided to have "only" 10GB /home because any movies, music, even docs can happily stay on the 141GB ntfs data partition and be used by both OSs.
Also it will depend whether you'll decide to make separate /home which is good practice. The point of separate /home partition is that you can make a clean install of Ubuntu on / (like you said, if it gets mesed up), and during the install you just tell it to use /home and NOT to format it, and all your docs, settings, music, etc are there.
Having said that, if you don't make it separate, the space dedicated to / will include /home too (this time as a folder in /) so have in mind that your home folder can grow significantly with docs, music, videos, etc. Dedicate enough space for / to be able to cover that demand.
If /home is separate, I guess 20-25GB for / is more than plenty, remember it doesn't have high space demand as windows.
Read around for ubuntu/linux partitioning practices, it might give you even more ideas.
In fact LVM (Logical Volume Manager) is very nice, but it doesn't create much benefits if you are using only single drive sharing it with windows.

---

### Post by ers11121 on 2009-12-09
Thank you again, that is a big help.
Ed

---

