---
title: "alternate install 9.10"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by mxmike51 on 2009-11-23
I am attempting to install 9.10 on my laptop. I have already tried the desktop and netbook versions with no avail. I have been running fedora cause I can't get the base system installed it says no media or mirror found. Uhoh it just started working. Well I am going to post anyway. Does any one know of a link to some good help with alt install? not where you have to sift through a bunch of useless info to find it! like @ 

[https://help.ubuntu.com/9.10/installation-guide/i386/getting-newest-doc.html](https://help.ubuntu.com/9.10/installation-guide/i386/getting-newest-doc.html)

I just need help with alt install not the very basic installer that my 7 year old know how to use.

I love the software but I hate the installer. I think the Debian people need to take a closer look at what the anaconda folks are doing!

Thanks in advance,

Mike

---

### Post by phillw on 2009-11-23
The reason the installer is made so a 7 year can use it, is for those people who are not familiar with installing Ubuntu. You are complaining that method is too easy, yet you find the alternate install - for doing specific things with a set-up  too difficult ?

An, as for tutorials ? apcmag have a raft of them, various combinations of windows & ubuntu.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

A lot of them refer to pre 9.10 ubuntu installs, so some will need altering for the re-building of GRUB2 when you are putting windows on AFTER a Ubuntu instal. The reccomended way is Windows1st, Ubuntu 2nd - but some people do have to do it 'back-to-front'

For those people, the rebuilding of Grub2 is covered here :

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

A good alternative to re-installing windows is to use virtalisation, you can put different operating systems on with this method - the information on that can be found over here -->
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)   This method saves the need to re-partition hard-drives.

Regards,

Phill.

---

### Post by presence1960 on 2009-11-23
> **mxmike51 said:**
> I am attempting to install 9.10 on my laptop. I have already tried the desktop and netbook versions with no avail. I have been running fedora cause I can't get the base system installed it says no media or mirror found. Uhoh it just started working. Well I am going to post anyway. Does any one know of a link to some good help with alt install? not where you have to sift through a bunch of useless info to find it! like @ 

[https://help.ubuntu.com/9.10/installation-guide/i386/getting-newest-doc.html](https://help.ubuntu.com/9.10/installation-guide/i386/getting-newest-doc.html)

I just need help with alt install not the very basic installer that my 7 year old know how to use.

I love the software but I hate the installer. I think the Debian people need to take a closer look at what the anaconda folks are doing!

Thanks in advance,

Mike

If you find that link "useless" I suggest to figure it out on your own. I can't help you because that is where I get a lot of my info...sorry but that is your choice.

---

### Post by mxmike51 on 2009-11-23
It is not too hard. It does not work!! I could probably write a better installer myself.

FYI I am a automation robotics engineer I write programs all day long just thought it would be nice if Ubuntu would work on my laptop. Maybe I will just switch over to Fedora on all of my machines

---

### Post by phillw on 2009-11-23
> **presence1960 said:**
> If you find that link "useless" I suggest to figure it out on your own. I can't help you because that is where I get a lot of my info...sorry but that is your choice.

not wishing to start a flame war -- but, at the end of the day, the wiki's are there for a deeper understanding of the innards of various tasks. For those not familiar with the finer points of installations etc. My advice is to learn to walk before your run. 
I used the default side-by-side vista / ubuntu install to get it on my system. After a while I felt comfortable enough to alter my partitions as I had faith in Ubuntu to be stable and handed over to it the responsibilities of my day to day computing. With the onset of 9.10 I chose the upgrade path. At EVERY stage I took a full backup. 

Linux is SO different to windows, take your time - I'm lucky, I have some background in UNIX from 20 years ago, so was not overly frightened of the console - They were just bringing 'X' out as the GUI as I left the UNIX environment. (Showing my age now !!).

Take your time, do not expect to know how to do things. Ubuntu allows you the freedom of choice - with that comes a responsibility to learn a little. If you are not happy in that environment then both Microsoft & Apple offer alternatives that "Do everything" for the user. As presence says - It's your choice - Ubuntu don't, however, charge you for trying it out ;)

I hope you get on with Ubuntu, I really like it. I agree there are still issues for new-comers, but massive strides have taken place in 9.10 in so far as installing software etc. We will always be hampered by propriatory drivers for things like WiFi / Graphics / Sound etc. until and unless those companies agree to release the code, even if not under GPL / GNU license, for it to be incorporated into either the kernel, or the repostitries. Some companies are making more progress than others in this respect.

Regards,

Phill.

---

### Post by snowpine on 2009-11-23
> **mxmike51 said:**
> It is not too hard. It does not work!! I could probably write a better installer myself.

FYI I am a automation robotics engineer I write programs all day long just thought it would be nice if Ubuntu would work on my laptop. Maybe I will just switch over to Fedora on all of my machines

Hi Mike, put on your engineer hat for a moment, and think "have I provided enough information for the 'robots' of Ubuntu Forums to help me?" 

So far all you've told us is "it does not work!!!" so don't expect a lot of helpful replies.

---

