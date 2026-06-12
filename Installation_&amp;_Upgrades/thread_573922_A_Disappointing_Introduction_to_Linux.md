---
title: "A Disappointing Introduction to Linux"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by Uncle Bunty on 2007-10-12
I have kept an eye on Linux for a few years in the hope that someday it would prove a viable alternative for me. It seemed that time had come after reading a lot of the latest hype.

Being a Linux virgin I decided on Ubuntu for ease of use as touted in numerous texts around the internet. Seriously though, when I download a Live CD, then burn it and insert it, I'm told I can simply reboot and Ubuntu will do the rest. Unfortunately in my experience, and it seems many others have the same issues from viewing the forums, Ubuntu simply doesn't do what it claims. It cannot even boot from the CD let alone improve my productivity. After sitting here waiting for about an hour for something to happen, sadly I'm thinking that Linux will never be able to compete with the simplicity and effectiveness of Windows. If this is the very first step in the procedure and I already have issues, what possible chance is there that Ubuntu will be able to compete at any level with any version of Windows. At least Windows installs before the problems start!

I think it's finally time to look seriously at what all these hours that are put in by volunteers are achieving. Guys, pack up your Linux and get some sleep. This simply is not working. I hate Windows with a vengeance and Macs give me the sh!ts with their holier than thou bs, but seriously, Linux/Ubuntu is nowhere near being ready to compete with either in any way. Sorry if I'm sounding pessimistic but I know what it's like to bust your butt working on a project only to have it vanish and all your hard work with it. Save your energy, save your sanity, don't waste any more time flogging a dead horse. The irony is the catch phrase: "An operating system that just works". I am so disappointed and depressed.

---

### Post by banewman on 2007-10-12
G'day mate. Sorry to hear about your troubles. The first and most important thing is to burn the cd at a slow speed - 4x is the best. All OS's are the same in this regard.I've been using ubuntu and other linux distros since 2002 when I gave up windows and have only been productive. Like when I first used windows there was a learning curve - but that curve was shallower since I already new about files, directories, mice etc...
Burn the cd at 4x and you might have better luck. :)

---

### Post by PmDematagoda on 2007-10-12
What are the specs of your computer?

---

### Post by floke on 2007-10-12
If you state what exactly the problem is then we'll get you up and running, no sweat.

(1) Make sure your bios is set to boot from CD, and (2) select verify CD from the menu the first time the CD boots up to make sure it's a good burn.

If you don't let us know the exact details then we can't help.

---

### Post by PmDematagoda on 2007-10-12
> **floke said:**
> 

If you don't let us know the exact details then we can't help.

That is the problem with so many new Linux users, they tell us that Linux is not working for them, but they will not tell us why or what errors they face which makes it impossible for us to help them solve their problems, maybe they think that by putting dirt on Linux they can get it working.

---

### Post by Uncle Bunty on 2007-10-12
Thanks guys for the incredible response in such a short time. I am trying a burn at 7x which is the slowest my drive will burn. 

System is a Pentium 4, 2.8Ghz, 512MB, can't remember if it's a SATA or IDE 40GB (1 of my spare puters).

I thought I did articulate the problem fairly explicitly actually. I boot from CD, get to 6 or so options; boot from CD or install; boot in safe graphics mode; etc. then nothing. No hard drive activity, no CD activity, no sounds, no flashing lights, no joy.

---

### Post by Uncle Bunty on 2007-10-12
> **PmDematagoda said:**
> That is the problem with so many new Linux users, they tell us that Linux is not working for them, but they will not tell us why or what errors they face which makes it impossible for us to help them solve their problems, maybe they think that by putting dirt on Linux they can get it working.

This is exactly the point I'm making isn't it? I'm not trying to put dirt on Linux - I'm trying to USE it! The simple fact is, and the point I'm making is; you simply don't have these issues with a Windows installation. I don't need to go asking what is wrong to get it to work. If you chose to read the post instead of giving me your obviously unreasonably biased response about how the user is the problem not the product, you would maybe understand the point of me writing the post was to highlight the shortcomings that are obviously present in Ubuntu. I'm actually trying to help by giving feedback from a first time Linux human lab rat. if you weren't so bogged down in your insecurity you would see that as the other posters already have.

