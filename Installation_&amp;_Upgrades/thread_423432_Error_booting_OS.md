---
title: "Error booting OS"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by derrekito on 2007-04-25
I have no clue as to why I cannot boot Ubuntu.

I just installed it, went through the process and after it reboots I get message from the BIOS saying "Error booting OS".  

I'm running an AMD 64  and I downloading the correct feisty ISO as well.  I also verified that the partitions were indeed made.

---

### Post by derrekito on 2007-05-02
bump

I just installed it a couple more times, still receive 'error loading OS'

---

### Post by derrekito on 2007-05-03
Bump.

---

### Post by happydan on 2007-05-05
hey, i get the same error. i followed the steps in the installer and installed to a fresh drive. i have 4 HDDs, 1 SATA with windows, 1 SATA with kubuntu 7.04, 1 IDE NTFS with my docs on and a USB drive NTFS.

asked a couple friends that know linux and they are stumped too!

---

### Post by derrekito on 2007-05-05
This error is occurring on my SATA device (74 gig Western Digital Raptor).  Seriously I'm stumped, i cant figure it out.  Are you using the 64-bit or 32-bit of Feisty?

---

### Post by happydan on 2007-05-05
64, on a C2D 6300

---

### Post by derrekito on 2007-05-05
> **happydan said:**
> 64, on a C2D 6300

have u tried installing the 32-bit one of there?  I'm desperate to isolate the issue.  It COULD be that the 64-bit distro is defective?

---

### Post by happydan on 2007-05-05
ill have to download it... ill try.

---

### Post by derrekito on 2007-05-05
> **happydan said:**
> ill have to download it... ill try.

I'm swamped with finals, I wont be able to for another week.

---

### Post by happydan on 2007-05-06
same problem with thei386 version...

im installing using the steps in that applet thing. i choose the second option for installing (first is the one with the slider to choose the partition size)

is there anyone that will give us any help? kinda stuck here!!

---

### Post by derrekito on 2007-05-06
SO far everything points to the SATA device.  Do you know what chip set you are using?  I'm using the Nvidia (whatever is used on the Nforce 3 boards) chip set.

---

### Post by happydan on 2007-05-06
im using an asrock motherboard. not sure what chipset...

---

### Post by derrekito on 2007-05-06
> **happydan said:**
> im using an asrock motherboard. not sure what chipset...

If you have the manual for the mobo, that might help.  Other wise if u know the model number, google it.  I'm just going out on a limb here because we seem unable to get any help.

---

### Post by happydan on 2007-05-06
on of my friends suggested it might be the bios thinking the drive is no longer primary. have you tried running just the one drive?

---

### Post by derrekito on 2007-05-06
> **happydan said:**
> on of my friends suggested it might be the bios thinking the drive is no longer primary. have you tried running just the one drive?

This crossed my mind as well, however in my BIOS I am capable of making my other drives not even a choice for boot.  I have done this, and no cigar.  I am running three OS (well two really, ubuntu wont boot), and the other OS boots fine.  I have tried wiping them out and experimented with all kinds of alterations without success.  If pulling all my other hdds out, and for whatever reason that works, that will not solve my problem really, especially since I'm running 7 hard drives.

---

### Post by happydan on 2007-05-07
yeah. im in a similar boat. i have 4 drives. im happy using the BIOS as a boot loader, and i would really love to use linux. this is getting frustrating.

SOMEONE! HOOK A BRUTHA UP?!

---

### Post by derrekito on 2007-05-07
Do you know if Edgy works with your configuration?  I was thinking that if it does, install that then update to feisty?

---

### Post by happydan on 2007-05-07
i shall try

---

### Post by happydan on 2007-05-07
is that the same as dapper drake? 6.06?

---

### Post by derrekito on 2007-05-07
> **happydan said:**
> is that the same as dapper drake? 6.06?

HUH... I guess it is.  Weird.  If I get all the studying I need for POLS and Chem tonight I'll get on it tomorrow.

---

### Post by derrekito on 2007-05-13
I tried reverting back to Ubuntu 6.06 however, the disk wont even load the kernel to do the installation.  WTF is going on here!  I'm really frustrated, and I really need a nix box for some software development.  Ii don't want to go back to Slackware, because that usually requires way to much configuration and I do not have that kind of time on my hands.

---

### Post by happydan on 2007-05-15
i havent had time to do any testing the last couple weeks. its on my list!

---

### Post by derrekito on 2007-05-16
SUCCESS!!! 

Alright this is going to very tedious but it worked for me!


I essentially removed every HDD from my PC, leaving only the disk in which Linux was to be installed.  After that I added the other sata disk that had windows installed on it, using the grub guide on ubunutguide.org I was able to add Windows to the grub list without problems.  I haven't added all my hard drives as of yet, so wish me luck.


 ANYONE have ANY idea why this happened?  Did grub mess up?

---

