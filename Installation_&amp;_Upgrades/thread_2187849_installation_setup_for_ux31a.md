---
title: "installation setup for ux31a"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by meceo00 on 2013-11-14
hi guys,

I think it would be great if somebody who owns ux31a would share his setup, like:
- what partitions are set, why?
- is swap on/off, why?
- maybe more tips?

I find ubuntu problematic on my ux31a. I have 13.10 upgraded from 12.04.

I often have memory issues (running out of memory and system slows down). I have swap partition but it's turned of, because when system starts to swap it gets frozen immediately! Macbook air with similar configuration (4gb ram, same cpu) but macOS deals with memory consumption much better than my ubuntu and I don't understand why.

I have also too small "/" partition, because with every kernel upgrade I need to remove previous one (no enough space). I have chosen wrong partition size.

As you can see I don't know how to setup ubuntu installation properly. I would really appreciate if somebody could tell how to do that. We all have same hardware so it should be easy to everyone like me to copy exact setup and enjoy better experience with ubuntu.

Thank you

---

### Post by oldfred on 2013-11-14
Some other threads.
 Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)

Is system UEFI or BIOS? And are both Windows & Ubuntu in same boot mode? 

I find only my 7 year old laptop with only 1.5GB of RAM uses swap. If you have 4GB or more of RAM you should not really need swap but we normally suggest a little just in case. Or do you normally open just about every app you have and then try to edit large videos? That consummes an unlimited amount of RAM.

I do not know specific settings that your computer may need. Threads above may give some clues.


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by meceo00 on 2013-11-17
hi oldfred,

Thank you for your answer.

"[COLOR=#000000]I do not know specific settings that your computer may need. Threads above may give some clues.[/COLOR]"

I bet everyone with ux31a and ubuntu would be able to help with configuration. Hardware in this case is the same (as in apple machines). The whole point is to get configuration / tips from ux31a owner who is also advanced ubuntu user.

I use laptop at work to develop web applications. Usually I have many browser tabs open, sublime editor, many terminals. The same workspace as my coworker with very similar hardware (macbook air) but apple OS. My configuration can not handle running out of memory, his can pretty well.

maybe there is somebody who owns ux31a and shares

---

