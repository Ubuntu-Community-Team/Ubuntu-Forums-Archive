---
title: "partition problem"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by bdrnetmail on 2012-09-07
I would like to undo an extended partition i have just done on my laptop.I am currently running ubuntu 10.10 off the cd and used the disk utility to start the install.I can no longer see my windows files.

---

### Post by darkod on 2012-09-07
Can you post a screenshot please? Lets see what's there.

---

### Post by bdrnetmail on 2012-09-07
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-3.png[/IMG]I can take the screen shot but it doesn't appear to want to paste here.

---

### Post by bdrnetmail on 2012-09-07
sorry i was expecting to see the shot

---

### Post by darkod on 2012-09-07
You can use the Screenshot application in ubuntu (not 100% if 10.10 has it) which can save it as JPG. After that simply attach the JPGs to the post, there is Manage Attachments button below when writing the post.

---

### Post by bdrnetmail on 2012-09-07
[IMG]file:///tmp/moz-screenshot-5.png[/IMG]/home/ubuntu/Pictures/Screenshot-160 GB Hard Disk (ATA Hitachi HTS543216L9A300) [-dev-sda] — Disk Utility.png

is this any good for you ?.

---

### Post by oldfred on 2012-09-07
In the edit panel above your message is a paperclip icon. click on the paperclip and it will open a window for you to upload files.

---

### Post by bdrnetmail on 2012-09-07
not sure if it's uploaded or not.

---

### Post by darkod on 2012-09-07
No windows partition that I can see. You created the logical partitions over the windows partition it seems. Were you doing this with the windows Disk Management or ubuntu tools?

---

### Post by bdrnetmail on 2012-09-07
the windows partition is the extended one that's why i want to undo my mistake. I was using the disk utility in ubuntu 10.10 from the cd.

---

### Post by darkod on 2012-09-07
I know the extended partition is in its place, but it's not the windows partition any more, that's what I'm saying. Next time use windows Disk Management for managing ntfs partitions, especially the partition where windows is installed.

I am not sure you can undo this in the real meaning of the word, there is no undo button in partitioning.

What you can try is scan the disk with testdisk and see if it can recover your old partition table (with the old partitions).
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you have any questions after doing the Deeper Search, post a screenshot and ask. You can do all of this from live mode.

---

### Post by bdrnetmail on 2012-09-07
Thank you will give it a try

---

### Post by bdrnetmail on 2012-09-09
I downloaded test disk but so far can't get it to run. sudo apt-get install test disk comes up with "unable to locate packege" I have  tried putting it in different folders but still no joy. I have made a usb boot stick and tried it with that.I've also tried archive manager,synaptic package manager but still it won't open. any thing else i should be doing.

---

### Post by darkod on 2012-09-09
If you downloaded it, you don't install it, you just run it from the location where it is. I think the main file is called testdisk_static or similar.

Open the terminal and browse to the folder where it is, then simply run it with like:
```
sudo ./testdisk_static
```

---

### Post by bdrnetmail on 2012-09-10
All i get is command not found.

---

### Post by darkod on 2012-09-10
As I said, you need to find the testdisk_static file. When you unpack the downloaded archive, it usually creates one testdisk-version_number folder. Inside that folder there is linux subfolder, and inside that is the testdisk_static.

Go to that directory and run it with the command I posted earlier, but only if you are at the right place. You can list folder content with ls.

Screenshots attached.

---

