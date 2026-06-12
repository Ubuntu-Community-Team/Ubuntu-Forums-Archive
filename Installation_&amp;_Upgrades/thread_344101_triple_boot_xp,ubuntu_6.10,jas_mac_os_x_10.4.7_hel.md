---
title: "triple boot xp,ubuntu 6.10,jas mac os x 10.4.7 help"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by nfsfan on 2007-01-22
hi,i am a first time linux user and was very upset with windows(becoz i dont install any anti-virus since my system goes slow,i get viruses and spyware frequently).
i used the live c and was so impressed that i formatted my whole drive into ext3 for a ubuntu only system.but since i discovered yesterday that i could also intall os x to my pc,i am now thinking of installing all the three at once.but i have a few doubts regarding this.so let me clear mysfelf at what i am going to do and plz correct me(surely i will be wrong somewhere,i just couldnt understand 100% from the how to guides.)but firstly heres my config :

1.core 2 duo e6300;2.asus p5ld2-vm-se 945g;3.realtek audio;4.intel lan;5.xfx geforce 7300gs;6.sony dvd writer;7.512 mb ram;8.160 gb sata2 seagate hard disk;9.d-link dsl 502-t router connected via lan->ubuntu recognises it perfectly

so heres my procedure;
1.since currently all partitions are in: ext3,i will have to change them.using gparted,i will repartition them like this :
10 gb ntfs primary1
10gb ext3 primary 2
10gb fat32(i guess thats what os x uses,correct me plz if wrong) primary 3
1 gb swap logical 1
rest:118 gb fat32 logical 2 for all 3 os's.

2.install xp into ntfs(i've done that a thousand of times).
3.boot into live disk and install ubuntu amd64 6.10 into ext3 and without changing any other settings(confused about changing boot settings here).
4.install frm os x disk into partition 3 ->copied this frm somewhere .this is what i am going to do,although not confident what it means correctly,

[B]Press "Install" and wait a couple of minutes (like 10) for it to install. It will optimize the disk and stuff. Then it will reboot.

Remove the disc at the asus screen and then if should load. You will notice the GRUB bootloader, choose to start Ubuntu. Your going to have to edit menu.lst to add OS X to it. In terminal, type "sudo gedit /boot/grub/menu.lst" and type your password if needed. I'm going to update this later with what to do here, so if you really can't wait about 10 minutes for me to update it then just go into Gparted and set the HFS+ partition to active to boot of it instead of GRUB.[/B]
5.reboot and complete the installation.

i wanted to ask a few more things
1.how do i get to see my hard disk in the christmas edition live disk : tried a lot of mount commands but couldnt figure out frm where to acces my drive.my drive cuurently has /dev/sda0,1,2,5,6,7,8 points
2.is there an error in the christmas edtion while installing permanatly.i tried a few times but it gives an error at 92%,or is my hardware not supported?currently downloading amd64 version of 6.10
3.in triple booting process ,how to mount the fat32 partion when installing,or it will be mounted automatically in 6.10 ?

---

