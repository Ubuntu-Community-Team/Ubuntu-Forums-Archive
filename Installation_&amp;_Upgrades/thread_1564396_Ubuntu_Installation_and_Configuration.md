---
title: "Ubuntu Installation and Configuration"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by BeginnerCsisz on 2010-08-30
Hi guys,
 

 I recently installed Linux on my home computer (Ubuntu 9.04), and began to use it. After a while I have decided to build a WLAN network at home (I have a desktop and a laptop) with a DSL internet connection and a D-LINK router. My final goal would be to create a configuration which I can use to develop homepages (with html, php, apache and oracle or mysql). Of course I meet with several problems during the installation. 



  I organised my questions into topics. I want to keep this thread focused, so first lets discuss topics 1/1 and 1/2. Any other points will be discussed later on! Thanks!


The topics are the following:
  
[LIST=1]
[*]Base system
[LIST=1]
[*]Which version to choose (9.10 or 10.04). What is the difference between the two version? Is it true         that the 9.10 version is more stable and less bug can be found?         What are the advantages of 10.04 Ubuntu? I have a 64 bit processor,         it is recommended to use the 64 bit version of Ubuntu I guess...?
[*]Which Ubuntu type to choose? Can  anybody explain the differences between the different types of Ubuntu? In the Hungarian Ubuntu site I can find the following main         types
[LIST=1]
[*]Base version – simple to install, but many disadvantages (limited number of partitions,             problematic upgrade)
[*]Server Version – hard to             install (text layout, problems with the configuration of internet             connection)
[*]Alternate Version – hard to             install (text layout, problems with the configuration of the             internet)
[*]Other Ubuntu versions –             Xubuntu, Lubuntu, Mythubuntu, Ubuntu studio – anybody has a             clue, what is the difference between these minor types?
[/LIST]
 
[*]Internet configuration: I want to         connect the desktop to the internet with a network cable to the         router, and the laptop should be able to use both network cable and         wireless connection
[/LIST]
 
[*]Software Configuration
[LIST=1]
[*]Package Manager:
[LIST=1]
[*]In the applications menu there             is a Add/Remove button and it leads to one of the Ubuntu package             managers. In the System/Preferences menu the
[*]What is sudo, alien, etc stands             for? How can I install rpm packages and how can I nistall deb             packages.
[/LIST]
 
[*]Internet configuration:
[LIST=1]
[*]How to configure Evolution – I             have a gmail mailbox, how can I configure it (though this problem             is broadly discussed)
[*]There are several blog motors –             which one should I use, how can I create a blog quickly with a             nice design?
[*]News: I want to use the desktop             to efficiently collect news and organise them into documents. I             plan to use somekind of RSS... Which RSS feed reader should I use,             how can I configure it. I also plan to use Clarice for creating             e-books. Again, is there any other choice?
[/LIST]
 
[*]Database
[LIST=1]
[*]Which database should I use             (MySql, Oracle). During development I want a free software, but             after moving to the development phase to the real phase I want to             use a commercial product (again Oracle or MySql, but a commercial             license). What are the options?
[*]What kind of data modeller             should I use. My first choice was DbDesigner. Is there any free             data moideel on the market?
[/LIST]
 
[*]Software Development
[LIST=1]
[*]I want to document my webpage.             Is there any free software for documentation
[*]I will use SQL, PL/SQL, java,             html, css, php. I want to use an editor which capable of syntax             highlighting and is able to organize the text files. Again, what             do you recommend.
[*]Version Control System: I want             to use Bazaar, though I am aware that there are many free, open             source products available. Again, what do you recommend.
[*]I have to install a LAMP             application. How can I do it? What other softwares do you             recommend
[/LIST]
     
[/LIST]
 
[/LIST]
 

 These are my first thoughts, but many other can hit me on the way. I will edit this post, if I have new ideas...


Regards,
BeginnerCsisz

---

### Post by uRock on 2010-08-30
The [Ubuntu Manual]("http://ubuntu-manual.org/") may be helpful with making these decisions.

10.04 will be supported for almost 2.5 years whereas 9.10 is only supported until April 2011.

64bit is faster but has a few incompatibility issues, such as crappy flash support, the Thunderbird Lightning extension isn't supported for 64bit and installing 32bit software is a real pain. I have a few 32bit programs that I have to run in a VirtualBox, because they cannot be installed in the 64bit OS.

---

### Post by BeginnerCsisz on 2010-08-31
Thanks for the answer, uRock, 

I am still reading the manual. My opinion changed a little bit - I would like to install both 32bit and 64bit Ubuntu 10.04 and I would create three partitions for Linux - one for the 64bit Ubuntu progs, one for the 32bit Ubuntu progs and one for data. Now the following questions arise:[INDENT]1. Security: I will create the same user structure for both OS - and I would like to implement the same rights for the data partition - can it be solved? If the answer is yes then how?
2. Database: Can I solve that the Oracle (or MySQL) database use the same partition (though the software will be installed on the 64bit OS partition.
[/INDENT]I am still thinking on three variants: Alternate, Kubuntu and the server version. The main question here is the windows environment (KDE or GNOME). I have the following questions connected with this problem:[INDENT]1. Pros and Cons: What are the pros and contras against KDE and GNOME. What are the differences, what are the strengths and weaknesses
2. Server: Is it possible to install a windows environment onto the server version?

[/INDENT]Thanks in advance,
BeginnerCsisz

---

### Post by BeginnerCsisz on 2010-09-06
Hi All again,

I managed to install Ubuntu both on my desktop and on my laptop. Now my main problem that my laptop is very-very slow. I know it is an old laptop (I bought it during the fall of 2004), but it should work, because I don't run any processor memory consuming software.

The paramters of the laptop:

[LIST=1]
[*]Athlon XP-m 2800+ processor
[*]420MB Memory
[*]60GB Hard drive
[/LIST]
My other problem that I can only create 4 primary partitions. Why? What is the difference between primary and logical partitions. Should the swap partition be primary or can it be logical? Isn't there a manual about partitioning?

Thanks,
BeginnerCsisz

---

