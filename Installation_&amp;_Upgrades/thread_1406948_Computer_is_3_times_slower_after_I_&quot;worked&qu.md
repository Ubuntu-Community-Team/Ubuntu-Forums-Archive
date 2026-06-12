---
title: "Computer is 3 times slower after I &quot;worked&quot; on it..."
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by jblaven on 2010-02-14
Well, 

So says my father.  He has an older computer that has XP and has been running very slow.  Some of the grand-kids have been playing online games and probably downloading all sorts of bad crap (spyware, etc).  My niece lives with them and I was setting up a wireless router for her laptop and ipod Touch.  The router is connected to his desktop.

His computer is an old HP Desktop. 

I also added a 40gig hard drive for ubuntu.  He is not much for change, (ubuntu is for the niece).  I figured it would give her her own place to explore and have access to software since she is hitting the teen years and will have a need to do reports, etc without getting into dad's stuff.

I swapped out the DVD-ROM trays for one that was not so dusty (as the current one wouldn't read the ubuntu CD I had).

So, I made 3 changes to his computer.  Can these changes really slow down Windows or is he just looking for something to pin it on?

The 3 changes are:

1. Added 40Gig HD for ubuntu
2. Installed and connected a wireless router
3. Swapped out a DVD-ROM tray

What do you guys think?  I am temped to remove his data files and do a re-format of his Windows HD and reinstall XP.

Since he lives a good distance from me, I am thinking about using the Remote Desktop to try and work on his computer.  

I know his computer is lacking in RAM, but I didn't think to make note of how much he has.

Other than installing the CD for the wireless router, I didn't touch Windows.

What do you guys think?

---

### Post by lucasart on 2010-02-14
Remove Windows, and install Ubuntu !

Ubuntu 10.04 alpha 2 is very good and faster than 9.10 I've found. Perhaps if the computer is old, you should install Ubuntu 8.10 instead, up to you. He won't need an antivirus antispyware and all these commercial placebos! Besides the combinations of these useless softwares and the Spywares and Trojan and Viruses that they fail to detect, make a Windows computer very slow.

Once you've installed Ubuntu, and before conecting to Internet, in the terminal a simple "sudo ufw enable" is enough to have far more security than in Windows.

Another misconception <<I figured it would give her her own place to explore and have access to  software since she is hitting the teen years and will have a need to do  reports, etc without getting into dad's stuff>>
From Ubuntu she will most certainly be able to have full read/write access on Daddy's files... But daddy on the other hand will probably not see her files (unless she chose an NTFS format): Windows is full of holes... It might "look nice" but behind the glitter hides a whole pile of crap...

---

### Post by phillw on 2010-02-14
If the aged XP machine does not have a 'decent' AV and the firewall enabled, it could well be full of nasties. AVG suddenly started having issues with XP (I used to use it for XP systems) I now use Avast! on them. also Spybot S&D would be handy to have.

There's some stuff on that in my Signature link, or directly to the Stickies in that little area by going to [http://www.vpolink.com/forums/99-Security-Stuff](http://www.vpolink.com/forums/99-Security-Stuff)  

Part #1 is an over-view, and Part #2 has the various links.

Whilst you can pretty much recover an infected Win installation, I'd still be minded to do a clean installation, provided you have a SP3 disk handy, else you can be infected before you've all the security updates !!! (I know where an ISO of SP3 is - if you need one - PM me)

As said, ubuntu is pretty kewl - if it is an aged machine, you may be better off with xubuntu - it's for machines with less than 256MB (you have to subtract your video RAM from the installed RAM - So, if it has only 256MB in, you're below what Ubuntu needs).
Xubuntu can run on 192MB as a LiveCD and it will install on a machine with 128MB, although this *can* go down to 64MB.

Regards,

Phill.

---

### Post by phillw on 2010-02-14
> **lucasart said:**
> Another misconception <<I figured it would give her her own place to explore and have access to  software since she is hitting the teen years and will have a need to do  reports, etc without getting into dad's stuff>>
From Ubuntu she will most certainly be able to have full read/write access on Daddy's files... But daddy on the other hand will probably not see her files (unless she chose an NTFS format): Windows is full of holes... It might "look nice" but behind the glitter hides a whole pile of crap...

'Daddy' could always encrypt his /home area with a password - even with root access, daughter can't read 'Daddys' stuff ;)

Phill.

---

### Post by Yogotiss on 2010-02-14
> **jblaven said:**
> Well, 

So says my father.  He has an older computer that has XP and has been running very slow.  Some of the grand-kids have been playing online games and probably downloading all sorts of bad crap (spyware, etc).  My niece lives with them and I was setting up a wireless router for her laptop and ipod Touch.  The router is connected to his desktop.

His computer is an old HP Desktop. 

I also added a 40gig hard drive for ubuntu.  He is not much for change, (ubuntu is for the niece).  I figured it would give her her own place to explore and have access to software since she is hitting the teen years and will have a need to do reports, etc without getting into dad's stuff.

