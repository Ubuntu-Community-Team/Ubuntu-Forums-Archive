---
title: "installation of linux on external HDD"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by TheNixObserver on 2011-08-14
I want to instal any linux distribution on an external hard drive.I have Ubuntu 11.04, Fedora 15 and Mint 11, but I do not know how it should be done. Mine is an old custom built PC with Intel 865G board and 1 GB DDR RAM running XP. Sound and video cards are integrated into the board.

I also have a R400 Lenovo laptop running Vista with 1 GB RAM.  I would like to use the HDD Linux instal on both the systems.

Ubuntu regular instal had problems with my PC hardware and had to be wiped off, so would prefer to have one of the other two.

Any help is appreciated.

---

### Post by raja.genupula on 2011-08-14
why dont you try to resolve the problem which you have faced in ubuntu .you said you have lenevo go with ubuntu there . ubuntu is faster than all i know . if you wanna check it out,  with out any risk take a move with wubi .if you have any problems simply you can remove it from add/remove programs in windows .

---

### Post by TheNixObserver on 2011-08-14
I have already thought of the Wubi option, but I don't want to do it.  I want to be able to use the HDD both with my PC as well as with my laptop.  A standalone HDD would be best suited for this purpose.

---

### Post by YesWeCan on 2011-08-14
Hi there. If you are new to linux you may find Mint quite friendly. fedora is not very friendly.

It's no problem to install to an external HHD. You just have to make darned sure you don't install the linux bootloader, Grub, to your internal XP drive by mistake. The Ubuntu installer defaults to doing this so you have to be vigilent. Alternatively, disconnect your internal disk.

---

### Post by ventrical on 2011-08-14
> **TheNixObserver said:**
> I want to instal any linux distribution on an external hard drive.I have Ubuntu 11.04, Fedora 15 and Mint 11, but I do not know how it should be done. Mine is an old custom built PC with Intel 865G board and 1 GB DDR RAM running XP. Sound and video cards are integrated into the board.

I also have a R400 Lenovo laptop running Vista with 1 GB RAM.  I would like to use the HDD Linux instal on both the systems.

Ubuntu regular instal had problems with my PC hardware and had to be wiped off, so would prefer to have one of the other two.

Any help is appreciated.


 I have Ubuntu 10.04 Lucid on two USB drives. I also had 11.04 but it was just a bit slow.

Fedora will not install correctly (at least for me).

If you have an 8GB pendrive (I use Dane Electronics) ...

1. Remove the hdd from the PC in question.
2. Insert CD into PC (open through pinhole).
3. Set to boot from CD in BIOS.
4.Start PC
5.Ubuntu will load up and when you are ready to install it, it will tell you that you have  8GBs of free space.
6. Choose yes.

You can then plug in your harddrive and if your PC BIOS is the right date then you can just choose USB/hdd/CD in BIOS. That way when you put your Ubuntu Pendrive into your PC it will boot up from there , otherwise your harddrive.

There are several other methods but this one works bonus for me.


You will now have a persistive drive that works and behaves as if it were an external harddrive through your USB port.

 I have Ubuntu Lucid installed on an 8GB and 16 GB USB pendrives, Lubuntu 11.04 on an 8GB and Linux Mint 10 on a 16 GB pendrive.

 They work out of the box... no broken pipes !!!!!!!!!


[http://www.youtube.com/watch?v=TuaqsrYjcPc](http://www.youtube.com/watch?v=TuaqsrYjcPc)


Above is a link showing my USB working. Sorry for the crappy video :)
,

---

### Post by Actonix on 2011-08-14
> **TheNixObserver said:**
> I have already thought of the Wubi option, but I don't want to do it.  I want to be able to use the HDD both with my PC as well as with my laptop.  A standalone HDD would be best suited for this purpose.

I think there is a major problem with your idea here - the problem is you want to install an OS onto a drive that you want to use to run the OS's for 2 different PC's with obviously different Hardware and therefore driver requirements.

I would suggest you go with the option suggested to have each individual PC running off it's own USB stick (and labeled as such so you know which USB stick is for which PC if they are identical sticks) and you use your ext-Hdd as a Data drive instead, I think that's the only way you will get both PC's to use your external drive without too much complexity involved.

That said you could probably have different partitions on the Ext-Hdd for each PC's OS install but only one would serve as the default boot for one of the PC's, on the other PC you would always have to remember to select the actual partition that holds it's own OS install.

---

### Post by ventrical on 2011-08-14
> **Actonix said:**
> I think there is a major problem with your idea here - the problem is you want to install an OS onto a drive that you want to use to run the OS's for 2 different PC's with obviously different Hardware and therefore driver requirements.

I would suggest you go with the option suggested to have each individual PC running off it's own USB stick (and labeled as such so you know which USB stick is for which PC if they are identical sticks) and you use your ext-Hdd as a Data drive instead, I think that's the only way you will get both PC's to use your external drive without too much complexity involved.

That said you could probably have different partitions on the Ext-Hdd for each PC's OS install but only one would serve as the default boot for one of the PC's, on the other PC you would always have to remember to select the actual partition that holds it's own OS install.

Actually I can use my Ubuntu Lucid pendrives on practically any PC (as long as I am careful with GRUB, not to scroll to boot from an option that was updated on the mother PC.) But then those can be edited out also). However , at first, you are correct , that it is a good practice to label usb drives to the HOME pc, however, I have found Ubuntu Lucid 10.04 to be an unbreakable kernel in mostly all cases - (in fact ALL cases) because I haven't broke the kernel in just about .. a year now .

And that USB has run on  Dell B130 Inspiron, Dell GTX Desktop, Acer Aspire 3620, Acer Extensa 4420, Sony Vaio,Cicero GIGABYTE desktop, IBM PL300, Compaq Pressario Desktop Pro .. Ebooks.. etc...

so, my point is that I am able to virtually carry my PC in my pocket , especially with Lucid LTS.

---

### Post by TheNixObserver on 2011-08-15
Thanks, will try out your suggestions.

---

