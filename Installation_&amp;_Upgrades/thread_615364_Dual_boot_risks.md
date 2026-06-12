---
title: "Dual boot risks"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by teabuntu on 2007-11-17
Hi,
Not sure if this isthe place, but, I'm currently tyring to learn more about security risks with dual booting Windows XP Home Edition and Gutsy Ubuntu. Since I'm totally new with things Ubuntu, Linux as well as computers in general, my question may seem like a no brainer, but I hope you would bear with me. 

Is it possible for anything like viruses or other nasties to migrate or transfer from one partition to another? Eg: from Linux partition to Windows or vice versa? 

Does Linux OS and Windows XP share a "common" partition when both OS is installed on a single disk? What about on seperate disks, such as having Windows OS on the main hard disk of a laptop, then installing Ubuntu on a USB flash drive? Would security risk diminish if the 2 OS were to be installed on seperate disks?

Some one on this forum once stated that even if you have a password set on your Windows program, if you use Linux, you can "see" the password and the reason is, it's because the two operate differently. If that is the case, then wouldn't having both OS pose a grave security risk when using the Windows OS? Because Linux is installed, wouldn't it make it really easy for someone who knows an awful lot about Linux to use the Linux OS on my laptop to "see" things or even start taking control over my computer even with security program installed on Windows OS?

Lastly, the firewall program like Firestarter for Linux, does it work in the same way as other firewalls designed for Windows? What about anti-virus programs for Linux like ClamAV? Do they only block known viruse for Linux or does it also take care of viruses designed to attack Windows for people who are dual booting?

Thank you for any advice or help on this matter.

---

### Post by rsambuca on 2007-11-17
> **teabuntu said:**
> Hi,
Not sure if this isthe place, but, I'm currently tyring to learn more about security risks with dual booting Windows XP Home Edition and Gutsy Ubuntu. Since I'm totally new with things Ubuntu, Linux as well as computers in general, my question may seem like a no brainer, but I hope you would bear with me. 

Is it possible for anything like viruses or other nasties to migrate or transfer from one partition to another? Eg: from Linux partition to Windows or vice versa? 

Does Linux OS and Windows XP share a "common" partition when both OS is installed on a single disk? What about on seperate disks, such as having Windows OS on the main hard disk of a laptop, then installing Ubuntu on a USB flash drive? Would security risk diminish if the 2 OS were to be installed on seperate disks?

Some one on this forum once stated that even if you have a password set on your Windows program, if you use Linux, you can "see" the password and the reason is, it's because the two operate differently. If that is the case, then wouldn't having both OS pose a grave security risk when using the Windows OS? Because Linux is installed, wouldn't it make it really easy for someone who knows an awful lot about Linux to use the Linux OS on my laptop to "see" things or even start taking control over my computer even with security program installed on Windows OS?

Lastly, the firewall program like Firestarter for Linux, does it work in the same way as other firewalls designed for Windows? What about anti-virus programs for Linux like ClamAV? Do they only block known viruse for Linux or does it also take care of viruses designed to attack Windows for people who are dual booting?

Thank you for any advice or help on this matter.
Hi,  hopefully I can help you with a couple of your questions.  

First, whether Windows and Linux are on the same physical drive or two separate drives doesn't matter.  They don't share any filesystems at all, so there is no "virus hopping".

Basically there are no linux viruses out.  There have been some tested, but there are no real known viruses to worry about when using linux.  You can, however, receive a windows virus via email, and then spread it to someone elses computer if you send the email on.  That is the only reason to really use a virus scanner on Ubuntu.  Some people also use the anti-virus in Ubuntu to scan Windows drives.

Firestarter is a GUI frontend to the linux iptables.  Basically, unless you are running a server, you don't really need to install Firestarter, as the default iptables should be sufficient.

Hope that helps a little bit.

---

