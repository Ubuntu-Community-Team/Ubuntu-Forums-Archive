---
title: "partioning error during installation"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by jimmyln2004 on 2006-09-07
hi!

I have 40gb hardrive and i want to dual boot Windows XP and Ubuntu together. i have just gotten myself the iso of the alternate version of the Dapper Drake 6.06 release. 

While I was installing, everything was fine except the step on manual partitioning. 

Firstly, they reported my NTFS partition to be 40gb where GParted and QTparted and Windows recognized it as 37.2GB.

Secondly, when i tried to resize the NTFS partition, after typing the new drive size, nothing happens and it just reverts back to the "select a partion" menu.

Any help will be greatly appreciated.

---

### Post by Herman on 2006-09-07
Hello,jimmyln2004,
> have 40gb hardrive and i want to dual boot Windows XP and Ubuntu together. i have just gotten myself the iso of the alternate version of the Dapper Drake 6.06 release. 
While I was installing, everything was fine except the step on manual partitioning. 
Firstly, they reported my NTFS partition to be 40gb where GParted and QTparted and Windows recognized it as 37.2GB.:D Well, what are you upset about? :D You said it is a 40.0 GB hdd, and now you are surprised when the partitioner confirms this? Well, there are a few different kinds of GB, there are GB, or GiB, and there are the advertised GB of a hard disk and the actual GB of the disk too. [Online Bandwidth/data Calculator]("http://www.easycalculation.com/bandwidth-calculator.php") One GB is supposed to be 1024 MB, but hard disk manufacturers call 1000 Mb one GB most of the time. I wouldn't worry about that too much, I wouldn't lose any sleep over it anyway. :D> Secondly, when i tried to resize the NTFS partition, after typing the new drive size, nothing happens and it just reverts back to the "select a partion" menu. The 'alternate' installer won't do anything if it senses there is data in the way when it is asked to resize your old partition. You will probably just need to do a lot of defragging and then try again.
If you want to see how to defrag a little quicker, try reading [this link ]("http://www.geekgirls.com/windows_defrag.htm")and especially what it says in the illustrated how-to under "Step by Step, Efficient defragging", which begins about 2/3 of the way down towards the bottom of the page. It is very helpful. :D 
Regards, Herman :D

---

### Post by orb9220 on 2006-09-07
Defrag windows and then defrag again. That is what caused gpart to choke for me.

---

### Post by jimmyln2004 on 2006-09-08
ok, i will try to defrag now.

i know this is off topic, but what defragmenting software do you guys prefer?

---

### Post by Herman on 2006-09-08
>  i know this is off topic, but what defragmenting software do you guys prefer? I just use Windows XP or Windows 98's own defrag utility when I do mine, but I found the instructions in that link I already provided in an earlier post to be very helpful. It will get done much faster and better that way.

That web-page also suggests something called 'Power Defrag', but I don't know anything about that, I have never tried it. 

If you are in a hurry, the fastest way to partition your disk is to use the latest GParted LiveCD, it will move all  your FAT32 or NTFS files out of the way for you, you don't have to bother defragging first. It is quite safe, I have used it hundreds of times, ever since version Alpha3,  0.0.9-  

However, if you want peak performance from Windows, I still think Windows' own utility should be the best for Windows, probably. 
It just takes a long time, so you have to be patient. Or let it run overnight and wake up from time to time and re-run it until it finally gets the job done sufficiently. 

Regards, Herman :D

---

### Post by jimmyln2004 on 2006-09-09
after some searching, i decided to use dirms(do-it-right-microsoft) to defragment the drive.

dirms was really fast -- reduced my files defragementation rate form 1.23% to 0.2% in 2 hours!

anyway, i have successfully resized and partitioned the drive. it is gonna take a while for ubuntu to install

anyway, thanks Herman and orb9220! :P

EDIT: I've met another problem! I was away for a while, and when i came back to check on the pc, i saw a black screen with only 2 tiny grey bars. What happened?

Somebody please reply ASAP, i really in a rush now!

EDIT 2: After a while, suddenly, the cd tray just ejected. I thought that the installation should be complete, so i took out the cd waited. The system did not do anything, and on my display was still the 2 short bars. So, I press the force restart button and now, the computer get stucked the moment i on. I think that the system did not even pass the POST test. somebody please help me!

---

### Post by Herman on 2006-09-09
If you have a Live CD of any kind, try restarting your computer with the Live CD in the drive and see what happens. If it isn't a hardware failure of some kind, your Live CD should boot up and run normally.

If it does run alright, then open a terminal and do 'sudo fdisk -lu' ```
sudo fdisk -lu
``` and see what fdisk tells us about your hard disk.

if you computer will not run a Live CD, then you will need to begin testing your hardware to see what faults there might be. A hardware failure can happen any time regardless of what you happen to be doing  the time. If it isn't  POSTing then you should be getting a beep code that you can use to give you a clue as to what's wrong. You might need to go to the website of your motherboard manufacturer, or look up your BIOS's beep codes on the internet. 
Begin with the simplest things first, like unplugging and replugging things like keyboard, mouse, monitor, etc. It might turn out to be something really simple. 
I'll wait to hear from you before I continue. 
Regards, Herman :D

---

### Post by jimmyln2004 on 2006-09-09
i unplugged all the wires and stuff, such as monitors, keyboards, speakers, etc. and plugged it back. Voila! It booted!

I do not have the slightest idea what has happened, but who cares, it works now! By the way, do you have any ideas why the screen turned black during the installation?

---

### Post by Herman on 2006-09-09
I have no idea really. Perhaps you should watch it while the installer is running and see what happens. Did you leave it for a really long time? Maybe it was asking you some question and waiting for you to select an answer and it just kind of 'timed out'. 

Otherwise, there could be something overheating or something like that in your hardware, or a loose connection, or anything like that.
You could try going into your BIOS and looking at the 'system health check', if your BIOS has one. To see what I'm talking about, look at the bottom of this page, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").  There should be somewhere in your BIOS where you can look to see temperatures and voltages and that sort of thing.  Just see if everything looks okay there maybe. It could have been a fluctuation in your power supply. Maybe it's something that will never happen again. Or maybe it's an early sign of some maintenance you'll need to do sometime soon. 

Often just a good cleaning and re-seating of various computer parts will get even an old broken down computer working like new again. (I do not mean to imply that yours is like that though). On any computer a liitle 'TLC' can work wonders. Your computer repair man is generally the best person to perform maintenance like cleaning and re-seating parts inside your machine. (If it needs that). Unless you have the right tools and training. 

I'd just watch it and give it some time and see if it happens again. ('Monitor the situation') (Pardon the pun) :D

Regards, Herman :D

---

