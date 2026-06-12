---
title: "Question about partitioning"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by jojacob on 2006-08-03
I'm about to install Dapper Drake using the live CD, attempting to dual boot with XP. I have never partitioned a drive before, but I've read pretty much everything I can find on the operation, and it seems fairly straight forward and nothing above my level of experience with PCs, just something I've never done before.

The big question: I've got a 25 GB hard drive with 12 GB of free space, and I want to do a pretty standard division for a dual boot install. Windows defrag will completely defrag my drive, but leave defragmented files toward the end of the drive, according to its graphical diagram. What happens to this data when the NTFS partition is shrunk? Does it get overwritten in the formatting process? Moved over to within the end border of the newly shrunk first partition?

I've got all my important data backed up, I've got the Linux rescue CD, the LNX-BBC minidisc, and a Knoppix disc to attempt to fix anything that goes wrong, but would this arrangement of my drive lead to data loss or the breaking of my XP install? Just curious.

---

### Post by Herman on 2006-08-04
> What happens to this data when the NTFS partition is shrunk? Does it get overwritten in the formatting process? Moved over to within the end border of the newly shrunk first partition? Well, I'm just a computer user too, not a software engineer or anything like that, but I can tell you for sure it won't be overwritten. I guess it gets moved.
>  I've got all my important data backed up, I've got the Linux rescue CD, the LNX-BBC minidisc, and a Knoppix disc to attempt to fix anything that goes wrong, but would this arrangement of my drive lead to data loss or the breaking of my XP install? Just curious. You are right to back up your data and have some rescue disks ready. Linux Rescue disk is really good. It has GAG Boot Manager on it. GAG Boot Manager can boot Windows for you if you have any bootloader problems after installing.
Chances are, you won't have any problems though. 
I would imagine there would be someone who would have some real statistics about how many new 'Dapper' systems were installed altogether (in total), compared with the number of reported problems of various kinds.
I can only guess.
I think there were roughly around 100000 Ubuntu Forum members when 'Dapper' was released about 64 days ago. Most of those people would have been using 'Breezy', and either upgraded from 'Breezy' or clean installed 'Dapper' and deleted 'Breezy'.
Now there are about 143750 Ubuntu Forum members, so about 43750 could be new users in 64 days.

These figures could be very misleading, since some forum members like me represent a number of computers. I have five in my house right now and we're expecting another new one soon. On the other hand, there might be a few people who installed Ubuntu, signed up for Ubuntu Forums and then didn't like Ubuntu and left.  I think those would be a minority though.

Even presuming  143750  Ubuntu Forum members  only have one computer each, if every one of us performed only one 'Dapper' install each,  that would make an average of 2246 'Dapper' installs per day. (For 64 days).

I monitor Ubuntu Web Forums here seven days a week. I'm not very active on weekdays, but I still take a quick look twice a day. I have not seen very many problems reported here compared with the number who must be installing without any problems at all. I would guess that probably there would be about 1 install with a problem for every 1000 perfect installs.

Most of the 'problems' I have seen reported here have been easy to fix, just booting up problems and that sort of thing. A few have been real problems like partitions being lost. It can happen, and has been reported a few times, but I'd still say it's relatively rare.
We also have to take into account the fact that here are more than a few 'problems' posted here in the Ubuntu Forums each day that are put there by trouble-makers too, who greatly exaggerate trivial problems and could even be making things up just for something to do.

The main thing to do if you want to have a perfect install the first time is to md5sum your downloaded .iso before you burn the CD. After you burn the CD, or if you have a 'Shipit' CD, use the 'Check CD for Defects' option. If your CD passes you will have already gone a long way to ensuring a trouble-free install for yourself.

Since you are sensible and have all your important data backed up already, and presumably you can re-install an operating system if you need to (unlikely), then you really have nothing to worry about. Just have fun.
Good luck with it, Herman :D

---

### Post by Cariboo1938 on 2006-08-04
> **Herman said:**
> The main thing to do if you want to have a perfect install the first time is to md5sum your downloaded .iso before you burn the CD.   
:D
How do you do md5sum? is this a command line?
Juergen:?:

