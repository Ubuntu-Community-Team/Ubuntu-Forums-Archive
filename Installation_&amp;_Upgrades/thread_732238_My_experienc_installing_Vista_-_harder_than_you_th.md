---
title: "My experienc installing Vista - harder than you think."
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by pm124493 on 2008-03-22
I decided to upgrade one of my systems recently. I added a Q6600, 4 GB of memory, an nVidia 9600GT and a WD 500GB sata HD. My decision was to install Vista on the 500GB HD and Hardy Alpha 6 on the other drive, a 300GB sata. I also have a Plextor DVD RW sata drive. 
I purchased Vista Home Premium 32bit Upgrade since I already have several WindowsXP licenses. In order to install the upgrade you have to have a working WindowsXP on the drive with SP2 installed. Bad requirement number one. I installed WindowsXP on the largest partition it will support, 129.99GB. I could not use the sata drivers that came with the Gigabyte GA-P35-DS3L board. They blue screened all the time. I had to switch to IDE mode in the bios. That was trying to load the drivers using F6 option on install. I finally got WindowsXP loaded.

Then installed the Vista upgrade. Vista has to see a WindowsXP partition that has been activiated before it will install. Once loaded it took 24 hours to get the updated nVidia drivers to load. nVidia support told me I had to load the drivers in Safe mode?! Bad requirement number two. It took two hours to download the security updates (not SP1, yet). I have a 10mbit cable connection. Now Vista is loaded, but I can only use 3.5GB of memory. So I ordered the 64bit DVD "Windows Anytime Upgrade". What a misnomer.

You can not upgrade a Vista 32bit to 64bit without a clean install. Bad requirement number three. I had to wipe out Vista and reload WindowsXP. Then install using the 64bit DVD and the product code from the 32bit DVD. I installed the 64bit Vista without much incident.

The reason I decided to go with Vista was I wanted to run Crysis with DirectX 10 to see the visual differences. I must say Crysis runs smoother in 64bit than 32bit. That fun was short lived. I installed Vista 64bit SP1. That took around an hour and a half. But when I did my final reboot, Vista would hang at the black screen with the green moving bar. It would hang there for hours. I even had a hard time with getting Vista to boot into Safe Mode. Vista was hanging at loading crcdisk.sys. 

I went out to Microsoft Support web site and there was nothing on this issue. I went out on the web and found thousands of incidents prior too and after loading of SP1. I contacted Microsoft help desk and spent three hours on the phone going through the same things I did before. They left me with second level support would call between 9-11am EDST the next day. They never called.

I found out on the web where someone said that a Vista update caused the problem with sata drives. You have to copy over around ten system files from the DVD to your HD while in the command prompt. It fixed my problem. I have included the site here in case others run into this problem.
[http://windowshelp.microsoft.com/communities/newsgroups/en-us/default.mspx?dg=microsoft.public.windowsupdate&tid=03edeb5d-9259-47ac-990a-96ae08ffd4b2&cat=&lang=en&cr=US&sloc=en-us&m=1&p=1]("http://windowshelp.microsoft.com/communities/newsgroups/en-us/default.mspx?dg=microsoft.public.windowsupdate&tid=03edeb5d-9259-47ac-990a-96ae08ffd4b2&cat=&lang=en&cr=US&sloc=en-us&m=1&p=1")

The moral of this story is: Anyone tells you it's harder to get Ubuntu running than Windows just does not know what they are talking about. Drivers are an issue with any OS. Take that aside and Ubuntu beats Windows every time. If it weren't for games, I would not need Vista. Wine and Cedega have issues with games. I know. I have games running on Ubuntu with Wine. 

Installing Ubuntu Hardy Heron Alpha 6 with a brand new nVidia 9600GT still only took about four hours. All the help I needed I found on Ubuntu forums. My Vista help was also found on a forum. It is developers and the community that makes the difference. Not the corporation.

Odd though. The Windows Help Desk did not even sound concerned or phased by the fact I had Linux on another partition. Years ago they would have insisted I remove that partition before helping me. Things change.

Pete

---