I swapped out the DVD-ROM trays for one that was not so dusty (as the current one wouldn't read the ubuntu CD I had).

So, I made 3 changes to his computer.  Can these changes really slow down Windows or is he just looking for something to pin it on?

The 3 changes are:

1. Added 40Gig HD for ubuntu
2. Installed and connected a wireless router
3. Swapped out a DVD-ROM tray

What do you guys think?  I am temped to remove his data files and do a re-format of his Windows HD and reinstall XP.

Since he lives a good distance from me, I am thinking about using the Remote Desktop to try and work on his computer.  

I know his computer is lacking in RAM, but I didn't think to make note of how much he has.

Other than installing the CD for the wireless router, I didn't touch Windows.

What do you guys think?


Your best option would be to download the alternate Ubuntu of any edition. [Here]("http://releases.ubuntu.com/hardy/ubuntu-8.04.4-alternate-i386.iso") is the alternate download for Hardy Heron 8.04.4

**********************************************************
**********************************************************
***************Copied From The Actual Site****************
**********************************************************
**********************************************************
The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
setting up automated deployments;
upgrading from older installations without network access;
LVM and/or RAID partitioning;
installs on systems with less than about 384MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
In the event that you encounter a bug using the alternate installer, please file a bug on the debian-installer package.
There are two images available, each for a different type of computer:
PC (Intel x86) alternate install CD
For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
64-bit PC (AMD64) alternate install CD
Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.

---

### Post by phillw on 2010-02-14
> **Yogotiss said:**
> g;
installs on systems with less than about 384MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).


Is why I pointed the OP to Xubuntu, full GUI on low RAM
I didin't mention Lubuntu, that runs on less RAM than even xubuntu does - it's in alpha for release with 10.04

There's a ubuntu flavour for pretty much every computer :D

If the computer is 'up to it' there's edbuntu which has teacher locks to keep the kids from wandering off to far, as well !!!

Regards,

Phill.

---

### Post by jblaven on 2010-02-14
> **phillw said:**
> Is why I pointed the OP to Xubuntu, full GUI on low RAM
I didin't mention Lubuntu, that runs on less RAM than even xubuntu does - it's in alpha for release with 10.04

There's a ubuntu flavour for pretty much every computer :D

If the computer is 'up to it' there's edbuntu which has teacher locks to keep the kids from wandering off to far, as well !!!

Regards,

Phill.

That Xubuntu sounds interesting.  I'll have to check it out!

---

### Post by jblaven on 2010-02-15
OK,

So I am now typing this from an Emachine computer that has Xubuntu installed.  Runs nicely.  This is another computer I have, wanted to test it out before I give it a go on Dad's computer.

How realistic is it for me to expect to be able to connect to his Xubuntu machine from my Ubuntu machine through the internet so I can "see his desktop" and work on his computer?  It would be a huge leap and would make him MORE likely to give Xubuntu a shot.

I am thinking I will have to install more features to Xubuntu to make this work?  Will his slow computer keep this from working?  Thoughts?  Ideas?

Thanks,

Joe

---

### Post by Mencarta on 2010-02-15
I don't think you can install Ubuntu while using Remote Desktop Connection. It looks like you are going too need some gas money.

---

### Post by jblaven on 2010-02-15
> **Mencarta said:**
> I don't think you can install Ubuntu while using Remote Desktop Connection. It looks like you are going too need some gas money.


I would install it "in person", but Dad often needs "hand holding" with computer issues.  It would be nice to set it up so I could log in from my computer at home to fix/update his Xubuntu as needed.

---

### Post by Mencarta on 2010-02-15
Ya, but there is only so much you can do with Remote Desktop Connection. There are restrictions to prevent a malicious attack.

---

### Post by jblaven on 2010-02-15
> **Mencarta said:**
> Ya, but there is only so much you can do with Remote Desktop Connection. There are restrictions to prevent a malicious attack.

Is there a website you would recommend I read to get a better grasp on my options regarding connecting to his computer through the internet so I can work on it?

---

### Post by Mencarta on 2010-02-15
Ya, try this: [http://www.techiwarehouse.com/cms/engine.php?page_id=8118bf82]("http://www.techiwarehouse.com/cms/engine.php?page_id=8118bf82")

---

### Post by phillw on 2010-02-15
> **jblaven said:**
> .... Dad often needs "hand holding" with computer issues....

In that case, ensure he has a login name for this forum & you put a short-cut on the FireFox Bar !!

You may want to also install xchat, set him up a user name and show him how to get on the #ubuntu-beginners IRC channel. You can get 'live' help on there most of the time.

Regards,

Phill.

---

### Post by Mencarta on 2010-02-15
You need to show me that.

---

### Post by phillw on 2010-02-15
The easy way, for beginners, to get software, such as xchat is to use the Ubuntu Software Area (Applications --> Ubuntu Software Area) You can search by 'type' of application, or if you know the name of what you want, you can type that in, e.g. **xchat** and hit Return - It will then offer to install it for you.
Once on, you will find x-chat under Applications --> Internet.

Info, with screen-shots of setting it up is here --> [https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

If you tell it your favourite channel is **ubuntu-beginners** it will take you there when you start x-chat up.

Info on the Ubuntu Beginners Team can be found here --> [https://wiki.ubuntu.com/BeginnersTeam](https://wiki.ubuntu.com/BeginnersTeam)

You'll find various members of the Beginners Team popping on and off, so feel free to ask questions. (I'm a trainee - lol)

Regards,

Phill.

---

### Post by Mencarta on 2010-02-15
I have a problem when installing Ubuntu Desktop 9.10. My thread is [here]("http://ubuntuforums.org/showthread.php?t=1407470").

---

