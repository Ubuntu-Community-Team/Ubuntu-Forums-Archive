---
title: "I Need Advice Before Beginning My First Foray Into Linux (sort of complicated)"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2010-07-03
My first foray into the Linux world might begin this weekend if all goes  well. This isn't terribly complicated but I know I have several steps  to handle before I get started. Somebody familiar with hardware as well  as software needs to help me out on this one. I have no knowledge of  command line stuff but I know it exists and I'll need to do some of it.  If the commands are typed correctly in instructions I can duplicate them  to the letter. 

This is my situation. I have an 11 month old HP Pavilion with an AMD  Sempron chip and NVIDIA graphics card. It has Vista and last week Vista  got a virus, no thanks to the AVG free anti-virus program. I downloaded  Bit Defender and it has deleted the viruses and the computer works  except for the browsers. None of them will connect to the internet. The  e-mail will still send and receive messages and the printer works, just  no browsers. Since I don't know how to fix that problem (HP doesn't  either) I'll need to restore Vista. I can either use the OS partition or  create some recovery discs and use them. 

((((( [COLOR="Red"]This section was answered YES.[/COLOR] [COLOR=Blue]OK, somewhere in that discovering the virus problem I  was able to use the browsers temporarily before they stopped working.  That is when I downloaded Bit Defender. The second Bit Defender scan  deleted the viruses that weren't handled on the first scan. That is when  the browsers stopped working for good.[/COLOR]

I need to store my files before wiping the drive. Here is the first part  I don't know about; I have a Mac that uses an external hard drive. This  hard drive can also be used by Vista because I installed a program  called Mac Drive 7 which somehow allows Windows computers to communicate  with Mac hard drives. After Vista is reinstalled can those files on the  external hard drive also be read by Linux? If so then that is the end  of that. If not, how should I store the files on the Vista computer so  that they can be read by Ubuntu 10.04? I know the program files won't  work on Ubuntu but the text, PDF, audio, and video files will need to be  transferred to Ubuntu once it is working. 

[COLOR=Blue]Can Ubuntu read files stored by my Mac on that hard  drive too? If so, that would save me a lot of time transferring the  files elsewhere so they could later be put into Ubuntu. I don't expect  the Time Machine files to be readable. That is probably a different  situation. [/COLOR])))))

((((( [COLOR="Red"]Nobody answered this one so I went ahead. I used the internal partition and everything is OK[/COLOR]. HP technical support said that I shouldn't save any files that end in  .exe or any Word/text/OpenOffice/PDF files because they contain  executable code that could be infected despite the full  anti-virus/malware scan done by Bit Defender. Is this true or can I  trust that Bit Defender succeeded in removing all traces of the viruses?  HP technical support said audio and video files should be OK to save. 

They also said that creating recovery discs is risky because the virus  might have been smart enough to penetrate the OS partition and the  problem will continue in the future. They said I need to get recovery  discs that weren't made on this machine. What do you think?)))))

I know that fixing the HP Vista machine must be done first. I want to  dual boot it because I want to continue watching streaming movies from  Netflix and the Starz live stream. I also want to use iTunes because I  intend to buy an iPad in the future. Once Ubuntu is working fine I  intend to sell my Mac Book and stop drinking the Apple Kool-Aid (well  maybe I'll just have a little every once in a while). 

((((( [COLOR="Red"]Though I've already burned the discs using the Vista computer I'd like an answer to this one.[/COLOR] Next thing; can I burn Ubuntu ISO discs using my Mac and then put them  into the Vista HP machine? I don't know how to do that. In the Ubuntu  Pocket Guide it explains how to do it on a Windows machine. It even  explains how to set up the disc burning (or is it downloading) to the  slowest speed in order to ensure no data is lost. )))))

That's it for now. These questions need to be answered before I go on. 

Here's what I want to do today (or whenever these first questions are  answered);

[LIST=1]
[*]Back-up the Vista files some way ([COLOR="Red"]Done[/COLOR])
[*]Create Recovery Discs ([COLOR="Red"]Done[/COLOR])
[*]Restore Vista. ([COLOR="Red"]Almost Done. I'm reloading programs, drivers, settings, and defragmenting it 7/5/2010[/COLOR])
[/LIST]
 Once those things are done I'll then either create the ISO discs on the  Vista computer or the Mac. After that is done I'll follow the  installation instructions in the Ubuntu Pocket Guide. Then I'll ask more  questions whether things go well or not. Remember I'm not familiar with  doing any of the things above other than backing up data. Everything  else is new to me. 

If there are some steps I'm leaving out please inform me about them. 

Thank you for your assistance. I'm looking forward to enjoying Ubuntu.  With compiz creating a really cool desktop environment, I'll have all  the features I love about the Leopard OS. Most of what I do is basic web  browsing with some video creation using my Flip camera. I also create  text documents often using Open Office software. Perhaps in time I'll  learn enough about Ubuntu that I won't need to vist the Windows world  very often. If Netflix starts allowing Firefox to utilize its HTML 5  streams that it prepares for the iPad and iPhone I'll rarely need to use  Vista. That will be a relief.

Michael J. Beninate

---

### Post by darkod on 2010-07-03
I haven't used a Mac so I don't know if it can burn standard ISO to a cd. I guess it should. Just set low speed, for example 4x, and try to create a cd from the ubuntu ISO.

With that cd you can boot your PC into ubuntu live mode (Try Ubuntu option), which will run it from the cd. You can connect your ext hdd and check that way whether it will be recognized. Ubuntu can recognize file formats used by Mac so I think it can work.

You are right, if it can recognize the ext hdd that would be the best way to backup, trough ubuntu live mode. It also means you can put the files back without any problem from ubuntu too.

So these would be the first things to try out. As far as which files to back up, only you can answer that question. Yes, it is safer to exclude any .exe files, if you don't have any important .exe files you want to keep.

---

### Post by efflandt on 2010-07-03
Unfortunately many computers (including HP) do not come with recovery disks.  So in hindsight, the first thing you should have done when you got the computer should have been to create the utility and recovery disks.

I have a friend who got her WinXP laptop totally infected with several worms or viruses (probably beginning with a bogus search engine that planted other things).  One of them (scareware) was so invasive is got into the browsers, disabled Task Manager, changed the background image to a fake virus warning, and disabled Safe Boot or any sort of recovery.

I cannot tell you how to burn an Ubuntu CD with a Mac, or if you know any other PC you can use.  But I ended up booting an Ubuntu CD on the infected laptop, copied directories and files from the user's Windows home dir to a dir on a USB drive, then virus scanned the USB drive from another computer.  It found and removed several virus remnants from temp files.  Since I had gotten the user a new laptop, I made sure that anti-virus software was installed first, then just copied over the files they needed from My Documents and imported data files and address from Outlook Express into Microsoft Live Mail.

I inherited the infected laptop, reinstalled WinXP from scratch using the recovery disks written when it was new (12 CD's since the Compaq did not have DVD writer), and left room for Ubuntu on the drive.  The old laptop had some problems with 9.10, but 10.04 works fine.

---

### Post by someEEguy on 2010-07-03
> **Smallwheels said:**
> 
This is my situation. I have an 11 month old HP Pavilion with an AMD  Sempron chip and NVIDIA graphics card. It has Vista and last week Vista  got a virus, no thanks to the AVG free anti-virus program. I downloaded  Bit Defender and it has deleted the viruses and the computer works  except for the browsers. None of them will connect to the internet. The  e-mail will still send and receive messages and the printer works, just  no browsers. Since I don't know how to fix that problem (HP doesn't  either) I'll need to restore Vista. I can either use the OS partition or  create some recovery discs and use them.
Is this the virus you got, if so step 2 will fix Internet Explorer. The virus turns on the "use a proxy server for your LAN" option in IE, as a cruel joke.

[http://deletemalware.blogspot.com/2010/04/how-to-remove-antivirus-suite-fake.html](http://deletemalware.blogspot.com/2010/04/how-to-remove-antivirus-suite-fake.html)

---

### Post by Smallwheels on 2010-07-03
I did get that virus while downloading an episode of Leverage at one of the ydio.com links. This is the first virus I've gotten in eight years. 

I did a system restore to a point a few days before the problem happened. Bit Defender is no longer on the computer but the log files are. That's weird (it's Vista). Thanks to the information on that site you linked to I just reset IE to its default settings and it works fine now. I suppose I could skip reinstalling Vista from the recovery discs now. On the other hand, if I do a fresh install all the files will be in a tight little group and I won't need to defragment the computer. That is one of the setup steps in the Ubuntu Pocket Guide.

I still need answers to the other questions though. Maybe by tomorrow enough of the people who know the answers will see this thread and give me a clue. 

Michael J. Beninate

---

### Post by wookieshaver on 2010-07-04
Well, you do seem in a bit of a pickle. The first thing you should do is create the Vista Restore Discs for your computer using the HP Backup and Recovery manager. Instructions on that are here: 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00882383&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00882383&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)
 
You'll be able to restore your HP vista machine with the discs. Alternately, you can access the Recovery Partition by usuing F11 on the boot of your machine and running restore that way.
 
Incidentally, OpenOffice and other Linux apps should have no problem at all reading your backed up documents, pictures, pdf's, music, and video. This is true whether you use NTFS or FAT32 as the file system for your backup drive. Ubuntu reads these all very well. 
 
You can download and burn an ISO in mac OS. Here is the shorthand for that (assuming you already have the downloaded ISO on your mac):
 
[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)
 
As far as backing up your data, which you should do before you do the restore of your Vista, backup all the files you want and need. You can scan them before accessing them again after your pc is newly protected. AVG is pretty good for Windows but I like Avira if I am picking a free antivirus. 
 
Best of luck!

---

### Post by Smallwheels on 2010-07-04
I've run into a problem. I downloaded the InfraRecorder for the purpose of burning the ISO file to a disc. When I ran the program I had the opportunity to choose a write speed of 3.5 times. When I started the process I got an error message saying that the speed test was skipped. Then while the disc was being written it said the write speed was 9 X. Now I'm concerned that data might have been lost or corrupted. I used a DVD for the process. 

Do you think this disc will work or will there be a problem with it?

I first tried the ISO Recorder but couldn't find a way to get it to open, so I deleted it and went with the InfraRecorder. Does anybody know how to get InfraRecorder to write the disc at 3.5 X? I don't have an unlimited supply of blank DVDs to experiment with this.

Michael J. Beninate

---

### Post by wookieshaver on 2010-07-04
The disc would very likely work if it was a dvd iso image you downloaded. I always burn my dvd's and cd's that I have used for Ubuntu and other Linux distributions at the default highest speed on my machines. More often than not the bad burn is caused by the source you downloaded from - they won't always download perfectly. 
 
That said as long you downloaded an image that was a dvd image - say from here:
 
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/10.04/release/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/10.04/release/)
 
rather than just clicking "Start Download" on this page:
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
you would be ok. The second link is for cd iso rather than a dvd iso. It's the formatting that would confuse the pc trying to read it when you are done that would be the issue.

---

### Post by Smallwheels on 2010-07-04
Thank you for your assistance. I decided to try using the DVD as a live CD. It's working in some respects. I can view the web from it using Firefox. I can't view video content due to no drivers. I've viewed all of the things in the Example folder and I don't know if there is anything else I can do with it. Is there?

It does recognize the things on my HP computer but it can't access them. There is a file entitled HP. It has all of my major file names in it (Documents, Music, Pictures, etc.) but they are all empty. 

I plugged in my external hard drive and Ubuntu recognized it. I opened many picture files and they worked. So did some text files. It didn't have the ability to play music files or video files that were wmp files. It gave me a message that I needed a certain plug-in. When it searched for it there were no packages available in the results. It said I need the Advanced Streaming Format (ASF) demuxer. I suppose those are things I've never heard of because they deal with Linux. That was with the movie player. I tried getting Rhythmbox to open wmp music files and it wouldn't import them.

The text files in Open Office opened very quickly compared to files on my Mac and Vista systems. Even though the Open Office software was run via the DVD. 

What else can I do using the Ubuntu CD other than visit the web on Firefox or view the flies on the disc? If I can't connect to many things due to just using the Live CD then I suppose I must install it to get to the next level. It would be great if I could buy a thumb drive and have my entire OS and data on it. I could carry my computer around with me in my pocket. All I'd need to do is plug in to someone else's hardware. 

Is there an online tutorial for Ubuntu that can teach me how to operate it? There weren't any for Leopard and I didn't bother to look for one when I was using Windows XP.

Michael J. Beninate

---

### Post by wookieshaver on 2010-07-05
The live cd/dvd is a sneak peak at Ubuntu. Basic functions like web surfing and writing documents are really about the limit of use apart from, say, trying to get data off a bad windows hard drive (which I have found it useful for). The best functionality you will find with a full install. This allows for an install of codecs and plugins to watch movies and listen to mp3's and have an office program or other programs on the hard drive and not operating just in ram. 

Ubuntu forums are a good place to get incidental help here and there. I also find the Ubuntu documentation pretty good! You can find it here for the latest release:

[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

That said, welcome to Ubuntu town. Take the plunge and install! You will have fun or go insane in a few days, either way you will be different for having tried it!

---

### Post by oldos2er on 2010-07-05
> **Smallwheels said:**
> Is there an online tutorial for Ubuntu that can teach me how to operate it? 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by wookieshaver on 2010-07-06
Re:[COLOR=#ff0000]Though I've already burned the discs using the Vista computer I'd like an answer to this one.[/COLOR] Next thing; can I burn Ubuntu ISO discs using my Mac and then put them into the Vista HP machine? 
 
Mac OS is certainly capable of burning ISO format. There are free apps available like this one (LiquidCD): 
 
[http://www.maconnect.ch/](http://www.maconnect.ch/)
 
 
Re:[COLOR=#0000ff]Can Ubuntu read files stored by my Mac on that hard drive too? If so, that would save me a lot of time transferring the files elsewhere so they could later be put into Ubuntu. I don't expect the Time Machine files to be readable. That is probably a different situation.[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]You certainly can read files on your mac using Ubuntu! Check this guide out:[/COLOR]
 
[http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

---

### Post by Smallwheels on 2010-07-06
Good News! It's installed. This whole process took a really long time due to the time needed to backup and reload my Vista files. Burning the ISO disc took a long time too. 

At the end of the setup it asked me to restart the computer for all the changes to take effect. When I did there was an error message and a gigantic litany of lines repeating the same error only with different numbers at the end. I have no idea what they mean. Here is what was on the screen:

[ 6324 . 635578 ] end_request: I/O error, dev sr0, sector 506312

As I said, that repeated over and over with just the last number changed for each line. The numbers were almost sequential.  I had to turn off the computer using the power button. When it restarted I entered my password and the desktop appeared. Soon afterward a message opened about updates. I loaded them and that took nearly two hours. 

I haven't used the computer yet to see what works and I haven't had time to read those helpful manuals either. Until I know what I'm doing I won't really know if something isn't working properly. 

I'm typing this from my Mac. Maybe in a day or two I'll have Ubuntu configured so that I can use it.

Should I be concerned about that error message? I was able to shut down the computer from the desktop after those updates were installed.

Thanks for the help. I'm sure I'll be asking a ton of questions in the future. 


Michael J. Beninate
[www.MySpace.com/Beninate](www.MySpace.com/Beninate)

---

### Post by wookieshaver on 2010-07-06
That error message is more than likely the shutdown sequence of Ubuntu failing to match up exactly withe ACPI or power management of your machine. Not all that weird on first shutdown just make sure you run your updates upon first boot!

---

### Post by Smallwheels on 2010-07-06
I needed to get to a file so it could be sent to someone. I tried to access Vista and couldn't. 

At the start I clicked the esc key until I had the chance to choose an OS. Before I just though one of those other choices was for loading Vista. It turns out they aren't. Here is what is written on the opening page:

I selected Windows Vista (loader) (on/dev/sda2)

Next the black screen changed to the words Windows is loading and there was a progress bar on the bottom of the screen.

There was a very brief view of the normal Vista loading progress bar and it disappeared. A blue screen opened and stayed for a while. An old style Windows dialog box opened that said Systems Recovery Options. There was just one thing to check and it was Choose a recovery tool.

The list on the next dialogue was: Startup Repair, System Restore, Windows Complete PC Restore, Windows Memory Diagnostic, Command Prompt, Recovery Manager.

I selected Startup Repair. A progress bar opened and took a few minutes to finish. After this happened I clicked finish and it restarted the computer with no change. 

I shut down the computer again after going to Ubuntu. On the next startup I didn't select anything after pressing the esc key so I could write down my choices in case someone here could tell me what they mean. When I was finished writing them I tried to select one and none of the keyboard keys worked. The arrows or enter keys had no effect. I shut it down with the power button. 

Here were my choices at the startup after pressing Esc. 

> HDD Group
               T332 0813AS
>CD ROM Group
               TSSTcorp CDDVDW TS-H653R

Before I would select the second one because it took me to Ubuntu. When it would open it would give me many choices of Ubuntu related to recovery or other things. I just selected the one that didn't seem like it was for repair. The last two were for Vista but I didn't even pay attention to them before today. I just assumed they were for loading Vista. One is for recovery and the other was for some other type of diagnostic. Neither opens Vista. 

I need to get to Vista for that file and so I can use a web site that doesn't work with Firefox, or Safari. 

What can I do?

By the way when I was in Ubuntu during this set of problems I tried using Firefox to go to a site. It was so slow in getting to it I felt it might be the fault of the site. Then I went to two known sites (yahoo.com and apple.com). Both took almost a minute for Firefox to get to them. I can't use Ubuntu if that can't be fixed. While at the Apple site I typed in the yahoo address and hit enter then the blue arrow. At the bottom of the screen the status bar kept showing more and more things loading on the Apple site. It was as if the browser didn't get the information from the address bar after I clicked enter. Eventually it did switch to the yahoo site. That is unacceptable. I know that can't be normal behavior. I'll need to get help with that later.

Michael J. Beninate

---

### Post by Smallwheels on 2011-03-24
March 24, 2011. Ubuntu is working. As of today I haven't posted on many threads. Anybody having installation problems as a new to Ubuntu person should search for Smallwheels and just read of my experiences. 

With help I got Vista and Ubuntu dual booted. 

I found drivers to make the video players work.

I got the mail program working though it almost never gets used.

All of my browsers work now but not all are doing well. I still haven't found a way to get Opera to play Quicktime videos. With the release of Firefox 4 I finally got a way to update it and get it working at a normal speed.

Chrome can't successfully synchronize my bookmarks across different computers. Perhaps the new Firefox 4 can succeed at this.

I found something in the Software Center that got my HP printer and scanner working.

Skype audio is now working. Go into Skype controls and turn the audio to just one channel (I don't recall if it is right or left). Then the audio will work. You might need to search for that one because I don't recall posting in any threads about getting Skype to work. 

This was started July 3, 2010 and is nearly finished. Ubuntu isn't perfect but it is working and it is free. Had I stuck with it on a daily basis this computer might have been working with full functionality within a few weeks instead of so many months. 

Thanks Ubuntu community

Michael J. Beninate

---

