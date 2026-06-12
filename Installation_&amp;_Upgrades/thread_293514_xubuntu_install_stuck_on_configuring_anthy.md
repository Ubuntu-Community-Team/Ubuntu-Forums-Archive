---
title: "xubuntu install stuck on configuring anthy"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2006-11-05
I am installing xubuntu on an old laptop (64MB RAM). The install, in low memory mode, has got to the 'select and install software' section, and at 65% complete has got stuck on 'configuring anthy...'

It has been disk-thrashing for well over an hour, with no tangible progress.

Do I really need anthy? What does it do?
Is there any way to skip this package and continue with the instalation?

Thanks in anticipation,
Alan

---

### Post by cd7 on 2006-11-05
I had the same problem... to complete the installation I had to add 128 MB (I borrowed from an other NB) and everything went fine. After the install I went back to 64 MB of memory. It works quite well now.

---

### Post by gruntus on 2006-11-05
> **cd7 said:**
> I had the same problem... to complete the installation I had to add 128 MB (I borrowed from an other NB) and everything went fine. After the install I went back to 64 MB of memory. It works quite well now.

I had the same problem ... difficulty is I can't add the extra memory. Any other ideas out there?

---

### Post by frostie on 2006-11-07
I had the same, 65% configuring anthy and no further.

Looking it up it seems to be something to do with inputting Japanese characters which I definitely don't need. I started the install again but there doesn't seem to be anywhere I can select not to install it and like you I can't add more memory so I'm not sure there's any way round it.

I downloaded and burned the alternate iso for the install which mentioned it was for machines that had less than 128mb ram so I'm not sure why it won't install.

I'm actually setting up an old machine for a friend so I think I'm going to have to give Vector Linux or Slackware a go for now. I'll keep an eye here for any suggestions though.

---

### Post by kerry_s on 2006-11-07
Grab a gparted live cd and make a swap that it can use while installing, you might as well create your partion while your add it then just select it on install and make sure you go through all the steps,select file,mount,....

-> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by estilete on 2006-11-11
I have the same problem. I used the file xubuntu-6.10-alternate-i386.iso and at 65% complete has got stuck on configuring anthy

---

### Post by MotivatedTea on 2006-11-12
I have run into the same problem. I'm trying to install Xubuntu on an old laptop (Pentium III 600MHz with 64MB RAM). I don't think the install actually hung. I had made a 256MB swap partition. I didn't get any error messages and the system remained responsive (you can press Alt-F2 to get to a console, then Alt-F1 to get back to the installer), but the harddrive was thrashing like crazy. If you've got the time, you could try leaving it going overnight and see if it finishes. However, after 1h30 I decided not to wait.

I have a workaround, if you're not too uncomfortable with a command-line. Instead of performing a normal installation, chose a command-line install (CLI). The install will finish quickly, but all you'll have is a command prompt. Log in. Put the install CD back in the drive and run **sudo mount /cdrom**. Run **sudo aptitude**, select **xubuntu-desktop**, then un-select both **scim-anthy** and **anthy**. *(For those unfamiliar with aptitude: Press slash (/) to search for packages. Press plus (+) to select the highlighted package or minus (-) to un-select it. Press G to go ahead and perform the installation.)* When you're done, you'll need to **sudo umount /cdrom** before you can eject it.

This should finish what would normally have been done by a "normal" install, except that we have told it not to install anthy. I have just finished, and it worked for me. Kind of. On the reboot, I got the login manager, logged in, but got a completely blank desktop (no menus). A minute later I got crash notice and Xfce restarted. Then it worked properly.

---

### Post by jgaffke on 2006-11-12
Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry

---

### Post by ncc74656m on 2006-11-13
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry


Bless your heart, sir! I've had the same problem with four different installs and wanted to shoot myself! Sure enough, a quick search on these most knowledgeable forums helped. You guys rock!

My friend for whom I'm installing this will be most happy. If you're in New York, you should stop by and get cookies from her, which I'm sure she'd be more than happy to provide. :D

---

### Post by Warstrong on 2006-11-19
> **MotivatedTea said:**
> I have run into the same problem. I'm trying to install Xubuntu on an old laptop (Pentium III 600MHz with 64MB RAM). I don't think the install actually hung. I had made a 256MB swap partition. I didn't get any error messages and the system remained responsive (you can press Alt-F2 to get to a console, then Alt-F1 to get back to the installer), but the harddrive was thrashing like crazy. If you've got the time, you could try leaving it going overnight and see if it finishes. However, after 1h30 I decided not to wait.

