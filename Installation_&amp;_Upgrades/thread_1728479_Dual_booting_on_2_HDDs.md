---
title: "Dual booting on 2 HDDs"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by samn122 on 2011-04-13
Currently I have vista 64 bit and Ubuntu 9.10. I've wanted to upgrade for a long time but I'm scared to do so, so help me out ;). Windows Vista is installed on a 500gb HDD and I have Ubuntu installed on a separate 350gb HDD. I want to upgrade from 9.10 to 10.10. The last time I upgraded (barely remember) I messed up on upgrading the GRUB booter and had to wipe both systems and do a clean install of windows vista and ubuntu. Can anyone give me any tips or pointers before I get started on upgrading. I do have my important data backed up btw. I haven't done this stuff for a while either.

---

### Post by oldfred on 2011-04-13
Post this to see entire configuration. I use it to document exact how I boot and what partitions are where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

I like to keep each drive independant, so the windows drive will boot windows if the Ubuntu drive is missing & vice-versa. But many times grub has installed to sda or the windows drive.

Some suggest when installing Ubuntu to a second drive you physically disconnect the windows drive. It absolutely works.

But if you do manual install you can control where Ubuntu is installed and which MBR the grub2 boot loader is installed.

Do you have a separate /home? or data not in the / (root) partition?

You may want to back up installed packages.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