---

### Post by Herman on 2006-08-04
>  How do you do md5sum? is this a command line? Yes, it is easiest and quickest to use any Linux Operating system, (including a LiveCD) to run an md5sum check on any file from the command line.
The command is,
```
md5sum filename
``` You can replace the word 'filename' with the actual name of the file you want checked, for example, ```
md5sum ubuntu-6.06-alternate-i386.iso
```  and be sure to include the path to the file if it isn't in your /home/username folder.
A tip is to use 'Tab completion. That make it easier, you just type 'md5sum ubu' (the first two or three letters of the filename) and then press your 'Tab key. The rest of the filename will be automatically completed for you. That not only saves typing, it also prevents typing errors.
if you are using a LiveCD, you will need to 'mount' your other filesystem (Windows partition) first. 

If you are new to Linux and you would rather do it from Windows, you can. There are plenty of apps you can install for running md5sum tests from Windows. 

The following link will tell you more about how to md5sum your Ubuntu .iso download , including how to  use '[MD5summer]("http://www.md5summer.org/")' in  Windows. Here is the link:[Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm")

Any more questions are welcome, please feel free to ask.
Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-05
May be that this is confusing because it has nothing to do with partitioning. Any way, its a message for Herman.

> **Herman said:**
>  
Any more questions are welcome, please feel free to ask.
Regards, Herman :D
Thank you Herman, I really appreciate your detailed "md5sum explanation" and your invitation to ask an other question. Here it is:
I installed Ubuntu and I have trouble to set up my Internet Dial-up connection. I live in a remote area and there is no High-speed Internet available in the near future. So I depend on dial-up and it always worked very well with Windows XP, with Libranet 3.0 and with Fedora Core 5. It was always installed automatically.  Well, several days now, I’m trying, with the help of the Ubuntu Forum community, to set this thing up. I have a PCI hardware modem which is correctly detected (I checked with [COLOR="Blue"]“lspci”: 0000:02:07.0 Communication controller: TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice modem)[/COLOR]. I configured it in the terminal with command [COLOR="blue"]“sudo pppconfig”[/COLOR]. In >NETWORKING, the modem is listed, together with eth0 and eth1, but not active. Trying to activate it gives the Error: [COLOR="Magenta"]‘Could not enable the interface ppp0’[/COLOR]. Because it is a PCI modem I entered it as /dev/modem but I’m not sure if this is ok. May be you have an idea and could give me some advice?
Kind regards
Juergen :?:

---

### Post by Herman on 2006-08-05
Hello, Cariboo1938,
 Juergen, I'm not really very good on the subject of networking, but I have found a couple of how-tos for you that might help, [DialupAndFax]("https://help.ubuntu.com/community/DialupAndFax?highlight=%28CategoryDocumentation%29")   [DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto?highlight=%28CategoryDocumentation%29")
It isn't so long ago that we got ADSL broadband here where I live, but I was lucky and my old 56k dial-up modem was automatically set up for me when I installed Ubuntu 'Warty' and 'Hoary' in my old PC Chips 'Book PC' pictured in my avatar. Now I have some newer computers and we use ethernet modems and broadband.
I hope one of those links will help you, Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-05
> **Herman said:**
> ...but I have found a couple of how-tos for you that might help, [DialupAndFax]("https://help.ubuntu.com/community/DialupAndFax?highlight=%28CategoryDocumentation%29")   [DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto?highlight=%28CategoryDocumentation%29")
I hope one of those links will help you, Regards, Herman :DThanks a lot, Herman, for helping me...the problem is solved...the DialupModemHowto was the rescue...the only problem actually was the name/port of the PCI modem...it has to be [COLOR="Blue"]/dev/ttys4 [/COLOR]... Ubuntu is great!
Thanks again for your time and kind regards
Juergen:-({|=

---

### Post by Herman on 2006-08-06
Juergen, great work by yourself and also the person or people who wrote the how-to! I'm pleased it worked for you. :D
Regards, Herman

---

