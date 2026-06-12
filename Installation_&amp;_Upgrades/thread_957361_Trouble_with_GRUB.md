---
title: "Trouble with GRUB"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by Flicules on 2008-10-24
Here is the thing.
I installed Ubuntu 7.10 some while back....and the 8.04 came out....it made the update and it worked just fine.So...on my hard drive i had and still have Ubuntu 8.04.
The problem is...i had to reinstall Windows..and yes it changed the MBR...so i had no GRUB.
I searched the forum and i found about the Super GRUB...i made a cd...and it did recover my GRUB...but when it loads...it has the old stuff(i don't know how to call it)
I already said my ubuntu updated from 7.10 to 8.04.
The recovered GRUB now looks like this:
Ubuntu 7.10
Ubuntu 7.10 kernel
MemTest
....
WindowsXP
Windows boots just fine.The trouble is with ubuntu.When i select it...i get Error 17.
What should i do.Can i edit GRUB...to change something?It works...but it doesn't contain what it should.
My hard drives are on Promise Fasttrack RAID.
Thanks.

---

### Post by kellemes on 2008-10-24
You probably instructed SGD to reinstall a default Grub install?
Is this possible?
You need to let SGD point to the correct /boot/grub/menu.lst (the one of your updated Ubuntu install) to "fix" grub.

Can you post /boot/grub/menu.lst if you can't work it out?

---

### Post by caljohnsmith on 2008-10-24
Having a RAID setup can cause problems with Grub, but if you had it working before, you should in theory be able to get it working again. How about booting your Live CD, open a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -lu
```
Also, one thing you can try is the next time you boot, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)" and let Y be 0,1,2,3,4,5 or however many partitions you have, press return to save the change, then press "b" to boot. One of those combinations will probably work to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know if you get as far as being able to boot Ubuntu (which (hd0,Y) you used), and we can work from there. :)

---

### Post by Flicules on 2008-10-24
Thank you for the help....i'll try and reply as soon as possible.:)

---

### Post by Flicules on 2008-10-24
It worked....so it's root(hd0,2)
It didn't work the first time...and i tried again and changed root(hd0,2) and something in the second line(the kernel)....pdc_ijifdjie4....changed it to pdc_ijifdjie3.
These lines were both under the first line in GRUB(Ubuntu 7.10)
It did not run as before...it did do some checks...1%...100%...and then the Ubuntu screen appeared(my old Ubuntu 8.04).
:D
Thanks....please guide through the next stepts....to make these changes permanent.:)
Thank you again for your time.

---

### Post by caljohnsmith on 2008-10-24
OK, if (hd0,2) worked, that would mean Ubuntu is on sda3 (if you have only one drive, otherwise that won't be true). So once you get into Ubuntu, just do:
```

gksudo gedit /boot/grub/menu.lst

```
And change the line that has "# groot=(hdX,Y)" to:
```
# groot (hd0,2)
```
But about changing the UUID in that kernel line like you did, make sure you get the *exact* correct UUID, which you can find with:
```
sudo blkid
```
And use the UUID for sda3, but that assumes you don't have a /boot partition, is that correct? Then change the following line in your menu.lst with the correct UUID:
```
# kopt=root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro
```
So replace the UUID above with the UUID of sda3. Save, quit gedit, and run:
```
sudo update-grub
```
And you should be all set about booting Ubuntu. Let me know how it goes. :)

---

### Post by Flicules on 2008-10-24
It works but i do have to change the kernel lines in order to boot Ubuntu

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper[COLOR="Red"]/pdc_ijifdjie3[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper[COLOR="Red"]/pdc_ijifdjie3[/COLOR] ro single
initrd		/boot/initrd.img-2.6.22-14-generic

I checked the other thing you said about the UUID and it was correct as the one returnet by the command line you said.
If i only change root(hd0,2) the freezez...it sais Ubuntu...and the loading bar just doesn't move.
After i changed [COLOR="Red"]/pdc_ijifdjie3[/COLOR] (initially it was 4) it loads just fine.
Is that correct what i did?...i mean it works...but is it as it should be done?
Another thing....i'm tring to install ATI drivers on my computer...and the installations stops in the terminal...saying i have to be a super-user in order cu run this application.
I'm really starting to stress you out with to many questions....please do not get mad...i'm new with linux.
The other thing that doesnt work...are the updates...when i try to install them...it request the Ubuntu8.04.1 Hardy Heron CD...why?...it didn't ask before.
And the last thing...when i try to set the appearance to Extra Visual Effects or Normal...the system crashes...it does not respond....the screen freezez.
Sorry to bother you.:)

---

### Post by caljohnsmith on 2008-10-24
> **Flicules said:**
> It works but i do have to change the kernel lines in order to boot Ubuntu

```
title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper[COLOR="Red"]/pdc_ijifdjie3[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper[COLOR="Red"]/pdc_ijifdjie3[/COLOR] ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```

I would recommend sticking with UUIDs instead of the /dev/mapper drive listings as you have above. Just change the kernel lines similar to:
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=[COLOR="Blue"]UUID=51c6525c-a30b-49c5-b67d-7a83626c5049[/COLOR] ro quiet splash

```
And use the UUID for sda3, or your Ubuntu partition. 
> **Flicules said:**
> 
Another thing....i'm tring to install ATI drivers on my computer...and the installations stops in the terminal...saying i have to be a super-user in order cu run this application.
I'm really starting to stress you out with to many questions....please do not get mad...i'm new with linux.
No problem, when you need to run a command/program as superuser (also known as "root user"), for a command that runs in the terminal you would do:
```
sudo <command>
```
Or if you are trying to run any type of graphical program, like nautilus for example, you would do:
```
gksudo nautilus
```
But don't run the program/command as root user unless you have to, because you can really mess up your system if you are not careful.
> **Flicules said:**
> 
The other thing that doesnt work...are the updates...when i try to install them...it request the Ubuntu8.04.1 Hardy Heron CD...why?...it didn't ask before.
If you go to System > Admin > Software Sources, I believe you can disable using the Live CD in one of its tabs. I'm not in Gnome right now so I don't remember exactly, but see if you can find it there. 
> **Flicules said:**
> 
And the last thing...when i try to set the appearance to Extra Visual Effects or Normal...the system crashes...it does not respond....the screen freezez.
Sorry to bother you.:)
Well first you should get your graphics card working OK with the ATI drivers, and then you can try adding the extra eye-candy effects. See how that goes, and if you have problems with it, it would be good to start a new thread with that subject and not post here. And if you search the forums, I know you will find lots of info that will help. Good luck and let me know how it goes. :)

---

### Post by Flicules on 2008-10-24
It works!!!!
The thing about the UUID is that it's already there...it's correct.....
I'll just leave it that way....
Hope to not get in trouble.:)
I installed the ATi driver...it worked...need to restart...i'm downloading updates now:)
I'll keep you posted....thank you for all the help.

---