I have a workaround, if you're not too uncomfortable with a command-line. Instead of performing a normal installation, chose a command-line install (CLI). The install will finish quickly, but all you'll have is a command prompt. Log in. Put the install CD back in the drive and run **sudo mount /cdrom**. Run **sudo aptitude**, select **xubuntu-desktop**, then un-select both **scim-anthy** and **anthy**. *(For those unfamiliar with aptitude: Press slash (/) to search for packages. Press plus (+) to select the highlighted package or minus (-) to un-select it. Press G to go ahead and perform the installation.)* When you're done, you'll need to **sudo umount /cdrom** before you can eject it.

This should finish what would normally have been done by a "normal" install, except that we have told it not to install anthy. I have just finished, and it worked for me. Kind of. On the reboot, I got the login manager, logged in, but got a completely blank desktop (no menus). A minute later I got crash notice and Xfce restarted. Then it worked properly.

could you explain to me EXACTLY what i need to do to get past configuring anthy?  I don't really understand what you mean...

1- i don't understand how i'm supposed to "Log in" if I don't have Windows or Xubuntu installed yet :P 
2- I need to understand what I'm supposed to type into the command line.  Going into the command line install brings up that command line and i know that's what is supposed to happen, but when you say for example "...and run **sudo mount/cdrom**." does that mean that i first type "/run **sudo mount/cdrom**" or what?  I wanta know exactly what i need to type in.  Quote it too so i know.  

Thanks, I have been trying to fix this problem for a month and finally i read your post and i think this will resolve the issue. YOU ROCK!

---

### Post by Piotr.Sniady on 2006-11-27
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry

Thanks. On the bottom of the processes given by "ps" there is one (or two) involved in generating dictionaries for the Japanese input method. In my case I had to kill two processes to proceed. Thanks!

---

### Post by toekneebullard on 2006-11-30
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry
Well I have to say that you could have stated that a little nicer, but after poking around I figured out what that means.  Thanks.

---

### Post by Risc on 2006-12-07
Thank you! Thank you!

A very very handy bit of help.

---

### Post by timsk on 2006-12-30
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2          #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen



Worked well for me too. Thanks aplenty.

To make my contribution a little more worthwhile too, here's the above tip, formatted to be easier for beginners:

  press alt-F2
  type [FONT="Courier New"]ps | grep mkworddic[/FONT] and press <Enter>. [Note: that's 'p' followed by 's' then a space, then a vertical bar, then another space, then 'grep' then a space and finally 'mkworddic']
  type [FONT="Courier New"]kill -9 xxxxx[/FONT] where xxxxx is the id number from the previous command, and press <Enter>
  press alt-F1

---

### Post by MaSa256 on 2007-01-01
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry


Thanks a lot, that worked for me. Now i can use xubuntu on my old Intel celeron 466 :D

---

### Post by pohaku on 2007-01-05
> **ncc74656m said:**
> Bless your heart, sir! I've had the same problem with four different installs and wanted to shoot myself! Sure enough, a quick search on these most knowledgeable forums helped. You guys rock!

My friend for whom I'm installing this will be most happy. If you're in New York, you should stop by and get cookies from her, which I'm sure she'd be more than happy to provide. :D
Just adding my "Me Too!" thank you - I finally got my 200mhz/96mb ram/2gb hdd Sony VAIO 505G up and running thanks to this post! The forums are GREAT!

---

### Post by tonywhelan on 2007-01-14
Thanks a heap for this fix. I was on my third attempt to install and ready to pack it in when I decided to have a look on the forum. 

cheers

Ton
in Canberra, Australia

---

### Post by saf on 2007-01-21
I would also like to add my thanks--process had hung for 1h+ on configuring anthy @ 65%.  Found this thread and back to chugging along w/ Xubuntu on my Inspiron 7000.  :)

Thanks again!

-Soren

---

### Post by drahmad on 2007-01-23
Thanks! That worked for me (Celeron 400, 64Mb laptop).

Does this "do" anything to my installation? ie. Will I have to go back and "correct" anything or is the installation just going to be ok?

---

### Post by IanW on 2007-01-28
Thanks from me too. I had the same problem until I read this thread.

