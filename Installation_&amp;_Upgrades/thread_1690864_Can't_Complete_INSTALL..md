---
title: "Can't Complete INSTALL."
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by FahvahKarol on 2011-02-19
I Downloaded Free Ubuntu Desktop From InterNet In Order to Have a Separate OS. I Used the 'TRY UBUNTU', and Rather Liked It, But Every Time, (Which Now Has Been Several), The Install STOPS at Approximately 80%, The FORWARD Button Remains Greyed Out, and I Get 'READY WHEN YOU ARE...', With Some Sort of PROMPT After Clicking On the 'Ready When You Are...', With a Button That Says SKIP, but It TOO Remains Greyed Out.
 
Between a Couple of My Install Attempts, I Removed Disk From Tray, To Open From WINDOWS XP. My Screen Remained BLACK. I Now Cannot Open WINDOWS From That Computer Even Though I CHOSE 'Install Alongside Other Operating Systems', and Had a Separate Partition For UBUNTU.
 
What Do I Do NOW? HELP! Please.
 
FaKA

---

### Post by Sean Moran on 2011-02-19
> **FahvahKarol said:**
> I Downloaded Free Ubuntu Desktop From InterNet In Order to Have a Separate OS. I Used the 'TRY UBUNTU', and Rather Liked It, But Every Time, (Which Now Has Been Several), The Install STOPS at Approximately 80%, The FORWARD Button Remains Greyed Out, and I Get 'READY WHEN YOU ARE...', With Some Sort of PROMPT After Clicking On the 'Ready When You Are...', With a Button That Says SKIP, but It TOO Remains Greyed Out.
 
Between a Couple of My Install Attempts, I Removed Disk From Tray, To Open From WINDOWS XP. My Screen Remained BLACK. I Now Cannot Open WINDOWS From That Computer Even Though I CHOSE 'Install Alongside Other Operating Systems', and Had a Separate Partition For UBUNTU.
 
What Do I Do NOW? HELP! Please.
 
FaKA
80% is about when the installation process starts looking online for apt-get and language-packs and stuff, and that can take hours depending on your Internet connection.  It is best to install Ubuntu offline, and get all the necessary updates and things AFTER you have Ubuntu on your hard disk.  That's one.  Pressing SKIP works just the same, but not so melodiously.

Not sure on the second problem - Screen Black, but try the install offline because it will get to the GRUB installer a lot faster and complete the installation, and should boot into a GRUB menu with Windows and the new Ubuntu on the menu.  I assume you're installing Ubuntu 10.10 Meerkat.

---

### Post by FahvahKarol on 2011-02-19
> **Sean Moran said:**
> 80% is about when the installation process starts looking online for apt-get and language-packs and stuff, and that can take hours depending on your Internet connection. It is best to install Ubuntu offline, and get all the necessary updates and things AFTER you have Ubuntu on your hard disk. That's one. Pressing SKIP works just the same, but not so melodiously.
 
Not sure on the second problem - Screen Black, but try the install offline because it will get to the GRUB installer a lot faster and complete the installation, and should boot into a GRUB menu with Windows and the new Ubuntu on the menu. I assume you're installing Ubuntu 10.10 Meerkat.
Thank You For Responding So Quickly Sean. Do You Mean That the INSTALL Is Still Working In the Back Ground, and I Need To IGNORE the 'Ready When You Are' With the Flashing Prompt? I've Got DSL and a Couple Hours to Spare. I DID Check the 'Install Updates' Button. And I THINK That I'm Connected to the Internet Though, I've Reached the Same Place Before Without Being Connected If I Recall Correctly.
 
I Don't Know WHY My Compter Doesn't Fire Up In Windows Either. Perhaps I'll Have to Run the REPAIR Program?
 
But As I Say, I Can Wait For Something to Happen For the Next Couple Hours If It Doesn't Take Longer Than Five.
 
FaKA

---

### Post by Sean Moran on 2011-02-19
> **FahvahKarol said:**
> Thank You For Responding So Quickly Sean.  Do You Mean That the INSTALL Is Still Workig In the Back Ground, and I Need To IGNORE the 'Ready When You Are' With the Flashing Prompt.  I've Got DSL and a Couple Hours to Spare.  I DID Check the 'Install Updates' Button.  And I THINK That I'm Connected to the Internet Though, I've Reached the Same Place Before Without Being Connected If I Recall Correctly.
 
