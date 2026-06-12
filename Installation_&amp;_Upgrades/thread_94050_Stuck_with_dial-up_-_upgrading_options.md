---
title: "Stuck with dial-up - upgrading options?"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2005-11-23
Good morning -
I have yet to enter a keystroke on a Linux machine.  Does that make me an uber-newbie?
I'm waiting on the Ubuntu CD's, and have the guinea pig computer ready for the injection.  The guinea pig will not be dual-booted.  Just Ubuntu on a clean 120GB HDD.  The existing M$ machine won't even know what's happening until I attempt to network them together.  
However, I can see the wall coming, and I want to ask this before crashing and burning.
I'm stuck with dial-up at home.  It appears that there will be lots of data that will need to be downloaded once Ubuntu's installed.  Dial-up is just not gonna work.  What are my options?  Below are the only things I can think of so far...

#1 - The network card in the guinea pig is listed as compatible in the Wiki - it won't be convenient but I can prob'ly find some way to jack into somebody's fast connection.  Would that be the absolute best solution?  Since I'm an uber-newb my fear is that I'll find someone I can impose on, bring the machine over, then won't be able to get the machine to connect.    
  
#2 - There's an awfully big pipeline at my workplace...is it possible to find out what I need to download, write it down, go to work, dump the files to a USB flash drive, then take that home and convince Ubuntu to look to the flash drive for the good stuff?  I would prefer to do this if it's possible.  Once I get the guinea pig up and running I should be able to network thru the M$ machine and go online long enuf to find out what it wants.  Is this even possible?  I mean, can I ask the Linux machine to generate a list of updates?  What about optional stuff like wine, dvd burn packages, etc.?

Anyone have any other ideas?  I've been haunting the forum for a coupla weeks now and haven't seen mention of this situation.  There's gotta be others w/out broadband...

---

### Post by adwait on 2005-11-23
Well, once you get the CD and have installed Ubuntu, there won't be a LOT of downloads. Some security updates once in a while and that's it and those can be handled with your dial up connection. When a new version of Ubuntu comes out (that happens every 6 months) you can again order a new CD. But if you absolutely must, I beleive it is possible to download the files on to a CD and then make Ubuntu use them.......I dunno how, but someones bound to know.

---

### Post by Bartender on 2005-11-23
Hi, adwait -
Thanks for the quick reply.  As I mentioned, I've been wandering thru the forums for a few weeks.  Just from the volume of posts asking about all kinds of things like wine and GIMP and dvd burning programs etc. etc. I thot there was a LOT of stuf to download.  I dunno how much of this stuff is stashed on the install CD's.  Hopefully some other folks will drop by and share some input on alternatives if any exist.
If downloads aren't huge, then dial-up will work for me.  Anything past about 10MB starts getting unwieldy and time-consuming and I worry about botched downloads due to interference on the phone lines.  I don't know if that's really much of an issue..

---

### Post by yesplease on 2005-11-23
#1 would work. You may consider to install with the modem connected, it will be automatically detected (best chances if it is not wireless).

#2 would work. You dont need the security updates when youre not connected. You will want the drivers for your videocard. There is a tool for package handling that is called synaptic. Over a dial-up connection it will show the packages and all the depndent packages.  Now you take note of that and download on a medium somewhere else. At home you add the CD or USB stick to your repostories and let synaptic install from there.

Dont worry so much :)  (Edit:, no offence meant ...)

Edit: This has some extra info: [http://ubuntuforums.org/showthread.php?t=94727](http://ubuntuforums.org/showthread.php?t=94727)

---

### Post by Mirko Scurk on 2005-11-24
[QUOTE=yesplease]#1 would work. You may consider to install with the modem connected, it will be automatically detected (best chances if it is not wireless).

#2 would work. You dont need the security updates when youre not connected. You will want the drivers for your videocard. There is a tool for package handling that is called synaptic. Over a dial-up connection it will show the packages and all the depndent packages.  Now you take note of that and download on a medium somewhere else. At home you add the CD or USB stick to your repostories and let synaptic install from there.

Dont worry so much :)[/QUOTE]

