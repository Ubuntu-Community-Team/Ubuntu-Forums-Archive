---
title: "Hoping to avoid my old issue again."
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by laprairie4 on 2011-02-16
[SIZE=2]So the last time I installed Ubuntu, I ran into the 'Operating System Not Found' problem. I eventually gave up and formatted and reinstalled my copy of Windows. I am hoping to avoid that same problem once again.

From what i remember of my first install, I used the slider bar to partition Windows without formatting. I could boot into Ubuntu fine, but after I booted into Windows, and then shutdown, my boot loader (I would assume to be the GRUB loader) never showed. All that came up was something about abort and press any key to exit. Press my any key, no OS found, and repeat the process. [/SIZE] [SIZE=2]

When I formatted and reinstalled Windows, I partitioned off 50 GB for my eventual install of Ubuntu. I don't know how to properly set up this partition to install, and I don't want to have to back up and reinstall all over again.[/SIZE] [SIZE=2]

Can anyone help me through the install? I'm currently sitting at the 'Allocate Drive Space' screen. Thanks in advance.[/SIZE]

---

### Post by sikander3786 on 2011-02-17
Welcome to the forums :-)

We'll surely try to help you the most. Install alongside other OS option in Ubuntu installer is not recommended at present due to a bug. Instead, go for Manual partitioning. See here for a simple guide.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

And the issue Operating System not found means that you didn't successfully install Grub (Ubuntu booloader). I think there is just one HDD in your system and in that case, the bootloader needs to be installer to its default location i.e, MBR of your only HDD. See the Grub section at the bottom of page I linked above.

If you've got further queries, You are Welcome :-)

---

### Post by laprairie4 on 2011-02-17
okay so I understand how to set up everything but the GRUB loader part. my options are:

/dev/sda ATA WDC WD5000BEKT-7 (500.1 GB)

/dev/sda1 Windows 7 (loader)

/dev/sda2 (which is my install location of windows 7

/dev/sda5 (has the / mount point)

/dev/sda6 (which is where i set my /home)

I have a feeling that my boot loader is where I went wrong last time, but I'm not certain. So which one should I use?

---

### Post by sikander3786 on 2011-02-17
> /dev/sda ATA WDC WD5000BEKT-7 (500.1 GB)

This is where your Grub loader should be installed. I hope everything goes fine for you.

---

### Post by laprairie4 on 2011-02-17
okay well that's the one i used last time so we'll see how it goes... wish me luck people, thanks for the help

---

### Post by sikander3786 on 2011-02-17
> **laprairie4 said:**
> okay well that's the one i used last time so we'll see how it goes... wish me luck people, thanks for the help
All the good lucks to you :-)

And let us know how that goes and if you need further assistance ;-)

---

### Post by laprairie4 on 2011-02-17
well, i booted into ubuntu just fine as i did last time.. time to boot windows, then restart

---

### Post by laprairie4 on 2011-02-17
I booted windows just fine and am now back into Ubuntu. When I booted Windows, it said something about startup repair, but I figured it was telling me that because the normal Windows loader had been replaced with the GRUB loader, so I skipped it and started normally. and now it's working fine. @[sikander3786]("http://ubuntuforums.org/member.php?u=806649"), thanks, you've been a big help.

---

### Post by sikander3786 on 2011-02-17
You are most Welcome. Hope you enjoy your stay with Ubuntu.

Happy Ubuntu-ing!

---

