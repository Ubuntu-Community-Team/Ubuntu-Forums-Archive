---
title: "[SOLVED] install help (i'm a newbie with linux/ubuntu)"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by ecom on 2008-11-18
hi guys.

recently, my pc caught a virus. the OS was winxp pro. I tried to get rid of it but failed. i decided to switch to ubuntu 8.10. i downloaded ubuntu-8.10-desktop-i386 from ubuntu.com and burned it to cd. and i also checked the md5sum, no corruptions found.

I am a complete newbie to linux/ubuntu but i am (maybe) above average with using a computer.

i tried to install it but i got stuck in step 4 of the graphical installer. i decided not to let my hocus-pocus abilities prevail and i decided to ask the people here for help.

My hard disk is 80 gb, with 2 partitions. drive C is fat32 and drive D is ntfs. drive C is 30 gb and drive D is 50 gb. There is no OS installed in drive D and the windows xp is installed in drive C. I transferred all my personal stuff to drive D. I wanna replace the OS on drive C with ubuntu 8.10. the sooner i get rid of windows xp, the better. but at the same time, preserving my data on drive D.

May I ask for a very detailed guide on how to accomplish this task? 
Reformatting drive C doesn't affect drive D, right?

and also, can u guys tell me what to do exactly after installing ubuntu? how do i install my drivers? and stuff like that. 

Help!!! Help!!! Help!!!

PS: if someone already posted a problem similar to this, then i apologize.

---

### Post by iaculallad on 2008-11-18
You can try reading this page: [Installing Ubuntu 8.10]("http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml")
(Step by step installation guide with screenshots)

As for the driver, Ubuntu tends to auto-detect and install the drivers for your hardwares. But this could be limited that it requires you to manually install drivers for undetected/unsupported hardwares.

After your successful Ubuntu installation, you might want to install your restricted codecs.

---

### Post by ecom on 2008-11-18
hi and thanks.

but sadly, that guide doesn't fulfill what i need. i got stuck in step 4 of the graphical installer. that guide is not very detailed in step 4. the part where u choose between guided or manual. the instructions weren't clear enough.

can u be more specific or guide me personally? i'm a complete newbie to ubuntu. 

again, i wanna get rid of windows xp in my drive C. My personal stuff have already been copied to drive D. I wanna put ubuntu 8.10 on my drive C without affecting my drive D.

Reformatting only affects drive C, not drive D, right?

---

### Post by ecom on 2008-11-18
come on guys. BUMP!

I wanna put ubuntu 8.10 on my drive C. but i wanna keep my drive D intact. how do ya do this?

oh and to confirm, reformatting drive C won't affect drive D, right?

---

### Post by Sef on 2008-11-18
Please have patience - sometimes answers come fast and sometimes they come slow.   Don't bump unless 24 hours have gone by with no reply.  Thank you.

Check out [Psychocats]("http://psychocats.net/ubuntu").

---

### Post by ecom on 2008-11-18
yo Sef. hello. 

i clicked that guide but it didnt answer my question:

i've got winxp in my drive C. but it got infected. i transferred my personal stuff to drive D. Now i wanna put ubuntu 8.10 on my drive C and remove winxp from it. but i also wanna keep my drive D intact. how do ya do this?

oh and to comfirm, reformatting drive C doesn't affect drive D, right?

---

### Post by Sef on 2008-11-18
> i've got winxp in my drive C. but it got infected. i transferred my personal stuff to drive D. Now i wanna put ubuntu 8.10 on my drive C and remove winxp from it. but i also wanna keep my drive D intact. how do ya do this?

oh and to comfirm, reformatting drive C doesn't affect drive D, right?

Back up your data.  It should not affect your D drive.  However, there is no 100% guarantee that all will go well.  

You could just reformat your C drive.   That would erase xp and install Ubuntu.   

First, have you run the Live CD for a while to make sure that your system is compatible with Ubuntu?

Second, naming convention is different.  From the Live CD, go into the terminal (System > Administration > Terminal) and paste or type in this command:

```
sudo fdisk -l
``` Small L  - That shows your partitions.  Then paste a copy of them here, and someone can help you install Ubuntu on the correct partition.

---

