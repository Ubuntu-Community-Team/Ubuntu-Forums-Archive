---
title: "Lost Ubuntu after grub rescue"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by sheriff_009 on 2010-08-30
Hi,

I m using a Toshiba 64-bit m/c. It was loaded with Windows 7 and I loaded Ubuntu as well. I wanted to partition windows drive where the problem actually start. Upon partitioning using a partition software, I got the grub rescue error.
Then I found below steps in one of the forms and followed the same.
I was able to retrieve windows 7 safely, but my laptop is directly booting to windows now and not asking for an option to boot to Ubuntu.

Here are steps I had followed...
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Now I know I format existing Ubuntu partition and reinstall it. But I dont want to do that :( as I had got lot of customization and software installed. Dont want to lose them all :(

Appreciate if you can help me to boot back to Ubuntu..

Thanks
Shariff

---

### Post by bcbc on 2010-08-30
Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by sheriff_009 on 2010-08-30
Hi, Please find the attached results.

Thanks
Shariff

---

### Post by bcbc on 2010-08-30
It looks like you just need to reinstall the grub bootloader.

Boot from a live CD and run the following:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Reboot.

EDIT: Your ubuntu partition changed from /dev/sda5 to /dev/sda6 when you edited your partitions. Now that shouldn't be a problem as there is a UUID override in grub. But if it is a problem, then just edit the first grub entry (when the grub menu appears hit 'e'), then change (hd0,5) to (hd0,6) and hit CTRL+X to boot.

Once you've booted, run 
```
sudo update-grub
```

---

### Post by sheriff_009 on 2010-09-01
This worked, thanks a lot.

When I m booting my laptop, I would like to default it to Windows 7.

As of now it defaulting it to Ubuntu (#1). Can you please suggest me a method to change it windows (#7)

Shariff

---

### Post by bcbc on 2010-09-01
> **sheriff_009 said:**
> This worked, thanks a lot.

When I m booting my laptop, I would like to default it to Windows 7.

As of now it defaulting it to Ubuntu (#1). Can you please suggest me a method to change it windows (#7)

Shariff
I like this guide [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

However, you have to do a little work. But once it's setup it works without additional maintenance. 

If you want the easy method, you can just install and run startupmanager and set the default to windows - but note that you will have to rerun this every time a new kernel is installed or removed.

---

