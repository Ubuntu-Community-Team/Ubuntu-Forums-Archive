---
title: "Dual boot"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by yoyspaSm on 2007-10-02
Hello, I would like to create a XP, Ubuntu (feisty)  dual boot, I've got 2 hd's(SATA2,320GB). On the first I have a partition C: on which i have installed windows xp sp2, on partition D are just my files such as music. My new drive I have made partition F. I would like to install Ubuntu on F, my question is: Is this possible without plugging out HD's and just by installing ubuntu of partition F. And can i make the partition for the swap file during the installation? When I have installed on partition F do i have to put my ubuntu HD as primary boot device in BIOS or can i make it boot from my xp drive? And when it boots from my xp drive will i have a menu in which i can select wether i want ubuntu or xp?

thanks in advance,
yoyspaSm:KS

---

### Post by Herman on 2007-10-02
> I would like to create a XP, Ubuntu (feisty) dual boot, I've got 2 hd's(SATA2,320GB). On the first I have a partition C: on which i have installed windows xp sp2, on partition D are just my files such as music. My new drive I have made partition F. I would like to install Ubuntu on F, my question is: Is this possible without plugging out HD's and just by installing ubuntu of partition F. Yes, that is normally quite simple and straight-forward, just look at this website here,  [COLOR=#3333ff]**[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php),**[/COLOR] and especially look at this page of that website here, [Install Desktop CD Ubuntu]("http://www.psychocats.net/ubuntu/installing") ,  That should help you plan what you want to do.
> And can i make the partition for the swap file during the installation? 
 Yes, that should be easy or maybe even automatic, refer to the links I already gave you.
> When I have installed on partition F do i have to put my ubuntu HD as primary boot device in BIOS or can i make it boot from my xp drive?
 Ubuntu will install a pointer in your first hard disk's MBR to point your BIOS to your new GRUB bootloader in Ubuntu. From there you'll be able to choose to boot either Windows or Ubuntu.
That's what most people do, that's the easiest and the best. In I guess roughly 99.9% of installations that will all go smoothly and you will have no problems, once in a while someone needs to do something extra to bet GRUB working 100%.
There is no such thing as an 'C" drive or an 'F' drive in Ubuntu, we use hard disk numbers and partition numbers, you'll get used to it, it's much more useful. :)
> And when it boots from my xp drive will i have a menu in which i can select whether i want ubuntu or xp? No, that is not easy to do, you can boot Ubuntu from XP but it's a lot of extra work and not as good as booting XP from Ubuntu.
If you really need to do that for some specail reason the you can install WinGRUB in your Windows and use that, but I do not think it is worth the extra work. Here is a page about that, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").
However, it is usually smarter to just use GRUB from Ubuntu because Windows needs to be re-installed very often compared to Ubuntu and you won't want to be losing the boot of Ubuntu whenever you re-install Windows or if Windows gets a virus or any bad problem. It is much smarter to let Ubuntu boot Windows because Ubuntu is immune from viruses and all kinds of other garbage, so it is much more reliable. Anyway, it's easier to do it that way too. :)

HINT: If you don't use Windows for email or internet any more but use Ubuntu instead, your Windows will stay clean and probably not need re-installing ever or at least for a long time.

EDIT: If you mean when you boot from the MBR of your first hard drive (which in your case happens to have XP in it), will you get a GRUB menu, then the answer would be 'Yes', it depends what you mean by 'you XP drive', I may have interpreted your question wrong, if I did then sorry about that. Some people call a partition a 'drive', especially if you are new from Windows. 

Regards, Herman :)

---

### Post by yoyspaSm on 2007-10-03
Yes, sorry for the confusion I meant my hard drive which has XP installed on it. Also my primary boot. But thanks for the very useful links. I will post another message when I encounter more problems.

thank you :D

---