### Post by phillw on 2009-11-23
> **mxmike51 said:**
> It is not too hard. It does not work!! I could probably write a better installer myself.

FYI I am a automation robotics engineer I write programs all day long just thought it would be nice if Ubuntu would work on my laptop. Maybe I will just switch over to Fedora on all of my machines


Fighting against the instinct of "Don't let the door catch you on the way out" ... You have been provided with links to full tutorials for installing - If you let us know your robots, mebbie we could teach them how to use a set of instructions that work for 1000's of other people ?

Start with Windows -- undo all and partioning you have done. Put it back to a 100% windows machine.
Then, head over to the apcmag link & follow the instructions. It DOES work.

If, however you prefer to ask for assistance in where your attempt at the install is falling over - Then, as mentioned - "It doesn't Work" will get you no help from ubuntu, fedora, microsoft, apple et all.

As you 1st posted ... you don't like the instructions posted 'for a 7 year old' - yet, you didn't use them. If your customer came in screamed "Your robot sucks & doesn't work" and walked out ... It'd not be too helpful a diagnostic of the problem. That is the diagnostic you are giving us.

Regards,

Phill.

---

### Post by mxmike51 on 2009-11-23
hey folks usually I get a simple solution but I guess some of U cry babies got offended.

I installed on another machine with the alt install it worked fine so...

OS install the easy way...

Step 1 disassemble laptop

Step 2 remove hard drive

Step 3 place hard drive in docking station

Step 4 install Ubuntu

Step 5 replace hard drive in laptop

Step 6 reassemble laptop

Step 7 energize and boot laptop

Problem solved!! 

Thanks for nothing!1 All I was looking for was info on Alt Install not!

IF THE OS WASN'T FREE IT WOULD NOT HAVE BEEN WORTH IT!

I REALLY LIKE UBUNTU! ALOT! I JUST HAVE HAD SOME TROUBLE WITH THE INSTALLER!

I USE...

REDHAT

FEDORA

TRIXBOX AND OTHER OPEN PBX

UBUNTU IS THE ONLY ONE THAT I HAVE TROUBLES INSTALLING ON CERTAIN HARDWARE

BELIEVE ME I INSTALLED TRIXBOX ON THE SAME MACHINE. LIKE I SAID IN THE FIRST POST YOU FOLKS NEED TO TAKE A LOOK AT THE ANACONDA INSTALLER AND EMULATE. THEIRS IS BETTER... DON'T BE OFFENDED FIX IT! THATS WHAT I DO ALL DAY LONG! FIX OTHER PEOPLES SHTUFF! SEVERAL TIME I HAVE HAD TO GO TO EXTREMES TO INSTALL UBUNTU! BY THE WAY I PICK UP OLD COMPUTERS AND REFERBISH AND GIVE THEM TO KIDS THAT DON'T HAVE A COMPUTER! 

I HAVE INSTALLED UBUNTU ON MOST OF THEM!

THANKS TO ALL THE HARD WORKING PEOPLE DEVELOPING OPEN SOURCE SOFTWARE. I APPRECIATE IT VERY MUCH. IF I MIGHT SUGGEST YOU COULD DEVOTE A HELP SECTION FOR THE INSTANCES WHEN THE DEBIAN INSTALLER IS NOT COMPATIBLE WITH CERTAIN HARDWARE. MAYBE YOU ALREADY HAVE I SIMPLY COULD NOT FIND IT BECAUSE I WAS OVER WHELMED WITH PAGE AFTER PAGE OF HOW TO INSTALL UBUNTU. THANKS FOR MAKING IT SO THE VILLAGE IDIOT CAN INSTALL UBUNT. I REALLY THINK THEY COULD HAVE ANY WAY

---

### Post by snowpine on 2009-11-23
> **mxmike51 said:**
> hey folks usually I get a simple solution but I guess some of U cry babies got offended... LIKE I SAID IN THE FIRST POST YOU FOLKS NEED TO TAKE A LOOK AT THE ANACONDA INSTALLER AND EMULATE. THEIRS IS BETTER... DON'T BE OFFENDED FIX IT! 

Hi Mike, I think you are seriously misinformed about what the Ubuntu Forums are... I could emulate the anaconda installer until the cows come home, but all that will happen is people on the street will look at me funny. You are crazy if you think any actual Ubuntu developers are reading your rant; we here on the forums are all just volunteer everyday users like you. Glad you got the problem fixed (even though I never really figured out what it was). :)

---

### Post by mxmike51 on 2009-11-23
One more

i used a little utility called killdisk long before i posted 

once again you don't get it 

your installer does not work

i installed windows clean first it failed

i killdisked that writes 0000000000000 to the hd a lot of times k

then i tried to install ubuntu first it did not work

this is only a problem on a select few pcs. For the majority i have had no problems. 

I tried ten ways to sunday to install 8.04 8.10 9.04 9.10 it would not work. The anaconda installer did though. 

You would not be able to function in my world their would be very exspensive crashes then you would be looking for a new profession.

So don't try it

---

### Post by snowpine on 2009-11-23
> **mxmike51 said:**
> You would not be able to function in my world

My loss; best of luck building your robot army! :)

---