---

### Post by floke on 2007-10-12
(1) Select verify CD from menu to make sure you get a good burn (I get bad burns sometimes so it's not unusual).

(2) Also - the download may have been bad - I got a bad download of Mandriva a couple of days ago and had to re-download it.

(3) Before doing (2) try booting with some commands like acpl=off or noapic - there could be a problem with your power management (I've had this also).

(4) Don't give up. It took me several burns and install attempts before I got anything working the first time.

And what version of Linux are you trying to use?

---

### Post by Uncle Bunty on 2007-10-12
Haven't given up yet! Just finished burning the 7x so fingers crossed. 

Thanks again

PS Version is Ubuntu 7.04

---

### Post by Uncle Bunty on 2007-10-12
Progress report

There was an error starting the Gnome Daemon - apparently it's going to start next time?

---

### Post by PmDematagoda on 2007-10-12
I got the same thing as well, but after I installed Ubuntu this problem solved itself, so you won't have to worry much over that, you are getting that warning on the Live CD right?

---

### Post by Uncle Bunty on 2007-10-12
Is there a way to see behind this brown screen to find out what is happening?

Hard drive is clicking away furiously. Isn't this supposed to be a "Live CD"? Is it normal to take so long running from CD?

---

### Post by PmDematagoda on 2007-10-12
That is how Live CD's are as they work on the RAM, so if you have little RAM then it will take a lot of time, but even if you do have plenty of RAM it will take some time for the Live CD to finish starting up. Just be patient and you will be brought to the desktop without fail, just don't click around or you might prolong the Live CD bootup.

---

### Post by Uncle Bunty on 2007-10-12
Yes Live CD. I'm assuming it will fix itself at next boot. Seems to be taking forever but it's probably because I can't tell what is happening. Maybe I'll make that my priority - to improve feedback to the user during installation :)

---

### Post by Uncle Bunty on 2007-10-12
OK now I need to know if I'm on the desktop or not.

I see "Applications | Places | System" at top left but still a lot of clicking going on inside. Is it finished or do I wait for something else?

---

### Post by tact on 2007-10-12
> **Uncle Bunty said:**
> Yes Live CD. I'm assuming it will fix itself at next boot. Seems to be taking forever but it's probably because I can't tell what is happening. Maybe I'll make that my priority - to improve feedback to the user during installation :)

Mate - definitely booting from CD takes a long time.  CD drives are very slow compared to HDD.

Be warned also when you get to a desktop and start to click around and see if all your hardware is properly working, when you try looking at some of the files in the "examples" folder...  IT WILL BE SLOW to load and run...  its all loading off a CD.  Its Normal.  Sip a cuppa and dont let it get you.

Only when you are satisfied that all your hardware is working fine, sound, video, internet, etc..  then consider double clicking on the "install to HDD" icon.   Things do run a LOT faster when installed to the HDD.

Now - before you do that (install to HDD) can I prepare you for something else...  its not really easy for people who have never had to do many operating system installs.   

Like installing windows clean you have to make lots of technical decisions - like how to partition your hard disk...  what partition to instlal to etc.  Did I mention "just like windows"...  and "its not easy"  and "lots of technical decisions to make" and "just like windows".   (only different).  :)

If you want help people here are ever able and keen to help.

---

### Post by PmDematagoda on 2007-10-12
Just be patient, wait until all the activity ends, then start the installation. If you try to do something now you may end up making your Live CD freeze, so be patient:).

---

### Post by tact on 2007-10-12
yes wait a little longer.   as well as those menus you should end up with a folder on the desktop labelled something like "examples"...   and if you had windows installed you might see another icon looks like a HDD with a weird name like SDA1...    that will be your windows partition and if you click on it you can see all your files.....

I am going to dinner now.  Back in an hour or two - will check in here then.  see how you are going.

---

### Post by Uncle Bunty on 2007-10-12
Wonderful!

Clicking has stopped now and I can see the 3 menus at the top left and the Examples folder and an Install icon.

