---
title: "triple boot grub2 probs."
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by dan1973 on 2009-11-14
Hello all, hope someone can help.

Am running Ubuntu 9.10 (enjoying it in the main) and Windows 7 in a dual boot system.

Recently added windows XP to the mix, reinstalled grub2 to the MBR where it had no trouble detecting my Ubuntu and Windows 7 partitions but has not picked up the XP.

Now, i am tempted to get stuck in there and fiddle with things, but it has been a long day and I would hate to make things worse after just getting my prior two partitions back up and running, so I therefore turn to you all in the hopes of an elegant and simple solution.

Many thanks in advance,

Dan

---

### Post by darkod on 2009-11-14
How about the following:
Since you have a working Win7 go in there and check your XP partition (drive) whether boot.ini is there. You might need to enable seeing hidden and system files in Win7 for that.
If it's there, it should be the bootloader for XP.
Even though grub should have picked it up, just add manual entry in grub for your XP because you know the exact partition it's on.

---

### Post by dan1973 on 2009-11-14
I mounted the xp partition and searched for boot.ini and it wasn't found - not really sure wherabouts it normally resides.

Is it the case that i actually need to boot into windows 7 to see it?

Should mention that my windows xp was working just fine before reinstalling grub2 - it booted up no problem.

---

### Post by darkod on 2009-11-14
It would be in the root of the partition.
Another option, not very likely. Sometimes during installation Win7 creates a small 100MB boot partition. XP might have put the boot.ini there. Check that partition too, if it exists.

If not, mount again the XP partition and check do you have ntldr and ntdetect files in it. Those three files with boot.ini make the loading process of XP.

If you do have these two files but just boot.ini is missing, here is microsoft article how to write your own boot.ini but it is best to write it with notepad in win7, not with gedit in ubuntu:
[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)
Among the steps there is one step to create boot.ini. Ignore the rest. Of course, adjust the content of boot.ini with information about the partition your XP is on.

PS. Ctrl+H hides/unhides folders in ubuntu. You might check with mounted XP partition maybe it will allow you to see hidden files, assuming boot.ini is hidden in ubuntu too. Maybe you didn't see it if it hides it too like windows.

---

### Post by oldfred on 2009-11-14
I know that if you install Win7 with a XP install it combines the boot into one, so you can only boot XP and it gives you the choice of xp or Win7. I do not know if in the reverse it is true also but I bet it is as the windows boot loader only can choose which to boot from one of the windows partitions. 

When windows combines boot it moves some files that prevent separate boot of each windows. If you uninstall the windows with the boot you have to repair the other one to get it working again.

A work around was to turn off the boot flag before installing the second windows so it would not see the first install. You then could not boot directly from windows into either windows but then could use grub to boot directly into each.

---

### Post by dan1973 on 2009-11-14
ok, the problem has indeed changed somewhat.

With the grub loader i selected the windows 7 option and to my surprise i find myself back in windows xp.

So at present i have karmic and XP functioning albeit under a windows 7 heading. How can this be straightened out?

---

### Post by oldfred on 2009-11-14
Have you rerun:
sudo update-grub

If it is separately bootable it should find it. 
Next choice is to add manual entries into 40_custom. You can copy your xp entry from grub.cfg in twice and edit one to be for your Win7. Does you Win7 have a separate boot partition of about 100mb? If so that is the partition to boot to. If you have to add manual entries you can turn off the osprober in /etc/default/grub to prevent duplicate xp entries.

sudo gedit /etc/grub.d/40_custom

/etc/default/grub 
GRUB_DISABLE_OS_PROBER=true

---

### Post by dan1973 on 2009-11-14
Have tried the grub update but it does appear as if the two windows have 'merged' into one as far as grub is concerned.

will try some editing of the files that grub2 uses for the config and report back on any sucess/ faliure.

---

