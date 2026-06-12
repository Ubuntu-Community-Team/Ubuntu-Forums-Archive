---
title: "UBUNTU10.04LTS hangs at login after installing new updates"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by 12averma on 2011-03-25
[SIZE=3]firstly i have both vista and ubuntu10.04lts on my system,(vista installed first).Both were working well[/SIZE].[SIZE=3]I was enjoying using ubuntu10.0lts than vista...felt great.
    but i installed new updates on ubuntu and some error occured, so updates were not installed fully.
i restarted the system, Grub window appears showing both ubuntu and vista and i selected ubuntu OS to run,but at login screen , it freezes and nothing happens by moving mouse, pressing keyboard and even mouse cursor doesn't moves and if i select vista to run , then vista runs smoothly.but i want to work more with ubuntu. 

i dont want to lose data on ubuntu ......but if it not possible then its okay.....but i want to work on ubuntu.


-> there is no dual boot.
-> i have a ubuntu10.04lts cd too.
-> i have a lan connection too.

ANY HELP IS WELLCOME .........please help me.:(
[/SIZE]

---

### Post by 12averma on 2011-03-29
Help me please.................:(

---

### Post by Rubi1200 on 2011-03-29
Hi,

1. please post the specifications for the computer, especially graphics card

2. please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