### Post by scannerdarkly on 2007-11-17
As far as the password thing that your talking about the only thing i can think of is that using a program to decrypt the SAM file in Windows would expose your password.  But you can do that without even gaining access to your linux install.  For the most part for virius's there really aren't that many out there for Linux.  I mean there are a few but for the most part if you make sure you don't open emails from people you don't know or if you get an error message from a website and you don't know what it is don't click ok.  You should be ok on the virus front.  Technicoly if a virus was written to look for Windows partitions then yes that would or could happen.  I haven't seen one that does that.  You should always use a good password practive.  Use long passwords that have letters and numbers with maybe some cap letters as well.  You can't protect your password totally but you can make it take a long time for them to gain access to your computer.  That's more old school hacking.  If someone really wants to get in they will.  Regardless of your security.  I don't want to scare you but that's just a fact.  Not sure how clamav works but I'm sure it's just the same as other security products.  Firestarter does work like other firewalls.  You can set up rules and open and close ports.  In reality you should only have the ports that you need open and close the rest.  

Windows and Linux only share a comman physical drive.  The partitioning is totally different.  Linux for the most part uses ext3 and Windows uses NTFS (you should always partition in NTFS for Windows).  Without a 3 party app Windows can't read/write on a Linux partition.  Even the 3rd Party app's aren't that great.

In general just be aware  of what your doing and what is going on on your computer.  If you feel that perhaps your computer is hacked then just wipe out and start over.  It's a pain but that will work.


Security is very important but don't make it stop you from doing something new.  I triple boot with Windows, Mac OS X, and Ubuntu.  I don't use any Virus scans I only have the simple Firewalls that come with each OS.  Never been hacked.  Downloaded a virus on Windows once but that was years ago. 

Have fun!

---

### Post by Herman on 2007-11-17
Ubuntu actually prevents Windows from being exposed to anything bad if you only use Ubuntu to collect email and browse the internet. If you avoid going on the internet in Windows as much as possible, (only maybe to get Windows  Updates or updates all your various anti adware, spyware, virus etc, etc,) you will find that all your scans in Windows by the battery of apps you need to run all the time will begin to come up clean.

If you transfer files from Ubuntu to Windows it might be a good idea to scan them first, just in case, because since viruses don't hurt Linux, there could be one there somewhere undetected. You can probably transfer files you made yourself without any problems, but files you downloaded from the internet might be different.

Actually, if you really want to be safe, the best thing to do is delete Windows altogether and just use Ubuntu. Or at least avoid using Windows except when you really need to (I don't know why anyone would need to though).

Windows is easy to get into without any password, or by changing the password, or by finding out the password, just type 'Windows XP Password' into google and you'll see. There's no reason to think the presence of Ubuntu can weaken Windows. Windows is already weak and vulernable by default, built that way from the ground up.

One thing I noticed, when I am using SSH Networking inside my home LAN I can easily get into any mounted Windows system via an other computer's Ubuntu and do whatever I want. Except I needed the Ubuntu password first in order to get into the other computer's Ubuntu in the first place. 
In a family home environment that probably doesn't matter too much. In a business or work environment you would use file ownership and permissions and user accounts to control who can access what in each computer anyway. It's just something to be aware of though. Most people who dual boot have their Windows file system automatically mounted at boot-up by having it listed in /etc/fstab.
You have to install SSH Server software to enable that though, so you know what you are doing.

Here is a great link, [Security in Ubuntu]("http://www.psychocats.net/ubuntu/security") by aysiu, I really think that's a must-read! I especially like the last part about the user being the most important part of OS security. That's so true! :lolflag:

Regards, Herman :)

---

### Post by scannerdarkly on 2007-11-17
> **Herman said:**
> Windows is easy to get into without any password, or by changing the password, or by finding out the password, just type 'Windows XP Password' into google and you'll see. There's no reason to think the presence of Ubuntu can weaken Windows. Windows is already weak and vulernable by default, built that way from the ground up.

