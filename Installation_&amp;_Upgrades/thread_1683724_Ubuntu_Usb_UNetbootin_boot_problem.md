---
title: "Ubuntu Usb UNetbootin boot problem"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by YoulBeAmazed on 2011-02-08
I am installing ubuntu for the first time on my old computer which I don't care about losing the files that are on it. I don't have any dvds right now because I'm in the middle of a move but I do have a usb stick that I found so I used UNetbootin to put Ubuntu onto a usb stick(version 10.10 the newest) Everything goes fine and when i boot the computer from the usb it says all the info about it then goes to the menu where it says UNetbootin at the top and then all your options(default, help, try ubuntu without installing etc.)
I want to just completely remove windows and put on ubuntu but when I press enter on one of the options it shows a blinking curser at the bottom below the press tap to edit options and it just stays there and I cannot move up and down with the errors or anything. When I first told it to boot using the usb it took about a minute to get to the main menu so I left it thinking it would do something but I've tried several times trying the different options including default and install ubuntu and all of them just stop and don't do anything. Any help would be appreciated.

---

### Post by BACbOK on 2011-02-08
What configuration of your PC?
You can try make bootable usb-drive from WinXP **[Linux live usb creator]("http://www.pendrivelinux.com/linux-live-usb-creator/")**.

---

### Post by ugm6hr on 2011-02-08
Few possible explanantions (and solutions):
[LIST=1]
[*]Your iso download was corrupt (check md5sum)
[*]Unetbootin is misbehaving (try using the official USB process)
[*]Your old computer does not have enough RAM (you need minimum 512MB realistically)
[*]You downloaded a 64-bit version, when your computer is 32-bit (get corect version)
[/LIST]

Links:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://xenoxcomputers.com/?page_id=316](http://xenoxcomputers.com/?page_id=316)

---

