---
title: "multisync-tools not available any longer after upgrade from Lucid to Maverick"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by patrickvdbemt on 2010-10-13
Hi all,
Until yesterday I had the Lucid environment running with my PDA (a WM6) synchronised with Evolution via Synce and the Multsync-tool.
After my upgrade to Maverick I do not have the multisync tools available any longer ($sudo apt-get install multisync-tools returns that the app is not available).
In my old config I could add libraries in the Synaptic package manager, however these are limited up to Lucid.
Please have a look at this website that enabled me to sync in my previous os : µ
[http://www.synce.org/moin/GuidoDiepen/NewUbuntuStuff/ModernDevice](http://www.synce.org/moin/GuidoDiepen/NewUbuntuStuff/ModernDevice)
[https://launchpad.net/~synce/+archive/ppa](https://launchpad.net/~synce/+archive/ppa)
Can someone please help me out of this as I am not that technical to do setups without a proper document base.
patrick.

---

### Post by TBerk on 2010-10-16
The question will be, in the short term,can we specify the Lucid Lynx 'version' and press-fit it into Meerkat Maverick.

I'm likely going to try that today, I'll report back...

TBerk
looking for the 'subscribe to this thread' link

---

### Post by TBerk on 2010-10-16
So far I've thrown every synce and multi-sync 'apt-get install' I can find and due to some missing apps/moduls/files all I have so far is a SynCE Tray Icon that can 'see' the pda. 

I'm still missing a sync function (which I'm not so in need of at the moment) but also missing is the ability to browse the device w/ Nautilus, etc.

So, (and yes my post is lacking specifics at the moment...) I have half an install.


TBerk
PS- my pda is running WinCE 2003

---

### Post by patrickvdbemt on 2010-10-21
Hi there,
indeed as you state the Synce icon is available, I can open the PDA file system so have access to the files stored on it. However the addresses and calendar synchronisation is more or less a backup for my PDA as well, and therefore I am hoping that soon the msynctool becomes available one way or the other.
I will be patient and check the forum threads day by day.
Patrick.

---

### Post by rplantz on 2010-10-24
Yes, this is very strange. I note that multisync 0.90 has been available in the last couple of releases, but 10.10 has dropped it, along with multisync-tools. In previous versions, I used multisync and unison to sync my evolution on two different computers (desktop and laptop). I haven't tried the older multisync (0.82), but it's weird that 0.90 is missing.

---

### Post by patrickvdbemt on 2010-10-25
And this is very frustrating. We try to get more and more people away from Micro$, situations like this do not help us at all and might have a negative impact. A new release should always build on the previous one and guarantee backwards compatibility as maximum as possible.
I am not sure how the releases and developments in the O S community happen, and I appreciate that this has all been put together by many "volunteers". I am not that technical and have no clue about the details. But that does not mean I do not put question marks right now.:confused:
Nevertheless I am very happy with 10.10 although it has got an additional problem with the video card (accelerator does not seem to start and returns an error while starting up the system).
Looking forward to see fixes on both of these issues. Now I am happy, after the fixes I might be proud again to run Ubuntu.

---

### Post by pgoffa01 on 2010-10-27
I'm banging my head on the wall trying to sync my blackberry with evo.  No multisync means no open sync means no barry.  AHHHH  

I just want to browse my blackberry, sync to evo or thunderbird, and tether.

I agree, Win 7/Vista/XP/2000/Server 03 and 08 were so easy.  Come on Canonical!

---

### Post by davidoff01 on 2010-10-28
Hi,

this bug (or whatever it is) also affects me.
I´m going mad while trying to sync my mobile to evoluton.
I started using Ubuntu with 8.04.
I´m syncing since 9.04 and until 10.04 this was running fine.

I tried to be a little productive and reported this issue as a bug to launchpad.

[https://bugs.launchpad.net/ubuntu/+source/osynctool/+bug/665909](https://bugs.launchpad.net/ubuntu/+source/osynctool/+bug/665909)

but it is still new, unconfirmed and unassigned.
Maybe someone else need to confirm that this is a bug ?

However in the meantime I discovered that the msynctool was only renamed to osynctool. So don´t get confused when reading the bug report.

I hope this will help to solve the issue soon.

---

### Post by TBerk on 2010-11-07
There seems to be two parts to this;

1) Getting the PDA (PocketPC, WinCE 2003 in my case) 'seen' by Ubuntu 10.10, that is having the OS treat the external unit like any other USB connected storage device. This would allow file transfer w/ ease and perhaps apps/util loading despite it not being an MS OS. An offshoot of this might be a Linux based app installer.

2) The other part is actively supporting 'Syncing' either through a stand alone app or optimally whatever Calendering/Phone-book/Contacts, etc app of your choice. 

