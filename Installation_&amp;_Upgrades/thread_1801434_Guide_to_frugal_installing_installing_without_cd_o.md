---
title: "Guide to frugal installing/ installing without cd or usb Ubuntu 11.04"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by maximo360 on 2011-07-10
Hello!:D
I just frugal installed ubuntu 11.04 Natty after hours of research and troubleshooting using these steps. For those that dont know, a frugal install is when you burn an iso image to a hardrive and you load it from there. This is handy for those who dont have any cds or usb sticks laying around like me ;). Hopefully this helps.

_Steps:_
1. In windows, download the program,Unetbootin:[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to install the iso to your hardrive. (you dont need to install the program, just run it) Its really easy, fast and simple. Check the diskimage option,on iso select the iso of Ubuntu 11.04, on type select hardisk install, and then on drive select your C: drive, or whatever drive you want to install to. Then click ok and let it install. When it is finished it will ask you to reboot now or later, choose whatever you want. 
here is how your screen should look like:[ATTACH]197164[/ATTACH]

2. Once it is done installing, reboot and you will see two options in the windows bootloader, one is Unetbootin and one is Windows. Choose Unetbootin and it will boot into Ubuntu 11.04 livecd.

3. Once it is done booting, you will have to do two things to make the installer work, one is to trick the system to thinking /cdrom is not mounted so that you dont get an error saying "failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom"

And the other to prevent this error message when configuring apt to install packages from the cd:""An attempt to configure apt to install additional packages from the CD failed."

4. So first thing you do is go to terminal and enter: sudo gedit /etc/mtab
Once in gedit of the file mtab, delete the line telling the system that /cdrom is mounted, which is something like: dev/sda2/cdrom fusblk 
Or just look for the line that has the words "cdrom and fseblk"
Then save the file, close terminal, and reopen terminal.
Now the system thinks /cdrom is not mounted.
Which fixes the problem:"failed to unmount partitions 
 
 the installer needs to commit changes to partition tables,
  but cannot do so because partitions on the following could
  not be unmounted.
 
 /cdrom"

5. Next in terminal, type: sudo nautilus
You will be in root home. Go to file system, then go to usr/lib/ubiquity/apt-setup/generators/  
You will see the file  '40cdrom' and delete it or move it to trash. 
Now we fixed this error:"An attempt to configure apt to install additional packages from the CD failed."

6. Now your all set, just click the install icon, and install.


Extra: Some help for partitioning: It will automatically take you to to allocate drive space page, it will not let you choose whether to install alongside windows or use entire drive space,etc. when you double click on the partitions you are going to use, it will say"do not use this partition" just change that to "use as ext 4 or ext 3 journaling system" or whatever type of partition you are using. And then choose your preferred mount points for each partition.
p.s.:The installer will not let you create your own mount point you will have to choose one of the presets they have.

So in my case :
1. double click  12gb ext4 partition, choose "use as ext 4 journaling file system" and choose "/" as mount point. This is my installatin partition where ubuntu will be installed.
2. swap partition is already ready to use you dont need to change that
3. double click  120gb  ext 4 partition , "choose " use as ext 4 journaling file system", and choose "/home" as mount point. This is my home partition where all my files, music and such will be stored.
4. then click install now.

NOTE: Of course I created these partitions in Gparted beforehand.


Everything should work and if you should have problems let me know  and Ill see what I can do. Hopefully this works for you guys as it worked for me!:D

---