He's so right about this.  Most people don't realise that Windows has what they call Administrative shares.  That is that any drive that has a drive letter is shared by default.  You just have to know that it's there.  Windows installs to the C: drive for the most part.  Well that's where the OS is installed and lets just say you are using the admin account and that account doesn't have a password.  You just gave anybody a free pass to your computer.  They can lock you out, steal your info, and they can even damage the OS itself.  I believe that in Ubuntu the only thing that's shared from the start is the spool directory.

---

### Post by teabuntu on 2007-11-17
Hi,
I just wanted to quickly say thanks to all you guys for taking the time to reply.  I'm still reading your posts as I write this.

---

### Post by mellowd on 2007-11-17
If anyone got your laptop and knew that much about linux they wouldn't even need linux to be installed because you could boot off a live cd and do what you want.

also, anything installed in an OS is useless unless that OS is running. i.e. whatever 'security' programs you have installed on windows won't make a bit of difference unless the program and the OS is running. when it's not running it's just bits on a disk

---

### Post by glotz on 2007-11-17
Dual boot risks? None. :)

---

### Post by LaRoza on 2007-11-17
> **glotz said:**
> Dual boot risks? None. :)

If the other OS has write access to the other partitions, it could be fatal. Now that Ubuntu has default write access to NTFS, it is easy to delete essential Windows files. (This isn't a problem) The real danger, I believe, would be if Windows had write access (which is possible) to Linux. A virus in Windows could then alter that partition. 

The permissions are not honored when doing this.

---

### Post by seachnasaigh on 2007-11-17
There aren't very many viruses out there written with Linux in mind, but there are a few. There are also some rootkits and several ways to hack it, but these are largely aimed at servers, not desktop Linux machines. You're much, much safer using Ubuntu than Windoze.

That said, as Hermann pointed out above, the user is the most important part of security, and major congrats to you for thinking of this stuff and having the presence of mind to ask about it. You're using your most important asset ... your brain!

No password is 'unhackable'. Johntheripper, a popular password cracker, will take about 4 seconds to crack a lowercase all-letter password; it'll take about half an hour to crack one with letters and numbers only (8 chars or less), and between 6 and 15 hours to crack a password that has uppercase letters, non-letter symbols (like * and % and #) and numbers (8-10 chars).  The question comes down to: how important does the hacker think your machine is? For your lappie, the answer is probably always going to be "not at all" unless you're Donald Trump's nephew or something. ;) Pick a good password, using a combination of letters, numbers, and symbols, and at least 8 characters. You'll be just fine with that.

You should pick the same sort of passwords for your windoze side, disable the guest account, change the name of the administrator account to something else (pick something other than pwnr, master, etc) and insert a random empty folder near the top of your C:\ drive root. Those things make hacking any windows fs, even from a linux os, much harder. 

Good luck!

ckr

---

### Post by LaRoza on 2007-11-17
> **seachnasaigh said:**
> 
No password is 'unhackable'. Johntheripper, a popular password cracker, will take about 4 seconds to crack a lowercase all-letter password; it'll take about half an hour to crack one with letters and numbers only (8 chars or less), and between 6 and 15 hours to crack a password that has uppercase letters, non-letter symbols (like * and % and #) and numbers (8-10 chars).


My password for the most important hardware, is an MD5 hash of a word. Easy to retrieve, if you know the word, but difficult (impossible?) to crack.

---

### Post by Herman on 2007-11-17
I agree, a good strong password is important. It isn't everything, but it is very important.
I like to have a password that is based on two or three special letters on the keyboard that are easy to remember.
You press the special key itself, then you press surrounding keys to make a shape, like a circle (hexagon), or a rhombus around the main key, then press the special key again. 
Then you go to your second and third specail keys and do the same thing.
You can go clockwise or anticlockwise around your special keys.

If you are having a hard time understanding what I mean, here is a link to an illustration, [password tip]("http://users.bigpond.net.au/hermanzone/p2.htm#password_tip").

I think that should help people to have a good strong password with lots of characters in it that they can easily remember, (because really they only need to remember two or three special letters), and I think that would be hard to crack.

Everyone can remember two or three letters.

From three letters you can have a 24 character password, but one that's easy ofr yourself to remember!

That means you can probably remember lots of different passwords too, because one of the  problems with passwords, is, people can be tricked into giving away their password ( for a fake IT help caller or something like that maybe), and if people use the same password for everything, they have access to everything you own!
Many people do use the same password for everything, because they are afraid of forgetting it themselves and getting locked out of whatever the password is for.

I hope I'm not giving too many secrets away here already. :)

Anyway, the thing is to make it as convenient for yourself and as inconvenient for the potential cracker as possible.

'Password Manager' is a good program in Ubuntu, available from 'Applications'-->'Add/Remove Programs'.

Regards, Herman :)