Having the ability to browse the PDA is more useful to me, personally, but getting sync'ing going would support a wider group of people I'm sure.

So basically I'm hoping to help define two goals of mine; PDA Browsing & PDA Syncing. And a thread bump never hurt too much.

One question through; Can a retrograde install be supported by the current OS version? 
What I mean is, would a PDA install for Ubuntu 8.04 or 9.10 etc, work on Meerkat Maverick?


TBerk

---

### Post by Pieuga on 2010-12-19
> **pgoffa01 said:**
> I'm banging my head on the wall trying to sync my blackberry with evo.  No multisync means no open sync means no barry.  AHHHH  

I just want to browse my blackberry, sync to evo or thunderbird, and tether.

I agree, Win 7/Vista/XP/2000/Server 03 and 08 were so easy.  Come on Canonical!

Same situation trying to sync calendar and contacts from win CE 6 and Evolution. 
I tried for long time since I've upgraded to the "perfect" 10 and I've read a lot of discussion without resolving nothing.
I've also tried with synce-kpm: all relationship with the mobile seems OK
the first time a new relationship is created a syncronisation is performed (a lot of contact and calendar events where counted...) but nothing really happens...](*,)

Next step seems to be downgrade to 10.04? :confused:
Nobody have any better ideas?

best regards

---

### Post by revtds on 2011-01-08
The issue appears to me, or to my limited knowledge, to be that the developers decided that syncing with pdas with Palm OS on them was not to be supported anymore.

Imagine my surprise when I could no longer create expense reports, sync calendars, addressbooks, or memos with my PDA which I have done for over 8 years now.

The conduits are missing in gnome-pilot/Evolution to make the connection.  My Handspring Visor will do a back-up, but nothing else

I found someone who had written out how to compile and install gnome-pilot 2.32.0 and the associated conduit file, so I now have the latest version of gnome-pilot running, but I have lost the ability to connect with the pda for some reason. Conduits are all there, but no connection can be made, so there is still something missing.

I assume that multi-sync and synce have met the same fate, and therefore a downgrade to Lynx is rapidly appearing to be the only tenable solution that I can find.  Someone else did compile Evolution 2.32.0 for Maverick, but it is for 32bit, as far as I can tell, and I am afraid to try it, until I find out more.

Good luck. I will check back if anything breaks my way, or to see if anyone else gets an answer.

Link to compiling 2.32.0 pilot [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/569601]("https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/569601")

---

### Post by revtds on 2011-01-08
After posting the above info, I continued to read for a while, found nothing, and left the forum.

I decided to try one last time to sync my pda, and this time it connected, allowed me to set up the conduits I wanted, and then did a full sync, with backups, sync of all calendar, memo and address book and time.

I did nothing that I am aware of, but it now syncs perfectly with no warnings or errors.

Apparently, upgrading gpilot and conduits has worked.

I will lock those apps, and hopefully they will stay that way.

And I say again, Good Luck! It worked for me, and I hope it helps someone else.

---

### Post by dart80 on 2011-03-11
If you navigate to the following site, you just might find your desired dependencies.

[http://pkgs.org/](http://pkgs.org/)

---

