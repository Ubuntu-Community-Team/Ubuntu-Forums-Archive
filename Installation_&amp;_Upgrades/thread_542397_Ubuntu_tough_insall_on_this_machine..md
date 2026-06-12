---
title: "Ubuntu tough insall on this machine."
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by stevelasvegas on 2007-09-03
I have Ubuntu installed on my laptop; I used WUBI. Everything there is good.
Now I want to put Ubuntu on my desktop. I would really like to do it without the training wheels (WUBI), but maybe later (that looks like it's going to be a REAL headache).
So, I installed WUBI and rebooted into Ubuntu but as far as I can get is a black screen that says;
Booting GRLDR.....
Turning on gate A20... success.
And then it stops, with no disk activity.
Here's the info I think is important.
I sure hope someone can get me past this, I really want Ubuntu running on my desktop.
I would like to have the WUBI folder on K:. K is a SATA drive.
Thanks for any help you can provide.
[IMG]http://farm2.static.flickr.com/1231/1314658197_ad0c52fbf7.jpg?v=0[/IMG]

---

### Post by stevelasvegas on 2007-09-05
[IMG]http://farm2.static.flickr.com/1040/1331773659_8f2404735d.jpg?v=0[/IMG]
[IMG]http://farm2.static.flickr.com/1382/1332662492_a5734aa107.jpg?v=0[/IMG]

OK, so I'll try and do a 'real' installation and not use WUBI.
I want to install Ubuntu in the partition Windows refers to as Linux L: but it doesn't seem to be an option during the install using Ubuntu current Live CD.

---

### Post by Pumalite on 2007-09-05
Post your specs. You might need Alternate CD or some other guidance.

---

### Post by stevelasvegas on 2007-09-06
This conversation has moved here [http://ubuntuforums.org/showthread.php?t=542397](http://ubuntuforums.org/showthread.php?t=542397).

---

### Post by dabl on 2007-09-06
If it's true that the partition "Linux L:" is formatted NTFS, then that's a problem -- you can't install Linux on NTFS. You'll have to make it ext3 or reiserfs.  The other possible problem is that Ubuntu will require a miniumum of 2 partitions, but maybe you were going to deal with that during the installation process, by splitting "Linux L"?

---