I have done literally thousands of Windows installs and (don't take this the wrong way) Ubuntu really needs to inform the user what is happening while the install is underway. In fact as soon as I get up to speed with this I will investigate improving this aspect. I really want a viable alternative to Windows for the masses and I'm hoping this could be it.

I'm gonna risk it and click somethin....'click'......no...please...no.....arrrghh....kaboom....aaaaeeeeiiiiii

---

### Post by PmDematagoda on 2007-10-12
Uh, Uncle Bunty:confused:? What is going on?

---

### Post by floke on 2007-10-12
It's still loading.
Live CDs are slow - and you have the bare minimum of RAM to run it on - so you will have a slow experience. For livecd you might want to try a different distro - eg xubuntu - though ubuntu itself will run fine when installed - its just the livecd ram issue.

---

### Post by floke on 2007-10-12
Intallation tells you exactly what is going on - this is a livecd, not an installation!

Don't install untill you have defragged Windows either - and read up on it first - don't jump in and then complain when you muck something up.

---

### Post by Uncle Bunty on 2007-10-12
Was a little hesitant to click anything but hey....you only live once right. I'm cruising around Ubuntu 7.04 now, albeit very slowly. It looks very much like an old version of Windows but it feels more like OS 9 on a Mac. I like the icons used in the system folders. Just having a look around the network to see if/how it works. So slow from CD but it is a risk free trial I guess cos I didn't actually install it (or pay for it). The GUI just needs to be brought into this century, it's trying but just doesn't have that eye candy thing happening. Masses like eye candy :) 

I'm very big on multi-tasking, eg., a dozen or so browser windows, an API or 2, and just other general stuff happening at the same time. Will Ubuntu handle this and if so, how well? I can't get an idea by running from the CD.

---

### Post by Uncle Bunty on 2007-10-12
I'm not installing Windows on that machine at all - just Ubuntu. Good to know the install lets you know what's going on but I'm assuming the only time this is run from Live CD is when a user is evaluating the product, therefore my comment seems valid considering that first impressions will most likely guide decisions on whether to use Ubuntu or not.

 I'm just looking at this objectively, from a first timer's point of view. It's all well and good to say well you gotta do this and that and the other but....we are all first timers when we are running this Live CD so it should leave a good impression/experience. it also should be intuitive to use and as much as I hate to say it, Windows is intuitive to use. Macs aren't. Depends on your background too I guess.....not knocking it..just thinking of areas where improvements could be useful. 

Anyone here do any actual development on Ubuntu?

---

### Post by Uncle Bunty on 2007-10-12
Another thought

can I format or partition a drive from Ubuntu or more specifically from the Live CD?

---

### Post by PmDematagoda on 2007-10-12
You can, but if you are partitioning a Windows drive then it would be better if you defragment the drive before partitioning.

---

### Post by Uncle Bunty on 2007-10-12
No Windows on this drive - hoping to keep it that way :)

Where do I find the formatting commands on the Live CD GUI? Will take me forever to find them at this pace :)

---

### Post by LaRoza on 2007-10-12
> **Uncle Bunty said:**
> Another thought

can I format or partition a drive from Ubuntu or more specifically from the Live CD?

Yes, but GParted LiveCD is best for that.

For Ubuntu's interface, many believe it gives a poor representation of what Ubuntu and Linux are capable of. Google "Beryl", "Compiz-Fusion", "Emerald" and such, and you will see that Linux is capable of supporing some flashy effects and themes. The brown of Ubuntu makes many people wonder, but that is only a default.

Also, you can get KDE, which is more Windowsy. There is a lot out there, and when starting out, it can be overwhelming.

Good luck!

---

### Post by PmDematagoda on 2007-10-12
> **Uncle Bunty said:**
> No Windows on this drive - hoping to keep it that way :)

Where do I find the formatting commands on the Live CD GUI? Will take me forever to find them at this pace :)

You can use Gparted, or the partitioner of the Linux installation itself, both of them worked for me.

---

### Post by FriedChips on 2007-10-12
Look under applications>system tools>partition editor/Gparted/or something it's in there

I really strongly urge you to set-up a dualboot system man. It is a very frustrating learning curve sometimes, and it's nice to have a fallback. I still have XP on my box even though I haven't booted into it in a month or more. I just always say to dual-boot cuz when you first start out you will want to use windows still sometimes. Until the time you get comfortable enough to do everything in linux.

---