It's not worry in question. There is new kernel out and I hope that it will solve some of my hw problems!

There are, also, some libraries that I suspect are gonna make some of programs work better.

Does anybody know exact address where that new packages are downloaded if not anything else I will install them via dpkg?

---

### Post by Mirko Scurk on 2005-11-24
[QUOTE=Bartender]Hi, adwait -
Thanks for the quick reply.  As I mentioned, I've been wandering thru the forums for a few weeks.  Just from the volume of posts asking about all kinds of things like wine and GIMP and dvd burning programs etc. etc. I thot there was a LOT of stuf to download.  I dunno how much of this stuff is stashed on the install CD's.  Hopefully some other folks will drop by and share some input on alternatives if any exist.
If downloads aren't huge, then dial-up will work for me.  Anything past about 10MB starts getting unwieldy and time-consuming and I worry about botched downloads due to interference on the phone lines.  I don't know if that's really much of an issue..[/QUOTE]

Tnx, for directing me to this thread!

---

### Post by Bartender on 2005-11-24
Hi, Murko -
You're asking better questions than I am!  So, I thank you, since all I'm gonna do is hang out and see what sort of wisdom is imparted to us. ;)

---

### Post by adwait on 2005-11-24
I don't what you mean by the exact address....if you mean the URL from where they are downloaded its archive.ubuntu.com. If you are talking about where the files are downloaded on your computer its /var/cache/apt/archives.

---

### Post by Jeandré on 2005-12-07
[QUOTE=adwait]Well, once you get the CD and have installed Ubuntu, there won't be a LOT of downloads. Some security updates once in a while and that's it and those can be handled with your dial up connection. When a new version of Ubuntu comes out (that happens every 6 months) you can again order a new CD. But if you absolutely must, I beleive it is possible to download the files on to a CD and then make Ubuntu use them.......I dunno how, but someones bound to know.[/QUOTE]

I have an unreliable dial-up connection at home, but can download via ADSL and burn to CD at work.

I've upgraded from 5.04 to 5.10 at home from CD. At work I downloaded all the 5.10 security updates from [ubuntu-security-announce]("http://lists.ubuntu.com/archives/ubuntu-security-announce/"). At home I tried to add the CD with the updates as a repository in Synaptic, but it doesn't recognize it. Should I put some config files on the CD for Snyaptic to recognize it?

---

### Post by bwog on 2005-12-07
There is an option in Synaptic: Edit, add CD ROM. Did you try that?

---

### Post by Bartender on 2005-12-07
Hi, bwog -
I just dropped in on this thread and was surprised to see new posts.  Still waiting on Ubuntu CD's but will try Jeandre's and your ideas and get back here with results.  Might be a few weeks from now!

---

### Post by Jeandré on 2005-12-09
[QUOTE=bwog]There is an option in Synaptic: Edit, add CD ROM. Did you try that?[/QUOTE]

Yip:
[list=1]
[*]Inserted the CD which has all the 5.10 security updates.
[*]A file browser opened showing the .udeb and .deb file.
[*]I could display the text file I created and burned with the updates.
[*]Opened Synaptic package manager.
[*]Logged in.
[*]"Warning: w: couldn't stat source package" because I wasn't dialed in. OK.
[*]Clicked Edit in the menu, then "_A_dd CD-ROM...".
[*]"Please insert a disc in the drive.", OK.
[*]"Scanning CD-ROM".
[*]File browser with empty [media] [cdrom0].
[*]Error: "E: Unable to locate any package files, perhaps this is not a Debian Disc".
[*]"Add another CD?", No.
[*]CD-ROM icon not on desktop anymore.
[/list]

Didn't find any answers googling for it. I suspect that if I can create a package file Synaptic can recognize, it'll work.

---

