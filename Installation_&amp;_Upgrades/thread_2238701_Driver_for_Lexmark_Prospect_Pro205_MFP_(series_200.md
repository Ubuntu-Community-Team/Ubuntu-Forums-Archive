---
title: "Driver for Lexmark Prospect Pro205 MFP (series 200-500) for ubuntu 12.04 + 12.10"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by Thomas_Boll on 2014-08-09
I think I found a fix on the web for the lexmark printer and scanner drivers for ubuntu 12.04 + 12.10 (and maybe upwards).

If you get the error "cp: cannot stat `/usr/local/lexmark/printer_utility/bin/%%JARVIS_VENDOR_PREFIX%%hcp': No such file or directory" when trying to install the printer_utility debian package,
see [http://ubuntuforums.org/showthread.php?t=2087791&highlight=driver+Lexmark+Prospect+pro205+ubuntu+12.10](http://ubuntuforums.org/showthread.php?t=2087791&highlight=driver+Lexmark+Prospect+pro205+ubuntu+12.10) for a description of the problem.

Jerome has provided a path for the printer_utility debian package (Thank You man!). See [http://lacostej.blogspot.de/2012/12/lexmark-s305-on-ubuntu.html](http://lacostej.blogspot.de/2012/12/lexmark-s305-on-ubuntu.html) for his original blog post.

In short, this is what there is to do:

"You can fix the installer using [this script]("https://gist.github.com/4374626"). To install it, run this from the directory where you have downloaded the debs.

 wget [https://gist.github.com/raw/4374626/e946d2a3ad2e24657ddd32a84f31927970773745/fix_lexmark.sh](https://gist.github.com/raw/4374626/e946d2a3ad2e24657ddd32a84f31927970773745/fix_lexmark.sh)
chmod +x fix_lexmark.sh
./fix_lexmark.sh
dpkg -i build/lexmark-printer-utility_1.0-1_i386.deb
  You will notice that the new package is one revision below the original,  that's because the DEBIAN/control in  lexmark-printer-utility_1.0-2_i386.deb was invalid I guess... "

Please share if this works for you and which printer model and ubuntu version you tried.

That's all for now folks.

me.

Copy of the "fix_lexmark.sh" script:

-- snippet start --

dir=tmp

rm -r $dir
mkdir $dir
dpkg -x lexmark-printer-utility-1.0-2.i386.deb $dir
dpkg-deb -e lexmark-printer-utility-1.0-2.i386.deb $dir/DEBIAN

file=$dir/usr/local/lexmark/printer_utility/etc/lxpsu.desktop
sed -e 's/\$JARVIS_VENDOR_SHORT_NAME%%/lexmark/g' $file > $file.1
mv $file.1 $file

file=tmp/usr/local/lexmark/printer_utility/bin/.scripts/lxpsu
sed -e 's/%%JARVIS_VENDOR_SHORT_NAME/lexmark/g' $file > $file.1
mv $file.1 $file

file=tmp/DEBIAN/postinst
sed -e 's/%%JARVIS_VENDOR_PREFIX%%/lx/g' $file > $file.1
mv $file.1 $file
chmod +x $file

grep -r JARVIS $dir

mkdir -p build
dpkg-deb -b $dir build
ls build

-- snippet end --

---

### Post by koohiisan2 on 2014-09-05
This worked perfectly for me on Mint 17 for my Lexmark Pinnacle Pro901!  Thanks!!

---

