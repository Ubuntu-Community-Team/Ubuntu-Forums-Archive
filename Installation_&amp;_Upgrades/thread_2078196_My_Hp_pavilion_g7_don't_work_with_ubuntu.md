---
title: "My Hp pavilion g7 don't work with ubuntu?"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by patica100 on 2012-10-30
My laptop is a Hp pavilion g7 and I try to install anytimes ubuntu 12.04 and when I restart the pc.. I choose a ubuntu later Normal mode.. and latet the screen is in BLACK and no more... I don't know whats happen if any people can help me is good...

I have Win 7
Try to instal with wubi
Try to instal with daemon
Try instal 64 and 32 bits
Any don't work
My Laptop is "Pavilion g7-1310us Notebook PC"

Bye :)

---

### Post by darkod on 2012-10-30
Can you boot the cd in live mode (Try Ubuntu)?

This sounds like video driver issue. If you have Nvidia probably you need to use the nomodeset parameter until you activate the driver.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by patica100 on 2012-10-30
I don't have nvidia, I have intel HD graphips 3000

---

### Post by darkod on 2012-10-30
OK, but why do you focus only on one part of my post. I said IF, I never said you DO have Nvidia.

The more important question was can you boot live mode? You didn't answer anything.

---

### Post by patica100 on 2012-10-30
ohh sorry man! And not.. I can't, only can enter to "console"

---

### Post by darkod on 2012-10-30
What console?

The standard ubuntu desktop cd has the option to work live from the cd when you select Try Ubuntu and not Install Ubuntu. Have you tried that?

---

### Post by patica100 on 2012-10-30
I don't have live cd... I donwload the .iso and imagine with daemon tool and when I restart the pc I choose ubuntu later Normal mode or demo mode and ANY mode don't work when I choose a mode.... Go black scren and don't work more 


:(

---

### Post by darkod on 2012-10-30
Can you brun a cd from the iso?

I don't know how it would work with daemon tools. You should always have the live cd at hand anyway, it's a very useful tool.

---

### Post by mastablasta on 2012-10-30
live CD or live USB drive (loads much faster than CD). to cretae a live usb you can use various applicaitons such as unetbootin or linuxliveusb or pendrivelinux.
 
i don't think you can use daemon tools to install operating system. additionally you need to check md5sum and make sure that downloaded ISO is good. th eimage you downloaded has top match the one on server. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
if you want a test ride instead of using daemon you should use virtual box. here is how: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by patica100 on 2012-10-30
With virtualbox I can enter but I need a particione with linux and the other with win7 but I don't know when I restar the pc and I choose linux and normal mode go Black scren and don't load more :(



Help me pls!

---

### Post by darkod on 2012-10-31
We already helped, we suggested to make a cd or usb stick with ubuntu and try to run it in live mode. If that works, you can use it to install too.
Daemon tolls probably don't work but you insist on using them. Don't tell me you can't make a cd or usb. You need an install media to install, we can't help much more. The OS can't magically appear on your computer. Make an install media first.

---

