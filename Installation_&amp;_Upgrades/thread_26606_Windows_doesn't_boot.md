---
title: "Windows doesn't boot"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by look on 2005-04-13
Hello,
I'm a new user of ubuntu...
This is my problem:
I've an Amilo (fujitsu siemens) laptop.
I had WIndows Installed in this machine and all was ok.
Then I decided to install ubuntu. Ubuntu is great and works fine.... but I can't boot windows now!!!
In my menu.lst is written like this:

title= Windows
root (hd0,0)
savedefault
makeactive
chainloader +1

By the way also the windows installation CD can't boot....
When I try to boot windows a blinking cursor appears on the screen and that's all...
Thanks for the help...
Bye bye.
Look.

---

### Post by localzuk on 2005-04-13
Regarding the Windows CD not booting - that won't/can't be caused by the Ubuntu installation as it is controlled by the BIOS.

---

### Post by look on 2005-04-13
Ok.... I didnt' explaine well..
The cd boot... but when it starts to check the hardware configuration it blocks...
Anyway the big problem is that windows doesn't boot...  :? 

Thank for replay ;)

---

### Post by Dr Gonzo on 2005-04-13
See if you can mount the Windows partition under Linux.  Does it work?  If yes, then we can do something.

Did Ubuntu's installer automagically add the Windows entry?  My inkling is that it's trying to boot the wrong partition.  Note that Linux starts numbering partitions from 1, while Grub starts at 0.  So, /dev/hda1 in Linux is (hd0,0) in Grub.  /dev/hdb3=(hd1,2), and so on.

Try also, in menu.lst, changing the root command for Windows.  Instead of 'root (hd0,0)', try 'rootnoverify (hd0,0)'

Hope this helps.

---

### Post by look on 2005-04-14
ok..
Yes, I can mount the windows partition in ubuntu... It's an NTFS partition, so I'm able to read but no to write it...
The command I use to mount it is:
sudo mount /dev/hda1 /mnt/windows
The windows partition is then on hda1 that is (hd0,0) for grub.

I also tried to change root with rootnoverify but nothing happens...
:) what can I try more?

Thanks for replaying me ;)

---

