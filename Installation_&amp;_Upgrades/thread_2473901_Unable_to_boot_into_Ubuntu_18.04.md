---
title: "Unable to boot into Ubuntu 18.04"
date: 2022-04-17
forum: Installation &amp; Upgrades
---

### Post by galzin on 2022-04-17
On an older PC, I was attempting to purge some dependencies which were preventing an upgrade. I ended up with a system that will not boot, though I am unsure both are related because I had not rebooted the system in some time. Among the reasons why I am unsure there is a connection is the fact that boot-repair warned me that my disk was quite full and that could prevent proper booting, so I proceeded to make some room on the disk and use boot-repair, unfortunately that did not solve the problem.

Here is the boot-repair pastebin : [https://pastebin.ubuntu.com/p/Cwj2M3RBS3/](https://pastebin.ubuntu.com/p/Cwj2M3RBS3/)

The symptoms are as follows: I boot and grub does not provide a choice (ubuntu vs advanced options) and eventually I get the startup Ubuntu loading screen. Unfortunately, at the end of this loading process, I get the following error : "fsck error: no such file or directory while executing fsck.ext4 for /dev/sda2. Fsck excited with status code 8". This then takes me to tty1, where I can log on but can only use command line. Note: before using boot-repair, I had actually tried using fsck but all seems good. I used a disk repair option available in gparted via a live Xubuntu disk as well...

Although I've used Ubuntu for a number of years and I know my way around a few command lines, every time I get stuck like this it seems I have to follow guidelines and do some black magic. So I'm hoping someone can help me figure this out? Thanks!

---

### Post by grahammechanical on 2022-04-17
Here is my guess. Ubuntu 18.04 is installed in UEFI mode on a Master Boot Record (MBR) partitioned drive. Grub is installed in the MBR of the drive and is looking for the Grub configuration files on what Grub calls msdos1 and which the rest of us call sda1. The trouble is that the Grub configuration files are in sda2 because sda1 is an EFI System Partition (ESP) with EFI Grub boot files.

Of course it could be the other way around. Ubuntu installed in BIOS mode on a MBR drive and Boot Repair being used from a live session running in UEFI. So, Boot Repair installs EFI boot files. But this would require the creating of an EFI System Partition (sda1).

Regards

---

### Post by yancek on 2022-04-18
Try booting in EFI mode by selecting the line in the BIOS firmware that shows on line 159 of boot repair.
If that fails, go into the BIOS firmware and enable Legacy/CSM booting and try bootiing that way.
Make note of any warning or error messages you get and if both fail, post that information here.
Although it is possible to do an EFI install on an MBR/Legacy drive, the standard is to install Grub code to the MBR and the other Grub files too the system /boot/grub directory.

---

### Post by galzin on 2022-04-18
Hello grahammechanical, your guess sounds reasonable: I installed Ubuntu on what was an OEM Windows Asus laptop (and I accidentally scratched the Windows install in the process). However, if your analysis is correct, how can I solve the problem? Thanks!

As for yancek's answer:
- I will try that as soon as I get back to the laptop and will add a reply below... thanks as well!
- Looking at the boot-repair file, should I be worried at all about the warnings regarding "This MBR does not have a unique signature" or the "GUID Partition Table Header signature is wrong /Primary GPT is invalid, using alternate GPT"?
- regarding your last line: "although it is possible [...], the standard is [...]" : I would be more than happy to correct this if I have not done it the standard way, but I am not sure if I have a non-standard install in the first place. Did I do the non-standard "EFI install on an MBR/Legacy drive"?

---

### Post by galzin on 2022-04-18
I tried following the instructions and booting in EFI mode to the path given in line 159, i.e. booting to sda1/efi/ubuntu/grubx64.efi , but I am not sure how to do this:

[LIST]
[*]My boot options, whether I obtain them from prescing Esc during BIOS or whether I go into my BIOS boot options, are the following:
[LIST]
[*]1. UEFI OS (P0: Samsung SSD 860 EVO 1TB) 
[*]2. Ubuntu ((P0: Samsung SSD 860 EVO 1TB) 
[*]3. Ubuntu (P0: Samsung SSD 860 EVO 1TB) 
[*]4. P0: Samsung SSD 860 EVO 1TB 
[*]5. P1: HL-DT-ST DVDRAM GUAON 
[/LIST]
  
[*]if I select option 4. P0: Samsung SSD 860 EVO 1TB, I get : "error: file '/boot/grub/i386-pc/normal.mod' not found. Entering rescue mode..." followed by a "grub rescue>" prompt. 
[*]if I select option 3. Ubuntu (P0: Samsung SSD 860 EVO 1TB), I get GNU GRUB v2.02 and have choices 1. Ubuntu, 2. Advanced options for Ubuntu and 3. system setup.
[LIST]
[*]if I select Ubuntu and press a bunch of keys in the hope of seeing what's going on in  the background (a combination of Esc and ctrl+alt+F1 through F3 seems to do the trick), the first line I see is "A start job is running for dev-mapper-ubuntu\x2d\x2dvg2x2dswap_1.device" which seems to take a long time and eventually runs the full time limit of 1min30s (fails ?) before moving on to a bunch of lines saying "starting ..." and eventually followed by a green OK "Started ...". I then get that same line again (the first one I mentioned, which timed out) but with a new countdown. This eventually times out again and I get two lines: a red TIME which says "Timed out waiting for dev-mapper-ubuntu\x2d\x2dvg2x2dswap_1.device" and a yellow DEPEND which says "Dependency failed for /dev/mapper/ubuntu--vg-swap_1". After this, nothing happens. 
[*]if I follow the same recipe but without showing the details (without pressing Esc after choosing Ubuntu), I have an approximately 1mn30s wait until I end up with "Ubuntu 18.04.5 LTS nameOfMyLaptop tty1" and a shell login prompt, which I can use to effectively logon, see my files using cd / ls, etc. 
[*]if I select "Advanced options", I am given 6 Ubuntu choices: 1: 5.4.0-70-generic, 2: idem (recovery mode), 3: 5.4.0-67-generic, 4: idem (recovery mode), 5: 4.15.0-140-lowlatency, 6: idem (recovery mode). I assume that what I was testing above is option 1 and go for option 2, i.e. the latest update I have but in recovery mode. Here I see again a bunch of lines zip by, then it says several "Being: .... done" items which seem o be successful until this one:
[LIST]
[*]Begin: Will now check root file system ...fsck from util-linux 2.31.1 
[*]fsck: error 2 (No such file or directory) while executing fsck.ext4 for /dev/sda2 
[*]fsck exited with status code 8 
[*]done. 
[*]Warning: File system check failed but did not detect errors

finally, a few more lines before I read "Welcome to Ubuntu 18.04 LTS!". This is then followed by lines similar to what I tried previously, with a bunch of green OK lines and the one saying "dev-mapper-ubuntu\x2d\x2dvg2x2dswap_1.device" going the full 1min30s before timing out. This ends with the red TIME and yellow DEPEND as before, and I now have an extra yellow DEPEND: Dependency failed for swap. After this, a few more green OK lines followed by a choice menu for recovery tools (resume, clean dpkg, fsck, grub, network, root, system-summary). Clicking resume shows me a bunch more green OK lines with one red "FAILED Failed to start Raise network interfaces", which maybe was shown before but I could have missed it. Finally , I end up with the same tty1 prompt as the previous test. 
[/LIST]
  
[*]if in "Advanced options" I select option 3: 5.4.0-67-generic, I get similar stuff but the file system check seems to do better. It says:
[LIST]
[*]Begin: Will now check root file system ...fsck from util-linux 2.31.1 
[*][/sbin/fsck.ext4 (1) -- /dev/sda2] fsck.ext4 -a -C0 /dev/sda2 
[*]/dev/sda2: recovering journal 
[*]/dev/sda2: clean 3246476/60956672 files, 201459224/243808256 blocks 
[*]done.

it proceeds with a bunch of green OK lines, then the menu choice, then more OK lines but ends up with the same job as previously timing out. I end up again with a tty1 login prompt. 
[/LIST]
   
[/LIST]
  
[*]if I select option 2. Ubuntu ((P0: Samsung SSD 860 EVO 1TB) or option 1. UEFI OS (P0: Samsung SSD 860 EVO 1TB), I try the same recovery modes as above for option 2 and see no visible difference between them or with the above option 3. I still get an fsck error when booting 5.4.0-70, and I still get a success for fsck when I boot 5.4.0-67. 
[/LIST]

So all in all, I do not know how to specifically start on sda1/efi/ubuntu/grubx64.efi, and none of the options I can access using a combination of BIOS booting choices and GRUB recovery modes seem to do the trick :( Thanks for your help!

PS: all this was done using the "launch CSM" option enabled in BIOS. disabling CSM reduces the number of options I have in BIOS to options 1, 2 and 3 above but does not make my life any better, i.e. I seem to get the exact same results. Also please note that on my laptop this option must be enabled for booting on live USB keys and such...

---

### Post by yancek on 2022-04-22
The Boot Options you show in your last post are not specific enough to know which to select.  On my laptop, these entries are more detailed and the file mentioned will show so I guess all you can do is try options 2 and 3 which show ubuntu in the title which you seem to have done. 

The lines including 'dev-mapper' indicates you have done an LVM install which I have never done and am not familiar with.  My understanding of LVM is that it needs a separate /boot partition which I don't see.  I'm not sure about that as I don't use LVM.  

Was your system booting UEFI before you tried the updates?  

Line 298 in the boot repair you posted above shows the UUID for the Ubuntu system partition (sda2).  Check the /etc/fstab file, the grub.cfg files on the EFI and system partitions to see if they are the same.  If that isn't the problem, I'm not sure what it would be.  Good luck.

---

### Post by galzin on 2022-04-23
Thanks yancek! The fstab file looks surprising since it does not reference the UUID you mentionned on line 298, so I think this might give someone new clues. So I am copying the fstab file here manually since I  cannot use the computer in question, will try to avoid typos. (I am  skipping the commented lines at the top of the file.)[INDENT]```

# <file system>    <mount point>    <type>    <options>    <dumpt>    <pass>
/dev/mapper/ubuntu--vg-root    /    ext4    errors=remount-ro    0    1
# /boot/efi was on /dev/sda1 during installation
#UUID=607E-6E8F    /boot/efi    vfat    umask=0077    0    1
/dev/mapper/ubuntu--vg-swap_1    none    swap    sw    0    0
#UUID=607E-6E8F    /boot/efi    vfat    defaults    0    1
#UUID=607E-6E8F    /boot/efi    vfat    defaults    0    1
#UUID=607E-6E8F    /boot/efi    vfat    defaults    0    1
#UUID=607E-6E8F    /boot/efi    vfat    defaults    0    1
UUID=607E-6E8F    /boot/efi    vfat    defaults    0    1

```
[/INDENT]

My disk UUIDs are:[INDENT]```


```[/INDENT]
```
sda                                                                                                              
&#9500;&#9472;sda1 vfat     607E-6E8F                                                                                        
&#9500;&#9472;sda2 ext4     a504996e-313f-4ebb-bd6c-f88c7795dfbe                                                             
&#9492;&#9472;sda3 swap     9a555757-d93c-475a-a2a7-89f421073114                                                            
```[INDENT]
[/INDENT]


My feeling is therefore the following: this computer might have gone through 2 grubs (this was a long time ago, I do not remember how it was setup), maybe starting first on the origina; "windows" partition which was scrapped and then moving on to further booting instructions on sda2?

As for the grub.cfg file, it is wa too long for me to rewrite here, but let me focus on what seems relevant:
[LIST]
[*]after "function load-video {...}", I have on line 62:
```

if [ x$feature_default_font_path = xy ] ; then
    font=unicode
else
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ] ; then
        search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 a504996e-313f-4ebb-bd6c-f88c7795dfbe
    else
        search --no-floppy --fs-uuid --set=root a504996e-313f-4ebb-bd6c-f88c7795dfbe
    fi
    font="/usr/share/grub/unicode.pf2"
fi

```
[*]after "export linux_gfx_mode", line 131:
```

menuentry 'Ubuntu' --class ubuntu --class gnu-linux class os $menuentry_id_option 'gnulinux-simple-a504996e-313f-4ebb-bd6c-f88c7795dfbe' {
    ....
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ] ; then
         search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2  --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a504996e-313f-4ebb-bd6c-f88c7795dfbe
    else
        search --no-floppy --fs-uuid --set=root a504996e-313f-4ebb-bd6c-f88c7795dfbe
    fi
    linux   /boot/vmlinuz-5.4.0-70-generic root=UUID=a504996e-313f-4ebb-bd6c-f88c7795dfbe ro quite splash $vt_handoff
    initrd  /boot/initrd.img-5.4.0-70-generic
}

```
[*]I then have a bunch of other options corresponding to the menu choices I described in a previous post higher up in this thread. These look like variations of the above but always seem to reference the correct UUID. (happy to copy another specific section here if that helps, just let me know... but given that the first option is selected by default and used to boot, I think focusing on just this info is probably enough.)
[/LIST]

One last piece of info which could help: if I boot using a live USB key and launch gparted, I can see that /dev/sda1 (fat32) has the "boot" flag but that /dev/sda2 (ext4) does not have the "boot" flag. Should it have? Would that be enough to fix things? Or does this give a clue to another element of this partitioning info which is incoherent?

---

### Post by galzin on 2022-04-24
Sad news: after about a week of trying all I could think of and going to various troubleshooting sites / forums for help andideas, I was forced to scrap my install and start afresh in order to get the computer finally running. Lost a bunch of installs / settings / personalizations, but was able to retrieve the data by changing my partitioning scheme. To do this, I was able to cleanup to make my disk about 50% empty, then I reduced the partition and created a new one using GParted from a Ubuntu Live USB key, and finally moved my data to that second partition. I then did a fresh install on the first original partition, and finally followed the following instructions for moving my home folder to the second partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This therefore closes this topic, unfortunately with an unsuccessful outcome, sorry for others in this situation.

---

