---
title: "Adding windows xp to menu.lst"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by richbarna on 2006-07-09
Hi everyone.

I had to put Xp on the pc for my wife, and I can't get it to boot.
Here is my setup :-
[ATTACH]12459[/ATTACH]

hdc6 has the windows xp on a Fat32 partition. I edited the menu.lst with the usual : 

title        Microsoft Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Then I realised that it's on partition 6, so I changed it to :

title        Microsoft Windows
root        (hd0,5)
savedefault
makeactive
chainloader    +1

Here is another thing, my main Dapper install is hdc3, where the new Dapper and Xp are, used to be a 40Gb partition that I split in two.
My idea was that if I installed xp first and THEN the 2nd Dapper, windows would be bootable from grub.

I do remember that i had to change the format of the boot partition so that windows could create a Fat16 for the MBR. All went well and I got the usual windows boot menu.

On to the second Dapper, when I was installing, I couldn't put the boot partition where the windows MBR was because it's Fat16 so i formatted it to ext3 and installed.

All ok, Now I can boot to my Main Dapper and the New Dapper, but am having no luck at all getting Xp recognised.

Can anyone help?

---

### Post by confused57 on 2006-07-09
Anybody can correct me if I'm wrong, but I believe Windows has to be on a partition table prior to any other OS(sounds like you already knew).  Wonder if the GAG bootloader on Herman's site will allow this?

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by richbarna on 2006-07-09
> **confused57 said:**
> Anybody can correct me if I'm wrong, but I believe Windows has to be on a partition table prior to any other OS(sounds like you already knew).  Wonder if the GAG bootloader on Herman's site will allow this?

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Yeah, I know, I put it inside an extended partition (logical) after Ubuntu.
Now I know the sequence for drives on the menu.lst for standard partitions, and i have triple booted Linux and dual booted with windows.

Because I am now triple booting with windows I get a problem.

I also saw this while reading the forums :-
>  the first partition on the primary drive is (0,0)
second on primary (0,1)
third on primary (0,2) etc

first on secondary (1,0) etc.

any logical/extended partition is always the [COLOR=Red](n,4)[/COLOR] so the first
partition of a logical partition is [COLOR=Red](n,5)[/COLOR] 
I don't understand this, does anybody know what I have to put in the menu.lst if XP is on a logical partition inside of an extended partition?

---

### Post by richbarna on 2006-07-09
I have just read that windows can only be booted from a Primary partition. There was a solution to this using the windows MBR and bootloader, but I want Grub.

So I am going to rearrange the hardrive so that windows is on a primary, and hope that i don't mess it up.

Thanks for the help Confused57 :)

---

