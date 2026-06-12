---
title: "Ubuntu and Windows Vista problems"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by popcorn09 on 2008-04-25
Hi,

I have a dell inspiron 1420. It was running Windows Vista earlier and
a couple of days back I installed Ubunru 8.04 RC on it. I did the
automatic NTFS resizing since originally there was only one partition
with 140 GB. I made a 20GB partition on which I installed Ubuntu and
the rest remained NTFS with Vista.

The installation went fine, Ubuntu seemed to run fine. It was mounting
NTFS too. I tried downloading some files to the NTFS partition and it
all seemed fine.

Now when I booted into Vista, it gave an error saying that C: needs to
be checked for errors. It progressed fine, booted, etc. Now Vista
randomly crashes say when I am watching a video or downloading a file.
Moreover, the NTFS partition would no longer mount on Ubuntu. It gives
an error saying that cannot mount NTFS partition because the logfile
says that it was not shutdown cleanly. It shows to be still in use...
blah blah.

Can anyone shed light on what is wrong? Has the resizing messed the
partitions? Do I have any recourse except to format, partition, and
reinstall everything?

Please help!

Thanks.


[Edit] This worked after I prefixed a sudo. Sorry for the trouble!

---

### Post by Pumalite on 2008-04-25
I'm not a Windows user, but I understand that if Windows is not closed 'cleanly', all sort of things can happened. As example you can end up with Ubuntu not regognizing your ethernet, etc. I think it has something to do with hibernation in laptops. In Desktops, I don't know.

---

### Post by arsenic23 on 2008-04-25
You should be able to mount that ntfs partition if you use '-o force', so it'd look like:
```
sudo mount -t ntfs-3g /dev/sdaX /whereever/you/mount/it -o force
```

---

### Post by popcorn09 on 2008-04-25
> **arsenic23 said:**
> You should be able to mount that ntfs partition if you use '-o force', so it'd look like:
```
sudo mount -t ntfs-3g /dev/sdaX /whereever/you/mount/it -o force
```

I mounted it. Now I read in some other post about ntfsfix. So I try doing - 
```
$ ntfsfix /dev/sda3
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
```

This is the NTFS partition. Any idea what is wrong?

Thanks.

---

### Post by Pumalite on 2008-04-25
Run TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Global Unity on 2008-06-28
[SIZE="5"]**XP Black-Project:**[/SIZE]

[SIZE="3"]**Preliminary Enquiry:**[/SIZE]
This enquiry is for the attention of the forum owner and moderators.
NB: I cannot find any means of starting a new thread on the Forum.

I am a new member of the Ubuntu Forum, registered as Global Unity.
I would like to present the following proposals to your forum members, for the reasons stated below. Initially I would like to discuss this proposal with you, primarily to allay any concerns you may have, especially regarding the legal implications.

[SIZE="4"]**XP Black: Salvation for MS Vista Sufferers:**[/SIZE]Global Unity is a not for profit organisation established for the purpose-mission of introducing Autonomous Socio-Environmental projects & proposals.
Most of the western world’s socio-environmental problems are directly caused by the ‘Global Un-Environmental Corporate Conglomerate’ (GLUCC) greed for political power & financial profit. The GLUCC ‘locks’ the entire global public into the Centrally Controlled & Centrally Generated Energy, Food, Water & Technology systems, thereby removing any ‘freedom of choice’ or hope of creating any autonomous, Socio-Environmental, sustainable systems or better ‘Quality of Life’.

[SIZE="4"]**What started out as the ‘American Dream’ has ended up as a ‘Global Nightmare’ we now know as Global Warming.**[/SIZE]

It is Global Unity’s intention to establish a Global Network of privately & publicly funded organisations for the purpose of counteracting the GLUCC’s greed and profiteering, and introduce many autonomous Socio-Environmental proposals and projects, to create a better Socio-Environmental, Self Sufficient and Sustainable World, providing ‘freedom of choice’ and a better ‘Quality of Life’ for the entire Global Public.

[SIZE="4"]**Initially, to achieve this mission, we need a Political Presence:**[/SIZE]
Global Unity (GU) is currently establishing the APPP (Anti-Political Political Party) a UK registered Political Party & Foundation for a new form of None Political National (and later) World Government. 

[SIZE="4"]**If you doubt this is possible! Watch this Space!**[/SIZE]
The WWW (World Wide Web) is a GLUCC controlled global communications system, primarily controlled and governed by Bill Gates and Microsoft.
Fighting Fire with Fire:	
As one of its many Socio-Environmental projects, GU proposes to use Bill Gates own system and methods to provide a more autonomous WWW, allowing ‘freedom of choice’ and a better quality of independent computer and internet systems.

[SIZE="4"]**Copyright Law:**[/SIZE]
Some legal-uniformed individuals and some cynics may argue that GU’s actions contravene the Copyright Laws. However, the Public Law Company (PLC Ltd) is one part of the GU network of organisation, established in 2004, providing legal expertise and advice to GU, the APPP and other affiliated organisations.
PLC Ltd has established that as a Political organisation and in the ‘Public Interest’, GU in conjunction with the APPP can use Microsoft’s copyright material, for evaluation and research, without contravening the copyright laws.
Also in view of the recent US court rulings against Bill Gates and Microsoft, any incidental infringement can be argued as justifiable and reasonable cause, in the public interest.

