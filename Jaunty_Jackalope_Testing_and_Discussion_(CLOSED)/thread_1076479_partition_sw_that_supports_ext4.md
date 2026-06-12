---
title: "partition s/w that supports ext4?"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-02-21
I need to resize my home partition. 

gparted does not appear to support ext4 as of yet.  

Do I have any options at this time besides formating? 


thanks,

---

### Post by whoop on 2009-02-21
Are you using ext4 atm?

---

### Post by halfsane on 2009-02-21
^  yes, that's my dilemma

---

### Post by whoop on 2009-02-21
You could give partedmagic a try. I think the got ext4 support in version 3.5 and above. Have not tried that myself, though

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by autocrosser on 2009-02-21
What I've done is make the current gparted: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can do:
./configure --prefix=/usr
make
sudo make install

and it will replace the installed one you have with the most current one or goto debian's repositories and get the .deb--In any case--you need at least .42 or better to resize ext4 partitions.

There is a on-going bug report: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872)  about ext4 issues.....

---

### Post by Starks on 2009-02-21
gparted ppa for ext4

[https://launchpad.net/~surfaz28/+archive/ppa](https://launchpad.net/~surfaz28/+archive/ppa)

---

### Post by Slug71 on 2009-02-21
Well, i wonder what will happen with this. I can see a lot of people having trouble here if this isnt fixed with Jaunty Final.

And the problem is that we are passed Feature Freeze :-k

---

### Post by autocrosser on 2009-02-21
I don't know---I've been making a lot of "noise" on the bug report, so I "hope" the devs get the idea.......

---

### Post by autocrosser on 2009-02-21
> **Starks said:**
> gparted ppa for ext4

[https://launchpad.net/~surfaz28/+archive/ppa]("https://launchpad.net/%7Esurfaz28/+archive/ppa")


That's pretty good--the most current gparted is .43--adds a "bit" more stability--that's what I'm using.....

---

### Post by Starks on 2009-02-21
> **Slug71 said:**
> Well, i wonder what will happen with this. I can see a lot of people having trouble here if this isnt fixed with Jaunty Final.

And the problem is that we are passed Feature Freeze :-k

A gparted update would get a freeze exemption.

---

### Post by autocrosser on 2009-02-21
You might add some "noise" (constructively:) ) to the bug report....I am thinking about talking about it on dev-discuss list also. This really needs to be moved on---unless they have decided to remove ext4 support from the final 9.04:o:o

---

### Post by Starks on 2009-02-21
Which mailing list is covering this proverbial shitstorm in the making?

---

### Post by halfsane on 2009-02-21
> **autocrosser said:**
> What I've done is make the current gparted: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can do:
./configure --prefix=/usr
make
sudo make install

and it will replace the installed one you have with the most current one or goto debian's repositories and get the .deb--In any case--you need at least .42 or better to resize ext4 partitions.

There is a on-going bug report: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872)  about ext4 issues.....


thanks for the link, got it downloaded and installed.

Now, how the heck do I use it to resize my existing partitions without deleting them first?  Some messing around and I came to realize that I am a total noob to gparted.


basically nothing is available as far as editing my mounted partitions.  A shove in the right direction please :)



EDIT :  Looks like i need to use the live CD for what I am trying to do



 
Hopefully the capability make the final release one way or another.

---

### Post by halfsane on 2009-02-21
> **autocrosser said:**
> You might add some "noise" (constructively:) ) to the bug report....I am thinking about talking about it on dev-discuss list also. This really needs to be moved on---unless they have decided to remove ext4 support from the final 9.04:o:o

I just noticed that all the smiley faces in your post look kinda like your avatar!

---

### Post by MacUntu on 2009-02-21
Yes, you cannot manipulate mounted partitions and please make sure to backup important stuff. GParted never let me down but you never know.

---

### Post by halfsane on 2009-02-21
> **MacUntu said:**
> Yes, you cannot manipulate mounted partitions and please make sure to backup important stuff. GParted never let me down but you never know.

yeah, that was one hell of a ride.  The livecd was great and everything seemed fine at first.

