---
title: "No boot for Karmic Koala after installing BackTrack 4"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by XxX_VLAD_XxX on 2010-03-21
I need help, i had my Karmic Koala working fine in dual boot with Vista, then i decided to install Backtrack 4 since it was based on Ubuntu 8.10, so I did and it worked fine, Windows too, but my Karmic Koala doesn't boot. I did this in my HP laptop.

Error 15: File not found

How can i get my two linux partitions to boot ok?

I believe when I install a new GRUB erased the old one and reset the MBR, what can I do? if i reinstall grub in /sda5 (where my Karmic is) i lose backtrack?

---

### Post by oostue on 2010-03-31
I have the exact same problem, with Win7, BT4 and Koala. Win7 and Koala worked good together, when i installed BT4 it changed my menu.lst and now only BT4 and Win7 boot. Also getting error 15. Let me know what information would be usefull to post.

---

### Post by XxX_VLAD_XxX on 2010-04-01
You know what, i´m just gonna wait until 10.04 comes out and start over again, for some reason when i tried to reinstall GRUB from LiveCD i couldn't do it 'cause it said grub wasn't installed, i tried to do it inside BT4 and it did had find the grub script, i tried to re-install it on my Jaunty partition but no effect, for some reason my third partition with NTFS (not C:\) had been de-formated or something i had to format it again and lose my information there.

So when 10.04 comes out i'll install that and pray for it to recognize BT4. I miss Ubuntu tough

---

### Post by uRock on 2010-04-01
BT uses grub 1.5 right? You may need to install grub2 to get them working. Just a thought.

I have been debating installing BT also, I guess I'll wait until I am ready to reinstall everything to add it.

---

### Post by mcoleman44 on 2010-04-01
Depending on how you installed BT4 you might have deleted everything on your hard drive.

---

### Post by 4ll41 on 2010-04-06
Hi there,

Had the same problem when I installed BT4 in my machine that was running already Ubuntu 9.10. Backtrack installed also an older version of Grub (Grub legacy) which -unfortunately- can not recognise the Ext-4 partition, where Karmic is installed.
Tried to upgrade to Grub2 in order to run the Karmic partition, but in vain, there were dependency problems if I remember correct, that I could not fix.

The only way that worked for me was to format everything, install BT4 first, then Karmic Koala and everything works ok. :)

Of course you can save all your data as your partition can be accessed from a live-CD.

Good luck

Or you can try this [one ]("http://ubuntuforums.org/showthread.php?t=224351&highlight=%2Ftmp+content+boot")

---

