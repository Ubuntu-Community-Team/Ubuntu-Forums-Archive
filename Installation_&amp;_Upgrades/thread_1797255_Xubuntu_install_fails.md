---
title: "Xubuntu install fails"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-07-04
Hi,

I was trying to install Xubuntu alternate install (tried regular Xubuntu before that) and I get an error message something about debootstrapper failed to load or something like that. It says in the error message I can look at virtual terminal at F4 so I go to that but I'm not sure what it't talking about or what I can do to get a clean install. I took a picture (attached) of the virtual terminal message at F4 but couldn't get out of it to get one of the original error message (tried "exit" ctrl+alt_F7, esc, everything). Below are some details about the system I'm trying to install on.

```

HP Pavilion 6350
A dinosaur that prob really belongs in some museum not under someone's desk.

~ RAM upgrade: 256 mb of sdram @ a lighning fast 100 Mhz!  :D

~ Disk: Quantum Bigfoot TX8.0AT weighing in at a whopping 7.49 GB
  - never seen anything like it before. It has this odd looking, huge, [weird], card
looking thing sticking out the side of it and it makes these god awful noises when
it runs. It's been checked out pretty thoroughly though and appears to be healthy.
I think that's just how those drives sounded back then (you know, back before there
was dirt).

~ CPU: a Pentium Celeron 800 Mhz (Ooooo . . . The Glory!)  :p

~ Mobo: Don't recall the specs on this one. I do remember it was some obscure thing
and most things (like graphics and sound) are on-board.

=> Has a NIC and it works. Surfed the net for few minutes this morning.
=> Has some other weird expansion card I don't know what it is. Has a (com port?)
on it.

```

If anyone can help I would sure appreciate it.

Thanks.
:confused:
-----------------------

Edit:

Sorry guys. Forgot pic till just now. There ya' go.

---

### Post by mörgæs on 2011-07-05
With 256 MB of memory, I would go for Lubuntu rather than Xubuntu.

---

### Post by Jose Catre-Vandis on 2011-07-05
Dodgy CD / CD rom ? Have had similar problems on an ancient laptop with only 192mb ram.
 
Try the minimal install:

Boot the CD
Select Language
Press F4
Chose Command Line Install
Install Xubuntu

Uses the same installation routine but no desktop. Then once running you can install xubuntu-desktop.

---

### Post by Toz on 2011-07-05
Looks like a faulty hard drive as well:> Jul 5 00:33:48 kernel: [274.099996] end_request: I/O error, dev sda sector 458664

---

### Post by faria2159 on 2011-07-05
i have this kind of problem too. thanks all of them who answered the question. It helped me a lot.

---

### Post by ClientAlive on 2011-07-05
> **Jose Catre-Vandis said:**
> Dodgy CD / CD rom ? Have had similar problems on an ancient laptop with only 192mb ram.
 
Try the minimal install:

Boot the CD
Select Language
Press F4
Chose Command Line Install
Install Xubuntu

Uses the same installation routine but no desktop. Then once running you can install xubuntu-desktop.


Is the minimal install the same as the "alternate install cd" mentioned about half way down the page here?

[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/)

I tried the regular and that one but I'll try the install from terminal like you mention.

Also, is the script:

```
apt-get install xubuntu
```

then

```
apt-get install xubuntu-desktop
```

???

But wouldn't those codes look for something in a repo over the internet?

I'd have it coming from the cd.

I don't understand.


> **mörgæs said:**
> With 256 MB of memory, I would go for Lubuntu rather than Xubuntu.

If the terminal install doesn't work I'll have to try this I guess.


> **Toz said:**
> Looks like a faulty hard drive as well:

I have another hard drive but I'm not sure if it is compatible. The other one is an ide drive; and, I think, the one in it is a scsi. Also, by the design of the case, I'm not sure how I would mount the other drive. I'd McGuiver it but I don't really have the tools for that.


I have like 3 computer's sitting around here but they are all messed up in one way or another. The deal was I recover any data from the drives that I can, try to get one fired up to give back to the guy, and I can have what's left. Well I don't really have the equipment to diagnose these things; and, even if I did, may not have replacement parts to make a working one.

Arrrghhh . . . What can you do? Maybe the other, Gateway machine will fire up. I don't know.

Thanks for all the help guys. I'll let you know how it goes.

---

### Post by ClientAlive on 2011-07-05
I noticed something odd in the screen I see at boot up. I had changed the boot order in bios when I started working on this thing just to make it more convenient to boot from cd. I know that the changes I made had nothing to do with primary/ slave though. Just boot order.

