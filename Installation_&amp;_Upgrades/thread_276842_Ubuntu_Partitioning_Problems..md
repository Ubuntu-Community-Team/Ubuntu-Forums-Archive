---
title: "Ubuntu Partitioning Problems."
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by ctrl_freak on 2006-10-13
Hi,

I'm a completely new user to Linux, and have only had a small amount of experience with Boot-from-CD distros. I decided, based on that Windows was crashing too much and M$ was screwing around,  I would jump straight in and install Ubuntu. I had read recommendations in high profile tech magazines regarding the ease of installation and use and thought Ubuntu would be the best place to start.

The boot from CD worked fine, as well as most of the installation. However. I carefully manually edited the partitions to resize my XP/NTFS partition, create a FAT32 partition for share and an ext3 partition for linux. All seemed to go well until it completed the actions.

[|                    NTFS                    | fat32 |     ext3     |]


It finished up claiming that the hdd was now 'Filesystem: Unknown', the FAT32 partition was 7.84Mb, and the ext3 was 0Mb.

I can't seem to figure out what went wrong. I did everything right, including allowing more than 3Gb for the linux partition (in fact it was intended to be about 13Gb).

My hdd is ~78Gb and the NTFS partition was filled to about 60Gb.

I realise that there is considerable risk in creating and resizing partitions, however I largely did not expect this and are glad there isn't anything extreemely important on the drive.

Now, all partitions are inaccessible, both to Ubuntu and XP (which in reality no longer exists on the drive.)

I am now faced with a complete format, the reinstallation of XP and Apps/Programs. I am hoping there is a way out - to somehow miraculously restore the system.

Any help would be HUGELY appreciated.

Cheers,

ctrl_freak

EDIT: I was installing 6.06 LTS

---

### Post by Herman on 2006-10-13
Try downloading your own [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), (free and less then 30 mb download size), it includes a program called '[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")', which has recently been used a couple of times with great success to perform similar tasks to what you want to do. Be sure to read the TestDisk documentation first.

TestDisk is also available on a few other Live CDs, such as Knoppix and I don't know what others. It could even be in Ubuntu's Live CD too, I haven't chacked. I know it's in the repositories.

Good Luck, I hope it will work, I'll keep my fingers crossed for you!

Regards, Herman :D

---

### Post by Herman on 2006-10-13
Posted by mistake, (keyboard fumble), (sorry)

---

### Post by Herman on 2006-10-13
To run TestDisk from GParted LiveCD, you just open a terminal, and type 'testdisk', and a TestDisk window will open for you.

I had a corrupted partition table once, after I decided to sample every different brand of disk partitioning software I could get my hands on. Fortunately, these things happen very rarely. I believe now in sticking with only Gnu Parted based partitioning software, and I avoid 'mixing' partitioning softwares now. I can not even tell which partitioner might have been to blame, because errors left by a previous partitioner can trip up the next one, or so it seems.
I hadn't heard of TestDisk, in those days, and I can't even remember for sure if GParted had been invented yet then or not. I fixed it by deleting all partitions and starting again. The Ubuntu installer's partitioner in the old 'Alternate' CD's installer fixed mine. I haven't had any more trouble since, and I use disk partitioners all the time, as I make a website for the 'Alternate' CD, so I need to test the installer quite a number of times.
I also make test installations and do risky things with them to try out ways of fixing other people's problems too, so I also use GParted LiveCD all the time.
GParted LiveCD also features [Partimage]("http://www.partimage.org/Main_Page") now too, for making backups with.

---

### Post by ctrl_freak on 2006-10-13
Thank heaps - I'll give it a shot and keep you updated.

UPDATE: Reading around, it seems like it was a bad idea to resize the NTFS partition using Ubuntu, and should have really used the Windows Disk Manager. *sigh*

---