Booted up fine and all the space on each partition checked out fine.  Then i tried to start up firefox and got an XPCOM error, so something wasn't right with xulrunner i found after a google using konqueror.

when i tried to run synaptic i was greeted with a couple of other package problems, something about missing endlines, i cant remember now.  I ended up deleting said problem entries from var/lib/dpkg/status


then ran apt-get update/ -f install and used defaults when prompted and all is well. (i think)  I had to loop through that a few times until it stopped complaining about problems.

I should have documented what went on, but I didnt think I would get back to this point.  I thought I had hosed things up pretty bad with my poking around.  :D



ok, 

here is a post, someone was in the same situation upgrading to 8.10 and this is what they did... and I did the same steps basically:
> 
hordur

Hello.
 
 I had a similar problem with another package.
 I spent a lot of time trying to fix and I finally managed to do it.
 Here's what I did:
 1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
 2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
 3. mkdir /var/lib/dpkg/info
 4. apt-get update, apt-get -f install
 5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
 6. rm -f /var/lib/dpkg/info
 7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info
 
 I don't know if all the steps are necessary, maybe 1 and 4 are enough.



---

### Post by autocrosser on 2009-02-21
> **halfsane said:**
> I just noticed that all the smiley faces in your post look kinda like your avatar!

Ya--Bill the Cat kinda' looks like that :o:o:o

---

### Post by autocrosser on 2009-02-21
> **Starks said:**
> Which mailing list is covering this proverbial shitstorm in the making?

Well--it "should" go on: [EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]  and yes, I expect it to be a mud-sling fest:(


I just sent in my post to the development-list & CC'd a copy to Colin Watson, so I am "hopeful" that some "positive" action will be taken (image of crossed fingers here)

---

### Post by autocrosser on 2009-02-22
Well--It was MUCH easier that expected---I sent an email to Colin Watson & his reply/my reply are as follows:

Thank you Colin!!!

I am sorry if I came off a bit "strong" :-)  I have helped a couple of people on the forums that needed the functionality in gparted & as I had not seen any indications come down the road----I figured I would trek down it myself.....  


Thank you for all you do--I know your plate is more that a bit full ;-) 

Cheers!!!
Dean Loros

On 02/22/2009 01:28 AM, Colin Watson wrote:[INDENT]   On Sat, Feb 21, 2009 at 06:14:10PM -0800, Dean Loros wrote:[INDENT]I have started to hear problems thru the Jaunty testing forum on  
ubuntuforums.org with the lack of support in gparted for ext4. There is  
a general bug report about gparted ext4 support at:  
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872)  and as  
gparted is currently at .43 at sourceforge.org, the PPA listed in the  
thread at: [http://ubuntuforums.org/showthread.php?t=1076479](http://ubuntuforums.org/showthread.php?t=1076479) is at .42-1  
and "official" Jaunty is at .39-1......I request that we exempt gparted  
from feature freeze to include support for ext4.
[/INDENT]Yes, it's already on my list and people can stop poking me about it :-)

I already pre-emptively got a feature freeze exception from Steve
Langasek. I've been delayed because there were other things on my plate.[INDENT]This will be very needed to move forward with ext4. It looks like ext4  
needs to be at least optional (if not default)
[/INDENT]We've already decided that it will be optional in Jaunty (and indeed it
already is, with the exception of gparted) and probably default in
Jaunty+1 based on testing.


So, there we have it---ext4 with support will be optional in Jaunty & default (image of crossed fingers!!!) in Jaunty+1!!!!
[/INDENT]

---

### Post by Slug71 on 2009-02-22
Nice work Autocrosser! :D

And thanks Colin! :D

---

### Post by autocrosser on 2009-02-22
It needed to be done my friend--And I do "tend" to be a bit proactive on topics that matter to me...I feel strongly about projects that enhance user experience and as this increases speed, adds a future defrag ability and makes the file system more robust........its really a no-brainer to push to adopt it as default--I know its still a bit rough around the edges and there are some corner-case problems but its still the best option to come along in quite a while.....

---

