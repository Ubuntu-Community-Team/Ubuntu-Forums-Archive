---
title: "Unable to Install Ubuntu 14.04 - Partitioner throws error"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by shibu_sawyer on 2014-09-30
Hi,

I got a problem on installing ubuntu 14.04 on my netbook, No matter what partition size i give i get this error message
"some of the partition you created are too small, Please make the following partition this large : /home 0TB0".

If i click continue my installation fails. 

I tried using xubuntu 14.04 too, it returned the same error. Not sure if this is a bug or what wrong.

I tried installing ubuntu 12.04 and it installed and worked like a charm, infact i am typing this from my ubuntu 12.04.

Attached is the screenshot. Any help would be really appreciated.

[ATTACH=CONFIG]256830[/ATTACH]

Thanks

---

### Post by shibu_sawyer on 2014-10-15
Any one has any idea about this...

---

### Post by sand7000 on 2014-10-15
Can you please take a screen shot that shows the partition sizes and mount points?  The error in your original screen shot covered that up.

---

### Post by shibu_sawyer on 2014-10-15
Hi,

Thanks for the reply.

At Present I do not have another screen shot, currently i am running 12.04.

These are my partition sizes :

/ - 8 GB
Home - 120 GB
Swap - 2 GB

I did not create other partitions, i found this is enough for a net-book to run. And currently i am running 12.04 with the same partition size and it installed smooth and works. Only when installing 14.04 i get this "[COLOR=#000000]some of the partition you created are too small, Please make the following partition this large : /home 0TB0[/COLOR]" error message.

---

### Post by sand7000 on 2014-10-16
The scheme you are describing should work fine, but a did some googling and found that other people have had the same issue.  Sounds like it is a bug.

Are you planning to mount the home directory on multiple OS (a different flavor of *nix on the same netbook I mean)?  If not the home directory being a separate partition is not necessary.  So you could try installing with just:

/ - 128GB
Swap - 2GB

---

### Post by shibu_sawyer on 2014-11-16
Yes ,guess its a bug cos the same partitioning scheme works fine for 12.04.

Thanks.

---

### Post by yancek on 2014-11-16
Don't plan on installing much software with an 8GB / partition.  Although the Ubuntu page indicates a minimum of 5GB needed, the second link below indicates it shows a minimum of 6.4GB needed.  I recall from my install it required 6+GB.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

