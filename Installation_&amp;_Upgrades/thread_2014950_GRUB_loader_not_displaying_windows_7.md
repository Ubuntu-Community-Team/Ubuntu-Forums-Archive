---
title: "GRUB loader not displaying windows 7"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by SYNech0 on 2012-07-02
Hi Ubuntu Forums    I am relatively new to linux, i have a decent amount of programming experience and knowledge of tcp/ip, so i decided it would be a good idea to install backtrack 5 r2 on my spare hdd. I had played around a little with ubuntu before and inseeing backtrack is based off a version of ubuntu i thought that i wouldn't have any problems.     After installing  backtrack on my second hdd and rebooting i was met with a blank screen and flashing cursor. I trawled the forums to find a solution. I tried multiple things to try and fix it. The latest attempt at fixing it was to run boot disk repairer off a usb. After doing this Windows 7 has disappeared from my grub loader all together.     I have to 500gb hdd's and i know that my windows data is still intact because i can access the drive from backtrack. I am running windows 7 64bit and backtrack 5 r2 64bit. I have attempted to alter the 40_custom file in /etc/grub.d/ however i either did something wrong or that didn't work.    Here is what i get when i type fdisk -l:     root@bt:~# fdisk -l    Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x00062cbd     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1          13      102400    7  HPFS/NTFS Partition 1 does not end on cylinder boundary. /dev/sda2              13       60802   488282112    7  HPFS/NTFS  Disk /dev/sdb: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x000c92fe     Device Boot      Start         End      Blocks   Id  System /dev/sdb1               1       58578   470524928   83  Linux /dev/sdb2           58578       60802    17859585    5  Extended /dev/sdb5           58578       60802    17859584   82  Linux swap / Solaris       Thanks for reading :), any help would be appreciated greatly.

---

### Post by SYNech0 on 2012-07-02
Holy crap, what happened to the whitespace?

---

