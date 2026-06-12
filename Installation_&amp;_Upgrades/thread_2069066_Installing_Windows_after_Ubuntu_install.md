---
title: "Installing Windows after Ubuntu install"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2012-10-10
My wife bought a new laptop:  HP Pavilion g6.  It is an Intel dual core and so runs 64-bit.

I had trouble installing Ubuntu 12.04 LTS 64-bit and in the process accidentally deleted the pre-installed Windows 7 Home Prem 64-bit.  It actually installed over the Windows partition deleting it.  I have now completed the Ubuntu install and settings, and would like to re-install the Windows OS, as she wants it..... :D

I have ordered the Windows restore CD (I have tried others I have laying about but for some reason, I assume it is that they do not have the correct HD drivers, they can not find the HD so can not install).  I have ordered the official HP recovery CD for this machine, so should load OK.

I have created a spare partition of 50G, currently unformatted, especially for it.

In the past I have had trouble when installing Windows after Ubuntu because its MBR deletes or prioritises over the GRUB install.  So I need help.

How do I install the Windows and retain my Ubuntu and GRUB install?

---

### Post by Jonners59 on 2012-10-10
Actually, just seen this....  I shall try it out and revert if I have any issues or comments.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2012-10-10
I'm concerned that what HP will send you will only be a "restore CD" from the standpoint of booting WinPE and looking for a Recovery partition on the drive.  This is because a CD is simply too small to hold Win7.

When you get the CD, you should look at its contents in Ubuntu.  If you don't see something like Wim.img (compressed windows image file), then my suspicions are correct.

For a WinPE-based restore to work, not only does the Recovery partition have to be intact, the drive itself must still have the original partitioning scheme -- which you removed when you installed Ubuntu.

So, if the CD does work (which I doubt it will), it will likely reformat your entire drive and reinstall Win7 from scratch.

---

### Post by coffeecat on 2012-10-10
> **Mark Phelps said:**
> I'm concerned that what HP will send you will only be a "restore CD" from the standpoint of booting WinPE and looking for a Recovery partition on the drive.  This is because a CD is simply too small to hold Win7.

+1

The Microsoft Win 7 64-bit install DVD is about 3.2GB. A set of HP Win 7 restore DVDs is much bigger. When I created a set for my HP Mini netbook running Win 7, it created no less than 4 DVDs, 4.1, 4.1, 4.1 and 3.2GB. I don't know why so much but you need the set to go with your particular model. Hopefully, that is what HP will send you rather than a single CD.

---

### Post by Jonners59 on 2012-10-11
Oh, hell!!!!
I so hate M and the big boys...  I hope you are both wrong, please..... 

It is the set specifically for this machine.  I went to their website and looked up the exact model and then ordered the recovery kit.  It is called, according to their invoice/website.

