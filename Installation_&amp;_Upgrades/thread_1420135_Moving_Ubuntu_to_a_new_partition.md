---
title: "Moving Ubuntu to a new partition"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Dr Droid on 2010-03-02
Hello all -

Recently, I began getting error messages when logging in due to the fact that I was running low on disk space on my Ubuntu partition. I started downloaded a file and later that night logged off- When I came back to log in I was unable to get all the way into my desktop manager. An error spit back at me something like: "Power Manger Settings were not set correctly". Immediately I understood that first of all since im running Ubuntu on my Desktop, that this was not the problem, but it was because I had no disk space to log in. Im not entirely certain but I believe my system was like so:

/dev/sda1
   /dev/sda3 - OS Vista 80 GB          *BOOT
   /dev/sda4 - NTFS SHARE SPACE 120 GB
/dev/sda2 -
   /dev/sda6 - OS ubuntu 29GB (FULL)
   /dev/sda7 - Swap 1 GB
   /dev/sda5 - NTFS SHARE SPACE  170GB (FULL)

Don't ask me why I originally partitioned them this way but nevertheless I was in serious need to resize sda6. My first step was to boot off a live cd, I use knoppix. I opened up GParted and there was no space for me to just resize the partition so I decided to format sda3 as ext4 and copy sda6 onto sda3. This part is fairly simple using GParted, just right click copy and paste sda6 into any unallocated space (use dd for the CLI). Now you should see both partitions listed as ext4 in GParted. I kept the original ubuntu install until after I finished this upgrade. Now the next step is to change your mount point for / in /etc/fstab on the drive that you will be booting off of. So mount the drive somewhere, i used a folder called /media/sda3, like this:

```
sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
```Change directories until you get into the etc folder on your new drive like so
```
cd /media/sda3/etc/
sudo gedit fstab
```search for the line that looks something like 

```
UUID=39c14bf8-g295-4385-9222-5dde32b7a9db / ext4 errors=remount-ro 0 1
```The uuid above should be edited to match the uuid of the destition drive you have copied ubuntu onto.

If you type this in command line 

```
sudo blkid
```you will notice that the uuid's of the two partitions you are toying with are identical. This is a big problem if you do not do something about it. Type in (change to appropriate device)

```
tune2fs -U /dev/sda3
```Now a new uuid should be assigned to sda3. If it was not displayed back to you or your simply a clutz, type

```
sudo blkid
```find the new uuid and place it in line in the /media/sda3/etc/fstab file we found before. Make sure that you are editing the line that corresponds with the / mount point.

Another problem that I ran into after updating the fstab file was that the new Grub2 was not playing nicely with me at all. Here is how I got it to work. If you are using legacy grub then please do not read the rest unless you want to upgrade to grub2.
If you are unsure of what ver. of grub you are using type 

```
grub-install -v
```[Warning: I am not a grub or ubuntu expert. I am just contributing to the Ubuntu forum who have been so helpful to me in the past. Also, I suggest reading the wiki's for Grub2 before continuing on in case you run into unforeseen problems of your own. This being said there may be 100 ways to do this faster and safer than how I am showing you. nevertheless read on if you'd like to see how I managed to get it to work.]

Mount the drive with your original ubuntu install to a folder of your choice. Mine was /media/sda6, like so:

```
sudo mkdir /media/sda6
sudo mount -t /dev/sda6 /media/sda6
```now once again from your live cd change directories until you are in /media/sda6/boot/grub/

then: 

```
cat grub.cfg
```scroll up until you see the similar:

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-15-generic-pae (/dev/sda3)" {
        recordfail=1                                                      
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi           
        set quiet=1                                                       
        insmod ext2                                                       
        set root=(hd0,6)                                                  
        search --no-floppy --fs-uuid --set 39c14bf8-g295-4385-9222-5dde32b7a9db
        linux   /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=39c14bf8-g295-4385-9222-5dde32b7a9db ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set 39c14bf8-f295-4085-9412-5dde32b7a9db
        linux   /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=39c14bf8-f295-4085-9412-5dde32b7a9db ro single
        initrd  /boot/initrd.img-2.6.31-15-generic-pae
}
### END /etc/grub.d/10_linux ###

