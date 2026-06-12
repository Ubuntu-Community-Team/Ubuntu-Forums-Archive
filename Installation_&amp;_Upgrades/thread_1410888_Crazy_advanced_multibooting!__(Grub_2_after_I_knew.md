---
title: "Crazy advanced multibooting!  (Grub 2 after I knew 1 GRRR!)"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by markjs on 2010-02-19
So this may be very complicated for some so please read very carefully, because my actual question is quite simple and I am sure very easy to answer!

OK, so I have on one 160GB drive iDeneb 1.5, OSX86, then I put Windows 7 on a 7590GB drive and I want these two drives to be able to boot all alone if you shut everything else off or take the drives out, which they now do, it's just that you have to change the BIOS, to choose.

So then I split a 400GB into three parts, and while I did it it was the only drive hooked up; about 80GB on which I put XP Media Center, 160GB for Vista which is now on the second partition, and currently that drive will boot as a standalone with the two choices of XP and Vista, and I have about 120+ left for Ubuntu.  So Ubuntu is the last OS I want and normally I would use a separate hard drive for it since 7 and Ubuntu are the most important to me and iDeneb is such a hassle to install that it gets it's own drive....

So this time I have no drive that can be dedicated for Ubuntu.  If I out 8.04 on it there would be no trouble because I had just mastered the Grub that came with it but this automated Grub 2 is REALLY annoying to me!  Crazy booting arrangements like this are tough enough to get right manually so when Grub starts automating things I get real nervous!  It worked great before when I had a dedicated drive because it picked up all of the other operating systems, I just had to make sure that Grub got written at the beginning of the Ubuntu drive and not the one it wanted to invade (don't remember which, but it was annoying having to repair whatever it borked!)

So what I want, is for Grub to be on the disk with XP and Vista on it and then that drive would work as a standalone with those three operating systems, and the other two drives can be initiated to boot from that three-way drive, but if it was removed will still work as standalones.  The trouble I have is I am not sure exactly where Grub should go, I am thinking it needs to be on the XP partition, which is the first on that drive, but I could be wrong.  I wish it would work if I had it on the Ubuntu partition which is the third on that drive and then if Ubuntu locked me out, since it is the one I am in most trouble with when something goes wrong, but I suspect that can't be done.  I also am 99% sure it can't even access the OSX86 drive at all, but I do know it can initiate it to boot.

So if anyone can clarify this for me **I'd surely appreciate it!**  I like all the OS's so I can be fluent in as much as I can, but it sure is nice when I can fit it on a single machine since I live in a small place and am utilitarian to the core.

Thanks for reading my novel, I'll sign a copy and mail it to you for $5, and if you like that deal there just may be some really cheap beachfront property in Wyoming I have a line on....

---

### Post by darkod on 2010-02-19
You're right, it's fairly simple. Few alternatives:

1. Boot the 9.10 cd into live desktop, run sudo fdisk -l and note what is each drive called. Then just start the ubuntu installer and in the last screen, before clicking Install, click on Advanced and check where the bootloader (grub2) will go. Select the drive you want, for example /dev/sdc, and that's it.

Note: it's better to select a drive, not an actual partition like /dev/sdc5 because then you would have to chainload to grub2 which is not impossible but why do it.

2. Even if the above sounds too much hassle, the installer in step 4 is showing you the drive name so you just have to make sure in the last step to click on Advanced and select the same drive for grub2, unless it already is the selected destination.

It shouldn't create any issues for you. Hope it works out fine.

---

