---
title: "VitualBox - which to install-  'ose-guest' or 'ose'?"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Sky Aisling on 2011-01-01
Hello,

We've just installed** Lucid Lynx 10.04 **on a **ZaReason Strata 3660 with 4Gigs of RAM.**
We now need to install** Virtualbox** on Lucid Lynx in order to run WIN7 (standard edition retail version) in Virtualbox.

The package library lists two Virtualbox choices:  

Virtualbox-ose-source
Virtualbox-ose-guest-source
 
Which module do we choose?

The install of Lucid was fresh install with standard default partitioning.  

Thanks so much for your attention to our question.

---

### Post by lkraemer on 2011-01-01
Why don't you go download the PUEL Version of VirtualBox at
[www.virtualbox.org](www.virtualbox.org) so you have USB functional.
There are deb's for Ubuntu.  Just download the deb, and double
left click on it.  Then be sure to install the Windows Guest Additions.

Linux Hosts:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Read about Debian based Distrubitions & the FAQ.

lk

---

### Post by Sky Aisling on 2011-01-01
@ikraemer,

I have downloaded and installed the Lucid_i386.deb package.
(The ADM64 download gave an error of 'wrong architecture'?  You'd think with the ZaReason being a year old that it wouldn't need i386 architecture. But, what do I know?)

You write: 
  > Then be sure to install the Windows Guest Additions.I must be overlooking where Windows Guest Additions download is on [www.virtualbox.org]("http://www.virtualbox.org/").
Where is Windows Guest Additions download located?

---

### Post by ottosykora on 2011-01-02
this should be in the package you have downloaded, somewhere there will be an iso file with the name guest additions or so. You have to install from that the correct additional drivers.

---

### Post by howefield on 2011-01-02
> **Sky Aisling said:**
> I have downloaded and installed the Lucid_i386.deb package.

Did you also get the extension pack downloaded ?

> (The ADM64 download gave an error of 'wrong architecture'?  You'd think with the ZaReason being a year old that it wouldn't need i386 architecture.

Not necessarily to do with the machine capabilities., more likely it is because the machine has a 32 bit version of Ubuntu installed.

> Where is Windows Guest Additions download located?

You can install guest additions from the Virtual Machine menu once you have installed your guest system.

Just one other point, presumably you have downloaded version 4, for which there is no OSE vs PUEL versions to pick over, there is one basic package to download plus an extension pack which will give you the closed source features, including USB capability.

Sorry to complicate things ;-)

---

### Post by Sky Aisling on 2011-01-02
@ottosykora
Yes, thank you.  I discovered that. Out of desperation, I read the VB manual.  The manual is good.  And, it has big print.

@howefield
Thank you!  You clarified *not* complicated.  :)

I'm stuck on one small point which may be a mute question.

The sequence of events:

I downloaded and installed VirtualBox 4.0 for Linux hosts from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).
I created a virtual machine in VirtualBox.
Then,* thanks to howefield*, I remembered to download the extension package, exten pack (all platforms).[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).
There was no indication that the files had been installed or any questions of where to put the files.
I checked to see if exten pack files were in system, they are.
I checked VB menu and it doesn't look like they are there.  See screenshot.
QUESTIONS: 
Did the ext pack files install automatically into VB or do I need to do further work? 
Does it matter that the virtual machine within VirtualBox was created *before* I remembered to download the exten pack?