Copy the first part of this so all you have on your clipboard is this:

menuentry "Linux Mint 8 Helena, linux 2.6.31-15-generic-pae (/dev/sda6)" {
        recordfail=1                                                      
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi           
        set quiet=1                                                       
        insmod ext2                                                       
        set root=(hd0,6)                                                  
        search --no-floppy --fs-uuid --set 39c14bf8-g295-4385-9222-5dde32b7a9db
        linux   /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=39c14bf8-g295-4385-9222-5dde32b7a9db ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-15-generic-pae
}

I am an avid knoppix fan so I used one of their live cds to boot up so I could manipulate the files on my hard drive. I opened a CLI and navigated to the /media/sda6/etc/grub.d folder. If you ls the directory you see a few scripts that contribute the the grub.cfg file which makes your handy desktop boot up.

```
sudo gedit 40_custom
```###on the bottom of the file paste your clipboard. Once you have pasted the info into the file replace  the UUID with the new UUID you created moments ago. Also be sure to change the line 
 set root=(hd0,6) 
to (in my scenario)
 set root=(hd0,3)   

hd0 represents grubs drive number and 3 is the partition (therefore, sda3 = (hd0,3))
alt+f, s, alt+f, q              (save and quit in gedit)
in CLI type

```
sudo chmod +x 40_custom
```To make the file executable. I also like to make the 30_os-prober file executable just in case it for some reason finds the OS right away.  

This will add a custom entry at the bottom of your grub menu. 

now run

```
sudo update-grub
```and then 

```
cat /media/sda6/boot/grub/grub.cfg
```make sure that the changes happened. If they did not check the steps and try again. Make sure you are doing this in the directory which you mounted your drive and not the ~ directory of your live cd.

```
grub-install /dev/sda
```to write grub to the MBR

Now, restart, remove the live cd, and hopefully u will see your new entry at the bottom of the list.  what I would do is press the letter 'e' while its highlighted to edit the command before it boots up just to make sure the two UUID's in the command are the same, this is what happened to me and I'm not entirely certain why. Regardless, if the command is there and the uuid's are correct(referring to your new partition) either press ctrl+x to boot if you changed anything or to be safe if you didnt have to press escape to get the the main grub screen and select the added menu entry.

Once ubuntu boots up and your desktop manager is available, the first thing to do is uninstall and reinstall grub2. This is the easiest way to clean up your grub menu and place the new entry at the top.

UNINSTALL  and reinstall GRUB 2

```
sudo apt-get remove grub2

sudo apt-get install grub2

sudo upgrade-from-grub-legacy

sudo chmod -x /etc/grub.d/30_os-prober   


```I make  30_os-prober so that it cant be executed so that grub2 will not add my old ubuntu to the menu. After this upgrade is complete you can remove the old ubuntu partition and make this file executable again (the file is extremely useful when you plug in a hard drive with an os on it and you want it to be in grub). When the 30_os-prober file is executed it searches all drives for OS'. Now:

```
sudo update-grub
cat /boot/grub/grub.cfg

```the only entry you should see is under the 10_linux portion of the grub.cfg file (unless you are dual booting in which case this guide does not help you). Also open up GParted, and make sure the flag for bootable flag and mount point are on (in my case) sda3.

if the information looks to be correct you should:
```

sudo grub-install /dev/sda
```Once again writing your grub to your MBR.

before you reboot make sure that you take a look at the boot.cfg file (dont edit it directly) for errors, gparted (to make sure the partition is bootable and is mounted correctly. 

Restart the computer and hopefully the 1st entry should be new one we have just created. Once logged in to be safe type in the CLI

```
df /
```and 

```
df /boot
```they should both refer to your new partition.

I hope that this guide is informative to some of you and that I helped save you some time. If you have any problems although im not an elite yet I will help with as much as I can and hopefully the real elites will chime in as well. Please dont respond with criticism, only questions, suggestions and/or fixes to the thread.

Thank you!

---

