---
title: "How to uninstall unbuntu on xp"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Ledus on 2009-12-14
I've had enough problems with ubuntu and i need to uninstall... and i have searched that people that about using a xp disk... which i dont have.

So how can i uninstall ubuntu from my hard drive on xp?
and also make sure that my xp uses the space that  ubuntu used for partitioning.

I cant even get past the login screen in ubuntu after updating but remember the question is  [B][I][U][SIZE=3][COLOR=Blue]how can i uninstall ubuntu from my hard drive on xp?
and also make sure that my xp uses the space that  ubuntu used for partitioning[/COLOR][/SIZE][/U][/I][/B]

---

### Post by lidex on 2009-12-14
> So how can i uninstall ubuntu from my hard drive on xp?
and also make sure that my xp uses the space that ubuntu used for partitioning.

You can do all of that from within windows. Boot into XP and right-click "My Computer" and select the management option (sorry-been a while, can't remember the details). You can select disk management in the left pane. Right-click on ubuntu partition and format to ntfs. If no option for growing XP partition, you may need to use gparted LiveCD:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by raymondh on 2009-12-14
Assuming this is not a wubi-installed ubuntu (or ubuntu is installed in its' own partition)

-  Use XP's disc utility or gparted to delete ubuntu and swap .... and resize the XP install.  If ubuntu and swap are in logical partitions inside an extended ... delete the logical first before deleting the extended.

-  You need an XP install disc (not the recovery cd) to fixmbr.  Otherwise, you will still have GRUB as your bootloader.

If this is a wubi-install

a.  Use the add/remove function in XP
b.  Delete the wubi-related line in the boot.ini file

Always have a working/tested back-up of your files.  Happy holidays.

---

### Post by cartisdm on 2009-12-14
Just as mention above, if your Ubuntu install is on its own partition then go ahead and delete the Ubuntu partition and format it for your Windows install

you can get GParted [here]("http://download.cnet.com/GParted-LiveCD/3000-2094_4-10698802.html")

---

### Post by Ledus on 2009-12-15
> **lidex said:**
> You can do all of that from within windows. Boot into XP and right-click "My Computer" and select the management option (sorry-been a while, can't remember the details). You can select disk management in the left pane. Right-click on ubuntu partition and format to ntfs. If no option for growing XP partition, you may need to use gparted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


there is no option for formating... but there is one called "delete logical drive" and yeah i created ubuntun in its own partion so xp and ubuntu are on the same hard drive but different partions.

---

### Post by lidex on 2009-12-15
Yeah, delete the partition.
Instructions here:
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/]("http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/")

---

### Post by Ledus on 2009-12-15
> **lidex said:**
> Yeah, delete the partition.
Instructions here:
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

ok so how do i make the space which ubuntu used, usable on xp?

---

### Post by darkod on 2009-12-15
> **Ledus said:**
> ok so how do i make the space which ubuntu used, usable on xp?

Create new ntfs partition from the unallocated space. XP will see it and assign a letter to it. Better choice then expanding the XP system partition, especially with no XP disc to reinstall.

---

### Post by Ledus on 2009-12-15
> **Ledus said:**
> ok so how do i make the space which ubuntu used, usable on xp?
  thank you very much looks like i can't use xp at all now it starts up and then it says 

grub loading 
no such partition
grub rescure>

i cant even start system recovery
thank you very much

i can use "try ubuntu without installing" but nothing else... because when i start up the grub loader fails

---

### Post by darkod on 2009-12-15
> **Ledus said:**
> thank you very much looks like i can't use xp at all now it starts up and then it says 

grub loading 
no such partition
grub rescure>

i cant even start system recovery
thank you very much

Well Raymond mentioned you will need an XP install disc to restore the windows MBR.
There was also application called install-mbr but I'm not sure whether you can use it from the ubuntu LiveCD and how to use it.
Get an XP disc from someone just to restore the MBR.

---

### Post by berksted on 2009-12-15
Once you have a windows disk, you'll boot from that and then it will detect your current window installation, at this point you will go into recovery mode and i believe there is a command/option to repair the master boot record.

---

### Post by Ledus on 2009-12-15
> **darkod said:**
> Well Raymond mentioned you will need an XP install disc to restore the windows MBR.
There was also application called install-mbr but I'm not sure whether you can use it from the ubuntu LiveCD and how to use it.
Get an XP disc from someone just to restore the MBR.

Well how much does it cost if a buy a windows xp disc?
do you know any other ubuntu like free OS that i could use?
im thinking of just erasing the whole disk and installing a new os
Ubuntu 9.10 does not regonize my monitor.

---

### Post by darkod on 2009-12-15
I guess this can help you:
[http://tips.vlaurie.com/2006/05/recovery-console-for-those-without-an-xp-disk/](http://tips.vlaurie.com/2006/05/recovery-console-for-those-without-an-xp-disk/)

---

### Post by Ledus on 2009-12-15
Well does anyone know how to uninstall ubuntu from windows vista ?
again without windows vista disk

---

### Post by carniola on 2009-12-15
> Well how much does it cost if a buy a windows xp disc?

Very much depends on the version. Amazon is selling copies of XP for $80+, for example. But if you're going to spend money it would probably make more sense to get a copy of Windows 7.

> do you know any other ubuntu like free OS that i could use?

There are tons. You might try [_Linux Mint_]("http://www.linuxmint.com/"), which is based on Ubuntu.

> 
Ubuntu 9.10 does not regonize my monitor. 

Sounds strange.. What kind of monitor is this? Are you sure it's not the graphic card? What was wrong?

---

### Post by darkod on 2009-12-15
> **Ledus said:**
> Well does anyone know how to uninstall ubuntu from windows vista ?
again without windows vista disk

I have to ask: are you joking with us? The same guidelines apply to vista too. With the difference that for vista MS has issued repair discs so that people that get no dvd media can use them.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by Ledus on 2009-12-15
> **darkod said:**
> I have to ask: are you joking with us? The same guidelines apply to vista too. With the difference that for vista MS has issued repair discs so that people that get no dvd media can use them.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)


are you telling me that by downloading and burning that i can at least get ubunto out my vista laptop?

if not then i'll just send it of to the  _*TechGuys*_ as i have a warranty with them.

---

### Post by Ledus on 2009-12-15
> **carniola said:**
> Very much depends on the version. Amazon is selling copies of XP for $80+, for example. But if you're going to spend money it would probably make more sense to get a copy of Windows 7.



There are tons. You might try [_Linux Mint_]("http://www.linuxmint.com/"), which is based on Ubuntu.



Sounds strange.. What kind of monitor is this? Are you sure it's not the graphic card? What was wrong?

Sorry for double posting.

DO you know any other OS that is free and most compatible?

xbuntu doesnt seem to recogize my monitor and max resoultion is 800x600 plus about 1cm in width about 20-30 cm in length of my screen stays blank
happened on ubuntu to

By the way i dont think windows 7 would work smooth on my comp anyway. (1gb ram)

---

### Post by darkod on 2009-12-15
> **Ledus said:**
> are you telling me that by downloading and burning that i can at least get ubunto out my vista laptop?

if not then i'll just send it of to the  _*TechGuys*_ as i have a warranty with them.

Getting rid of any OS is two step process:
1. You delete the partition of that OS (or reformat it, or similar). Very easy step.
2. You restore the MBR (bootloader) depending what changes were made to it for dual boot and what OS you want to keep using on it.

The CD image from that link will help you create vista repair CD. Note: it can NOT install vista on your or any pc, it can just repair the boot process of existing installation.
So if that's what you had in mind, yes, it will do the job for you.

---

### Post by cartisdm on 2009-12-15
> **Ledus said:**
> By the way i dont think windows 7 would work smooth on my comp anyway. (1gb ram)

If you are considering running Windows Vista, then I'm sure you can run 7 just fine (even better most likely).

Not trying to get flamed here, but if you just download an ISO of whatever version of Windows you are trying to install then burn it to a disk you can then use YOUR ORIGINAL license and install it as normal. Again, not promoting pirating here, just use your own license.

This thread is getting really hard to follow but why don't you post the specs of your machine (specifically your video card) and I bet we can get you up and running a fresh install of Ubuntu (or Linux Mint) with a working monitor very easily and you can start fresh!

---

### Post by raymondh on 2009-12-15
> **cartisdm said:**
> 

This thread is getting really hard to follow but why don't you post the specs of your machine (specifically your video card) and I bet we can get you up and running a fresh install of Ubuntu (or Linux Mint) with a working monitor very easily and you can start fresh!

@ Ledus

1.  Do you want to go back to windows as per your first post?  If so, you need to get hold of a XP install disc > boot into it > select R (for repair) > type 'fixmbr' (no quotes) > if you get a not successful message, type 'fixboot' (no quotes) > once you get a success message, type 'exit' (no quotes) > and reboot.

Another option is to download and burn [hiren's CD]("http://www.hiren.info/pages/bootcd") which has MBR tools in it.  

2.  Do you plan to install a windows OS?  If so, just install fresh.

3.  Do you plan to install a linux distro (whether ubuntu or otherwise), post your specs and I'm sure the forum can come up with suggestions.

Regards,

---

