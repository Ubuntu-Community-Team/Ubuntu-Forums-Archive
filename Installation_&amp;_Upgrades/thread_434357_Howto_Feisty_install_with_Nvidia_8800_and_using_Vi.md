---
title: "Howto: Feisty install with Nvidia 8800 and using Vista Bootloader (EasyBCD 1.52)"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Blackforge on 2007-05-05
The following Howto was done using this hardware: 
Intel E6600
Asus P5N32-E SLI Plus (Nvidia 650i chipset) 
XFX 8800GTS 640MB

I apologize as most of this is being done from memory.  Please let me know if there are any errors and I'll edit this.

Install Vista now or later, doesn't matter just as long as you do not overwrite the Vista BCD MBR.

Download and burn Feisty LiveCD (I used the AM64 version, but it shouldn't matter).


[COLOR="Blue"]----- Beginning of optional Nvidia 8800 section (Only useful if you have a video card with this chipset) :[/COLOR]

Boot the CD.  You will probably have to specify a resolution using F4 so the screen doesn't black out.  Just select something that your monitor supports (I used 1280x1024x32).

Once the CD boots up, your screen will go scramble/corrupt as the nv drivers tries to load.  At this time while Ubuntu is loading with your scrambled screen you can switch to a shell prompt by going to Ctrl-Alt-F1.  Now run:

sudo nano /etc/X11/xorg.conf

Find the &#8220;nv&#8221; within the xorg.conf and change it to &#8220;vesa&#8221;.

```

Section "Device"

    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"

    Driver         "vesa"

```

Save this with a Write Out (Ctrl-O) and Exit (Ctrl-X).

We want Ubuntu to fully load other wise you may have problems when we restart the X server so give it a few minutes.  You can check on it by switching back by using Ctrl-Alt-F7 until you see Applications Places System in the window.  If you have/can hear sound with your install then you should hear the long music when Ubuntu logs in to know when it is done.  

If you get any nautilus or gnome errors after you do a Ctrl-Alt-Backspace, switch back to the shell (Ctrl-Alt-F1) and run this:

```
sudo pgrep gnome | xargs sudo kill -9
```

This searches for all processes that contain &#8220;gnome&#8221; and kills them one at a time.  At this point you can switch back to X Windows (Ctrl-Alt-F7) and do restart X (Ctrl-Alt-Backspace).  Everything should load normally at this point.

[COLOR="Lime"]-------- EasyBCD users should  also take note of this section[/COLOR]

You can now begin the Ubuntu install.  This is going to vary for everyone.  I like to do all my installs by partitioning manually so I can get the disk/partition information prior to everything, but everyone is different. 

When it gets to screen where it is about to install you will note that it wants to install GRUB to hd0.  Also from this point you can see what device is being used for the install.  We want to change the GRUB location, so click on the advanced button for the Bootloader.  This needs to be changed from (hd0) to the partition where your ext3 is going to.  In my case /dev/sdb6.  You can use the GRUB partitioning/numbering if you know it or want to find it, but the device ids work fine too.  So type in:

```
/dev/sd??
```

With ?? being the appropriate device id for your install.  If you don't know what the device id, go to a terminal and type in:

```
sudo fdisk -l
```

You should see the ext3 partition.

When you click OK you will see that it does NOT change on the summary screen.  This okay, as it really has been changed.  Begin the install.  Once it finishes, you need to tell it you want to continue using the LiveCD.

[COLOR="DarkOrange"]-------- EasyBCD users just interested in booting can now skip to[/COLOR] [COLOR="Red"]Vista Bootloader[/COLOR] [COLOR="DarkOrange"]section [/COLOR]

[INDENT]If you have an Nvidia 8800 based card, now we want to head off some problems.  Go to Applications -> Accessories -> Terminal.

We need to mount the Ubuntu system we just installed.

Substitute the &#8220;??&#8221; to the appropriate device id.  If you need this information again you can run sudo fdisk -l to get a list of your partitions and look for the ext3 partition:

```

sudo mount -t ext3 /dev/sd?? /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash

```

Since we are now &#8220;root&#8221; on this file system you can specify sudo if you want for the following commands, but it is not necessary.  We need to edit the menu.lst for GRUB to prevent the Black Screen o' death:

```
gedit /boot/grub/menu.lst
```

Append vga=795 to the kernel line under &#8220;title Ubuntu, kernel 2.6.20-15-generic&#8221; so it looks something like this.  I changed the UUID as it will be different for everyone:

```

title Ubuntu, kernel 2.6.20-15-generic
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1234-5678-0123456 ro quiet splash vga=795

```

Save this and quit gedit.[/INDENT]

[COLOR="Blue"]---- End of Optional Nvidia 8800 section[/COLOR]

[COLOR="Red"]---- Beginning of Vista Bootloader section[/COLOR]

Now reboot into Vista.

Now we want to find out what Vista sees the numbers for the disks and partitions in order to be able to use it to boot Ubuntu using Vista's BCD. 

In Vista run a command prompt as administrator  (Right-click on Command Prompt in the Programs list and select &#8220;Run as Administrator&#8221;).

Go to the command prompt and type in DISKPART (depending on how many disks you have it may take a little bit for it to scan all your disks and partitions). 

Type:

```
list disk
```

If you have different disk sizes it should be easy to figure out which one is holding your Linux Partition. If you figure it out just remember the number next to it, as we'll be using it to configure EasyBCD. You can also figure out which disk number Vista is using through Computer Management, but we still need to look up the Partition number through DISKPART.  So if it makes it easier, use it and skip to the next step. 

Type: 

```
select disk # 
```

With # being the disk you figured out from either the List Disk in DISKPART or through Computer Management. 

Now from here type: 

```
list partition 
```

This should show you a list of partitions like so: 

```

DISKPART> list partition 

Partition ### Type Size Offset 
------------- ---------------- ------- ------- 
Partition 1 Primary 171 GB 32 KB 
Partition 0 Extended 109 GB 171 GB 
Partition 2 Logical 2055 MB 171 GB 
Partition 3 Logical 107 GB 173 GB 

```

For me linux is installed on Partition 3 according to Vista.  Partition 1 is one of my NTFS partitions, but I installed the GRUB bootloader directly to the Logical drive in Partition 3. So now I know my Partition number is 3. 

Run EasyBCD and select Add/Remove Entries.  Select Linux/BSD tab. Select GRUB under Type. Change the Hard Drive and Partition to match what you figured out above and select Add Entry.  Then click Save.

[COLOR="Green"]----- Problems with booting Linux/EasyBCD 1.52 or older section[/COLOR]

Download bootpart26 [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

Extract bootpart to a folder (I used c:\bootpart)


From an administrator command prompt:

```
C:\> cd \bootpart

C:\bootpart> bootpart
```

to get a list of your partitions.

Find the number of the ext3 partition you installed linux and GRUB to.  (In my case it was enumerated as partition 5.)  If you notice LBA in the partition line (which most should be), then you need to remember to specify it in the command prompt when you extract the GRUB  MBR from your partition.

Now type this at your prompt:

```
bootpart # LBA nst_grub.mbr
```

With # being the partition grub is installed on and specifying LBA.  This dumps out the GRUB MBR to file.

You now copy or move the nst_grub.mbr into your Drive:\NST.   You can figured out what drive this is stored using EasyBCD by looking through the entries.   You can also search your disks for the \NST folder that your particular Vista install uses, if Vista is not installed on your first drive on your system.  The NST folder that contains the current nst_grub.mbr will be your &#8220;Boot&#8221; drive.  I have my Vista installed on a 4th disk and my Windows XP disk actually contains the &#8220;true&#8221; \NST folder.  Overwrite or rename any existing nst_grub.mbr files as this was created by EasyBCD and doesn't always work.

[COLOR="#008000"]----- End Problems with booting linux/EasyBCD 1.52 or older section[/COLOR]

From this point you should be able to reboot and select the Linux entry you added before from the Vista bootloader.  If it works you can now use Envy or manually install the latest Nvidia drivers into Ubuntu.

Good Luck!  I hope this helps.

---

### Post by Computer Guru on 2007-05-06
Excellent guide there, Blackforge!

EasyBCD 1.6 will be using the same detection engine as bootpart26 - no more problems :)

The old version uses dd, which unfortunately doesn't seem to always work though no one knows why (i.e. not an EasyBCD-specific problem). I believe it may have something to do with LBA, though I'm not sure.

Even better, EasyBCD 1.6 presents users with a list of all partitions, filesystems, sizes, and the disks they're on (in order) to make it much easier to identify the correct partition.

May I ask what the "vga=795" is for?

(The LBA thing isn't necessary unless you're running some ancient machine that technically supports LBA but doesn't report that to the OS)

I've linked your post: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Cheers! :)

---

### Post by Blackforge on 2007-05-06
> **Computer Guru said:**
> Excellent guide there, Blackforge!

EasyBCD 1.6 will be using the same detection engine as bootpart26 - no more problems :)

The old version uses dd, which unfortunately doesn't seem to always work though no one knows why (i.e. not an EasyBCD-specific problem). I believe it may have something to do with LBA, though I'm not sure.

Even better, EasyBCD 1.6 presents users with a list of all partitions, filesystems, sizes, and the disks they're on (in order) to make it much easier to identify the correct partition.

May I ask what the "vga=795" is for?

(The LBA thing isn't necessary unless you're running some ancient machine that technically supports LBA but doesn't report that to the OS)

I've linked your post: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Cheers! :)

The vga=795 is to circumvent problems with a "Black Screen" on bootup with Nvidia 8800 video cards with Ubuntu.  Otherwise it just sort of hangs.  Anyone who doesn't have an 8800 can just skip that step.

Actually when I first extracted the MBR using bootpart without specifying LBA, it wouldn't boot.  However when I noticed all of my partitions actually specified LBA I decided to give it a shot.  At that point it booted.  Not sure why it worked if that isn't the case?  Maybe I just got lucky.

Here is the partition readout that led to me to try it:

Physical number of disk 0 : xxxxxxxx
 0 : C:* type=7  (HPFS/NTFS), size= 488384993 KB, Lba Pos=63
Physical number of disk 1 : xxxxxxxx
 1 : D:  type=7  (HPFS/NTFS), size= 179197011 KB, Lba Pos=63
 2 : D:  type=f  (Win95 XInt 13 extended), size= 113852655 KB, Lba Pos=35839408

 3 : D:  type=82   (Linux swap), size= 2104483 KB, Lba Pos=358394148
 4 : D:  type=5   (Extended), size= 111748140 KB, Lba Pos=362603115
 5 : D:  type=83    (Linux native), size= 111748108 KB, Lba Pos=362603178
Physical number of disk 2 : xxxxxxx
 6 : E:* type=7  (HPFS/NTFS), size= 146512768 KB, Lba Pos=63
 7 : E:  type=7  (HPFS/NTFS), size= 146520832 KB, Lba Pos=293025600
Physical number of disk 3 : xxxxx
 8 : F:* type=7  (HPFS/NTFS), size= 488384512 KB, Lba Pos=2048

Since you linked this, I marked the 8800 section as optional.

---

### Post by Computer Guru on 2007-05-06
Ah - nice catch there!

EasyBCD 1.6 will check if the drive is LBA and if it is, export the bootsector with LBA on. If it's not, it'll detect that too then :D

Thanks :)

When you say "wouldn't boot" do you mean the "GRUB_" error?

---

### Post by Blackforge on 2007-05-06
Yes, stuck at GRUB or maybe thats the time it would just reboot the system when you select NST Linux.  I tried so many things yesterday, I can't remember anything except what worked.

---

### Post by Computer Guru on 2007-05-07
> **Blackforge said:**
> Yes, stuck at GRUB or maybe thats the time it would just reboot the system when you select NST Linux.  I tried so many things yesterday, I can't remember anything except what worked.
That's OK, thanks! :)

---

### Post by ZapComix on 2007-05-07
Great HowTo Blackforge!

I have been trying to triple boot XP, Vista, and Ubuntu 7.04 for 2 weeks. Yesterday I found a link saying that EasyBCD could make it happen but when I set it up I kept getting a GRUB Geom Error.  I read several posts about it and tried several suggestions and nothing worked.  I used your guide from the ---- Beginning of Vista Bootloader section and it worked perfectly.  The Vista bootloader kicked off GRUB and I now have a functioning triple boot machine.

Thanks, this was such an easy fix :) 

I also see that EasyBCD 1.6 should work the same way as bootpart... nice!

---

### Post by Blackforge on 2007-05-07
> **ZapComix said:**
> Great HowTo Blackforge!

I have been trying to triple boot XP, Vista, and Ubuntu 7.04 for 2 weeks. Yesterday I found a link saying that EasyBCD could make it happen but when I set it up I kept getting a GRUB Geom Error.  I read several posts about it and tried several suggestions and nothing worked.  I used your guide from the ---- Beginning of Vista Bootloader section and it worked perfectly.  The Vista bootloader kicked off GRUB and I now have a functioning triple boot machine.

Thanks, this was such an easy fix :) 