Since Xubuntu is supposed to be the "lightweight" version of Ubuntu, I find myself wondering why anthy cannot be de-selected when we tell the installer we're not in Japan?

---

### Post by superxero044 on 2007-02-04
Thankyou ever so much. I am quite excited to see if this will actually let me get linux operating on my old Toshiba Tecra 720CDT! Wish Me luck!

Got past 65% finally though on the installer :)

---

### Post by lordavatar on 2007-02-08
Hi!

I'm almost a complete newbie with Linux, and I spent some unpleasant hours with this problem. I haven't tried the workaround yet, but I think maybe it would be a good idea if Ubuntu and/or Xubuntu had the option to do a "system test" before starting the actual installation. For example, it could check the amount of RAM, etc., and tell the user if the machine is capable of installing/running the distro in question. Also, if 64 MB is not actually enough to do the installation from Xubuntu Alternative Install CD (note: I had the same problem with 96 MB and a swap partition), then maybe the memory requirement on the download page should be changed. I don't know what would be the best option for me to tell the developers/website maintainers about these suggestions - any ideas?

---

### Post by Chris Beall on 2007-02-10
Killing the anthy process worked for me on a 96MB system.  I was installing Xubuntu using the text installer, which is supposed to need only 64MB...

Like the previous poster, I wonder why this process is part of installing an English-language system.

---