### Post by dan1973 on 2009-11-14
some extra info which may be of help:
[PHP]============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,249,469    10,249,407  82 Linux swap / Solaris
/dev/sda2    *     10,249,470   121,820,894   111,571,425   7 HPFS/NTFS
/dev/sda3         121,820,895   205,407,089    83,586,195  83 Linux
/dev/sda4         205,407,090   234,420,479    29,013,390   f W95 Ext d (LBA)
/dev/sda5         205,407,153   234,420,479    29,013,327   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="59c57d12-d513-4226-b9cd-336683068a98" TYPE="swap" 
/dev/sda2: UUID="9A4CE1F54CE1CC57" TYPE="ntfs" 
/dev/sda3: UUID="771a31a7-6bed-41df-a692-331442671a3b" TYPE="ext4" 
/dev/sda5: UUID="5800227F0022646A" TYPE="ntfs" [/PHP]

---

### Post by darkod on 2009-11-14
Yeap, boot files from both windows OSs are on the same sda2.

You said title Windows 7 is booting XP. Change that title in Windows XP.
Create new title for Windows 7, just copy the XP one, and instead of the standard command chainloder +1 put chainloader /bootmgr
I have used that with Win7 and it works. Use the exact filename and it should work with both boot.ini and bootmgr on sda2.

Like suggested by oldfred, disable the os prober and put your own custom entry for Windows 7 in 40_custom file.

---

### Post by dan1973 on 2009-11-14
This sounds like an answer, unfortunately i don't yet have sufficient experience to follow your instructions.

Could you explain the steps a little clearer please. 

I am trying, honest!

---

### Post by darkod on 2009-11-14
Hold on, let me reboot in ubuntu so I can give you exact filenames. I'm in windows now. be right back.

---

### Post by 23dornot23d on 2009-11-14
Some more info I found on this worth the read is here too ......