[FONT=arial, helvetica][SIZE=2][COLOR=#000000]System Recovery  Kit for MS Windows 7 Premium x64  System Recovery Kit  g6-1372saSystem  Recovery Kit  English, - (DR057E_A8S61EA#ABU_679938-031)                                                             [SIZE=1]                                                                                                                                         
Hardware product number: A8S61EA#ABU                                                                                                    [/SIZE][/COLOR][/SIZE][/FONT]

The other problem is that, if it does wipe the disk and install the system to "as new", even trying to shrink the partition it will only reduce to 150Gb due to unmovable fragments, when it only needs a max of 40Gb.  And the other point is, that the Ubuntu install failed because I could not install to the partition I had created, no matter what I did, so I let the CD do the default "install alongside Windows" and it just installed OVER the Windows partition, hence where we are today.

Kinda embarrassing. :redface:

PS:  There are two partitions, small at the front of the HD that I can not get in to.  I think one is an HP thingie and the other the "Recovery"...  either way, they were not searchable even with my current Windows CDs

---

### Post by coffeecat on 2012-10-11
> **Jonners59 said:**
> 
PS:  There are two partitions, small at the front of the HD that I can not get in to.  I think one is an HP thingie and the other the "Recovery"...  either way, they were not searchable even with my current Windows CDs

The usual default for HP machines with Windows 7 is as follows:

Partition 1 - SYSTEM (your Windows 7 boot partition).
Partition 2 - Your Windows C: partition.
Partition 3 - The recovery partition.
Partition 4 - HP_TOOLS - a tiny partition right up at the top end of the drive.

Some or all of #1, #3 and #4 will have the hidden flag set which is why you can't see them in Windows. You say you overwrote the Windows C: partition rather than the recovery partition, so if you still have the recovery partition, you should be able to boot from this from the BIOS without needing the DVDs. The recovery partition and the recovery DVDs have the same functionality.

> **Jonners59 said:**
> The other problem is that, if it does wipe the disk and install the system to "as new", even trying to shrink the partition it will only reduce to 150Gb due to unmovable fragments, when it only needs a max of 40Gb. And the other point is, that the Ubuntu install failed because I could not install to the partition I had created, no matter what I did, so I let the CD do the default "install alongside Windows" and it just installed OVER the Windows partition, hence where we are today.

Two points:

The unshrinkability of the C: partition will be irrelevant to when you run the restore function. This will create a new filesystem in the partition or may simply create a new set of partitions, restoring the machine to its factory condition, depending on what choices are available in the restore utility.

The Ubuntu installation probably failed because of the four primary partition limit for mbr partition table. It sounds as though you created unallocated space by shrinking the Windows C: partition. It is impossible to create a partition in that space without deleting one of the other partitions first. Once you've restored Windows, I suggest you start a new thread asking for help with installing Ubuntu to your HP machine. This is a common problem, but easily solved, and there are many threads about it.

---

### Post by Jonners59 on 2012-10-11
Thanks Coffeecat
> **coffeecat said:**
> The usual default for HP machines with Windows 7 is as follows:

Partition 1 - SYSTEM (your Windows 7 boot partition).
Partition 2 - Your Windows C: partition.
Partition 3 - The recovery partition.
Partition 4 - HP_TOOLS - a tiny partition right up at the top end of the drive.

Some or all of #1, #3 and #4 will have the hidden flag set which is why you can't see them in Windows. You say you overwrote the Windows C: partition rather than the recovery partition, so if you still have the recovery partition, you should be able to boot from this from the BIOS without needing the DVDs. The recovery partition and the recovery DVDs have the same functionality.

That sounds correct.  I can see them in gParted, but there is no access.  And I recall seeing 4, but only 2 seem to remain.  I am certain I deleted the C, and it does boot in to the initial mbr screen (I think that is what it is referred to - the equivalent of GRUB where the OS is selected).  It then says there is a problem and to install the Install CD and use Repair.

I'll take a look at the BIOS settings and get back.  May be a day or two.



> **coffeecat said:**
> Two points:

The unshrinkability of the C: partition will be irrelevant to when you run the restore function. This will create a new filesystem in the partition or may simply create a new set of partitions, restoring the machine to its factory condition, depending on what choices are available in the restore utility.

The Ubuntu installation probably failed because of the four primary partition limit for mbr partition table. It sounds as though you created unallocated space by shrinking the Windows C: partition. It is impossible to create a partition in that space without deleting one of the other partitions first. Once you've restored Windows, I suggest you start a new thread asking for help with installing Ubuntu to your HP machine. This is a common problem, but easily solved, and there are many threads about it.

Agree with point 1.

Point 2.  I agree, though I know about the limits from past experience and initially used the "Try Ubuntu" to create the partitions.  I used an "Extended Partition" and put two "Logical" partitions in there.  Then did the install.  It could not install in to either partition, so I tried the same via the install setup, creating new partitions, etc.....  It would create them, but would not install in to them, something I have done successfully on many other machines in the past.

Lest see what turns up.

---

### Post by Jonners59 on 2012-10-17
OK folks
CDs have arrived.  4 (four) in total. 1 x Recovery CD and 3 x new install......  So the question is which do I try first?

I am concerned that, based on your feedback below, one (or both)  could delete the current installation of Ubuntu.

Your vote/views are very welcome.

---

### Post by Mark Phelps on 2012-10-17
Restoration media obtained from an OEM are designed to do one thing -- restore the PC to the state it was in when you first unpacked it and started it up.  The nearly always involves wiping the hard drive, reformatting it, and reinstalling the OEM's version of Windows -- complete with any apps that came preinstalled.

Since different restore media do different things, I don't think any of us can tell you for sure what this media will do.

But, it's most likely that your Ubuntu install will be erased.

You could try to save it by hooking up an external drive and using Clonezilla (run by booting from a CD) to image off the Ubuntu install.  That will give you something you can later use to restore it to the hard drive.

As to what to insert first, you should have received instructions on that, either with the CDs, or via email from the OEM.  My guess, and it IS a guess, is that you would insert the Recovery CD/DVD first, and then insert the other CDs/DVDs in order.

---

### Post by JKyleOKC on 2012-10-17
Most, if not all, current products from HP and Compaq are using the UEFI-gpt boot procedure rather than the more familiar MBR-legacy approach -- and the Ubuntu installer doesn't always recognize that fact, resulting in serious problems when you want to dual-boot.

Before you do anything to restore the system, read the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to get an understanding of what may be at the root of your problem with the laptop, and how to solve it.

Using the HP restore DVDs will definitely remove your existing Ubuntu installation, so be sure to use Clonezilla or a similar program to keep an image of it. After restoring Windows and before doing anything else, boot up Windows and go to its Disk Management utility to shrink the "SYSTEM" partition as small as possible. I've seen reports that doing this before anything else can make the Win7 partition much smaller; I didn't do so and could only shrink it to about 250 GB!

After the initial shrinking, you can clean bloatware off of Win7 if you like, then defragment its partition a couple of times and try to shrink it again to get it even smaller.

Be sure to note the requirements for UEFI compatibility in the page I referred to above, and make certain that your BIOS is set up accordingly.

Only after all this should you reinstall Ubuntu. Use the live CD and tell it to use the unallocated space on the drive, or take the "Something else" option and set up your partitions manually. Finally, put the saved image back over the new installation of Ubuntu.

Since the gpt scheme has no four-primary limit, ignore all advice about extended and logical partitions if you have a UEFI system. This is becoming an increasingly serious problem, as UEFI usage spreads!

---

### Post by gerrman97 on 2012-10-17
i read over your posts. i think you should just install windows (make sure you format your hard drive) then install xubuntu from the application called wubi.exe. you can get the app. from the ubuntu website. hope that works
 
also if you need it i can send you a windows 7 installation iso file that u can use. just email me at {removed emails to prevent spam}[EMAIL="gerrman97@yahoo.com"][/EMAIL]

---

### Post by oldfred on 2012-10-17
@   	gerrman97
I removed your emails. We are a forum so users can collectively solve issues. Also never trust software from an unknown source.


OEM serial number on bottom of system will not work for a full install ISO, you still have to pay for the full install software.
Full install ISO - Limited use then you must purchase
[http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/](http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/)

---

### Post by gerrman97 on 2012-10-17
allright. sorry new guy.

---

### Post by Jonners59 on 2012-10-17
Guys
Many thanks for the input.

"JKyleOKC" and "Mark Phelps"  Thanks for the tips.

"gerrman97" thanks for looking in and the kind offer(s).  Re WUBI.exe, no, not for me.  That is OK when forst starting out and experimenting.  I only use MS for the odd apps that do not work on Ubuntu, so I always have a full and proper install of the OS

"Old Fred" always a comfort to know you are there in the background!

 I have much to think about.  I am thinking a good idea to make the iso  image, follow up on my understanding of the new UEFI and I shall try and contact HP and see what they have to say, but I do not hold my breath.  Then go with it  and see what happens using the full install CDs in the hope they may ask for partitions to choose from.  May ask, note!!!!

I'll feedback as I think this could be a good lesson for others.

OK first update.  Followed the link re EIFD:  I suspected upon reading it that this was not an issue, then running the cmd ```
dmesg | grep 'EFI: mem' && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
``` showed it was a legacy setup.

2nd update:  I thought I'd just run the Recovery CD and see what comments it made.  It is clear it deletes and reformats the whole HD, so that is a no, no until I make an image of the current OS.

I have raised a posting on the HP forum:

Reply.  This sounds like the answer we are after.  Shame I didn't know this before I bought the recovery CDs.  Could have saved me £35 and 2 weeks of time.

[HTML]If the retail Windows 7 disk is used, then it will give the user a  choice.  If the COA sticker is still readable on the case of the PC, a  retail disk can be used with that key to install windows 7.  If the  retail disk cannot be borrowed, see here: http://en.community.dell.com/support-forums/software-os/w/microsoft_os/3316.2-1-microsoft-windows-7-...Pick  the Windows 7 version that matches what was install, then follow  directions under "Windows 7 Official .iso Files (Digital River)"[/HTML]

Downloading now - 1 hr 30 mins

Downloaded and installed "unetbootin" to install the iso image to USB by running
```
sudo apt-get install unetbootin  
```

Installed the image to USB drive.  Very simple.

Shall try and install to the laptop either tomorrow late evening of Saturday.....

---

### Post by Jonners59 on 2012-10-18
OK, small problem.
I thought I would test run the image to see what prompts come up before I install.
When I boot with the USB it opens in to a unetbootin window with "Default" and "Tab to change settings" and a counter running down from 10 sec to zero to boot.  It just loops round and does not boot

As I am working on one machine and repairing another I installed unetbootin on the repair machine too just in case it was needed, but it made no difference.

What am I doing wrong?  Why does it not boot?  Any helpers, please?

ok IGNORE THAT.  hAVE FOUND A wINDOWS IMAGE PROGRAME AND USED THAT IN A wINDOWS os ON ANOTHER MACHINE.  i HAVE BURNT THE ISO TO usb.  iT NOW LOADS, BUT STOPS AT THE SELECTING WHICH PARTITION BECAUSE IT SAYS IT DOES NOT HAVE THE CORRECT DRIVERS.  How do I find the drivers? "ATA Hitachi HTS54757"

---

### Post by Jonners59 on 2012-10-21
OK SOLVED:

I hope the following helps others with HP machines.  Seems there are many around from the threads and sites I have read who had and could not resolve this.

1. Install and run "Grub Customiser", customising if required, "Save" and "File"/"Install to MBR".

2.  First check if EIFD
run the cmd
```
dmesg | grep 'EFI: mem' && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```
For me this showed it was a legacy setup.

3. Delete the remaining HP partitions relating to the original install using "gParted".  There is something in one of these that will block your install.  Create a new partition in **NTFS** and make it **bootable** using the "Flag".  I made mine 60Gb, more than enough as I have also created a partion in NTFS that both share for all downloads and Docs.

4. Obtain a RETAIL copy, do not use the HP Recovery copies, of Windows 7.  The COA sticker has the Key and can still be used.  If the  retail disk cannot be borrowed, see here: [HTML]http://en.community.dell.com/support-forums/software-os/w/microsoft_os/3316.2-1-microsoft-windows-7-official-iso-download-links-digital-river.aspx[/HTML]
...  Pick  the Windows 7 version that matches what was installed, then follow  directions under "Windows 7 Official .iso Files (Digital River)"  I.e. download and burn to either USB or CD.

5. Boot up with the Windows OS CD and install to your new Windows NTFS partition as normal

6. After, reboot into Ubuntu Live CD and select "Try"

7. Install "Boot Repair"
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
``` then press enter
Then enter cmd to install it:
```
sudo apt-get install -y boot-repair && boot-repair
```
Once installed run it and select "Recommended Repair". It shall fix the boot to.

8. Reboot (and do not forget to remove the CD) and load in to Ubuntu.

9. Select "Grub Customizer" and check the setup, it should be as saved before you started this project and then in "File" select "Install to MBR"

You will be good to go....

Now just have to go back in to Windows and customize and fix missing driver issues.

---

### Post by JKyleOKC on 2012-10-21
Your Step 4 gets a "404 - not found" error; apparently it's an incomplete address...

---

### Post by coffeecat on 2012-10-21
> **Jonners59 said:**
> 
I hope the following helps others with HP machines.

....

For me this showed it was a legacy setup.


For an HP machine with a legacy setup - i.e. mbr partition table - that is an extraordinarily complicated procedure. The following should work. It's worked for me and it's worked for others if many other threads are anything to go by:

1 - Backup contents of HP_Tools partition.

2 - Delete HP_TOOLS partition.

3 - Shrink Windows C: partition from Windows Disk Management tool.

4 - Boot up Ubuntu live CD. Use Gparted to create an extended partition in the space you created by shrinking the Windows C: partition. Either use Gparted or the partitioner in the "Something else" choice in the installer to create your Ubuntu root and swap partitions. Either way, use "Something else" to install Ubuntu (which will install grub for you).

5 - Boot into your dual boot and enjoy.

If you have got into a muddle with your partitioning and need to set the machine back to its factory condition, boot up with the DVD restore set that you prepared earlier or that you have purchased from HP and restore the system. Once the machine has been restored to its default state, proceed from 1 above.

---

### Post by Jonners59 on 2012-10-21
JKyleOKC
I have corrected the link.  Should work now.  It takes you direct to the official Windows iso download site.

Coffeecat
It may be, but I, as a non techie, like to make sure every step is very clear so I can repeat if I need to.  Your steps seem shorter, but have not got the detail an idiot like me would need.  Also, I have ensured my repair ended up as an identical copy of the one I had before, hence adding the use of GRUB Customizer, which is not essential.  In all this only took a few minutes

Also, I can not confirm your fix will work.  The HP install prevents any access to the partitions at all.  I have never seen this before.  No Windows build bar the Recovery CD would work. I have seen many threads on this and other forums and none have a solution.  I resolved this on the HP forum and shared it here

Obviously, I don't mind which process is used.  This worked for me and I am happy with it.  I have shared my experience and solution for both helping others and for my future needs.  The thread was there for a long time and no one came up with a solution.  I know this works.

---

