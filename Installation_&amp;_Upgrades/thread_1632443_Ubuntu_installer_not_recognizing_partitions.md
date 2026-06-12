---
title: "Ubuntu installer not recognizing partitions"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by sadiq-ali on 2010-11-28
I'm trying to install Ubuntu 10.10 from my live USB disk. In My computer, it is showing all drives correctly, but when I try to install using the installer on desktop, it is showing the whole hard disk as free space and no partitions at all.

when I tried 'sudo parted' and then print command, I got the below error message.

Error: Can't have a partition outside the disk!

I formatted the C drive from linux using ext4 filesystem. 

How can I make the ubuntu installer recognize my partitions?

---

### Post by wet-willy on 2010-11-28
Is it mounted when you go to do the install?

---

### Post by sikander3786 on 2010-11-28
Welcome to the forums :-)

From your Bios menu, switch your HDD mode to "ahci" or compatible if available.

Try installation again and if that doesn't yet show the partitions, post the output of

```
sudo fdisk -l
```

---

### Post by srs5694 on 2010-11-28
The "sudo fdisk -l" command that sikander3786 suggests will display results with cylinder precision, which is likely to be inadequate for proper diagnosis. You must add a "-u" option to get sector precision, as in:

```

sudo fdisk -lu

```

Chances are your problem is the one described on [this Web page of mine.](http://www.rodsbooks.com/missing-parts/index.html) I recommend you read it and post back here (including the "sudo fdisk -lu" output, presented between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility) if you've got more questions.

---

