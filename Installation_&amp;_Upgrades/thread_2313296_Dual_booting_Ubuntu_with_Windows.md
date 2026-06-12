---
title: "Dual booting Ubuntu with Windows"
date: 2016-02-11
forum: Installation &amp; Upgrades
---

### Post by alex503 on 2016-02-11
hello everyone.

I installed Ubuntu like the 2nd os and had got a problem. After process of installing pc required a password for hard ****. Have no idea haw to deal with it

below I described the installation 

1) create a bot flash 
2) bot from flash 
3)choose a part of hdd (i ve had divided hdd before installation on windows 7 and than just reformated it to ubuntu's file system )
4)set all check boxes like update after installation download drivers for mp3 (i don't remember well)
5)after installation was over I pressed  button restart(button appear after installation)
6)and after reboot blue rectangular windows appears with text "enter hdd password".

please help me )) in the best case I'd like to get both os to work but at lies windows )) 

thanks in advance.

---

### Post by howefield on 2016-02-11
Thread moved to the "*Installation & Upgrade*" forum for better support.

---

### Post by slickymaster on 2016-02-11
Hi alex503, welcome to the forums

I moved your post to a thread of its own in the Installation & Upgrades sub-forum, which is the proper venue for it.

---

### Post by yancek on 2016-02-11
Some major changes have been made in the way computers boot in recent years so it is necessary to know "which" version of windows you have installed as they have been licensing systems for 30years.  During the installation of Ubuntu, it is mandatory to create a user with a password.  That user and password is created by the user or the person who is installing the system.  If you have some other password necessary to access the BIOS or for encryption that is different.  

During the installation of Ubuntu, you should have several options and to help you we need to know which you selected.  Install Alongside, Erase disk, Something Else.
To start, provide the information requested above and also boot the Ubuntu install medium again, open a terminal after it boots with the Try Ubuntu option and enter the following command and post the output here:  sudo parted -l(Lower Case Letter L in the command)

Can you post the image of the "blue" rectangle you mention.  Doesn't sound like Ubuntu.

---

