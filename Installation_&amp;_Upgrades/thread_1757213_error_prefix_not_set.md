---
title: "error prefix not set"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by cure2001 on 2011-05-13
I installed from wubi when I restarted and went to boot up ubuntu I got the error prefix not set.

wn7 64

please help

---

### Post by varunendra on 2011-05-14
Did you search WUBI megathread? See this post: [http://ubuntuforums.org/showthread.php?p=10771873#post10771873](http://ubuntuforums.org/showthread.php?p=10771873#post10771873)

According to the above post by bcbc (expert in WUBI),
> In terms of warnings/messages, there's the one grub boot message about  the "prefix not being set". This is new in Natty, but it is a known  issue and harmless.

So what happens after getting this message? Posting the exact error messages would be helpful.

---

### Post by cure2001 on 2011-05-14
it throws me to grub command prompt

---

### Post by varunendra on 2011-05-19
Well, for best advice, bcbc is your man! Follow these links and his suggestions to see if any works for you:
[https://answers.launchpad.net/wubi/+question/154912](https://answers.launchpad.net/wubi/+question/154912)
[https://answers.launchpad.net/wubi/+question/144942](https://answers.launchpad.net/wubi/+question/144942)
[http://ubuntu-with-wubi.blogspot.com/](http://ubuntu-with-wubi.blogspot.com/)

---

### Post by tj4linux on 2011-05-28
hi cure2001 have you sorted this error...!!! I started receiving 2 days ago :P

---

### Post by Rubi1200 on 2011-05-28
> **tj4linux said:**
> hi cure2001 have you sorted this error...!!! I started receiving 2 days ago :P
Did you check the possible solutions in the links provided by varunendra?

---

### Post by tj4linux on 2011-05-28
I saw them... but i didnt tried them yet... I dont know if they will work... or trying them should not lend me with some other issues.. :P

---

### Post by bcbc on 2011-05-28
This error message was reported to the developer and he stated that it wasn't causing any problems and he wasn't going to try to fix it (in case something broke in the attempt). See comment 28 and 29 [here]("https://bugs.launchpad.net/wubi/+bug/693671/").

My natty wubi install(s) have all reported this "error" on every startup. 

So... I think there is likely some other problem and you're assuming it has something to do with this error message.

My steps to trouble shoot would be:
If you don't see the grub menu
==============================
1. confirm that the file \ubuntu\disks\root.disk exists or find it (search by name and/or size since windows chkdsk will sometimes rename files it considers corrupted)
2. back it up once you find it
3. run chkdsk on windows.
4. if you still can't boot, boot a current Ubuntu CD ("Try it" without installing) and [fsck the root.disk]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?").

If you see the grub menu but booting fails
==========================================
1. Try the recovery mode and try to repair if that works
2. Try an older kernel if you have one available
3. Boot a current Ubuntu CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results, then post them on a new thread asking for help if you can't get it working.

---

### Post by Payero on 2011-09-22
For what is worth, I was having the same issues after having Ubuntu 11.0.4 up and running for over a month.  After looking at the files system under Windows I noticed that my root.disk file had 0 bytes.  Something, either Windows 7 or Ubuntu itself, corrupted the file.  Luckily I had a backup of my computer including my ubuntu install so I was able to recover by replacing the bad root.disk file with a previous version.  Hopefully this information would throw some light into this problem.

---

### Post by abtexas130 on 2011-12-24
OK I had this same error.  I do not know what but their is something wrong with the new wubbi the orange one.  I had to install Ubuntu 11.04 from the old wubbi and then get the upgrade.  The reason my computer crashed and burned earlier is because I was working with the split command trying to learn more about the terminal and large text files.  Then it crashed i rebooted and then got the message prefix not set.  Frustrating.

---

### Post by mem0l on 2012-02-05
sorry guys but i surly reach this blief that u are so weak at answering this problem...
i like linux but when i can not soleve my prob so i cant use it..
pls tell us a clear answer
tanks

---

### Post by fachex on 2012-10-05
I am not using Wubi and I've got the same error. I do have software raid thou.

---

