---
title: "Help me please I am an idiot"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by Jimbabwe on 2007-02-10
OK where to begin? First thing's first: I can't update. The update manager icon in the top right corner tells me I have 25 updates but when I click on it, nothing happens. It thinks for about a tenth of a second and does nothing more. When I try to use the command prompt i always get the same answer for anything "sudo __". here is a copy paste of my prompt:

jimmy@bishop:~$ sudo apt-get upgrade
sudo: can't stat /etc/sudoers: Value too large for defined data type
jimmy@bishop:~$ sudo apt-get update
sudo: can't stat /etc/sudoers: Value too large for defined data type
jimmy@bishop:~$ gksu "update-manager -c"
sudo: can't stat /etc/sudoers: Value too large for defined data type
jimmy@bishop:~$

I don't know what this means because I am a total n00b and I've been using Ubuntu for a year and this is the first time i've had problems.

Also, i don't know if this is related but for some reason all the fonts on my computer changed one day. Like the menu toolbars got bigger and the fonts in windows got smaller. AND I can't uninstall azereus. Which is annoying. Somebody help me please!!

---

### Post by LotsOfPhil on 2007-02-10
Looking around, I think you're root password might be corrupted. 

For example: [http://forums.swsoft.com/showthread.php?threadid=30142](http://forums.swsoft.com/showthread.php?threadid=30142)

---

### Post by housam on 2007-02-10
Did you tried system >> admin. >> update manager.

---

### Post by Jimbabwe on 2007-02-10
No I don't think my password is corrupted, I can still switch to root no problem. I still get the same output when I try to do anything sudo. If this helps understand what's going on at all, when I pressed the up arrow key in the prompt to see my previous commands, i got this weird thing which I definitely did not ever input:

root@bishop:/home/jimmy# CLIENTADD "IOR:010000001700000049444c3a436f6e6669674c697374656e65723a312e300000030000000054424f540000000101020005000000554e4958000000000a0000006c6f63616c686f73740000002a0000002f746d702f6f726269742d726f6f742f6c696e632d333136642d302d3536346561656133616636346600000000000000caaedfba54000000010102002a0000002f746d702f6f726269742d726f6f742f6c696e632d333136642d302d353634656165613361663634660000001c00000000000000925ec4f0f579e8a8282828282828282801000000becd2feb01000000480000000100000002000000050000001c00000000000000925ec4f0f579e8a8282828282828282801000000becd2feb01000000140000000100000001000105000000000901010000000000"

And yes, I tried going sys>admin>update but it does the same thing, nothing. Thanks for the replies though. Any more ideas?

---

### Post by LotsOfPhil on 2007-02-11
If you can switch to root, can you check out your /etc/sudoers file?
i.e., type "visudo"

This is just a shot in the dark though.

---

