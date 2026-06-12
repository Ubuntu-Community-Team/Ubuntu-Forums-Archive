---
title: "Install Ubuntu alongside Windows 7"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by shelef on 2013-04-02
I want to install Ubuntu alongside my Windows 7. I defragmented my C: drive and shrink it.
I then started the Ubuntu installation which I burned on CD. I followed the installation [guide]("http://www.ubuntu.com/download/help/install-desktop-latest") from the official site. I did step 3 and choose my wireless. According to the guide I supposed to arrive step 4 and install Ubuntu alongside Windows 7. But instead I arrived this place:
What did I made wrong? Why I didn't get an alongside installation?

---

### Post by darkod on 2013-04-02
This usually happens if the hdd has been used in raid before and it still has meta data remains. If you are NOT using raid, boot the ubuntu cd in live mode (Try Ubuntu), open terminal and run:
```
sudo dmraid -Er /dev/sda
```

If there is meta data, that will ask you if you want to remove it. Confirm and start the install again, it should work.

Note that you only run the above command if you are not running raid, since if you are, it can break your existing array.

---

### Post by shelef on 2013-04-02
My knowledge in hardware is very small. so actually I dont know if i using raid. I took this pictures. it might help.

If it doesn't enough, how can I check if I'm using RAID?
I understood from you what to do in the case Im doesnt using RAID. But if I do, how do I install ubuntu?

---

### Post by darkod on 2013-04-02
Small or big HW knowledge, you should know your machine and what you have. :)

The image didn't post, don't insert images in the text, use the Advanced options when posting and post them as Attachments.

For raid you would need at least two physical disks. Do you know at least whether you have one or two HDDs in the machine?

---

### Post by shelef on 2013-04-02
> **darkod said:**
> Small or big HW knowledge, you should know your machine and what you have. :)

The image didn't post, don't insert images in the text, use the Advanced options when posting and post them as Attachments.

For raid you would need at least two physical disks. Do you know at least whether you have one or two HDDs in the machine?
I added a link.
[http://s22.postimg.org/lbnu3vits/aaa.jpg](http://s22.postimg.org/lbnu3vits/aaa.jpg)

---

### Post by darkod on 2013-04-02
Looks like only one single disk. It should be OK if you run the dmraid command.

---

