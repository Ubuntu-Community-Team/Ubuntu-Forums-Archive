---
title: "Do I follow guide images or doI follow default setting automatically set up by Rufus?"
date: 2023-01-30
forum: Installation &amp; Upgrades
---

### Post by finemouche on 2023-01-30
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291687&stc=1[/IMG]
Hi ! ):P
In the image tuto/guide, it's FAT32 the default, in my use of Rufus it's set up by default in FAT that's all / short / without anything else / Without adding anything more (c'est tout / tout court / sans rien d'autre / Sans rien ajouter de plus)(1)
So i keep FAT or i switch to FAT32 ? what are the risks of a bad choice ? 

Maybe it's related to my use of a 4Go(2)  usb key 2.0

p.s : For "cluster size", 64 kb is my only option.


(1) I will get help me, so i can at least learn you a little of french in exchange :P
(2) Rufus say/show 3.9Go available. Whereas I just byu it, but the info on the product say : "A portion of the storage capacity is used for system files and maintenance"

---

### Post by yancek on 2023-01-31
I don think there is any risk, either should work although mostly FAT32 is used in these situations.  FAT is sometimes used for either FAT16 or FAT32 and VFAT is synonymous with FAT32.  Either shoud work but I've never used Rufus so...

---

### Post by jamesmillere on 2023-01-31
Hi,


It depends on what you are trying to do. If you are trying to install an operating system on a computer, you should follow the guide or instructions provided by the operating system. If you are using Rufus to create a bootable USB drive, the default settings should be sufficient for most users. However, if you have specific requirements or preferences, you can change the settings in Rufus to match your needs.


It's always a good idea to read the documentation and understand the options and settings available in the tool you are using. This will help you make informed decisions and ensure that you are using the tool in the way that best fits your needs.


Thanks

---

### Post by finemouche on 2023-01-31
i'm using Rufus to create a bootable USB drive

i read since hours about FAT, FAT32, large FAT, ExFAT, Virtual FAT, NTFS, clusters .
I don't want bricks / make unusable the USB i just bought.
I want understand why it set ut by default on FAT with a cluster of 64ko with no others sizes proposed.
64ko is huge waste if ubuntu have many little files.

FAT32 4ko [COLOR=#008000]seems / looks like[/COLOR] the best choice but i'm not sure, so i would DL this tool : [https://www.lprp.fr/1999/10/cluster/](https://www.lprp.fr/1999/10/cluster/) but it was create on 1999 and [FONT=Arial]Malwarebytes Browser Guard don't want i DL the app version (I think he is a honest person, but i still fear), i could only DL the shell extension version but i don't know how to use it, the cluster.htm say the same things than the link i shared. and the cluster.inf(o) file juste say "[/FONT]POUR L'AIDE CONSULTER CLUSTER.HTML" (FOR HELP SEE CLUSTER.HTML), there are a .dll and a .Reg but i'm fear to click on one of them.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291697&stc=1[/IMG]

it's 4:21, i work at 8:30, i need to go sleep a little, i'm sorry i will continue my search when i can. (Or do you know a more modern similar cluster calculator ? Or can i just copy a small file in the vierge USB and see what is the size of the cluster, but since it will be formatted to receive ubuntu, having a vierge one is maybe optimal. (maybe it doesn't matter)
4:32 :frown: zZzzZ

---

### Post by oldfred on 2023-01-31
I do think it is your 4GB flash drive.

But Ubuntu is now over 4GB, so you need a larger drive and then use FAT32.
Also best not to use USB2 flash drive, that will be very slow. Even if older system with USB2 port, USB3 flash drive is a bit faster. 
I stopped buying USB2 flash drives years ago, when I still only have USB2 ports on old BIOS only system.

If old system, you may need a lighter flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I use Kubuntu on all my systems which is more midweight, but did install on an old system that would not install Ubuntu. It installed Ubuntu server & I was able to add lightweight gui. Bit surprised that old system worked with Kubuntu, expected it would need a light weight flavor.

---

### Post by finemouche on 2023-02-01
I didn't tried to put ubuntu on the UFD, i still on the selecting UFD and ISO
i want to test on a ASUS with a CPU intel core I7 and GTX 750m, where windows start/begin to be very low(1), and install if the test is conclusive.

(1) can the test(2) of ubuntu be slow since it's maybe virtually(2) running on windows ?
(2) :
[LIST]
[*]Test out the Ubuntu desktop experience without touching your PC configuration (from [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#5-write-the-iso](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#5-write-the-iso) )
[/LIST]
I have to do administrative paperwork, i BRB when i can.

p.s : So what can be the use of my 4Go 2.0 USB drive ? Bios update of Windows ? (i normally use @bios from Gigabyte App center, but i can try from USB Flash Drive (aka UFD(3))

(3) i say it for me to train my memory, because the day before yesterday [i didn't knew/known / I didn't yet know] what UFD meant, because as french I said "(Clé) USB" that i translate to "USB (key)"

---

### Post by MAFoElffen on 2023-02-01
> **finemouche said:**
> p.s : So what can be the use of my 4Go 2.0 USB drive ? Bios update of Windows ? (i normally use @bios from Gigabyte App center, but i can try from USB Flash Drive (aka UFD(3)"

Yes. Try an 8GB USB 3.x USB drive. Ubuntu ISO will not fit into 4GB.

---

### Post by finemouche on 2023-02-02
i bought :
-the 4Go 2.0 UFD for ubuntu,  
-a 32Go 3.0 for windows 10(1) and 
-a 64Go 3.0 UFD for store during the change of OS, the data of the laptop where i will put Ubuntu, 
so i need byu another usb key >_< (i think i have a 8Go UFD somewhere, but it will be, i'm sure at 80%, a 2.0)

(1) and 32Go is maybe overkill for installing Ubuntu.

---

### Post by mark-chandler on 2023-02-02
I used a 32GB thumb drive to install 22.0.4, and it was definitely overkill (space-wise). An 8GB USB would have been fine.

---

