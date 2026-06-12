---
title: "PRIMARY and LOGICAL option not in CREATE PARTITION TABLE"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by abros2k11 on 2011-03-06
Hi all,
I have a serious problem here. When I tried to create manual partition in Ubuntu 10.10 there was no option for logical and primary. Rest everything was there. Still I followed the steps ignoring the above pb. At the end when I tried to access ubuntu I got this error: No such partition
grub rescue>
I tried to install grub using sudo mount /dev/sd8/mnt:confused: but the output says that the mount: /dev/sd8/ failed or not present i actually dont remember the error. But the main thing is I was not able to dual boot Windows 7 and Ubuntu even after trying 3 times.

Please tell me y there is no option in create partition table.

Thank you

---

### Post by ikt on 2011-03-06
> **abros2k11 said:**
> Hi all,
I have a serious problem here. When I tried to create manual partition in Ubuntu 10.10 there was no option for logical and primary. Rest everything was there. 
Please tell me y there is no option in create partition table.


Are you installing ubuntu on the same hard drive as windows 7? 

If so have you made a space on that hard drive to install ubuntu in?

There is some more information here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by howefield on 2011-03-06
Moved to "*Installation & Upgrades*"

---

### Post by oldfred on 2011-03-06
If you are up to sda8, have you installed multiple times. You can only have one extended partition and if you have sda8 it must be in the one extended partition.

To see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