I Don't Know WHY My Compter Doesn't Fire Up In Windows Either.  Perhaps I'll Have to Run the REPAIR Program?
 
But As I Say, I Can Wait For Something to Happen For the Next Couple Hours If It Doesn't Take Longer Than Five.
 
FaKA
The 'ready when you are' is, if I recall just something new for Meerkat.  I don't recall it in Karmic, but if you can do the installation OFFLINE, it should breeze past that 80% point, where it starts to go online looking for apt data and language packs.  Do it offline and it will just install the Ubuntu you have already on your Live-Cd, and it's a bit of a guess, but it will then configure GRUB, looking around for anything in the way of Windows or other Linux operating systems, and setup GRUB to boot properly - Ubuntu AND Windows.

That's my best guess.  The online installation might be the crux of the installation problem, so run the install offline, and and hopefully 'ready when you are' will change to 'Installation Complete' inside 5 minutes.

---

### Post by FahvahKarol on 2011-02-19
> **Sean Moran said:**
> The 'ready when you are' is, if I recall just something new for Meerkat.  I don't recall it in Karmic, but if you can do the installation OFFLINE, it should breeze past that 80% point, where it starts to go online looking for apt data and language packs.  Do it offline and it will just install the Ubuntu you have already on your Live-Cd, and it's a bit of a guess, but it will then configure GRUB, looking around for anything in the way of Windows or other Linux operating systems, and setup GRUB to boot properly - Ubuntu AND Windows.

That's my best guess.  The online installation might be the crux of the installation problem, so run the install offline, and and hopefully 'ready when you are' will change to 'Installation Complete' inside 5 minutes.
O.K.  I'll Stop THIS Install, and Try Again OFFLINE.  But It Seems to Me That I DID Try to Install Offline at Least ONCE, and It 'Stopped' At About the Same Place.
 
Please Be On the LookOut For My Return.
 
FaKA

---

### Post by Sean Moran on 2011-02-19
> **FahvahKarol said:**
> O.K.  I'll Stop THIS Install, and Try Again OFFLINE.  But It Seems to Me That I DID Try to Install Offline at Least ONCE, and It 'Stopped' At About the Same Place.
 
Please Be On the LookOut For My Return.
 
FaKA
I can wait for another 30 minutes, but if your OFFLINE install fudged at 80%, then all my guesswork was mistaken.  I hope not, but I'll wait another half hour in the hope that you got the clean install and a good installation of GRUB with Windows and Ubuntu atleast bootable.

---

### Post by FahvahKarol on 2011-02-19
> **Sean Moran said:**
> I can wait for another 30 minutes, but if your OFFLINE install fudged at 80%, then all my guesswork was mistaken.  I hope not, but I'll wait another half hour in the hope that you got the clean install and a good installation of GRUB with Windows and Ubuntu atleast bootable.
It Began Install at 29 Minutes After the Hour, Reached the 80% Point At 38 Minutes After the Hour, and Progress Bar Is Still Stalled At 80% Point At 48 Minutes After the Hour With 'READY WHEN YOU ARE' and Flashing Prompt.
 
FaKA

---

### Post by Sean Moran on 2011-02-19
> **FahvahKarol said:**
> It Began Install at 29 Minutes After the Hour, Reached the 80% Point At 38 Minutes After the Hour, and Progress Bar Is Still Stalled At 80% Point At 48 Minutes After the Hour With 'READY WHEN YOU ARE' and Flashing Prompt.
 
FaKA
I'm sorry that my suggestions were not the answer.  The 80% made me guess at some online/offline problem, but I was wrong.

#1 Check the MD5SUM on the .iso file you're using.  Make sure you have a good foundation to work with.
#2 Go back to Karmic Koala 9.10 because it might be either your hardware, or yet another 10.10 bug.

Either way, it might be a long night to download another 700Mb of Meerkat OR Koala, and I hope that your MD5SUM is good, because then someone else might work out what is going wrong at the hardware end, because I only know the hardware I am using now.

