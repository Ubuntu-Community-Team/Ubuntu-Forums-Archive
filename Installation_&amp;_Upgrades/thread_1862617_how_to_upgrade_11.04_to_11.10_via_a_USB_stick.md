---
title: "how to upgrade 11.04 to 11.10 via a USB stick"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2011-10-16
I want to upgrade 11.04 to 11.10 I have downloaded alternate ISO on a USB.
In update manager GUI---> Add volume while USB is inserted and I click add volume I get 
Please insert a disk in drive.
Why is there a default assumption that some one will Upgrade from a CDROM only.
Can't it be a USB (in my case) and then I get an error
```
Error scanning the CD 
E:Unable to stat the mount point /media/cdrom/ -stat( 2: No such file or directory), E:Unable to stat the mount point /media/cdrom -stat (2:  No such file or directory),
E: failed to mount the CDROM.
```

and then I can not proceed.
I have alternate ISO of 11.10 on a USB stick and want to upgrade from the USB is it possible?

sudo do-release-upgrade is failing
[http://paste.ubuntu.com/709769/](http://paste.ubuntu.com/709769/)

can check above.
I am on 11.04
[http://paste.ubuntu.com/709770/](http://paste.ubuntu.com/709770/)

---

### Post by df747jet on 2011-10-18
Correct, it does assume you are using a CDROM drive. What I have done is mounted the .iso file virtually.

sudo mkdir /cdrom
sudo mount -t iso9660 /path/to/alternate-iso/ubuntu.iso /cdrom -o loop
sh /cdrom/cdromupgrade

The upgrader works, but it still forces you to download all the packages from online, essentially making the tool useless. Looking at past forum posts this issue has been going on since the last release. Perhaps a bug needs to be filed...

---

### Post by Bmonsterboy on 2011-10-18
Try googling for a live usb creator. LiLi is good :)

---

### Post by ubu_dynamite on 2011-10-18
Or use startup disk creator it is already installed if you have a default gnome installation.
"System->Administration->startup disk creator

---

### Post by Bmonsterboy on 2011-10-18
Does that work for USB?

---

### Post by ubu_dynamite on 2011-10-18
> **Bmonsterboy said:**
> Does that work for USB?

Yes it,s a tool to create Live USBs of Ubuntu from the Live CD or from an iso image.
[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

---

### Post by Bmonsterboy on 2011-10-18
Cool :) I had never noticed it before :)

---

### Post by raja.genupula on 2011-10-20
I am also looking for upgrading through USB , please provide me a solution.

thanks in advance

---

### Post by ubu_dynamite on 2011-10-20
> **raja.genupula said:**
> I am also looking for upgrading through USB , any one provide me a solution.

thanks in advance

"System->Administration->startup disk creator"?
The live/dvd has a upgrade option although i prefer and recommend a clean install myself.

---

### Post by raja.genupula on 2011-10-20
Hi

    Yes i have used the startup disk creator for Live USB but its not showing me any upgrade option while doing installation option .

---

### Post by ubu_dynamite on 2011-10-20
> **raja.genupula said:**
> Hi

    Yes i have used the startup disk creator for Live USB but its not showing me any upgrade option while doing installation option .

I,m getting the option right after "Preparing to install ubuntu"
1. When you install you get first "Welcome" and you choose your language
2. Preparing to install ubuntu "checks drive space and internet coonection.
3. Installation type with 4 options for me here
- Install ubuntu 11.10 along side ubuntu 11.10
- Upgrade ubuntu 11.10 to ubuntu 11.10
- Erase ubuntu 11.10 and reinstall
- Something else "For manual partitioning and resizing

I assume it's same when you do an upgrade from 11.04 to 11.10 but i,m not sure running this in virtualbox and not planning on upgrading for now not so font off loosing gnome classic

---

### Post by raja.genupula on 2011-10-20
> **ubu_dynamite said:**
> I,m getting the option right after "Preparing to install ubuntu"
1. When you install you get first "Welcome" and you choose your language
2. Preparing to install ubuntu "checks drive space and internet coonection.
3. Installation type with 4 options for me here
- Install ubuntu 11.10 along side ubuntu 11.10
- Upgrade ubuntu 11.10 to ubuntu 11.10
- Erase ubuntu 11.10 and reinstall
- Something else "For manual partitioning and resizing

I assume it's same when you do an upgrade from 11.04 to 11.10 but i,m not sure running this in virtualbox and not planning on upgrading for now not so font off loosing gnome classic

Hi 
   Thank you for replaying back. Yeah it should be like that but i have multi-Ubuntu's in my system(Xubuntu 11.10 and Ubuntu 11.04) and i wanna take my Ubuntu 11.04 to 11.10 . I think its not gonna give such option of upgrading from USB with multi-Ubuntu's.

---

### Post by aoniumo on 2011-10-21
> **df747jet said:**
> Correct, it does assume you are using a CDROM drive. What I have done is mounted the .iso file virtually.

sudo mkdir /cdrom
sudo mount -t iso9660 /path/to/alternate-iso/ubuntu.iso /cdrom -o loop
sh /cdrom/cdromupgrade

The upgrader works, but it still forces you to download all the packages from online, essentially making the tool useless. Looking at past forum posts this issue has been going on since the last release. Perhaps a bug needs to be filed...


I get this error:

Traceback (most recent call last):
  File "/tmp/tmp.jajiJjzHbq/oneiric", line 7, in <module>
    sys.exit(main())
  File "/tmp/tmp.jajiJjzHbq/DistUpgradeMain.py", line 172, in main
    logdir = setup_logging(options, config)
  File "/tmp/tmp.jajiJjzHbq/DistUpgradeMain.py", line 77, in setup_logging
    os.mkdir(backup_dir)
OSError: [Errno 13] Permission denied: '/var/log/dist-upgrade//20111021-1756'

---