### Post by Herman on 2006-10-14
> UPDATE: Reading around, it seems like it was a bad idea to resize the NTFS partition using Ubuntu, and should have really used the Windows Disk Manager. *sigh* No, you did right,  the Ubuntu installer's partitioner has been perfectly safe with NTFS filesystems ever since the Ubuntu 'Hoary' edition, the first edition, Ubuntu 'Warty' had a few bugs with NTFS, but that was a very long time ago. Since then there have been almost no reported problems with either the older 'Alternate' installer's menu based partitioner, 'Partman', or the newer GParted in the 'Desktop' LiveCD Installer. 
Well, nothing is perfect, but compared with the number of uses, problems are extrememly rare, and may not be completely the fault of the software either, other factors might be involved as well. Take for example, your own situation, where Windows wasn't running properly before you decided to install Ubuntu. How would anyone know for sure there wasn't some underlying problem there before you inserted your Ubuntu CD? It could be hardware, or a malware (virus)  type of problem.

In my opinion, open source software is more honest. No-one is here to rip you off, so there is no reason for anyone to tell you anything that's not true, or to hide the truth from you. When you use open source software, there are publically accessible web forums like this one, and GParted LiveCD's own web forum, and others as well, where any problems can be publically posted and discussed. And for most problems, you can get free help.

When you use commercial partitioning software, it has just as many (if not more) problems, but there are no public web forums to help you. You may get help, but it is all done in secret, behind closed doors, so to speak. They wouldn't dare let all their problems be publically exposed. So, you have to log into some site with your serial number or other password. You might even have to pay for help too. If I wanted to, I could link you to several threads right here on this very forum where commercial software has been thought to be the cause of major problems. Some are very recent too, like within the past week or so.

In my opinion, the right partitioning software to use for Ubuntu is any 'Parted based partitioner. GParted is excellent partitioning software, I think it is the most advanced of the 'Parted based partitioners.

Regards, Herman :D

---

### Post by ctrl_freak on 2006-10-14
Sorry, but I seemed to have in my mind to use testdisk? Or should I use gparted?

I've run into some troubles with installing testdisk, largely because of my inexperience and unfamiliarity. I can't seem to figure out what to do with the downloaded file (Linux) on the CGSecurity Wiki, and apt-get can't seem to find it.

I'll have a look at gparted and figure that out.

btw: I saw in your sig, you're website is hosted on Bigpond! I'm an Aussie too! Thanks for the timely responses.

UPDATE: I've taken a screenshot of the view in gparted, hopefully it'll help. It only seems to be able to reformat as NTFS etc, not able to change the partition type.

---

### Post by Herman on 2006-10-14
Yes, that's the best idea, TestDisk is already included in the GParted LiveCD, so you don't have to worry about installing anything now.

You can ignore that Gparted desktop for now. Can you see four little squares down on your bottom bar? Over towards the left? One has your current Window showing, and the others are empty. Just click on one of those desktops and open a terminal by clicking on a little black square over towards the left there. It's about fifth from the left in mine, and it has a $ sign on it.
That opens a terminal in GParted LiveCD for you.

Now type in ' testdisk ' after the prompt, ```
testdisk
``` You may need to click in your 'maximize' square in the upper right of the terminal window to enlarge it.

Then use TestDisk as outlined in the TestDisk docs from the link I provided earlier and hope for the best.  I hope it will work well for you, as I said, others have reported successes with TestDisk recently, so with luck and skill it should help you too, all the best,
Regards, Herman :D

And yes, I'm living in outback Queensland.

---

### Post by ctrl_freak on 2006-10-14
So I should download the LiveCD? Sorry, I'm slow on catching on... :rolleyes:

---

