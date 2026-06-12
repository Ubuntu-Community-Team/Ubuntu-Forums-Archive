---
title: "How do I restore Grub2 after Windows reinstall?"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by kahlil88 on 2010-01-19
My friend recently re-installed WinXP on his laptop, but I'm having trouble getting Grub2 working. I followed a guide online, but when I booted it back up again, I got a Grub prompt instead of a boot menu.

---

### Post by garvinrick4 on 2010-01-19
> **kahlil88 said:**
> My friend recently re-installed WinXP on his laptop, but I'm having trouble getting Grub2 working. I followed a guide online, but when I booted it back up again, I got a Grub prompt instead of a boot menu.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by kahlil88 on 2010-01-20
Yeah, that's what I tried, but I still get a prompt every time. :(

---

### Post by garvinrick4 on 2010-01-20
> **kahlil88 said:**
> Yeah, that's what I tried, but I still get a prompt every time. :(


[http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459](http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459)

Do not give up on it.

---

### Post by garvinrick4 on 2010-01-20
**Using CLI to Boot**

 If the user has problems booting but the menu is available, the easiest method to boot the system is to edit the existing menu. Refer to *[Editing Menus During Boot]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot")*. If GRUB 2 fails to find a usable *grub.cfg* file it should revert to the *grub-rescue* mode. The command line prompt will display *grub-rescue>* and no menu will be displayed. From this command line the user can attempt to manually enter the instructions to boot to a usable system. 
If the command line prompt is not already active press "c" to enter the *Command Line* mode. You will see the GRUB 2 prompt: **grub>** or **grub rescue>** 
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG] If you wish to cancel and start over at any time, *ESC* will remove changes and return the user to the previous menu. 
Use the following two commands to determine the device (drive) and partition of the system you wish to boot. 

[LIST]
[*]  **set**
   
  When **set** is typed without additional entries the command displays the current GRUB 2 settings.
    ** ls **
   
  Run **ls **  to see the devices recognized by GRUB 2. *Example: (hd0) (hd0,1) (hd1,5)*  In this example sda, sda1, sdb5 are recognized.
[/LIST]
 
**Express Boot to the Most Recent Kernel**

 
[LIST]
[*]  Command Summary *:  
   **set root=(hd*X,Y*)**
     

  **linux /boot/vmlinuz root=/dev/sdXY  ro**
     

  **initrd /boot/initrd **
     

  **boot**
  
  Expanded Instructions *:
[LIST]
[*]  Press *ENTER* after completing each line. Some entries will not provide feedback. This is normal.
    If a "file not found" or similar error message is displayed while running these commands, ensure you are using the correct *X,Y* values. The **ls** command can help determine the correct values. Once the *X,Y* values are confirmed run the following command:
[LIST]
[*]  **set prefix=(hdX,Y)/boot/grub**
[/LIST]
 
[/LIST]
  1*. **set root=(hd*X,Y*)** 
   Type with correct *X,Y* results from the *ls* command and press *ENTER*. Remember GRUB 2 counts the first drive as 0, the first partition as 1. Example: If the Ubuntu system is on sda5, enter: *set root=(hd0,5)*
    2*. **linux /vmlinuz root=/dev/sdXY ro**
   Example: *linux /vmlinuz root=/dev/sda3 ro* 
     

  * Wubi users see note.
    3. **initrd /initrd.img**
   Selects the latest initrd image.
    4. **boot**
   Boot to the latest kernel on the selected partition.
    * Wubi users only - substitute these commands in Steps 1 & 2: 
  

[LIST]
[*]  **set root=(loop0)** 
    **linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro**
