---
title: "What is the root of my Vista installation?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Olmen on 2007-04-20
I installed Feisty parallel to Vista today. But the GRUB failed to recognize my Vista installation and it doesn't show up in it's menu. Nothing else to do but to to manually add it to the menu.lst file. No problem there. The problem, however, is that I don't know what the root of my vista installation is, because it's not hd0,0. That's Ubuntu's root.

Is there a smart way I can find this out or do I just have to try manually? They're both on the same partitions and Vista is on D:\ (in windows) for some reason I can't remember... and then there's the swap partition of course :S

---

### Post by reiki on 2007-04-20
I think sudo fdisk -l will tell you what disks you have (run that in a terminal). One will probably be NTFS which would, of course, not be the Ubuntu partition :)

---

### Post by sourchier on 2007-04-20
Hello, sorry you are having so much trouble. Have you tried the following in your menu.lst:

code:
title Microsoft Windows Vista
root (hd0,2)
savedefault
makeactive
chainloader +1

or code:

title Microsoft Windows Vista
root (hd0,1)
savedefault
makeactive
chainloader +1

could you also post the output of /sbin/fdisk -l as the root user? That would help us help you. Thanks!:KS

---

### Post by Olmen on 2007-04-21
Hi guys, thanks for your replies. When I run fdisk it only shows the ones mounted in dev/. Ie, dev/hda1 through hda3. This should mean that the root of vista is hd0,2

But unfortunately I get "NTLDR missing" when Vista's booting and that never is a good sign :( Or maybe this is the perfect time to migrate to Linux once and for all :P

---

### Post by biffta on 2007-04-21
You sure you didn't [do what I did?]("http://ubuntuforums.org/showthread.php?t=415883")

---

### Post by Olmen on 2007-04-21
> **biffta said:**
> You sure you didn't [do what I did?]("http://ubuntuforums.org/showthread.php?t=415883")

I followed a pretty similar scenario. However, I did not resize nor delete any existion partitions. There was 20 gig unpartitioned space on my harddrive (from a previous XP or something) and I wanted to install ubuntu there. I can still access my Vista partition from Ubuntu so everything is still there, except the NTLDR is missing and probably also the MBR... weird. Not that I particularily need Vista on this machine anyways - it just annoys the heck out of me when both Vista and Ubuntu 7.04 are supposed to be sooo god and using them in parallel should be sooo easy and it just isn't :(

---

### Post by tiwest on 2007-05-07
Hi! I've actually got exactly the same problem as you! 

I installed Ubuntu after Vista in order to not have to worry about the Vista boot loader messing up GRUB - So like you, I manually added my Vista installation to grubs menu.lst file. That's all fine and I know my vista installation is fine as I can access it like you can via Ubuntu. 

The problem is (like you say, it seems like i'm just repeating what you've written ^^) upon booting vista I'm presented with the error 'NTLDR missing, hit a key to reboot bla bla' - Then ofcourse i'm back to GRUB and the cycle continues.

I need some help or a poke in the right direction if possible on how to create a new NTLDR/boot.ini / whatever appears to have gone *caput*

Any advice is much appreciated!

---

