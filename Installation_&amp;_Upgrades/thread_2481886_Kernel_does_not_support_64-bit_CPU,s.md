---
title: "Kernel does not support 64-bit CPU,s"
date: 2022-12-12
forum: Installation &amp; Upgrades
---

### Post by s-laugharne on 2022-12-12
Last night I installed ubuntu 22.04 onto my pc and chose the option  to have 22.04 to run alongside my older 18.04.6 which all my documents  and pictures are stored on as i didn't want to lose them, now when I  boot up the pc it gives the option to load 18.04 but when I click on it,  it says error: kernel doesn't support 64-bit cpu,s, error you need to  load the kernel first, press any key to continue. Please could anyone help me with this as I don't want to lose all my  documents. Thank you Kind regards Steve

---

### Post by The Cog on 2022-12-12
Welcome to the forum.
You have strayed into an area of the boot process I know nothing about. However, if 22.04 is working for you, you can copy the data from the old partition. I suggest copying it to an external USB drive or stick in addition to copying the data to your new home, just so you have a backup. 

You don't say what the partitions are, so I will use sdax for the old partition id - replace it with the real one. I would go about it this way:
```
# Boot 22.04 first
# Use lsblk to find out what the old 18.04 partition is known as now:
lsblk -fm
# Make a mount point for mounting the old partition into, then mount it:
sudo mkdir /mnt/sdax                               # This is the directory the partition content will appear in
sudo mount /dev/sdax /mnt/sdax             # This command does the mount, making the partition content appear
```
Now you should be able to use a file manager and look into /mnt/sdax/home/your-name and find your data. Copy it to the new home.
If you are concerned about application settings etc., they are largely stored in hidden directories (their names start with a dot). It is probably worth copying the whole /mnt/sdax/home/your-name directory to make sure you capture all the settings files and folders.

---

### Post by s-laugharne on 2022-12-12
Hello
Thank you so much for your prompt reply, this is what comes up when I first boot up

Ubuntu
Advanced options for Ubuntu
Memory Test  (memtest86+.elf)
Memory Test  (memtest86+.bin, serial console)
Ubuntu 18.04.6 LTS (18.04)  (on /dev/sdb1)
Advanced options for Ubuntu 18.04.6 LTS (18.04)  (on /dev/sdb1)

---

### Post by s-laugharne on 2022-12-12
Just hope I don't lose any data by carrying out some wrong moves, as I'm a novice in the area of commands in the Terminal

---

### Post by The Cog on 2022-12-12
The top one "Ubuntu" will be the new 20.04. 
If you really don't want to use the command line, you can probably mount the old partition by clicking it in the file manager, where it will probably mount under /media/yourname/something, and again, you should be able to see all your files under /media/yourname/something/home/yourname.

---

### Post by grahammechanical on 2022-12-12
It should be possible to use 20.04 + File manager to access the 18.04 partition and the folders on it. Open Files and select Other Locations. Then select the partition/Volume that corresponds to the 18.04 partition. Then select the Home folder and then your username folder and you should see before the standard folder layout of the Ubuntu 18.04 desktop. You should now be able to copy/paste into your 20.04 folders.

Regards

---

### Post by s-laugharne on 2022-12-12
Thank you all very much for taking the time to help with my question.
I thought I'd have to boot into my old Ubuntu 18.04.6 system separately from my new 22.04 Ubuntu, but no its not the case.
I have found the file containing all my data on my new 22.04 system, its listed as Parent folder  /media/steven/then a long list of letters and numbers, and it amounts to 350GB containing all my data, well pleased.
Thanks again for your help
Best wishes
Steve

---

### Post by mIk3_08 on 2022-12-14
> **s-laugharne said:**
> Thank you all very much for taking the time to help with my question.
I thought I'd have to boot into my old Ubuntu 18.04.6 system separately from my new 22.04 Ubuntu, but no its not the case.
I have found the file containing all my data on my new 22.04 system, its listed as Parent folder  /media/steven/then a long list of letters and numbers, and it amounts to 350GB containing all my data, well pleased.
Thanks again for your help
Best wishes
Steve
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