### Post by ajgreeny on 2012-07-02
> **SYNech0 said:**
> Holy crap, what happened to the whitespace?
Yes, a paragraph or two would have made it much easier to read, but assuming I didn't miss this in the OP, have you tried ```
sudo update-grub
```to try and add windows back in to the menu?

---

### Post by oldfred on 2012-07-02
If ajgreeny's suggestion does not work, post BootInfo link:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

What did you use to post, normally copy & paste keeps line endings. Using code tags also help preserve formating on longer output from terminal. From message, you can highlight text and click the # in edit panel to get code tags.

---

### Post by SYNech0 on 2012-07-03
ajGreeny

I did try that, after altering the 40_custom file i ran update-grub2.

I ran update-grub just to make sure:

root@bt:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.6
Found initrd image: /boot/initrd.img-3.2.6
Found memtest86+ image: /boot/memtest86+.bin
done


oldfred

One issue i had with bootloader is the livecd didn't appear to recognize my network card, as when bootloader needed to connect to the internet, i couldn't detect any networks. I played around with it a bit and couldn't find a way to fix this.

Does the Create bootinfo need to be run from within the bootlader?

Also i have no idea what happened to the formatting of the original post. I typed everything into the vbulletin editor. I copy and pasted the code.
The formatting disappeared when i submitted the post.

---

### Post by oldfred on 2012-07-03
Almost everything now needs a working Internet connection. Do you have a wired connection as that almost always works?

Wireless seems to have so many different drivers that the wired connection has to be used so you can download a wireless. A few wireless have to have major work arounds.

You can download the Bootinfo script and copy it to a flash drive and then use that to copy to & run from LIveCD or LiveUSB.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by SYNech0 on 2012-07-04
I connected to my router via ethernet and the software updated itself and i got no errors. It said it ran successfully, but i still cant find windows on the grub menu.
 
Here is the bootinfo url: [http://paste.ubuntu.com/1074350/](http://paste.ubuntu.com/1074350/)
 
Also i did boot into sdb first. Tried sda afterwards just to make sure. Both have grub.

---

### Post by YannBuntu on 2012-07-04
Hello
some Windows boot files are missing. You can try this: run Boot-Repair, update it, click "Advanced options", go tot the "Other options" tab, tick the "beta" checkbox, apply. Indicate the new URL. Reboot, there should be a Windows entry in the GRUB menu. Indicate if Windows can boot or not.

---

### Post by oldfred on 2012-07-04
Yann keeps making improvements to the Boot-Repair, so I am not sure what improvements he has done now that may fix your issue.

The issue seems to be the Windows 100MB boot/repair partition. It normally has two of the three essential boot files and the Windows repair console. Partition table still says it is NTFS, but script could not open it for reading. That would be the same issue with grub2's os-prober not being able to open it and see the boot files. 

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Often Linux's NTFS driver will not open a NTFS partition if the chkdsk flag is set or it needs chkdsk. That is to prevent possible further damage that chkdsk then might not be able to fix. 

But you can also add the Windows boot files bootmgr & /boot/BCD that are missing to the main Windows install and also boot. Windows has it as a separate boot partition so you can encrypt the main install as the boot files could not be encrypted.

---

### Post by cutterjohn on 2012-07-04
> **oldfred said:**
> If ajgreeny's suggestion does not work, post BootInfo link:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

What did you use to post, normally copy & paste keeps line endings. Using code tags also help preserve formating on longer output from terminal. From message, you can highlight text and click the # in edit panel to get code tags.This worked for me.  (Asus p9x79/gtx 670 FTW/3930k/16GB/1TB WD caviar black 6G/UEFI new build)

I originally did a manual(well custom) install from the base DVD image, but got no grub.  I just figured that the install scripts were borked after seeing reports of problems with UEFI after a brief search and decided to try "auto"-install later.

(I had just finished with the initial hw build and had just installed win7 pro x64, so I still had some tweaking to do on the hw yet -> just left Ubuntu alone until I was sure that everything was nice and stable/cool(just better diagnostic/monitoring tools available for windows).)

So, some days later I do the default install(after deleting my "custom" partitions leaving them blank/unformatted) and let it do whatever it would default to(kind of a mistake, waste a good chunk of space) and still got no grub.

-> live install, get boot-repair, run -> upgrade/reinstall grub and bingo works now.

Seems like 12.04 has some half baked install scripts, which is kind of scarey for something that's supposed to be LTS...

(On a side note is so MUCH nicer being back with nVidia GPUs and drivers that just aren't crap of various levels(AMD I'm looking at you and the living hell of 4y of garbage drivers with ancient bugs never being corrected(even the windows drivers weren't so hot)).)

---

### Post by SYNech0 on 2012-07-07
> **YannBuntu said:**
> Hello
some Windows boot files are missing. You can try this: run Boot-Repair, update it, click "Advanced options", go tot the "Other options" tab, tick the "beta" checkbox, apply. Indicate the new URL. Reboot, there should be a Windows entry in the GRUB menu. Indicate if Windows can boot or not.
 
Hi yann
 
Thanks for your support, this brought windows up in the GRUB menu, however when i try and boot from it i seem to get an error. I cant read it because it looks like it is in an eastern european language. I can only make out the last line that says press enter to continue and then it sends me back to my bios flash screen. Is there a way i can download the files to for the boot partition and just copy them over or not?

---

### Post by SYNech0 on 2012-07-07
Ok i've just worked out its in polish. I have no way of copy and pasting the whole thing. The information given with the error roughly translates to:
 
Unable to run startup items, because the required device is not available.
 
I also got something that said, "Stan: 0x000000e", which i think means that there is a missing or corrupt winload.exe.
 
Again is there any way i can download winload.exe and paste it into the correct partition.
 
I do not have my windows repair disk, which means that i cannot run windows repair. If i got a friend with a windows machine to create a repair disk would i be able to use that, or are they created specific for each machine.

---

### Post by oldfred on 2012-07-07
Repair disk only needs to be either 32bit or 64bit and Vista or 7. But I have used a Windows 7 repairUSB to run chkdsk and replace PBR on my XP install.

Best to find a friend. We used to have a free site, but they now charge $10 for a repairCD that you can make from any Windows 7.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by SYNech0 on 2012-07-08
HI

Sorry, i made 2 posts the other day and i just checked and it looked like they didnt go through. 

The jist of it was that ticking the beta box made windows appear in the GRUB menu, however i got an error booting into windows. The error was in polish, i translated as much as i could. It basically said that winload.exe wasn't was either missing or corrupt. 

Firstly it looks like i should now head over to the windows forums to try and fix it. And secondly thank you for all of your help. :)

---

### Post by YannBuntu on 2012-07-09
For information, I think you can download a Windows7 Recovery CD for free here: [http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/](http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/)

---

