---
title: "Installation problems"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by thiagof on 2012-06-22
Hi everybody!
I was trying to install the ubuntu 12.04 in my computer, that already has windows on it! So I partitioned it before, on Windows, and then proceed to installation. When I got to the point that I had to partition manually, i searched for my newly created windows partition, and deleted it, so that i could free space to ubuntu. I created one partition for the OS, but as I was not sure  if the partition that i had deleted was the right one, I didn't proceed with the installation, and I quit the process, just to double check in Windows, if that was the right partition. When I tried to startup Windows, I couldn't, and when I got back to the ubuntu, using the CD, I could see the partition I created during the instalation, which is weird, because I didn't hit the "Install now" button, so the changes I did were not supposed to continue after restarting the computer! Does anybody knows what can I do to solve this problem?

---

### Post by dino99 on 2012-06-23
formatting is one thing, installation is an other one; you should understand that first. Then when you said: i'm not sure about the partition i've deleted, wow you're a scary dude.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by hansdown on 2012-06-23
Welcome to the forum,thiagof.

Apparently,I drew the short straw, so I need to tell you that your windows install "may" be gone.

Do you have a windows install disk?

Not the Reinstall ones.

---

### Post by darkod on 2012-06-23
Why would you create a partition for ubuntu in windows, knowing that it doesn't install on ntfs, just so you can delete it later in the ubuntu installer? If you just left that space as unallocated, you would have had exactly what you needed, unallocated space where you can create your ubuntu partitions.

Stop using that hdd, don't try to boot it any more!!!

Boot with the ubuntu cd in live mode (Try Ubuntu), open terminal and post the result of:
```
sudo fdisk -l
```

If you can, explain under the results which partition is what, you should be able to tell according to their size.

After we see that we can continue. Even if you deleted the windows system partition there is great chance it can be recovered as long as you stop using the hdd.

---

