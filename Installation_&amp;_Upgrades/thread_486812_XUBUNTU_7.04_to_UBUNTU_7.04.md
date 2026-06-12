---
title: "XUBUNTU 7.04 to UBUNTU 7.04"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by Jerr973 on 2007-06-28
I hope I am posting in the right place, Ok my question is I am running XUBUNTU 7.04 and want to switch to UBUNTU 7.04, can I just upgrade or do I have to do a fresh install of UBUNTU and if I can just upgrade how would I go about doing it?

---

### Post by Topfs on 2007-06-28
sudo apt-get install ubuntu-desktop should do the trick.
If you want to take away Xubuntu and the XFCE you can do sudo apt-get remove xubuntu-desktop also, but you can have all installed, Xubuntu, Kubuntu and Ubuntu. You can choose between them in sessions at the login screen

check out [www.ubuntuguide.org](www.ubuntuguide.org)

Good Luck

---

### Post by Jerr973 on 2007-06-28
Thanks alot for the quick reply, will go it a shot....

---

### Post by Topfs on 2007-06-28
Sudo apt-get install ubuntu-desktop and reboot and wait until you have verified that it works before you remove anything, but it should work, is almost no reason why it shouldn't. Don't forget to add extra repositories :)

Best of lucks ;)

---

### Post by Jerr973 on 2007-06-28
Good thing I cam back, about these extra repositories how and when do I add them?  Sorry for all the questions but want todo everything right..

---

### Post by Topfs on 2007-06-28
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_XFCE_.28Xubuntu.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_XFCE_.28Xubuntu.29)

Change the how to install Xubuntu to sudo apt-get install ubuntu-desktop and then follow on through removing xubuntu and you should be fine.

Also bookmark [www.ubuntuguide.org](www.ubuntuguide.org) Have saved my skind SEVERAL times :)

Best of lucks

---

### Post by Jerr973 on 2007-06-28
Thanks seems to have all worked out fine just that after I removed xubuntu-desktop, was still booting with xubuntu upslash,  But did check with  "cat /etc/issue"  and says Ubuntu 7.04 \n \l
  so I guess did work, thanks alot again for your quick replies, I is much appreciated....;)

---

### Post by Topfs on 2007-06-28
I had the same problem when I first changed from Xubuntu to Ubuntu on my laptop.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_USplash_Screen_when_you_boot_or_shutdown_the_computer](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_USplash_Screen_when_you_boot_or_shutdown_the_computer)

This should fix it, the change of desktop enviornment doesn't always change USplash.

Also if you still have the blue background when loggin in and want the brown one it is changeable at.
System -> Administration -> Login Window
Under the tab local is a color picker.


I'm always glad to help out. I have just used linux for the past year or two and everyone in the ubuntu community is so helpfull, so it is nice to finally be able to help back :)

Best of lucks

---

### Post by IagainstI on 2007-07-04
This fix didn't work for me.  I've had this problem before, but reinstalled a fresh Ubuntu.  I can't reinstall now, but I don't like the Xubuntu USplash.  I'm wondering why this isn't working and how to fix it.  Any help is greatly appreciated.

UPDATE: Oh, nevermind.  I found the option on the Local tab of System -> Administration -> Login Window.

---

