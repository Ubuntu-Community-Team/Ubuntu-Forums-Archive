---
title: "installation on windows XP"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by gsudhindra on 2012-08-21
Hi,
 
I recently installed ubuntu using the live CD, it booted with the CD and then I choose to do the installation. However the installation never worked. When i restart the PC, it does not run ubuntu without the CD.
 
I created partitions as below (chose EXT4 for all and selected primary for /) - 
/ 5 GB
/home 1 GB
/usr 1 GM
swap 800 mb
 
I also choose the hard disk name in the drop down when it said where to install the boot loader. i do get the initial list of OS to select, but when i select something now, nothing works. Even with the live CD it doesn't work.
 
So i tried OpenSuse, burned the ISO file into a CD and it did boot. I chose the install option, after sometime the screen went blank and nothing happened.
 
Now i am not able to boot the computer and use Win XP as well. Does anyone know what i did wrong and how to fix it? I do not want to format the C: drive as well.
 
 
Thanks,
Sudhindra Gururaj

---

### Post by darkod on 2012-08-21
If you started the OpenSuse install over ubuntu, I guess their forum is a better place to look for answers. The ubuntu live cd should always work, no matter what is on the hdd.
There are cases when the live desktop doesn't boot properly because of video driver issues, but if it loaded once for you, it seems the hardware is supported.

What exactly happens when you try to boot from the cd? Are you sure you are booting from it and not from the hdd?

---

### Post by gsudhindra on 2012-08-22
hi,
 
I tried disabling the HDD from BIOS to avoid a hard disk boot, but i got a disk boot failure error.
 
The live CD worked perfectly fine till I chose to install it and created partitions. I am worried now that I might have messed up with the master boot record, but I am getting the OS choice menu though.
 
please ignore about the OpenSuse thing, i just mentioned it since even that didn't work.
 
 
Thanks.

---

### Post by mastablasta on 2012-08-22
what happens if oyu boto from live CD delete all ubuntu partitions and then simply chose to install on largest empty disk space (or something like that) leaving the installer to create only necessary partitions. it could be you are low on disk space (you gave it 6.9GB) . if you can (and if you intend to Ubuntu more often) give it at least 15 Gb in total disk space. i gave Xubuntu (i think it needs less disk space by default anyway) 8 GB and space got filled up preety fast with new kernel updates. i removed old kernels and a few progs i don't need (GImp and such) which left me with little less than 2 GB free space.
 
so just to to give it some more disk space. see if that helps.

---

### Post by gsudhindra on 2012-08-22
it doesn't boot even with the live cd. that's what i was desperately trying to do, somehow boot and delete the partitions. so tried with OpenSuse cd, but didn't work.
 
will try again today and post what i could do. thanks for taking the time with my query.

---

### Post by mastablasta on 2012-08-22
ah that is strange. if it boot before it should boto now (providing the CD is still good).
make sure the boot is set to boot from CD first. botoing form live media should work even if oyu unplug the disk out. all it need sis drive for live media (e.g. cd drive, usb plug), motherboard and RAM.
 
you could try to use: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
however i am not sure if it will work or help since yo say you booted before without this.

---

### Post by darkod on 2012-08-22
The situation is really strange. What ever you did on the hdd has nothing to do with booting from cd (or at least it shouldn't have).

Booting from cd is one thing, what you have on the hdd completely different.

It could be that the cd or the optical drive are failing you. I know it worked before, but it doesn't mean it will continue working always. :)

Try the cd in another computer.
Try replacing temporarily the optical drive with another one if you can, or using external usb optical drive to see if that works.

Also you can try making new cd and burn it at low speed, not more than 8x or 10x. That lowers the burning errors.

---

### Post by irv on 2012-08-22
Let's back up completely here. Maybe you should first try getting your WinXP working first. Go into your BIOS and set your boot list to boot from the CD first then the HD second.
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list. Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

Once you have the computer working in WinXP you can try to re-install Ubuntu. Boot from the Ubuntu CD/DVD. Boot into the live OS off the CD/DVD and run a program called gparted. Take a screen shot of what your Hard Drive looks like and we can go from there.

---

### Post by gsudhindra on 2012-08-26
Thanks all for trying to help. had been spending all the time i could get to fix my PC, finally lost my patience and installed OpenSuse.

I have XP licence but no software :( 

I got to know two things, one the RAM could have given problems, recently had upgraded, and two the live cd itself could have given problems.

irv, read your post little late. it sounded like a workable solution, read it too late.

thanks again,
Sudhindra

---