### Post by Herman on 2006-10-14
Yes, I recommend GParted's LiveCD, it's great! Download the latest version, last time I looked it was GParted 0.3.1-1
You can get it for USB drives too I think, I use the ,iso files and burn them to CD-RW disks, because then when a newer version is released I can just re-write the same CD.
Here's a link to GParted's download site, [click here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828").

---

### Post by ctrl_freak on 2006-10-14
I seemed to have thie idea that testdisk was already installed on Ubuntu, or was available on apt-get. Thanks, DLing and burning now.

Thanks for all this help. I'll report back when I've achieved something.

UPDATE: I've DLed and burnt the image, rebooting

---

### Post by ctrl_freak on 2006-10-14
It worked well, gparted, and did a good job of identifying the original NTFS partition and changing it back (but was still unbootable - or didn't boot), however unfortunate circumstances caused me to have to cancel the moving and resizing of the partition and I think it might be rendered useless. Hope fully I'll be able to do a bit of shuffling as to install Ubuntu and backup the data on the NTFS (primarily music, images and websites), then start again.

Thanks again, your help was awesome.

Cheers.

ctrl_freak

---

### Post by Herman on 2006-10-14
Not a problem, well, at least your data is accessible now.
I would suggest rescueing it with a LiveCD, but anyway, you haven't asked for help with that, but I can help you with ways to rescue your data if you need it.
After the data has been rescued, I would try to boot it with a Windows Boot floppy disk (if you have a floppy disk drive), the best kind is the type you can make yourself, they have NTLDR, boot.ini, and NTdetect on them, here's how, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").
It would be worth a try. Maybe Windows just needs a good scandisk and a lot of defragging, if you can get it to boot up, it would probably be best to use your Windows' own utilities for that. I have never looked into what utilities you can run from a LiveCD to fix Windows, but there would probably be some good apps available for that.
Anyhow, I'm glad if you can rescue your info at least. Actually, a good clean re-install does Windows a real lot of good, probably that's the best anyway. It's awfully time consuming though, I'm glad I use Ubuntu, (complete re-install in under an hour. Actually, I can copy a spare copy of a Ubuntu install and paste it over a broken one in less then ten minutes with GParted).
Good on you for persevering with it so far, too. Let me know how you go and sing out if you want a hand again.

Regards, Herman :D

---

### Post by ctrl_freak on 2006-10-16
(Note: I had written a long explanation etc, but the seemingly buggy log in system of these forums caused me grief and I lost it.)

I'm afraid I lost all my data, but started again with a properly partitioned computer, with Ubuntu installed properly.

I have run into some problems - my current network setup isn't allowing Ubuntu to access the net. It has already worked before on the network where the initial problem happened, but I haven't been able to test it on the current network as a LiveCD.

Due to this I'm pretty sure it's my router playing up - I'll get onto the manufacturer about it.

Also:

The other partitions (fat32 and ext3) are seemingly recognised as removable storage - they have the same icon as the floppy and cd-rom drives. When double clicked or opened, it comes up with a message such as 

error: /.../.../hda1 is not a removable drive
error: pmount command failed

or something of the like, I don't have access to the exact error at the moment. I'm hoping an XP quickformat of the NTFS drive will help.

Is there any tips you can give that I might have done wrong?

---

### Post by Herman on 2006-10-16
I am very sorry that you lost your data, ctrl_freak. 
I'm glad you are back again though.

About your networking, have you tried looking in 'System'-->'Administration'-->'Networking', and making sure your Wireless, Ethernet or Modem connection is activated (enabled) and properly configured? (DHCP or Static IP, etc). ?

About your mounting other filesystems, normally Ubuntu automatically detects other filesystems (partitions), and we get an icon for each one on our desktop, but not every time. Sometimes we have to mount them ourselves. Here's a link to my page on mounting, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm") have a read and see if that will help you. It also contains a link to aysiu's page on mounting as well, which is very good.

You can check in your /media directory to see if there are already some folders in there or not for those other partitions and if not, make your own. 
Then you add a line in /etc/fstab and type 'mount -a', or reboot. The web page will explain it all. 

Opening 'Places', 'Computer', '13.4GB Volume (Icon) results in the same error message for me too. That's not the right way to do it.

Going 'System', 'Administration', 'Disks' and clicking 'enable' doesn't seem to do anything for me either. although the official help info seems to say it should. Maybe it's something still under development or something.

If you need more help let me know. I'll keep an eye on this thread for a while, for any help I can give you.

Regards, Herman :D

---

### Post by ctrl_freak on 2006-10-16
Yes, your page helped me heaps - I now have them mounted with fstab, both the Windows and fat32 partitions.

Yes, I have checked the networking settings, it's as it should be. I'll get onto the manufacturer.

-- I've fixed it through help on these forums! This is a great place! I'll be sure to come back whenever I have a problem.

Many thanks again for your time and help - you're a great teacher to introduce me to the inner workings of Ubuntu and Linux.

Good luck, bye for now.

**ctrl_freak**

---

### Post by egd on 2006-10-23
> **ctrl_freak said:**
> 

Now, all partitions are inaccessible, both to Ubuntu and XP (which in reality no longer exists on the drive.)

I am now faced with a complete format, the reinstallation of XP and Apps/Programs. I am hoping there is a way out - to somehow miraculously restore the system.

Any help would be HUGELY appreciated.

First off, personally I'd never contemplate resizing NTFS partitions with Linux based tools - you're always better using a windows based tool to do that first, then install Linux.

If you're really intent on recovering the data, here is a long winded way to go:
Install a 2nd hdd in the machine and install windows to that disk - don't write to your original windows drive / partitions.
To try to recover data / make your box bootable again I'd get a demo copy of GetDataBack for NTFS.  No guarantee it'll recover your system, but there is a pretty good chance if the win partition has not been overwritten it should be recoverable.  If the demo confirms data is recoverable then the next step is to buy the program and use it to recover to another drive in the same machine or a networked drive.  Sounds long winded, and it is - it's just a question of how important the data is to you.

---

### Post by gn2 on 2006-10-23
What was originally posted here was entirely wrong.

---

### Post by ctrl_freak on 2006-10-23
It's ok - I'm sure, I'm not to shot up about losing my stuff - as I've said - its probably for the best! A good refresh is good once in a while.

If there is something that could have fixed it easier, it's a bit late, what's done is done. He did the best he could with what I gave him.

Let's just make sure anyone else who needs help with anything like this, finds out about it first up.

---

### Post by Herman on 2006-10-23
The original post that was here has been deleted, gn2 is forgiven. 

Regards, Herman :D

---

### Post by gn2 on 2006-10-23
> **Herman said:**
> gn2, you should learn a little bit more first before you start pretending you know everything. 
Do you have any understanding of the parts of the MBR and function of the FIXMBR command? 
How would 'FIXMBR' repair a corupted partition table? 
Now, really! :rolleyes: 

I think you just here to upset everyone and disrupt things as much as you can, I think you are a troll.

Herman, I can only apologise profusely for the offense I have caused you.

I was entirely wrong, and freely admit I do not know everything.

My intentions are never to cause disruption or irritation, sadly due to my erroneous behaviour that has occurred here.

What I would say is that the how-to thread on dual-booting with two drives I started has been useful to many.

I hope I can prevent others from falling into the traps I did with single booting on one hard drive, which is something I would continue to counsel against for the inexperienced. 

Again I can only apologise Herman,

all the best,

gn2

---

### Post by dvader on 2006-10-23
Herman 

re partitioning HD 

Is it possible to corrupt the boot sector/partition table and get an error message when booting up (Checking file systems)  , getting a text message like this 

'There are differences between boot sector and its backup'

then continuing through the boot procedure and having a operational system  

Dvader

---

### Post by ctrl_freak on 2006-10-24
> **egd said:**
> First off, personally I'd never contemplate resizing NTFS partitions with Linux based tools - you're always better using a windows based tool to do that first, then install Linux.

If you're really intent on recovering the data, here is a long winded way to go:
Install a 2nd hdd in the machine and install windows to that disk - don't write to your original windows drive / partitions.
To try to recover data / make your box bootable again I'd get a demo copy of GetDataBack for NTFS.  No guarantee it'll recover your system, but there is a pretty good chance if the win partition has not been overwritten it should be recoverable.  If the demo confirms data is recoverable then the next step is to buy the program and use it to recover to another drive in the same machine or a networked drive.  Sounds long winded, and it is - it's just a question of how important the data is to you.

Where the hell did this post come from?! I only saw it just now! Wierd... :-?

---

### Post by Herman on 2006-10-24
> re partitioning HD 
Is it possible to corrupt the boot sector/partition table and get an error message when booting up (Checking file systems) , getting a text message like this 'There are differences between boot sector and its backup'
then continuing through the boot procedure and having a operational system   Hello dvader,
I don't think that error message referes to any problem in your partition table, but  in the Ubuntu partition's  Linux ext3 filesystem, or another installed filesystem. 

I'm not sure exactly what the meaning of that particular error message really is, but I would probably attempt to solve that with an e2fsck command from a Live CD. I would try, ```
e2fsck -c -c -v /dev/hda2

``` Where, /dev/hda2 is the right designation for an ext3 filesystem, please feel free to replace that with /dev/sda2 if you have an SCSI or Sata hard disk, or with a different hard disk letter or parition number as might suit your arrangement.
Note: never run fsck or e2fsck on a mounted filesystem, use a livecd, or arrange the fcsk for boot-up, before the filesystems are mounted.

That command will take a long time to completely run, longer if you have a very large ext3 filesystem (partition), so be prepared to wait a while for it. I hope that will help you. Please let me know if it works or not.

I am not an expert on filesystems, so please take this solution with a grain of salt, but I'm sure it won't do any harm, and will likely do some good.
I was learning about filesytems recently, but I got sidetracked on to some other subject, and mean to get back to it. Filesystems are something that there seems to be a shortage of people answering posts about. I intend to do better in future. 
Here are a few of the interesting webpages I'm reading,

 [5.10. ]("http://www.tldp.org/LDP/sag/html/disk-usage.html")[Filesystems]("http://www.tldp.org/LDP/sag/html/filesystems.html")[SIZE=-1]**  Linux System Administrators Guide**[/SIZE]
     
     [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html")

**[EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")**

      **[Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")**

If anyone else can shed some more light on this subject I would be keen to read it, so please share.

dvader, I'll try to find out more and get back to you, when I have something useful. 

Regards, Herman :D
PS, I'm from Nova Scotia too. (Originally).
EDIT: Here's one link I found about it, but this one is about running dosfsck on a Windows partition, [http://ubuntuforums.org/showthread.php?t=32531](http://ubuntuforums.org/showthread.php?t=32531)

Here's another link about this error message when it's coming from a Windows partition. Is there any indication of which partition you are getting this error message from? [http://service1.symantec.com/SUPPORT/nav.nsf/aab56492973adccd8825694500552355/024c927836400f528825675100593eb2?OpenDocument](http://service1.symantec.com/SUPPORT/nav.nsf/aab56492973adccd8825694500552355/024c927836400f528825675100593eb2?OpenDocument)

---

### Post by dvader on 2006-10-24
hello Herman 

Thank you for you information . I printed it out as well as the links to file systems and XP + Ubuntu.  Will slowly go over everything and see if there is a reason for my problems .   One thing I noticed was using the alternate CD for install, and it appears that there is more control on the installation 

I am using two HD's.  a 80G for the master and a 40G for the slave.. My main OS's are on the 80 or C drive .  I did notice one thing , trying to install rc 1 of 6.10 that after setting all the fields , and ready  to install it comes up with a warning... no root 

Will start with the hardware and make sure each drive jumpers is set properly , and study the printouts .....  Will advise you as to how things work out. 

Dvader  

PS do you miss NS winters 8)

---

### Post by Herman on 2006-10-27
ctrl_freak,
>                      Originally Posted by **egd**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=1651268#post1651268")                 
                 *First off, personally I'd never contemplate resizing NTFS partitions with Linux based tools - you're always better using a windows based tool to do that first, then install Linux.*[I]There is no evidence to support the idea that open source disk partitioning software is not as good as commercial software for working with NTFS and other filesystems. Failures have been very rare, and are exposed to full public view on open web forums. With commercial software, everything is kept secret, so they can pretend their software is perfect, but it might not be really. Who can tell for sure?
> [I] If you're really intent on recovering the data, here is a long winded way to go:
Install a 2nd hdd in the machine and install windows to that disk - don't write to your original windows drive / partitions.
To try to recover data / make your box bootable again I'd get a demo copy of GetDataBack for NTFS. No guarantee it'll recover your system, but there is a pretty good chance if the win partition has not been overwritten it should be recoverable. If the demo confirms data is recoverable then the next step is to buy the program and use it to recover to another drive in the same machine or a networked drive. Sounds long winded, and it is - it's just a question of how important the data is to you.[/I]
I agree with egd on this part, as long as you didn't overwrite the data, it might still be able to be recovered if you had decided to keep trying. It's a matter of how much time you might have wanted to spend trying, and maybe even money. You might have been  successful with another application. In that case,[/I] it would have been a good idea to use a 'dd' command to copy the damaged partition to another disk too, then work on a copy of the partition and leave the original alone or vice-versa. But it's too late now if you've already reformatted and overwritten the data.  Actually, it's still not securely deleted, if somone  like a government department wanted to, (so I have read),  they can still recover data from such hard disk of they think it's warranted for some reason, but they have lots of time and money to spend.
[I] I'm sorry that TestDisk didn't do it easily for you.
According to my interpretation of TestDisk Documentation it should be good for that type of thing, and others have reported success with it. 

FIXMBR is only for writing the Windows boot code to the first 446 bytes of the MBR, and will not do anything for the partition table or your filesytems. Please refer to this link, [Click Here]("http://bootmaster.filerecovery.biz/fixmbr.html?gclid=CNGSrqalmogCFSEaTAodWiimQw").
[/I]Also, that would be presuming the problem is in the partition table, it could be in the filesystem itself, we didn't attempt to establish that.

> However, [COLOR=#ff0000]if you         have a situation with a damaged partition table, FIXMBR         is not useful[/COLOR]. In that case you will need to         rebuild the partition table using partition recovery         software.
Anyway, it's practically too late now, I wanted to straighten out a few points here just for the record though.

Regards, Herman

---

### Post by egd on 2006-10-27
> **Herman said:**
> ctrl_freak,
[I]There is no evidence to support the idea that open source disk partitioning software is not as good as commercial software for working with NTFS and other filesystems. Failures have been very rare, and are exposed to full public view on open web forums. With commercial software, everything is kept secret, so they can pretend their software is perfect, but it might not be really. Who can tell for sure?
[/I]

Herman, I wasn't for a second suggesting that open source software isn't as good as proprietary software.  In my experience open source software is often vastly superior to commercial software.  The point I was trying to make is that given NTFS is not *yet* fully reverse- engineered, you're better off going with a microsoft certified partner to recover ntfs partitions and data and/or resize an NTFS partition.

I have personally successfuly used the tool I recommended to recover data from a windows created JBOD comprising two 400GB drives with close to 740GB of data on it.  w2k3, being what it is, for some rhyme or reason decided the JBOD should be trashed and become inaccessible - damned scary that this occurs on the server end of microsoft's products, but I won't go there.  Suffice it to say the partition table was screwed and the logical drive had become totally inaccessible.  I recovered 100% of the data intact by using the tool to recover and copy it to a network drive.  I know JBODs are risky, but at the time it was created I didn't have another viable storage option.

---

### Post by Herman on 2006-10-27
> I am using two HD's. a 80G for the master and a 40G for the slave.. My main OS's are on the 80 or C drive . I did notice one thing , trying to install rc 1 of 6.10 that after setting all the fields , and ready to install it comes up with a warning... no root  Hello dvader,
It seems there are several people reporting this same problem lately. I installed rc 1 of 6.10 with the 'Alternate CD' and it all went well for me. I hope yours did too. Now I will probably delete it and re-install the released version of Edgy several times to test it and explore the installer to see what updates I need to make for my install web site.
All the best, Regards, Herman :D
PS. the only time I miss NS winters is maybe in Queensland summer, when temperatures reach up to about 47 degrees C sometimes. But most of the time the weather here is perfect, and the climate is very comfortable.

---

