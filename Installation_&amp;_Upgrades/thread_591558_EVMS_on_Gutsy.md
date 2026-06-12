---
title: "EVMS on Gutsy?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by sfaoldun on 2007-10-25
Hi all,
Quick question, as I haven't been able to find a definitive answer anywhere on google or these forums - does the Gutsy live CD come with EVMS on it or not? My system is thoroughly broken and I'm tempted to do a complete reinstall, but I don't want to find I can't get at my homedir and such ...

I should perhaps mention I DO use EVMS, so the "fix" of removing it isn't ideal. ;) -- I found mentions of upgrade-bugs.

Thanks!

---

### Post by Glowing Fish on 2007-10-25
What I was told was that evms was a holdover from Dapper, and that it was almost totally broke on anything fiesty or post. In fact, I was told this when I was asking why udevd was taking up all my system resources when I first started. I was told to do an apt-get purge of evms, and that solved that particular problem.

That is mostly what I know. But you should probably wait for someone who knows more than me to answer!

---

### Post by peitschie on 2007-12-17
*bump*

I'm having this issue too!  I used EVMS to set up a RAID1 array, and a linear raid array.  I am now unable to boot... I'd like to reinstall Gutsy, but the problem is I have no idea how to setup and restore the RAID devices under Gutsy.  Can anyone help?  Will doing the 'aptitude purge evms' lose all my RAID information?

---

### Post by peitschie on 2007-12-18
For those who are interested, EVMS data is stored on the drives, so purging evms off the system doesn't delete this!  It does however mean the drivers become no longer accessible if they were EVMS only mapping.

To get around this problem, I found it easiest to remove EVMS and simply use mdadm for control and creation instead.  To do this, 
[LIST=1]
[*]I booted the system using [SystemRescueCd ]("http://www.sysresccd.org/Main_Page") which has EVMS installed on it.  This allowed me to run the EVMS CLI.  (theoretically this is also possible using the Gutsy LiveCD.  Except this then requires the LiveCD to have an active internet connection so evms can be installed on it)
[*]I then followed instructions in the [EVMS manual here]("http://evms.sourceforge.net/user_guide/#evmstocomp") to convert my EVMS partitions to LVM compatible partitions (i.e., they map to /dev/md/md[0-9] rather than /dev/evms/).
[*]I rebooted the system, and this time booted using the Ubuntu Gutsy LiveCD
[*]Following instructions found in [the forums here]("http://ubuntuforums.org/showpost.php?p=3596917&postcount=4"), I removed evms, updated any other packages etc.
[*]Rebooted the system, and using the mdadm man pages ([online copy]("http://man-wiki.net/index.php/8:mdadm#EXAMPLES")) I followed 7th example roughly to create the appropriate mdadm.conf file
[*]Reboot again and viola... all works again.  Then I just needed to reconfigure fstab to use the new mdadm devices (as defined in the mdadm.conf), and the system has had no problems since
[/LIST]

---

### Post by primski on 2007-12-19
> **peitschie said:**
> I then followed instructions in the [EVMS manual here]("http://evms.sourceforge.net/user_guide/#evmstocomp") to convert my EVMS partitions to LVM compatible partitions (i.e., they map to /dev/md/md[0-9] rather than /dev/evms/).


How exactly do you convert to LVM compatible partitions, so they map to /dev/md... instead of /dev/evms...?

i cannot get it to map anywhere else but /dev/evms...

---

### Post by peitschie on 2007-12-19
The line from the [online manual]("http://evms.sourceforge.net/user_guide/#e2ccli") is:

```
convert: /dev/evms/my_vol, compatibility
```

It is important that this doesn't delete the /dev/evms mapping!  It simply ensures the array is constructed in such a way that it can be accessed using the standard LVM tools like mdadm.

From my own experience, I had a link in /dev/evms & /dev/md at the same time both pointing to the same device.  Then, when I purged evms, the /dev/evms link disappeared and I had to use mdadm and mdadm.conf to recreate the /dev/md links...

Does that make any sense?  Perhaps a little background about what exactly you are attempting might help me craft my response a bit better :)

---

### Post by primski on 2007-12-24
Yes, i used the convert command, i even tried doing it with evms ncurses gui, but got same results.

Let me clarify, the mentioned procedure mapped my devices to /dev/evms/group0/volume1, it converted great and worked like a charm. but after i removed the evms package, the /dev/evms was no longer there, therefore so the other lvm tools didnt see the volumes at all.

