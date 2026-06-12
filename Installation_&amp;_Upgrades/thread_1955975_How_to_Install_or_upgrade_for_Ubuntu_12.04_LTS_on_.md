---
title: "How to Install or upgrade for Ubuntu 12.04 LTS on Ubuntu 8.04?"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by paragpranat on 2012-04-10
Hello

Is it advisable to install or upgrade to UBUNTU 12.04 LTS from UBUNTU 8.04? I use Mozilla Firefox version 3.6.17 

If yes, How do I upgrade saving my all files? I use Openoffice 3.2 version for all my daily work. I also use Skype. On my current version of UBUNTU 8.04, I'm facing initial start-up problem on my Laptop. I have to start in the recovery mode, if it doesn't start automatically in the regular mode. 

Write me at - _{deleted}_[EMAIL="paragpranat@yahoo.co.in"][/EMAIL]    Thank you. 

Parag Shah

Edit removed email or else you will get an awful lot of spam.

---

### Post by oldfred on 2012-04-10
We are a forum and as such everyone shares info. If you do want a message you can do PM from within forum. But support should all be in forum.

If you have 10GB of space on a hard drive install the 12.04 version and try it, it is a good way to learn about the differences and you still have your current version to boot into.

I have a full install on my Desktop to test, but do not have a lot of room on my laptop. So I created a full install in 8GB on my 16GB flash drive. A bit slower (especially writes) but functional. So far only minor issues but I did change to fallback or classic from Unity.

OpenOffice has been replaced with LibreOffice which is the same but a fork of the original.  Many other applications have major updates so they may be different and some have been replaced with different standard applications.

---

### Post by paragpranat on 2012-04-10
Thank you Oldfred, since I'm new, I didn't knew of the email ID posting. I thank you again. My real issue is will I be able to  upgrade on UBUNTU 8.04 To 12.04? Should I simply do it through "Download" and upgrade from UBUNTU website link? What time does it take to upgrade and will I be able to save all my documents of openoffice 3.2 version? Or what should I do? Parag Shah PS: How can I reply against your message in the forum? As I don't see reply button there.

---

### Post by oldfred on 2012-04-10
I would backup all your important files. 

I upgraded in place every 6 months from 6.06 thru 9.04. I think I had some issues every time. I then wanted to convert to 64bit, new grub2 & ext4 with 9.10 and did a clean install. I am now a fan of clean installs, but I happened to get a new drive with lots of room so I can do clean installs to a new 25GB / (root) without removing old install.

The newer versions of the installer will save some data, but I have not tried that to know how much or what it saves. Since you have the LTS you may be able to upgrade to 10.04 & then to 12.04. But if system is that old does it meet minimum specs or would Xubuntu or Lubuntu be better choices? 

Time to upgrade depends greatly on Internet speeds and your system. It works best if you have Ethernet connection so you can also update as part of the install. It also depends on how fast your system is. With my 2006 system, 4GB of RAM, my installs used to take 20 min, updates another 20 to 30 minutes with cable (relatively hispeed). Updates are now all part of install. And I semi-automated some of my configuration and reinstall of additional  apps. But I found USB flash drive to be quicker than CD. And my most recent install on a new SSD using an ISO loopmounted from another hard drive installed extremely fast. I always partition in advance, so that is not part of my time to install and if repartitioning that can also take some time.

---

### Post by CottonCandy on 2012-04-10
Hello Parag Shah, welcome to the forums! 

> **oldfred said:**
> I would backup all your important files. 
Yes, always! If you would be unhappy to lose your files, you need to back them up regularly. 

Like oldfred said, if you have 10GB of unused space on your hard drive  you can install 12.04 to  try it and to test out different desktop  options. Back up your files to an external hard drive or USB (flash drive), download 12.04 from Ubuntu.com and burn it to a CD/DVD (use the slowest speed to burn it, higher speeds have a higher chance of causing errors) or create a bootable USB or whatever your preferred install method is, install and try things out. Once you decide which option works best for you, you can install that and transfer your files from the backup. 

LibreOffice is just like OpenOffice. I created many documents in OpenOffice using Ubuntu 10.10 and LibreOffice was able to open all of them with no problems. You can easily test if LibreOffice will open your documents by saving them to an external drive, creating an Ubuntu 12.04 CD/DVD/USB, booting it and clicking Try Ubuntu. When the desktop loads, plug in your external drive & try opening some files.

---

### Post by paragpranat on 2012-04-12
Thank you Oldfred and Cotton Candy. I use HCL (Indian Brand) Y2001 Laptop AMD TURION DUAL CORE 1.6,  512 / 120/ 15.4 wide screen. with DVD Writer and web cam.  I bought this Laptop on April 7, 2007.

Mostly Hard Disk is of SATA, This laptop was crashed before three years, and than got two (mostly) partitions. I once got 10.04 installed on the other partition, but didn''t work well. Posing some problems, so deleted the upgrade. What I want is can I now delete 8.04 permanently and Install simply 12.04 with either openoffice3.2 or what is best as per your suggestion. 

