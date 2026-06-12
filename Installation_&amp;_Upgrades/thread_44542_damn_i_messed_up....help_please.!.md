---
title: "damn i messed up....help please.!"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by raizen on 2005-06-26
k i really need help on this one. i think i f'ed up. 
i had installed kubuntu on my computer and everything worked fined. but then i loaded back on windows cus UNIX systems are too complex for me. im too much of a newb so i decided to delete the partition holding KUBUNTU. so then i reformatted the drive using a NTFS. after i rebooted my comp, it comes up with grub error 17 and my windows wont boot. like wtf? why cant it work. i changed my hdd type from LBA to NORMAL only to get "GRUB" spammed accross my screen not stoppping as for as i know. wel help is appreciated. thanks.

---

### Post by mingus on 2005-06-26
Grub is still installed in the HDD's Master Boot Record.  If you installed W2K or XP, boot from the CD and choose "R" to enter the Recovery Console.  At the prompt do:
>fixmbr
If you don't have this media (or it's an older vsn of W$), boot from a W98/ME/DOS bootable floppy.  At the A:\ prompt do:  >fdisk /mbr
If you don't have this media either, you can get it on the web, e.g., bootdisk.com

[I]FYI, from the Forum Policies and Expectations:
Profanity: Mild profanity/swearing is allowed in the context of general speech. Explicit profanity/swearing is not allowed.[/I]

---

### Post by raizen on 2005-06-26
[QUOTE=mingus]Grub is still installed in the HDD's Master Boot Record.  If you installed W2K or XP, boot from the CD and choose "R" to enter the Recovery Console.  At the prompt do:
>fixmbr
If you don't have this media (or it's an older vsn of W$), boot from a W98/ME/DOS bootable floppy.  At the A:\ prompt do:  >fdisk /mbr
If you don't have this media either, you can get it on the web, e.g., bootdisk.com

[I]FYI, from the Forum Policies and Expectations:
Profanity: Mild profanity/swearing is allowed in the context of general speech. Explicit profanity/swearing is not allowed.[/I][/QUOTE]
 oh. sorry about the profanity. i was just a little nervous  a little. thanks for the help, ill try it and see what happens. thanks again man.

---

### Post by raizen on 2005-06-26
[QUOTE=raizen]oh. sorry about the profanity. i was just a little nervous  a little. thanks for the help, ill try it and see what happens. thanks again man.[/QUOTE]
 ah ok! thanks man!!!1 it works!!! i appreciaite ur help man omg i thought i was completely screwed. yes my windows works again!

---

### Post by bored2k on 2005-06-26
Future use of profanity, specially on a topic will not be allowed. 
[http://ubuntuforums.org/faq.php?](http://ubuntuforums.org/faq.php?)

P.S. - It was enormously tedious having to edit every single post here.

---

### Post by mingus on 2005-06-26
[QUOTE=bored2k]Future use of profanity, specially on a topic will not be allowed. [/QUOTE]

Was it out of bounds for me to cite the policy . . .?

---

### Post by rvergara on 2005-06-26
[QUOTE=raizen]ah ok! thanks man!!!1 it works!!! i appreciaite ur help man omg i thought i was completely screwed. yes my windows works again![/QUOTE]

Raizen,

Now that you have cleared your MBR issue, can I ask you why you choose to reformeat your successful installation of Kubuntu? You could have kept your computer as a dual boot and then you would have an opportunity of learning more about Ubuntu.

Regards

Ramiro

---

### Post by bored2k on 2005-06-26
[QUOTE=mingus]Was it out of bounds for me to cite the policy . . .?[/QUOTE]
 Not really.

---

### Post by davahmet on 2005-06-26
Linux, and Ubuntu, is clearly not for everyone.  

Raizen, I wish all the luck in the world as you work in Windows.  When you feel you are ready, know that you can come and try again with the same or greater degree of ease that you had this time.  And, just as this time, you can expect to find lots of free help to get you up and running in Ubuntu-solo or even with dual-booted Ubuntu if you wish.

Ubuntu might not be able to compete in all areas against Windows and Mac, but one thing we do have is free, helpful support.  :)

---

### Post by raizen on 2005-06-27
heh thanks. well the reason i formatted kubuntu was because i needed the extra space for a video i planned to download on windows, and i didnt have much space left on my windows partition. so i figured since i wasnt really using kubuntu much because i didnt know anything about UNIX :D i just should format it until i read more about how everything works. i do plan on using UNIX, specifically (k)ubuntu again. this seems like a great community so far and helped me with my prob that i thoguht id have to erase my entire hard drive. heh well, yeah thats why :P

---