### Post by Uncle Bunty on 2007-10-12
So I can format or partition the drive during the installation setup just like Windows XP?

---

### Post by LaRoza on 2007-10-12
> **Uncle Bunty said:**
> So I can format or partition the drive during the installation setup just like Windows XP?

No, it is easier and you get more format choices, not like XP: "Would you like ntfs or ntfs?".

You can have Ubuntu automatically partition and format, or you can do it manually. I usually use GParted to create the partitions then install.

---

### Post by tact on 2007-10-12
just like a windows install the partitioner is fired up when you begin the install.  unlike windows - its a nice graphical interface.    ;)

If you back off...  and download the v7.10 release candidate (v7.10 proper is released in a week) and install this instead of v7.04  - then v7.10 will install the compiz eyecandy for you by default if your graphics system is up to it.

---

### Post by kerry_s on 2007-10-12
512ram and your going for gnome and want speed, i don't think so.
from what you describe for the way you work you should go lighter.

xubuntu-> 
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)

better still debian, no live cd though->
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

debian is faster.

---

### Post by Uncle Bunty on 2007-10-12
> **kerry_s said:**
> 512ram and your going for gnome and want speed, i don't think so.
from what you describe for the way you work you should go lighter.

xubuntu-> 
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)

better still debian, no live cd though->
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

debian is faster.

I have loads of RAM lying about doing nothing so I'm happy to put a few sticks in, but are you saying that you don't think Ubuntu will handle the multi-tasking so well, or is it just a question of RAM. Vista needs about 1GB minimum anyway so it's still a level playing field. I'm really not so interested in the eye candy for myself, that was just first impressions from a mass market point of view. Keep in mind that this is entirely an experimental machine specifically to check out what I need to get away from the 5 copies of Vista I am using here at home. Anyone have experience with 64 bit Linux - recommendations?

This is good information because as I said I am brand new to Linux and have no idea which versions are light, heavy, pretty, whatever. Thanks guys.

---

### Post by PmDematagoda on 2007-10-12
If you are not going to use any eyecandy then you can use Ubuntu without much problems, but it would be recommended if you made your swap space atleast 512Mb because you will face problems if by any chance Linux runs out of memory due to the running of memory-intensive applications..

---

### Post by thecdn on 2007-10-12
> **PmDematagoda said:**
> but it would be recommended if you made your swap space atleast 512Mb because you will face problems if by any chance Linux runs out of memory due to the running of memory-intensive applications..

I've read that you should have double the amout of swap space as ram if you have less than 1gb ram, but that could be dated by now.

Uncle Bunty, I admire your sticking to it after some initial difficulties. It's not really harder, just different from what you are used to.

If you are curious to see what a faster livecd experience looks like, try out Wolvix or Zenwalk, Slackware based distros that use xfce as their desktop. They are nice for livecds.

I also agree with the person who suggested trying to install kde to see what that looks like. Or you could just install kubuntu as well. Depending on how big your hd is you can make multiple partitions and install many different distros to check them out. (I currently have 10 different distros and xp in a multi boot system). That would give you a chance to check out kde vs gnome vs xfce as well as debian vs rpm vs slackware based distros.

The amount of choice in linux these days is staggering :)  Take a look at distros such as PClinuxos, Mint, the new Mandriva One, Mepis, Vector, Pardus, the afore mentioned Wolvix and Pardus, etc. There is much goodness out there.

Note that not all distros have a combined live/install cd. Some have separate versions of each - Zenwalk and Vector come to mind. So make sure you download the right one depending on what you want to do with it.

---

### Post by wpshooter on 2007-10-12
Dear Uncle Bunty:

You are going to find out that installing and learning to use Ubuntu is a long drawn out process.  Ubuntu does not hold your hand like Windows does.  You are going to have to install and reinstall and reinstall, until you learn different things each step along the way.  I bet I have reinstalled the 4 machines I have at least dozens of times each.  Also, if you need to wipe out the machine and start over again I would suggest that you download and get familar with the Killdisk program at [www.killdisk.com](www.killdisk.com) , if you are not already familar with it.

