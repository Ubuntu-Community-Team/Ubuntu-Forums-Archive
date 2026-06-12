---
title: "no grub... please help me"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by samssf on 2006-09-16
Ok I've spent 8 hours trying to get Ubuntu installed and am very frustrated.

What pisses me off is all the answers people are giving about my kind of issue is "did you let ubuntu install to MBR??" blah blah.

I am installing ubuntu 6.06.

When I select the disk I want Ubuntu on, and structure my partitions correctly (Windows primary, Ubuntu / root mount as 2nd primary, and a logical partition with /swap)  I GET NO PROMPTS or any other mention of either Grub or MBR. I have never seen the words MBR or grub listed in the Ubuntu install.

I am not doing the default install. Will someone please direct me to a step-by-step guild on using the advanced partitioning of the Ubuntu install????

When my install finishes, I reboot... and windows boots. Grub does not load. I have tried using GPartEd to mark either of my primary partitions on the HDD as bootable. Doesn't help.

ALSO... on the ubuntu screen that lists the mount points and the partitions.. i have no idea what to do. I have not seen anything online detailing this. What i have done so far is assign / to the larger primary partition that is formated as ext3. I assign /swap to the smaller logical partition. What about the other mount points?????? There are tons listed. /boot, /usr, etc. I am guessing this is why my install doesn't work. But no where does anything online or in the install guide tell me what to assign those to. And there's no mention of grub or anything about the master boot record.

jesus I thought I knew quite a bit about this stuff too.

---

### Post by kidders on 2006-09-16
Hi there,

It's probably wise to read a little about Linux before trying to install it ... it's quite different than many other OSs!

You do not *need* to create partitions for every single directory in your root filesystem ... only do so if there's a specific reason! One other observation -- as a rule, try to keep your swap out of logical partitions.

I'm not sure what the trouble with your grub is, but if you can manage to get from one end of the Ubuntu setup to the other without it installing, you can always do it manually later. If you have more than one hard disk, you should make sure it didn't install on any of them first though :-)

Hope that helps.

---

### Post by pradeepadapa on 2006-09-16
hi, 
     i understand ur problm, just in the default install mount the point ' / ' as primary partition not logical partition nd swap also the same nd just keep the swap size double to ur RAM size nd just continue with the installation nd it wll work fine, then reboot nd u shall hav the GRUB,

hav any doubts , u can ask or pm me.

bye

---

### Post by samssf on 2006-09-16
Thanks for the replies and suggestions... however, it seems I've tried this things already.

My swap was in a logical partition... but not the / mount point. I associated the / mount point with the large primary partition I created.

I would hope it didnt install grub onto any of my other drives... since during installation I told it to install to my main drive. The other 2 drives are on a raid array and cant be messed with. It does seem like it recognizes one of my raid drives as drive 0 though... weird.

At tried the first grub install directions I found, but they didn't work. When I booted I still went right into windows. (Keep in mind my windows OS and Ubunutu are on the same drive, both in primary partitions)

Directions for installing grub:
>  find /boot/grub/stage1
>  root (hd?,?)     using values found from above
>  setup(hd0)

---

### Post by randell6564 on 2006-09-16
I think that you are making things more complicated then they really are, my friend.

First.,How about a little info on your hardware, specifically, what type of HD/HD's?  And how about partitions?

Have you tryed to install using the Ubuntu [Alternate CD]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/")?  This installs in text mode and gives you more control over the process.

Ubuntu desktop live CD installs GRUB to your MBR by default, so if you are not getting dual-boot option then it is something that you are doing wrong.

I suggest that you leave your partitions alone, use the Alternate CD and install grub to your MBR when you are asked.

---

### Post by randell6564 on 2006-09-16
> **samssf said:**
> 
(Keep in mind my windows OS and Ubunutu are on the same drive, both in primary partitions)
Directions for installing grub:
>  find /boot/grub/stage1
>  root (hd?,?)     using values found from above
>  setup(hd0)

I did not see this before.

If your OS's are on the same HD, on seperate partitions and you installed Ubuntu AFTER Windoze, but now you keep booting to windows, then that means that Windoze is still in charge of the MBR! (Ubuntu did not place GRUB to MBR)
So...
Whatever 'find /boot/grub/stage1' returns, thats what you want to enter when doing 'root' and 'setup'
Example:
'**sudo grub**'
'**find /boot/grub/stage1**'
if it returns, '**(hd0,0)**' then you would ENTER:
'**root (hd0,0)**'
'**setup (hd0)**'
'**quit**'

---

### Post by randell6564 on 2006-09-16
> **randell6564 said:**
> I did not see this before.

If your OS's are on the same HD, on seperate partitions and you installed Ubuntu AFTER Windoze, but now you keep booting to windows, then that means that Windoze is still in charge of the MBR! (Ubuntu did not place GRUB to MBR)
So...
Whatever 'find /boot/grub/stage1' returns, thats what you want to enter when doing 'root' and 'setup'
Example:
'**sudo grub**'
'**find /boot/grub/stage1**'
if it returns, '**(hd0,0)**' then you would ENTER:
'**root (hd0,0)**'
'**setup (hd0)**'
'**quit**'

After doing this there is no reason that GRUB would not end up on your MBR, UNLESS it is Write Protected!

---

### Post by samssf on 2006-09-21
*solved*

The reason this happens is because the order in which my drives appear in bios and the order in which they load in linux is different. This causes ubuntu to install grub into the MBR of the wrong disk. If I screw around with it, I can get grub installed... but the config list will be screwed up and the OS options will point to the wrong drives. Currently I have to edit the boot commands myself when I get into the grub menu.

---

