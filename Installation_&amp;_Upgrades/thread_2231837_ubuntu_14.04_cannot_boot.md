---
title: "ubuntu 14.04 cannot boot"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by dhp1990 on 2014-06-28
[FONT=arial]Hi,[/FONT][FONT=arial]I installed ubuntu 12.04 through wubi and then upgraded it to 14.04 a few days ago. It works well then. However, my PC cannot boot now. It stops at certain stage.( a picture is attached to show you what I saw)  I have tried the boot-repair software and the record is at [http://paste]("http://paste/").ubuntu.com/7715717/. I really want to rescue my system. I will appreciate it if you can help me out. Many thanks.[/FONT]

---

### Post by Bucky Ball on 2014-06-28
Please read this:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

If you want to stick with Wubi, go ahead, but don't expect a lot of help on these forums, unfortunately. Much better to install Ubuntu as a dual-boot, Win on one partition and Ubuntu on another. Wubi is virtually a thing of the past ...

---

### Post by dhp1990 on 2014-06-28
Maybe you are right. Could you please tell me how to get the data in my broken Ubuntu system? I need it badly.

---

### Post by ajgreeny on 2014-06-28
Ideally you'd use a live DVD/USB and mount the root.disk file which is in the windows filesystem,  and copy all you need from that (see below). If all you need to do is get the personal data off it you could also try [ext2read]("http://ext2read.blogspot.com/"), which gives read-only access to the root.disk direct from Windows, though how effective that might be with wubi I have no idea.


  If you do decide to access the root.disk that contains your data from the live DVD/USB, you can mount the old root.disk with command:
```
sudo mount -o loop /path/to/root.disk /mnt 
```changing that pathway to your own situation, of course.

  Then you can use the file browser to view and copy the files to another USB drive and later restore them to your new dual booted Ubuntu install..

---

### Post by hakuna_matata on 2014-06-28
> **dhp1990 said:**
> ([FONT=arial] a picture is attached to show you what I saw)[/FONT]
I don't understand the message in your language, but I assume it is the same problem like here: [http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

edit: Another link with same problem and solution:  [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-temp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-temp-could-not-be-mounted)

---

