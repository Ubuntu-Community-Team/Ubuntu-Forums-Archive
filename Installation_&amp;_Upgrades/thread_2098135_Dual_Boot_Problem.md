---
title: "Dual Boot Problem"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by ClockworkSwordfish on 2012-12-25
So here is my dilemma. I got a new laptop with Windows 7, and fairly easily set it up to dual-boot Windows and Fedora (Grub2 as bootloader). However, I am having much trouble getting Fedora to recognize my wireless card, including Wi-Fi and Bluetooth), and eventually decided that Fedora was more trouble than it was worth and decided to install Xubuntu instead.

Booting into live environment worked fine and I confirmed that Xubuntu does indeed recognize the card, Bluetooth and all. But the installer did not seem to recognize Fedora in the main options and only gave me the options to either install Xubuntu alongside Windows 7 or instead of Windows 7, i.e. only on the one half-the-hard drive partition. I selected to install to half of the half-the-hard drive partition and it gave me an error. Next I went into the advanced settings and saw that the Fedora partitions (3: one swap, one large home, and one smaller either root or boot, I forget which.) were recognized. 

I was going to set the home one as my main Xubuntu partition and the swap as swap and try to delete the other one later, but I am not sure if there is a better way. Is there any kind of way to fix this up such that I have Xubuntu and Windows together, each with half the hard drive and GRUB recognizing both without reinstalling Windows?

Sorry for the wall of text and thanks in advance!

---

### Post by Kirk Schnable on 2012-12-25
> **ClockworkSwordfish said:**
> I was going to set the home one as my main Xubuntu partition and the swap as swap and try to delete the other one later, but I am not sure if there is a better way. Is there any kind of way to fix this up such that I have Xubuntu and Windows together, each with half the hard drive and GRUB recognizing both without reinstalling Windows?

Absolutely.

In your Live CD environment, you should be able to install and launch GParted.  GParted is a very simple partition editing tool you can use to manually clean up your partitions yourself.  Your other option is to choose, during the Xubuntu Setup, to manually partition the drive, by choosing "Something Else".

You'll want to delete your existing Linux (ext3\ext4\swap) partitions, but you'll want to leave your Windows (NTFS) and your Windows System partition (very small partition at the front of your drive) intact.  Then, Xubuntu will be able to be installed in the available space.

There will be no difficulties for your existing Windows boot loader unless you resize\move the Windows partition, or delete your Windows System partition.  GRUB should recognize Windows, and Windows should still work, after you've deleted your existing Linux partitions.

If you want help editing your partitions, please use the Live CD environment, install GParted, launch GParted, and post a screenshot of your partition layout.

Kirk

---

### Post by oldfred on 2012-12-25
I think Fedora's default install is a boot partition and LVM. So to get Ubuntu to see it you need to install the lvm driver.

sudo apt-get install lvm2

Not sure if gparted will work with your LVM or not as that normally has its own &  different partitioning tools, but if just deleting I would think it should work.

---

### Post by Kirk Schnable on 2012-12-25
> **oldfred said:**
> I think Fedora's default install is a boot partition and LVM. So to get Ubuntu to see it you need to install the lvm driver.

sudo apt-get install lvm2

Not sure if gparted will work with your LVM or not as that normally has its own &  different partitioning tools, but if just deleting I would think it should work.

Good to know, thanks for mentioning that, I'm not really a Fedora person.

---

### Post by ClockworkSwordfish on 2012-12-26
UPDATE:

Yes, you are right about Fedora using LVM, but the Xubuntu live CD (12.10) already has lvm2 installed. HOWEVER, GParted will not let me delete the LVM partitions nor will the "Something else" manual install options (the options are greyed out and inactive).Screenshots for your benefit:
[http://i672.photobucket.com/albums/vv88/Qwertyuiopschmoe/Pic3.png](http://i672.photobucket.com/albums/vv88/Qwertyuiopschmoe/Pic3.png)
[http://i672.photobucket.com/albums/vv88/Qwertyuiopschmoe/Pic4.png](http://i672.photobucket.com/albums/vv88/Qwertyuiopschmoe/Pic4.png)

---

### Post by oldfred on 2012-12-26
Gparted will not work on the LVM partitions only the LVM tools. But you should be able to totally reformat the entire partition that the LVM is installed into.

Some info on LVM
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

### Post by ClockworkSwordfish on 2012-12-26
Yes, virtual machine testing confims that just reformatting the partitions works fine. And it still boots anything else that was on the hard drive besides what was formatted over. Will try soon on the actual machine.

Edit: The actual machine has a third LVM partition (the smaller boot or root one mentioned above) while the virtual machine only has the two. Will this throw a wrench into things at all? What should I do about it?

---

### Post by ClockworkSwordfish on 2012-12-27
Well, it was harrowing, but I am now smoothly running Xubuntu and Windows 7. As to how, it is a wretched tale which leaves in its wake tears and a small 1 GB partition full of nothing. Still, Machiavelli at least would approve.

Thanks all.

---

