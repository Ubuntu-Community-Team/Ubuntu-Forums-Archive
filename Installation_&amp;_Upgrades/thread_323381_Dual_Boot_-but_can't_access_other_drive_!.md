---
title: "Dual Boot -but can't access other drive !"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Babak on 2006-12-22
I have two hard drives, 20Gig and 80 Gig. They both ran on Win2k.

On my smaller drive I installed Ubuntu Edgy Eft (over the Win2k OS). On the larger drive I kept Windows 2000 Professional. Before the install, on starting my computer I would see a dos like screen and be given a choice of which drive to go into (although it was actually a screen which showed the OS's - one above another... I had a few seconds to choose by using the cursor keys and press enter, or else wait until the timer expired and the computer booted whatever the default was).

I assumed that once I installed Ubuntu, this cosy arrangement would continue.   

Wrong!

Now when I start my computer it automatically goes into Ubuntu. It not only doesn't give me a choice but I can see no way of accessing my other drive or booting from it. I'm freaking out here!

I'd really appreciate any help, but  be gentle with me, I'm a total n00b and will have no idea what you're talking about if you start with shell commands and such. So please keep it simple and step-by-step.

Thanks in advance.

---

### Post by Ashrael on 2006-12-22
So if i'm correct you have on your first harddrive installed Ubuntu, and w2k on your second? it just means that you have to add your second drive to your grub config.... Try searching for GRUB on the forum.. you'll find the sollution to your prob. You're not the only one....

succes!

---

### Post by Babak on 2006-12-22
Thanks but what is GRUB? I see it on the screen (white text on black background) just before Ubuntu loads.  I have no idea what you mean or what I'm supposed to do.

---

### Post by bulldog on 2006-12-22
You have a choice really,only you didn't see it :D 
The boot manager you have is called GRUB and list all your OS's so you can boot them as you like.
The question is,which drive is the master on your machine,because GRUB will be installed on this disk.

If you can boot ubuntu,just do so and go and press ALT and F2 to same time.
This will open a box in which you type [copy and paste the commands is the easiest way]
```
gnome-terminal
```which will open a terminal for you.
This terminal we need to copy and paste more commands,and the feedback given by your terminal you have to copy and paste to the forum,so we can see what's wrong.

Okay here we go,```
sudo fdisk -l
``` to see how your drives are partitioned.
```
cat /boot/grub/device.map
``` to see which drive is the master
```
cat /boot/grub/menu.lst
``` to see how your menu.lst is is starting your Os's.
If you give us this info we can help you with your problem.

Welcome to ubuntu,btw.

---

### Post by Babak on 2006-12-22
Thanks. I did ALT+F2 and got a small window titled Run Application in which I c/p what you provided. Then I hit the button RUN. A new window popped up.

Here is what it said:

Could not open location 'file:///gnome -terminal'
The location or file could not be found.

I pressed OK/ENTER and it closed.

Is this (Run Application) something like the command line (Applications>Accessories>Terminal)? or something different?

---

### Post by bulldog on 2006-12-22
Sorry,try again,a wrong space placed between them :(

It's the same terminal as you mentioned,only I open it with ALT F2,it's a matter of taste really.

---

### Post by Babak on 2006-12-22
Ahh, ok. That explains it.

Alright, here is the output, in order of the commands you mentioned (line separated):


Disk /dev/hdc: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2392    19213708+  83  Linux
/dev/hdc2            2393        2498      851445    5  Extended
/dev/hdc5            2393        2498      851413+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    6  FAT16


--------------------

(hd0)   /dev/hdc
(hd1)   /dev/sda

--------------------


title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

---

### Post by bulldog on 2006-12-22
I can't see a windows install?
Where is your windows disk?
[Wrote a whole story,but you haven't windows installed yet I presume]

If you did have a windows install,I'm afraid you haven't it anymore.
Your Sata disk sda seems quite empty to me.

---

### Post by Babak on 2006-12-22
What? You've got to be kidding me!

I clearly installed Ubuntu on my smaller drive!!

How could it have formatted/erased my other drive? the one containing windows?

WTF?!?!? AAAuuuugh! Please, tell me you're joking. 

If it did, this shouldn't have happened! I didn't format my other (larger drive)! I only installed Ubuntu on my smaller one. Jeezus... I can't believe it. I'm hyperventilating here.

---

### Post by bulldog on 2006-12-22
Well your sda seems to be formatted FAT16 which is rather strange,because windows isn't using this for ages.
We can try to mount your sda so you can see if there's data on it.
In terminal,
```
sudo mkdir /mnt/windows
```
```
sudo mount -t fat16 /dev/sda1 /mnt/windows
```

Navigate to the /mnt/windows folder and have a look what's on it.

How it is happened,I don't know,but you have messed with the format option,ubuntu isn't going to erase a windows install by itself.

---

### Post by Babak on 2006-12-22
Thanks bulldog. I followed your instructions...

First command gives this result:
mkdir: cannot create directory `/mnt/windows': File exists

Second, this result:
mount: unknown filesystem type 'fat16'


How do I 'navigate' to the /mnt/windows folder?

---

### Post by bulldog on 2006-12-22
Try this```
sudo mkdir /mnt/rescue
```
```
sudo mount -t vfat /mnt/rescue
```

Open Computer and navigate to /mnt/rescue if the mounting was succesfull.
How can there be a folder /mnt/windows?

---

### Post by TheTeZ on 2006-12-22
Something kinda like that happened to me with my freespire install. 
To Solve the problem TRY downloadaing a new wboot manager [preferably not grub or anyother one that linux uses] and you should be able too see your O.S's.
I did this and have been happy ever since. Good Luck

One i would recomend is OSL2000 VERSION 5.6!!! trial, good luck ficnding it, youll probably get stuck with the new version, which means youll get a nag screen,  But in times of need who cares.... If you want version 5.6 let me know i can send you the file, the trial works with out the nag screen... for the most part.

---

### Post by bulldog on 2006-12-22
Would this work with the windows boot loader a s well?

You're saying in fact that ubuntu not recognize the windows partition?

---

### Post by TheTeZ on 2006-12-22
> **bulldog said:**
> Would this work with the windows boot loader a s well?

You're saying in fact that ubuntu not recognize the windows partition?


Are you replying to me?  If so, IF windows is still on the harddrive then a seperate boot manager should recognize it, and if its OSL it WILL recognize windows, the good thing about osl2000 is that it doesnt edit the MBL at all. it loads itself and lets you select an operating system with it, if you uninstall it, your computer will boot like it did before you installed osl2000

---

### Post by bulldog on 2006-12-22
Yes,if windows is on that disk.....................it should be recognized by ubuntu as well,the fact is that you only see a FAT16 partition.

Well we wait on further notice from TS.

---

### Post by TheTeZ on 2006-12-22
im pretty sure it will work if hes still got windows, cuz some how i messed mine up, and doing it worked for me... So yeah... i guess we gotta sit and wait.

---

### Post by Babak on 2007-01-02
Thanks for the help so far guys. :p 

I've been away for the holidays and stuff so lets see if we can get this fixed and rescue my poor Win2k with all my data on it!

While I was away visiting family during the holidays, by chance I happened to meet a techie who works for Celestica. He knows linux/unix well and windows inside out. So I took advantage of the chance meeting to see what he thought of this mess I made on my dual HD computer.

I showed him this thread and his diagnosis was that I was unable to see the other hard drive (with Win2k) because Ubuntu (installed on the 20 Gig drive) had actually written on it (the 80 Gig drive). I was bewildered and asked him how this was possible!

He said that eventhough there were two separate drives, for ubuntu they were seen as one drive with two partitions (I guess since they were connected - one being master, the other slave). He said that this is common and necessary for some technical reason which I've forgotten now.

His suggestion was that somehow this had overwritten or corrupted my MBR on the 80 Gig drive and that's why I couldn't see the drive or Win2k. His suggestion was to use the windows boot loader. He suggested that I use the Win2k recovery CD (recovery console) and type in something like: fixboot or fixmbr or fdisk /fixmbr

He pointed me to this (after some googling):
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Dual_boot_with_XP_2000_NT_and_install_linux_windows_whenever_You_want](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Dual_boot_with_XP_2000_NT_and_install_linux_windows_whenever_You_want)

He highlighted this part especially:

"Now you can go about installing your linux system. Here the issue to be taken care of is installing the boot loader (LILO/GRUB) to the proper place

Usually the installation program will ask u were to load the boot loader. default choice would be on the MBR. Now DON'T GO FOR THIS . If u want to go my way , don't go for it. Instead , get the installer to install the boot loader onto the root partition.Also note down the root partition's name , ie) the '/dev/hda*' where * is 1,4,5 etc.
If possible create a boot disk"

:confused: 

Also he said that the suggestion by TheTez to use another boot manager could perhaps fix the problem since his hunch was that GRUB was at fault here.

I found all of this reassuring since he told me that there was a very high percentage chance that my 80 Gig HD with Win2k and all my files, etc. could be restored but being the n00b that I am, I don't know what exactly I should be doing next. ](*,) 

Should I try to fix MBR/NTLDR? or go with OSL/LILO/etc as replacement og GRUB?

I'm afraid I've bitten off waaay too much and that it has turned around and bitten me on the butt!

I would really appreciate some help on how to get this all sorted out. 

Thanks very much.

ps in  my original message I made reference to having a choice of OS/HD's to go into at startup. I've found out that this was the NTLDR:
[http://en.wikipedia.org/wiki/NTLDR](http://en.wikipedia.org/wiki/NTLDR)

---

### Post by gn2 on 2007-01-03
Ubuntu's live CD installer doesn't give a choice of where to install Grub to, and puts it in the MBR of the master drive by default, and without adequate warning.

This is how I recommend setting up a dual-drive-dual-boot with Ubuntu: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

fixmbr should repair the damage in the meantime.

PCLinuxOS is better in that it will allow a choice of location for LiLo or Grub, and has much easier system configuration tools.

---

### Post by Babak on 2007-01-03
Thanks gn2, I appreciate the help (and the link)... I wish I had anticipated this and followed your tutorial before installing ubuntu. In usability they have two elements: the user's mental model and the 'machine' model. When these two are different, all sorts of antics ensue.

My mental model was that since ubuntu was being installed on a  separate HD my other drive would not be effected. The machine model as I've learned was quite different! Usability faults the designer in such cases since it is their job to anticipate the user's mental model and work to closely match it with the machine model.

Anyway, getting back to the nitty gritty... if I use the system recovery disk and fix my MBR will that mean that I've lost ubuntu on my 20 Gig HD? If so, that's not a big deal since I can then follow your instructions and install it the proper way so that the two drives/OS's play nice together.

Cheers

ps how do you "disconnect the Windows drive" and "reconnect the [first] drive"?

---

### Post by bulldog on 2007-01-03
Did you already try to boot from the sda disk?
You can set it as the master boot device in your BIOS.
Maybe it can boot,if not boot the windows install disk and let it run till you get three options.
1/Install Windows
2/Repair a Windows
3/Exit
Choose option 2 and you will be taken to a console,choose the windows you want to repair,mostly 1 provide the administrator password and type fixboot  and after that fixmbr
The last one will give you a warning but never the less proceed.
After doing so the windows MBR on the Sata disk is restored,and you should be able to boot the Sata [change the boot order in the BIOS!]

To disconnect the windows disk [Sata] just disconnect the power plug.

---

### Post by Babak on 2007-01-03
> **bulldog said:**
> Did you already try to boot from the sda disk?
You can set it as the master boot device in your BIOS.
Maybe it can boot,

I went into BIOS and switched the order of the boot disks and got this message:

NTLDR is missing
press CTRL+ALT+DEL to restart


> **bulldog said:**
> if not boot the windows install disk and let it run till you get three options.
1/Install Windows
2/Repair a Windows
3/Exit
Choose option 2 and you will be taken to a console,choose the windows you want to repair,mostly 1 provide the administrator password and type fixboot  and after that fixmbr
The last one will give you a warning but never the less proceed.
After doing so the windows MBR on the Sata disk is restored,and you should be able to boot the Sata [change the boot order in the BIOS!]

Would this allow me to use both OS/HD's? or only give me access to Win2k/80Gig HD and mean that I would have to install ubuntu again (using the instructions for dual boot as per previous link)?


> **bulldog said:**
> 
To disconnect the windows disk [Sata] just disconnect the power plug.

Just so there's no misunderstanding, this would imply opening up the case and physically unplugging the power that goes into my HD, right?

---

### Post by bulldog on 2007-01-03
If I see it well your GRUB is installed on the ubuntu disk so repairing your windows MBR allows you to start windows from the windows disk.
To start windows from GRUB we have to add the windows entry in menu.lst.

I'm just curious if your windows install still exists,just repair the windows MBR to see if it's still there.

Yes.to disconnect the Sata you have to open the case,but first look if this is of any use.

---

### Post by gn2 on 2007-01-03
> **Babak said:**
> TIn usability they have two elements: the user's mental model and the 'machine' model. When these two are different, all sorts of antics ensue.

My mental model was that since ubuntu was being installed on a  separate HD my other drive would not be effected. The machine model as I've learned was quite different! Usability faults the designer in such cases since it is their job to anticipate the user's mental model and work to closely match it with the machine model.

ps how do you "disconnect the Windows drive" and "reconnect the [first] drive"?

I see you may have had a good read through the thread and I couldn't have put it better myself.

Bulldog will give excellent advice, (much better than mine) he's a real Grub guru.

And yes, I meant physically disconnect the power connector to the hard drive.

---

### Post by Babak on 2007-01-03
I'm a bit stumped because I've put the Windows 2000 Pro CD in the CD tray but for some reason my computer doesn't boot from it. In BIOS the boot setting id's the CD-ROM as the 1st Boot Device so I don't know what else to do (??)

Am I doing something wrong?

---

### Post by gn2 on 2007-01-04
> **Babak said:**
> I'm a bit stumped because I've put the Windows 2000 Pro CD in the CD tray but for some reason my computer doesn't boot from it. In BIOS the boot setting id's the CD-ROM as the 1st Boot Device so I don't know what else to do (??)

Am I doing something wrong?

Some BIOS versions I've seen have a page to set the boot order and a page to identify bootable devices.
Is it possible the CD-ROM is set non-bootable?
Have you tried a cold re-boot?
Have you checked jumpers and connectors?

---

### Post by Babak on 2007-01-04
How can a CD-ROM be set to non-bootable? I'll look into it. Is this anything I can change?
Yes, I've tried cold re-boot... no help.
I don't know what you mean by "jumpers and connectors" could you please explain?

Thanks.

---

### Post by Babak on 2007-01-04
Alright...

The end of this tragic saga is at hand. I'm writing this thru Windows 2000 Pro on my 80 Gig HD... yes I broke down and took my machine to a pro and after wrestling with it for a while (missing NTLDR and then a strange compressed NTLDR message, he was able to get it back on its feet)

I'm just happy to have my computer back and find that all my files/programs are still intact. The only thing that ubuntu apparently blowed up was my boot.ini (and similar) file.

There's a lesson in all of this and I'll be writing about it but not here in this forum. 

Last, but not least, I wanted to sincerely thank everyone who pitched in and patiently tried to help this n00b understand what the bleep was going... I learned a lot more than I ever wanted to about BIOS and the intricate nuances of just how exactly a computer boots up... I also learned that there are a lot of very kind and knowledgeable people on the ubuntu forums who are ready to selflessly help out those in need.

Thank you very much, you're time and kindness is appreciated more than you can imagine!

Cheers

---

### Post by ubu_xp on 2007-01-28
Hi

i am also a new to ubuntu and i am having the same issue that "babak" had,
 basically "not able to login in my xp partition and not able to mount xp drives"

so what i have is
2 Drives
first drive (primary) 8 GB has ubuntu installed and working
2nd drive (secondary) 80 gm winXP installed and was working before i installed ubuntu.
now both of these drives have 2 partitions.

and here is my fdisk result.

Disk /dev/hda: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1001     8040501   83  Linux
/dev/hda2            1002        1048      377527+   5  Extended
/dev/hda5            1002        1048      377496   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6376    51215188+   7  HPFS/NTFS
/dev/hdb2            6377        9964    28820610    f  W95 Ext'd (LBA)
/dev/hdb5            6377        9964    28820578+   7  HPFS/NTFS

so you can see that  /dev/hda is ubuntu and /dev/hdb is win xp
so i basically have 2 issues.
1) currenly my desktop is not dual boot even though it has 2 OS.
2) not able to mount my windows drives on ubuntu. here is the result of mount command.

linux:~$ sudo mount -t HPFS/NTFS /dev/hda1 /mnt/windows/
mount: unknown filesystem type 'HPFS/NTFS'

i would be happy to see my windows drives mounted first.

any help is appreciated.
Thanks
ubu_xp

---

### Post by kj1h234lkj1234 on 2007-01-29
> **ubu_xp said:**
> linux:~$ sudo mount -t HPFS/NTFS /dev/hda1 /mnt/windows/

Try just:

sudo mount -t ntfs /dev/hda1 /mnt/windows/

;)

---

