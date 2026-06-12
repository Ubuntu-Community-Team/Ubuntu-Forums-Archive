---
title: "GRUB doesnt detect my windows partition?"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by StifflerNewb on 2009-10-17
Hi!

I just installed 9.10 on this computer and I'm having a wierd problem. I decided to dual boot and went in with the live CD, formated a 120gb partition I had to ext3 and then went on with the installation.

After the installation I just boot right into ubuntu. The wierd thing is this:
I can see the 20gb partition via "Places" and I can see the files in it. When I select it and have a look where it's located it's in /media/ for some reason.

Anyway, my question is this:
Did I **** up so much that I have to install XP and Ubuntu again, or is this fixable?

---

### Post by quinnten83 on 2009-10-17
Might be fixable. Sounds likeyou have to manually configure grub. i can't remember how that went tho. You will have to google some.

---

### Post by StifflerNewb on 2009-10-17
Hmm ok, thanks for the lead. Found this [http://ubuntuforums.org/showthread.php?t=27218](http://ubuntuforums.org/showthread.php?t=27218) but the thing is the menu.lst is missing any clues there? I found a topic that is about a missing menu.lst but it just doesnt fit me, I had no errors while installing and made sure to verify the installation CD when I burned it.

---

### Post by thunk77 on 2009-10-17
Hello,

Please post the teminal output of

```
sudo fdisk -l
```

---

### Post by oldfred on 2009-10-17
9.10 is Karmic which is in Beta. If it is a new install it uses grub2 which is totally different than legacy grub.

There is a grub.cfg that you do not edit but is created from other files every time you run grub-update. If you are missing os-prober install that and it should find your windows and then update grub.cfg with the update-grub2 command. If that does not work you have to create a new file with the windows boot stanza, somewhat like you used to add to menu.lst that the update will add when run.

Even still, the latest Karmic  needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

---

### Post by solorak on 2009-10-17
thanks for the info oldfred actually helped with a small problem i was having

---

### Post by StifflerNewb on 2009-10-17
What I'm gettin is this:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f561adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2710    21760042+   f  W95 Ext'd (LBA)
/dev/sda2   *        2711       19458   134520844+   7  HPFS/NTFS
/dev/sda5   *           2        2384    19141416    7  HPFS/NTFS
/dev/sda6            2385        2688     2441848+  83  Linux
/dev/sda7            2689        2710      176683+  82  Linux swap / Solaris


---

### Post by StifflerNewb on 2009-10-17
turns out something went horribly wrong in the install (I'm suspecting PEBCAK), so reinstalled and just wiped everything. nothing important on this computer anyway :P

thanks for the all the advice!

---

### Post by cariboo on 2009-10-17
When asking questions about Karmic, please go [here]("http://ubuntuforums.org/forumdisplay.php?f=359"). If you had checked, you would have found that your problem was fixable in less than 2 minutes. There was no need to re-install.

---

### Post by oldfred on 2009-10-17
I just went back an looked at fdisk listing. His sda6 is 2.4. Did they not fix the installer in Karmic? I always manually partition using gparted and then manually install, so I never see this:

HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

---

