---
title: "Ubuntu 10.04 installation issues"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by gamesnepal on 2010-04-30
Hi,

I downloaded the latest ubuntu and then installed this new operating system inside my windows. After the installation is completed 100%, I get this message:

```
An error occured:
Permission denied
For more information, please see the log c:\docume~1\[username]\locals~1\temp\wubi-10.04-rev189.log
```

When I check the log, I find out the following error messages in the bottom of the log file

> 04-30 13:36 DEBUG  TaskList: ### Finished copy_file
04-30 13:36 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-30 13:36 DEBUG  TaskList: # Cancelling tasklist
04-30 13:36 DEBUG  TaskList: New task check_iso
04-30 13:36 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-30 13:36 DEBUG  CommonBackend: Searching for local ISO
04-30 13:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-30 13:36 DEBUG  TaskList: New task get_metalink
04-30 13:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-30 13:36 DEBUG  TaskList: # Cancelling tasklist
04-30 13:36 DEBUG  TaskList: # Finished tasklist

I could install Ubuntu 9.04 perfectly this way. But what is wrong this time

please help me out

---

### Post by gamesnepal on 2010-05-01
I tried the installation on my laptop as well and I get a similar error message. Is my installation CD broken or something?

```
05-01 13:44 DEBUG  TaskList: ### Finished copy_file
05-01 13:44 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-01 13:44 DEBUG  TaskList: # Cancelling tasklist
05-01 13:44 DEBUG  TaskList: New task check_iso
05-01 13:44 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-01 13:44 DEBUG  CommonBackend: Searching for local ISO
05-01 13:44 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-01 13:44 DEBUG  TaskList: New task get_metalink
05-01 13:44 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-01 13:44 DEBUG  TaskList: # Cancelling tasklist
05-01 13:44 DEBUG  TaskList: # Finished tasklist
```

---

### Post by isaiasmy on 2010-05-04
I have the same problem in ubuntu or kubuntu

---

### Post by fidamehran on 2010-05-10
Same problem here. Windows 7 doesn't play well with Ubuntu, I guess.
Any advice, Ubuntu Gurus?

---

### Post by strat1227 on 2010-05-21
It'd be really nice if someone replied, this seems to be a common error, I'm getting it too.

---

### Post by darkod on 2010-05-21
First, IMHO, install ubuntu properly, on its own partition, the way it's supposed to work.
You didn't install windows inside another OS right? Why installing ubuntu inside windows?

If you have questions about that procedure, we're here to help.

As for the permissions error, the only idea on my mind is some complication with the windows security blabla. When activating the wubi.exe file, instead of double click, right-click it and select Run as Administrator. If that doesn't work, I have no other idea.

---

### Post by strat1227 on 2010-05-21
I've always used wubi for its ease of installation and lack of any risk. Unfortunately this is my only machine and I can't risk losing my Windows partition, but I need Ubuntu for my work :/

The wubi page links here for help, so I just assumed you guys would help, sorry

---

### Post by darkod on 2010-05-21
> **strat1227 said:**
> I've always used wubi for its ease of installation and lack of any risk. Unfortunately this is my only machine and I can't risk losing my Windows partition, but I need Ubuntu for my work :/

The wubi page links here for help, so I just assumed you guys would help, sorry

We do, but not all of us use it. For example, I have never installed wubi. It would need patience for the right person to see the thread.

Plus, the thread type is wrong, it says [ubuntu] and the question is about [wubi]. It helps for right people spotting it.

As for the risk, installing ubuntu on its own partition is not risky at all. Of course you need to follow some basic steps, and that it.

The main remark I have on ubuntu is this: they have tried too far to make the installer user friendly especially for people new to linux that are usually nervous what will happen to their windows. Offering the side-by-side option is nice, but it can lead to problems because windows wants to be the boss and doesn't like other programs resizing its system partition.

Resize your win7 system partition using Disk Management, leave the newly created space as unallocated. Boot win7 few times to do its disk checks. Boot the ubuntu cd and select the Use Largest Available Free space option. That will install into the unallocated space. Or use manual partitioning option if preferred.

