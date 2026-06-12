---
title: "Hellp! Windows XP install won't let me boot!"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by suchawato on 2008-04-08
So I have a harddisk with 4 partitions.
A swap,
A version of windows home edition,
Ubuntu 7.10.
and, a utility partion that I normally use for backing up stuff or testing new Ubuntu or linux builds.

Well, some spyware corrupted my Windows system so bad that photoshop wouldn't run and I am unable to do my homework.
So I decided to install XP Pro in the utility partition so that I could get Photoshop and other programs running.
So far so good.
Well, upon reboot after the install,
A few things notably happended.

1, there was a new MS boot menu that let me choose between the Pro or Home Ed. partions.
However, the Home edition partion did not work. It gave me an error message saying it needed a hal.dll file or somthing like that in windows/sytem 32.
Well I checked through the Pro side and the file was there.
Also,  My user files were locked on my home edition side, so even though I could see them, I could not access them to back up my stuff.
Being unable to access my data, I decided to move on to fixing grub to restore Ubuntu 7.10.
Well I used Super Grub Disc and it restored Grub allright, but it did not fix the menu.
It still said I had the old OS's installed in my utility partion that I did not have.
Oh well,
I selected the line for my regular 7.10 boot and it failed.
Did not boot.
So I then rebooted and tried the windows line:
It gave me the windows bootloader screen where I could select the same two Windows partion.
At this point somthing interesting happended;
I could still from there boot into XP Pro, but the home Edition was still not letting me in for some reason.

So, I installed 7.04 (the disc I had on hand) in the utility partion eraseing XP Pro, hoping that a clean install would erase the problem and rewrite the grub menu properly.

No such luck.
XP Pro is indeed gone as I am typing this from Fiesty,
However the Grub menu still gives me the Windows boot selection screen if I select the Windows line.
Now of course neither of them work as Pro is gone and the problem seems to not have been fixed with the Home Edtion side.
I still cannot boot into 7.10.

Any ideas?
Suggestions?
I could really use that data.
It will not even mount so I can't back up through Fiesty.
Thanks,
Sara

---

### Post by suchawato on 2008-04-08
So I have a harddisk with 4 partitions.
A swap,
A version of windows home edition,
Ubuntu 7.10.
and, a utility partion that I normally use for backing up stuff or testing new Ubuntu or linux builds.

Well, some spyware corrupted my Windows system so bad that photoshop wouldn't run and I am unable to do my homework.
So I decided to install XP Pro in the utility partition so that I could get Photoshop and other programs running.
So far so good.
Well, upon reboot after the install,
A few things notably happended.

1, there was a new MS boot menu that let me choose between the Pro or Home Ed. partions.
However, the Home edition partion did not work. It gave me an error message saying it needed a hal.dll file or somthing like that in windows/sytem 32.
Well I checked through the Pro side and the file was there.
Also,  My user files were locked on my home edition side, so even though I could see them, I could not access them to back up my stuff.
Being unable to access my data, I decided to move on to fixing grub to restore Ubuntu 7.10.
Well I used Super Grub Disc and it restored Grub allright, but it did not fix the menu.
It still said I had the old OS's installed in my utility partion that I did not have.
Oh well,
I selected the line for my regular 7.10 boot and it failed.
Did not boot.
So I then rebooted and tried the windows line:
It gave me the windows bootloader screen where I could select the same two Windows partion.
At this point somthing interesting happended;
I could still from there boot into XP Pro, but the home Edition was still not letting me in for some reason.

So, I installed 7.04 (the disc I had on hand) in the utility partion eraseing XP Pro, hoping that a clean install would erase the problem and rewrite the grub menu properly.

No such luck.
XP Pro is indeed gone as I am typing this from Fiesty,
However the Grub menu still gives me the Windows boot selection screen if I select the Windows line.
Now of course neither of them work as Pro is gone and the problem seems to not have been fixed with the Home Edtion side.
I still cannot boot into 7.10.

Any ideas?
Suggestions?
I could really use that data.
It will not even mount so I can't back up through Fiesty.
Thanks,
Sara

---

### Post by pdadad on 2008-04-08
I'm no expert but have you tried to access the drive with your data from the Ubuntu CD?

---

### Post by suchawato on 2008-04-08
Yes,
No go.

---

### Post by zwygart on 2008-04-08
I cannot help you entirely, but can say some ways to solve some problems. You have more than one.

