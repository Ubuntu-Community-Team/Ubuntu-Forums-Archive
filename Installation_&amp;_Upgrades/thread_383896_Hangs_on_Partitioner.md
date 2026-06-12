---
title: "Hangs on Partitioner"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by cgdoc7 on 2007-03-13
Hi everyone.  I am having an install issue for the last several weeks that I just can't get around.  I am trying to install 6.06 on a computer that I have recently upgraded.  I was able to install my 6.06 disk before so I think my problem lays with my upgrade.  I am able to install and use Windows XP without any problems.  I have been unable to install both 6.06 and OpenSUSE 10.2. I was successfully able to install Suse10.2 on my external HDD connected to my computer.  So I am wondering if it has something to do with the communication between my motherboard, internal hard drive, and the Linux installer.  I have tried more the one internal hard drive with the same problem.  I want to avoid reinstalling windows and I'm sure there is some kind of work around out there.  

The particular error i'm having is when I load the 6.06 live CD and click on the install icon, go through the time/language/username/password screens it loads the partitioner and stops. I'm left with a grey window and nothing else happens.  

My system specs are as follows: 

[[COLOR="RoyalBlue"]Gygabyte GA-965P-S3[/COLOR]]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2321") motherboard
Intel Core 2 2.13ghz processor
2gb Ram
Radeon 1650 512 mb video card
External DVD Drive connected via USB
300gb Seagate PATA drive.

In review I have tested all my hardware and it works.  I have verified my hard drive is working properly.

Thank you for your help!

Jason

---

### Post by rsambuca on 2007-03-13
It might help us if you specify what exactly you upgraded, and what you had prior to the upgrade.

---

### Post by cgdoc7 on 2007-03-13
> **rsambuca said:**
> It might help us if you specify what exactly you upgraded, and what you had prior to the upgrade.

  I upgraded pretty much everything (my board, vid card, processor, ram).  The processor was a 1.2 ghz AMD Duron.  Board was an AK77 Pro A-133 if I remember right.  Ram was 1 gig DDR and vid card was a Radeon 9600 either 128mb or 256mb (128 I think).  Hard drive was the same.  I also did not mention in the above post that I have tried more the one hard drive with the same problem.  The one I want to install on is a 300gb Seagate PATA drive.

Jason

---

### Post by cgdoc7 on 2007-03-14
Any ideas?  Could it be the fact that i'm trying to use a PATA HDD instead of a SATA HDD with my particular MOBO?

---

### Post by bulldog on 2007-03-14
If your hdd is listed in the BIOS correctly ,there shouldn't be a reason why it's not found by ubuntu.
I presume it's connected straight to the motherboard,without the use of a PCI card?

---

### Post by cgdoc7 on 2007-03-14
> **bulldog said:**
> If your hdd is listed in the BIOS correctly ,there shouldn't be a reason why it's not found by ubuntu.
I presume it's connected straight to the motherboard,without the use of a PCI card?

Correct, my HDD is connected straight to the MOBO via PATA.

---

### Post by rsambuca on 2007-03-14
Is the drive listed in your bios?

---

### Post by cgdoc7 on 2007-03-15
Yes, My HDD is listed in BIOS. Keep in mind I can install and run XP w/o problems.

---

### Post by rsambuca on 2007-03-15
I just looked up your motherboard specs.  There are compatibility problems with the JMicron controller (the Intel p965) set.  Some people have gotten it to work by disabling the controller first, but there are a lot of difficulties getting it up and running.  Search the forums for JMicron and you will find a bunch.

[[COLOR="Red"]This thread[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=234706&highlight=jmicron") is probably a good place to start looking for help.

Sorry I can't help you more.

---

