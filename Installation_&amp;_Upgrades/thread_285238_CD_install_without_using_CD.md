---
title: "CD install without using CD?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Sarisar on 2006-10-26
So I ran the torrent, grabbed the CD (save Mark's servers!) and went to upgrade from the CD.  Said 'no' I didn't want it to connect to the internet to save the servers (CD will have all of the files anyway right?  Or most of them anyway).

So why is it downloading from the internet and it doesn't appear to be using the CD at all?  It doesn't really matter, except it's taking a hell of a lot longer then from the CD and it's hitting the servers which is of course slowing everyone else down.

Also I read somewhere you can copy files from the CD into the apt cache directory - would that speed things up?

---

### Post by mrobbert on 2006-10-26
I've got the same problem here. The http servers are very slow, which I'd expect. So, I grabbed the torrent and got the CD (desktop and alternative just in case) and want to upgrade from the CD. I found the instructions which say to run the cdromupgrade program on the CD. I did that and even if I tell it that my network is expensive it still insists on adding an http entry to sources.list and grabbing the files from the net.
I am in the process of trying the approach of copying files from the CD to my cache directory. Here is the command that I used:
```
find media/cdrom/pool/main/  -name *.deb -exec cp {} /var/cache/apt/archives/ \;
```

Not sure how well it'll work though. I doubt that all the files I'll need are on the CD. That may be the crux of our problem.

Alternatively, does anybody know how to point update-manager at one of the mirrors? Since it writes it's own entries into sources.list I don't seem to have any control over that.

Thanks,
Mike ](*,)

---

### Post by cg18 on 2006-10-26
Same problem here. I use gksu "sh /cdrom/cdromupgrade" and said no to download the files from the internet but the upgrade insist and start download all the packages from the internet.

Why this happends if i have the CD?

---

### Post by mrobbert on 2006-10-26
My plan worked, sort of...
After copying the files from the CD and restarting the process it skipped over a bunch of files, but then got stuck again downloading file 800 something. I checked the partial directory to see what it was downloading and found it to be a file that was not on the CD. The entire distro will not fit on a single CD so if you have packages installed that aren't on the CD it must download them. I tried the process of peeking at the partial directory and downloading that file from a mirror, but then I still needed to restart the process which took awhile since it need to re-check some files before starting up again. That was taking to long so I have decided to manually edit my sources.list to use a mirror and just use: 
```
aptitude update; aptitude dist-upgrade
```
That seems to be going much faster. It was showing about 15 minutes from when I started and is already down to 5 minutes. YMMV.

Good Luck,
Mike

---

### Post by beameup on 2006-10-26
I plan to do the same thing tomorrow. Grabbed that Alt install ISO off the torrent and was getting 300Kb download speeds. I'm at work and can't try it now but I'll ask these questions.

Has anyone tried disconnecting from the internet while upgrading from the CD? 

In the Update Manager, can't you select just the CD?


And everyone is using the alternate install CD right??
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Sarisar on 2006-10-26
*cough* erm... no.  Normal CD.

Guess that may be the problem lol

---

### Post by ihavenoname on 2006-10-26
comment out all of the servers on your /etc/apt/source.list

then mount your alternate install iso to a directory, lets just say /media/iso

in a terminal
sudo mount /path-to-iso/ /media/iso auto -o loop 

(make sure media iso exsists

then add this to /etc/apt/source.list 

deb file:/media/iso edgy main restricted 

(can't remeber if it's file:/ or file:// try adding extra ones if it doesnt work)

now go to the terminal and

sudo aptitude update 
sudo aptitude dist-upgrade


hopefully this works!

---

### Post by beameup on 2006-10-27
> **Sarisar said:**
> *cough* erm... no.  Normal CD.

Guess that may be the problem lol

Hey, no problem. That's what this forum is for. Let us know how your install goes.

---

### Post by Sarisar on 2006-10-27
Well what does it say over on the right here -----------------------------------------------------------------------------------------------------------------------------------^

(at least is should say I'm running Edgy now)

Couple of minor things like it removed amarok so I had to reinstall which was... slightly more complicated then it should have been.  It wouldn't install amarok because it needed amarok-xine.  Amarok-xine wouldn't install because it needed amarok and libxine.  Installing libxine uninstalled democracy player (was a manual install) but allowed me to install amarok.

Weird... but acceptable.  Hell I remember old install programs on windows that only look at the D drive to install from - if you had two HDs or partitions you had to copy the CD onto the D drive to install!

---

### Post by beameup on 2006-10-27
Well, don't know what I did different, but I did the Alt CD install today, told it NO, don't connect to the internet.........and it didn't.

Now while it was updadting from the CD, the notification pooped up that "updates were available". I ignored it.

After I rebooted it said I had 146 updates and I need to do a distribution upgrade to complete some of them. So I did, took about an hour.

Only thing I can see I lost was GnomeBaker. Everything runs fine so far.

:KS   Yipee!  LOL

---

