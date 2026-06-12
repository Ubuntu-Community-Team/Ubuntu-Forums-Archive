---
title: "Having trouble partitioning in 8.0.4"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by choicefresh on 2008-05-12
Everyone was telling me in IRC that I should try Ubuntu, so the first thing I did was download Wubi. Wubi is a Windows-based Ubuntu installer. Unfortunately, after three hours or so, I realized my BIOS wasn't supported.

The next thing I tried was to burn a LiveCD. While at first I had a few issues, and I still can't get my wireless internet to work, I decided I might as well install it because I was getting annoyed losing my settings each time I rebooted. When I tried to partition in the Install Manager, I chose the deafult one that gives 13% to Windows and 87% to Ubuntu. It told me that it could not write the changes to disk, so I rebooted into Windows and ran a defrag. After rebooting into Ubuntu once again, I got the same error, Now it's not even showing that option, and just showing "Guided - use entire disk", "Guided - use largest free space" or "Manual". I was told the default would work best, but apparently that doesn't work.

I'm running Windows XP Professional on a Dell Latitude D620 with Intel Core2 Duo. Is it possible that Ubuntu isn't supported on my system? Or am I doing something wrong?

It seems whatever strategy I try, I get an error. :confused:

---

### Post by Pumalite on 2008-05-12
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP and choose 'resize' from the menu. In the free space newly obtained, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops for hibernation)
The rest for /home
Then install Ubuntu, go Manual and choose the partitions already prepared.

---

### Post by choicefresh on 2008-05-14
Hi,

Thanks for the advice, but I'm having trouble following along. When I first try to boot from the CD I made, it asks me if I want to boot it to RAM, default, boot my normal operating system, and others. I tried the default, and then it went through asking me a whole bunch of questions, some of which I just did the default answer. Finally, it loaded up what seemed like Debian and GParted, but "XP" was nowhere to be seen. The only two things shown were FAT32 and NTFS. Could you give more detailed instructions?

Thanks,
Choicefresh

---

### Post by Partyboi2 on 2008-05-14
The fat32 and ntfs are your windows partitions. I am guessing that the fat32 is a small partition ie backup and the ntfs the larger one is where you windows xp is. (The one to resize) I suggest backing up your data as this is always a good practice in case of something going wrong.

Edit: More added

---

### Post by choicefresh on 2008-05-14
> **Partyboi2 said:**
> The fat32 and ntfs are your windows partitions. I am guessing that the fat32 is a small partition ie backup and the ntfs the larger one is where you windows xp is. (The one to resize) I suggest backing up your data as this is always a good practice in case of something going wrong.

Edit: More added

So choosing the default was the right thing?
What backup program do you recommend? Is it necessary?

---

### Post by Partyboi2 on 2008-05-14
As far as i can remember I haven't yet ran into problems with losing data from partitioning but from time to time people do run into problems, so its really up to you if you want to or not. If I am backing up I normally just transfer all my data I want to keep onto a usb stick. So I am not sure what programs there are that would help you to backup.

---

