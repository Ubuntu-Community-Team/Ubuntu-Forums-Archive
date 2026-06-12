---
title: "Grub &quot;Unknown filesystem&quot;"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by anareis on 2010-07-14
Hi all,

I have a laptop with windows7 and ubuntu installed. When I installed Ubuntu it created 4 partitions (2 for swap and 2 for ubuntu). Yesterday, a friend of mine deleted one of the partitions (swap+linux) because they weren't being used (weren't even mounted) and he thought I could use the free space. I kept on using the laptop but today I had to reboot it. Instead of getting the usual grub menu I got this:
```
error: unknown filesystem.
grub rescue>
```

I tried using the solutions I found in lots of posts related with this matter but I couldn't fix it. What I tried was this:

```
#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot
```
from this thread [http://ubuntuforums.org/showthread.php?t=1493436]("http://ubuntuforums.org/showthread.php?t=1493436") and also tried stuff from [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

The problem is that it doesn't recognise the commands 'linux', 'boot' or 'initrd'... 
Can you please help me? And I'm new in this forum so I didn't know if I could edit a SOLVED post or if it was better to start a new one... so I'm sorry if I did wrong...

---

### Post by Rubi1200 on 2010-07-14
I am not sure what you have done, but something is definitely messed up.

I also don't understand why you would allow a friend, even a well meaning one, to fiddle with your setup and delete partitions; that is asking for trouble!!

Anyway, to cut a long story short and stop lecturing you here is my suggestion.

Get hold of an Ubuntu CD if you don't already have one and boot the computer with it.

Choose to try Ubuntu in live mode but do not choose to install.

When you are at the Desktop in Ubuntu and assuming you can connect to the Internet,
click on the link at the bottom of my post.

Follow the instructions there and post the results back here.

Please don't forget to wrap the text with the code # tag.

Once we see the results of the script it will be easier to help diagnose your problem and help you fix it.

Good luck!

---

### Post by anareis on 2010-07-14
Hi,

Thanks for your help but I asked my friend to correct what he had done and with the help of a live CD with ubuntu he managed to correct my problem.

He basically did this:

```
sudo fdisk -l

sudo mount -t ext4 /dev/sda2 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda

```

(Notice the difference from the url "ext4" instead of "ext3" as it said on the forum post)
Got it from here: [http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/")
Oh and btw, I though he really knew what he was doing so I trusted :P not happening again I guess! :)

---

### Post by Rubi1200 on 2010-07-14
Great that it worked out for you!

And you were lucky this time. I have seen plenty of cases where reinstalling the bootloader did not work because there were also other issues going on.

For future reference:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