When you install a windows version, be carefull to not replace GRUB. It seems that you have GRUB so the most difficult is avoid.

In GRUB, are you sure that the partitions are selected correctly (ex.: (hd0,0)). If you are not sure, try some different values for the partitions by editing at start up. After that you can edit /boot/grub/menu.lst. This way you may be able to boot 7.10. In this you may be able to mount the windows partition. In the dir etc it have a file fstab. I don't remember where. In this you can add a line to mount Home partition at start up. The correct line is in the help of Ubuntu.

To remove the windows bootloader you have to edit a file in the root of Windows partition. I think it is boot.ini. In this you find to lines at the end : one to boot Home edition, the other the Pro edition. Only remove the right. In windows you can execute the command msconfig and then remove the line under BOOT.INI.

It's not a lot but I hope that it can help you.

---

### Post by zwygart on 2008-04-09
Now I am on Ubuntu (Version 6.10 liveCD),

I will complete my answer on how to access a Windows partition from a installed Ubuntu.

First, create a directory in which mount the partition.

```
sudo mkdir /media/windows
```

Then copy this file and edit it with administrator privileges.

```
sudo cp /etc/fstab /etc/fstab_sauvegarde
sudo gedit /etc/fstab
```

Ad this line at the end of the file 

```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

Replace hda1 with the partition where Windows is located. If Windows is on fat32, replace ntfs with vfat and umask=0222 with umask=0000.

This way you should be able to access your datas.

However, your Windows partition may be no more bootable until you fix with a way I don't know or format the partition. I hope it helps.

Also take a look at [http://ubuntuforums.org/showthread.php?t=747452](http://ubuntuforums.org/showthread.php?t=747452)

---

### Post by suchawato on 2008-04-09
> **zwygart said:**
> Now I am on Ubuntu (Version 6.10 liveCD),

I will complete my answer on how to access a Windows partition from a installed Ubuntu.

First, create a directory in which mount the partition.

```
sudo mkdir /media/windows
```

Then copy this file and edit it with administrator privileges.

```
sudo cp /etc/fstab /etc/fstab_sauvegarde
sudo gedit /etc/fstab
```

Ad this line at the end of the file 

```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

Replace hda1 with the partition where Windows is located. If Windows is on fat32, replace ntfs with vfat and umask=0222 with umask=0000.

This way you should be able to access your datas.

However, your Windows partition may be no more bootable until you fix with a way I don't know or format the partition. I hope it helps.

