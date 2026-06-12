---
title: "what files should be in a 10.04 image download?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by TXbirder on 2010-08-10
I have downloaded 10.04 via BitTorrent.  I have burned it to a CD.  The various download instructions advise me to check the contents of the CD.  If there is only Ubuntu, I'm missing some important files.

I want to make a live CD.  I can't make the new CD open.  I looked at the contents and the folders are:  *dists,  doc,  install, isolinux*, *pix, pool, preseed, ubuntu, chromupgrade, md5sum.txt, README.diskdefines*.

Am I missing something?  I tried changing BIOS to boot from the disk but that only offered an installation, not a LiveCD.

John

---

### Post by ajgreeny on 2010-08-10
What is the name of the iso file you downloaded?  It sounds as if you did not get the **ubuntu-10.04-desktop-i386.iso** but maybe the alternate .iso or server, or something else.  If it was downloaded by torrent the iso file should be a good one, but perhaps simply the wrong one for a live CD.

If it appears to be the correct iso file, boot to it again but after using the power-on button, keep hitting any key and you should get a menu where you can choose to check the CD (or media, I can't remember the exact word used).  If it shows any errors after the check, reburn the CD at a lower speed.

---

### Post by TXbirder on 2010-08-10
ajgreeny,

I downloaded  the version you suggested, made a new CD.   I still can't make it work as a LiveCD.  When I boot the computer from the CD, it just wants to install 10.04.

When I try to open it in Ubuntu, it just displays the files on the CD but doesn't start 10.04.

John

---

### Post by fea2k on 2010-08-11
> **TXbirder said:**
> ajgreeny,

I downloaded  the version you suggested, made a new CD.   I still can't make it work as a LiveCD.  When I boot the computer from the CD, it just wants to install 10.04.

When I try to open it in Ubuntu, it just displays the files on the CD but doesn't start 10.04.

John
[IMG]http://image163.poco.cn/mypoco/myphoto/20100811/14/5555945320100811142040091.jpg[/IMG]
maybe when you click "try ubuntu 10.04 LTS",it can work as a liveCD.

---

### Post by TXbirder on 2010-08-11
Thanks but the Install screen I get has language choices on it but no buttons labeled **[FONT=Lucida Console]Try Ubuntu...  [/FONT]**[FONT=Lucida Console]or[/FONT]**[FONT=Lucida Console]  Install Ubuntu.....[/FONT]**

Maybe I need to download a third version and make another CD.

John

---

### Post by howefield on 2010-08-11
> **TXbirder said:**
> Thanks but the Install screen I get has language choices on it but no buttons labeled ...Try Ubuntu...    Install Ubuntu.....

So what do you see after you select your language ?

---

### Post by TXbirder on 2010-08-11
After language selection, I see **Setting the clock**, **Where are you?,** 
**Keyboard layout, Prepare disk space, Who are** **you?**

The next page is for installation so I stop there.  Nowhere is there a LiveCD selection button.

John

---

### Post by ajgreeny on 2010-08-11
Check the md5sum of the iso file you have against the listing here:-
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
I'm not sure how you do it in windows, but it can certainly be done.

---

### Post by TXbirder on 2010-08-11
I went to that screen and then** How to MD5SUB**.  In the terminal I typed  **cd download_directory** as instructed and got:  **No such file or directory exists**.

Think I'll check Ebay to see if any U10.04 cds are on sale.  They're usually cheap and faster than waiting on a copy from Cannonical

John

---

### Post by howefield on 2010-08-12
Just a thought..

When you first boot with the CD, do you see some graphics at the bottom of the screen, one looks like a keyboard, the other like a person (I think).

When you see those graphics, are you pressing the enter key ?

---

