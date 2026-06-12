---
title: "GRUB's being a party-pooper!"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by minigilani on 2010-09-22
Hey, i installed Kubuntu 10.04 Lucid Lynx on a friends' computer, and the install continued like it normally would, i selected options and rebooted, and everything, but on restart, grub gives an error and refused to boot!
.
It gives an error on stage2 and gives me a console, the only command i can get to work on it is ls, and that lists my partitions, i think. =s
.
.
Key points:
- 80GB IDE HDD.
- 1st Partition has WinXP.
- Shrank last partition to accommodate Kubuntu.
- Live CD boots perfectly, ran installation twice, ran perfectly both times.
- Installation CD is fine, i installed the OS on my own computer, using it as i type.

If it can't be helped, i guess i'll just plug in the XP install CD and give the fixmbr command on the recovery console.. but i really want my idiot of a friend to start using Linux.

---

### Post by minigilani on 2010-09-24
anyone? Really, grub's being a real <snip> here.

---

### Post by drs305 on 2010-09-24
If you boot a LiveCD and run *meierfra's* boot info script and post the results we may be able to see what's wrong.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Is it the error with the device and UUID not being found? It would help to have the exact error message.

---

### Post by minigilani on 2010-09-25
I believe Kubuntu 10.04 LTS ships with Grub2.

---

### Post by Rubi1200 on 2010-09-25
> **minigilani said:**
> I believe Kubuntu 10.04 LTS ships with Grub2.
Yes it does.

Please post the results of the bootscript linked in the post by drs305 above; it will hopefully tell us if there is an issue and we can then suggest solutions.

Thanks.

---

### Post by minigilani on 2010-09-25
I'll post the result as soon as i go over today, but as far as i can remember, i think it's a problem with Grub stage2, i don't think it can find it.. but i'll run the script and post the results ASAP.

---

### Post by garvinrick4 on 2010-09-25
> **minigilani said:**
> I'll post the result as soon as i go over today, but as far as i can remember, i think it's a problem with Grub stage2, i don't think it can find it.. but i'll run the script and post the results ASAP. That is what they are going to tell you
what partition your grub2 is located so they can put it in mbr and make you have a bootable system. If you installed correctly and grub is just not put is sda like 90 % of these situations you should be up and running 5 minutes after you post the results of Bootscript.
Make sure you download to DESKTOP. Then run this code:
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

