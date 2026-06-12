---
title: "problem mounting usb drives"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by neferty on 2009-06-29
it has started yesterday or today, i'm not sure. I'm doing updates daily, so it's impossible for me to say which one has screwed up the system. No usb will mount. Gnome gives folliwng error message box:
```

Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.44" (uid=0 pid=5368 comm="/usr/lib/devicekit-disks/devkit-disks-daemon ") interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" error name="(unset)" requested_reply=0 destination="org.freedesktop.PolicyKit1" (uid=0 pid=25488 comm="/usr/lib/policykit-1/polkitd-1 ")

```

has anybody had same issue? any ideas?

---

### Post by zika on 2009-06-29
> **neferty said:**
> it has started yesterday or today, i'm not sure. I'm doing updates daily, so it's impossible for me to say which one has screwed up the system. No usb will mount. Gnome gives folliwng error message box:
```

Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.44" (uid=0 pid=5368 comm="/usr/lib/devicekit-disks/devkit-disks-daemon ") interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" error name="(unset)" requested_reply=0 destination="org.freedesktop.PolicyKit1" (uid=0 pid=25488 comm="/usr/lib/policykit-1/polkitd-1 ")

```has anybody had same issue? any ideas?+1
[http://ubuntuforums.org/showpost.php?p=7533996&postcount=19](http://ubuntuforums.org/showpost.php?p=7533996&postcount=19)

---

### Post by psyke83 on 2009-06-29
Is this post the [fifth]("http://ubuntuforums.org/showpost.php?p=7533154&postcount=5") dupe or are there even more I haven't counted? ;)

---

### Post by zika on 2009-06-29
> **psyke83 said:**
> Is this post the [fifth]("http://ubuntuforums.org/showpost.php?p=7533154&postcount=5") dupe or are there even more I haven't counted? ;)I did not understand what You were saying. I did not post any "dupe" posts as far as I know.

---

### Post by douham on 2009-06-29
@ zika
I think Psyke83 was not pointing the finger towards you. 

@ Psyke83.
dupes. That's just the luck of the Irish I s'pose.

---

### Post by psyke83 on 2009-06-29
> **zika said:**
> I did not understand what You were saying. I did not post any "dupe" posts as far as I know.

I meant duplicates, not the alternate meaning of the word... ;)

Perhaps we could set up a wiki page (so that anyone can edit) that gives information on daily issues arising during the development process - that way, everybody can refer to the page before posting new threads. On this wiki page we could provide a link to a bug report and *one* discussion thread on the forums.

---

### Post by descendent87 on 2009-06-29
> **psyke83 said:**
> No, you only responsible for one of the duplicates... ;)

Perhaps we could set up a wiki page (so that anyone can edit) that gives information on daily issues arising during the development process - that way, everybody can refer to the page before posting new threads. On this wiki page we could provide a link to a bug report and *one* discussion thread on the forums.

Sounds like a good idea, hopefully might stop multiple threads about the same problems and would be quicker to check before updating than searching through the forum

---

### Post by dagrump on 2009-06-29
Yep, it's 5 of them, needs a merge.

---

### Post by muglikar on 2009-06-29
Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

### Post by douham on 2009-06-29
> **muglikar said:**
> Hello brother,
                    
I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

Hi muglikar. Ubuntu might solve these problems for you. An alpha release of Ubuntu in heavy testing and development may not. A stable release such as Ubuntu 9.04 (Jaunty Jackalope might).

---

### Post by neferty on 2009-06-30
Sorry for opening a thread about the same issue, guys. I quick-searched the forum before posting and found nothing, I swear :)

The problem seems with the freedesktop authorizations (at least to me). I've been able to sudo mount manually in terminal.

---

### Post by douham on 2009-06-30
Hi nferty

check how up to date the server you are receiving updates is. Some of the servers are up to a week or more behind main. If yours is one of those and a problem is in an update it is likely that any issues have also been raised in the Karmic forum. 

The Karmic forum is also pretty slow moving and if you just look through the first few pages there may be a similar sounding thread to your problem. Don't think to verbosely when looking at thread titles. You have a mounting problem and there have been a number of posts regarding an update which has caused this problem. Follow up on these threads and read all the posts in those threads. You may find that those threads are a better place to post your problem than to create a new duplicate thread.

cheers

---

### Post by neferty on 2009-06-30
thanks for your kind answer, douham. I'll check my repositories.

:)

---