Your windows is perfectly safe. Of course, it doesn't hurt having a backup. Even if running only windows you should always have backup.

---

### Post by strat1227 on 2010-05-21
I'm sorry but to say there's no risk is just misleading. Yes you just have to follow steps, but to mess up even one small step can ruin your computer (I've ruined one before, which is why I use wubi now).

And as far as the thread title, should I go make another thread? I didn't make this one, I doubt that guy will check back any time soon to edit his title.

---

### Post by darkod on 2010-05-21
> **strat1227 said:**
> I'm sorry but to say there's no risk is just misleading. Yes you just have to follow steps, but to mess up even one small step can ruin your computer (I've ruined one before, which is why I use wubi now).

My point was that there is no more risk than installing any other OS. Of course there is risk installing an OS. But even when installing windows if you select a wrong partition you'll mess things up, right?

Sorry to hear you ruined one computer, but that shouldn't shake your confidence. :) The approach I suggested above is the best IMHO to minimize risk. First shrink using windows tools, then install into the unallocated space.

> And as far as the thread title, should I go make another thread? I didn't make this one, I doubt that guy will check back any time soon to edit his title.

It's up to you. Sometimes it really helps for someone who knows more about wubi spotting it.

---

### Post by michopop on 2010-05-31
ok. i have the same problem. and your discussion didn't help me a lot. can someone now look for a solution how to install 10.04 with wubi? (and not another way)? thx

---

### Post by navalmundada on 2010-06-01
hi
i also have similar issue

06-01 11:13 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-01 11:13 DEBUG  TaskList: # Cancelling tasklist
06-01 11:13 DEBUG  TaskList: New task check_iso
06-01 11:13 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):


I tried running wubi as administrator but no success

I also tried installing ubuntu by booting it from CD.  But i m getting blue Ubuntu screen and it stops there only way is restart my laptop.

I am using Windows 7 Home basic and dell 1464 laptop.
Can somebody suggest a solution...

---

### Post by darkod on 2010-06-01
> **navalmundada said:**
> hi
i also have similar issue

06-01 11:13 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-01 11:13 DEBUG  TaskList: # Cancelling tasklist
06-01 11:13 DEBUG  TaskList: New task check_iso
06-01 11:13 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):


I tried running wubi as administrator but no success

I also tried installing ubuntu by booting it from CD.  But i m getting blue Ubuntu screen and it stops there only way is restart my laptop.

I am using Windows 7 Home basic and dell 1464 laptop.
Can somebody suggest a solution...

Depending what solution are you talking about. I can't advise anything about wubi, I don't use it. Besides, part of the problems coming with wubi is because you are sort of trying to install OS inside an OS. Do you think windows easily allows that? There are too many things that can go wrong.

As for installing a full ubuntu. Try to run the cd first in live mode, to see if it will load successfully. When the first purple splash shows, press any key to get a menu. From that menu there should be option Try Ubuntu. If it doesn't load, restart and try the same but this time before selecting Try Ubuntu hit F6 for advanced options and select Safe Graphics. Only after that Try Ubuntu.
If that works, that means there is issue with the video driver.

---

### Post by navalmundada on 2010-06-03
Thanks Darko...
I tried both of the options but nothing works out...
When i tried Ubuntu from Live mode(boot from Cd) it gave me purple Ubuntu screen with the options like Try Ubuntu, Install Ubuntu,...  When i selected Try ubuntu, this got struck and nothing goes next. Then i tried Install ubuntu but same screen no further options. 

By pressing F6, while restarted, i got only option of Windows 7.

Please help if u know any other way of installing.

Regards,
Naval
Pune, India

---

