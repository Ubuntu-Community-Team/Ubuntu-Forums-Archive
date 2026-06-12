---
title: "Win7 U  64 + Ubuntu 11.10 64 + BT5 R2 64 Triple Boot (GRUB Entrys missing)"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by WickedXXL on 2012-03-22
Hi Guys !

I was sucked into the Linux Universe some time ago and enver looked back :)

But for LEarning Purposes and a few programs that I am used to i still have to have Win7 on my Notebook.


So I had Windows7 Ultimate 64bit and Oneric Ocelot side-by-side and not problems anywhere.. 

When Installing them i left 60Gig Partition espeicially for a third OS.

Now i Bootet up the BT5 Live Cd , solved my Blank Screen Problem and installed it.

In Install menu i choose "use largest continous space" as otherwise BT5 would have taken a cut of my Win Partition for itself..

Not i can Boot into BT5 flawlessly and everythign works..but Ubuntu and Win7 went missing from the BootMenu..

also it seems i installed a 2nd swap..how can i make Ubuntu and BT5 use the same? Or is that important anyhow?


Thanks for any answer or pointing to threads where this is already solved..(i found a few but they didn seem to solve my Problem)...

I am at the countryside right now and only have the BT5 CD with me ..nothing else.. :)

---

### Post by otherethe on 2012-03-22
> **WickedXXL said:**
> Hi Guys !

I was sucked into the Linux Universe some time ago and enver looked back :)

But for LEarning Purposes and a few programs that I am used to i still have to have Win7 on my Notebook.


So I had Windows7 Ultimate 64bit and Oneric Ocelot side-by-side and not problems anywhere.. 

When Installing them i left 60Gig Partition espeicially for a third OS.

Now i Bootet up the BT5 Live Cd , solved my Blank Screen Problem and installed it.

In Install menu i choose "use largest continous space" as otherwise BT5 would have taken a cut of my Win Partition for itself..

Not i can Boot into BT5 flawlessly and everythign works..but Ubuntu and Win7 went missing from the BootMenu..

also it seems i installed a 2nd swap..how can i make Ubuntu and BT5 use the same? Or is that important anyhow?


Thanks for any answer or pointing to threads where this is already solved..(i found a few but they didn seem to solve my Problem)...

I am at the countryside right now and only have the BT5 CD with me ..nothing else.. :)

It sounds to me as if it's missing from your Grub file, So just add them back with a timer of 10, If you don't know how to add them Just load up your back track 5 go into your Ubuntu folder it should be /boot/grub the files name will be grub.cfg and copy them from there into your bt5 grub should also be in your bt5 folder /boot/grub same file ect I don't know back track Never used it but I heard it's based on Ubuntu os should be in the same place, If you don't understand how to copy grub to grub just repost If i'm on i'll try and explain it 

PS. By doing this when you update your Ubuntu kernels ect you will need to update your grub every time but this is the simplest way for you to do this

---

### Post by WickedXXL on 2012-03-22
> **otherethe said:**
> 

PS. By doing this when you update your Ubuntu kernels ect you will need to update your grub every time but this is the simplest way for you to do this



Thanks a bunch ! will try that asap !

Can i get around the "redo everytime " if i install Easy BCD from Windows 7 then? 

I assume this should solve that...

Will try and let u know !

Thanks !

---

### Post by otherethe on 2012-03-22
> **WickedXXL said:**
> Thanks a bunch ! will try that asap !

Can i get around the "redo everytime " if i install Easy BCD from Windows 7 then? 

I assume this should solve that...

Will try and let u know !

Thanks !

The problem I stated is because you run more then 1 OS, It doesn't matter what OS has your main grub any time you use a OS that isn't the main the Grub will need to be updated each time you upgrade that system, Thats the prob with running TWO Linux Distros, If you have windows handle the boot then you will need to upgrade both bt5, and Ubuntu each time you upgrade them, Just like if you have the main grub on Ubuntu you will need to upgrade the kernels for bt5 in the Ubuntu Grub each time you upgrade bt5, Windows upgrades isn't as big of a problem with booting from grub as the Linux distros because it's upgrades are not the same Not sure if you can understand me or not because of the grammar if you don't I can try to explain it in another term

---

### Post by oldfred on 2012-03-22
What are you going to boot the most. Then that is the boot loader you should have in the MBR.

You should only edit grub.cfg once, as the work around of not having the Ubuntu liveCD to repair grub2's boot entry in the MBR.

