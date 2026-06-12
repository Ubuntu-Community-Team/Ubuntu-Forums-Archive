---
title: "Lost all my life's data while installing ubuntu"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by asif12 on 2016-05-08
Hi 

Please help I really need an advice.

I am a new user of Ubuntu and installed successfully but while installing made a life's big mistake.

Scenario

I was installing Ubuntu through USB while my external HDD was attached to the laptop.

Ubuntu picked the external HDD (3 TB) and I have installed ubuntu on my external HDD (By Mistake) and the operating system (ubuntu) formated my external HDD and installed the ubuntu operating system.

Now all my life's data was on my external drive.

After installation I have not touched my external HDD through any software.

Please advice, will be waiting for your expert advice.

Thanks

---

### Post by Mohammad_Mekini on 2016-05-08
Dear Asif, my condolences

It was a sameness for me, as my first trial of GNU/LINUX installation was with a specific release of fedora 7 and I lost all my my computer's information too that time but fortunately I had backed up my information.

most of GNU/LINUX releases file system run in EXTENSION 4 (EXT4) format, however the formal HDDs and SSDs have NETWORK FILESYSTEM OF MICROSOFT (NTFS), i.e. the same as Microsoft Windows drivers' format especially after millennium OS.

It's really hard and nearly impossible for a simple home user to change these formats and get his data back, I would like to recommend you to use your HDDs support warranty services, if there are available in your area, or trust some other data restoring security companies, most of them have an internet webpage and you can search for them.

But as you wish to restore them yourself, which I could not really recommend, you have to search for "data restoring programs" keywords according to your OS. and follow their manual.

Wish you luck in restoring your valuable data.

---

### Post by DuckHook on 2016-05-08
This somewhat oldish thread might help.

[http://ubuntuforums.org/showthread.php?t=2087725&p=12370874#post12370874](http://ubuntuforums.org/showthread.php?t=2087725&p=12370874#post12370874)

Do absolutely nothing with that disk. You have probably overwritten a lot of data, but hopefully, what has not been overwritten with your actual OS is still recoverable. Note that Mark's advice is with respect to data created by Windows. You must use another computer in order to not touch your current one and overwrite any further files.

It's a shame that you did not backup first, but we all live and learn.

---

### Post by oldfred on 2016-05-08
Did you have all your data in one massive partition? That makes it even tougher to recover.

Some more suggestions.
But you will require another drive with at least enough room for all the data you may recover. And when I used photorec it also recovered deleted files as it does not know difference.

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by asif12 on 2016-05-09
Hi Guys first of all REALLY REALLY THANK and appreciation for prompt response, THE GOOD NEWS is after reading this post and Mark's instruction found my 99% data in front of me like magic, but just need to buy licence yet, but I really appreciate your effort and time for answering these questions.

Further would like to share my knowledge as well.

1. Tried Testdisk/Photorec but was not luck
2. Through Ubuntu to recover from windows is not ideal.
3. Windows 7 did not recognize my external HDD due to Ubuntu OS (my guess).
4. Once I installed[SIZE=2] GetDataBack Simple Data Recovery Software from runtime software it recognized the file system and gave me option for EXT,Fat32 and NTFS, after selection of NTFS as I knew that I had this file system within 2 to 3 minutes of scan It gave me full tree of my files and folders ...........yaaaaahoooooooo I hope after buying Licence I will be able to copy all my data.

Once again sincerely thanks.

 And one question if I have some questions to ask shall I start new thread accordingly or can I ask on a same thread ?
[/SIZE]

---

### Post by DuckHook on 2016-05-09
Glad it worked for you. :) For new questions, please ask each question on its own thread.

---

### Post by DuckHook on 2016-05-09
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