---

### Post by Depressed Man on 2007-11-18
My professor does that for the lab security systems lol. Though he pointed out that anyone that observes him will notice the pattern he uses. Passwords are problematic...we have to pick strong passwords which are hard to remember by us yet have to be unique.

You could always try chunking the passwords..but it seems kinda pointless if your going switch it in 6 months..which leads to other problems (post it notes, etc..).

---

### Post by teabuntu on 2007-11-18
> **seachnasaigh said:**
> There aren't very many viruses out there written with Linux in mind, but there are a few. There are also some rootkits and several ways to hack it, but these are largely aimed at servers, not desktop Linux machines. You're much, much safer using Ubuntu than Windoze.

That said, as Hermann pointed out above, the user is the most important part of security, and major congrats to you for thinking of this stuff and having the presence of mind to ask about it. You're using your most important asset ... your brain!

No password is 'unhackable'. Johntheripper, a popular password cracker, will take about 4 seconds to crack a lowercase all-letter password; it'll take about half an hour to crack one with letters and numbers only (8 chars or less), and between 6 and 15 hours to crack a password that has uppercase letters, non-letter symbols (like * and % and #) and numbers (8-10 chars).  The question comes down to: how important does the hacker think your machine is? For your lappie, the answer is probably always going to be "not at all" unless you're Donald Trump's nephew or something. ;) Pick a good password, using a combination of letters, numbers, and symbols, and at least 8 characters. You'll be just fine with that.

You should pick the same sort of passwords for your windoze side, disable the guest account, change the name of the administrator account to something else (pick something other than pwnr, master, etc) and insert a random empty folder near the top of your C:\ drive root. Those things make hacking any windows fs, even from a linux os, much harder. 

Good luck!

ckr

Hello,
Thank you for taking the time to reply.  I really appreciate all of you for taking the time to reply to my questions.  I realize notw taht there is no lcear cut answer when discussing security, or anything related to computers for taht matter.

Just a little background here about myself, and why I'm askng about security.  I know that when I have asked around about security, people have tended to question my set of questions, saying that they don't understand why I'm asking about such things.  After all, it's Linux.  I'm not saying at all that any of the people qwho have replied to this particular thread have said this, but I've come across a few on other occasions... Anyway, the reason why I became so intersted in learning about security and other things realted to computers is because I almost screwed up my computer from doing something that was suggested as being safe.  I'm talking about BIOS updates.  Now I learned after doing the updates that it's not really safe at all, especially doing the flahs method.  But I was prompted by Dell Support software (I have a Dell), that I ought to update my BIOS, and that it's critical.  Long story short, the update said it was successful, but after the update, I immediately started hearing these high pitched sounds from the top right hand corner just where the AC adapter goes into the laptop.  That incident is what started me from asking questions before doing anything, regardless of what others have said is safe to do (actually, when I called Dell Tech Support about this problem, they said flashing the BIOS from Windows is a very safe thing to do).  

