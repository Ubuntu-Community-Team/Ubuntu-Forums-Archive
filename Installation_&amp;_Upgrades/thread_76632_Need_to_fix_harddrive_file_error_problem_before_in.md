---
title: "Need to fix harddrive file error problem before install"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-10-15
Hi a while ago my Ubuntu gave me an error stating something about ext3 becomming unstable and reverting to ext2 on boot it says its usung ect 2 but on mount output in terminal it stats ext3. How do I fix this. I tryed some scan before and it gave me a cannone do it while volume is mounted error and how it can damage the contents. Any help would be apreciated. Woo Hoo im finaly getting around to installing 5.10

---

### Post by SilentCacophony on 2005-10-15
If you're going to do a fresh install into that partition, when you get to the partition setup, you can just select 'manually edit partitions', select the partition in question, set it as ext3 filesystem, and select the option to format it. Also set the mount point.

---

### Post by Omnios on 2005-10-15
I might try that but realy want to fix it before the install just in case.

---

### Post by Omnios on 2005-10-15
Actualy my back up computer is not set up yet so I want to try to solve this problem before attempting th install. The things that bother me about this are.

1: On boot up Lunux stats its mounting my main Linux drive as ext 2 and on boots stats its ext 2

2: In gnome and KDE when I do mount in terminal it shows it as ext 3 

 This is making me think that there is something wrong here such as a bad sector or a currupt portion which I would like to fix it before trying an install.

---

### Post by Omnios on 2005-10-15
[QUOTE=SilentCacophony]If you're going to do a fresh install into that partition, when you get to the partition setup, you can just select 'manually edit partitions', select the partition in question, set it as ext3 filesystem, and select the option to format it. Also set the mount point.[/QUOTE]

 Um the thing about setting the mount point It is my main install drive which is / anyways will it do / automaticly? Though I have had Ubuntu for about 6 months now I realy didn't find I had to do many reinstalls.

---

### Post by Omnios on 2005-10-15
All fixed up and finished the install pretty impressive so far.

---

### Post by pksings on 2005-10-19
To do this you will need to boot from a different source and then check/fix the disk. I recommend either the "Live" CD or Knoppix. 

Upon booting and getting to a shell prompt, fsck /dev/hdXX (whatever one to fix), repeat until no errors.  I usually run fsck with a -y flag so It doesn't ask me whether or not I want to fix the errors, I wouldn't be running it if I didn't.

Hope this helps...

PK

---

