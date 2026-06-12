---
title: "From 6.10 to 7.04 without Internet"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by O-pos on 2007-04-05
Hello,

I've installed Ubuntu 6.10 and I like it, but there's wireless communication problem, so I think to upgrade it to 7.04 beta, because I've read that 7.04 has more advanced wireless networking tools. however, like I said, I have to do that without internet. I've already burned 7.04 iso as an image on the CD. How can I now update my linux?

I have dual boot, with shared data partition (exp3, including "home"). So I want the data and settings on that partition to be maintained. In addition, I have no linux skills yet, I'm newbie.

---

### Post by bollix47 on 2007-04-05
Try the following:

Open a Terminal (Applications - Accessories - Terminal)

Insert your 7.04 cd

Copy and paste the following into your open Terminal:

```
sudo apt-cdrom add

```

This should add the cd-rom to your repository list.

To upgrade copy and past the following into your Terminal:

```
gksu "update-manager -c -d"
```


DISCLAIMER:  I've never done this but it's the way I would try if I was in your situation.

---

### Post by bollix47 on 2007-04-05
Perhaps easier would be to simply boot your computer with the 7.04 cd in your drive and install 7.04.  You would reformat just your root partition (/) but not your /home partition or other data/windows partitions.

---

### Post by O-pos on 2007-04-05
Thanks, I'll try.

---

### Post by O-pos on 2007-04-06
First choise didn't work, so I'm trying the second one.

More specifically, I should jout install only "/", right? I mean I don't have to install "home" for it can  leave the old "home" with it's settings and shared data.. right?

---

### Post by bollix47 on 2007-04-06
Yes ... just make sure you don't format /home or any windows partitions.

---

### Post by O-pos on 2007-04-06
When I reach the partitions part of the installation, there's window "prepare partitions", I select only the partition where I have "/", but it says "no root file system is defined, please correct this from the partitioning menu". what should I do?

---

### Post by bollix47 on 2007-04-06
You have to tell the installer where /, home, and swap will reside.

For example my / is on /dev/sda6 and my /home is on /dev/sda7.

After telling the installer where these file systems will reside and making sure the /home is where it was before you will notice down the right side a small box for each one where if you check that box it will format that partition.  So, make sure there is no checkmark in the /home box.

For more info on this whole process have a look [_here_]("http://www.psychocats.net/ubuntu/index").

---

