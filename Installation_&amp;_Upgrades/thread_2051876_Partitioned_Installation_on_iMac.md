---
title: "Partitioned Installation on iMac"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by kiusau on 2012-09-02
I own a Mid-2007 iMac with a partitioned hard-drive.  When I go to install the latest version of Ubuntu on the partition that I have set aside for the installation, I am told by Ubuntu that my root is undefined, and the installation aborts with an error message.

  How might I overcome this impass?  Any suggestions?

Roddy

---

### Post by 2F4U on 2012-09-02
Do you have other operating systems installed?

---

### Post by kiusau on 2012-09-02
Yes, I have OS Lion installed.
The format of the partition on which I want to install Ubuntu is in the 32-bit FAT format, however.
Specifically, the partition has the volume format MS-DOS (FAT).
When it asks me to select a volume this is the one that I select, but it is still unhappy.

---

### Post by Lars Noodén on 2012-09-02
> **kiusau said:**
> 
The format of the partition on which I want to install Ubuntu is in the 32-bit FAT format, however.

That filesystem won't work for Linux.  You'll have to choose a useful filesystem like EXT4 or something.  When you do the installation, you'll have the choice of using the existing partition and formatting it to the filesystem of your choice.  In the Desktop images the choice will be "Something else: You can create or resize partitions yourself..."

---

### Post by kiusau on 2012-09-02
1) When given the three options of dual boot, erase, or something else, I chose something else.
2)  Having chosen something else it automatically provided me with the option of repartitioning my partition.  So, I expanded the original partition to its originally intended size and chose DOS format.  Should I have chosen something else?  

By the way, I do not remember having seen the format that you suggested.  There was a long list of format options, though.

This is what the partition selection menu looks like:

                                         format            size                 used
/dev/sda       
freespace                          box              0MB            
/dev/sda1   efi                 box              209MB            209
/dev/sda2   hfs+              box              228633MB     30799
/dev/sda3   hfs+              box              650MB            503
/dev/sda4   fat32            box              91445MB       756
freespace                          box              134MB

The entry /dev/sda4 fat32 is what I tried to reformat.  Although I was unable to check the box, I was able to get it to appear in isolation at the bottom of the window via a drop down menu.  it was when I went to format it in still another panel that I was told that the root was not defined.

---

### Post by black veils on 2012-09-02
i think i am a bit confused, but this is what you want, when having gone into "something else"

[B]1st partition (after the mac OS)
[/B]
format:  ext4

mount point:   /  which is root

[B]
2nd partition (after root)[/B]

format: swap (size of your ram, plus 1/2)

no mount point

---

### Post by darkod on 2012-09-02
No need to specifically try to format it.

Select /dev/sda4, click the Change button below. That will open a new window.

In the Use As field, select ext4. That will try to format it as ext4 automatically since right now it's different type.
In the mount point field select /.

That's it.

I am not sure if the bootloader installs correctly on Mac with UEFI. But the above it how to select partition, filesystem type and mount point during the manual install.

---

### Post by kiusau on 2012-09-02
OK.  Some progress has been made.

Doing as I was told resulted in two procedural requests from Ubuntu:  the first that I was able to easily meet and the second that is less easily implemented because of insufficient information in the instruction.

After reformatting dev/sda4 with EXT4 Journaling and assigning the mount point as / I was asked to create a new partition of at least 1MB in size and assign it to a category of partition called "[something] BIOS"for the purpose of booting. This succeeded.

Ubuntu then asked that I reserve still another partition for swapping.  Unfortunately, it did not say how big, and I have no idea.  Any suggestions?

---

### Post by black veils on 2012-09-02
as i said, swap is best made the size of your ram plus 1/2. eg. 2gb ram would mean 3gb swap, which i am guessing they want in mb's, not gb's. each gb equals 1024 mb's.

---

### Post by darkod on 2012-09-02
You can also tell it to proceed without swap. It can work without it.

Usually it's better to have it since if it gets low on memory it will start using the swap space. But if you have loads of RAM, you might never use swap anyway.

If you do want to add it, the best would be to delete sda4 (and the new sda5 you might have created for the bios_grub partition), and then create three partitions in the place of the two.

For swap you select the Use As swap area, and it doesn't use mount point.

---

