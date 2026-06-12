---
title: "Repartitioning disk for Ubuntu"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2010-05-19
I have finally bought myself a new laptop, HP DV6-2113sa. It comes with Win7 which I intend to keep for a while (though do not know why as I have been using my old laptop with only Ubuntu installed for the last 5 years and had a need for Windows only a few times). Anyway, the laptop's disk has 4 partitions: SYSTEM (200Mb) with a boot flag, the main one (450Gb), RECOVERY(13.5Gb) and HP_TOOLS (100Mb). As all the partitions are primary I cannot create a new partitions for Ubuntu. I wonder if I can repartition the disk and preserve the ability to recover Windows if something wrong happens to the current Win7 installation. Any advice is welcome.

---

### Post by darkod on 2010-05-19
There were couple of threads here with exact situation on HP laptop.

Personally, I think the HP_TOOLS is not needed, but it would be up to you if you want to delete it. One person deleted both the HP_TOOLS and Recovery, and it worked out fine.

The main reason the recovery partitions are useless IMHO is because most of them destroy all partitions on the laptop and create the setup as from factory. Even if your win7 gets corrupted, no need to destroy everything trying to recover it.

Another option: the recovery partition offers possibility to create rescue DVDs from it, and after that you can delete it. So even keeping HP_TOOLS would be fine in that case, you only need to create one extended partition for ubuntu. Actually creating the DVDs and getting rid of Recovery was also suggested by HP Support to a user on one of the threads. Not sure if there is procedure about this in the user manual or where...

---

### Post by srs5694 on 2010-05-19
> **darkod said:**
> Another option: the recovery partition offers possibility to create rescue DVDs from it, and after that you can delete it. So even keeping HP_TOOLS would be fine in that case, you only need to create one extended partition for ubuntu. Actually creating the DVDs and getting rid of Recovery was also suggested by HP Support to a user on one of the threads. Not sure if there is procedure about this in the user manual or where...

This is what I recommend doing. I don't know how the names map onto your system, but I did this with a Toshiba laptop I bought a few months ago. The partition I ended up deleting was about 10GB in size, so that may help you spot the right one. While I was acting as a human disc-changer, I wrote a letter to Toshiba telling them how cheap I thought they were for not just including a rescue DVD. I recommend you do the same; the manufacturers will keep pulling this garbage for as long as customers accept it without comment.

---

### Post by darkod on 2010-05-19
> **srs5694 said:**
>  I wrote a letter to Toshiba telling them how cheap I thought they were for not just including a rescue DVD.

I'm not sure if this is the manufacturers being cheap, or MS thinking that by not including OS Install DVD they will stop piracy.

Having the install dvd to help you repair your OS is crucial. Especially when paying the (not so cheap) license for it. And by repair I don't mean the recovery partition wiping your whole hdd. :)

On the other hand, I wouldn't be surprised either if really the manufacturers are trying to save 50cents on a dvd. :confused:

---

### Post by srs5694 on 2010-05-20
> **darkod said:**
> [quote=srs5694]I wrote a letter to Toshiba telling them how cheap I thought they were  for not just including a rescue DVD.I'm not sure if this is the manufacturers being cheap, or MS thinking that by not including OS Install DVD they will stop piracy.[/QUOTE]

I cc:ed my letter to Microsoft, too. ;)

If it were just for my personal use, I'd never boot Windows again. I write about computers and do consulting for a living, though, so I do sometimes need to boot Windows. I also sometimes have to re-install OSes, juggle hardware, etc., which makes Microsoft's restrictions a real pain, and the lack of a proper recovery DVD is unacceptable to me. It's tempting to use a cracked pirate copy just to avoid the need to type in those obnoxious registration codes and avoid all the other obstacles Microsoft puts in place. (I don't do so, but it is *tempting.*)

---

