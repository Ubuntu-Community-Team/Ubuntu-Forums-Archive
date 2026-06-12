---
title: "Debootstrap error on install"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by greenwom on 2005-04-21
Trying to upgrade to hoary (btw I'm a Linux newbee)

Burned the CD, install started

The first flag I get is couldn't configure the network
so I opted to "Not configure the network"

The install continues and I get 
  [COLOR=Red]Debootstrap Error[/COLOR]
Couln't retrieve bsdutils.

I followed the instructions in the error message  and re burned the CD at the slowest speed possible.   Anyone have this issue?

Warty worked first try so I'm lost  ](*,) 

PLEASE HELP

reran install The first  problem  again was 
Network autoconfiguration failed
network not using DHCP protocol

This is a stand alone machine, not connected to anything.

---

### Post by greenwom on 2005-04-21
I did co to the Vitual Counsol (CTRL_ALT _F3)  The last line is

cp: Read error: Input/output error


Prior to that line there are two others that raise a question

   File descriptor 6 left open
            No matching physical volumes found

few lines down

    File desciptor 6 left open
             No volume groups found.
   

DONT know if that means anything

---

### Post by az on 2005-04-21
[QUOTE=greenwom]Trying to upgrade to hoary (btw I'm a Linux newbee)

Burned the CD, install started

The first flag I get is couldn't configure the network
so I opted to "Not configure the network"

The install continues and I get 
  [COLOR=Red]Debootstrap Error[/COLOR]
Couln't retrieve bsdutils.

I followed the instructions in the error message  and re burned the CD at the slowest speed possible.   Anyone have this issue?

Warty worked first try so I'm lost  ](*,) 

PLEASE HELP

reran install The first  problem  again was 
Network autoconfiguration failed
network not using DHCP protocol

This is a stand alone machine, not connected to anything.[/QUOTE]
If you already had a running Warty system, you could have inserted the cd, added it to your synaptic repos and sis a dist-upgrade.

As it is, it would seem you have a bad cd, or the install kernel is havinproblems with it.

---

### Post by greenwom on 2005-04-22
Well, I don't know what the problem was.....

Two computers, two cd burners, 4 CD's, and 2 different downloads of hoary!!!

Same problem.

I then came to work downloaded the install again, burned the CD a BAM it worked....

Odd, Anyway now that I'm at work I can't get the box on the internet, I'll have to wait until I get home to tweaker.

Hoary looks cool so far, I just hope my WPC-11 Linksys card works out of the box.

---

### Post by Eau on 2005-04-22
I have the same problem on my end.

K\Ubuntu Live Cd works fine.

My errors is always during the Base Installation for both.

Debootstrap Error.....Couldnt retreive "Corutils"

I've tried burning about 5 different ISO's (all checked with MD5SUM)
I've tried low Burning speeds...

I've even tried ed_agamemnons idea for a network install while booting with GRUB with the similar results.

Ubuntu : Debootstrap Error.....Couldnt retreive "Bdsutils"

This is rather frustrating...any help is apreciated.

---

### Post by veritas366 on 2005-04-22
I had the same issue some time ago.  The only response you will ever get is that it is a bad cd.  While I think this answer does not always make sense, it is the one you will get...no matter how many md5sums you do.  I did, on the other hand, order the cd's and the install went perfectly fine.  I don't know why the Ubunut cd's are so hard to burn as it is the only thing I've ever had that didn't burn correctly....if that's even the issue!  

order some cd's right away and go get some fc3 or other distro iso's to hold you over.  Sorry to give you the bad news.

---

### Post by Levander on 2005-04-23
Probably a little more thorough way of checking the CD is I know that the hoary install CD has a "verify cd integrity" option or something like that.

To get to it, start running the install, as soon as you get to a menu that gives you an option to "Go Back" (and before you partition your disk damaging any data), select the "Go Back".  This brings you to a menu, where towards the bottom there is a "Verify CD" option, or something, don't remember the exact name.  

Try running that verify and see if it says your CD is okay if you're having problems with it.

---

