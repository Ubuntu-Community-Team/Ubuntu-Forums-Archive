---
title: "ubuntu 10.04 install on samsung r60"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by ptd89 on 2010-07-15
Hi,
 
I'm new here and to linux. I've been trying to install 10.04 on my Samsung R60 laptop. When I choose to install to hard disk or use the live USB I get a black screen. I've been googling it and I think it's because of the ATI 1250 graphics on the laptop.
 
A couple of places say to change the queit splash to nomodeset but I have no idea how to do this :( Can anyone give me a guide or some advice please?
 
Thanks in advance

---

### Post by scdsone on 2010-07-15
i could never get 10.04 on my r60 i tryed the "nomodeset" in the boot setting when you install 10.04 but it would just black screen after it all installed

i tryed 10.10 beta for a few weeks & it installed fine but had to many problems (beta) so im back using 9.10 which is working fine

if you find a solution to installing 10.04 to the r60 pm me the answer thanks

---

### Post by ptd89 on 2010-07-15
I think you have to use nomodeset in the boot settings to install it, then when it loads for the first time you have to enter the GRUB and change the settings again and it should work. I think you can change the graphics driver to one that works then and everything should be fine.
 
I'm going to try it this evening so I'll let you know if it works

---

### Post by scdsone on 2010-07-15
yeah great i just used "nomodeset" at the install screen
i tryed some of the other 10.04 versions all with the same result (black screen)
i might try lubuntu because its lighter than ubuntu & i only use my laptop for surfing the net
ill post back in a couple of hours

edit
got lubuntu live cd to work & installed fine but just black screened on first boot

---

### Post by Cason on 2010-07-15
To change your boot options, select which system you want to boot, then press the key (I think it's 'x'; the bottom of the GRUB window will tell you.) If you select Ubuntu, it should look something like this:
```
menuentry 'Ubuntu 2.6.32-23' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
```
You would simply type one space add the "nomodeset" command after the "quiet splash" in this line:
```
linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash
```
Then the whole thing should look like this:
```
menuentry 'Ubuntu 2.6.32-23' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash nomodeset
	initrd	/boot/initrd.img-2.6.32-23-generic
```
Some other people have had similar screen problems and have been able to solve them by adding either "processor.max_cstate=1" or "nohz=off" instead of "nomodeset". If you're still having trouble, you might consider trying those too. :)

---

### Post by ptd89 on 2010-07-16
Thanks!
 
I got it to work using nomodeset then updated the graphics drivers once it was installed. All working now :D

---

### Post by scdsone on 2010-07-16
@ptd89

could you tell me how you did it in easy steps please

---

### Post by G-Freshman on 2010-08-03
> **Cason said:**
> To change your boot options, select which system you want to boot, then press the key (I think it's 'x'; the bottom of the GRUB window will tell you.) If you select Ubuntu, it should look something like this:
```
menuentry 'Ubuntu 2.6.32-23' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
```You would simply type one space add the "nomodeset" command after the "quiet splash" in this line:
```
linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash
```Then the whole thing should look like this:
```
menuentry 'Ubuntu 2.6.32-23' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash nomodeset
    initrd    /boot/initrd.img-2.6.32-23-generic
```Some other people have had similar screen problems and have been able to solve them by adding either "processor.max_cstate=1" or "nohz=off" instead of "nomodeset". If you're still having trouble, you might consider trying those too. :)

Hi.
I made same as you wrote here :added "nomodeset" and then it runs normally.But when I restart it i should enter same command again.Con you tell how can I save this.
Thanks.
laptop :Samsung r18plus  
os :ubuntu 10.04

---