Not sure if this works from inside in BT5 or not. It also has a full liveCD download.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can reset which system is the default boot by booting into it (if you can after the grub.cfg edit) and installing its boot loader to the MBR. This only works from your working install not a liveCD.
```
sudo grub-install /dev/sda
```

Ubuntu also sets links to the most current kernel in the / (root) and you can use the link to boot instead of referring to a specific kernel. Then you do not have to manually update anything.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number. And add this to 40_custom.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom


```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
```

---

### Post by WickedXXL on 2012-03-22
@otherethe


I tried copying grub cfg from ubuntu to bt5 via nautilus..but the only thing that happened was that now one second 

```

error, file not found
error, file not found
```



 blinks up on boot and the screen is blank..

i recovered from it because i had a backup..

EDIT: i thought so..just inserted the original grub.cgf but same error?

i am doublechecking everything now

---

### Post by WickedXXL on 2012-03-22
Okay heres what i did for now..

as restoring the frub.cgf was not sucessfull I inserted BT5 CD and reinstalled it with the Option Side by side..

now i have GRUB Bootloader again and can acess my OSes 

But my MBR and my partitions are now a bit chaotic..

thx @ oldfred with the bootrepair tips !

here is what bootrepair is showing

[http://paste.ubuntu.com/895526/](http://paste.ubuntu.com/895526/)

so now i am trying to identify the old BT5 install and to delete the partition belonging to it ..

and then i want to change the names shown in the boot menu :) any hints ?

maaan i feel so nobish ^  but i swore myself to get good at using linux :)

---

### Post by otherethe on 2012-03-22
> **WickedXXL said:**
> Okay heres what i did for now..

as restoring the frub.cgf was not sucessfull I inserted BT5 CD and reinstalled it with the Option Side by side..

now i have GRUB Bootloader again and can acess my OSes 

But my MBR and my partitions are now a bit chaotic..

thx @ oldfred with the bootrepair tips !

here is what bootrepair is showing

[http://paste.ubuntu.com/895526/](http://paste.ubuntu.com/895526/)

so now i am trying to identify the old BT5 install and to delete the partition belonging to it ..

and then i want to change the names shown in the boot menu :) any hints ?

maaan i feel so nobish ^  but i swore myself to get good at using linux :)


/dev/sda6         507,955,200   620,263,423   112,308,224  83 Linux /dev/sda7         620,265,472   625,141,759     4,876,288  82 Linux swap / Solaris /dev/sda8         185,942,016   302,643,199   116,701,184  83 Linux /dev/sda9         302,645,248   307,693,567     5,048,320  82 Linux swap / Solaris 
You have two swaps, You only need 1 as far as the old bt5 goes My best guess is it's on
sda6 because of the file size and number of it thats just a best guess

for editing the names thats very easy,  Just edit say the code in your pastbin
```
 
menuentry 'Ubuntu, with Linux 3.2.6 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod ext2 	set root='(hd0,8)' 	search --no-floppy --fs-uuid --set bf7eb353-5510-4776-9dae-b2d3f2515353 	echo	'Loading Linux 3.2.6 ...' 	linux	/boot/vmlinuz-3.2.6 root=UUID=bf7eb353-5510-4776-9dae-b2d3f2515353 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-3.2.6 }
``` Change the Ubuntu, with linux 3.2.6(recovery mode)' to what ever you would like it to say such as
```

menuentry 'your os or w/e you wanna call it' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod ext2 	set root='(hd0,8)' 	search --no-floppy --fs-uuid --set bf7eb353-5510-4776-9dae-b2d3f2515353 	echo	'Loading Linux 3.2.6 ...' 	linux	/boot/vmlinuz-3.2.6 root=UUID=bf7eb353-5510-4776-9dae-b2d3f2515353 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-3.2.6 }
```

---

### Post by WickedXXL on 2012-03-22
I just deleted both an reinstall now..if i got everything right now i should have the system as i wanted it in a few minutes..and then i can start learning :)  

(but not before i didnt image it all with clonezilla ^^)

thanks a lot for ur help guys !

---

### Post by otherethe on 2012-03-22
> **WickedXXL said:**
> I just deleted both an reinstall now..if i got everything right now i should have the system as i wanted it in a few minutes..and then i can start learning :)  

(but not before i didnt image it all with clonezilla ^^)

thanks a lot for ur help guys !

Just hope I helped you any, I know the way I explain things isn't always clear

---