Also take a look at [http://ubuntuforums.org/showthread.php?t=747452](http://ubuntuforums.org/showthread.php?t=747452)

Hey I appreceate this,
However can you be a little more specific aobut how to do this?
Like step by step?
I am a visual arts student and I do not understand much of anything that you wrote for the command line codes.

specifically the copy and paste section.
I am not comfortable using the command line, so if I have to use it the instructions must be exact as I will simply be copying it into my command line and pressing enter.
I really don't know what I am doing here.
I am learning, but am not comfortable navigating using the command line.
Thanks a lot!
-Sara

P.S. Specifically where do I create the directory?
If you could be more specific and match that to your instructions that would be great!
Thanks!
-Sara

---

### Post by confused57 on 2008-04-09
Here's how to mount the Windows partition(for data recovery), using the live cd or an installed Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

You would need to:
```
sudo fdisk -l
```
-l is a lowercase "L"
this will show how your partitions are designated, then to mount an ntfs filesystem:
```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
substitute /dev/sda1 for your Windows partition.

You should then be able to open Nautilus, navigate to the /media/windows folder, then drag & drop files.

---

### Post by zwygart on 2008-04-10
Hi,

I'm sorry. The mount point is in /media/windows wich is at root. I forgot to write that you have to reboot the computer with my method. When you rebooted it should have a directory directly on the desktop. If not it is in Nautilus at root completly, directory media then directory windows. After that you are at root of Windows partition. The files of users are in the directory "Documents and Settings", User name, "My Documents". Then you should be able to copy the files you need. I never used the method of confused57 but it seems to be more efficient than my method. But you have to repeat it at each boot up. 

You don't need to change the command lines wich I wrotte. Only paste them directly in the terminal in that order and pressing enter after each line. But in the file you have to adapt the command. So after saving the file, exit, reboot and you should have a icon on the desktop called windows.

N.B.: To copy or paste in a terminal you have to press shift. So for pasting press Ctrl+Shift+V instead of typing it.

Post if you have an other problem.

---

### Post by suchawato on 2008-04-13
Oh hey thanks!
Your method worked,
Only thing though, when I was in gksudo nautilus,
I tried to change the owner of the "windows" directory and it wouldn't allow me to.

Even as root.

It said I could not change the owner as the "disc" was read-only.

What is that about?

And,

I presume I can do somthing similar with the gutsy partition to access it?

I would prefer to have grub be able to at least boot gutsy.

If not, i can back up the files in there, but I have done a lot of work on that environment, And I would like to access it if I can as a user and not just through a file tree.

-thanks!
-Sara

---

### Post by MightyMag on 2008-04-13
This is a Windows problem. Use method 2 in this guide.
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

---

### Post by suchawato on 2008-04-13
Oh wait, I just remembered, Fiesty cannot write to ntfs, that came with gutsy,
So I probably need to use gutsy or hardy beta to change my windows boot.ini file.

-Sara

---

### Post by suchawato on 2008-04-13
Ok, so I tried the method of mounting Windows, and it worked.
However, even as root and even in Gutsy, it will not allow me to write to the partition.
I *need* to write to the partition in order to be able to modify my boot.ini file in windows.

The link that mighty mag posted for the windows section will not work as I need my administrato password for windows which I do not remember.

However I still have not mounted my gutsy partion.
I am using the gutsy live cd right now, but my regular is still not mounting.

-Thanks!
Sara

---

### Post by suchawato on 2008-04-13
by the way, here is the output of sudo fdisk:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056    5  Extended
/dev/sda2   *        7296       16235    71810550    7  HPFS/NTFS
[COLOR="Red"]/dev/sda3           16236       19295    24579450   83  Linux[/COLOR]
/dev/sda4           19296       19457     1301265   82  Linux swap / Solaris
/dev/sda5   *           1        7113    57135109+  83  Linux
/dev/sda6            7114        7295     1461883+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/gutsy/ -t linux -o nls=utf8,umask=0222
mount: mount point /media/gutsy/ does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3/ -t linux -o nls=utf8,umask=0222
mount: mount point /media/sda3/ does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3/ -t ext3 -o nls=utf8,umask=0222
mount: mount point /media/sda3/ does not exist
ubuntu@ubuntu:~$ 

```

I as you can see, I tried sever varriations of a modified version of the windows instructions to get my gutsy partition to mount, and they didn't work.
The line in [COLOR="Red"]red[/COLOR] is my gutsy partion.

-Sara

---

### Post by confused57 on 2008-04-14
Here's how to mount your Gutsy partition:
```
sudo mkdir /media/gutsy
sudo mount -t ext3 /dev/sda3 /media/gutsy
```

Once you've mounted your Gutsy partition, you may want to post the output of:
```
gedit /media/gutsy/boot/grub/menu.lst
```

Added:  You should also probably post the output of:
```
gedit /media/gutsy/etc/fstab
```

Do get an error message when you try to boot Gutsy that a UUID cannot be found, something like press "Ctrl+D" to continue, then you're presented with a root command prompt?

---

### Post by zwygart on 2008-04-15
Hi Sara,

To mount gutsy the same way as windows partition make the same steps and add this line at the end :
```
/dev/sda3 /media/gutsy ext3 umask=0000 0 0
```
I'm not sure about ext3 but I think it should

The steps to do where :

```
sudo mkdir /media/gutsy
sudo cp /etc/fstab /etc/fstab_backup2
sudo gedit /etc/fstab

```

You said you have to write to Windows partition. It may present some risk. To be able to access change the umask of the windows line to umask=0000. So your line should look like this : 
```
/dev/sda2 /media/windows ntfs umask=0000 0 0
```

To be able to boot in gutsy : 

take a look at ```
gedit /media/gutsy/boot/grub/menu.lst
```

after you made this steps

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

At the end of the file add the block of lines which you see at the end of the file shown in the other code. The block should begin with the name of gutsy. 

Pasting the output of this files will it make easier to be clear : 

```
gedit /media/gutsy/boot/grub/menu.lst
gedit /boot/grub/menu.lst
```

The file asked by confused57 could help too.

Like I think about. Your grub wich boot the computer is in the second Ubuntu. If you remove this partition you will not be able to boot your computer or you find a method to redirect grub to the first Ubuntu. I don't know how. My answers should help you to be able to boot in both Ubuntu and to have read-writte access to your three partitions.

To boot Windows you may follow the instructions contained in the menu.lst file.

At next time

---