[SIZE="4"]**The Research & Evaluation Team:**[/SIZE]
To successfully carry out the proposed research & evaluation of any proposed PC and Internet systems, requires many 1000s of private member testers and researchers, to run the proposed systems, and to provide feedback on their opinions and findings.

[SIZE="4"]**XP Black: Salvation for MS Vista Sufferers.**[/SIZE]
At last some very clever computer experts (some unkindly call them ‘Nerds’) have ‘Reverse Engineered’ an alternative system called ‘XP Black’, which demonstrate that Microsoft’s ‘Vista’ is purposefully designed with flaws (bugs) and built-in obsolete systems, to illegally create further sales of other Microsoft products.

[SIZE="4"]**About XP Black:**[/SIZE]
XP Black is a ‘Reversed Engineered’ combination of the best parts of Microsoft’s XP and Vista programmes, taking the best from both, to provide a smooth and workable package, as Bill Gates could and should have done, had he not been so intent on profiteering, greed and controlling the market.

[SIZE="4"]**International Copyright Law: Legally: We’ve got it covered!**[/SIZE]
Since XP Black is subject to the usual international copyright laws, one cannot legally buy or sell copies of XP Black. As part of Global Unity’s (GU) mission, in conjunction with the APPP, to research and create a more autonomous global society, we are offering XP Black for free, and asking a select number of private members to test-drive XP Black and give their feedback and opinions regarding the program and the mission.

[SIZE="4"]**XP Black HDD Installation:**[/SIZE]
To achieve this mission, Global Unity’s proposal is to install XP Black on a new Hard Disk Drive (HDD) of your choice. The installation takes an average of around 7-hours, for which GU charge an installation fee of £75 ($150) plus the cost of the HDD, plus recorded delivery p&p (mailing costs). (Most of the installation fee will go towards funding the GU-APPP mission).

The new XP Black HDD is then mailed to your address and installed in your computer as the ‘Master’ HD, along-side your existing Vista etc HD, which then becomes the ‘Slave’ HD. Your old MS Vista, XP etc is untouched and remains on your old HDD, just in the unlikely event that you ever wish to use it again.
The New XP Black HD becomes your ‘front end’ operating system (OS) by-passing Vista. You can then access your personal files on your original-slave HD, placing links on XP Black ‘Desk Top’, or you could copy all your personal files to the new XP Black HD and use your old HD as a backup and extra storage disk.

**This system allows you keep your existing Microsoft ‘Vista’ package intact,** complete with all your personal files. This is ideal if you ever wish to revert your PC back to its original Vista package, for example, if you wish to pass your PC onto someone else or sell it.

[SIZE="4"]**APPP Private Members Registration:**[/SIZE]	
For legal reasons, and to comply with copyright law, all participating members are also required to register as members of the APPP (Anti-Political Political Party) for an annual fee of £25.

[SIZE="4"]**XP Black is fully transportable:**[/SIZE]
Unlike all MS packages: Vista, XP etc, **_‘XP Black’ is not specific to one computer and does not require any MS access or verification codes._** This means that if you wish to change your PC, you can remove the XP Black HD and transfer it, with all your personal files, to any other new or old PC, **_without having the worry and hassle of registering or verifying it with Microsoft._** XP Black also takes up far less PC memory, which is one of the main problems with Vista.

[SIZE="4"]**Installing XP Black on your PC:**[/SIZE]
If you wish to install the XP Black HD yourself, we can provide specific instructions to do this, however you may wish to ask a friendly, local PC engineer to do it for you.
Microsoft charge around £300 for their useless Vista rubbish, and they have withdrawn Windows XP (which was the last reasonable MS OS) from the market, specifically to ‘encourage’ people & manufacturers to buy MS Vista.

[SIZE="4"]**Automatic MS Updates:**[/SIZE]
XP Black also provides automatic, free access to all MS updates and downloads, but avoids what has become known as Microsoft ‘Nag Ware’. 

XP Black also comes with a vast array of other software, including Office 2007, AVG (Anti-Virus Guard) and the latest MS Photo Shop. 

The trial version of XP Black also comes with a 7 day money back guarantee, provided you have not attempted to copy or otherwise alter the HDD. 

We are also interested in contacting like minded computer engineers for technical advice, promotion and installation purposes.

[SIZE="4"]**To the Owner:**[/SIZE]
Initially I would like to discuss these proposals with the forum owner, especially the legal implications, which may cause you some concern, which are being handled by the Public Law Company (PLC Ltd).

Thanks for your attention to this issue.
John A Webb: Founder: Global Unity, PLC Ltd & the APPP (Anti-Political Political Party)

Contact Details:
Dr. John A Webb PhD
[email][COLOR="Blue"]globalunity2000@aol.com[/COLOR][/email]

PS: If possible please re-submit this message as a new thread.
Thank you.

---

### Post by Pumalite on 2008-06-28
What is this doing here?

---