I agree with you.  Ubuntu/linux has a long ways to go BUT I have been using it about 2 years now and believe me it has come a looooooooong way in that time.  But here is my big disappointment with Ubuntu and Linux.  It is their inability to run natively the same software applications that are available for windows based computers or more correctly the fact that the developers of these software applications have so far refused to write their applications for Linux.  And many Linux users will try to tell you that there are Linux substitutes for the windows based applications but believe me there are some BUT they do not hold a candle to the sofistication and feature sets of the windows based applications.

Also, once you get Ubuntu actually installed and running off the hard drive, you will find that you can do a lot more things and much faster than you can from the Live CD.  The live CD is not really a good/true reflection of Ubuntu's capabilities.  But if you have some more memory that you can put in that machine it would probably help you are good bit.  512 is probably the least you should try to run, 1024 is much better.

P. S. - One thing I forgot to mention is that you are going to really like the fact that you are not constantly having to worry about your Ubuntu/linux O/S getting hacked and bogged down with mal-ware, etc. and e-mail viruses like you did in Windows.

Good luck.

---

### Post by DDuong on 2007-10-12
Hi Uncle,

Learning Linux can be frustrating but after figuring out the problems the rewards comes afterwards.  "Patience" plays a huge part in this world (IMO).  I've been using Linux for about 3-4 years coming from Mandrake (aka Mandriva), Suse, Redhat/Fedora, and now Debian/Ubuntu.  After playing with those distros and going through all the frustration, I don't regret every bit of it.

Keep up the good work Uncle, I'm glad you are sticking to this instead of just "giving up".

---

### Post by Pumalite on 2007-10-12
Ahh...and one other thing: you'll never have to call anybody on the phone to ask for a 'key'

---

### Post by qamelian on 2007-10-12
> **Uncle Bunty said:**
> The simple fact is, and the point I'm making is; you simply don't have these issues with a Windows installation. 

After working in technical support for 20 years, I can tell you haven't done many Windows installations. I've seen exactly the same things happen on many Windows installs, including my home box, in which XP did not like the specific combination of hardware I had selected. XP would blue screen while attempting hardware detection during the install and the only way I could get around it was to replace my existing sound card with another one. The sound card that seemed to be the problem was perfectly fine, however, and is functioning perfectly in a second box...that is running Ubuntu.

---

### Post by phr0ze on 2007-10-12
Just click the install button, when you get to step 3 or 4 it will ask you about formatting/partitioning. Just choose 'Use Entire Disk'.  The installation is 7 steps and that one step is actually the most difficult. The other steps are such things like time zones, language, and your name.

While Ubuntu is installing you can still play around with it. There is no need to leave your computer for an hour.

---

### Post by wpshooter on 2007-10-12
> **phr0ze said:**
> Just click the install button, when you get to step 3 or 4 it will ask you about formatting/partitioning. Just choose 'Use Entire Disk'.  The installation is 7 steps and that one step is actually the most difficult. The other steps are such things like time zones, language, and your name.

While Ubuntu is installing you can still play around with it. There is no need to leave your computer for an hour.

I would suggest that you instead that you choose MANUAL formatting/partitioning.

And make SURE that you setup a SEPARATE **/home **partition and also a fairly large SWAP partition.

The partitions that you need are:

/ = root
/home = home
/swap = swap

---

### Post by Jive Turkey on 2007-10-12
When you get to the partition options I suggest the following (assuming you have a 40GB HDD).
/              (the "root" partition) 8-10GB max
/swap     (like the pagefile in windows)  ~equal to amount of memory or a bit more
/home     (Think "Documents and Settings") the rest of the space ~30GB

My 2cents, you wont want or need a FAT32 partition unless you are dual booting windows.

---

### Post by kerry_s on 2007-10-12
> **Uncle Bunty said:**
> I have loads of RAM lying about doing nothing so I'm happy to put a few sticks in, but are you saying that you don't think Ubuntu will handle the multi-tasking so well, or is it just a question of RAM. Vista needs about 1GB minimum anyway so it's still a level playing field. I'm really not so interested in the eye candy for myself, that was just first impressions from a mass market point of view. Keep in mind that this is entirely an experimental machine specifically to check out what I need to get away from the 5 copies of Vista I am using here at home. Anyone have experience with 64 bit Linux - recommendations?

