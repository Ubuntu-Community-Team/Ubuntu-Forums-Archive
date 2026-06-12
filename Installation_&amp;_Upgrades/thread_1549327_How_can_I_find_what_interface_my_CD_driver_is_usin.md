---
title: "How can I find what interface my CD driver is using?"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Inder on 2010-08-09
I'm in the process of installing the newest version of my BIOS driver and I have to use FreeDOS because I don't have windows (I'm using Ubuntu 9.10). So I'm following [AndrejaKo's advice]("http://superuser.com/questions/170624/how-do-i-install-a-new-bios-driver-on-ubuntu-9-10-karmic-koala"). The problem is that when FreeDOS comes up and I choose option #5: FreeDOS Live CD only, I don't end up with the same screen as AndrejaKo's. Rather, I get this:
```

UMB's unavailable!
XCDROM V2.3, 7-24-2006.
Driver name is "FDCD0000".
No CD-ROM drive to use; XCDROM not loaded!
FreeCom version 0.84-pre2 XMS_Swap [Aug282006 00:29:00]
Cannot open CD driver FDCD0000. SHCDX33A cannot load!
There is no CDROM, or the wrong CD-ROM!

A:/>

```

I've posted a question on [superuser]("http://superuser.com/questions/173511/what-does-the-following-error-message-mean-in-freedos") and got the following comment: How is the CD drive connected to the PC - which interface?

But I don't know how to check that information. Any help?
Thanks very much to all of you in advance!

---

### Post by corrytonapple on 2010-08-09
Go to **System>Administration>Disk Utility. **Then look in the left hand column, you will see SATA or IDE host adapter, whatever is below that is either SATA or IDE. See pictures.

---

### Post by Inder on 2010-08-09
I don't see anything called SATA or IDE host adapter.
See pictures:

---

### Post by corrytonapple on 2010-08-09
Can you go to File, get more info or something like that while the drive is selected? Can you right click the drive to get more info? What are your system specs? How old is it?

---

### Post by Inder on 2010-08-09
Neither pressing on File nor right-clicking bring up any interesting options. I am running Ubuntu 9.10 Karmic Koala on an Acer Aspire 5536-5519. I don't believe it's very old...

---

### Post by corrytonapple on 2010-08-09
No, I just forgot that you were running 9.10. Let me look around a bit.

---

### Post by corrytonapple on 2010-08-09
Try This: But you will not see the password for security reasons.
```

sudo apt-get install hardinfo

```Then:
```

hardinfo

```
That will install a hardware spec fetcher. Typing hardinfo will launch it.
Now go to where the screenshots show you. Report back what you get from those respect rows. Be sure to use ```

``` tags at the beginning and end of what you get back.:)

---

### Post by Ginsu543 on 2010-08-09
There may be another way. If your computer supports booting from a USB thumb drive, you can use [_UNetbootin_](https://launchpad.net/~gezakovacs/+archive/ppa) to basically create a LiveUSB (rather than a LiveCD) of FreeDOS.

Go to the link, add the PPA to your system and install UNetbootin using Synaptic. When you run UNetbootin, it will allow you to create a FreeDOS LiveUSB. You can either click on the == Select Distribution == radio button and choose FreeDOS (in which case UNetbootin will download the necessary iso for you) or since you already have the iso, just click on "Diskimage" and point it to where your iso is located. Select your USB thumb drive under "Drive:" and hit "OK."

Once you have a working LiveUSB thumb drive, just boot with it and you should get to the screen you want to get to.

---

### Post by Inder on 2010-08-10
> **corrytonapple said:**
> Try This: But you will not see the password for security reasons.
```

sudo apt-get install hardinfo

```Then:
```

hardinfo

```
That will install a hardware spec fetcher. Typing hardinfo will launch it.
Now go to where the screenshots show you. Report back what you get from those respect rows. Be sure to use ```

``` tags at the beginning and end of what you get back.:)

It appears hardinfo is a GUI, so no need to use code for what I get back. Actually, the only news I can find is that my CD is a SCSI disk. Is that the name of the interface? See attached screenshot...

---

### Post by Inder on 2010-08-10
> **Ginsu543 said:**
> There may be another way. If your computer supports booting from a USB thumb drive, you can use [_UNetbootin_](https://launchpad.net/~gezakovacs/+archive/ppa) to basically create a LiveUSB (rather than a LiveCD) of FreeDOS.

Go to the link, add the PPA to your system and install UNetbootin using Synaptic. When you run UNetbootin, it will allow you to create a FreeDOS LiveUSB. You can either click on the == Select Distribution == radio button and choose FreeDOS (in which case UNetbootin will download the necessary iso for you) or since you already have the iso, just click on "Diskimage" and point it to where your iso is located. Select your USB thumb drive under "Drive:" and hit "OK."

Once you have a working LiveUSB thumb drive, just boot with it and you should get to the screen you want to get to.

Tried it , but when I choose Default in the UNetBootin menu, it just says bad kernel image or something like that, so I never even got to the freeDOS menu that way.

---

### Post by corrytonapple on 2010-08-10
> **Inder said:**
> It appears hardinfo is a GUI, so no need to use code for what I get back. Actually, the only news I can find is that my CD is a SCSI disk. Is that the name of the interface? See attached screenshot...
I would think. SCSI in laptops in uncommon. SCSI is expensive and is for servers. I'm sorry if it appears I don't know what I am doing. All of this software works for me. You can now do one of four things. 1. Assume as I do that SCSI is expensive for that laptop and say it runs SATA. 2. It does use SCSI and thats what you should tell the guide manager. 3. Burn a live CD and go to the Disc Utility Program and look their. Open up where the Laptop Hard Drive is and see if its a thin cable or a 80 pin cable.
I am sorry again if it seems as if I don't know what I'm doing.:)

---