### Post by varunendra on 2010-06-03
> **fidamehran said:**
> Same problem here. Windows 7 doesn't play well with Ubuntu, I guess.
Follow this thread:> [http://ubuntuforums.org/showthread.php?t=1498681](http://ubuntuforums.org/showthread.php?t=1498681)(go through entire thread to get a better idea)
If that kind of guy can install Ubuntu 10.04 (through WUBI 10.04) within Win7, then it is imperative to say that it can't be a compatibility issue with Win7.

> **darkod said:**
> First, IMHO, install ubuntu properly, on its own partition, the way it's supposed to work.
You didn't install windows inside another OS right? Why installing ubuntu inside windows?Guys are just trying to play safe, & Ubuntu is humble & capable enough to let them. So it's fine!

> Plus, the thread type is wrong, it says [ubuntu] and the question is about [wubi]. It helps for right people spotting it.Admins can move it for them if we report it. I just did it.
PS: My bad! I guessed there would be a separate section for [WUBI] where this thread could be moved. Just figured out I was wrong.

> Of course, it doesn't hurt having a backup. Even if running only windows you should always have backup.He means saving the partition image. Make sure to take images of both boot-partition & the partition where Win7 is installed. Also, boot-partition image should contain MBR. Norton Ghost, PartImage, Clonezilla, .... all do the job just fine.

> Do you think windows easily allows that? There are too many things that can go wrong.Think again. If installing through WUBI can be problematic, the proper setup may be even more risky, especially when the guy loves to stick with his Windows installation. WUBI is relatively safer- that's it!
(Of course the user should consider making a proper install once he gets used to it & becomes capable to figure out things).

> From that menu there should be option Try Ubuntu. If it doesn't load, restart and try the same **but this time before selecting Try Ubuntu hit F6 for advanced options and select Safe Graphics. Only after that Try Ubuntu**.
If that works, that means there is issue with the video driver.Good point!

> **navalmundada said:**
> By pressing F6, while restarted, i got only option of Windows 7.I think you didn't get darkod right..... Sounds like you tried f6 the way you do with f8 in windows - to boot into safe mode - while booting. Read the boldened lines of the above quote.

You said you got the menu with options "Try Ubuntu, Install Ubuntu,...etc." in your first attempt. You have to press f6 only after getting this menu. After pressing f6, click on 'Try Ubuntu' & then choose 'Safe Graphics'.
It **should** work.

---

### Post by navalmundada on 2010-06-03
> **varunendra said:**
> Follow this thread:(go through entire thread to get a better idea)
If that kind of guy can install Ubuntu 10.04 (through WUBI 10.04) within Win7, then it is imperative to say that it can't be a compatibility issue with Win7.

Guys are just trying to play safe, & Ubuntu is humble & capable enough to let them. So it's fine!

Admins can move it for them if we report it. I just did it.
PS: My bad! I guessed there would be a separate section for [WUBI] where this thread could be moved. Just figured out I was wrong.

He means saving the partition image. Make sure to take images of both boot-partition & the partition where Win7 is installed. Also, boot-partition image should contain MBR. Norton Ghost, PartImage, Clonezilla, .... all do the job just fine.

Think again. If installing through WUBI can be problematic, the proper setup may be even more risky, especially when the guy loves to stick with his Windows installation. WUBI is relatively safer- that's it!
(Of course the user should consider making a proper install once he gets used to it & becomes capable to figure out things).

Good point!

I think you didn't get darkod right..... Sounds like you tried f6 the way you do with f8 in windows - to boot into safe mode - while booting. Read the boldened lines of the above quote.

You said you got the menu with options "Try Ubuntu, Install Ubuntu,...etc." in your first attempt. You have to press f6 only after getting this menu. After pressing f6, click on 'Try Ubuntu' & then choose 'Safe Graphics'.
It **should** work.


Hi,
Thanks a lot for ur reply.
I tried following things, but in vain.


For Ubuntu 10.04 32bit.
Pressing F6 : I got options like 
acpi=off
noapic
nolapic,.. Free software only.

I even tried(both selecting any of these and not selecting any of these) but my purple screen is not going to next screen.

F4 is the option to select in safe mode or so, nut in any case i m getting the same screen forever. 

Then i tried, Ubuntu 9.10 32 bit,
when i used Wubi, it got installed properly but after rebooting it give me black screen.

When I tried 9.10, booting from CD, there also no success, blank screen only.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1421611](http://ubuntuforums.org/showthread.php?t=1421611)
I have same laptop configuration as him and facing same problem for ubuntu 9.10 and above.

Please let me know if some1 faced same problem or has found solution on this.


Regards, 
Naval
Pune,India

---

### Post by ubu-jdc on 2010-06-03
This may not be a great deal of help, but I successfully installed Ubuntu on Windows 7 quite happily the other day. My system configuration/install process was as follows:

Windows OS: Windows 7 Professional (Retail) 64-bit;
Architecture: amd64

Went to [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) and hit the download link and let it get on with it. I didn't at any point create a CD from an ISO to continue the installation. When the system restarted, the Windows bootloader gave me a choice between Windows and Ubuntu. Oddly then I ended up at the GRUB bootloader letting me choose between Ubuntu, Windows 7 and a dead XP install, but Ubuntu worked fine.

Its not something like you're trying to install a 32-bit OS inside a 64-bit one is it? Not that I'm aware that this would cause any problems!

---

### Post by varunendra on 2010-06-07
For the record,

I installed Windows 7 32bit on VMware yesterday, then installed Lucid 32bit through WUBI on it (used Ubuntu 10.04-Desktop.iso). Installed perfectly & works perfectly.

ubu-jdc's post was example of Win7 64bit. So again, there seems to be no compatibility issue between Win7 & WUBI either with 32bit or 64bit versions.

The only areas that I can suspect now are:

[LIST]
[*]Hardware compatibility/configuration (especially when live CD also fails)
[*]broken setup (md5 checksum may be used to check the integrity of installation source - the Lucid iso)
[*]some error during setup (remove, then reinstall would do in this case)
[*]file/folder permissions on the installed files/folders set by Win7 (giving full permission to "everyone" or installing on a fat32 partition would eliminate the chances of this kind of error)
[/LIST]
I'd try to dig up more on this issue but some more feedback (how exactly did you guys install- sources, methods....etc.- full details) should definitely be helpful.

---

### Post by navalmundada on 2010-06-10
hi all,
i tried many diff ways to install ubuntu but ending up with a purple screen of ubuntu for both 9.04 & 10.04...
9.04 ends with black screen and 10.04 ends with welcome screen with options like install/.. etc
i m not getting any way to find out whts the issue.
I need any unix OS to learn it from home...coz i cant connect to office server.. 
:(

---

### Post by varunendra on 2010-06-10
> **navalmundada said:**
> I need any unix OS to learn it from home...coz i cant connect to office server.. 
:(

Have you tried VMware server? If you want to learn something related with networking then Perhaps VMware Server can serve you everything you need. If your laptop has 2GB or more of RAM then it should be able to run Ubuntu 10.04 server + Any lightweight desktop OS on top of Win7!
VMware's server edition is free.

EDIT: VirtualBox 3.2.4 is out. It is much lighter than VMware & getting better every time (still not as perfect as VMware, but being much lighter is an advantage in itself. Besides, it does what most users will need it to do!). It's free too.

---

### Post by keinea on 2010-06-16
I was also encountering the “permission denied” error message when trying to install Wubi in a WinXP SP3 system using the Ubuntu 10.04 LiveCD.

What eventually worked for me was to copy both the wubi.exe installer AND the ISO used to create the LiveCD (ubuntu-10.04-desktop-i386.iso).  Both these files were copied into my C:\Download|Wubi folder.

Once it finished installing then I rebooted it twice to finalize the installation.

Best Regards.

Keith
:cool:

---

### Post by rayf on 2010-06-26
Thanks keinea. I also managed to get round the Errno 22 problems by downloading Wubi 10.4 to the same folder as the Ubuntu iso image and running it from there. Although, for some reason, it insisted on having a CD (any CD) in my CD drive.

BTW, it is not very helpful for you guys to tell folks that they should do a 'proper' install and not use Wubi. If the Live CD is going to have a Wubi install as an option, it ought to 'work out of the box'

---

### Post by varunendra on 2010-06-27
> **rayf said:**
> BTW, it is not very helpful for you guys to tell  folks that they should do a 'proper' install and not use Wubi. If the  Live CD is going to have a Wubi install as an option, it ought to 'work  out of the box'

You do have a point ray! I can't disagree with you.
However you should understand that everything in this world has its  advantages & disadvantages. This universal rule applies to the  'Open Source' concept too. Although, at least to the extent I have  learnt so far, the advantages of Open Source are much more valuable when  compared to the little existing disadvantages.

The 'should-work-out-of-the-box' thing you are complaining about is a  compatibility issue. It is just not easy to be compatible with  'everything', especially when the other party is too reluctant to  cooperate. The most popular desktop OS windows lacks the simple &  basic (& somewhat essential these days) capability to read linux  partitions, or to provide a fully operational LiveCD environment  'out-of-the-box'. How many people have you seen complaining about that?

If you review this thread (or any help thread I've posted in) you'd  realize that I always try to help what one wants to accomplish &  never come up with things like "you're an idiot to do this or say that".  **But sometimes it feels that people think the fault is on your side  if you don't try to explain that actually it isn't!** And that's  exactly why I'm writing this post.

I'm not saying that you shouldn't complain. I'm also not saying that you  should compromise with whatever rubbish you are provided with. When  things are expected to work & they don't, it does cause frustration  & gives you the right to complain. But why blame it all to linux?
So when you calm down, I want you & everyone like you to realize  that you are actually blaming the one who is trying to help, not the one  who is absolutely not! And then if I put it this way: "The almighty  Win7, in reality, is so buggy & incapable that it can't guarantee to  be compatible with WUBI- one of the most user-friendly tools ever  made", would you concur with me?

Linux, despite the lack of support from hardware manufacturers &  profit-making mature software companies (excluding a few ones), is  growing like a wildfire just because IT HAS THE CAPABILITY. Thanks to  the sheer amount of dedication & support that mostly comes from  people who are passionate about freedom and work for the sake of it, not  necessarily to gain profit out of it!
If you are using it, the least you can do is to appreciate the effort  even if you can't appreciate the product itself!

The people here who are suggesting you to make a proper install are just  trying to suggest a better way of trying Ubuntu in its own, original  way where it is much more capable, flexible and comfortable.
However, I do understand that **the terms "better" & "comfortable"  may have different criteria for different people**. But hey! That's  exactly what Open source is all about! The freedom to try out different  things, do whatever you want to do with them, come up with one that  suits you best.

If something is not working for you and you ask others for help, They'll  naturally suggest what has proved to be 'better for them'.

[COLOR=DarkRed]**_So the bottom line is_:**[/COLOR] set  some rules of safety for yourself, then enjoy the dynamic &  versatile journey of Open Source. Nothing is perfect in this world so  don't expect it. If you want a smooth ride, stick with what 'just' works  for you. If you want adventure, there's no limit in Open Source!

Got it Ray? :D

---

### Post by rayf on 2010-06-27
Thank you for that well thought out and considerate reply, varuendra. 

I'm very much in favour of Open Source, I already run Ubuntu NBR on my netbook and, although my desktop is still WinXP, I am trying to replace as many proprietary applications as possible with Open Source, cross platform equivalents so that I can move completely to Ubuntu.

I think that I am knowledgeable and resourceful enough to be able to solve most problems with the help of resources such as these forums. Although it can be frustrating to spend a couple of hours doing that rather than what you intended to do in the first place :p

However, there must be many people who are perhaps trying Ubuntu for the first time who run into this problem and just give up and go back to Windows and my 'complaint' was really on behalf of them.

Parts of Wubi have been re-written in Python, I think. As I'm just learning Python (another great Open Source product), I wanted to have a look at the source to see where the problem occurs. I've not been able to find the source for 10.04 though, the link to Sourceforge from [http://wubi-installer.org/]("http://wubi-installer.org/") seems to have nothing later than 9.04.

---

### Post by Daddyo-613 on 2010-06-27
Kudos to Verunendra;

I just stumbled across this thread and read Verunendra's posting above. Thank you for a your thoughtful response. It should remind us all why the Linux experiment is so important. The freedom to control our own destiny is being eroded, bit by bit, as we allow others to regulate how and what programs we can have access to. 

The computer on your desk is yours. How you use it should be dictated by you and not by commercial interests that consider your desktop their proprietary real estate. That's my personal opinion. But if we want to use a computer and to be connected there are few options out there, at least for those of us who can't write their own operating system. The various Opened Source Linux based OS give us a choice.  

The Linux and GNU experiments and other open source projects allow each person to "pop the hood" and to customize their own system. They are created and maintained largely by volunteers around the world who like tinkering and who understand the importance of preserving our individual freedom and independence. Thank you Verunendra for reminding us all.

**The Virtual Alternative:** On the matter at hand, I don't use wubi so I can't offer much help on your immediate problem. I can however offer a longer term alternative setup that's not a quick fix but may give you the stability and flexibility you're looking for. 

Rather than using a dual boot system you may want to consider switching to have your Linux OS as your primary OS and then load Windows in a virtual machine using programs like VMware or Virtual Box. If you're not familiar with the concept, it allows you to boot up into your Linux environment and then run "Windows" inside a window on you Linux desktop. 

**Some Benefits of a Long Term Solution:** 
1. Windows is happy because it believes that it's controlling the entire computer when in fact its safely contained inside Linux; 
2. There are no partition issues because you only have one partition which is your Linux partition;
3. You don't have to exit one operating system to access the other, both run simultaneously on your screen;
3. With programs like VMware tools you can transfer files from your Windows OS to your Linux desktop simply by dragging and dropping the file;
4. Backing up your Virtual Windows to an external hard drive is a snap you just copy the directory where you're Windows OS data resides.

As this post is slightly off topic, I won't make it any longer with a detailed step by step 'howto'. But I will point out to those who may be interested that you can go to the virtualization forum on this web site. Just go back to the home page on this forum and look for Virtualization.

Cheers and good luck!

---

### Post by rayf on 2010-06-29
I have done some more investigation into the Errno 22 problem. I my case it appears to be connected with using Nero Burner ROM 6.6 to burn the iso image to CD. I burnt a DVD using Nero and that worked.I also burnt a CD with CDBurnerXP which worked. I tried Infrarecorder, which is recommended by the  [Ubuntu download page]("http://www.ubuntu.com/desktop/get-ubuntu/download") but this hangs trying to burn the CD.

Wubi is designed to work with an iso image. If it is run from the LiveCD, it reads the whole CD as a binary file in Python and copies it to the installation hard drive to create a temporary iso image. It is this process that fails. 

The iso image for 10.04 is 699Mb+454Kb and with the Nero created CD, the read of the final 454Kb fails.

My 9.10 LiveCD burnt with Nero also fails. That is 693Mb+ so it's not that its too close to the CD capacity (700Mb)

Update - A CD burnt with Nero Express 6.6 works OK

---

### Post by rayf on 2010-06-30
This is a long standing and ongoing [problem]("https://bugs.launchpad.net/wubi/+bug/207137") with wubi.
It seems to depend on exactly how the iso image was burnt to CD and goes deeper than wubi or Python into the Windows code for reading CDs.

---

### Post by varunendra on 2010-07-20
> **rayf said:**
> This is a long standing and ongoing [problem]("https://bugs.launchpad.net/wubi/+bug/207137") with wubi.
It seems to depend on exactly how the iso image was burnt to CD and goes deeper than wubi or Python into the Windows code for reading CDs.

Hi Ray!

I was offline for last 15-20 days so could not reply.
Your efforts to pin down the culprit are much appreciable. I personally don't know even ABC of any programming language nor do I have any kind of academic background regarding computer education, so can't help at that level. However I do have something I really like to share with you:

**AFAIK, the most common method to install Ubuntu is to download its iso image, then burn it to install it. Now if a person is planning to install it through WUBI, why not use the original downloaded iso itself instead of burning it to a CD? It'll be much more convenient, quicker & (almost) guaranteed way to do so. They can use any utility (like winzip, winrar, 7zip, daemontools, etc.) to extract the provided WUBI program from the iso image.**

*Now something about your interest in python. As I already said, I've no idea about these (or any programming) languages, so pardon me if I sound stupid. I just read somewhere recently that Ruby is becoming more friendly & powerful than python & is thus rapidly becoming favorite of new programmers these days. So if you are new to python & are playing around with the source code of WUBI, I wonder if you wish to have a look at Ruby language. I've also read somewhere that ruby & python have very little difference in coding techniques.*

In the last, yes, I've also faced problems in the past caused by the non-standard method of creating iso images or burning them -adopted by different programs (Nero 5.5- in my case). I think we can do nothing about that except trying to make people aware of these issues. And your contribution about that in this thread- supported by evident facts in your experiments & observations- is quite appreciable! I thank you for that.

---

### Post by linfidel on 2011-02-10
I realize this thread is getting old, but I found this while searching for help on the same problem.  I've tried installing with wubi on XP, and it fails at the end with "invalid argument".

I've been using linux for a long time, and Ubuntu for several years, and I resent the attitude of some of the ex-spurts who are not only unhelpful, but antagonistic toward people who come here for help doing something that is completely expected.  Why should someone not use wubi?  I have 2 dedicated Ubuntu systems, 2 Mac systems, and 2 XP systems.  I need to have the windows system for certain programs.  

I want to see if my current windows system will run Ubuntu well enough to move to it.  I know it will run the live CD, and of course, it may run under a VM, but neither of those situations tells me whether it will run well or not normally.  Sure I can repartition, install Ubuntu in a partition, but then, if it doesn't work the way I want, I'm left with a mess to clean up.  Wubi is a perfect compromise, it's on the damn CD, why should I not use it?  WTF good does it do for people who know nothing about it to jump in and harass people who have a problem?  Hey, guy, if you can't help, stay out of the way so people who can might take an interest.  You know, when you answer a post without helping, a person who may be able to help will think the issue is being handled, and not even read it.

And, if the solution is known, then instead of vague references to downloading the iso and using wubi in that way, tell the people how to do it in steps.  These are often new users looking for help, not confusion.

And don't rationalize the failures by saying Ubuntu sucks less than Windows because windows can't handle linux partitions.  That's just lame.

OK, I'll get down from my soapbox now.

---

### Post by varunendra on 2011-03-15
> **linfidel said:**
> I realize this thread is getting old, ........

OK, I'll get down from my soapbox now.

I think we are having a little misunderstanding here. But since you are partially right about a couple of my replies ("Hey, guy, if you can't help, stay out of the way so people who can might take an interest"), and then I also missed the fact that I should suggest solutions in steps (perhaps because I wrongly thought I was referring to rayf's post only, and he didn't need step-wise description), so I won't deliver anymore of my own ideas here.

Just a humble suggestion for anybody who stumbles this thread seeking help:-
If this thread doesn't solve your problem, you may wish to look at **[Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). **If even that thread doesn't help you, then I'd suggest to follow **[bcbc's]("http://ubuntuforums.org/member.php?u=946783")** posts. He, in my opinion, is a perfect expert on wubi issues.

---

### Post by linfidel on 2011-03-16
On reading my post, I'm not even sure myself what I was referring to.  :)  I think I was frustrated at previous posts here and/or elsewhere that basically said something like "why would you use WUBI?  Just install normally as dual-boot".

I actually came up with another way to test Ubuntu on my Windows system without the need to do anything fancy to uninstall.  In fact, it turned out to be such an easy way to do it that I thought I'd post the idea.

I happened to have two drives, but drives are cheap enough that it might be worth it to get a 2nd drive to do it this way - it doesn't have to be that big.

I installed Ubuntu on a partition on the 2nd drive, then during the final step, there was an opportunity to customize the installation, including where to install GRUB.  In a flash of inspiration, I decided to try installing it into the boot sector of the 2nd drive instead of the first.  I then set my BIOS to boot from the 2nd drive, and have the normal dual-boot options.  But I can make a change in the BIOS to boot the 1st drive if I wanted to abandon the Linux installation, and it would be almost like I never did it, and I can then remove the 2nd drive or delete the partition.  Or, I can get rid of Windows and use the 1st drive for whatever.

It turned out that I was able to get a PCIe video card for $35 after rebate that works very well with dual monitors, so I'm now in the process of converting it to be my main Linux system, and I can convert the old system to be a server system.

Maybe this is old hat to everyone but me, but it worked out very well for me.

---

