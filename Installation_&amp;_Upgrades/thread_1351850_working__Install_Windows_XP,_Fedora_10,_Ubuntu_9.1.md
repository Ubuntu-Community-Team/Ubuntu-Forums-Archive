---
title: "working : Install Windows XP, Fedora 10, Ubuntu 9.10 &amp; boot with Fedora's grub"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by sephiroth_slash on 2009-12-11
hii everyone

  I just managed to install : Windows XP, Fedora 10 & Ubuntu 9.10 !!! I used Fedora's grub to boot, it's works perfect after configuring the boot configuration file : /boot/grub/menu.lst
 

  Here is the process : 

 - I already had two NTFS Partitions, one for windows & the Other for data backup, XP was already installed then.

- I insered Fedora 10 DVD, and followed the install steps, untill the Partitions Step :
   
       Select Manuel or personalised partitioning, and create :

         /boot      200Mo    ext3      ( sda3 for exemple ) 
         /home    20Go      ext3      ( sda4 for exemple ) 
          /            20Go      ext3      ( sda5 for exemple ) 
         swap      ( suggest : 2x your RAM )          ( sda6 for exemple )
        
Of corse you can change the size of partition !! it's up to you !! just pay attention
make sure that the is some space left, at least 10Go

note the partition reference ( sda ) !! it's very important for what's coming ! 

then, pursuit the instalation, when at " grub " Page, fedora automaticaly detect Windows XP, & give it the label " Other ", you can set it the defalut OS or change it to " Windows XP " for exemple by selecting it & click on " modify ".

  then select your packages, the installation sould be fine.
  when  the installation is complete, it will restart, make sure to remove the DVD before booting. everything sould be fine until now.

- Then, to install Ubuntu 9.10, insert the DVD ( or the CD ) & follow the steps until the partitions step, as before, select Manuel or personnalised creation.

   here, we can use the partitions /boot and /home and swap for both ubuntu and Fedora !!! :D cooool huh ?? the user files & data will be the same on both ubuntu and Fedora .

 for the creation, you should have the partitions table ( in our case, from sda1 to sda6 )

=> select sda3, click on " Change..." or "modify ", change " do not use the partition " to ext3, and mount it under : /boot

=> select sda4, click on " Change..." or "modify ", change " do not use the partition " to ext3, and mount it under : /home

 ATTENTION !!!!! : don't check " Format partition " for both partitions !!! make sure of that !!!!!!!!!!!!!!


=> create a new partiton:      /       ext3      20Go     ( sda7 )

the swap is already there ! the one we created during Fedora installation 


    then click on "next" , pursuit the installation steps, Untill the last step ( 7/7 I guess, or 8/8 ), click on " advanced ", uncheck " Install grub ", we can't have two grubs installed !! .

  after the installation is complete, you will restart you computer, at the OSs selection, you will find that there is Only Windows XP and Fedora !! Ubuntu is not listed, otherwise it was successufly installed ?!! well, it is, but Fedora's grub don't know if there is a ubuntu or not !! we have to configure it to tell him that there is a ubuntu on this PC !! :D:D:p

  Boot Fedora, and Select terminal ( Applications -> system tools -> Terminal ),  if you type " df " command, you will see that there is a partiton that is not reconized as Linux partition, it's mounted under /media/disk, it's Ubuntu'spartition / ( sda7 in this case )

 then, type su, type root password, then gedit /boot/grub/menu.lst : 



          For the Fedora configurations, you will find something like that : 


        title Fedora (Kernel-2.6.27.5-117.fc10.i686)
                       r[FONT=&quot]oot (hd0,2)
[/FONT]     [FONT=&quot]kernel /vmlinuz-2.6.27.5-117.fc10.i686 root=UUID=63766a10-f196-47b2-b2be-2a057b4be170 ro rhgb quiet
       [/FONT][FONT=&quot]initrd /initrd-2.6.27.5-117.fc10.i686.img[/FONT]


       note that the space under "title" is tabulation, not space !! the TAB tells grub that it's a command  ( like the stuff in the makefiles in Linux :D ), to include Ubuntu's grub parameters, add the lines : 

     title Ubuntu 9.10            
                        [FONT=&quot]root  (hd0,2)       # the same as in fedora configuration,since there is one boot partition for Both[/FONT] 
      [FONT=&quot]kernel /vmlinuz-2.6.31-14.generic ro root=/dev/sda7              # the partiton that is mounted under /media/disk , where we installed ubuntu[/FONT]
       [FONT=&quot]Initrd  /boot/initrd.img-2.6.31-14.-generic[/FONT]






then save the changes, then reboot & you will see that Ubuntu Entry was added to the OSs select menu !! :D




note that if you have a different Ubuntu version, you have to know what is it's Kernel version !! you can run Ubuntu Livd CD ou DVD without install it, then type the command : grep vmlinuz /boot/grub/grub.cfg, here is it !! the same thing with configuring /boot/grub/menu.lst , use your kernel version instead in the Ubuntu configuration lignes .








Hope you'll have no problem with Installing ubuntu & Fedora :D


see yaaaaaaa

---

### Post by chuina on 2009-12-11
;)very very promising .........
thanks for this nice steps...

i wish to install **RHEL5**,**CentOS5** and **Ubuntu9.10** in one hard disk.
is the same procedure applicable for **RHEL5**,**CentOS5** and **Ubuntu9.10** ?
which one should i install first ??

---

