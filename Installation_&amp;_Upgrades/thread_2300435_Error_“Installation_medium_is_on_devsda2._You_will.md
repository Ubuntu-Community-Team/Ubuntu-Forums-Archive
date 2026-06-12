---
title: "Error: “Installation medium is on /dev/sda2. You will not be able to create,delete…”"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by sark2 on 2015-10-25
I installed ubuntu 14.04.3 using netbootin in order to have a dual boot along with pre-installed windows 8.1 in my HP DV6 Pavillion. But unfortunately, I got the Error: "Installation medium is on /dev/sda2. You will not be able to create,delete, or resize partition on this disk, but you may be able to install to existing partitions there."

---

### Post by yancek on 2015-10-26
That's not an error it is just information.  You apparently used Unetbootin to do a frugal install which has the Ubuntu installation medium on a hard drive partitions (sda2).  As it states, you can install Ubuntu to another partition but you won't be able to "create, delete or resize partitions on that disk".  Not a problem if you already created a partition with a Linux filesystems.  Not knowing what you did, there isn't much else we can say.

---

### Post by sark2 on 2015-10-26
Thank you yancek for your reply I thought it is fatal error. Please bear with me as I am a newbie and totally new to this OS. I have decided to install precisely because I want to shift from windows and try my best to gain more knowledge about this OS. So it means that I can install ubuntu on [COLOR=#000000]/dev/sda2 without any issue and without messing my windows OS.[/COLOR] what I saw in the installation type is almost similar to below.


**INSTALLATION TYPE**

         [COLOR=#000000]/dev/sda1(windows)
[/COLOR]         [COLOR=#000000]/dev/sda2 
         Free space
[/COLOR]

---

### Post by oldfred on 2015-10-26
Was Windows 8 pre-installed? You partitions do not look like a typical UEFI install which all Windows 8 pre-installed systems have. And Windows does not normally show all the hidden partitions that it needs.

Post this from Ubuntu live installer's terminal. And best to use a live installer not install from same hard drive as that is a bit more advanced.
sudo parted -l


You need a DVD or flash drive:
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

And you want to have a bootable flash drive for current versions of every installed system or one  with Windows repair and one for Ubuntu installer.  

Lots of detail info in link in my signature. Best to review & follow several of the example install links that have screen shots to show the install process. Then if you have more questions come back and ask about those details.

---

### Post by yancek on 2015-10-26
> So it means that I can install ubuntu on [COLOR=#000000]/dev/sda2 without any issue and without messing my windows OS[/COLOR]

No, it means exactly the opposite.  You can't install an operating system to the same partition or medium (DVD/flash drive) you are booting from.  Follow the instructions at the links posted above by oldfred.  Much easier and less confusing if you use a DVD or flash drive.

One windows partition looks a little odd.  Usually newer windows systems have 3 partitions, at least when pre-installed.

---

### Post by sark2 on 2015-10-27
Thank you guys...:D i installed it using the bootable flashdrive and i did it...thank you...now I will start to explore linux OS and i will show to my colleague that their perception and "old myth" is totally wrong mainly because they are saying that linux is not a friendly user and it's hard to use.

Just i saw this message(attached) while am installing, i am just wondering if this is a serious problem?

[IMG]/home/sark/Desktop/installation.jpg[/IMG]

---

### Post by oldfred on 2015-10-27
The img link you posted only works on your system.
With forum easiest to use forum's advanced editor and the paper clip icon to attach screen shot.

---

### Post by sark2 on 2015-10-27
[ATTACH=CONFIG]265207[/ATTACH]

---

### Post by sark2 on 2015-10-27
the above message i got was it serious?

---

### Post by oldfred on 2015-10-28
If partitions 5 & 6 are correct, it does have to create & write to them.
As long as it has seen Windows correctly in your side by side install you should be ok. But do you have Windows fully backed up just in case?

I do prefer Something Else as then I have total control over partitions, but still have made mistakes, so backups required. And I prefer to use gparted to create new partitions, as it seems a bit easier.

---

### Post by sark2 on 2015-10-28
It's ok I backed up the windows. I guess this issue has been solved that's why i am very glad and thankful to you guys (**oldfred** and **yancek**) for your full support and help. I have gained valuable experience and knowledge about the installation process. Now it's time for me to explore and learn deeply about this OS, i hope that you will help me again and again in case i will encounter more issues.:)

---