I also see that EasyBCD 1.6 should work the same way as bootpart... nice!

Glad I could help!  The only installation of Linux I got working without doing this was Sabayon.  Unfortunately I just wasn't happy with it and wanted to get Ubuntu going.  I had been trying off and on for over a month on different hardware.  Finally tracked down all the "correct" information and put this together.

---

### Post by fisher0065 on 2007-10-13
Firstly, great post, very helpful.

Secondly, using this post seemed to get the bootsector recognised, but it says:

Loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk
Insert Systemdisk and press any key.

Not sure what it wants but do you know anyway around this?

---

### Post by Blackforge on 2007-10-15
> **fisher0065 said:**
> Firstly, great post, very helpful.

Secondly, using this post seemed to get the bootsector recognised, but it says:

Loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk
Insert Systemdisk and press any key.

Not sure what it wants but do you know anyway around this?

What version of EasyBCD are you using?  I'd suggest skipping my EasyBCD steps above and trying the latest 1.7 version.  I think that error is from older NeoGRUB which is part of the older version and was flakey when I used it.  Not sure about in the later versions.  My method installs the actual GRUB bootsector to the linux partition.

---

### Post by fisher0065 on 2007-10-15
Im already using version 1.7, same issues.  The mbr that is being written out looks wrong, all it says is that error in its text.

---

### Post by Blackforge on 2007-10-15
Just took at a look at my nst_grub.mbr file and that definitely looks correct.  I see the text you are referring to.

I just installed 7.10 RC last night, and used EasyBCD 1.7 and it worked without a hitch.  (outside of the splash page problems I have with Ubuntu itself)

During your install, you actually installed GRUB to the linux root partition itself (or the boot partition if you've split up the partitions)?  In EasyBCD make sure the partition you selected was classified as "Linux Native".

Try telling EasyBCD that you don't have GRUB installed when you create the entry and see what happens.

---

