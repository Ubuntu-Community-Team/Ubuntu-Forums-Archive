---
title: "Install Ubuntu mode in VMPlayer"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Mach101 on 2012-02-24
Hi all,
I want to install Ubuntu mode in my Windows 7 through VMware Player. I have updated the VMware Player to 4.0.1 so it should be able to install the Ubuntu, but when I choose the iso file which I downloaded from ubuntu.com for my 64 bit laptop, it keeps on showing that it can not detect that its a Ubuntu iso file.

I even ignored it and went further to install it, but nothing happens. 
I will hardly choose Virtual box as a second option as I already have XP mode also installed and like to have it kept in one place.

Appreciate helps for installing in VMware Player.

---

### Post by azmyth on 2012-02-24
I would check the md5 checksum from your iso file with the one from the Ubuntu download page to make sure you didn't get a bad file.

Also, you need to create the Virtual container then you need to select the iso under the storage tab and then tie the iso to the CD/DVD. Under the Controller in the middle it should list the Ubuntu iso if dome properly.

---

### Post by Mach101 on 2012-02-24
> **azmyth said:**
> I would check the md5 checksum from your iso file with the one from the Ubuntu download page to make sure you didn't get a bad file.

Also, you need to create the Virtual container then you need to select the iso under the storage tab and then tie the iso to the CD/DVD. Under the Controller in the middle it should list the Ubuntu iso if dome properly.

Thanks for the reply.

What do you mean by checking the md5?
How can I create the Virtual container?

---

### Post by azmyth on 2012-02-24
View the md5 from your iso by doing the steps below

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

then compare to the ones here

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I assume you want to install Ubuntu as a Virtual Machine. In VMWare player select File - Create New VM and then when the page comes up select use ISO then select your Ubuntu iso and then keep going through the setup until your down then start the created VM which should start your iso.

---

### Post by Mach101 on 2012-02-24
I have now checked the md5sum and its different from the one it is on the page you mentioned. I try download it once again, and hopefully gives the same md5sum this time.

I guess this file was corrupted and thats why VMPlayer didn't detect it.

---

### Post by Mach101 on 2012-02-25
I finally managed to download it after 3 attempts and its installing it. 
Thanks for the help.

---

### Post by ThomasAndersn on 2012-02-25
why don't give try VLC player its the awesome & supported by ubuntu ........

---