This is good information because as I said I am brand new to Linux and have no idea which versions are light, heavy, pretty, whatever. Thanks guys.


it's speed and multi-tasking, but since your just messing around try them all so you can feel the difference. my machines only 450mhz 256ram, but i'm using a custom build up from debian, i do the base install than add what ever i want. i have mine setup to be light, no eye candy or frills, just does what i want done. i just did a clean install yesterday, so not much added yet. i mostly just have the browser and all the add ons.

---

### Post by thecdn on 2007-10-12
> **kerry_s said:**
> but i'm using a custom build up from debian, i do the base install than add what ever i want. i have mine setup to be light, no eye candy or frills,

Arch is great for that as well but may be kind of intimidating to a newbie until he's more comfortable with linux.

---

### Post by phr0ze on 2007-10-12
So can manual partitioning which I why I suggest keeping it simple and use the automated partitioning.

Besides, as the user advances, these partitions can be resized/split when the user is ready.

---

### Post by Uncle Bunty on 2007-10-12
Thanks for all the encouragement guys, I'm downloading the alternate CD and will spend the weekend learning about Ubuntu. I will also check out the many other flavours (correct spelling for Australia) of Linux that have been mentioned here.

I have to say that the most encouraging aspect of Ubuntu is definitely the support available in forums such as this. I have never seen such a useful and immediate response overall to issues raised by a newcomer. Thanks again guys, I expect you will see me around lots more, but hopefully I'll be answering some questions as well from here on :)

---

### Post by BobK on 2007-10-12
New user here too Uncle Bunty.  I played around with partitioning and installing maybe two or three times before I understood what was happening and I had a good installation.  I'm currently dual booting (Ubuntu 7.10 Beta & PCLinuxOS 2007) on a PIII450MHz with 327Meg of ram with NO problems.  Sure it is not the snappiest computer on the block but it is VERY functional.  Due to my old video card I do not have the latest eye-candy but, that's not for me anyway.  I had prior versions of Ubuntu and PCLinuxOS on that machine before updating to these versions, I'm ONE YEAR into my Linux journey and loving it.  I still have a windows box, no shame in that.  I did away with the s**t brown ubuntu 7.10 wallpaper and changed to a new theme and I'm super happy.  A buddy put PCLinuxOS on his 3.0 GHZ machine with 2 Gig ram last weekend.....talk about impressive!!!  He is trying Ubuntu 7.10 RC now, I'll talk to him tomorrow.  Someone told me "it's a journey".  Enjoy the ride.  These forums are GREAT for help!

---

### Post by Pumalite on 2007-10-12
Keep these two links in mind; the first as a guide and the second for troubleshooting:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by ubuntu27 on 2007-10-12
Hello Uncle. Welcome to the Ubuntu community Forum. 
Whenever you have question, concerns or problems, just open a new thread and tell us a bout it. We will be happy to help you out. Every one here is a user like you, no one is being paid to provide support-help in this forum. We are volunteers.


Now. There is a guide made by on of Ubuntuforums' member for those who are new to Ubuntu. I recommend you to read it.  [Ubuntu Guide]("http://www.psychocats.net/ubuntu/")

[Here is a guid]("http://www.psychocats.net/ubuntu/installing")e on how to install ubuntu using the Desktop CD [It contains ScreenShots so it is easy to follow]

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by perlluver on 2007-10-12
You can always try Kubuntu also.  I am running it and it looks basically like Vista, if that's what you are going for.  I am running it on an AMD 3400+, 1GB RAM, 128MB Nvidia Geforce Fx 5200.  I looked at the ubuntu desktop, and the xfce desktop, but the wife likes KDE.  If you would like screenshots, let me know.

---

### Post by Samhain13 on 2007-10-12
I just want to give some input on the multitasking thing.

I'm using an AMD Sempron 2400+ with 512MB RAM, and I think it's not too far removed from Uncle Bunty's specs. My video card is an Nvidia GeForce with 128MB, using a 1600x1200 screen resolution. I'm also using Feisty Fawn (7.04) with a lowlatency kernel (that I simply installed from Synaptic).

Here are the things I have running when I work (these are constant):

