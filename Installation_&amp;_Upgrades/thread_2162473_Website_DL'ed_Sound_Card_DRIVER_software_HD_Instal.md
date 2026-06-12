---
title: "Website DL'ed Sound Card DRIVER software HD Installation"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by iearu on 2013-07-14
My PC:  Desk top Dell mini-tower Dimension 2400; Ubuntu 10.4 version OS

I disabled (turned off) the MB integrated Sound via the BIOS settings option.

Installed a StarTech 4 Channel PCI Sound Card (Hardware).

Loaded the supplied Driver CD software only to discover that Linux OS's were not included.

Chatted on-line with a StarTech Support man, and was given an http ... URL where I could DL Linux DRIVERS for Redhat, SUSE, and several other Linux OS's (but Ubuntu was not listed).

I went to the website and DL'd the Driver which to my delight Ubuntu copied {it}.

It appears on my "see Downloads" monitor screen as:  CMedia_CM18738, 155.6 MB, Folder, (Date modified) 30 March 2012.  (FTR, I tried DLing from the CD just in case Ubuntu would recognize the DRIVER, but I got the Error / not in archive folders [or something like that] message).

The monitor's screen Heading reads:  CMedia_CM18738.zip [_read only_]

My Question is, **How do I INSTALL the Driver onto my Hard Drive ?!**

TIA
Dennis

---

### Post by iearu on 2013-07-14
My Update:

Going to   **System** > **Administration** > [B]Hardware Drivers
[/B]the monitor's screen correctly informs me that _as yet_ there are no _proprietary_ drivers enabled (all of my apps are within Ubuntu's Packages).

Because the Sound Card driver software is not within the Ubuntu Packages I Clicked On the HELP button at the bottom of the HD screen.

The Help section offered me the instructions for "Enabling a proprietary driver", which upon reading its' number 4 (of 5) steps says : [B]The proprietary driver may have to be downloaded and INSTALLED. 


[/B]However I can not find / locate any instructions on HOW to do step 4 !  FTR, I have the driver DL'd but that's as far as I can get ...

Doesn't it seem logical that the instructions should provide a Click On link informing one how he / she can do step 4 ?!

Dennis

---

### Post by iearu on 2013-07-14
[h=2]Re: Website DL'ed Sound Card DRIVER software HD Installation[/h] 		 				 				 					 				 		 			 				[INDENT] 					My Update:

Going to   **System** > **Administration** > [B]Hardware Drivers
[/B]the monitor's screen correctly informs me that _as yet_ there are no _proprietary_ drivers enabled (all of my apps are within Ubuntu's Packages).

Because the Sound Card driver software is not within the Ubuntu Packages  I Clicked On the HELP button at the bottom of the HD screen.

The Help section offered me the instructions for "Enabling a proprietary  driver", which upon reading its' number 4 (of 5) steps says : [B]The proprietary driver may have to be downloaded and INSTALLED. 


[/B]However I can not find / locate any instructions on HOW to do step 4  !  FTR, I have the driver DL'd but that's as far as I can get ...

Doesn't it seem logical that the instructions should provide a Click On link informing one how he / she can do step 4 ?!

Dennis 				[/INDENT]

---

### Post by coldraven on 2013-07-15
I'm guessing that the package you downloaded was for Windows and therefore cannot be installed.
If it was a Linux package and if it was designed for your version of Ubuntu you would have to right click on it, select "Properties" and set "Permissions" to "Allow as Executable".

Edit: Thinking about it you would probably need to install it as root. So after doing the above you would run it in a terminal 
```
sudo <packagename>
```

---

### Post by Cheesemill on 2013-07-15
Threads merged.

Please don't create more than one thread for the same issue as it dilutes the communities ability to help.

---

### Post by Mark Phelps on 2013-07-15
A .ZIP file is a compressed archive.  You need to use unrar to uncompress it into its constituent parts.  Once you do that, you should see a bunch of files, and maybe directories, with a readme text file -- which will provide the instructions you need.

Additional Drivers is for video and network drivers, not for audio drivers.

---

### Post by iearu on 2013-07-15
[Post #5] Cheesemill:  Sorry about that!  My thinking (as a first time poster) was that this forum was like perhaps most others, i.e. once an OP's Thread / Posting  gets dropped down the list due to subsequent other postings then it becomes some what like the saying, "out of sight, out of mind".  I had noticed that after 9 hours and 127 views -- but no replies -- there was a slim chance of my receiving an answer (OR perhaps I needed to rephrase my question; hence the "new" Thread).
**Thanks for correcting me**!

[Post #4] Coldraven:  Your response looks like it may be the / a QUICK solution!  And thanks for adding the Command Line Code!

The DL {proprietary} driver is for Linux, and was copied by my 10.4 version; Ubuntu opened it with "Archive Manager (default)".  Your comment about one's Ubuntu _version_ was very interesting.  For any reading this, this is what the StarTech tech told me it was for (he didn't know about Ubuntu): Slackware 4.0, Open Linux 2.2, Redhat (the Tech called it "Redhead" lol) version 6.0 and S.u.S.E. 6.1.

[Post #6] Mark Phelps:  Yes!  All that you stated about what I should see after UNcompressing the .zip is exactly what the StarTech driver CD showed me when I attempted to DL the Windows options (Visa, XP, 7 and 8). Naturally when I tried to open any of the "bunch of files" it was nada nada!  I plan on trying Coldraven's suggestion first, and IF it fails I will do it as you have so kindly informed me --- I see what you are saying because of what I saw when attempting the Windows drivers off of the CD!

=================================

Again, I sincerely **Thank All of you repliers!** as well as all you unknown "Viewers" who in doing so were at least interested in seeing if you could help me -- or perhaps wanted to "learn" something also!

Dennis
Precepts Precede Promises

---

