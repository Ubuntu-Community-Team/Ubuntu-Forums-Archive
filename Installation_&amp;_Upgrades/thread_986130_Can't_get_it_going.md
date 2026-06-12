---
title: "Can't get it going"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Oliverl on 2008-11-18
Hey

Just tryed to install Ubuntu for my first time.

I downloaded it and burnt it to a disk. No Problem. Then I partitioned my hard-drive so I had 48gb for Ubuntu. Then i ran the disk... It asked me to fill in some info, like language, username etc... it all went well. Then at the end it asked me to restart the coputer, so I did.

Then when I turned on, it was all going normall untill I get the part where it says "Updating DMI Pool Data ......... Update Success" When i get there it just stopps. With this little "_" flashing on the next line, I've tried leaving it for awhile, nothing happens...

So I turned it off and restarted, got to the first screen and entered the boot-up menu and had a go at booting up from the CD i burned. So i selected to use the CD drive and it got passed the "Updating DMI Pool Data ........" and goes somthing like:
"Updating DMI Pool Data .........
Booting from CD" them some stuff that goes to quick...

anyway, that takes me to a screen saying:

"ubuntu
Try Ubuntu without any change....
Install Ubuntu
Check CD for defects
Test memory
Boot from first hard disk"

Then some "f#" commands. I've tried just about every option and they all lead to the same black screen with a underscore flashing. They dont have any "Updating DMI Pool Data ......... Update Success" or anything just the flashing underscore.

Please help me :| I can't get into vista or ubuntu. And I dont have any CD's for my computer.

Thanks
Oliver!

---

### Post by Oliverl on 2008-11-18
anyone, anything? I really need to get my PC working again

---

### Post by Oliverl on 2008-11-18
bumb?

---

### Post by benson444 on 2008-11-18
Did a quick web search on updating dmi pool data and this is one of many similar pages I found

[http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)

It's the last message that BIOS shows before booting is passed to the OS. Hanging there could be due to several different things.

The first thing I'd try is checking the CD and then reinstalling grub, the boot-loader that Ubuntu uses. I'm supposing that you chose to install it to the Master Boot Record.

Boot from the Ubuntu CD and choose 'Check CD for defects', maybe the disc was not burned right and installed some corrupt files. If it passes the check then boot with the 'Try Ubuntu without any change' option. Open a terminal (Applications > Accessories > Terminal) and enter these commands:

sudo grub
find /boot/grub/stage1

That will give some output, like (hd0,1) or similar. Enter whatever was shown in the next command:

root (xxx,x)
setup (hd0)

Which will reinstall to the MBR.

---

### Post by want2bdifferent on 2008-11-18
it might be because you have the disk in?

take the disk out and try again

if you have installed it then it is trying to boot from CD, and it is rather then from your hard disk

---

### Post by Oliverl on 2008-11-19
Hey

Thanks for the replys. 
I'll try some of those ideas later, and get back to you on them. But one thing...I cant start at all, every option on the list goes to a " _ " even the "Check CD for defects" and "Try without any changes".

I'll have another go, at booting from the HardDrive...

---

### Post by Oliverl on 2008-11-19
Ok, Update

I've tryed booting from my harddrive again, still leads to "Updating DMI Pool Data ........" 

Just burnt it to another disk...still cant get past 
"ubuntu
Try Ubuntu without any change....
Install Ubuntu
Check CD for defects
Test memory
Boot from first hard disk" Its still always going to the same cursor...so now i've lost my hole pc I guess...

---

### Post by Oliverl on 2008-11-19
ok. I just put the Cd in, went to Boot up thing, selected the cd, and it went to the normall screen, Try without change, Install...etc...Anyway, I read in the help docs about Boot Parameters, So I pressed F6 typed, at the end acpi=off and pressed enter, over the install, and loooads of white writting was going down my screen. Well, eventually, the desktop apperared :) and an install dialogue comes, up i follow it through right to the end and it askes me to take the disk out and restart my PC, so i do. then when it comes back on, a square comes up with 5 options:

Ubuntu kernal somthing...
Ubuntu kernal Somthing eles (Recovery Mode)
Ubuntu Kernal
An other os:
Windows XP/NT/2000

i've tryed all of them, the first on comes up with the same sort of think as the DMI thing, but dosnt say DMI says somthing eles
the second one sends loads of white writting then dose the same
the 3rd dose the same as the 1st
the 4th says ERROR- invalid command or somthing
the 5th just repetedly sends me to the acer recovery manager.

But i now, using the acpi=off can run the try with no changes too. So i can use everything...just it wont install.

Is there anyway, I can just whipe my hooole computer?

Thanks and please reply someone!

---

### Post by themusicalduck on 2008-11-19
Can you put down exactly what it says when you choose the first option?

---

### Post by Oliverl on 2008-11-19
Boot from (hd0,0) ext3 89df64c2-ac68-475b-9c7c-f85b97949ac7
Starting up ...
_

---

### Post by Oliverl on 2008-11-19
Ok...now its changed to

Boot from (hd0,0) ext3 33cd8262-55ec-421d-a091-3297fea86e10
Starting Up ...
_

---

### Post by caljohnsmith on 2008-11-19
How about when you get the Grub menu, select the first Ubuntu option, press "e" to edit it, select the "kernel" line, press "e" to edit it, add "acpi=off" at the end of the kernel line, press return to save the change, and then "b" to boot. That should hopefully boot you into Ubuntu. 

If you can boot into Ubuntu, then open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And add the "acpi=off" to the end of the kernel line for the Ubuntu entries. Also you'll want to add the "acpi=off" to the "defoptions" line like so:
```
# defoptions=quiet splash [COLOR="Blue"]acpi=off[/COLOR]
```
And that should be it. Let me know how it goes.

---

### Post by Oliverl on 2008-11-19
Yayyy! It worked!!! I'm in, I think i love you...mabey not that far...but thanks loooooads!

but one think, when I turn on again, it just goes back to the same, and i have to add the acpi=off in the grub menu again...so I thought i hadn't saved it or somthing...but i opened up the menu file through the terminal again and it still says # defoptions=quiet splash acpi=off

Thanks!

---

### Post by caljohnsmith on 2008-11-19
> **Oliverl said:**
> Yayyy! It worked!!! I'm in, I think i love you...mabey not that far...but thanks loooooads!

but one think, when I turn on again, it just goes back to the same, and i have to add the acpi=off in the grub menu again...so I thought i hadn't saved it or somthing...but i opened up the menu file through the terminal again and it still says # defoptions=quiet splash acpi=off

Thanks!
Glad to hear you booted into Ubuntu OK; just run:
```
sudo update-grub
```
And then check your Ubuntu entries in the menu.lst to see that they have the "acpi=off" at the end of the kernel lines, similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d0b10c15-66ed-4d1c-b7f6-c1fc131636f7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]acpi=off[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Then you should be all set. :)

---

### Post by Oliverl on 2008-11-19
Yup :) Working now :)

---