Since I'm totally new with Linux, and I know from reading the posts on this Ubuntu form that I'm quite lacking in computer knowledge.  So I'm learning as much as I can, but I must admit, with the wealth of info out there about Linux and Ubuntu, it's quite confusing to figure out what to believe and what to do.  Right now, I'm at a stage where I finally got a hold of Ubuntu Live CD (the first one that was shipped to me from Shipit was missent to Iran, and when it came to me, all the discs would not even boot the Live CD).  I'm playing around with it, and I love Ubuntu.  So far, my printer works and my wi-fi is recognized as well, but I'm having difficulty connecting to the internet using dial up.  But the most improtatn aspect of installing Ubuntu for me is security.  I don't know yet how files, and partitions interact with one another.  As much as I know linux is safe to use (especially compared to Windows), since I'm considering having 2 OS, I don't know what the impact would be on Windows if I'm connecting to the internet through Linux.

Thank you all for taking the time to help me understand things better about Linux.  Although I'm not 100% clear on what goes on when both Windows and Linux is installed, I have a far better picture than when I started because of all of your help.  Thanks.

---

### Post by jwalling on 2007-11-18
Here are 3 primers on installing dual boot for Windows and Ubuntu:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This utility allows windows to read/write the Linux file system:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

An alternative to dual booting  is to use VMWare or VirtualBox:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.vmware.com/products/ws/](http://www.vmware.com/products/ws/)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

By reading those resources you may get a better idea of where the potential security risks are.

---

### Post by bulldog on 2007-11-18
Basically,if you boot into Linux,working as a user you're quite safe.
You **can** set read/write NTFS partitions on,but it isn't by default,you only have read access to your NTFS partitions,not write access.
Linux won't do anything with your windows,except when you told it to do.
Same wise with booting windows,it doesn't even see your linux partitions,only it knows there's a hdd connected but it can't read or write to it.
If you share a FAT32 partition between windows and linux,and you make this the place were your email would be stored,so you can get email through windows as well ubuntu,your taking a risk.
With windows that is,malware which came on that partition can do almost nothing with linux,but it can damage your windows.
So not sharing partitions would be better IMHO.

---

### Post by teabuntu on 2007-11-20
Hello,
Thank you for your posts.  I appreciate it.  These last couple of days have been hectic so I haven't been able to really sit down and spend time on computers as I would like.  Thus, I could not reply sooner.  Thanks again though.

---

### Post by seachnasaigh on 2007-11-20
You're quite welcome. I don't think the Linux community would exist without folks like you, willing to take some chances, and we've all done the same. It's a cool place to be.

As LaRoza, above, says, yes ... you can create some very sophisticated sorts of passwords that are not really easy to hack. MD5 hashes are typically the realm of the professionals; in the professional world, we do a lot to secure our hardware -- closing ports, reactive firewalls, NAT, etc etc etc -- in order to keep the bad guys out. It's a more-or-less constant war. However, on the consumer/home user side, there are some fairly simple things you can do, and a lot of good folks here have mentioned them, to keep script kiddies and bots away from your machine. The bad guys are (and it's tough to remember some days) almost as short of resources as we are. 

It's kind of like using the built-in door locks on your car. Just locking your car keeps most casual thieves at bay; sure, a determined professional could break into it, but most casual thieves will walk away, looking for the sloppy victim who forgot to lock the doors. The same applies to internet baddies ... a couple of quick knocks on your door to make sure you're not an easy mark, and they move on. A determined hacker with plenty of time can (and will given the evidence) crack most systems, but the price (time) has to be equal to the payoff for most crooks. 

As I said, take the good precautions ... good password, decent firewall, use Linux on the internet wherever possible ... and you'll be OK, way ahead of most folks using out-of-the-box Redmond OS's. Bulldog (above) had a great point about not sharing too many of your files across your dual boot; damned good advice, really. Especially the bit about your email. I'd use a web email client and forget storing it locally. Where you need to share files, mount a USB flash drive on both systems and use that. With good AV software on both sides, you're going to be able to sleep at night.

Cheers!

ckr

---

