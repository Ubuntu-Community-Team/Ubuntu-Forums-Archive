---
title: "Ubuntu runs fine on Preinstalled VISTA"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by rstevesat on 2007-04-03
Hi All,
          I tried to install Ubuntu 6.10 on a laptop withpreinstalled VISTA on it. Here is my story:
1. Always partition your hard disk with the partitioner that is coming with VISTA. Go to Control Panel->Administrative Tools ->Computer Management->Storage->Disk MAnagement. Previously my partiton was
 C:\145 GB  ,HP_Recovery:\6GB .
 Now partition the 145 GB into how much would you want for Ubuntu. Say if you want 100GB for Ubuntu . Then doing so should result in this partition :
C:\45GB , HP_recovery:\6GB . Now you wont see the 100GB because its still unallocated .

2. Now get out of VISTA . Boot through the Ubuntu Live Disc or other sources you have. Start to install it. Well it gives you 3 options about how you would like to partition the HD then select the 3rd one which is MANUAL.
3. now you can see the 100GB partition as unallocated. First create a Extended Parttition out of the whole space. Now with 100GB as Extended , partition it to as many logical partitions depending on how much space you want to give to / , swap and /home  and may others if you want. now you go FORWARD and mount the sd5,6,7 or hd5,6,7 coming out of the 100GB for swap , / , and  /home if you want. 
4. After this is done just go forward with the installation. I found that you dont even have to ad lines to the /boot/grub/menu.lst as my VISTA partition was already there created manually.
5. The next time you boot your system , you should find the VISTA in the boot menu as 
VISTA/Longhorn
hope this helps .

Cheers

---

### Post by webjames on 2007-04-03
hi, thanks for the post. do you know if feisty's new migration assistant works with vista? have you tried it?

---

### Post by Kristopher on 2007-04-03
By default i can see Vista on my laptop but to make changes i.e. remove or edit/delete files i needed to install "ntfs" from the add / remove or at terminal type

sudo apt-get install ntfs-config

Select the windows drive, name it say "windows" and thats you.

Regarding the migration assistant, it told me there was no users, I need to log in with my username and password so am guesing it doesnt.

---

### Post by rstevesat on 2007-04-03
Hi Kristopher ,
                     I can see my /VISTA mount when i log into Ubuntu as i mounted it while installation as ext3 supports ntfs.  But i could not see my Ubuntu partition in the VISTA, i suppose because it is ext3 and ntfs does not allow you to write/read from ext3 . Is that right? 
If i is do you know how to make both the ext3  and ntfs filemsystem do read/write on each other . i know it could be done but dont know how. thanks in Advance 

Infect Truth

---

### Post by Kristopher on 2007-04-04
Sorry am a noob when it comes to Ubuntu as I only started using it as my main OS for about 3 weeks now, before it was a VM (though hardly used it)

I did what i said in my post to be able to read/write to my Vista drive from Ubuntu. I know there is an application at [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) that lets you do the same under Vista.

Sorry but thats all know (so far)

---

