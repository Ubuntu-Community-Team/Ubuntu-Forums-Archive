---
title: "Windows 2000 internetworking - Cannot see out or in"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by lcphill on 2008-03-09
Hello,

I installed ubuntu7.10 desktop as a clean install; I'm determined to make this work for me; I have the general desktop features working (firefox, thunderbird, sound blaster card works precariously nonetheless, scanner interestingly works, etc);

However, I cannot see out nor in over my windows network;

I have spent two full days this weekend, countless hours, scouring the forums to no avail; I have samba installed, pyNeighborhood installed, firestarter installed and nothing works; I simply cannot see out and I cannot see in from the outside [over the local network, that is];

Note that my windows 2000 local network is just fine -- I can see out and in no problem; It is only ubunu 7.10 that has no ability to be visible;

I have gone through the procedures on practically every thread in the forum to no avail; I have edited smd.conf, I have sudo'd just about everything and I'm getting no where. So, please don't send me on a runaround, I've been on quite a few over the last 48 hours; I'm literally exhausted; I can't believe ubuntu7.10, the latest release, is this horrific at such a seemingly simple task as internetworking;

One note, my host name:   phillips-ubuntu-1 gets seemingly truncated to phillips-ubuntu- when I look through "places" et al... Could it be my host name I chose from the very outside is causing a problem in that now it's being truncated?  Huh?

Thanks...

---

### Post by lcphill on 2008-03-09
Hello,

Some progress -- turns out, on my windows2000 boxes I am running zone-alarm firewall; It must be blocking something; I had to completely shutdown zone-alarm and then ubuntu would **see** in and out; But shutting down zone alarm on my windows 2000 laptop, I was able to use pyNeighborhood to connect to a share ('er, mount a share) [as user] and it worked; Not all good news, however...

Conversely, with zone alarm shut down on my win2k laptop, I was able to use network neighborhood to **see** that my ubuntu system existed... However, it had a very odd looking hostname entry:

PHILLIPS-UBUNTU1phillips-ubuntu1  -- obviously, something is amiss there... I suspect I need to edit something in smb.conf ????  Also, if I double click on the entry, I get "bad parameter" [go figure, I guess]; Worse yet, however, when I right click => properties, I get something a bit more ominous: ... (samba, linux) not accepting remote requests ...

Note - I also have firestarter shutdown on the server side, so I **believe** the request to connect from client to ubuntu/samba is getting through to samba, but it dies there (probably related to the wacked out hostname above) [noting I fixed the truncation, and vi'd /etc/hosts as the gui's didn't seem to fix that minor detail... go figure...]

Of course, one thing that bothers me is that I have to shutdown zone alarm on the client; I mean, since windows networking works just fine, that means samba is taking some sort of non-MS route and there apparently is no way to address this from within zonealarm -- which even if I get all this to work puts me in a non-useable scenario because I'm not living without a firewall just to share within my local network -- that's pretty much a non-starter for me...

SIgh ...

Is there a non-windows file sharing route I could go?  Like URL/ftp? ubuntu has got to support this with a bit more user friendliness? but, then again, after what I've been through, nothing on ubuntu seems easy... SIgh...

---

### Post by prshah on 2008-03-09
In ZoneAlarm, open ports 137-139 and 445. It will probably do it automatically if you select the service name samba.

In "gksudo firestarter", do the same, if you select service "samba" it will open up the ports for you. (Policy->inbound...->right click in Allow service section->Add rule... etc) You can initially set the source to "anyone", and once it is working, if your other computers have static IPs you can change "anyone" to the actual IP addresses.

Samba is a standard: there is no "non-MS-route" because then Samba will not BE samba, but something else.

Cheers,
PRShah

---

### Post by lcphill on 2008-03-09
Hi, until I can get something / anything to actually work, I'm just disabling firewalls for the time being ... If I can't get anything to work, what's the point / use?

I am consistently able to go from ubuntu [desktop file server] to win2k laptop, but that's not of interest to me; My main goal is to go from the laptop to the ubuntu desktop file server and that is inoperable:
A). I can not even **see** the ubuntu desktop server in network explorer unless I run pyNeighborhood and then ask for the ip address of my laptop,... at which point
B). An entry with a double host name shows up in my network neighborhood explorer, however it's useless in that it says "... (samba, ubuntu) is not accepting remote requests... go figure...

One more interesting item, from the samba var/log file(s):

==> log.nmbd <==
[2008/03/09 15:57:07, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server PHILLIPS-UBUNTU1 is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.100
  
  *****
[2008/03/09 15:57:18, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
  Unable to sync browse lists in this workgroup.
----------------------------------------------------------------------------------------------------------------------------

Ubuntu is just not ready for the masses... I'm ready to ditch windows internetworking and look for an ftp server or http server solution, because this is just ridiculous...

Well, appreciate the reply...

---

### Post by lcphill on 2008-03-09
Ubuntu-Samba is a nightmare;

I'm tossing this load and the partitions;

If I have to spend an entire weekend attempting to configure a sever using 'vi', that pretty much says it all... There is absolutely no way I would bank a migration strategy on this nightmare;

I still haven't figured out why my sound card is precariously perched on this platform, although I did see an outstanding bug report for it -- go figure;

I'm just going to have to bite the bullet, get an apple desktop/server and laptop and call it a future;

ubuntu-samba shouldn't bother with another release until a typical desktop setup doesn't require pouring through forums and man pages and configuration files and PDF documents to do menial tasks like mount an ntfs file system (which by the way STILL required me to 'vi' /etc/fstab to make THAT work -- how arcane is that?); Let alone stumble upon a terminal bug and have to simply give up with features that just don't work, although advertised to the contrary...

Good bye... Good riddance...

---

### Post by koenn on 2008-03-09
Given that windows networking was designed to work between Windows systems and nothing else, it's a small miracle Samba exists. 
And It actually works too, I use it all the time, at work, serving files for about 120 Windows users 

> Good bye..
bye.

---

