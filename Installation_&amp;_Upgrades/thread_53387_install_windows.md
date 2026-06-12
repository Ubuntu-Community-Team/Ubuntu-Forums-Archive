---
title: "install windows"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by art on 2005-07-31
OK
I was so stupid that I basically f@&*ed up my windows installation, when moving it with qtparted in knoppix... Now I have Ubuntu installed on /dev/hda2, linux swap on hda1 and and ntfs on hda3 (without windows, just a formatted partition). Now, is it possible to install windows from this point, or ot will mess it all up (I would hate loosing this installation of ubuntu, after so much effort put in it)? When I put the toshiba recovery dvd, there is an option to save other partitions, and install on C only. but when it proceeds it sais it will delete the first partition. 
Any ideas?

---

### Post by GavinX on 2005-07-31
I have done this once or twice with different distros. As far as I'm aware, Windows OSes are quite greedy and will take over the entire disk. Unless you really, really, really NEED Windows, I would recommend that you use QTparted again and just modify the entire disk for Linux usage. However, if you NEED Windows, you should be prepared to reinstall Ubuntu also.

WIndows is the MOST GREEDY OS that I know!

---

### Post by kvidell on 2005-07-31
Uhh.. What I would always do is install windows first then install linux next to it so that Grub takes over the MBR.

I've never installed windows first, then linux... I never wanted the hassle of the MBR being overwritten by MS.

I'm sure there's a simple solution... Reinstalling Ubuntu shouldn't have to be it, though.
- Kev

---

### Post by Simplimus on 2005-07-31
you probably should go get a "clean" version of windows. there are so many out there. those recovery cds work, however, they will most definitely mess up everything on your computer. those I know just copied a drive image.

get yourself a windows all-in-one dvd from the net, which holds all windows version starting with 98.

and yes, windows is greedy.
the best would probalby be, in case you dont have a different windows available, to backup your drive somewhere, install that OEM stuff, see what it does and recover your partition afterwards.

---

### Post by art on 2005-07-31
Thank you very much guys
I also always install win and then linux, the same was this installation. But since this installation of ubuntu is so much customized, I would really die while deleting it. So I guess installing from the scratch is not an option. As for installing windows I do have a Win XP installation cd, I am just not sure if it will want to write stuff on hda1 and/or hda2 or not, do you guys know, have experience? Or if I specify to write it on hda3 only, it won't touch the rest. 
Thanks a lot!

---

### Post by Hairy_Palms on 2005-07-31
i had the same problem, i was so scared a scavanged an old 30gb hd for windoze and installed it whilst my main disc was unplugged but ive known people to simply installl windoze to the remaining free space then repair grub but that was with suse not ubuntu

---

### Post by art on 2005-07-31
I would definetly do that, the problem is this is a lappy, only one harddrive, so can't do that...
Is it possible to somehow hide the other partitions so that windows installer doesn't even see them?

---

### Post by super on 2005-07-31
actually if you install windows and it steals your boot loader you just have to *re-install grub, not all of ubuntu* it is an option on the install CD if you select rescue mode when you boot the CD.

---

### Post by art on 2005-07-31
So you are saying there is no chance of windows deleting the ubuntu partition? If it is do I will try installing the windows.

---

### Post by super on 2005-07-31
hmm  :-k 
on a second thought i think i usually had hda1 as my windows partition and i windows usually tries to take over the the first partition so your problem is different from my situation.

sorry.  :( 

have you taken a look ath this thread:
[http://ubuntuforums.org/archive/index.php/t-22537.html](http://ubuntuforums.org/archive/index.php/t-22537.html)

---

### Post by Ptero-4 on 2005-07-31
[QUOTE=super]actually if you install windows and it steals your boot loader you just have to *re-install grub, not all of ubuntu* it is an option on the install CD if you select rescue mode when you boot the CD.[/QUOTE]
 Don't install XP after Linux. It's got a hidden program that as soon as you boot from the XP CD it will run. The program basically looks at your hd and if it sees one or more partitions in any format different from fat 16/32 or ntfs it will: if there are partitions in the fat or ntfs formats it will delete the partitions with formats other than fat or ntfs and then resize the fat/ntfs partitions and move data (if there is any) to one partition and delete the rest of then and finally resize that partition to cover all the hd. OTOH if there aren't fat/ntfs partitions if will wipe the entire hd and create one big partition to cover all the hd.

---

### Post by art on 2005-07-31
Oh my...
I am in big trouble. That's what I thought. So I guess I better wait, till I have more time to mess with this. 
I now understand how important is that dialog which asks you "Are you sure you want to do this?"...
Thanks everyone!

---

### Post by GavinX on 2005-08-01
[QUOTE=Ptero-4]Don't install XP after Linux. It's got a hidden program that as soon as you boot from the XP CD it will run. The program basically looks at your hd and if it sees one or more partitions in any format different from fat 16/32 or ntfs it will: if there are partitions in the fat or ntfs formats it will delete the partitions with formats other than fat or ntfs and then resize the fat/ntfs partitions and move data (if there is any) to one partition and delete the rest of then and finally resize that partition to cover all the hd. OTOH if there aren't fat/ntfs partitions if will wipe the entire hd and create one big partition to cover all the hd.[/QUOTE]
This was exactly my point in the earlier post. I've found in my experience that whenever Windows (and this is not just restricted to XP) is installed after Linux, it takes over the entire disk and deletes the Linux partitions. If you had two disks, that would be different. With two drives, you just specify the one you want to install Windows on and all you need to do afterwards is to reinstall the botloader. However, with a single drive, Windows is known to eat the entire disk. That is why I indicated that Windows is the most greedy OS that I know.

[Don't look at the number of posts that I have in these forums, I'm pretty experienced with Linux. I've been using it since 1999 and I've passed through many distros. So by now, I think I have an idea of what's going on.]

---

### Post by art on 2005-08-01
Hi GavinX
I am sorry if I seemed as ignoring your opinion or anything like that (It was not my intention at all)... I appreciate everyones opinion, and thankful to everyone who was helping me. 
As you know when the situation is like mine, when you have so much to lose, you want to hear as much opinions and stories as possible and draw your conclusion... 
Again thank you very much!

---

### Post by GavinX on 2005-08-01
[QUOTE=art]Hi GavinX
I am sorry if I seemed as ignoring your opinion or anything like that (It was not my intention at all)... I appreciate everyones opinion, and thankful to everyone who was helping me. 
As you know when the situation is like mine, when you have so much to lose, you want to hear as much opinions and stories as possible and draw your conclusion... 
Again thank you very much![/QUOTE]
Actually, art, my last post was not directed at you. I understand your dilemma and really understand that you are seeking guidance and that is in order. I was really responding to those who were suggesting that a reinstall is not necessary. Sorry for the misunderstanding, art.

---