[http://www.linuxquestions.org/questions/linux-general-1/what-is-the-best-way-to-multi-boot-several-linux-distros-765169/](http://www.linuxquestions.org/questions/linux-general-1/what-is-the-best-way-to-multi-boot-several-linux-distros-765169/)

But this is just for info ........... and it explains quite a lot of what you need to know ..... it might save some time .....

but continue ..... here if what you need to know is not shown  ....... 

it  will be good to see ....... 

Here is another interesting link ...... 

[http://ubuntuforums.org/showthread.php?p=8224270](http://ubuntuforums.org/showthread.php?p=8224270)

because I at the moment run 5 different OS's ..... 

but some others OS's  I have on my USB now fail to boot .....

so I too am quite interested in knowing why .......

( and I would like to know that GRUB2 will be ok and not leave me with less than I have now )

---

### Post by darkod on 2009-11-14
As oldfred suggested, better disable os prober if entering manual entries.
Step 1:
In terminal (Applications -> Accessories -> Terminal) enter the command:
sudo gedit /etc/default/grub
At the bottom add the line he suggested:
GRUB_DISABLE_OS_PROBER=true
Save the file and close the window.

Step 2:
In the terminal execute:
sudo gedit /etc/grub.d/40_custom
At the end add:
title Windows 7
makeactive (not sure you can try with and without it)
chainloader /bootmgr

Then leave one empty line and add also:
title Windows XP
makeactive (same as above)
chainloader +1

Save and close the file.
In the terminal execute:
sudo update-grub

That should be it. Reboot and check if the grub menu will show the entries and if they work.
At start you might want to add (new) next to the titles of both new entries you create so you know which ones are from you. If you have more than 2 windows entries we will sort it later, the first step is for this to work.
Try it.

---

### Post by dan1973 on 2009-11-14
Have to go to bed, it's already 1 in the morning and my eyes are practically bleeding.

Thanks all for your help, i will be back trying to solve this tomorrow.

much love,

Dan

---

### Post by dan1973 on 2009-11-14
have not gone yet,

when writing the entries to 40_custom do i not need to specify any more than you wrote - no hard disc id's or anything etc?

---

### Post by dan1973 on 2009-11-14
really must go now,

need sleep....

...
.

---

### Post by oldfred on 2009-11-14
Darkod - are you sure those are grub2 commands? I thought they all had the {} like below:

### BEGIN /etc/grub.d/21_winxp ###
menuentry "Windows XP" {
       insmod ntfs
       set root=(hd0,[COLOR=DarkRed]0[/COLOR])
       search --no-floppy --fs-uuid --set[COLOR=DarkRed] EC0CEE940CEE595A[/COLOR]
       chainloader +1
}

### END /etc/grub.d/21_winxp ###

I do believe you can leave out the entire search line and possibly the isnmod ntfs if you are just chainbooting into the partition.

I also found they did away with the makeactive command and it is now 
   #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

I am suprised the XP boots as it is in the extended partition and not the Win7 booting.

Dan - because your winXP is in an extended partition you cannot uninstall win7 and still be able to boot XP. Windows will not boot from and extended partition unless you are going thru the primary partition of windows.
Question - Why XP if you have win7? Ithought it had a compatibility mode that give it XP capabilities for those programs that do not run correctly under win7. I only have XP and have no plans of ever buying another windows, so I am no expert on Win7.

---

### Post by darkod on 2009-11-15
I owe you big apology. In my post with the instruction I forgot the most important command. :( Too late and too tired. :)
When entering the titles for windows after the line "title" for both 7 and XP there should be:
rootnoverify (hd0,1)

That will point it to the correct partition, first hard drive, second partition. Sorry about that.

PS. oldfred is right. All of the above seems to work only on grub not on the new grub2. Sorry. Have to dig little deeper to find more info and the correct syntax.

---

### Post by darkod on 2009-11-15
I think I found it, adding manual windows entries. But the value of UUID for the partition is needed.

Open terminal, run:
blkid

and post the information here. If you can't post it, just write down the UUID value for your windows ntfs partition, /dev/sda2. You will need that number.

Once you have it, in terminal run:
sudo gedit /etc/grub.d/40_custom

At the end add:

menuentry "Windows 7 (new)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader /bootmgr
}

menuentry "Windows XP (new)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

In both entries you will have to replace the CFFC... value with the UUID you found earlier, that's the UUID value.

Save and close that file.

Then in terminal run:
sudo chmod -x /etc/grub.d/30_os-prober

That will disable the automatic os prober which is not correctly finding your windows anyway.
At the end you only need to run:
sudo update-grub

And that should be it.

If there are errors and someone has more experience with this please jump in. :)

PS. Because your boot files for both windows OSs are in the same place the above might not work ideally first time but we can adjust the chainloader values after we see the result. So don't get disappointed. :) See if the above can work and check if it will boot both windows OSs and Ubuntu correctly. If there is error with any, let us know.

---

### Post by dan1973 on 2009-11-15
I am sorry darkod and old fred,

I started from scratch again. wiped the hard drive and installed a simple win 7 and ubuntu dual boot. Both working fine.

The reason for the XP experiment was that I have an old IBM thinkpad T43 on the way with limited RAM and graphics card. My XP disk was hitherto untested and me being me, I just couldn't wait until the 'new' machine arrived to test it and re-acquaint myself with XP. Very nice and familiar, will install XP and ubuntu on the new machine.

Thank you for your patience. I will endeavour to try to comprehend this new grub - and i'm sure our paths will cross in the future when I inevitably **** up again.

Take care,

---

### Post by oldfred on 2009-11-15
No problem Dan, sometimes we spend hours trying to fix something when a reinstall is the best solution. Other times a simple one line fix can save a total reinstall and potential loss of data.

I was curious if we could get both windows to boot directly. I am not sure I have seen it work. One work around I saw was to turn off the boot flag and the second windows install will not see the first. From windows you can only boot the last install but from grub you can directly boot both.

Glad you got things working but why not Ubuntu or one of the light weight linux versions for the old machine?

---