### Post by sephiroth_slash on 2009-12-11
well, I can't tell for sure, but I think you should install RHEL5 first, since fedora is based on redhot, the RHEL5 grub file /boot/usr/menu.lst should be similar fedora's, in that case, you should install CentOS 5 & Ubuntu 9.10 & DON'T install their grub loader, you will keep the one of RHEL5, then you edit the file menu.lst as I discribeed abouve ( you will add lignes for Ubuntu 9.10, and others for CentOS5 )

   But as I told you, I'm not sure, this is Theorical :D

---

### Post by chuina on 2009-12-11
thanks for tips.

another thing is all of my RedHats and earlier Ubuntus detect my Hard Disk as **/dev/hdb1**.
though i pluged in my IDE cable to master. but it don't show any problem at all.

but this Karmic Koala  detect Hard Disk as [B]/dev/sda1. 
[/B]will it be an issue for multi-booting, if yes , then what should i do.

again thanking u.

---

### Post by chuina on 2009-12-11
I've tryed by these steps..
 
installed RHEL5 first . 
then while installing **Karmic** , file copying more 80% ,
it stop cpoying files and jump to **Live** Os mode. 
and on the upper task bar an icon appear with **Crash report detected**.

i have no RAID or LVM partition.

tryed twice but failed to dual boot with RHEL5.

---

### Post by sephiroth_slash on 2009-12-11
the fact that you can't boot RHEL5 means probably that you have modified the RHEL5 partitions, while you were installing Ubuntu Karmic, didn't you check the " Format partition " while mounting /boot ???
supposing that /boot originlay was created for RHEL5

---

### Post by chuina on 2009-12-23
Now i'm multibooting Karmic with RHEL5 :).
This time install Karmic first.
Using Karmic's Grub.

---

### Post by 14opsrc on 2010-10-10
Is there anything specific we need to consider if we are installing a mix of 32-bit and 64-bit versions of these Operating Systems. Lets say, I want to install the following :

1.) Win XP (32-bit)
2.) Fedora (64-bit) i.e., x86_64
3.) Ubuntu (32-bit)

Is the procedure same for installing the above three ?

---

### Post by sephiroth_slash on 2010-10-10
heey

No I don't think so, as long as u give every OS it's own " / " partition ( for linux )

---

### Post by 14opsrc on 2010-10-10
Also, another question. Lets consider the following situation:

1.) The root passwords for Fedora and Ubuntu are different.
2.) Root user in Fedora creates a user called fed1.
3.) Root user in Ubuntu creates a file called ubu1.doc inside /home/fed1/Documents folder.

So, in this case how does the whole permissions thing work. First of all, will Root user in Ubuntu be able to create a file called ubu1.doc inside fed1's home folder. If yes, will Root user in Fedora be able to access or change permissions of ubu1.doc ?

I want to know what kind of conflicts we might face if we use the same /home directory for both Fedora and Ubuntu.

---

### Post by sephiroth_slash on 2010-10-10
well, both root users have the right to do everything, if u have a user named "fed" created on fedora and an other user named " ubu" created on ubuntu,  from ubuntu , ubu don't have the right to acces fed's files & directories ( & I haven't tried it from fedora ) .

if there is the same user on both OS, exemple " /home/seph " , for exemple on fedora u created a file : " /home/seph/tmp.txt " and u wrote in it : " 123 ", and u reboot, then on ubuntu, u'll find it, if u open it u'll find : " 123", u can edit it : " 123456" and save, and again reboot and on fedora the file will remain and will contain obviously " 123456 " an so on .

But be careful, this simple example applies on all the files on " /home/seph" including config files, if u use the same session on both ( gnome for exemple ) on both OS, almost every every chcange u do on fedora will be the same on Ubuntu ( example : firefox settings, aMule setting .. )

---

### Post by 14opsrc on 2010-10-10
> **sephiroth_slash said:**
> well, both root users have the right to do everything, if u have a user named "fed" created on fedora and an other user named " ubu" created on ubuntu,  from ubuntu , ubu don't have the right to acces fed's files & directories ( & I haven't tried it from fedora ) .

Ofcourse user "ubu" will have no access to the files of user "fed" irrespective of whether we created each of them in different OS or in a single OS. My question was, if we create a user "fed" in Fedora and then log in to Ubuntu, can we create a file inside "fed" and access the file through Fedora. So, here are the steps:

1.) Create user "fed" in Fedora.
2.) Log into Ubuntu and create a file called (say) fubu.txt in /home/fed/Documents
3.) Log out of Ubuntu and log back into Fedora.
4.) Now, let us say the root user of Fedora will do something and change fubu.txt (note that user "fed" is not doing anything here. It is the root user that makes the changes)
5.) Log out of Fedora and log back to Ubuntu.
6.) At this point will the root user of Ubuntu user have access to fubu.txt ?

I was talking about the conflict of root users in two different OS sharing the same directory (like) /home.

---

### Post by sephiroth_slash on 2010-10-11
> **14opsrc said:**
> 
I was talking about the conflict of root users in two different OS sharing the same directory (like) /home.

 I get ur point, I don't remember having this kind of problems, so I guess the answer is there will be no conflicts, theoretically : 

if /home/fed/Documents/fubo.txt created & edited by root user of fedora, it's access rights
will be : 
   
             file owner : root , acces rights : 711 or 700 or something like that 


when u log on from ubuntu, the ubuntu root user will see the rights as : 

             file owner : root , access rights : 711 or 700 or something like that  
then, I think the file access rights apply just on some user named root as have the rights as root,
not specifically the root user of fedora or from ubuntu

---

