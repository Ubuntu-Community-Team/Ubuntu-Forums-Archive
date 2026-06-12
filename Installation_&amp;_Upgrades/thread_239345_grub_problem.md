---
title: "grub problem"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by hudelfa on 2006-08-19
I am newbee in ubuntu forums.

I have been using ubuntu dapper 6.06 for 3 months.Everything was perfect for me.But yesterday I wanna add a grub image into grub windows.When I rebooted my laptop it gave an error reads "Can not load grub image.Please press any key.(something like this)".I wanted to boot win Xp media center edition but it did not start and then I tried to boot ubuntu,ubuntu recovery,mem test respectively but none of them was started.My laptop rebooted in my every try.

THANKS FOR YOUR HELP IN ADVANCE.

---

### Post by majed on 2006-08-19
Use a LiveCD to boot and mount your disk then fix your grub configuration files.

Example LiveCD: INSERT ([http://www.inside-security.de/download_en.html](http://www.inside-security.de/download_en.html))

Online pages that can help you with the procedure to fix Grub:

[http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")
[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html]("http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html")

Good luck!
Majed

EDIT: two more links i found in the forum that can help you.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub")

---

### Post by ajgreeny on 2006-08-19
You probably got the image format wrong I'm afraid so you need to sort that out.  Here is a copy of some info I found a while ago and have used without problems since then.  This assumes you can at least boot into ubuntu and edit things from there, but if not you will need to use a live CD as suggested by  majed, mount your ubuntu partition and edit the menu.lst file from that.  Make sure you get the image size and colour number correct or you will still have the same problem. Good luck.

Grub splash

Get splash from net or produce your own picture
 [1] The image needs to be in xpm format.
[2] The image needs to be 640x480 in size.
[3] The image must have only 14 colors.

The xpm file can be left as is or gzipped; grub seems to load gzipped images a bit faster. The thinking on this is that grub can load a gzipped image and decompress it faster than it can load the full size image, due to hard drive access times.

You can still change the foreground and background colors of grub's menu if you're using a splash image, but the image itself won't be affected, only the menu overlay.

Here are a couple ways to get an image in the format you want it:

The quick way: (using convert from imagemagick)

convert -resize 640x480 -colors 14 whatever.xpm newwhatever.xpm && gzip newwhatever.xpm

The slow way: (using the gimp)

Open the image you want to use in the gimp, click the "Image" menu, then "Mode", then "Indexed". Select "Generate Optimum Palette:" and enter 14 for the maximum number of colors. It's also recommended that you check the "No Color Dithering" option.
After the conversion, save the file as whatever.xpm. The gimp should automatically create the correct format when it saves the file.

After you've gotten the image into the correct format and gzipped it (or not, your choice), all you need to do is add it to your grub config file, menu.lst

Look for :-
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
splashimage (hd0,1)/boot/grub/splashimages/AJG.xpm.gz

The bottom line is the one relating to you new splashimage and the partition in brackets is the same as in the line 
#groot=(hdx,x)
so make sure you edit that if needs be as well.

---

### Post by hudelfa on 2006-08-19
Thanks very much for your help, majed.I fixed my grub.Now I can boot both WinXP media center and Ubuntu Dapper..

---