* Beryl (the eye candy with some waving desktop and wobbly windows)
* Firefox with more or less 4 tabs: 1 for previewing my work (web development), 1 for PhpMyAdmin (but not always), others for browsing sites like this forum.
* Gedit with at least 3 documents open. Usually a PHP file, an HTML file that I use as a template and 1 CSS file. (My working tab in Firefox gets constantly refreshed at this point as I preview what I save in Gedit) My Gedit also has the browser pane extension enabled so I can view my files.
* Gaim with three connections: Yahoo! Account, Ubuntu IRC (2 channels) and DalNet IRC (1 channel).
* of course, Apache2 and MySQL since they are started-up automatically in my machine.

Here are other things that I may choose to open at some point WHILE the above are also running:

* GIMP for editing the graphics that I need to insert in my work. When I start this, I usually leave it open in another workspace. (Yes, I'm using the cube too.)
* RhythmBox OR Totem for entertainment.
* Inkscape (occasionally), when I have to edit some vector graphics. This, I always close immediately after use.
* 1 or more terminals for seeding/leeching torrents. I've never had more than 3 active torrents though.
* Evolution (occasionally), for getting e-mail. Like Inkscape, I immediately close it after use.
* Opera, just so I can have another look at what I'm working on. I also close this immediately.

When I open the following applications, I need to close all the rest (except for Beryl, because I'm to lazy to change it):

* Cinelerra, usually with two audio and one video tracks active. It's no trouble editing but the rendering takes longer than I would like.
* Rosegarden. Experiencing occasional ticks when writing notes but playback isn't so bad.

Added notes on Beryl (and Compiz, since I tried that also for a couple of weeks):

Ok, the Beryl cube still animates smoothly via mouse or keyboard (smoother with keyboard) but when animated, there appear some rough edges on the window borders. It's tolerable though.

Using fire for mini/maximize, the animation sometimes skips when animating tall windows. But this doesn't happen often. Magic Lamp... it really looks ugly on my setup but tolerable under 1024x768.

Anyway...
I hope that gave a bit of perspective. :D

---

### Post by BLTicklemonster on 2007-10-12
> **kerry_s said:**
> 512ram and your going for gnome and want speed, i don't think so.
from what you describe for the way you work you should go lighter.

xubuntu-> 
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)

better still debian, no live cd though->
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

debian is faster.


??? What? I'm on an Athlon 2600+ with 512, and gnome is fast on my machine.

But icewm or fluxbox would do him well. Give him some stuff to play with while he's getting his feet wet.

---

### Post by RAV TUX on 2007-10-12
> **Uncle Bunty said:**
> Thanks for all the encouragement guys, I'm downloading the alternate CD and will spend the weekend learning about Ubuntu. I will also check out the many other flavours (correct spelling for Australia) of Linux that have been mentioned here.

I have to say that the most encouraging aspect of Ubuntu is definitely the support available in forums such as this. I have never seen such a useful and immediate response overall to issues raised by a newcomer. Thanks again guys, I expect you will see me around lots more, but hopefully I'll be answering some questions as well from here on :)

Welcome Unc. 

I suggest you try Xubuntu 7.10 Gutsy next, to get a beautiful desktop Environment(shell)...I also highly suggest "Enlightenment 17" CVS.
You can learn how to install Enlightenment 17 here:
[http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=11](http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=11)

Thanks be to [Rui Pais]("http://ubuntuforums.org/member.php?u=862").

E17 will satisfy you completely, and make Windows and Apple seem like yesterdays newspaper, ready for recycling. ;)

Again Welcome; to a wonderful ride that is far from boring corporate Spoon-Fed rations.

---

### Post by floke on 2007-10-13
> **RAV TUX said:**
>  Welcome; to a wonderful ride that is far from boring corporate Spoon-Fed rations.

+1

:guitar:

---

### Post by emshains on 2008-01-30
Who has a problem with liveCD and gnome ???

I was running a 500mhz 320mb machine in recent past.
Live cd booted for about 5min (from showing bootmenu to full installation) and it installed for 30 min.
Fully installed with added programs and some oldfashion games it takes just 2 minutes to fully boot it.
Of course it started to lag when running 3 progs or over 6-7 tabs in firefox but it was tolerable, probably thou because of my respect of it still running like an old granny beast

---