I use Skype, web camera, printer. Please ensure I can view all flash side, music and YouTube too. 

Can you come on skype to fix appointment for advising me in the matter? Alternatively through Team viewer  or any such devise, you can Install UBUNTU 12.04, and all other softwares required by me. Do you suggest I must first get RAM upgraded to 2 GB? 

Please advise, thank you.

Parag Shah

---

### Post by mastablasta on 2012-04-12
> **paragpranat said:**
>  
Mostly Hard Disk is of SATA, This laptop was crashed before three years, and than got two (mostly) partitions. I once got 10.04 installed on the other partition, but didn''t work well. Posing some problems, so deleted the upgrade. What I want is can I now delete 8.04 permanently and Install simply 12.04 with either openoffice3.2 or what is best as per your suggestion. 

If 12.04 works well in live mode you can install it if you wish. simply use default Libre office (it's Openoffice with bugs fixed and new features added)
 
> 
I use Skype, web camera, printer. Please ensure I can view all flash side, music and YouTube too. 
Again try live mode. if this stuff works in 8.04 it will likely work in 12.04 as well.
 > 
Can you come on skype to fix appointment for advising me in the matter? Alternatively through Team viewer or any such devise, you can Install UBUNTU 12.04, and all other softwares required by me. Do you suggest I must first get RAM upgraded to 2 GB? 
 
Please advise, thank you.
 
More ram is always better if oyu have the money for it and if the motherboard supports it it is always good to have as much as possible. more ram means faster computer.

---

### Post by CottonCandy on 2012-04-12
> **paragpranat said:**
> I once got 10.04 installed on the other partition, but didn''t work well. Posing some problems, so deleted the upgrade.  Having some problems getting everything to work properly is actually quite normal. Here is why: > **MAFoElffen said:**
> Linux distributions such as Ubuntu, basically and simplistically run in  layers like this-->  You have a Linux kernel running.  On top of that  layer, you have a terminal session- running to interact with other  layers.  On top of that, you have an GUI, XTerminal session, X-Wndows,  XServer or also known as an XSession running to have a visually  interactive session running.  **In each version of Ubuntu (and other  distro's) an honest and earnest attempt is made to make each new version  easier to use for a new user, in a way that is pleasing to the eye.    Each of these changes does mean underlying changes in how things relate  to each other layer... on a base that is trying to cover a myriad of  hardware combinations, that users will install that distribution onto.**   Sometimes all of these combinations cannot be foreseen.  (For instance  when a certain video card type is made by over a dozen different  vendors...)
There are thousands upon thousands of computer configurations out there. It is expected that some troubleshooting & tweaking will be required to get a Linux distribution working properly.
> **paragpranat said:**
> What I want is can I now delete 8.04 permanently and Install simply 12.04 with either openoffice3.2 or what is best as per your suggestion. 
It is recommended that you try 12.04 first by booting a 12.04 CD and clicking Try Ubuntu. If it seems to work well ***then*** you can delete 8.04 and install 12.04. You may also want to consider installing 12.04 on a partition so that you can get used to it and make sure you get everything working before deleting 8.04.
I believe I read somewhere that OpenOffice has stopped development and that is why Ubuntu switched to LibreOffice. LibreOffice is a "fork" of OpenOffice and the menu, how they work, the file type, is all **exactly the same.** So I recommend that you try LibreOffice. I am sure you will find it to be the same except for the name, but if not you can always uninstall LibreOffice and install OpenOffice through the Software Center.  > **paragpranat said:**
> I use Skype, web camera, printer. Please ensure I can view all flash side, music and YouTube too. 
All of those should work in 12.04, however as I said above, some troubleshooting is to be expected. It is great if everything works "out of the box" but do not expect that.
If you look in the top right corner of the Ubuntu Forum you will see a search box. Searching the forum and searching with a search engine such as Google or Ixquick/Startpage will usually help you fix problems. If you cannot find what you are looking for you can post a thread here with your computer info & what problem you are having and hopefully someone here can help you fix it. There is even a sticky that has suggestions on how to get your support questions answered as quickly as possible. > **paragpranat said:**
> Can you come on skype to fix appointment for advising me in the matter? Alternatively through Team viewer  or any such devise, you can Install UBUNTU 12.04, and all other softwares required by me.  Sorry, I don't have the time or technical expertise required to walk you through installing your computer and getting everything working. But I'm sure searching the forum and the internet and posting your questions will help you to fix most problems.  Linux OSs have become much more user friendly over the years, and now instead of having to figure everything out ourselves (requiring much computer knowledge) a large community and lots of documentation exist to help us learn. :) I have learned more about how computers work in less than 2 years with Ubuntu than I did in over 4 years with my old laptop.  > **paragpranat said:**
> Do you suggest I must first get RAM upgraded to 2 GB? Yes. I think the minimum recommended now is at least 1-2 GB.

---

