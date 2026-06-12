---
title: "How many HDDs is better to use in a dual booting system?"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by theo5 on 2014-06-27
Hello.

I am a newbie in Linux OS and I am planning to create a dual booting system with Ubuntu 12.04 and Windows 7. From technical perspective, it' s better to use 1 HDD - split in half - or use 2 HDDs - one for each OS ?

I am apologizing in advance for any language error - English is not my native tongue.

---

### Post by SuperFreak on 2014-06-27
From the standpoint that if one hard drive fails you will still have a working system(you might have to repair grub) with 2 hard drives, it might matter. Other than that I don't see how it would matter

---

### Post by theo5 on 2014-06-27
Yea a boot repair is always needed, at least in my case, but i can manage that.
Maybe my question sounds stupid, but I want to be sure that it doesn' t matter.

Thank you very much :)

---

### Post by Bucky Ball on 2014-06-27
Welcome. In the past, having the OSs (or the OS and personal data) on separate hard drives would be ideal as it would be faster. Now, it doesn't matter. Both on one or one each, take your pick. (When I got two five and a half inch floppy drives I thought I was king of the world!)

The only time it would make much difference now is if you were doing some hardware intensive computing; editing HD video or mixing a dozen tracks of high quality audio. Then you'd split things up to separate physical drives if possible.

---

### Post by Bucky Ball on 2014-06-27
Welcome. In the past, having the OSs (or the OS and personal data) on separate hard drives would be ideal as it would be faster. Now, it doesn't matter. Both on one or one each, take your pick. (When I got two five and a half inch floppy drives I thought I was king of the world!)

The only time it would make much difference now is if you were doing some hardware intensive computing; editing HD video or mixing a dozen tracks of high quality audio. Then you'd split things up to separate physical drives if possible.

---

### Post by theo5 on 2014-06-27
Well I am not into video editing but I usually work with open MATLAB, C++ Compiler (mostly Codeblocks) and a wine window with Autocad or Multisim or any other program I can' t find running natively in UNIX. So I sometimes push hard my CPU and RAM but not GPU.
In that case what should I do?

---

### Post by Bucky Ball on 2014-06-27
Both OSs on one drive and data on another. That's where I'd be going. You can't use both OSs at the same time so effectively, OS on one drive, data on another. Makes sense for what you are doing. 

Be creative with how you split up your data drives so you might need a bit of time to think about it with a piece of paper and pen and beverage of choice.

What size are your drives before you go much further? We could possibly inspire your creativity. For example, if the OS drive is, say, 500Gb, the OSs would take about 60-70Gb (Ubuntu needs about 20-25) and you could use the rest for your personal data; pics, documents, what not, and on the second drive goes your hard-core computational data and vids/audio on three separate partitions (you could add your pics folder to the second drive rather than the first also in case you want to do some photo editing with Gimp or something else). :-k

There are many ways to go about it. Give us an outline of your plan. ;)

---

### Post by yancek on 2014-06-27
I think that it depends upon your knowledge and experience with bootloaders.  Also, if you have a windows installation from an OEM (pre-installed) you might have difficulty if you need to send it in for repairs if you have a non-windows bootloader.  This varies with the OEM.  If your warranty has expired, that won't matter.

Having Linux with its bootloader on one drive and windows with its bootloader on its drive is simpler for new users or people unfamiliar with bootloaders.  You select the drive in the BIOS on boot.  I would also agree that having a separate drive for data and backups is a good idea.  If you're confident with the Grub bootloader, put both systems on one drive.

---

### Post by theo5 on 2014-06-27
Thanks for your ideas.

As I say in the first post I only care in a technical level. I can manage bootloaders quite well, so don' t mind about that. I have 2 x 500GB HDDs so there are to options:
HDD_0 250GB ext4 Ubuntu + 250GB NTFS Win 7
HDD_1 500GB NTFS (so both OSs can read it) for personal data etc.

or

HDD_0 500GB ext4 Ubuntu
HDD_1 500GB NTFS Win7

I only care about the efficiency of the system in both cases + if you can explain which is better, so I can get the basic idea. :)

---

### Post by nerdtron on 2014-06-27
I'd go with the first first setup since it is what I'm doing. Another advantage of that is when you experiment on your OS and reinstall many times, your DATA is safe on the other drive.

---

### Post by oldfred on 2014-06-27
I prefer each system on its own drive. And totally configured to boot without the other drive. Then if one drive fails you can boot the other drive.
And better to keep system partitions for both Ubuntu & Windows smaller and use a larger data partition for all other data.
You also can have NTFS partition on Linux drive and ext4 partition on Windows drive and do some backups of Linux files to Windows drive and Windows data to LInux drive. Then one drive failure does not lose all data.
But you still should have image backups to external devices. I like to write most critical data to a couple of DVDs periodically as well.

---

### Post by theo5 on 2014-06-29
Thank you all for your help :)

---

