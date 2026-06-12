---
title: "Installing Xubuntu 11.04 on usb"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by A-algen on 2011-05-09
p { margin-bottom: 0.08in; }  p { margin-bottom: 0.08in; }a:link {  }p { margin-bottom: 0.08in; }a:link {  }  [FONT=Times New Roman, serif][SIZE=3]Hi i have some problems whit my eeepc it is a old one white a 3.7 gb ssd system disk and xubuntu 8 hardy installed on it. It has swap partition to on 500 mb so that lives 3.2 gb for the system. I haven't updated it in a long time and now when wont to updating the dist it takes 1.6 gb in free disk space fore all the packages and I cant get al that free disk space. So I thought that it was time to re-install it but usb-creator for hardy was not to be found whit apt-get or synaptic my system was to old. After some time of searching I found usb-creator for hardy and it works perfect it copy's al the files but it never makes the usb bootable so my bios cant detect it and I have tried 30 times but its the same error every time. So I tried usb-imagewriter but I cant find it to hardy so it was a dead end. Then I tried [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]sudo dd if=/path/to/downloaded.img of=/dev/devicenode bs=1M it works as god as usb creator  it copy's all the files right but it is not bootable. So I ask t a friend ho ones gave me a working debian net-install usb made whit dd hi sad that there is a file that makes the dd usb bootable and the command was cat /path/to/file > /dev/sdx. The file was suppose to be uploaded on ubuntu forum but I cant find it and my friend doesn't have it on his computer any more so hi cant help. I came a cross some linux forum that it was mention that the iso was made for cd and dd wrights it in a cd´s fil system ISO 9660 and that if you wane make a linux usb you should use an iso made for usb that would run in ext3. I [/SIZE][/FONT][[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]posted tis thread not becos i thing tha i´m completly out of options but becos it is geting very hard and haow hard can it bi to install xubunut 11.04 on a stupid usb. I will tri to open it whit grub and som other stuff but if som one ha an esyer way out of dis i woud love to hear it. Sorry for  my crappy english im moore use to wright in swedish :)[/SIZE][/FONT][/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=asc&sort=title")

---

### Post by mörgæs on 2011-05-09
Hi, welcome to the fora.

Try creating the USB stick with Unetbootin.

---

### Post by dajare on 2011-10-15
@mörgæs - Thanks for this pointer to Unetbootin - it's what I needed to know, too! The USB startup-creator on my old Ubuntu Jaunty couldn't "find" the Xubuntu 11.10 .iso I had downloaded, but Unetbootin did the trick. :)

---

### Post by mörgæs on 2011-10-15
You are welcome. 

Since 9.04 the USB startup creator has improved quite a bit, but if it still gives trouble you know the solution.

---