### Post by ecom on 2008-11-18
i already backed up my data. i put them in my drive D.

[quote="sef"]You could just reformat your C drive. That would erase xp and install Ubuntu.[/quote] 

how do you put ubuntu in drive C without affecting drive D? this was my original question. I wanna kick out winxp from drive C and replace it with ubuntu. 

Oh and yes, my system is compatible with ubuntu. I played around with the live cd for 2 hrs.

to answer your last question, i have only 2 partitions. drive C is 30 gb and fat32. drive D is 50 gb and ntfs.

---

### Post by ecom on 2008-11-19
i'm sorry that i seem to be pushy but my dad recently got hospitalized and we really need to get the pc back going. my friend showed me the great features of linux and thats why we decided to ditch winxp. I checked all the guides on the internet, none of them answered my question. all of them are not even specific regarding step 4 of the installer.

is there something i failed to make clear? I only have 2 partitions. 

drive C is fat32 and size 30gb. 
drive D is ntfs and size 50gb.

i moved all my personal stuff to drive D. windows xp is installed in drive C. but i wanna replace it with ubuntu. how do ya do this without affecting drive D? all of those guides seem to format the entire hard disk.

---

### Post by ecom on 2008-11-20
bump

more than 24 hrs have gone by

---

### Post by oldos2er on 2008-11-20
Use manual installation, and point the installer to sda (which should be your C drive).

---

### Post by nickyoung on 2008-11-20
I am in the process of installing my self and have questions about the install but let's see if I can help explain partitions. :)

You have 2 partitions.  You can format either or both.  If you format C, D will remain intact with all files.  It is common to separate your documents from the OS/software by multiple partitions.  This way you can wipe C drive clean if the OS goes bad, and still have all your documents on D.  So for your case, it sounds like this will be easy since you already have 2 partitions.  It should be as easy as booting off the cd, and installing ubuntu right over the C partition.  As for the partition window, I'm a little unsure how it works cause I haven't done it before. lol...

---

### Post by ecom on 2008-11-21
guys can u provide a very detailed guide? or just guide me personally?

i tried that but when i select drive C, it says "no root file system defined"

again, how do u install ubuntu in drive C? can anyone give a more detailed help?

all of them internet guides out there, they just format the entire hard disk.

---

### Post by ecom on 2008-11-21
ok it seems you guys are busy. i got this reply from a friend via YM:

"In step 4 of the installer, select manual and select drive C. then delete that partition. recreate it as ext3 and add swap area 500mb. that should do it."

well, will this do the job? i have 512mb of RAM.

---

### Post by ecom on 2008-11-22
BUMP

come on guys. help a young kid get his ubuntu running.

---

### Post by ecom on 2008-11-22
this is what comes up during step 4 of the installer:

i selected manual and this is what came up:

Device====Type====Mount point=====Format?=======Size========Used
/dev/sda    
 /dev/sda1==fat32==============================31453 MB====16681 MB
 /dev/sda5==ntfs===============================50494 MB====41111 MB
 free space====================================8 MB     

when i select on sda1, and click the forward button below the window, it says "no root file system defined".

Help. i wanna kick out winxp from my drive C but preserve my drive D. all of my personal stuff are on drive D. How do u install it on drive C?
All of them internet guides seem to format the entire hard disk.

PS: ignore the "=" in the table above, the forum ignored the whitespaces

---

### Post by ecom on 2008-11-22
problem solved.

---

### Post by tuskenraider on 2008-11-22
this is assuming that drive c and drive d are two different hard drives.... 

yeah man format that puppy...  if youve backed up all your stuff to drive d then format c..  NO formatting of drive c will NOT affect your drive D.  Format away.  
When in the live cd use the guided method and use "entire disk" method.  Odds are it will be the hda0 drive (the one thats 30 gb) (if my hda0 label is wrong you will be able to tell which drive your formatting because of its size) ....  

hope this helps.... tho the thread is marked solved so i think im a little late with my help.:lolflag:

tusken

---

### Post by MerlinsLair on 2008-11-22
Nice of him to post back that he solved his problem and not relate what the solution was.

---

### Post by ecom on 2009-01-17
oh, my friend(the one on YM) installed it for me. 

i wasnt being sarcastic when i said "problem solved".

---

