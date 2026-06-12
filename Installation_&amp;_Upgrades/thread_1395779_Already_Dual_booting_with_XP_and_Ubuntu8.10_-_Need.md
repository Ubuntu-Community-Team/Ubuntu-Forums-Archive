---
title: "Already Dual booting with XP and Ubuntu8.10 - Need to install Win7 - Can I?"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Cyber6 on 2010-02-01
I did look all over the place.  Found that most people with similar question are asking for instructions on How to triple boot from scratch. 

I am not in that situation.  Mine is as follows:

1. Laptop V6V (Pentium M - 1.86 GHz) running XP Pro for 5+ years

2. I installed Ubuntu 8.10 (intrepid - Gnome 2.24.1, kernel 2.6.27-11-generic) from a live CD.. easy install  and have been running successfully for more than a year

3. WinXP and Ubuntu have coexisted peacefully 

Now.. I would  like to install Win7 as triple boot.  Meaning, I do not want to get rid of WinXP, and don't want to hurt my awesome ubuntu installation (took me looong months to get it to where it is right now)

Can this be done?

I was thinking in partitioning my hardrive (to make sure not to hurt either install)... and then just add the Win7 to my grub

Is that even possible?? 

Thanks for all your help.


C.

---

### Post by Mark Phelps on 2010-02-01
Yes ... it's possible ... but let me suggest some other things first.

Since you want to make sure that your Ubuntu install is not damaged in any way, you should back up the partition before you do anything.  My suggestion for doing that is using P.I.N.G (Partimage Is Not Ghost) -- a Partimage front-end available from windowsdream.com website.  They provide an ISO file you can burn to a CD to use it to boot and make backups.

Once you have Ubuntu backed up, suggest you then boot from a GParted LiveCD and shrink the partition to make room for a Windows 7 NTFS partition.  I would then run a backup of the resized partition.

You can then use GParted LiveCD to make an NTFS partition, or you could simply boot from the Win7 DVD and select the unpartitioned space -- and let it make an NTFS partition.

Realize that after you install Win7, it will automatically overwrite not only the MBR but will also write its boot files and loader into your XP partition.  You will then have to restore GRUB to restore the capability to boot into Ubuntu.

---

### Post by Cyber6 on 2010-02-01
Ok.. Thanks Mark...   

Now.... what about (real sorry to bother) if boot into XP and partitioned the drive with partition magic.

I can then install Win7 to the new logical partition.  That will certainly destroy my grub anyway.  

Does it sounds like just another way to skin a cat??  


Also, How do I restore my grub after? :-s



Thanks,


C.

---

### Post by raymondh on 2010-02-01
re-installing GRUB (legacy) using a liveCD

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Another comment ... though it's possible to install windows inside an extended partition (as a logical partition), it'll be simpler if you just make it primary.

I would heed MarkPhelps advice of creating a back-up image of your current install using PING.  Once done, I would (as a preference) use gparted to resize, create space and format to NTFS ... then I would just install win7 unto it.

After re-installing GRUB, there might be a need to manually edit the /boot/grub/menu.lst if (and if) grub does not detect the win7 install.  Note, the win7 bootloader will be newer so you might just see 1 windows option in grub which after you select, will present you with either XP or win7.

Raymond

---

### Post by Gatemaze on 2010-02-01
> **raymondh said:**
> 
Another comment ... though it's possible to install windows inside an extended partition (as a logical partition), it'll be simpler if you just make it primary.



Why is it simpler? Anyway, bear in mind you can only have four primary partitions.

> **raymondh said:**
> 

After re-installing GRUB, there might be a need to manually edit the /boot/grub/menu.lst if (and if) grub does not detect the win7 install.  Note, the win7 bootloader will be newer so you might just see 1 windows option in grub which after you select, will present you with either XP or win7.

Raymond

Things have changed with grub2... there is no menu.lst... Ignore this, thought I saw you were using 9.10. Yup, there is still a menu.lst on 8.10

---

### Post by oldfred on 2010-02-01
If you want to directly boot you new install it will have to be a primary partition. If you want to boot thru your XP then it does not have to be a primary.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by raymondh on 2010-02-01
> **Gatemaze said:**
> Why is it simpler?0

