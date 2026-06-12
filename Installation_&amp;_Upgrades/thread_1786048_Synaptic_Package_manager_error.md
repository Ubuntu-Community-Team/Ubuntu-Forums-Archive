---
title: "Synaptic Package manager error???"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by 9000cse on 2011-06-19
> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)Hi all. Anybody know what the above means?
Also how to fix?
Thanks.
Andy

---

### Post by coffeecat on 2011-06-19
> **9000cse said:**
> Anybody know what the above means?

Yes, you have a duplicate entry in your sources.list file which is confusing the package manager. Post the output of this terminal command:

```
cat /etc/apt/sources.list
```Then we can see what's amiss. It should be easily fixable by editing that file.

**EDIT**: by the way, you can highlight the terminal output with the mouse, right-click to copy it to the clipboard and then paste it into your post.

---

### Post by 9000cse on 2011-06-19
> asjmm@asjmm-Saviour:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick main restricted multiverse
deb-src [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-updates main restricted multiverse
deb-src [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick universe
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-security main restricted multiverse
deb-src [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-security universe
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-proposed restricted main universe multiverse
deb-src [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-proposed restricted main universe multiverse #Added by software-properties
deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-backports restricted main universe multiverse
deb-src [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-backports restricted main universe multiverse #Added by software-properties

asjmm@asjmm-Saviour:~$ 


Hope that's what your looking for.
Thanks for getting back to me.
Andy

---

### Post by coffeecat on 2011-06-19
Oops, sorry, the duplicate must be in /var/lib/apt/lists/. Post the output of:

```
ls -l /var/lib/apt/lists/archive*
```

---

### Post by 9000cse on 2011-06-19
> asjmm@asjmm-Saviour:~$ ls -l /var/lib/apt/lists/archive*
-rw-r--r-- 1 root root   21784 2011-06-15 00:04 /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages
-rw-r--r-- 1 root root   11765 2011-06-15 00:04 /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_source_Sources
-rw-r--r-- 1 root root    5925 2011-06-15 00:04 /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_Release
-rw-r--r-- 1 root root     198 2011-06-15 00:19 /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_Release.gpg
-rw-r--r-- 1 root root 3764068 2010-10-10 11:17 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources
-rw-r--r-- 1 root root   39772 2010-10-10 11:18 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_Release
-rw-r--r-- 1 root root     198 2010-10-10 11:18 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_Release.gpg
-rw-r--r-- 1 root root   13585 2010-10-10 11:17 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_restricted_source_Sources
asjmm@asjmm-Saviour:~$ ^C
asjmm@asjmm-Saviour:~$ 


Hows That.

---

### Post by coffeecat on 2011-06-19
Now I'm totally puzzled. I cannot see a duplicate for your partner entries in sources.list and the list in /var/lib/apt/lists seems OK.

Try this. Open Synaptic, and go to Settings > Repositories > Other Software tab. Untick the two Canonical Partners lines. Close the Software Sources window and click on "Reload" in the main Synaptic window. Now open Settings > Repositories again and tick just the Canonical Partners line, not the Canonical Partners (Source Code) line. Close the Sources window and do a reload again. What happens?

If there's still a problem, I'll muster up some more help. :)

---

### Post by 9000cse on 2011-06-19
Closing the SW window and clicking reload, I get
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 Closing that error I than get.
> 
An error occurred

The following details are provided:
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by coffeecat on 2011-06-19
> **9000cse said:**
> Closing the SW window and clicking reload, I get

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted  because of network problems. If available an older version of the failed  index will be used. Otherwise the repository will be ignored. Check  your network connection and ensure the repository address in the  preferences is correct.                      
```

That's a generic error. Underneath it would have been a more specific message. Did it start of with "Failed to fetch cdrom..."?

> **9000cse said:**
> Closing that error I than get.

```
An error occurred

The following details are provided:
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory                      
```

Was another package manager open? Update Manager or Software Centre?

Close all package managers except Synaptic and go to Settings > Repositories again. This time look in the Ubuntu Software tab and untick the two lines under "Installable from CD-ROM/DVD". Now close the Sources window and click on reload again. Do you still get an error?

You can re-enable any of these sources again later. I just want to see if you can do a metadata update with reload without errors first.

---

### Post by 9000cse on 2011-06-19
> Could not download all repository indexes

The repository may no longer be available or could not be contacted  because of network problems. If available an older version of the failed  index will be used. Otherwise the repository will be ignored. Check  your network connection and ensure the repository address in the  preferences is correct.
Nothing open this time.  I'm going to reboot at start from fresh.

Now I rebooted her, and tried again, I get this wonderfull msg.
> 
Please insert the disk labeled:
Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)
in drive /cdrom/
I'm not running ver 11

---

### Post by dino99 on 2011-06-19
are you booting from cdrom bios choice ?

---

### Post by 9000cse on 2011-06-19
If that's what I think you mean, Boot from a CD, then NO.
Boots to HDD. and both CDROM's MT

---

### Post by coffeecat on 2011-06-19
> **9000cse said:**
> Now I rebooted her, and tried again, I get this wonderfull msg.

```
Please insert the disk labeled:
Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)
in drive /cdrom/                      
```I'm not running ver 11

Yes, but you have:

```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
```... in your sources.list, so you must have enabled the Natty CD somehow. Did you...

[quote="coffeecat"]Close all package managers except Synaptic and go to Settings >  Repositories again. This time look in the Ubuntu Software tab and **untick  the two lines under "Installable from CD-ROM/DVD".** Now close the  Sources window and click on reload again.[/quote]

:?:

---

### Post by dino99 on 2011-06-19
you should not mount hardware you dont need to boot on by default, they will be mounted on demand via mountall

---

### Post by 9000cse on 2011-06-19
OK, I have checked, both ROMS, MT, and have been all this time.  Rebooted. and started SPM.
The moment I hit the reload button, it gets to 108 of 113, then asks for the ver 11 disc, as above.

There are no discs within any of my CDROMS.

---

### Post by coffeecat on 2011-06-19
> **9000cse said:**
> 
The moment I hit the reload button, it gets to 108 of 113, then asks for the ver 11 disc, as above.

I ask again, have you unticked the two lines under "Installable from CD-ROM/DVD" in the Synaptic Software Sources window?

---

### Post by 9000cse on 2011-06-19
Yes, both unticked.  But I found another, re the V11 CD. So, I have unticked that now as well.  And it seems now there are no errors.  When you know what your looking for it's easy.. At one time I was going to upgrade to 11, so, I must have left that there, without thinking.
Cheers
And thanks.  Now onto the next problem..
Andy

---

