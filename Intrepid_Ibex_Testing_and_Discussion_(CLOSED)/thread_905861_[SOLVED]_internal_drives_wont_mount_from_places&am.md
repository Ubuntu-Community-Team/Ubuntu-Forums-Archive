---
title: "[SOLVED] internal drives wont mount from places&amp;gt;computer"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-08-30
can some one please confirm this bug ?  [https://bugs.launchpad.net/ubuntu/+bug/254098](https://bugs.launchpad.net/ubuntu/+bug/254098)    I entered it 3 weeks ago and it still needs confirmation .

---

### Post by Nullack on 2008-08-30
Mate my workflow has been to edit fstab and add the UUID for the internal drive I want mounted - it auto gets mounted on boot then. Have you got the entry in fstab as I understand you need that in there for a normal user to mount it?

---

### Post by lonniehenry on 2008-08-30
ronacc, did you go to authorizations and enable users to mount internal drives?  I ran into the same situation and by changing the authorizations allow myself and others to mount them. After changing the permission setting, just clicking on them in nautilus mounts them.

---

### Post by ronacc on 2008-08-30
thanks lonnie that got it , I never had to do that before , it always just worked .
@ Nullack I don't want them in fstab because that would automount them and I dont need them every session and some I only rarely mount or never mount from what ever dev version is current , on the fly mount as needed suits me better .

---

### Post by plun on 2008-08-31
Well...  it must be a typical "nerd" which finds out that
he must change permission for this basic function.

Maybe to try to find a Gnome Bugzilla bug for this.... ?

This is the sort of bugs which drives newbies back to Windows... IMHO.

---

### Post by ronacc on 2008-08-31
That is exactly why I "bugged" it , the workaround suggested by lonniehenry does allow mounting of the drives by a user but it is not the "propper " fix . Note that hardy and previous versions of Ubuntu do NOT require the permission change and changing the permissions in that manner represent a security risk.

---

### Post by plun on 2008-08-31
> **ronacc said:**
> That is exactly why I "bugged" it , the workaround suggested by lonniehenry does allow mounting of the drives by a user but it is not the "propper " fix . Note that hardy and previous versions of Ubuntu do NOT require the permission change and changing the permissions in that manner represent a security risk.

Within a corporate environment this is important but *not* for a home user.

Another example is the mess to connect Windows PCs to a mixed workgroup at home.

It must be different policys for a different user groups and for sure
a corporate admin must know this....  compare with **gpedit.msc** for Windows.

---

### Post by Nullack on 2008-08-31
Its the AppArmor profile. If you feel the policy is wrong, policy discussions are best discussed in the development discuss mailing list or on IRC.

---

### Post by ronacc on 2008-08-31
even within a home environment many people have things they would not want "all" to have easy access to , and no I'm not talking about their Por* collection . I haven't run window for 8 or 9 years so I wouldn't know about that and as far as security goes on my personal system I have the best security of all , nothing worth stealing:lolflag:

---

### Post by plun on 2008-09-01
> **ronacc said:**
> even within a home environment many people have things they would not want "all" to have easy access to , and no I'm not talking about their Por* collection . I haven't run window for 8 or 9 years so I wouldn't know about that and as far as security goes on my personal system I have the best security of all , nothing worth stealing:lolflag:

Well, who knows....    

Discussed within this bug.

[http://bugzilla.gnome.org/show_bug.cgi?id=520736](http://bugzilla.gnome.org/show_bug.cgi?id=520736)

and this

[http://bugzilla.gnome.org/show_bug.cgi?id=536292](http://bugzilla.gnome.org/show_bug.cgi?id=536292)


> - We only show mounts in /media and $HOME (excluding $HOME/.gvfs)
 - We attempt to mount everything that gets shown as a volume
 - We only show volumes if there's a mountable filesystem
   - Except if an entry in /etc/fstab point to it (see also bug 520851)
   - Or if hal's volume.ignore is set to TRUE
  [B] - On most distros this is locked down for internal drives
     either via volume.ignore for all internal drives (so they
     are hidden) or, these days, via PolicyKit (the action / authorization
     is called org.freedesktop.hal.storage.mount-fixed) so e.g. partitions
     can't be mounted without authenticating[/B]

This is intended behavior and here's why:

 - It's relatively easy to explain to users ("you don't want to see
   an icon for /dev/sda2? Just create an /etc/fstab entry pointing to
   outside /media")

 - In general if you have mountable filesystems you want to see them

 - In particular you want to see Windows and OS X file systems



"Dog-fooding"....  :redface:

Well, this just must be fixed...!!!!     :)

---

### Post by plun on 2008-09-01
> **plun said:**
> Well, who knows....    

Discussed within this bug.

[http://bugzilla.gnome.org/show_bug.cgi?id=520736](http://bugzilla.gnome.org/show_bug.cgi?id=520736)

and this

[http://bugzilla.gnome.org/show_bug.cgi?id=536292](http://bugzilla.gnome.org/show_bug.cgi?id=536292)





"Dog-fooding"....  :redface:

Well, this just must be fixed...!!!!     :)

EDIT  > changed status to confirmed....

---

### Post by ronacc on 2008-09-01
@plun   Thanks for the confirmation and upstream references , it looks like they are undecided about how to handle this . As far as I am concerened this is a regression since in previous Ubuntu releases atleast as far back as dapper clicking on an internal drive in places>computer mounted it which I find very handy in my particular situation . right now on my test box I have 6 drives with 9 partitions not counting swaps , all linux and occasionaly but not often want to move files between them or mabye just look at the same file on 2 different installs to compare them.since this is a test box things change often and keeping fstab entries sync'd between (right now ) 4 different installs would be a real pain , it's bad enough kepping grub up to date especialy with uuid's .

---

### Post by plun on 2008-09-01
> **ronacc said:**
> @plun   Thanks for the confirmation and upstream references , it looks like they are undecided about how to handle this . As far as I am concerened this is a regression since in previous Ubuntu releases atleast as far back as dapper clicking on an internal drive in places>computer mounted it which I find very handy in my particular situation . right now on my test box I have 6 drives with 9 partitions not counting swaps , all linux and occasionaly but not often want to move files between them or mabye just look at the same file on 2 different installs to compare them.since this is a test box things change often and keeping fstab entries sync'd between (right now ) 4 different installs would be a real pain , it's bad enough kepping grub up to date especialy with uuid's .

Well, you can find this "pain" in every forum worldwide when a user wants
to use a new drive or a new partition.

The key sentence must be this.
> 
- On most distros this is locked down for internal drives
either via volume.ignore for all internal drives (so they
are hidden) or, these days, via PolicyKit (the action / authorization
is called org.freedesktop.hal.storage.mount-fixed) so e.g. partitions
can't be mounted without authenticating


Change the rule for a default Ubuntu install.....  if a company has an admin which doesn't check policykit-rules its up to them.

---

### Post by ronacc on 2008-09-01
Quote:- On most distros this is locked down for internal drives
either via volume.ignore for all internal drives (so they
are hidden) or, these days, via PolicyKit (the action / authorization
is called org.freedesktop.hal.storage.mount-fixed) so e.g. partitions
can't be mounted without authenticating

that is exactly what I did change , the regression is that this was never necessary before and also that there is not even a dialog box that pops up saying "you don't have permission to mount this drive" alerting you that "something has changed" instead just click and nothing...........

---

### Post by Nullack on 2008-09-01
Dog fooding is a business slang for "eating your own food" - meaning, using your own products you sell.

So its policykit not apparmour eh.

Well in any case, I think its ok from a security point of view but then again Im a security nazi :)

I think discussion on the devel-discuss mail list would be the most productive option for policy stuff like this.

---

### Post by ronacc on 2008-09-01
yes for getting it fixed at the default level but this forum is probably better for bringing info and workarounds to the attention of other testers . and I for one am not sure I should be cluttering up the dev mailing list since any programing skills I once had are decades out of date .

---

### Post by Nullack on 2008-09-01
There is a devel list purerly for devs, then there is a devel-discuss designed for user - developer interactions. Its a dev policy item and I think on the discuss list would be appropriate.

---

### Post by plun on 2008-09-02
> **Nullack said:**
> There is a devel list purerly for devs, then there is a devel-discuss designed for user - developer interactions. Its a dev policy item and I think on the discuss list would be appropriate.

Yup, I proposed that myself to psyke83 and phil, but if you not are a Ubuntu member or dev it seems to be less interesting for someone to answer and debate about an issue.

ronacc bug is alive.... and maybe someone is "lurking" the forum...:)

---

