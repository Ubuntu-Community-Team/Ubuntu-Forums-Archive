---
title: "Upgrade 8.10 intrepid to 9.04 jaunty with update manager fails"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by scprotz on 2010-02-11
Hi All,

I had an old machine running Feisty.  I followed the EOL guides and upgraded from 7.04 => 7.10 => 8.04 => 8.10 (intrepid).

Now that I'm at intrepid, I want to use the update manager to upgrade to 9.04 (Jaunty).  Whenever I launch update manager (System->Administration->Update Manager) everything looks fine until I choose "New distribution release '9.04' is available" and click the Upgrade button.

At this point, Update Manager complains and says "Could not find the release notes" "The server may be overloaded".  I'm assuming this could be a faulty URL somewhere, but I wouldn't know where.  My sources.list seems to work fine for regular intrepid updates, so not sure there would be anything there that could be the fault.  Once I get this error, I can only click "close".

I've also tried >sudo do-release-upgrade

$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

Obviously, my general networking is fine (or I wouldn't be able to post this message)..and again, standard updates work fine

Any insight into what is causing this (or maybe how Update Manager works so that I might try a bit of debugging myself?

Thanks

---

### Post by mörgæs on 2010-02-12
You are following a long path of upgrades, each being a major change to your system. I think the fast and safe way would be a back-up and a clean install of 9.04, plain and simple.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by scprotz on 2010-02-13
As much as I'd love to, I have too many files (of a size that makes them difficult to move).  I am more worried about losing the partition than getting upgraded...I just wanted to upgrade to something a bit newer since all my other machines are 9.10

(I know..I should archive off the files, do a clean install, etc..) but for now just trying to figure this out..

At this point, things have worked...I just followed the EOLUpgrades blog on ubuntu.com and got this far. There just seems to be some glitch in a url in the upgrader.  I just want to know what that URL is (or rather, WHERE it is) 

Thanks,

---

### Post by scprotz on 2010-02-13
So I've made it a bit farther.  I looked in DistUpgradeFetcher.py (the python code that actually prepares for the upgrade) and found that it was looking for release notes here:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/ReleaseAnnouncement)

now..if plug that into a browser...I get a 404.  Anyone know what that 'should' be?

thanks,

---

### Post by slakkie on 2010-02-13
The page is available to me ([http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/ReleaseAnnouncement))

You could also try a different mirror, eg 

gb.archive.ubuntu.com
us.archive.ubuntu.com

Have a look [here for more mirrors](https://launchpad.net/ubuntu/+archivemirrors).

PS. glad you liked my EOLupgrade guide :)

---

### Post by slakkie on 2010-02-13
> **mörgæs said:**
> You are following a long path of upgrades, each being a major change to your system. I think the fast and safe way would be a back-up and a clean install of 9.04, plain and simple.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

[http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)

---

### Post by scprotz on 2010-02-13
So after digging through python scripts (and noticing that everything points to [http://archive.ubuntu.com](http://archive.ubuntu.com)...) I thought about it..and then noticed that in one of my prior upgrades, it was recommended that I make a host file modification (I mapped archive.ubuntu.com to a specific IP..)..  Well, needless to say, the IP used 2 weeks ago now doesn't work and so broke my upgrade.

Now that I fixed that (by removing the host file entry in /etc/hosts) everything is back to normal.

I may have solved it, but hopefully if someone else ever has to do a number of chain-upgrades and runs into this, they'll find a quick answer :)

---

### Post by slakkie on 2010-02-13
> **scprotz said:**
> So after digging through python scripts (and noticing that everything points to [http://archive.ubuntu.com](http://archive.ubuntu.com)...) I thought about it..and then noticed that in one of my prior upgrades, it was recommended that I make a host file modification (I mapped archive.ubuntu.com to a specific IP..)..  Well, needless to say, the IP used 2 weeks ago now doesn't work and so broke my upgrade.

Now that I fixed that (by removing the host file entry in /etc/hosts) everything is back to normal.

I may have solved it, but hopefully if someone else ever has to do a number of chain-upgrades and runs into this, they'll find a quick answer :)

:) You hit that upgrade error with 7.10 iirc, where one needs to edit the hosts file to point archive.u.c to old-releases.u.c and forgot to remove it..

---

### Post by DribbleCastle on 2011-05-25
I know its a been over a  year now but I was wondering if you ever got around this problem?   I have several servers that are having the same problem.    I'm stuck on 8.10,  the initially installed OS, but I want to upgrade to 10.04.   Any help would be great.   Thanks.

---

### Post by mörgæs on 2011-05-25
8.10 is unsupported, and your path will bring you through 9.04 and 9.10, both also unsupported. After this you will get to 10.04. 

If it works, you will have 10.04 running on Grub 1, and updating this to Grub 2 is another process. 

Compare that to the time it takes to do a fresh install of 10.04.

---

### Post by walter23 on 2011-05-28
> **DribbleCastle said:**
> I know its a been over a  year now but I was wondering if you ever got around this problem?   I have several servers that are having the same problem.    I'm stuck on 8.10,  the initially installed OS, but I want to upgrade to 10.04.   Any help would be great.   Thanks.

I just encountered this problem myself and I think I found the solution (upgrading as I write here; no guarantee it will finish, will update later).  You can download the distribution upgrade tarball, untar it, and run an upgrade command manually.  I'm going 8.10 to 9.04 (and then trying to move on after that). 

I did all the steps described here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

And then here: [https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)

And got stuck at "do-release-upgrade" with the same errors: 

Failed Upgrade tool signature
Failed Upgrade tool

What I found was this:

[http://ubuntuforums.org/showthread.php?t=1159312](http://ubuntuforums.org/showthread.php?t=1159312)

Where a manual upgrade is described.

Basically you run these commands from some temporary directory.   

```

wget http://old-releases.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz

tar xzvf jaunty.tar.gz
gksu "./dist-upgrade.py --frontend=DistUpgradeViewGtk"

```And that'll get you going with the gtk interface.  I'm writing this as it downloads the upgrade packages so I don't know for sure that it will complete yet, but it looks like it's working fine.   I wasn't getting anywhere with update-manager or the command line version.

Notice I left out the gpg signature check.  That's because it fails.  This may be a security issue; I'm not sure.  It seems likely it's the cause of the problem we're experiencing with the automatic upgrade though.

I did find this thread that suggests adding a trusted key:

[http://ubuntuforums.org/showthread.php?t=285904](http://ubuntuforums.org/showthread.php?t=285904)

Maybe that will "fix it" so you can just run the update normally.

And this:  [http://www.google.ca/search?hl=en&source=hp&biw=1280&bih=641&q=437D05B5&aq=f&aqi=&aql=&oq=](http://www.google.ca/search?hl=en&source=hp&biw=1280&bih=641&q=437D05B5&aq=f&aqi=&aql=&oq=)

Another suggestion is to just delete your gpg keys and reinstall them: [http://techpad.co.uk/content.php?sid=84](http://techpad.co.uk/content.php?sid=84)

---

### Post by Hedgehog1 on 2011-05-28
> **walter23 said:**
> I just encountered this problem myself and I think I found the solution (upgrading as I write here; no guarantee it will finish, will update later). ...

I can see doing this and enjoying the technical challenge of it all.

But this amount of work is orders of magnitude more effort than a clean install or a separate '/' and '/home' install.

Is there a benefit I am missing?

Just wondering...

***The Hedge***

:KS

---

### Post by walter23 on 2011-05-28
> **Hedgehog1 said:**
> 

Is there a benefit I am missing?


I'm using relatively old hardware, I can't find my USB stick, and I don't have any blank CDs.  Maybe that's not the best reason to go this route, but it is what it is.

---

### Post by Hedgehog1 on 2011-05-28
> **walter23 said:**
> I'm using relatively old hardware, I can't find my USB stick, and I don't have any blank CDs.  Maybe that's not the best reason to go this route, but it is what it is.

Works for me - you are using available materials; gotcha!

---

### Post by mariuxx on 2011-09-06
Hi guys...

Sorry to disturb the harmony here, but i have a server on a remote site that should have been upgraded ages ago...or a year at least.

Obviously the GTK trick won't work for me.

It's now running 8.10 Intrepid, which i understand must (or should) be upgraded to 9.04 Jaunty

I included the old-releases lines in sources.list

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

That made it possible to update&upgrade the system.

However, issuing:

sudo do-release-upgrade

still only yields:

Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.

I seems the signature for the upgrade tool cannot be verified (or something like that), I have also used:

apt-get install ubuntu-keyring

which works ok, the keyring is installed, but still the same error...

Anyone?

---

### Post by aerotux on 2011-09-12
> **mariuxx said:**
> Hi guys...

Sorry to disturb the harmony here, but i have a server on a remote site that should have been upgraded ages ago...or a year at least.

Obviously the GTK trick won't work for me.

It's now running 8.10 Intrepid, which i understand must (or should) be upgraded to 9.04 Jaunty

I included the old-releases lines in sources.list

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

That made it possible to update&upgrade the system.

However, issuing:

sudo do-release-upgrade

still only yields:

Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.

I seems the signature for the upgrade tool cannot be verified (or something like that), I have also used:

apt-get install ubuntu-keyring

which works ok, the keyring is installed, but still the same error...

Anyone?

Walter23 (post #11) worked for me, I was having the same issues as you.

---

### Post by PierceNicholas on 2011-11-15
I'm also stuck on 8.10 but after playing around a little I know have the look of 9.04, yet my lbs_release -r states I'm on 8.10 still. 

Using Kubuntu and a returning linux user but I've forgotten most of it.

Also as much as it would be tons and millions and even lightyears better, faster, stronger to do a fresh install, I can't do that. I simply _need_ this to work via upgrade methods.

Does anyone have anything that will work?

---

### Post by MountainX on 2011-12-26
try this:
[http://serverfault.com/questions/278078/error-upgrading-ubuntu-server-from-intrepid-to-jaunty](http://serverfault.com/questions/278078/error-upgrading-ubuntu-server-from-intrepid-to-jaunty)

I'm in the process of using these steps from the link above:
> 
  I think the problem can be solved in a much simpler fashion without having to use another machine.  Here is what I did:
  Copied the old (incorrect) file from [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) to a local file (say) /etc/meta-release.rvg I modified /etc/meta-release.rvg so that "archive" was replaced by "old-releases"
  Modified /etc/update-manager/meta-release so that it pointed to my local file rather than the incorrect URI on the ubuntu site - here is what it looked like after my change:
  [METARELEASE]
  URI = file:///etc/meta-release.rvg
  URI_LTS = [http://changelogs.ubuntu.com/meta-release-lts](http://changelogs.ubuntu.com/meta-release-lts)
  URI_UNSTABLE_POSTFIX = -development
  URI_PROPOSED_POSTFIX = -proposed
  I then ran do-release-upgrade and everything worked like a charm
  Regards,
  Rajendra Gokhale
 
It got me past this error:
```
root@server1:/# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.

```

The next challenge will be to complete the upgrade from Jaunty to Karmic... (and yes, I also have good reasons for doing the stepwise upgrades rather than a fresh install).

In the future, I'll keep my servers on LTS releases only. ;)

---

