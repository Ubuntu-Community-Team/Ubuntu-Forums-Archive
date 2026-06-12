---
title: "[SOLVED] XP SP3, Ubuntu 8.10 and Fedora 10 Triple Boot"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Jammy4041 on 2008-12-01
Hi all,

I came across Fedora 10, and I wanted to give it a go. 

However, I want to install ubuntu as well, on a system which I have, for this reason, just formatted and installed windows. 

So, what would now be the best way to go on and do a triple boot? 

Thankyou all for your help,

James

---

### Post by Kevbert on 2008-12-01
Install Fedora next and finally Ubuntu as Ubuntu is best at finding Linux OS and adding them to the grub menu.

---

### Post by Jammy4041 on 2008-12-01
OK- I have just managed to install Fedora on my computer. I shrank my windows partition using gParted and installed Fedora in the resulting free space.

---

### Post by Jammy4041 on 2008-12-02
This maybe be helpful,

Fedora 10 was set up using defaults. It has a 196.11MiB /boot partition and the rest seems to be an lvm drive not recognized by the  gparted CD as it comes up in black.

/dev/hda1 = Windows XP (NTFS)
/dev/hda2 = Boot Partition (EXT3)
/dev/hda3 = Fedora (LVM)

---

### Post by Jammy4041 on 2008-12-02
Where would I have to go from here>? How would I have to install ubuntu to acheive a triple boot? Would there be any problems/things I have to take into consideration? 
 
And finally, would I put this all into one Grub screen?
 
Again, thank you all for your help

---

### Post by Jammy4041 on 2008-12-02
If this helps, I have attached an image of gParted, showing the above.

---

### Post by nvance on 2008-12-02
When you go to install Ubuntu, you can tell it to install within the leftover space that you have as 'unknown' on your harddrive.  With the Ubuntu install it should recognize, Fedora, and XP therefore adding them into Grub without any issue (that is my experience).  I am not sure if you have to manually partition out that remaining space or if Ubuntu will use it as is.

---

### Post by Chazall1 on 2008-12-02
If you add a Dedicated grub boot partition, you can install and uninstall your OS and Grub would not be tied to any OS
Look at my link on Getting started, look at Grub and info on the dedicated grub boot partition. I use this configuration and has eliminated alot of grub confusion!

---

### Post by Jammy4041 on 2008-12-10
Hi, Thanks that's what I have been needing- a dedicated boot partition.
 
I now have:
 
/dev/hda1 Windows Partition (NTFS)
/dev/hda2 GRUB Partition (Resiser FS)
/dev/hda3 Extended Patition consisting of:
/dev/hda5 Fedora Partition (Unencrypted, ext3)
/dev/hda6 Swap Space
/dev/hda7 Ubuntu Partition
 
The only problem that I have now is getting to boot fedora and ubuntu. Would I be best editing the grub partition from a live cd and saving it to disk? 
 
I don't know if this would make any difference, but the grub menu I copied from was from my old fedora installation before I deleted it to make way for the current layout.
 
Thanks for all your kind help so far, and sorry, I have taken a few days to respond.
 
EDIT: I have added a picture for all to see.

---

### Post by caljohnsmith on 2008-12-10
How far did you get about installing Grub to your hda2 Grub partition and installing Grub to the MBR (Master Boot Record)? If you've done that part, you could take the new menu.lst created by Fedora/Ubuntu and combine their entries into one menu.lst, and put that in your Grub partition. Or if you need help with any of the specific steps of creating that Grub partition, let me know and I'll be glad to lend a hand.

---

### Post by Jammy4041 on 2008-12-11
I am able to boot windows from this grub menu, but I now need to assign entries for ubuntu and fedora as my main problem is getting to boot my installed ubuntu and fedora I will edit the /media/boot/grub/menu.lst with the live cd and save it to the hard drive that way.
 
Would I also be able to boot them for the Super Grub Disk?
 
As I have said before, thankyou for all your help

---

### Post by caljohnsmith on 2008-12-11
> **Jammy4041 said:**
> I am able to boot windows from this grub menu, but I now need to assign entries for ubuntu and fedora as my main problem is getting to boot my installed ubuntu and fedora I will edit the /media/boot/grub/menu.lst with the live cd and save it to the hard drive that way.
 
Would I also be able to boot them for the Super Grub Disk?
 
As I have said before, thankyou for all your help
You could boot into Ubuntu/Fedora with the Super Grub Disk like you say, or you could simply mount their partitions from the Live CD in order to access their menu.lst files. For instance, you could do:
```
sudo mkdir /media/hda5 /media/hda7
sudo mount /dev/hda5 /media/hda5
sudo mount /dev/hda7 /media/hda7
gksudo nautilus /media/hda7 &

```
And then you can access your Fedora/Ubuntu partitions in /media/hda5 and /media/hda7 respectively. It's entirely up to you how you want to do it, there's always many ways of doing things in Linux. :)

---

### Post by Jammy4041 on 2008-12-13
[FONT="Arial Black"][SIZE="5"]**SUCESS!**[/SIZE][/FONT]

Thankyou for all you help, but this thread is now OFFICIALLY SOLVED! I now have a Fedora, Ubuntu and XP Triple Boot running off just one GRUB screen

What I had to do was to delete /dev/hda5, /dev/hda6 and /dev/hda7 and do [another] fresh install of fedora, with an unencrypted install filling the rest of the drive. 

Then I loaded up the ubuntu installer and it recognised Fedora 10 and I made room for ubuntu. 

Finally, I deleted the second swap area and ubuntu with filling the rest of my drive up.

In Ubuntu I made a symlink (thanks to Herman's guide) to make sure my fedora stays up to date and that also means my ubuntu stays up to date.

In gParted I also made labels of my partitions.

In short, thankyou very much to all of you how have helped. 

:guitar:

---

