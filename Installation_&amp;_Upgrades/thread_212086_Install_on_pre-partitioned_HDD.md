---
title: "Install on pre-partitioned HDD"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by indijay on 2006-07-09
Hello All,

So I am desperately trying to switch from Windows to Ubuntu but I have issues with installation.

I am using HP AMD64 3400+ machine with 1024mb RAM and 250GB HDD which I partitioned into 3 partitions using partition magic. (Screenshot 1) One partition of 29GB is solely for (planned) linux. You can see 2 linux swap drives but they are created by Ubuntu when I use it as live CD.

Now I want to install it. It offers me to prepare disk space during installation. Since I want a dual-boot, I choose to "manually edit the partition table" and I am offered Screenshot 1.
I select 29GB partition as root and those linux swap drives as swap (Screenshot 2)
After confirming the disks, the installation looks like have begun but...........it offers me Screenshot 3.

I will be glad if anybody can help me with this installation

And yes, I can not mount any partition on live CD, any explanation for that??

Thanks a lot

---

### Post by RRS on 2006-07-09
Is this your only hard drive or is windows installed on a different drive?

Looking at screenshot 1 it appears that windows may be on hda2. If so, what is hda1 used for?

As for the other partitions, you only need 1 swap (app. 1.5x to 2x your ram) and your Ubuntu partitions (/ and /home) should be formatted as ext3.

Also, instead of Partition Magic I'd use Gparted from the live cd. PM sometimes has issues with Linux.

Use [this guide]("http://psychocats.net/ubuntu/windowstoubuntu.html") for the partitioning and installation procedure. It's the best I've seen for using the desktop (live) cd.

---

### Post by indijay on 2006-07-09
You are very true, hda2 has my windows installed in it. Since I am not good at partitioning and booting things, I though PM would be an easy option.

Another thing is, so far my understanding was that / and home drives are same so if you keep one drive as / then by default it turns /home, which doesn't seem to be the case from your post. And then comes making them ext3.

My apologies but this is bit beyond my understanding at this moment, can you please bit elaborative?? Meanwhile, I will go through the guide that you suggested.

---

### Post by RRS on 2006-07-09
Sorry it took so long for me to get back, did Aysiu's guide help?

Your understanding of / and /home is partially correct. The / (called root) partition contains the system operating files while /home contains the files with your personall settings and data. Many users (myself included) install with / and /home on the same partition.

The main reason to install them on seperate partitions is so you can upgrade or reinstall at a later date without having to reset all your personal settings and changes you've made along the way.

It would probably be easier to put your entire Ubuntu installation on one partition. You can always create a new partition and move /home later after you've become more comfortable with Ubuntu. I seem to have trouble learning more then one new trick at a time anymore myself.

My suggestion would be to use partition magic to reset things to original, I'm guessing the entire drive was NTFS for windows. Then follow the directions in the link to install using the cd's partitioning tool.

Also it can't be restated enough; though 99.9% of the time everything works fine always backup any important data first and it also helps to run a couple defrag cycles in windows before partitioning/installing.

I hope I've helped make things a little clearer for you. Don't hesitate to ask if you still have questions.

---

### Post by indijay on 2006-07-10
Thanks for your reply.

Infact, the link that you provided di help me with understanding the 3 partition options and as the guide suggests that first option should be selected if someone prefers dual boot system.

In such scenario, I have windows installed on 33GB partition but this partition is shown as 56GB on screen. I don't know where this 56GB came from and honestly I am really afraid to touch that windows partition because the restore disc that I have got from the company will restore it to factory settings and it will be a LOT of work to set up system again.

I will still give a try over the weekend and see.

One query though, any idea why I can't mount any drives in Live CD??

---