Also,
I checked to see of certain support files were present in the system via a tip from somewhere in the documentation.  They are.  (sorry, for the life of me I can't find the names of the 'supportive files'.  I'll come to me in the middle of the night. But, the point is, all's well there.)

I believe I installed the 64 bit version of Lucid Lynx 10.04.  That was my intention at install time.

Thank you, everyone, for all your help.

---

### Post by howefield on 2011-01-02
Taking your screenshot as a starting point, click on the little blue/yellow icon to the right of "version" and navigate to where you saved the downloaded extension package and press the open button.

You should then go through the installation wizard which should be self explanatory.

Once installed, the screen shot will look something like this...

---

### Post by Sky Aisling on 2011-01-02
Thank you.

howefield writes:

> Taking your screenshot as a starting point, click on the little  blue/yellow icon to the right of "version" and navigate to where you  saved the downloaded extension package and press the open button.Here is the sticking point.  The blue/yellow icon throws me to 'downloads' folder which is blank. (  See screenshot.)

I thought the download of extension pack files was successfull.  However, there was no indication after the download of the extension pack completed of where to place the downloaded files.  

Here also is a screenshot of a search for the extension files.

I will sit with this a while longer.  I must be missing something obvious.  Where did that download go?

---

### Post by Sky Aisling on 2011-01-02
Here is screenshot of the download box showing vbox-extpack file.
Here is screenshot of 11 files found for 'vbox-extpack'.

---

### Post by howefield on 2011-01-02
Not sure if you have downloaded the correct file, it certainly isn't the one you have highlighted in your screenshot.

Go here..

[http://download.virtualbox.org/virtualbox/4.0.0/](http://download.virtualbox.org/virtualbox/4.0.0/)

and download the second file from the top, the one that is named..

Oracle_VM_VirtualBox_Extension_Pack-4.0.0-69151.vbox-extpack

and note where you save it to :)

---

### Post by howefield on 2011-01-02
Ah you posted before my last reply, you have the correct file.

That's the one you need to navigate to.

---

### Post by Sky Aisling on 2011-01-02
I think this is what we are looking for.  :)

You wrote:
> Go here
[http://download.virtualbox.org/virtualbox/4.0.0/](http://download.virtualbox.org/virtualbox/4.0.0/)

and download the second file from the top, the one that is named..

Oracle_VM_VirtualBox_Extension_Pack-4.0.0-69151.vbox-extpac

This file downloaded into the 'Download' folder.

The download from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) did *not* download to 'Download' folder.

_Thank you so much._

Now,... Does it matter that I created a virtual machine in VirtualBox **before** I did this download of extpack?

---

### Post by howefield on 2011-01-02
> **Sky Aisling said:**
> Now,... Does it matter that I created a virtual machine in VirtualBox **before** I did this download of extpack?

No that won't matter, the extra functionality will be available to your previously created guests.

---

### Post by Sky Aisling on 2011-01-02
@howefield

Again, thank you.  Now, it is off to install WIN7 into VirtualBox.  This should be interesting.
Not sure I'm up to it tonight, but we'll try.

Already VB is floating mind-twisting words in front of me.  (See Screenshot)

I'll mark this thread 'solved'.

---

### Post by howefield on 2011-01-02
The dialogue is helpfully telling you what to do, if you choose the first option, see the attached screenshot for an idea on where to find the I/O cache option, you may find it is already set.

Or as the dialogue suggests, place the image file and snapshot folders on another disk, an ntfs one. It is actually a good idea to run VMs from a separate disk to the one that the host is run from, for reasons of performance. Not necessary, but preferable.

---

### Post by Sky Aisling on 2011-01-02
@howefield

You write:

> Or as the dialogue suggests, place the image file and snapshot folders on another disk, an ntfs one. It is actually a good idea to run VMs from a separate disk to the one that the host is run from, for reasons of performance. Not necessary, but preferable.Is this what is called creating a 'separate home partition'?
Is that a 'disk'?

Here's a screenshot of how the machine currently is configured by GParted.

---

### Post by Sky Aisling on 2011-01-03
@howefield

You write:

> The dialogue is helpfully telling you what to do, if you choose the  first option, see the attached screenshot for an idea on where to find  the I/O cache option, you may find it is already set.Here is how the Storage settings in VB are currently showing.
'Use host I/O Cache' is marked.
Does this mean the I/O cache option is 'set'?

The IDE Controller is empty.  I thought we just installed the extension package?

---

### Post by howefield on 2011-01-03
> **Sky Aisling said:**
> Is this what is called creating a 'separate home partition'? Is that a 'disk'?

A "separate home partition" is putting /home in a separate partition or disk to /. A default install of Ubuntu will create 2 partitions (as per your screenshot) - one for swap and one for everything else.

It can make sense to separate out /home as it makes reinstalling easier because you won't lose application settings and personal data, but it's a matter of choice.

I'm not sure that there is a performance benefit from separate /home partitions/disks, certainly not in the same way that you'd expect when running operating systems simultaneously.

---

### Post by howefield on 2011-01-03
> **Sky Aisling said:**
> 'Use host I/O Cache' is marked. Does this mean the I/O cache option is 'set'?

Yes.

> The IDE Controller is empty.  I thought we just installed the extension package?

The Sata controller is populated, with what looks to be your .vdi file, so no worries.

---