Windows can run from a logical partition.  But, it still needs a primary partition to boot from.  So usually, *unless things have changed*, we would split the win install into two and have the boot.ini, the NTLDR and the ntdetect files in one (the boot partition in primary) and the OS in another.  

That's why I offered the suggestion to just have win7 in a primary.

Of course, OP has to adhere to the 4 partition rule.  Either 4 primary partitions or 3 primary + 1 extended (which can then house as much logical partitions his/her system or sanity can take) :)

Regards,


Raymond

---

### Post by Cyber6 on 2010-02-02
Guys.. you are totally amazing.. THANKS.

Let me go slowly on this.. don't want to screw things up.  Worst come to worst, I just end up installing everything from scratch and get a chance to try Karmic Koala.. ;)


I'll try this at the end of day.


Thanks again,


C.

---

### Post by darkod on 2010-02-02
Another suggestion: Since with triple boot you're definitely gonna be short on partitions, after you create unallocated space by shrinking any partition, use Gparted as suggested and create ntfs partition from that unallocated space.
The thing with win7 installer is: if you want to install on existing ntfs partition, it will install there. If you want to install in unallocated space and the installer has to create partition(s), it will create that small 100MB boot partition and waste one primary for you.
Wasting a partition is easily avoided if you have ntfs partition prepared in advance.

---

### Post by Cyber6 on 2010-02-02
Oh My what a ride !!!!  

This is not a story for the faint at heart.. is a story of deception, anger, loss and maybe hope... and is still not finish..


So following Mark's advice (BTW I am not blaming anyone..:P) I download it and burned PING and GParted.  Then things started to heat up..

1. No issues with PING
2. GParted seemed to be working... after 6hrs of nothing decided that something must have gone wrong.  There was no indication that anything was being done.  I close it reboot it
3. At this point I believe I have destroy my data (resizing the partitions).. took a deep breath and decided to just install Win7 from scratch and then try Karmik (what the hell!!)
4. BIG Surprise... found my data totally intact.  XP loaded with no problems, Ubuntu loaded fine too.  
5. Since I have already gone through the worst (resigned to do a fresh install of Win7 and re-install ubuntu) decided to WHAT THE HECK and use gparted to create new partitiones and have it ready to do a Win7 fresh install
6. Loaded from my Win7 DVD, half way through it.. tells me that "it can't install on this hardware"... WTF ???  I know I have the minimal specs.  
7. Decided to try one more time (it wouldn't be the first time Windows gives me funky messages) ... Another surprise...  I get an error message "no boot loader"... AUGH!!!!!!
8. Went to the recovery console (Win7 DVD) and fixed the boot loader (it couldn't find my system boot loader.. so I just fix 'ALL')
9. Restarted the install one more time (still going through)... and crossing my fingers that this time will 'stick'

****sigh****

I am not stupid, but obviously I must have done something wrong.. (buying Win7 for starters... :lol: )

---

### Post by spot-da-haze on 2010-02-03
i found [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) helped alot i installed windows 7 and spent 2 days trying to boot in to ubuntu! ... hope this helps

---

### Post by Cyber6 on 2010-02-03
Thanks Spot..


The good news...   IT WORKS!!!!!!!!!!!!!  Win7 WORKS!!!!!!!!!

Now .. I need to download a new ubuntu flavor ..  Which one is causing the least troubles nowadays?... ;)


C.

---

### Post by raymondh on 2010-02-03
> **Cyber6 said:**
> Thanks Spot..


The good news...   IT WORKS!!!!!!!!!!!!!  Win7 WORKS!!!!!!!!!

Now .. I need to download a new ubuntu flavor ..  Which one is causing the least troubles nowadays?... ;)


C.

Try the liveCD's first.  Though not a comprehensive test of whether the distro works for your system or not, live sessions can give you a 'heads-up' of sorts.

Always have a working/tested back-up of your files.  Also a good idea to [PING]("http://ping.windowsdream.com/") your HD/partitions.

Good luck and happy ubuntu-ing.

Raymond

---

### Post by Cyber6 on 2010-02-08
Wow .. what a ride.  Everything is working BEAUTIFULLY !!!!

Dual booting Win7 Ultimate and Karmic Koala.  I only had to install and re-install Win7 three times and Karmic Koala twice.

I am anal about my installations... don't ask.  :P


Anyway thanks for all the help... :popcorn:

---

