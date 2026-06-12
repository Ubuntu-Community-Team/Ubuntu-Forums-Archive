---
title: "Missing Auto Partition Option in Install"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by tonofclay on 2006-07-07
I don't have very much experience with Linux and no partitioning experience, so when I saw that Ubuntu made it easier for less knowledgable people to partition their drives, I thought it would be for me. I have been running off the live cd for a few days now, and after getting my wireless network working with Ubuntu I decided it was time to install. Unfortunately when I got to the partition section of the install, I saw only two options, as opposed to the three I was expecting. The first was to erase the drive completely, and the second was to manually partition the drive. Its my understanding however that there should be another option before either of these two allowing for Ubuntu to recommend what to do. This option is missing however and I don't feel comfortable partitioning the drive myself. I've tried both the LiveCD and the Alternate CD, neither have the option...

---

### Post by Herman on 2006-07-07
[IMG]http://users.bigpond.net.au/hermanzone/p2d/9fat32.png[/IMG]
This option in above image is how to automatically partition your drive in the 'Alternate' Install. You will be given a suggested default size for your Windows partition in the next frame, and you can backspace over that and type in any size you want for your Windows partition instead. Then the Ubuntu installer will automatically divide  your free space thus created and make you an ext3 partition for your main Ubuntu root filesystem and a swap area for Ubuntu.
For an illustrated site to help you with the 'Alternate' CD installer, [*Click Here.*]("http://users.bigpond.net.au/hermanzone/")

[IMG]http://img230.imageshack.us/img230/2340/w2u260tf.png[/IMG]
The image above shows the equivalent option to be found on the 'Desktop' Live/Install CD. 
There is a very helpful site to guide you through the process using the 'Desktop' Live/Install CD, [*Click Here*]("http://www.psychocats.net/ubuntu/installing.html").

Even if that option really is missing, it isn't really very hard to manually partition the drive yourself when you use one of these install sites to help you. Otherwise you might be better off waiting and just be happy with the Live cd for a while until you are ready. I remember I found it a little scary at first too my first time when I didn't know what to expect to happen next or how to deal with it. The 'Warty' partitioner (an ancestor of the Dapper 'Alternate' Installer), was my very first partitioner I ever used and there were no install sites to guide me.
I hope one of these will help, all the best, Regards, Herman :D

---

### Post by Herman on 2006-07-07
...unless maybe the installers are detecting something they aren't too sure about in your partition table and it wants to protect your existing partitions by refusing to do anything. In that case manual partitioning probabaly won't work either, and you (probably) can't install Ubuntu in that computer, or at least on that hard disk.

Are you *sure* you really aren't getting that option?

---

### Post by tonofclay on 2006-07-07
Sorry I didnt post a screenshot, I was back on Windows at the time, but here is a link to a thread I made in beginners forum.

[http://ubuntuforums.org/showthread.php?t=211053](http://ubuntuforums.org/showthread.php?t=211053)

My thread seemed to have died there so I thought I might get more help at the installer specific forum. There is a screenshot there though, so you can clearly see that the option is not present. I don't have a screenshot from the text-based installer but I can assure you that it is not present there either.

---

### Post by Herman on 2006-07-08
Wow! You're right, it isn't there at all is it?

Well, as I said already, probably manual partitioning won't work either. You can try it though, and if it does work, then good! :D

(In my opinion) this is Ubuntu Installer's way of 'bowing out' and failing on the safe side.  Chances are it has detected something it feels it does not agree with in your partition table, perhaps an error made by another partitioner you may have used in the past, or some kind of boot sector virus activity, a buggy BIOS or something and chances are you will just not be able to install Ubuntu on that disk. 
Probably it would be best to just leave well enough alone and refrain from forcing things and just be happy with what you've got. Especailly if you are not that much practiced with partitioning disks and installing operating systems. Try on some other machine first.

Sorry, but that's my honest opinion for now anyway, Regards, Herman.

---

### Post by Brigitte on 2007-09-02
I'm having this same problem, but I know why.
I had first tried installing Ubuntu by clicking the button on the desktop.
When I got to the partitioning section I pressed the first option, but I was also browsing sites on Firefox. I accidentally EXITED the partitioning thing when it was barely starting.

So now... I only get the other two options.
I want to keep Vista so I do NOT want to use the "second" option of partitioning the whole drive.

What do I do now?

---

### Post by Pumalite on 2007-09-02
With Vista, you have to partition with Vista's partitioner; otherwise Vista won't let run anything in that computer.

---

### Post by amo310 on 2007-12-23
I just had the same problem when trying to install. I'm not sure if this will work for you but all I did was unmount the windows partition before opening the installer. This then gave me all the options.

---

