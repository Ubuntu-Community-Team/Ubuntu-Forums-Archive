---
title: "problem in installing ubuntu on my pc"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by ohogaty on 2012-09-04
Hi,yesterday I tried to install ubuntu on my pc but after some minute installation got stuck and I restarted my computer to try it again but it didn't work.
here is the image of my screen:
[IMG]http://up.vatandownload.com/images/lmlswgq5ftpqrx95czky.jpg[/IMG]
and here is my system details:
[http://ohdownload.persiangig.com/OMID.html](http://ohdownload.persiangig.com/OMID.html)
what should I do?
please help me.

---

### Post by dino99 on 2012-09-04
you got a well known issue called "kernel panic"

depending on the hardware you are using, you might need some boot option to get around that issue. Try first nomodeset or noacpi.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and here is the way i'm using for installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by ohogaty on 2012-09-04
Thank you,but it didn't work.
Who can help me?

---

### Post by oldfred on 2012-09-04
On the boot options screen linked by dino99  is nomodeset under f6.

I have nVidia 9600GT and have to use nomodeset on installs & first boot after install until I get nVidia driver installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by ohogaty on 2012-09-05
The problem solved just by F6 and click on nomodeset and no restarting the system or sth else.
I have an other question:
I want to install it with windows 7 .I should select something else or along side?
and I want to install it on my drive (j) how can I recognize it when I want to install it?
[IMG]http://up.vatandownload.com/images/oo04kpjpq65arijap0p8.jpg[/IMG]

---

### Post by oldfred on 2012-09-05
Please attach screenshots with the paperclip icon in the edit panel above you message.

Are your partitions basic not dynamic? Or are they logical partitions inside an extended?

Along side will automatically shrink the Windows partition and create new Linux partitions / (root) and swap. Or you can have it use unallocated space.

Manual install or something else lets you choose. You have to have Linux formatted partition(s) usually ext4. Ubuntu will not work from NTFS unless you want to install wubi from inside Windows. Reformatting will erase all your data so make sure you have nothing in f: that you want to save.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

