---
title: "I got froggy Yesterday....."
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by mickey57 on 2009-11-26
[SIZE="4"]....Updated my bios yesterday so I decided to try installing ubuntu 9.10 64bit again..Wasn't able to get the 64bit to install form the regular .iso so I got the alternative .iso and burned it at 2x....All was going fine until it got to installing grub.Virus protection in bios is disabled.I also tried lilo.so I skipped grub and figured I would deal with that later since the install would let me go ahead.It is now later,lol.Put super grub disk in thinking that it had grub that would configure for me but that would be just to easy,now wouldn't it,lol.Any suggestions for when I come back to this project? [/SIZE]
[SIZE="3"]....Took a few pics of what the error was.looks like I didn't quite get all the letters in the middle.[/SIZE]
[IMG][IMG]http://i146.photobucket.com/albums/r244/mickey57photos/fuckup.jpg[/IMG][/IMG] . . . ..[SIZE="4"]I did go and get this [COLOR="DarkRed"][http://rescup.winbuilder.net/bootdisk/#download]("http://rescup.winbuilder.net/bootdisk/#download")[/COLOR] and used RawWriteWin to put it to floopy.I looked over the files and it seems it is pretty much like super grub :([/SIZE]

---

### Post by Sealbhach on 2009-11-26
That error message is telling you that there is no bootloader installed i.e. Grub2 did not install properly. The first thing to try is to use a Live CD to  install Grub2. The instructions are here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Good luck!

.

---

### Post by mickey57 on 2009-11-26
[SIZE="4"]....Thank you Sealbhach for the links.I will study the information.Knowing the in's and out's of grub is something that I have been putting off for years.I feel a good understanding of how to manipulate Grub is a fundamental that should be studied.I seem to have skipped that step also:redface: [/SIZE]

---