### Post by trgz on 2007-03-03
Brilliant thread - I was stuck at 65% too. It's a shame I didn't read this thread before switching the laptop off (a 64MB 266Mhz Compaq Armada 7792DMT) - I was about to download gparted and then I saw this.
Thanks to those who posted the fix and to those who made it n00b frendly.
:)
footnote:
it's a shame that this 'bug' appears in a low memory install CD  (alternative xubuntu 6.10 disc) and that it's not been fixed. Also I just rebooted and noted that the OEM install is creating a SWP partion (#5) on the hd as I type.
and another footnote:
note that there are (may be?) three five figure numbers when you display - two on the first line and one on the second - I found that it's the first of the three

---

### Post by rippers on 2007-03-16
Thank you very much! merci!

---

### Post by rhinodog8 on 2007-03-17
i'm using a imac g3 and the screen goes off the edgye a little and I it can't get the xxxxx number could someone please post what the xxxxx number is

---

### Post by daporgue on 2007-03-21
Hi guys! 
Thanks a lot for your advice, it worked!!!!!!! My girlfriend's going to be very happy with her "new" old laptop :lolflag:

---

### Post by kimlevente on 2007-03-23
I have had same problem with my Thinkpad 240.
I have installed xubuntu by New laptop and i put again HDD to thinkpad 240 and it works.
I had to only configure Xserver.

Good luck Guys !!

---

### Post by didijeeeke on 2007-03-24
i found a way to install it on my old laptop i first had problems with the installer it got stuck each time at the partition manager. 
So i loaded the disk again and pressed f6 at the disk boot menu and i changed the size of the ramdisk into a lower size 
this left me more spare memory and i could install the whole system !! . 

i hope this helps.

---

### Post by aerie on 2007-03-24
Killing Anthy worked for me too. I'm running a Celeron 500MHz with 64 Mb of RAM. I wish I had more memory because the OS is very slow:(

---

### Post by bmxje on 2007-03-31
Tnx Tnx Tnx!!! worked for me too!
im now waiting for my laptop to complete the rest of the installation! 
afther that, i'll be running xubuntu on a celeron 500 Mhz with 64 Ram! :lolflag:

---

### Post by mikalh on 2007-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/anthy/+bug/56114](https://bugs.launchpad.net/ubuntu/+source/anthy/+bug/56114) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

Great advice! Apparently this has been reported as a bug on lanchpad for 8 months. I wonder why the installer doesn't use the swap partition after you've set it up...

---

### Post by ksryno on 2007-04-19
this also works on feisty fawn. Just installed on my rev a. iMac w 64mb ram, 4.3 gb hdd, 233mhz.

---

### Post by parsim on 2007-04-20
Thanks for the tip.

I found that the process ID of mkworddic kept changing, so "killall mkworddic" was required.

Actually seems like the problem is that the process is constantly dying and being re-spawned.

---

### Post by hardcle on 2007-04-24
I just wanted to add my thanks as well.  The fix got the install going again on my old Thinkpad with 64MB RAM.

---

### Post by RaineJen on 2007-04-28
I have a couple of old Dell Latitude CPx laptops hanging around my house.  One had enough memory for me to install Windows XP on it, and I decided to try Xubuntu on the other one (which was running Win95 before I started).  I am having the same "stuck on anthy" at 65% problem  (I'm using the alternate install CD, which informas me that its using 'low membory mode", and I have 64MB ram).  

I tried the Alt+F2, ps, & kill mkworddic solution listed above, but I don't seem to be getting anywhere.  When I typed " ps | grep mkworddic ", it returned a 3 digit number (along with some other stuff), which I tried killing but it didn't like it.  I tried the command again and got a different set of numbers, this time  including a 5 digit one, which I tried to kill & was returned a message indicating that there was no process (of that id) to kill.  As I'm new at this I wonder if I am missing something?

After about 15 tries (each time returned different numbers) I shut the computer down and restarted it, and tried the command-line install solution (also listed above).  After successfully installing a command-line, and apparently successfully installing xubuntu-desktop minus the anthy and scim-anthy, I tried to reboot and merely got a command line again; is there something I am missing here as well?

I am trying to install it one more time, to see what Control+C does.  Am currently at 50 percent of installing software and waiting for the 65% anthy fermata.  Supposing this doesn't work either, has anyone had any luck just waiting for anthy to finish whatever it's doing?  I could leave it on overnight and see what happens.

---

### Post by RaineJen on 2007-04-28
Done.  No need to use Alt+F2, since holding down the right hand Control button and typing C seemed to make it move on from the anthy fixation.

---

### Post by chris_moulding on 2007-05-01
Many thanks, Jerry for your solution.

I was stuck at 65% loading anthy for 5 hours. I'm loading Xubuntu on a Toughbook CF-M34 with no floppy or cd-rom using the Wubi network install so if I can't finish loading it may have been somewhat serious!

Thanks again,

Chris

---

### Post by lbmd on 2007-05-07
My Thanks in advance. I was trying to install xubuntu last night got stuck and I left it. I am at work now but it is still running. Will see if it fininshed after 24 hours. If not I will follow instrucktions above and hopefully will come right.

Regards
lbmd

---

### Post by dobratzp on 2007-05-07
I was running into "stuck at 65% problem" described here while trying to install Xubuntu on a Dell Latitude CPi (Pentium II 266 MHz).  It has 96 MB of RAM and  I'm running the Alternate CD.  As killing the mkworddic process seemed like a drastic step for me, I decided to wait it out.  I let it run overnight and the install completed and I now have a working Xubuntu desktop.

Note: the install previously had been stuck on a blue screen and then came up with a message that it failed to mount the CD.  Disabling DMA on the drive following the instructions here fixed the problem:

[http://ubuntuforums.org/showthread.php?t=309284]("http://ubuntuforums.org/showthread.php?t=309284")

---

### Post by dav7mx on 2007-05-09
Well, I have to say thank you very much too!

I had the same problem on my compaq presario 700 (128 RAM, 20 Gb HD, a swap partition of 1 Gb). 
I did the killing process and it seems that everything worked ok. I was installing the feisty fawn release. 

Thank you very much, you saved my computer of having windows :D

---

### Post by friarjack on 2007-05-09
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry

Complete newbie here trying to follow your suggestion.  I cannot figure out where the process id.  When I enter the ps command, this list is too long for my screen and too fast for me to see.  Is there a way I can get it to show me one screen length at a time?  Or is the id there in front of my face and I just don't know what I'm looking for?

Thanks,
Jack

---

### Post by ILYA99 on 2007-05-12
> 
Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

Alt-F2 #switch to a command line console
ps #type command "ps", then <Enter>
kill -9 xxxxx #type using process id from ps
Alt-F1 #go back to install screen
Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry


Worked also with Pentium 586 with 64 MB RAM.

---

### Post by DerArzt on 2007-05-17
Another thanks to the Jerry!

---

### Post by jimbean on 2007-06-02
thanks jgaffke
once i tried it a couple of times different ways
it sank in and worked

---

### Post by Webby_s on 2007-06-23
It also worked for me. Good to see that there is a work around but it is kinda weird that it is this popular why not just eliminate it some how?  Just a thought. Thanks all!

---

### Post by bhuthogg on 2007-06-25
thanks for this just got through that was about to switch off the old laptop wen i seen your post :D

---

### Post by LGer on 2007-06-30
Did any of you notice any problems by aborting part of the install? In other words... Did the process  of aborting anthy cause any other problems with the final install? Thanks.

---

### Post by xDaveManx on 2007-07-02
Thanks for this thread, guys.  I was about to give up on linstalling Xubuntu to my sister's ancient Gateway Essential (PIII, 64 MB RAM) until I found this.

What a serious bug.  You'd think someone would be working on it...

---

### Post by davester on 2007-07-02
I also experienced the same problem - however after following the a/m info into the command line, the install finished without problem.  Thanks people.  I am new to the linux world, and hardly ever go back to windows.

---

### Post by diogenes_3 on 2007-07-05
My ole Toshiba Tecra 550CDT (Pentium I/266 and 64 MB) and I are metooing on Jerry's "solution" after three hours of configuring anthy. I agree with some of the other posters that a workaround to this one should be included, even though I understand it is not really a bug, rather a nuisance (I read at least one poster had the patience to let the process run through 24 hrs and it eventually succeeded), but please, this thread started in November 06, while I am installing the next version, 7.04, and the figure is still 65%???

---

### Post by ajmo on 2007-07-10
Thanks Jerry

I was trying to install Feisty Fawn Alternative on a Celeron 433MHz with 64MB RAM and went to bed after two hours of $#*@ anthy. Six hours later it was still thrashing...

---

### Post by Ebuntor on 2007-07-19
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry

Thanks Jerry! That workaround did it. :D

In case someone can't find the process ID: if you type the "ps" command you'll see a whole list of processes with columns of numbers. The first row of numbers is the process ID.

---

### Post by YeagerRobber on 2007-08-02
Great tip,:) this saved my day!

---

### Post by gen0m on 2007-08-03
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry

You are my hero =D>

---

### Post by jtdunc on 2007-08-17
> **bmxje said:**
> Tnx Tnx Tnx!!! worked for me too!
im now waiting for my laptop to complete the rest of the installation! 
afther that, i'll be running xubuntu on a celeron 500 Mhz with 64 Ram! :lolflag:

Man o' man!

Dang I was stuck at 61% for about two hours and I found this thread.  Now it's moved onto installing other items and is at 65% in a about 8 minutes. 

Hope the rest of the install goes smooth.  Go to sleep for a few hours and wake up and check on it.

Installing on a 300 Mhz PII Dell  CPi D300XT with only 64MB of RAM.  I know, I'm looking under rocks for another 64MB of RAM.

Now I just hope I can configure my Linksys wireless card for the Net!

Then I would be :guitar:

---

### Post by Open on 2007-08-17
----------------------------------------------------------
Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

Alt-F2 #switch to a command line console
ps #type command "ps", then <Enter>
kill -9 xxxxx #type using process id from ps
Alt-F1 #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry
----------------------------------------------------------

Thanks allot guys !!!! :KS:)

---

### Post by blackdragon12 on 2007-08-25
Thanks alot, worked here too. Now I hope i dont come across anything more like this until the installation is completed.

---

### Post by slickw9 on 2007-09-11
> **jgaffke said:**
> Once stuck at installing anthy, try this,
where xxxxx is the process id that ps gives you
for /usr/bin/mkworddic:

  Alt-F2               #switch to a command line console
  ps                   #type command "ps", then <Enter>
  kill -9 xxxxx        #type using process id from ps
  Alt-F1               #go back to install screen

Install seems to nicely give up on anthy
and proceed from there.
Worked for me.

Jerry


I had to register just to say that you are a sanity saver!!!  Thank you SO MUCH!!!!:KS ](*,)

---

### Post by Starscream112 on 2007-09-12
I'm joining the club:  IBM Thinkpad 600E PII 400mhz 128mb 
800mb #5 swap, hoping it would facilitate the install.  No such luck.  But the process kill worked!

Thanks!

And does anyone know what anthy does?  I read the earlier post where someone *thinks* it has to do with Japanese language entry.  Does it?

Can anthy be installed afterwards?  How?

---

### Post by DaemonEX on 2008-04-02
I managed to install Xubuntu at a Compaq Presario 350mhz, with 64mb RAM, Ati 3d rage pro lt. 2x video-card (quite rare indeed :)).

After waiting whole night for the pc to install anthy, to find out that I can stop it! Thanks alot!

Btw, with process number the 1st number in the line is meant, NOT the changing number aside the process name.

---