### Post by kiusau on 2012-09-02
OK!  Still further progress has been made.
Before attempting to install, however.  I have at least one further question:  How do you eliminate unwanted free space?  In the process of creating my BIOS boot partition I inadvertently create 0MB of free space.  I believe that this occurred because I shrank my original partition more than what was required to create the BIOS boot partition.  Now, when I go to delete it by pressing the DEL button, nothing happens.

---

### Post by darkod on 2012-09-02
Since your xfs partitions are nicely lined out at the front, I suggest to delete the ubuntu partitions and create them again with the size you want. That's much better and easier than resizing. And currently there is no data on the ubuntu partitions anyway, so deleting them doesn't lose anything.

Also when creating partitions note the difference between MB and MiB for example, if you want to create some exact size.

I would say that's much easier right now to remove any unallocated space between these partitions, as opposed to moving them around to eliminate the unallocated space.

---

### Post by kiusau on 2012-09-02
I am hesitant to mess around any further with my partitions for fear of wiping out my MacOS partition.  It would pose much difficulty for me to replace it, as my machine is quite old and previous experience tells me that I would have to take my computer into the shop to replace the system software.

Here is my current partition status.  Please advise very carefully.

device           type    mount    format?                        size                  used
/dev/sda      
freespace                                   box                              0MB
/dev/sda1     efi                        box                              209MB            209MB
/dev/sda2     hfs+                     box                              227633MB      30799MB   
/dev/sda3     hfs+                     box                              650MB             503MB
/dev/sda4     ext4        /           box (checked)           88371MB        1580MB  
freespace                                   box                              0MB
/dev/sda6     swap                   box                              3072MB            unknown
/dev/sda5     biosgrub            box                             1MB                  unknown
freespace                                   box                              0MB


1) Notice that all of the so-called free space has disappeared despite the continued  presence of freespace.
2) Notice that the order of the /dev/sda partitions is not out of order.
3) Finally, in the menu bar below the above panel there are now only four options:

/dev/sda  ATA WDC WD3200AAJS-4 (308.1GB)
/dev/sda1
/dev/sda4  (highlighted)
/dev/sda5

---

### Post by kiusau on 2012-09-02
Thank you for your patience.  Truly, I am very surprized that I have come this far.  You all have been very helpful.

---

### Post by darkod on 2012-09-02
> **kiusau said:**
> Thank you for your patience.  Truly, I am very surprized that I have come this far.  You all have been very helpful.

So, did it install correctly or not yet?

The partitions list you posted above looks good.

As for the bootloader location, I am not sure how would it work on Mac dual boot. With windows dual boot it goes on /dev/sda which is the MBR of the disk. On Mac I am not sure if it needs to be /dev/sda or /dev/sda4 (the / partition).

---

### Post by kiusau on 2012-09-02
What is the device for boot loader installation?

Is it the partition on which resides Apple's Bootcamp -- namely, my MacOS?
What could happen, if I fail to choose the proper device?
1)  Would I still be able to boot my MacOS?
2)  Would I have to reinstall Ubuntu?

Is there a special software other than Bootcamp that I must use under the new versions of Ubuntu and MacOS?

---

### Post by darkod on 2012-09-02
Sorry, but I don't have any detailed knowledge how Mac boots. You might be able to ask on some Apple forum where to install the bootloader of the other OS in a dual boot.

If you install it on /dev/sda4, that can't ruin your OSX boot since grub2 will be on the / partition. So the worst that can happen is that you won't be able to boot ubuntu but OSX should work as normal.

Also, if it turns out you have installed grub2 to the wrong device/partition, you can add it on another one without reinstalling ubuntu from scratch.

---

### Post by kiusau on 2012-09-02
What does grub2 stand for?  Is it short for the boot loader software or still another partition?

---

### Post by kiusau on 2012-09-02
I would like to report that it is possible to install a Ubuntu 12.04 on a mid-2007 iMac in a MacOS Lion operating environment.  Further, I would like to thank everyone for their effort in helping me to make this possible.

I am not sure that my approach to this success was either the best or the most straight forward.  Nevertheless, I am happy to report that my installation has been successful. 

Roddy

---

### Post by darkod on 2012-09-03
> **kiusau said:**
> What does grub2 stand for?  Is it short for the boot loader software or still another partition?

Yeah, grub2 is the ubuntu bootloader. Glad it worked.

---

