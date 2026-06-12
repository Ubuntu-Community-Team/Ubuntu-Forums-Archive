---
title: "Cannot Mount CD/DVD Drive after upgrade"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by klezfire on 2008-09-04
Hello, I am quite new to Ubuntu and all of linux for that matter however I am highly experienced with Windows.  Anyways here is my problem...  I tried to install Ubuntu 8.04 using the Live CD however I couldn't get it to load blah blah blah.  So I used Ubuntu 7.10 (Fiesty) to install it on my computer and it was working "ok". My DVD Burner was working at this time.  Anyways I proceeded to upgrade to Ubuntu 8.04 which is installed right now and working GREAT excpept the fact that when I go to use my DVD Drive it says this **"Unable to mount location" "Cannot mount file"**.  Any idea to why this isn't working, I have verified my DVD Drive is physically working because I can boot off from the Ubuntu 7.10 Disc.  Any help would be greatly appreciated!

*Update* Not sure if this helps but if I click on the CD/DVD drive Icon it says "No media".

---

### Post by manishtech on 2008-09-05
Insert the CD/DVD media in the drive and when it starts spinning, type this command at the terminal and press enter

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom
```

---

### Post by Jota37 on 2008-11-21
Similar problem here... Actually, worse. It stopped mounting USB sticks too.

I have Ubuntu 8.04, which was working fine until some time ago. This week, when I tried to copy some data to USB sticks, none of them would not mount, either automatically or from the command line -- and I have sticks both formatted as ext3 and FAT, but none worked. Same thing at home, with Kubuntu 8.10 (DVD's are playing though, so they might be mounting fine).

I suspect some recent upgrade (NOT of the whole system, but of some part, by the Update Manager) broke this. I'm in the process of searching the fora right now for an answer...

Thanks for your attention!
J

---

### Post by Jota37 on 2008-11-21
> **manishtech said:**
> Insert the CD/DVD media in the drive and when it starts spinning, type this command at the terminal and press enter

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom
```

By the way, that does not work for me either. I get "mount: No medium found" as the guy above. And I know the CD is good, it opens fine in a colleague's XP machine, at least.

---

### Post by lurker316 on 2008-11-22
Alright. The DVDs are not mounting for me too. But here is the interesting aspect of it all. I am running a Virtual Machine on Ubuntu 8.10 of Windows XP Pro SP3. The DVD shows up in "My Computer" in VM Windows XP, but cannot mount in Ubuntu natively!?

When I type the command the person above gave.. I get the following message:


mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I shutdown the Virtual Machine.. Tried the command now and still no Go. Let me try a restart.

I got it working.
Here's how I got the DVD mounted.

*I inserted a standard ISO9660 DVD in the drive. It mounted it successfully.
*I then inserted a UDF 1.02 formatted DVD in the drive. This time it mounted it successfully. Hmm...

---

### Post by yergeht on 2009-03-25
I have this same issue... except that when I type the command **sudo mount -t iso9660 /dev/scd0 /media/cdrom** I get the same message as the fellow above, klezfire. but the system tells me that I have just inserted a blank dvd and asks me what I would like to do... except that I still can't make a dvd... WTH?

---

### Post by deboh on 2010-02-22
for me... i used what the guys said above **sudo mount -t iso9660 /dev/scd0 /media/cdrom** and it seemed to work, at least i could mount my dvd.

well i dunno, if this works now permanently or i have to repeat it everytime.

---

