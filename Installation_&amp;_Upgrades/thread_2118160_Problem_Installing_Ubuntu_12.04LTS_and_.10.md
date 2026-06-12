---
title: "Problem Installing Ubuntu 12.04LTS and .10"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by JpArcher on 2013-02-20
Okay, so all day I've been trying to install Ubuntu 12.10 on my old dell pc (1GB ram, intel Pentium 4)I've burnt the iso file to a CD using my windows 8 laptop I've made about 5 copies throughout the day using other machines.

I get to the installer and everything is fine, until the stage it asks me for my name etc when i get a pop up error (errno 5) it says its unable to install because it might be a dodge CD or hard drive so i swapped my hard drive and made a new CD and i got the same problem. I've changed my ram too.

I've tried a chkdsk and try before install and then install and both failed to work.:(

I then thought 12.10 might be to advanced for my old pc so tried 12.4 and got the same problem. Now I'm stuck between putting xp on :( or wasting whats left of my day trying to fix this.

**Hope someone can help.**:D

---

### Post by carl4926 on 2013-02-20
Are you saying you have verified the media is good?

Notice the option to check disk for defects
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.43.28.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.43.28.jpg)

---

### Post by JpArcher on 2013-02-20
I'll Check now

---

### Post by JpArcher on 2013-02-20
Just checked it and it said 1 error found, I don't understand how though as i downloaded it from the ubuntu website and burned it with windows iso burner and verified the disks. 

Any suggestions?

---

### Post by carl4926 on 2013-02-20
I download with torrent, as it will auto check the chunks.
Mind I don't use windows at all

Imageburn (you can get it at filehippo)

Burn dead slow speed

---

### Post by carl4926 on 2013-02-20
> **carl4926 said:**
> I download with torrent, as it will auto check the chunks.
Mind I don't use windows at all

Imageburn (you can get it at filehippo)

Burn dead slow speed

Oh and I only use quality media, such as Verbatim
Although now I most use USB booting
Unetbootin is probably easiest in windows for USB

---

### Post by mörgæs on 2013-02-20
> **JpArcher said:**
> 
I then thought 12.10 might be to advanced for my old pc so tried 12.4... 

12.10 is not too heavy for this computer, but Ubuntu is. I would go for X/Lubuntu 12.10.

Before focusing on the install you should aim for getting a live boot running for some time.

---

### Post by JpArcher on 2013-02-20
I am using Verbatim CD's, I re-downloaded it and burned it and then checked it and i have no errors, so i went to install it and got slightly past the old point and then got the same error.

[https://www.dropbox.com/s/p87hgsntb00svjc/20130220_175447.jpg](https://www.dropbox.com/s/p87hgsntb00svjc/20130220_175447.jpg)

sorry for the bad pic 

I've installed xp on it now and it works fine! I even ran wubi and that went through the installation process and stopped in the same place.

Its so frustrating

---

### Post by mörgæs on 2013-02-20
The **errno 5 input/output error** should be possible to google. There are lots of threads dealing with it - unfortunately there could also be many reasons for it.

Since you have a working Windows I would begin with upgrading your BIOS. It's normally an easy task on a Dell.

After that you could check if it's possible to boot from USB. Push F12 early in the boot process while the USB stick is attached.

If it does not work I recommend installing a [minimal Buntu]("http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/mini.iso") from a CD. After that you install Lubuntu with

```
sudo apt-get install lubuntu-desktop
```

The benefit of using a minimal install is that you just have to read 15-20 MB from the CD.

---