Basically, in that initial boot up screen, it looks like it's calling that hard drive a "slave". I'm not sure if this is because of the changes I made to the boot order (a software reason) or because of a jumper setting on the drive (a hardware reason). Since this is an older machine I imagine it's possible the way the did things with it are not the same as they do these days. (In other words, maybe the boot order in bios is the reason for it calling the hd a slave). This hard drive is very odd looking (very old) it doesn't look like the kind of hard drives you see today. It has a board sticking out the side of I noticed something odd in the screen I see at boot up. I had changed the boot order in bios when I started working on this thing just to make it more convenient to boot from cd. I know that the changes I made had nothing to do with primary/ slave though. Just boot order.

Basically, in that initial boot up screen, it looks like it's calling that hard drive a "slave". I'm not sure if this is because of the changes I made to the boot order (a software reason) or because of a jumper setting on the drive (a hardware reason). Since this is an older machine I imagine it's possible the way the did things with it are not the same as they do these days. (In other words, maybe the boot order in bios is the reason for it calling the hd a slave). This hard drive is very odd looking (very old) it doesn't look like the kind of hard drives you see today. It has a board sticking out the side of it.

Also, I think in that first boot screen it's calling it an ide drive. I thought, from some of the diagnostic tools I ran on it before, that it is a scsi1 type drive though.

I've attached pics of the initial screen I get upon booting up and of the various settings screens in bios/ cmos. I wonder if someone can take a look at them for me and let me know if anything stands out as being odd or out of place.it.

Also, I think in that first boot screen it's calling it an ide drive. I thought, from some of the diagnostic tools I ran on it before, that it is a scsi1 type drive though.

I've attached pics of the initial screen I get upon booting up and of the various settings screens in bios/ cmos. I wonder if someone can take a look at them for me and let me know if anything stands out as being odd or out of place.

---

### Post by mörgæs on 2011-07-05
The minimal ISO is, as the name says, minimal. You can download it from here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

When the installation is finished, just run
```

sudo apt-get install lubuntu-desktop
```(or xubuntu-desktop)

Have patience during this step! 

The alternate ISO is close to 700 MB like the regular one. The only difference is, that the graphics is coarse and that it takes less memory during install.


Always remember to have wired internet access while installing.

---

### Post by Jose Catre-Vandis on 2011-07-05
Sorry. When I wrote minimal install I meant the command line installation that you can do with the alternate CD, which avoids loading all the graphical stuff.

And yes, when you then type "sudo apt-get install xubuntu-desktop" it will call it from the repos online and not from the CD.

My aim is to get you setup with an installation.....

---

### Post by ClientAlive on 2011-07-05
> **Jose Catre-Vandis said:**
> Sorry. When I wrote minimal install I meant the command line installation that you can do with the alternate CD, which avoids loading all the graphical stuff.

And yes, when you then type "sudo apt-get install xubuntu-desktop" it will call it from the repos online and not from the CD.

My aim is to get you setup with an installation.....


Thanks man. I want that too. I have to do some other things for a few hours but I'll try to come back to it later tonight. Thanks for checking on me.
-------------------

Edit:

