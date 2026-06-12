---
title: "Canon i850 printer"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Torstein_V on 2006-06-10
First of all, I want to thank the community for making such a good effort in making this forum into what it is. I've read posts and howto's many times, and I've always gotten the help I needed. In fact, I'm so satisfied with the help I've recieved, that I've finally made up my mind and registered my self as an user of ubuntuforums.org. 

Again, thanks a lot for keeping the "Ubuntu" spirit alive! :)

Anyways, despite my happiness with the Ubuntu 6.06 system, I am experiencing a major issue, that in fact has caused the vein in my forehead to show up pumping like a maniac ;) . The issue is setting up my [SIZE="4"][COLOR="Blue"]Canon i850 Printer[/COLOR][/SIZE].

In Ubuntu 5.10, all I had to do was to open up the "Add a printer" application, select "Use another printer by selecting port", choosing "Parallell Port 1 (CANON)",  then set up the printer to work with the BJC7004 driver, reboot, and print.

In Dapper, on the other hand, the story's a bit different. The printer sets up perfectly, like in Ubuntu 5.10, but the printing doesn't. 

When I press the print icon in OOo2.0 Word Processor, the printer prepares it self for printing, but when it finally start printing, it stops after completing 1/12 part of the page, and just stays there, whitout sending the paper out. It's almost like it's frozen.

So, basically I'm asking if anybody else's experiencing this, or if anybody has gotten their Canon i850 printer to work, and if they have, how?

Thanks in advance! ;)

---

### Post by Torstein_V on 2006-06-11
EDIT:

 I finally figured it out, and it doesn't require any packages installed or anything:

I assume you are using Canon i850 with parallell port #1, and not USB, it might work with USB as well, but I can't confirm it, since I don't have it my self. Anyway:

Open up the Printing Management Apllication:

System -->Administration --> Printing

Click on the "New Printer" icon. Check the radiobox "Use another Printer by specifying port"

From the drop-down-menu, choose[COLOR="Blue"]LPT #1[/COLOR]

Proceed to the next step, pick Canon as manufactorer, and finally choose the BJC-7004-driver.

Reboot

Happy printing with Canon i850 :)

I hope this was helpful ;) 

Please leave a comment if you wish, or if you are experiencing any problems.

---

### Post by mandragor on 2006-06-11
Thanks, this worked great for me! After struggling with the advice from 
[http://ubuntuforums.org/showthread.php?t=10540&highlight=i850](http://ubuntuforums.org/showthread.php?t=10540&highlight=i850)
it was wonderful to see a one-step solution that works well. :)

---

### Post by mandragor on 2006-06-13
Sorry for double-posting this, but to get i850 working with the best drivers, namely
Canon's own i850 drivers follow this recipe:

You will need alien installed (converts rpm files to deb) and wget (downloads the rpms) and libpng and libtiff3g. Unfortunately libtiff3g is not available in the normal Dapper repositories so we have to add a line to our /etc/apt/sources.list.

sudo echo "deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install alien wget libpng3 libtiff3g
sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2

After this is done you should remove the last line from your /etc/apt/sources.list to prevent problems. Currently you need to download rpms and convert to deb-packages to get this printer working. Get the necessary files:

wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm)
wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus850i-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus850i-2.2-1.i386.rpm)

Then you can convert the files with the following commands:

sudo alien -c bjfilterpixus850i-2.2-1.i386.rpm
sudo alien bjfiltercups-2.2-1.i386.rpm

Install the deb packages:

sudo dpkg -i bjfilterpixus850i_2.2-2_i386.deb
sudo dpkg -i bjfiltercups_2.2-2_i386.deb

You will need to restart CUPS to see the drivers in the list, run the following command:

sudo /etc/init.d/cupsys restart

Now add the printer, in Gnome this is done via System > System Settings > Printing or in KDE via System Settings > Printing. The printer is listed as Canon (brand( and PIXUS-850i (model). Print a test page to ensure it works.

---

### Post by feelinggood on 2007-01-30
Hi, I am a complete newbie to linux.  Learning the basics and I am almost finished with Windows XP.  With my i850 the previous post to set it up with the I850 drivers is like a foreign language to me.  Can somebody help me with this as for the time being I am on a learning curve.  Thanks, Steve

---

### Post by feelinggood on 2007-01-31
bump up for help

---