anyways, no worries, i was lucky the vm machines were still relatively small, had backup, and did a reinstall of host OS. Actually, co-worker did it, i was having a few sick days lately, that explains the long gap between posts, sorry for that.

so, thanks for help.

---

### Post by sfaoldun on 2007-12-24
It's not exactly a fix though is it? I mean, removing EVMS and replacing it with LVM?

To fix the problem here I ... installed Gentoo. Sorry about that. :P

---

### Post by peitschie on 2007-12-26
> **primski said:**
> Let me clarify, the mentioned procedure mapped my devices to /dev/evms/group0/volume1, it converted great and worked like a charm. but after i removed the evms package, the /dev/evms was no longer there, therefore so the other lvm tools didnt see the volumes at all.

Mmm... sorry that didn't work out for you so well.  For this bit, after I uninstalled EVMS, I needed to use mdadm to re-assemble the array.  This was done using info found from the command ```
mdadm --examine --scan
```

The /dev/evms links do disappear when you remove the EVMS package, but you then need to re-enable the RAID array using mdadm... so yer... just for future reference :)

> **sfaoldun said:**
> It's not exactly a fix though is it? I mean, removing EVMS and replacing it with LVM?

To fix the problem here I ... installed Gentoo. Sorry about that. :P

sfaoldun, I don't quite understand what is wrong with removing EVMS and replacing it with LVM... if you are using software RAID (which I and primski are), then you need something such as LVM to manage it for you (generally speaking... I'm still waiting for ZFS...).  So replacing EVMS with LVM is a perfectly acceptable solution... installing Gentoo seems to me an even "worse" solution to the problem.  This issue is hardly reason to move distro's...

---

### Post by sfaoldun on 2007-12-26
> **peitschie said:**
> 
sfaoldun, I don't quite understand what is wrong with removing EVMS and replacing it with LVM... if you are using software RAID (which I and primski are), then you need something such as LVM to manage it for you (generally speaking... I'm still waiting for ZFS...).  So replacing EVMS with LVM is a perfectly acceptable solution... installing Gentoo seems to me an even "worse" solution to the problem.  This issue is hardly reason to move distro's...

The problem is that having to switch the back end applications to manage these volumes - in my situation it was both easier (I've installed Gentoo before, I switched to Ubuntu) and safer to simply boot the Gentoo disc and invoke 'evms_activate', then just install as normal.

I'm not sure if I've mentioned it either, but my Ubuntu install by this point was completely boned (intermittent sound, network issues, graphical sheen working then not working ever again) so the "official line" being that EVMS is no longer supported was enough to push me back to Gentoo. :P

As someone that uses Gentoo and loves it - why is Gentoo a worse solution? It's a useful learning tool and one hell of a distro to boot (with an incredible user community, no offence guys).

Oh, not to mention as a final point that EVMS *is not* broken. It works completely on Gentoo, I have it running neatly on a vanilla Debian install too somewhere, what was broken was the ability for it to nab disks correctly in Ubuntu.

---

### Post by peitschie on 2007-12-26
Ahh... as your post makes explicitly clear though, you were already moving towards Gentoo for various other reasons.  I have absolutely no issues with Gentoo... as you say, its a useful learning tool and a solid distro... but in this particular area, reinstalling a whole new distro as a solution is hugely overkill for most people.  

In your case, (and primski's), it makes sense as there was no great advantage to saving the data that was stored on EVMS ;), and in your situation especially, the install is already broken.  But in my case, I had a signification amount of data (100Gb mirrored, 1Tb linear raid), and shifting that amount of data around was going to cause me a lot of hassles... enough that it was worth investigating how to save the data in the first place.

Regarding EVMS being broken or not... you are correct that it generally works well.  There are some future concerns cropping up however, especially with IBM withdrawing a lot of their support for the product (they were the key maintainers).  For information about why Gutsy has stopped supporting EVMS, read the article here: [https://wiki.ubuntu.com/Evms]("https://wiki.ubuntu.com/Evms").  

In my situation, it was easier to convert to LVM than to EVMS as the root drive has a partition shared with the linear array (this is NOT an Ubuntu specific bug!), so I chose to remove EVMS.

Either way, you found an appropriate solution for your situation of which I am glad... I am simply very conscious of the number of times I have seen people recommend distribution changes (which brings a whole new set of issues!) for problems that only need a bit of careful massaging.  Generally, I think unless the user is actively looking to jump from Ubuntu, telling them to change distro's to fix was is actually a relatively minor problem such as this is not necessarily the most helpful advice...

---

### Post by sfaoldun on 2007-12-26
> **peitschie said:**
> Ahh... as your post makes explicitly clear though, you were already moving towards Gentoo for various other reasons.  I have absolutely no issues with Gentoo... as you say, its a useful learning tool and a solid distro... but in this particular area, reinstalling a whole new distro as a solution is hugely overkill for most people.  

In your case, (and primski's), it makes sense as there was no great advantage to saving the data that was stored on EVMS ;), and in your situation especially, the install is already broken.  But in my case, I had a signification amount of data (100Gb mirrored, 1Tb linear raid), and shifting that amount of data around was going to cause me a lot of hassles... enough that it was worth investigating how to save the data in the first place.

Regarding EVMS being broken or not... you are correct that it generally works well.  There are some future concerns cropping up however, especially with IBM withdrawing a lot of their support for the product (they were the key maintainers).  For information about why Gutsy has stopped supporting EVMS, read the article here: [https://wiki.ubuntu.com/Evms]("https://wiki.ubuntu.com/Evms").  

In my situation, it was easier to convert to LVM than to EVMS as the root drive has a partition shared with the linear array (this is NOT an Ubuntu specific bug!), so I chose to remove EVMS.

Either way, you found an appropriate solution for your situation of which I am glad... I am simply very conscious of the number of times I have seen people recommend distribution changes (which brings a whole new set of issues!) for problems that only need a bit of careful massaging.  Generally, I think unless the user is actively looking to jump from Ubuntu, telling them to change distro's to fix was is actually a relatively minor problem such as this is not necessarily the most helpful advice...

Ah, you misunderstand what I meant, perhaps. :) I wasn't recommending a distro change as a solution to this problem, because I too believe it to be a huge hassle for normal problems, I was merely defending my switch. :)

I was in no way dead set on Gentoo, but in the end I went for it because it's generally bleeding-edge (and you can have the very molecule-thin edge of the blade if you want, but that's stupid) and because I have prior experience. :)

Regarding your point about large amounts of data, I too have quite a lot - a good 800Gb across a few disks. In my case, I felt it easier and safer (losing any of my work is ... bad to say the least :P) to leave it as-is and simply re-install EVMS on a new distro instead of switching to LVM. But anyway. :)

---

### Post by peitschie on 2007-12-26
Gotchya!  We are so far off-topic now (though is in fact still funny), but thanks for clearing all that up for me :)

---

### Post by sfaoldun on 2007-12-26
> **peitschie said:**
> Gotchya!  We are so far off-topic now (though is in fact still funny), but thanks for clearing all that up for me :)

Not a problem - banter is what makes a community I think. :)
Also, having read the UWiki page on EVMS, I can see what they mean by a lack of maintenance ... I might see what I can do to help. :D

---

### Post by primski on 2007-12-27
> **peitschie said:**
> ...For this bit, after I uninstalled EVMS, I needed to use mdadm to re-assemble the array.  This was done using info found from the command ```
mdadm --examine --scan
```


ah, this is the part I missed, that should have done the trick.

however, i am using hardware raid on motherboards' controller, so maybe after all it wouldn't be the solution.

anyway, i got it with clean reinstall, had relatively small VM's, about 150gb altogether with allocated space included, so was done in a few hours altogether.

---

### Post by peitschie on 2007-12-27
Ahh... hardware raid is a different story!  I am not quite sure how to deal with that :S.  Oh well, sounds like it has been dealt with satisfactorily which I am glad to hear :)

---

### Post by dayhawk4 on 2008-02-17
EVMS, LVM, and MD

EVMS does all that LVM and MD does plus bad block allocation, centralized tool management, simplified syntax, three different interfaces, computer cluster management of distributed filesystems, additional logic checking to insure proper creating of partition tables, support of a larger array of disk management (low level including different methods of creating and saving partitions, etc), among many other features.  I have already read five posts today where those who understand the differences are leaving for Redhat or some other distribution.  Those that aren't are converting to LVM and MD.  Is the stability of all of your files really not a big issue?  If an individual is willing to spend upwards of $300. minimum in additional HDs, would anyone believe that it wasn't important?

hmmm

---

### Post by peitschie on 2008-02-24
Hi,

I'm not sure whether you have seen the Ubuntu wiki entry about EVMS: [https://wiki.ubuntu.com/Evms](https://wiki.ubuntu.com/Evms)

Have a quick read of that if you haven't already.  It covers the how and why of the issues present in EVMS.

---

