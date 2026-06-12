---
title: "boot up problem after successful installation"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by piyush| on 2011-09-27
one of my friend just installed ubuntu 11.04 along side windows but in different partition 
he used one mount point / and no other mount points as mentioned in this guide
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

now the problem is after successful completion of the installation ,there is no option for ubuntu in boot menu
win 7 automatically starts booting

plz help 
thanks

---

### Post by dino99 on 2011-09-27
standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by drs305 on 2011-09-27
If your friend can run the boot info script from an Ubuntu LiveCD we can see what happened and why Grub isn't booting Ubuntu.

Click on the "BIS" link in my signature line to go to the script download page. Run the script, and then post the contents of RESULTS.txt

---

### Post by oldfred on 2011-09-27
Did you change the default location of where to install the grub2 boot loader shown on the combo box at the bottom of the partitioning screen? If you installed grub2's boot loader to the MBR it should be booting to a grub menu.

Post this to see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by piyush| on 2011-10-02
ok the problem ois solved now
he just used a fresh copy of 11.04 and used UnetBootin instead of wubi

---

