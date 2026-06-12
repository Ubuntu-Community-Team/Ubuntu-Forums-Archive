---
title: "HDD problems with installation of Ubuntu 6.06"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Neky on 2006-10-25
After many problems with Ubuntu 5.10 ( integrated S3 graphics ) i got my hands on 6.06 version and all seemed to be fine with drivers. Installations was all good until partitioning part ( step 6/6 i think ). I allready had Linux and Linux swap partitions which i made before with cfdisk from Slackware and it worked pretty fine with Slackware. On step 6/6 partitioning manager of Ubuntu installer HAD NOT recognized ANY of my Linux/NTFS partitions and only option was to format the whole HDD. Of course i quited it and got a headache... What to do...? I need Ubuntu 6.06 like crazy because its the only distro ( that I`we tried ) that supports my S3 graphics and my wireless card chipset.

Thanks in advance, Neky, Serbia.

---

### Post by ebutton on 2006-10-25
Hello!  Not much help from me.  I'm fairly new to Ubuntu.  However, please provide a little more info.  Are you intending to dual boot?  I think the ext3 format would be better for your Ubuntu partitions.

Sorry if this is of no use.  I just thought you'd like someone to try and help.

Regards,
EdB

---

### Post by Kateikyoushi on 2006-10-25
If you have valuable data do a backup first.

You can follow this installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")
If the partitions are not recognised and there is nothing important on it you could delete them and create new ones instead of them. Except for the Ntfs one which your windows needs.

If you need more help post the output of this command.

```
sudo fdisk -l
```

---

### Post by Neky on 2006-10-25
@ebutton

yes, i am going for the dual boot because i need WinXP for internet access, untill i set up my wireless card in Ubuntu...then...bye bye XP. I don`t really know what else to say...HDD is Maxtor, 4 partitions ( 2 NTFS, 1 ext3, 1 linux swap ). Hints please :p 

@Kateikyoushi
I do have some valuable data on both NTFS partitions but i can back them up. Only problem is that i need my first NTFS partition because of WinXP and internet access ( as mentioned above ) so that i can search for tutorials about setting up wireless internet access on Ubuntu and talk with you guys about problems with Ubuntu. I cheched link that you gave me and everything looks the same as in my case except of [this]("http://img230.imageshack.us/img230/2340/w2u260tf.png") ... I only get "Erase entire disk..." option.

---

### Post by Kateikyoushi on 2006-10-25
I just meant to delete the linux partitions, but if you can't even partition it. Try to use gparted from the live cd before installation, just type the command to terminal.

---

### Post by Neky on 2006-10-25
...and to create new linux partitions with gparted? Is that what you think i should do? No problem man...be back in about 30 minutes, thanks to both of you.

---

### Post by Kateikyoushi on 2006-10-25
Yes, I hope gparted can sort it out, if not we have to deep digger what's wrong.

---

### Post by Neky on 2006-10-26
All done and went fine, just fine, thanks Kateikyoushi for help. Gparted got it all seted up and running. Well...i had some problems with deleting swap partition, but nothing big...it`s still a swap, i just wanted to make it smaller.

Mods, lock it yeaaaaaaah!

---