[/LIST]
  These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (*/boot//grub/grub.cfg*). For problems with booting the main linux kernel, ensure the *search, linux*, and *initrd* lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now correctly point to the correct locations. The user may need to reinstall GRUB 2 (sudo grub-install /dev/sdX). 
 
[/LIST]
 
 
**Boot a Specific Kernel Manually**

 If a GRUB 2 menu is not available for editing during the boot process the command line may still allow booting a specific kernel. If GRUB 2 is looking in the correct location a user may be able to enter all the necessary information on the command line in a single entry. This section will provide a step-by-step guide on how to enter this information. The line will look similar to the following when completed: 

[LIST]
[*]  Command Summary *:  
   **set**
     

  **linux  /boot/vmlinuz-<your version>  root=/dev/sdXY  ro**
     

  **initrd  /boot/initrd-<your version> **
     

  **boot**
  
  Expanded Instructions *:  
  
  Press *ENTER* only after completing each step ("1", "2", "3" and "4").
  
  **Step 1*.** Set the Root Partition
[LIST]
[*]  **set root=(hd*X,Y*)** 
    Use the correct *X,Y* results from the *ls* command and *ENTER*. Remember GRUB 2 counts the first drive as 0, the first partition as 1. For example, if the Ubuntu system is on sda5, enter: *set root=(hd0,5)*
    * For a Wubi install inside Windows, substitute the following command:
[LIST]
[*]  **set root=(loop0)**
[/LIST]
 
[/LIST]
  **Step 2*.** Enter the "linux" line information 
  

[LIST]
[*]  **linux /boot/vmlinuz-<your version> root=/dev/sd*XY* ro **
    * For a Wubi install inside Windows, substitute the following command:
[LIST]
[*]  **root=/dev/sd*XY* loop=/ubuntu/disks/root.disk**
[/LIST]
   Afer typing ***linux /boot/***, the user can TAB to display the available kernels. There is no space character after "/". If no kernels are visible, the address in the "Set Root" section may be incorrect. Enter the correct kernel by typing or using tab completion.
    For the ***root=/dev/*** section use the correct device such as "/dev/sda1", "/dev/sdb5", etc
    Add any options, such as **ro** (read-only), at the end of the line (normally not required). 
     Once all the information on the line is correct it should look similar to the sample below. 
    linux  /boot/vmlinuz-2.6.31-16-generic  root=/dev/sda1  ro
  
   When correctly typed and *ENTER*, if the linux kernel is found, a line similar to the "Linux-bzImage" confirmation line highlighted below will appear.  
  
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.cli.boot.png[/IMG] 
   If a "file not found" or similar error message occurs, either the device/partition/file does not exist or GRUB 2 is not looking at the correct drive, partition and/or folder. Determine the correct location using the **ls** command and then run the following command. Repeat Step 2.
    **set prefix=(hdX,Y)/boot/grub** 
 
[/LIST]
  **Step 3.** Enter the "initrd" line information
  

[LIST]
[*]  **initrd /boot/initrd.img-<your version>**
  
   Afer typing ***initrd /boot/***, the user can TAB to display the available *initrd* images. Do not leave a space after the "/". If no images are visible, the address in the "Set Root" section may be incorrect. Enter the correct image by typing or using tab completion.
    Once all the information on the line is correct it should look similar to the sample below. Press *ENTER*. Look for confirmation. 
    initrd  /initrd-2.6.31-16-generic  root=/dev/sda1  ro
  
  When correctly typed and entered, if the *initrd* image is found, a line similar to the "Initrd"" confirmation line highlighted in the graphic above should appear.  
  
  **Step 4.** Boot
    **boot** 
    Type the command and press *ENTER*.
[/LIST]
 
[/LIST]
 
**Rescue Mode**

 The *rescue* mode is a major GRUB 2 enhancement. If GRUB 2 fails to find a useable *grub.cfg* and is unable to transfer control to a kernel it will drop to a *grub-rescue>* prompt. From this prompt the user can investigate problems, make changes, and retry the boot.  
The *rescue* mode provides fewer commands than the normal GRUB prompt line, but also provides these additional commands: 
  **Command**
    

  **Result**
    dump
   
  Clears memory
    exit
    

  Exit GRUB 2
    normal
    

  Return to the standard "grub>" mode if possible.
  
The following commands can be used in the grub rescue mode:   
  
  
  
  
  
   boot
   cat
   chainloader
   dump
   exit
   freebsd
    freebsd_loadenv
   freebsd_module
   help
   initrd
   insmod
   linux
    lsmod
   multiboot
   normal
   rmmod
   set
   unset
  
  While not all the following commands are necessary to boot to a linux kernel, running all the commands will provide a better chance of success by allowing the user to identify problems before the *boot* command is executed.
  
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG] If additional commands are needed, the user might try loading the normal GRUB 2 module with insmod normal. If successful, help and additional commands will be available.  
  Command Summary *:  
  
  1. **ls** 
    2. **set prefix=(hdX,Y)/boot/grub**  
    3*. **set root=(hdX,Y)** 
    4. **set** 
    5. **ls /boot** 
    6. **insmod /boot/grub/linux.mod** 
    7*. **linux /vmlinuz root=/dev/sdXY ro** 
    8. **initrd /initrd.img** 
    9. **boot** 
  
  * For Wubi installs (within Windows) only substitute these commands in Steps 3 & 7: 
  

[LIST]
[*]  **set root=(loop0)**
    **linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro**
[/LIST]
  Expanded Instructions:  
  
  1. **ls** This will display the known devices and partitions. From this information, the user must determine the device and partition on which the system is installed.
    2. **set prefix=(hdX,Y)/boot/grub**  If incorrect, "no such disk" or "not found" errors will occur later.
    3. **set root=(hdX,Y)** In this command, *X* is the device/drive, starting with 0. *Y* is the partition, starting with 1. Example: (hd0,1) is sda1. (hd2,5) is sdc5. 
    4. **set** Inspect the "prefix=" listing. It should match the root designation in Step 3, in the following format:  *prefix=(hdX,Y)/boot/grub*. 
    5. **ls /boot/** Inspect the contents. The user should see varioius kernels, initrd images and the *grub* folder. If not, use the **ls** command to inspect the device and attempt to find these files and folders. If necessary, set another device as root.
    6. **insmod /boot/grub/linux.mod** Load (*insert module*) the *linux* module. Without this module loaded, the user will receive an "*Unknown command linux*" message when trying to load the kernel.
    7. **linux /vmlinuz root=/dev/sdXY ro** Load the *linux* kernel, substituting the correct designations for "X" and "Y" (example: sda1). The user will see a message showing the kernel has been loaded. (See graphic in the previous section above)
    * Wubi users must use the alternate command presented earlier.
    8. **initrd /initrd.img** Load the *initrd* image. When pressing *ENTER* the user may or may not see a message in the terminal. (See highlighted graphic above) 
    9. **boot** Attempt to boot using the information entered. 
  
  These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (*/boot//grub/grub.cfg*). For problems with booting the main linux kernel, ensure the *search, linux*, and *initrd* lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now point to the correct locations. The user may need to reinstall GRUB 2 using sudo grub-install /dev/sdX.

---