Forgot to mention, thing won't boot from cd now (any cd). After initial boot screen I just get a screen with the cursor just sitting there blinking. After about 10 min I figure it's not gonna boot anything so I just shut it down. There's some things I think I know to check out and I'll do that when I come back to it later tonight. Just that it doesn't make sense how all along it boots these live cd's fine (several of them - I've ran like 3 diff ones in it). I even used Ubuntu 10.04 live to copy the data off the disk before wiping it and going after an install. Now, last night, I unplug everything, hook up one of the other computers to check it out, swap back to this one this morining, and I get this - where it isn't even booting the cd. Nothing has changed. All I did was plug a different computer into the periferals to check it out and then back to this one this morning. This kind of thing doesn't make sense to me. What, do I have gremlins in my house or something?!
------------------------

Edit 2:

Well my circumstances changed. I'll be able to work on it for a couple more hours before I have to go.

I'm running a test from the Ultimate Boot Cd on that drive. So far the things it's tested for have come up as "passed" but it's still in progress on the last one.

I don't know how it happened but when I looked more closely at the bios settings again they were back to the default. I changed them back (setting the cd drive as the primary boot device/ first boot device) and it's booting from cd fine again. The only thing I can think of is that something in the Xubuntu install changes the bios settings but I don't see how it could. Either that or the machine being unplugged from the power cord over night. This is one thing I just can't wrap my mind around.

I'll see what the test results come back as then try to do a minimal install from the command line as has been suggested. (If no obvious problems with the disk show up). I'd like to run a couple tests on it first though and then go from there.

Thanks.

---

### Post by mörgæs on 2011-07-05
Now I saw the pictures... Whoa, I used to have a computer with this BIOS. 

When everything is running well, you can squeeze a little lag out of the system by lowering wait states (or wait cycles). Be careful, because it can also make the system unstable.

---

### Post by ClientAlive on 2011-07-05
> **Toz said:**
> Looks like a faulty hard drive as well:
> 
Jul 5 00:33:48 kernel: [274.099996] end_request: I/O error, dev sda sector 458664




Looks like you were right. A diagnostic on the disk came back as failed; or, as it said in the summary, " . . . is failing". Guess that's why it was making all those weird noises.

I have another driver here but I don't know if it will work with that mobo. As I mentioned before it doesn't look the same; and, I thought, is of a different type. Guess I can plug it in and see what happens. I don't see how things can get worse - only better.

If that drive does work I'll have to figure out some way to mount it in the case. Unless someone has a little experience with this situation and has some better idea I guess id just have to McGuiver it and bolt it down however I can.

Anybody got some zip screws?!

I'm kidding . . .   :D

---

### Post by ClientAlive on 2011-07-05
If I had a hammer I can think of a really great use for it right now.

:evil:


I don't know what the hell HP was thinking when they built this machine - this this is made like a tank. It's virtually impossible to get into anything in there - let alone get that old drive out or put a diff one in. This is ludicrous!

---

### Post by overdrank on 2011-07-05
> **ClientAlive said:**
> If I had a hammer I can think of a really great use for it right now.

:evil:


I don't know what the hell HP was thinking when they built this machine - this this is made like a tank. It's virtually impossible to get into anything in there - let alone get that old drive out or put a diff one in. This is ludicrous!

The hard drive will slide out the back of the drive housing and the cd drives out the front of the case. :)

---

### Post by ClientAlive on 2011-07-05
> **overdrank said:**
> The hard drive will slide out the back of the drive housing and the cd drives out the front of the case. :)


I don't see how with this particular case/ construction.

See pic.

These people really did a doosey when they made this thing!

In addition to how tight everything is packed - the drive is fastened in somewhere else that I can not identify. Perhaps there is an additional screw on the side between the back wall and the carriage the drive rests in - not sure. I could not feel anything by running my fingers along that back edge though. I tried to get the plastic cover off the front; and, thought that tabs are designed in such a way to make it really tough on you, managed to deal with them. That didn't seem to matter though, as the front, plastic cover is also attached in some other way as well. I with you could see this thing. I really do. It's truly amazing - I don't think they meant for it to ever come apart again.
--------------------

Edit:

Am I missing something here overdrank?
-------------

Edit:

There's rivets all over this thing - clearly put there by the manufacturer/ in the manufacturing process - too!

---

### Post by ClientAlive on 2011-07-05
I'm starting to get that funny feeling that something's about to get broke . . .:twisted::twisted::twisted::twisted::twisted::twisted::twisted::twisted:


----------------------------

Edit:

I can't even begin to describe what I'm looking at right now. I managed to muscle a couple of the plastic covers off the front cover; and, eventually, identify what is holding the drive in there. Apart from a sawzall I can't see how this thing can ever be removed.

I suppose that if the drive itself is bad it doesn't really matter if it is destroyed in the process of removing it. I do however, need to the case to remain relatively in tact that I might still mouth the other drive.

Thanks HP - I'm really feelin' the love now!

---

### Post by overdrank on 2011-07-05
You may have to remove the floppy drive to see if any screws are beneath the hard drive. I think I remember having a quantum bigfoot hard drive that was attached like that one time.

---

### Post by ClientAlive on 2011-07-05
> **overdrank said:**
> You may have to remove the floppy drive to see if any screws are beneath the hard drive. I think I remember having a quantum bigfoot hard drive that was attached like that one time.


Thanks man. I managed to get a couple pieces off and discovered what is holding the drive. Problem is that what's holding it is absolutely not accessible. I ultimately decided to just lay the other drive in there loose and plug it in - to see if it was going to work for that computer. I know the drive is good because I ran diagnostics on it before (in my own desktop that does work). The mobo would not recognize the drive. I don't think that mother supports ide.

I got tired of fiddling with it. For what it's worth, I'm crossing the line of labor/ payoff here. After discussing it w/ the guy we decided to just call it a wrap with the data recovery.

So, sorry guys. I appreciate your help and I'm sure the information will come in useful in the future. This one's a wrap though.


Be blessed fellas. See you around on the forum.

Jake

---

