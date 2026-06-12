---
title: "First steps... Install Ubuntu with Easy BCD Easy"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by Tuexnovia on 2011-03-20
HELLO WORLD xDDD I'm a Spanish guy who is going to start learning all or try it about this S.O because i want to improve my second profession and find any job doing something about computers... Then I'll try to make a huge effort even with my horrible English but like this is like I'm going to learn...


Ok my first question is... After I'll read the forum because it will take time to learn.
At least I know a lot about computers but for me this new S.O it will be new then I need to be sure of this first steps...


I have got already EasyBCD 2.0 In my Windows 7 ultimate 64 raid 0. xDDD
Then I heard about I would have to create a partition for my new S.O (I can't wait)
that is this ubuntu-10.10-desktop-amd64.iso

So what would you recommend me?

-Add new entry.
-Linux/BSD.
-WICH kind of partition name? I mean -Grub lilo etc...-
-And where?

Drive 0
partition 1 100mb ntfs
partition 2 C:\ 1863mb as ntfs

I don't know if I have to do it like this but from what little I've read I think is the best way...
I hope it was clear...



THANKSSSSS and HELLO My first POST...

---

### Post by Hedgehog1 on 2011-03-20
> **Tuexnovia said:**
> HELLO WORLD xDDD I'm a Spanish guy who is going to start learning all or try it about this S.O because i want to improve my second profession and find any job doing something about computers... Then I'll try to make a huge effort even with my horrible English but like this is like I'm going to learn...


Ok my first question is... After I'll read the forum because it will take time to learn.
At least I know a lot about computers but for me this new S.O it will be new then I need to be sure of this first steps...


I have got already EasyBCD 2.0 In my Windows 7 ultimate 64 raid 0. xDDD
Then I heard about I would have to create a partition for my new S.O (I can't wait)
that is this ubuntu-10.10-desktop-amd64.iso

So what would you recommend me?

-Add new entry.
-Linux/BSD.
-WICH kind of partition name? I mean -Grub lilo etc...-
-And where?

Drive 0
partition 1 100mb ntfs
partition 2 C:\ 1863mb as ntfs

I don't know if I have to do it like this but from what little I've read I think is the best way...
I hope it was clear...



THANKSSSSS and HELLO My first POST...

Welcome to the Ubuntu forums!

I noticed you are running RAID O on you current system.  So lets be sure that Ubuntu is OK with your setup.

Please burn the .iso to a CD (an .iso file is a whole CD compressed into the smallest file we can squeeze it into). You will need to burn the CD in 'Burn From ISO' mode; you may need burner software to do this (there are many free ones).

Then boot off of the 'LiveCD', and select 'TRY'.  This will give you a chance to make sure Ubuntu can read your RAID array DOS data - please use the 'places' menu and make sure you can read your DOS partitions.

If your RAID array is a software raid, you will not be able to see it in the 'places' menu; and cannot dual boot Ubuntu.  Instead you will have to install Ubuntu as a Virtual Machine using the free Virtual Box software.  But that works good, too.

***The Hedge***

:KS

p.s. VBox 'Virtual Machines' will also let you install many different Linux versions (we call them 'distros'; short for '**Distr**ibuti**o**n**s**'); it is great for learning.  Here is what my Vbox looks like:

[IMG]http://img862.imageshack.us/img862/3982/vboxmanager.png[/IMG]

---

### Post by Tuexnovia on 2011-03-20
> **Hedgehog1 said:**
> Welcome to the Ubuntu forums!

I noticed you are running RAID O on you current system.  So lets be sure that Ubuntu is OK with your setup.

Please burn the .iso to a CD (an .iso file is a whole CD compressed into the smallest file we can squeeze it into). You will need to burn the CD in 'Burn From ISO' mode; you may need burner software to do this (there are many free ones).

Then boot off of the 'LiveCD', and select 'TRY'.  This will give you a chance to make sure Ubuntu can read your RAID array DOS data - please use the 'places' menu and make sure you can read your DOS partitions.

If your RAID array is a software raid, you will not be able to see it in the 'places' menu; and cannot dual boot Ubuntu.  Instead you will have to install Ubuntu as a Virtual Machine using the free Virtual Box software.  But that works good, too.

***The Hedge***

:KS

p.s. VBox 'Virtual Machines' will also let you install many different Linux versions (we call them 'distros'; short for '**Distr**ibuti**o**n**s**'); it is great for learning.  Here is what my Vbox looks like:

[IMG]http://img862.imageshack.us/img862/3982/vboxmanager.png[/IMG]
1. Mi raid0 is from BIOS

2. I have already my UBUNTU in a USB I can see the tipical screen black when I turn on my computer... with UBUNTU LOGO I did put USB first start and bla bla...

I know about computers. I mean, Not about UBUNTU and UNIX because this is that i want to learn how to survive in another S.O xDDDD

> **Hedgehog1 said:**
> Please use the 'places' menu and make sure you can read your DOS partitions.

EDIT: So... I am inside of the O.S but just because I have put RUN from USB, can I install it...
cos I can not find the option that you told me...

But I think I could do it from here i give you a capture from my computer...
_[IMG]http://img25.imageshack.us/img25/1193/sinttulo4ok.jpg[/IMG]_

I will wait thanks anyway. xDDD

---

### Post by Hedgehog1 on 2011-03-20
I think pictures are best for the moment.

To be clear, you were able to boot off the Ubuntu 'LiveUSB', and you saw this:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

And if you pressed TRY, you are able to get here:

[IMG]http://img202.imageshack.us/img202/5771/small07trygui.png[/IMG]

If so can you see the DOS/NTFS partitions in the 'Places' menu from inside Ubuntu?  If you can, you can safely install Ubuntu as a dual boot.

So from the Ubuntu 'LiveUSB', can you see your DOS/NTFS partitions in the 'Places' menu?

***The Hedge***

:KS

---

### Post by Tuexnovia on 2011-03-20
> **Hedgehog1 said:**
> I think pictures are best for the moment.

To be clear, you were able to boot off the Ubuntu 'LiveUSB', and you saw this:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

And if you pressed TRY, you are able to get here:

[IMG]http://img202.imageshack.us/img202/5771/small07trygui.png[/IMG]

If so can you see the DOS/NTFS partitions in the 'Places' menu from inside Ubuntu?  If you can, you can safely install Ubuntu as a dual boot.

So from the Ubuntu 'LiveUSB', can you see your DOS/NTFS partitions in the 'Places' menu?

***The Hedge***

:KS


Yes I can sorry... Yesterday I was THERE also, and I was checking my 3 Hard drive I didn't know you were talking about this... Really sorry

So the best way to keep my MBR save is doing the installation?

1.Like this
[IMG]http://img25.imageshack.us/img25/1193/sinttulo4ok.jpg[/IMG]

Or from ubuntu installation?

Install alongside other operating system. (?)
erase and use the entire disk (x)
Specify partitions manually (?)

But I'd need to create a partition?
 
Because this step is the most important...  Sorry and THANKSS xDDD

---

### Post by Tuexnovia on 2011-03-20
Please GUYS... I'm in my day OFF I can't WAIT to install it xDDDD

I beg you a clue xDDDDDD

---

### Post by Hedgehog1 on 2011-03-20
Good.  I think we now know that your BIOS based RAID shows itself as a hard drive to Ubuntu.  So it is safe to do a dual boot.

When Windows looks at partitions, it looks at them this way (this is an example from an HP laptop):

[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]

When we look at the same partitions in Linux, we think of them like this:

[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]

In this example, C: = /dev/sda2

* /**dev**/sda2 means: **dev**ice
* /dev/**sd**a2 means: **S**CSI mass-storage **d**river (Linux sees most hard drive as if they were SCSI, even though in real life the can be SCSI, SATA, PATA (IDE), USB)
* /dev/sd**a**2 means: First device is letter '**a**', second device is letter '**b**', third device is letter '**c**'
* /dev/sda**2** mean: **2**nd partition on this drive.

So, this mean we want to install Ubuntu in position: /dev/sda3

However, the MBR style of partitioning only allow 4 primary partitions: sdx**1**,sdx**2**,sdx**3** & sdx**4**.

Because we may need more than two partitions for Linux, we create an 'extended' partition, and then put as many logical partitions in it as we need:

/dev/sda1 (Boot)
/dev/sda2 (NTFS, C:)
/dev/sda3 (Extended)
__/dev/sda5 - formatted as linux ext4 - '/' (also called root)
__/dev/sda6 - Linux Swap (this is like the Windows pagefile.sys)

This is what this looks like on that same HP computer, after sda3 was removed and a new extended sda3 was created.

In Linux (using gparted - **G**nome **PART**ition **ED**itor):

[IMG]http://img269.imageshack.us/img269/2134/hp4partitions15o.png[/IMG]

In the Linux 'Disk Utility':

[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]

In my next post I will walk you through this example - you can ignore the /dev/sda4, you don't have that partition.

---

### Post by Hedgehog1 on 2011-03-20
Using gparted from the 'liveUSB':

[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button to make the change real...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-03-20
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be ext4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually sets itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-20
You do need to know that Ubuntu will always install GRUB (**GR**and **U**nified **B**oot loader) so at boot up you will get a GRUB menu that looks something like this:

[IMG]http://img860.imageshack.us/img860/5730/small37grub2ndtime.png[/IMG]

While this can be altered using easy BCD, for now please use the GRUB menu so we can understand your questions better.

***The Hedge***

:KS

---

### Post by Tuexnovia on 2011-03-20
> **Hedgehog1 said:**
> You do need to know that Ubuntu will always install GRUB (**GR**and **U**nified **B**oot loader) so at boot up you will get a GRUB menu that looks something like this:

[IMG]http://img860.imageshack.us/img860/5730/small37grub2ndtime.png[/IMG]

While this can be altered using easy BCD, for now please use the GRUB menu so we can understand your questions better.

***The Hedge***

:KS

amazing all clear xD butttttt... Just one more question.

Where I have to install the boot loader?
In hard drive root or where ? 

Thanksss tonight I'm gonna feel like a properly noob...

Yeeaaa... I know it takes time to learn about it but I had to do it.

---

### Post by Hedgehog1 on 2011-03-20
In your case (and for most Ubuntu installs), you need to install the boot loader in **/dev/sda** (not sda1 or sda2; but **/dev/sda**. Just like in the picture:

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]


***The Hedge***

:KS

p.s. Your PC boots from Disk 0 (most PC's do).  Disk 0 = /dev/sda

---

### Post by Hedgehog1 on 2011-03-20
By the way; everything I am showing you can be undone (unless you overwrite an NTFS partition :D - that can only be fixed with a restore from your windows backup).  If you decide to uninstall Ubuntu and recover the disk space, I have the instructions with pictures.

***The Hedge***

:KS

> Yeeaaa... I know it takes time to learn about it but I had to do it.

We all started as Linux noobs at one time :D

---

### Post by Tuexnovia on 2011-03-20
> **Hedgehog1 said:**
> By the way; everything I am showing you can be undone (unless you overwrite an NTFS partition :D - that can only be fixed with a restore from your windows backup).  If you decide to uninstall Ubuntu and recover the disk space, I have the instructions with pictures.

***The Hedge***

:KS



We all started as Linux noobs at one time :D


I LOVE YOU THANKSSS... YEAAAAA FINALLY UBUNTU...
THANKS THANKS THANKS... And 1.000 THANKS.

---

### Post by Hedgehog1 on 2011-03-20
I am glad you have it installed!

We will look forward to watching & helping you learn more about Linux & Ubuntu.

***The Hedge***

:KS

---