If you do have to download another .iso, I have a 297.1MB iso for Ubuntu with GNOME and all the standard hardware drivers that you could test at [http://www.portstar.org/ISO/psminikar.iso](http://www.portstar.org/ISO/psminikar.iso) if it will save a few hours waiting for the extra 400Mb.  At least then you'd know if your hardware is good for Ubuntu, and if Ubuntu is good for your hardware.  It's a very alpha stage .iso but might suit testing for you and I both.

---

### Post by FahvahKarol on 2011-02-19
> **Sean Moran said:**
> I'm sorry that my suggestions were not the answer.  The 80% made me guess at some online/offline problem, but I was wrong.

#1 Check the MD5SUM on the .iso file you're using.  Make sure you have a good foundation to work with.
#2 Go back to Karmic Koala 9.10 because it might be either your hardware, or yet another 10.10 bug.

Either way, it might be a long night to download another 700Mb of Meerkat OR Koala, and I hope that your MD5SUM is good, because then someone else might work out what is going wrong at the hardware end, because I only know the hardware I am using now.

If you do have to download another .iso, I have a 297.1MB iso for Ubuntu with GNOME and all the standard hardware drivers that you could test at [http://www.portstar.org/ISO/psminikar.iso](http://www.portstar.org/ISO/psminikar.iso) if it will save a few hours waiting for the extra 400Mb.  At least then you'd know if your hardware is good for Ubuntu, and if Ubuntu is good for your hardware.  It's a very alpha stage .iso but might suit testing for you and I both.
Even Though We Got Nowhere, Sean, You Have Helped By Pointing Out What SHOULD Be the Difference Between ONLINE and OFFLINE.  Seeing That There Was No Progress In Either One, It Helps To Know Not to Wait Around For Hours.  
 
I'm Not That Much of a Geek, (YET), No Know Exactly What You Are Talking About.  But I'll Pursue Another Course and Contact Help/Support.  Perhaps It Was My Download, and I MIGHT Be Able to Pursude Ubuntu to Send Me a DISK.  I Had Ordered a Disk From Them Previously But It Was the Wrong One, Not the DeskTop.  They Were Reluctant to Send Me Another.
 
Again...Thank You.   I'll Stay In Touch With This Board To See What Further Developes.
 
FaKA

---

### Post by Sean Moran on 2011-02-19
> **FahvahKarol said:**
> Even Though We Got Nowhere, Sean, You Have Helped By Pointing Out What SHOULD Be the Difference Between ONLINE and OFFLINE.  Seeing That There Was No Progress In Either One, It Helps To Know Not to Wait Around For Hours.  
 
I'm Not That Much of a Geek, (YET), No Know Exactly What You Are Talking About.  But I'll Pursue Another Course and Contact Help/Support.  Perhaps It Was My Download, and I MIGHT Be Able to Pursude Ubuntu to Send Me a DISK.  I Had Ordered a Disk From Them Previously But It Was the Wrong One, Not the DeskTop.  They Were Reluctant to Send Me Another.
 
Again...Thank You.   I'll Stay In Touch With This Board To See What Further Developes.
 
FaKA
Thanks mate.  I've been trying to help out a little when I see a thread with zero replies in the Install and Wireless forums for the past few days, but today I can't seem to put a foot right with all my ignorant advice. 

I'll try to do better on Monday and only help when I know the answers without the guessing that did me well for a couple of days, but only by chance.

Take care mate, and don't give up on Ubuntu.  There's no shortage of will, so there will be a way.

---

### Post by kansasnoob on 2011-02-19
Shortly after you boot the Live CD you'll see a purple screen with two small icons at the bottom. At that point you have about 3 seconds to press any key and then you'll see a screen to select language, followed by a screen with 5 boot options, from there select "Check disc for defects". That usually takes about 4 minutes to complete so be patient.

If it passes it'll say, "no defects found" so next lets get a look at what you've done so far by posting the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions for the script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Old_Grey_Wolf on 2011-02-19
Double posted.

---

### Post by Old_Grey_Wolf on 2011-02-19
FahvahKarol, 

Just before you got to this point (...The Install STOPS at Approximately 80%, The FORWARD Button Remains Greyed Out, and I Get 'READY WHEN YOU ARE...), it asked for you to enter a user name. If you entered a user name that had any **C**apital **L**etters, try entering your user name without any capital letters. It should then let you go forward.

---

### Post by FahvahKarol on 2011-02-20
> **Old_Gray_Wolf said:**
> FahvahKarol, 
 
Just before you got to this point (...The Install STOPS at Approximately 80%, The FORWARD Button Remains Greyed Out, and I Get 'READY WHEN YOU ARE...), it asked for you to enter a user name. If you entered a user name that had any **C**apital **L**etters, try entering your user name without any capital letters. It should then let you go forward.
 
Thank You For Your Input kansasnoob and Old_Grey_Wolf. I Reduced My Name and User Name to All Lower Case, (And Also Working OFFLINE), But I'm Again Stuck At 'Ready when you are...', With the last Two Messages THERE Being....
update release notes label()
update release notes label()
 
I Still Can't Open WINDOWS XP Even Though I Ran SETUP>REPAIR>FIXMBR.
NOW I Can't Even Boot Up From OPERATING SYSTEM CD To Run the SETUP REPAIR Recovery Console. The Final Message In the Repeating Scroll Before EXIT Is 'Boot Textname not Received', (Or Something Along Those Lines.). I'll Now Try to Exit INSTALL......
 
Hold It....Just See That ANOTHER Message Popped Up Under 'Ready when you are...'. I Guess, Even Though It Has Been About an Hour...Something Is Still Happening.
 
Get Back To Youze.
 
FaKA

---

### Post by FahvahKarol on 2011-02-20
Wellllllllllllllllllllll......It APPEARS That the Install Is Going Nowhere.  There Were Only TWO Messages After the Two 'update release notes label()' Messages, and Those Are Basically the Same As Well One at 10:17:07, (Not REAL Time; PROGRAM Time, and the Other a Little Over an Hour Later 11:17:01, The Only Differenc Being the CRON Number.
 
[NOW....Dang It....The Thing Just Made a Liar Of Me Again 12,13, and 14:17:02 Are Here, Guess I Forgot to Scroll While Watching It.]  But Here Is How They All Read:
 
Feb 20 14:17:02 ubutu CRON[8595] :  (root)  CMD  (    cd  /  &&  run-parts  --report
/etc/cron.hourly)
 
To the Best Of My Ability to Line Up the Red Progress Bar It Ends Here    l  Between the 'r' and 't' In 'run-parts' and I Don't THINK It Has Changed At All, But Didn't Think to Measure It Until Sometime AFTER the 11:17:07 Message.
 
I'm Going to Let It Run While I Go To Bed, But I Have Strong Doubts That I'm Making Any Progress At All, and These CRON Messages Are Just the Program's Way Of Keeping Track Of How Long It Can PLAY This FOOL.
 
FaKA

---

### Post by Old_Grey_Wolf on 2011-02-20
FahvahKarol,

Also make sure the computer name you enter does not have capital letters.

---

### Post by FahvahKarol on 2011-02-20
> **Old_Gray_Wolf said:**
> FahvahKarol,
 
Also make sure the computer name you enter does not have capital letters.
 
My Computer Name 'Pavillion-dv4000-EC681AV' Was Placed In That Bar Automatically.  Do You Mean I Should 'Lower Case' Those Manually?  One Would Think the Program Would Clue One In On This Requirement.
 
Last Message:
Feb 21 00:17:01 ubuntu CRON(11035) :  (root)  CMD  (    cd / &&  run-parts  --report
/etc/cron.hourly)
 
Now Going to Try kansasnoob's Suggestion.  If I Can Get Into the TRY UBUNTU That Is.  When I First Booted With This Disk, It Went To the LogIn Page Which Suggests It Was Responding to a Partial Install.  I Had, Though, Checked 'Automatic Login'.
 
FaKA

---

### Post by FahvahKarol on 2011-02-20
> **kansasnoob said:**
> Shortly after you boot the Live CD you'll see a purple screen with two small icons at the bottom. At that point you have about 3 seconds to press any key and then you'll see a screen to select language, followed by a screen with 5 boot options, from there select "Check disc for defects". That usually takes about 4 minutes to complete so be patient.
 
If it passes it'll say, "no defects found" so next lets get a look at what you've done so far by posting the output of the Boot Info Script as described here:
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Alternative instructions for the script:
 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
The Two Icons Didn't Appear and Went to the 'TRY UBUNTU'/'INSTALL UBUNTU' Screen, So I'm Now In 'Try Ubuntu' and 'System Testing' Under Administration.  Going to Run the DISK TESTS First.
 
FaKA

---

### Post by FahvahKarol on 2011-02-21
Is There Another Way to Get To This Check Disk Program, kansasnoob?  The icons Don't Appear At the Bottom of the Screen.  It Just Goes to the 'TRY UBUNTU' and 'INSTALL UBUNTU' Screen.
 
FaKA

---

### Post by FahvahKarol on 2011-02-21
Here's What JohnnyVW Says About It:
 
"I'll have to look back at that again.  I did notice that a few folks were talking about checking the MD5SUM of the disc image.  Not easily done in your situation.  In a nutshell, each file has a certain MD5 key, MD5SUM prints out that key and you compare it to the key given on the Ubuntu download page.  Problem is, you downloaded the disc image in Windows, and you can't get to Windows to check that file.  It's just to check the integrity of the downloaded file...  to make sure it matches what you were supposed to download and that it's complete.

The other was a script that you can download.  A script is a sequence of commands that runs itself instead of you typing in all that stuff.  Not sure how that will help in your situation, but, it may give info that those guys can decipher."
 
FaKA

---

### Post by FahvahKarol on 2011-02-21
Here Is the Boot Info script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   622,069,759   622,067,712  83 Linux
/dev/sda2         622,071,806   625,141,759     3,069,954   5 Extended
/dev/sda5         622,071,808   625,141,759     3,069,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        fb708bf7-3e69-4bad-aecb-86909ff3bc98   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a333af7b-96f8-4cf5-b877-a76ac2cc78a3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/fb708bf7-3e69-4bad-aecb-86909ff3bc98 ext4       (rw,nosuid,nodev,uhelper=udisks)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fb708bf7-3e69-4bad-aecb-86909ff3bc98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a333af7b-96f8-4cf5-b877-a76ac2cc78a3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz

I Must Remind You.....I'm Just Learning This 'GEEK' Stuff and It Doesn't Make Much Sense to ME.


FaKA

---

### Post by FahvahKarol on 2011-02-21
Trying to Install Ubuntu AGAIN, (This Time Without the CAPS).  Seems to Be 'STUCK' At the Same Place....'READY WHEN YOU ARE'.  And THAT Seems to Be Asking For Some Sort Of PROMPT.  Anyone Know What THAT Would BE?
 
FaKA

---

### Post by Old_Grey_Wolf on 2011-02-21
> **FahvahKarol said:**
> My Computer Name 'Pavillion-dv4000-EC681AV' Was Placed In That Bar Automatically.  Do You Mean I Should 'Lower Case' Those Manually?  One Would Think the Program Would Clue One In On This Requirement.
 
Last Message:
Feb 21 00:17:01 ubuntu CRON(11035) :  (root)  CMD  (    cd / &&  run-parts  --report
/etc/cron.hourly)
 
Now Going to Try kansasnoob's Suggestion.  If I Can Get Into the TRY UBUNTU That Is.  When I First Booted With This Disk, It Went To the LogIn Page Which Suggests It Was Responding to a Partial Install.  I Had, Though, Checked 'Automatic Login'.
 
FaKA

I assume you get this page when installing, see attachment. Note that the "Your computer's name" and "Pick a username" are lower case.

---

### Post by FahvahKarol on 2011-02-21
> **Old_Gray_Wolf said:**
> I assume you get this page when installing, see attachment. Note that the "Your computer's name" and "Pick a username" are lower case.
 
Yes....Got That.
My Computer Name Automatically Entere As [name] Pavillion-dv4000-EC681AV, Then, When I Entered User Name, It Automatically Changed To fahvahkarol-dv4000-EC681AV, Which I THEN Changed to All Lower Case fahvahkarol-dv4000-ec681av.
 
Perhaps I Should Delete All But the fahvakarol?
 
FaKA

---

### Post by FahvahKarol on 2011-02-21
Here Is My GPart Page.  And Current Install.

FaKA

---

### Post by FahvahKarol on 2011-02-22
> **FahvahKarol said:**
> Here Is My GPart Page. And Current Install.
 
FaKA
 
There Have Been Some Notes Under 'Ready When You Are' Added Since. Several, In Fact. It Is Now At: Feb 22 **04: 17**: 06 ubuntu CRON (19430) : (root) CMD ( cd / && run-parts --report /etc/cron_hourly).
 
The PREVIOUS Two Were:
Feb 22 04:09:50 ubuntu ntpd(18997) :  sendto(91.189.94.4)  (fd=21) : Invalid argument.
 
AND
 
Feb 22 04:10:50 ubuntu ntpd(18997) :  Deleting interface #5 eth1, 192.168.2.4#1
 
FaKA

---

### Post by FahvahKarol on 2011-02-23
Still Running Ubuntu Install.  It's Been About 26 Hours Now I Think.  Got Additional and Varied Messages Under 'Ready When You Are' Until About 3 This Morning, Then the etc/cron hourly Thing Until I Got Up Today At 3pm, Then I Connected to Internet and Am Again Recieving an Additional and Varied Message, (Just Got Another One a Few Minutes Ago.).  If I Recall Correctly, The Download to Disk Was Something Like 19 or 20+ Hours.  So MAYBE Something Is Still Happening?  Anyway the Progress Bar Hasn't Moved a Bit In All This Time.
 
FaKA

---

### Post by FahvahKarol on 2011-02-23
Well the Only Messages Other Than the etc/cron hourly, Are 'kernel time sync, and I Think THEY Have to Do With From the Time I Connected to Internet.  Giving Up On THIS Install Attempt.
 
FaKA

---

### Post by FahvahKarol on 2011-02-23
Well....I Stopped the Ubuntu Install, but It Seems to Have Done What I Was HOPING It Would Do, ReInstall 'Boot textname', Cause I've Got WINDOWS XP SetUp Running, (Currently Formatting).  It Also Recognized The Precense of Partition 'F', but Not 'G'.  So We'll See.

FaKA

---

### Post by reikidude on 2011-02-26
Hi,

I installed 10.10. on my laptop. A friend asked me to install ubuntu on his laptop. I tried several times with the "READY WHEN YOU ARE" message appearing every time. then looked which processor he had  I have a 32 bit he has got 64 might that be the problem??

Martyn

---

### Post by reikidude on 2011-02-27
the different architecture CD did the same again a READY WHEN YOU ARE message. I have no clue to go further from this. 

Martyn

---

### Post by FahvahKarol on 2011-02-27
I'm Not Sure What I've Got Reikidude, But I'll Check It Out With JohnnyVW, Who Is Burning Another Disk For Me.  He Knows More About THIS Computer Than 'I' Do, But I THINK I've Got 32bit.

FaKA

---

### Post by Strolchi on 2011-02-27
Hi,
your installation process most likely stalls at or after the screen where you define user name etc.. The same happened to myself too. After a found out that you have to enter your data real fast (you can edit afterwords) your installation completes withou problems.
Hope that helps
Strolchi

---

### Post by FahvahKarol on 2011-02-27
> **Strolchi said:**
> Hi,
your installation process most likely stalls at or after the screen where you define user name etc.. The same happened to myself too. After a found out that you have to enter your data real fast (you can edit afterwords) your installation completes withou problems.
Hope that helps
Strolchi


Thanks Strolchi, I'll Keep That In Mind Too, When I Install the Disk That JohnnyVW Is Sending Me.  I Don't Want To Try With THIS Disk Any More, It May Have Been a Faulty Download On My Part, or I May Have Screwed It Up With the GPart In the Beginning.

FaKA

---

### Post by RancidJones on 2011-03-09
Hi there,

I'm installing Ubuntu on my MBP, which is one of last year's, 64 bit, so I know I downloaded the right thing,

But it came up with an error concerning the graphics, and then this same thing happened. The graphics error said it was aborting, and then it steamed on ahead nonetheless and seemed fine... Then after a while waiting at the same screen as fahvahkarol I thought it wasn't going anywhere so I turned off the laptop which then went a little loopy (black screen for a while, and it's now fine.)

Just wondered if you solved the problem?

---

