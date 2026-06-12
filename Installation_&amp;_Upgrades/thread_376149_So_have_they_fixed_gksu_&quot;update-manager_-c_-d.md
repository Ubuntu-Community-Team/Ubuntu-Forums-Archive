---
title: "So have they fixed gksu &quot;update-manager -c -d&quot; yet?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by steveyos666 on 2007-03-04
I reinstalled 6.06 last night so I could just skip edgy and go right to feisty clean to work on wireless, but of course it hasn't been working since last night. I guess the normal updates are on different servers than the kernals eh? :popcorn:

---

### Post by TehVague on 2007-03-04
Are you sure there is a server down and how do you know?

---

### Post by Geert Jan on 2007-03-05
I couldn't get my Edgy to update to Feisty either yesterday. But now it seems to be working again. Edgy is downloading the 963 files needed to upgrade right now.

---

### Post by steveyos666 on 2007-03-05
It had the Edgy update for me now, but no Feisty... Do I need to get Edgy first?

---

### Post by TehVague on 2007-03-05
Yes, I believe you need Edgy to get Feisty

---

### Post by steveyos666 on 2007-03-05
Got Edgy... Now for Feisty I get:
Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server. 

```

f@f-laptop:~$ gksu "update-manager -c -d"
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
extracting '/tmp/tmp7lcfiV/feisty.tar.gz'
authenticate '/tmp/tmp7lcfiV/feisty.tar.gz' against '/tmp/tmp7lcfiV/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
  self.parent.scrolled_notes.add(textview_release_notes)
extracting '/tmp/tmp-UwBiV/feisty.tar.gz'
authenticate '/tmp/tmp-UwBiV/feisty.tar.gz' against '/tmp/tmp-UwBiV/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072

```

---

### Post by hughes28105 on 2007-03-05
hay having the same problem I tryed to upgrade 5.10 to 6.06 lts and update-manager tell me there are no upgrades for 6.06.

---

### Post by steveyos666 on 2007-03-05
They need to have an official Ubuntu spokesperson let us know what's going on... I wonder if I could apply for the job :O

---

### Post by MikaelHolber on 2007-03-08
There is a launchpad bug for this [https://launchpad.net/ubuntu/+source/update-manager/+bug/78673]("https://launchpad.net/ubuntu/+source/update-manager/+bug/78673"). Hope they add it to the repos soon because I want to upgrade the right way.

Just add the /~.gnupg dir and your fine.

---

### Post by steveyos666 on 2007-03-09
I lost the thread but a guy had a link that just said, from what I gather, to type gpg in the console then that's that. It worked yesterday but I ended up reinstalling everything and now I'm stuck in Edgy. I don't understand what to do with that link there... What am I supposed to do to get to Feisty? They gonna fix this problem soon? How'd they even end up messing whatever up to get here? :/

---

### Post by MikaelHolber on 2007-03-09
Add the .gnupg dir and update-manager won't complain.

```
mkdir ~/.gnupg
```

Worked for me, I reinstalled Edgy and upgraded to Feisty yesterday.

---

### Post by steveyos666 on 2007-03-09
I tried that, didn't work. Is that all you're supposed to do? Doesn't that just make an empty folder?

---

### Post by rdw200169 on 2007-04-14
you *could* bypass the autheticate function in /usr/lib/python2.4/site-packages/UpdateManager/DisUpgradeFetcher.py
by commenting out every line in the function except 'return True'

that would be commenting out lines 96 to 101.

this is not for the faint of heart, of course, but it works....

---

### Post by blazercist on 2007-04-14
thank you so much rdw you saved me with the work around.

---

### Post by zvacet on 2007-04-14
```
update-manager -d
```

---