### Post by foxy123 on 2010-05-21
Thanks a lot for advice. I have created 3 recovery DVDs and removed the RECOVERY partition. I decided to leave HP_TOOLS as it's only 200Mb.Now I am going to shrink the main partition and create ext4 partitions for Ubuntu. Windows currently takes 30Gb, I wonder how much should I leave to it. Would 35Gb be enough?

---

### Post by cybrsaylr on 2010-05-21
> **foxy123 said:**
>  Would 35Gb be enough?

35 GB is plenty of room.
I've run Ubuntu on 15 GB with no problems whatsoever, using any other partitions I have for storage.

---

### Post by darkod on 2010-05-21
> **foxy123 said:**
> Thanks a lot for advice. I have created 3 recovery DVDs and removed the RECOVERY partition. I decided to leave HP_TOOLS as it's only 200Mb.Now I am going to shrink the main partition and create ext4 partitions for Ubuntu. Windows currently takes 30Gb, I wonder how much should I leave to it. Would 35Gb be enough?

If you can spare the space, give it 40-45GB. If it's 30GB now and you have all your software mainly installed, I don't see it growing much more. But it's better to be on the safe side. And windows can grow from nowhere... :)

---

### Post by foxy123 on 2010-05-21
> **darkod said:**
> If you can spare the space, give it 40-45GB. If it's 30GB now and you have all your software mainly installed, I don't see it growing much more. But it's better to be on the safe side. And windows can grow from nowhere... :)

thanks a lot!

---

### Post by gorski on 2010-09-14
I have the same lap and I had the same problem with **freeware **partitioning tools, as they said they couldn't create another Primary partition [MBR limitation, allegedly]. Not so, if you work around it...

I used Partition Wizard Home Edition [freeware] to simply reduce the main partition to 100GB for W7. Just slide the "limits" to a desired partition size and apply.

Then, I went to Admin Tools in W7 -> Comp management -> and created a storage partition of 300GB. I left around 48 GB "unallocated" for Ubuntu 10.10, when it comes...):P

---

### Post by srs5694 on 2010-09-14
> **gorski said:**
> I have the same lap and I had the same problem with **freeware **partitioning tools, as they said they couldn't create another Primary partition [MBR limitation, allegedly]. Not so, if you work around it...

I used Partition Wizard Home Edition [freeware] to simply reduce the main partition to 100GB for W7. Just slide the "limits" to a desired partition size and apply.

Then, I went to Admin Tools in W7 -> Comp management -> and created a storage partition of 300GB. I left around 48 GB "unallocated" for Ubuntu 10.10, when it comes...):P

Please post the output of "sudo fdisk -lu" on the disk in question. That will explain what happened in your case, although it may require translation from computerese into English. I guarantee you, though, it was *not* because Partition Wizard was able to create more primary partitions than other tools. The 4-primary-partition limit is a *hard limit* in the basic MBR data structures. Check [the Wikipedia entry on MBR](http://en.wikipedia.org/wiki/Master_boot_record) for details of its capabilities and limitations. Note in particular the "Structure of a Master Boot Record" table near the top of that entry, which specifies *precisely four* MBR entries.

---

### Post by gorski on 2010-09-26
How do you explain that I managed to do it, after all...?!? Just as I described above...
 
On the other hand, I can't go back in time and do what you ask, can I?
 
Besides, it was done in Windows. All of it.
 
I am waiting for 10.10 to install.
 
This was just prep.
 
Cheers!

---

### Post by srs5694 on 2010-09-27
[quote=gorski]How do you explain that I managed to do it, after all...?!? Just as I described above...[/quote]

I explain it as your misunderstanding what happened or how your disk was configured at the start. That's why I asked for the fdisk output; it'll show what the disk looks like now, and since your claim is that you've now got more than four primary partitions, the fdisk output will clarify what you *really* have. (Of course, if you've since repartitioned again or gotten rid of the computer, you can't show me what I'm asking for; but you didn't mention that in your earlier message.)

---

