---
title: "Install VIsta over XP on my Dual Boot PC"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Jmatthewc on 2009-12-03
Hello.

I use a dual boot Dell portable.  I am using 8.04 Ubuntu and WinXP.  I would like to blow away WinXP and install Vista using the two partitions I set aside for the microsoft OS.  How will the dual boot menu handle this?  Will I have to modify the dual boot menu to recognize the new  OS?

As you can tell, I am new to the Linux world.  I would appreciate any help you can give me.

(I do plan to backup the partitions before this process.)

---

### Post by oldfred on 2009-12-04
You should be able to install Vista (If you really want Vista[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]) to the XP partition. Besure to back up any important information from XP because it will totally erase all of XP and everything in it.

Also the Vista install will overwrite grub in the MBR so you are just booting Vista. I would boot Vista a couple of times to make sure if installed ok and does not want chkdsk or other clean up after the install.
Then you will have to go back and install grub legacy. If you still are 8.04 your still have old grub, so ignore any instuctions for grub2 as that is currently only for clean installs of Karmic 9.10.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Jmatthewc on 2009-12-04
Thank you for the information.  I understand what's going on now.
As for the Vista 'death wish;)' its due to my supporting family members and friends who use it.  Due to employer belief in all things MS, I need to be/stay MS competent, and will jump to Win7 when I have the funds.  In the meantime, since I have the time, I thought I would 'mess around' in the Vista OS, although I prefer Ubuntu.

---

### Post by phillw on 2009-12-04
> **Jmatthewc said:**
> Thank you for the information.  I understand what's going on now.
As for the Vista 'death wish;)' its due to my supporting family members and friends who use it.  Due to employer belief in all things MS, I need to be/stay MS competent, and will jump to Win7 when I have the funds.  In the meantime, since I have the time, I thought I would 'mess around' in the Vista OS, although I prefer Ubuntu.

Just be aware, if your machine is a happy XP machine - it will, most likely, be a very unhappy Vista machine - ensure your drivers are available from your computer manufacturers' site for Vista ehternet, graphics, audio, wireless, usb etc. etc. - Else it will all end in tears.

Phill.

---

### Post by Jmatthewc on 2009-12-16
I have a Dell portable that came with the OEM Vista installation disk and the device driver CD.  I am most concerned about getting back to the dual boot menu that Ubuntu created previously.  So, I have backed up my data, and will attempt the install of vista, then after being sure that vista will operate, booting up on my Ubuntu LiveCD and following the instructions  found on the previous link to setup grub.  When I have issued the appropriate commands in terminal, and reboot the PC, I expect to have my "old grub loader menu" back, allowing me to select which OS I want to boot up.

That is the plan.....as I understand it

---

