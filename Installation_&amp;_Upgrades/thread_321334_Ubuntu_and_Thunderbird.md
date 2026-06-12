---
title: "Ubuntu and Thunderbird"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by chejose on 2006-12-18
I recently installed Ubuntu 6.10 on a machine with windows XP. For some time I have used Thunderbird as my mail program.
But when I try to install it in Ubuntu a message says it cannot be installed on i386.
I am running a Pentium 2, so this should be an "i386" machine.
Is there a way around this problem, that is, to install Thunderbird/Ubuntu/Pentium?

---

### Post by wpshooter on 2006-12-18
How are you trying to install it ?

Are you installing it from Synaptic or from Add/Remove program or from some outside source ?

Not to be critical but if you are running XP on a PII, me thinks it is about time to get a bit better machine.

---

### Post by chejose on 2006-12-18
I was trying to do it from the graphical install program in Ubuntu. When I checked Thunderbird, the "can't install" sign came up.

And you are very right... it is a bit late here, and I should have put Pentium 4

---

### Post by wpshooter on 2006-12-18
When you say graphical install program are you referring to Synaptic and if so, does it not tell you that some other program installation dependencies are needed before Thunderbird can be installed ?

---

### Post by chejose on 2006-12-18
No, it simply says that the program cannot be installed on an i386 machine.

---

### Post by wpshooter on 2006-12-18
Then I would say something has gone wrong with your O/S installation.  Your machine, like you say should be 386.

---

### Post by aysiu on 2006-12-18
Can you post the output of these terminal commands? ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install mozilla-thunderbird
```

---

### Post by chejose on 2006-12-19
aysiu

I appreciate taking up this "problem". Last night I did some checking and noted that ALL the unistalled programs had the same notice: 

"AbiWord Word Processor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

I did what you suggested, and here are the results:

jose@jose-desktop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


jose@jose-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
35% [Connecting to ar.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

-> Note that it got this far and hung.

jose@jose-desktop:~$ sudo aptitude install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for mozilla-thunderbird
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Now that I see these results, I suspect that the solution is in the sources.list, but I still am to early in the game to experiment!!

Thanks again

---

### Post by tchoklat on 2006-12-19
try this.
 
here is the sources list shipped with edgy
replace your list with this and you should be OK
 
 
deb [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy main restricted
deb-src [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy-updates main restricted
deb-src [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy universe multiverse
deb-src [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy-backports main restricted universe multiverse
deb-src [[COLOR=#bd5900]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") edgy-backports main restricted universe multiverse

deb [[COLOR=#bd5900]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") edgy-security main restricted
deb-src [[COLOR=#bd5900]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") edgy-security main restricted
deb [[COLOR=#bd5900]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") edgy-security universe multiverse
deb-src [[COLOR=#bd5900]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") edgy-security universe multiverse

---

### Post by chejose on 2006-12-19
tchoklat

Very good. I did what you suggested and the "can't be done" messages disapeared.

What does not seem to work, though, is downloading.

First "add/remove" programs wanted to update, but after a long time a message came up saying it could not do it.

So I tried installing Thunderbird, but after some minutes the same happened.

So I guess I am closer to a solution, but something must still be lacking.

---

### Post by AlanRogers on 2006-12-19
> **chejose said:**
> So I guess I am closer to a solution, but something must still be lacking.Looking at your 'aptitude' output, it looks like the repositories are resolving to 1.0.0.0 which isn't right.

You should check the configuration of your internet/network connection. Post the output of ```
sudo ifconfig
``` and I'll see if I can point you in that direction too.

---

### Post by chejose on 2006-12-19
Alan:

Thanks for joining the struggle. :) 


OK... here it is. I had a hard time getting internet to work, so it would not be surprising if something is left dangling.


eth0      Link encap:Ethernet  HWaddr 00:50:FC:4F:E5:F9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe4f:e5f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1236075 (1.1 MiB)  TX bytes:157132 (153.4 KiB)
          Interrupt:193 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by AlanRogers on 2006-12-19
There doesn't appear to be anything wrong there so I'm guessing that you've got internet access sorted now. In a terminal window, if you run ```
ping ar.archive.ubuntu.com
```you should get the following response```
Pinging ar.archive.ubuntu.com [195.248.90.38] with 32 bytes of data:

Reply from 195.248.90.38: bytes=32 time=8ms TTL=49
Reply from 195.248.90.38: bytes=32 time=5ms TTL=49
Reply from 195.248.90.38: bytes=32 time=5ms TTL=49
Reply from 195.248.90.38: bytes=32 time=5ms TTL=49

Ping statistics for 195.248.90.38:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 5ms, Maximum = 8ms, Average = 5ms
```If you do, I'm afraid that I've had you barking up the wrong tree, for which apologies.

---

### Post by chejose on 2006-12-19
Alan:

I'm afraid that I got the same output as yours.

Well, you may have barked up the wrong tree, but at least you know where the trees are!!

But something that calls my attention, is that your address was ar.archive.ubuntu.com, while tchoklat in an earlier note in this thread give me instructions to remove the "ar." in from of the address in all of sources.list

Could that have something to do with it?

---

### Post by treris on 2006-12-19
> **chejose said:**
> Alan:

I'm afraid that I got the same output as yours.

Well, you may have barked up the wrong tree, but at least you know where the trees are!!

But something that calls my attention, is that your address was ar.archive.ubuntu.com, while tchoklat in an earlier note in this thread give me instructions to remove the "ar." in from of the address in all of sources.list

Could that have something to do with it?

The 'ar' in front of the url simply is the local (national) mirror of the ubuntu repositories, in this case argentina(??) using that or leaving that out really shouldn't make much of a difference, unless the local servers are down, in which case you could try for instance leaving the ar part out of the url or replacing it with for instance 'us' for the american mirrorserver

But because you got a ping result back from the local server I'm guessing they're just fine. 
Is there some way you could try using a different networkcard to access the internet? I've had weird problems with older computers in combination with networkcards too and sometimes just changing the networkcard made all the difference. 

Hope that works

---

### Post by AlanRogers on 2006-12-19
> **treris said:**
> I've had weird problems with older computers in combination with networkcards too and sometimes just changing the networkcard made all the difference.If he's got another one, it *may* be worth a go but I personally think it's a bit of a red herring - his internet connection is working fine or Ping wouldn't work at all.

I don't have much of a clue about Linux yet but IP connectivity I can deal with! He's connected, ergo the problem *should* be related to Synaptic/Aptitude/Apt-Get.

I'd suggest running with the suggestion of changing the mirror first.

---

### Post by chejose on 2006-12-19
Alan

Ok, modified the mirrors back to ar. but I am afraid that the results are the same. And just noticed that with Thunderbird at least, I am back to the original problem that started all this. I get the message: 

"XXX cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

That was solved... at least for a while.

Oh my, Linux. :(

---

### Post by AlanRogers on 2006-12-19
Sorry but I need to bow out at this stage then and leave it to the experts. We've ruled out your connectivity in general - it appears to be specific to the Repositories.

---

