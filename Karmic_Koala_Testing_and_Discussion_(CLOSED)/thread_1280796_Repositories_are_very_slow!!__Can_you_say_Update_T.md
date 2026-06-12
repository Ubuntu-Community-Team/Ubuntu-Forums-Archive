---
title: "Repositories are very slow!!  Can you say Update Torrent Manager??"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2009-10-02
Looks like the Ubuntu Repositories are very slow.  
I'm upgrading by terminal, since the Update Manager isn't quite working properly.

Wouldn't an Update Torrent Manager be better for the community??  
Or would this lead to major security issues??
And couldn't those issues be addressed by some sort of checksum code??

I'm not a programmer so i'm sorry if it is a stupid question.
Thanks 
:guitar:

---

### Post by slakkie on 2009-10-02
I used my countries mirror and it was FAST! Think a lot of people are downloading the beta and that is causing the connection problem most of us have/had.

---

### Post by zevans on 2009-10-02
> **slakkie said:**
> I used my countries mirror and it was FAST! Think a lot of people are downloading the beta and that is causing the connection problem most of us have/had.

How do you force it to use the country mirror?

---

### Post by yelo3 on 2009-10-02
Anyway local mirrors are not always up to date

---

### Post by jfernyhough on 2009-10-02
> **zevans said:**
> How do you force it to use the country mirror?Two ways, either start Software Sources and set it to Use Country's Mirrors or manually edit /etc/apt/sources.list and add your country ID to before archive (e.g. for the UK it's gb.archive.ubuntu.com, so fr.ubuntu..., ie.ubuntu... etc. etc.)

---

### Post by psyke83 on 2009-10-02
> **KrazyPenguin said:**
> Looks like the Ubuntu Repositories are very slow.  
I'm upgrading by terminal, since the Update Manager isn't quite working properly.

Wouldn't an Update Torrent Manager be better for the community??  
Or would this lead to major security issues??
And couldn't those issues be addressed by some sort of checksum code??

I'm not a programmer so i'm sorry if it is a stupid question.
Thanks 
:guitar:

IMHO, using torrent sources for individual packages in a development release doesn't make much sense. Torrents require seeders - which means that users would need to have a torrent client running in the background, using their bandwidth.
Packages also change frequently during development.

Using torrents to distribute the actual .iso images makes plenty of sense, however.

---

### Post by bonsiware on 2009-10-02
have you tried apt-p2p?
I haven't... yet...

---

### Post by slakkie on 2009-10-03
> **zevans said:**
> How do you force it to use the country mirror?

Given the fact that the archives are archive.u.c you can rename them to tld.archive.u.c, tld being nl in my case, uk/gb/us/de/etc for the UK, US and Germany.

See also this page: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by ikt on 2009-10-03
> **zevans said:**
> How do you force it to use the country mirror?

system > admin > software sources > download from: and select other and then select your closest mirror, just remember to reload after (open terminal > sudo apt-get update)

---

### Post by CRAY-4 on 2009-10-23
software sources > download from > select best server

this will ping every Ubuntu server and see which one is the fastest

---

### Post by Paqman on 2009-10-23
> **KrazyPenguin said:**
> 
Wouldn't an Update Torrent Manager be better for the community??  


Possibly. Another alternative would be delta downloads, where you only download the parts of a package that have changed, instead of the whole package.

---

### Post by KrazyPenguin on 2009-10-23
Surprising this thread popped back up!!!

Since the servers are overloaded "again" i guess this idea would relieve the servers and make everyones updates super fast.

Not sure if this idea is new, probably not, it just popped in my head.
I don't know if it is stupid, but apparently there is no such thing as a stupid idea !!! :confused:

Instead of getting the updates off the servers "we" could all share the updates with other users.  Some kind of Update Torrent Manager would be needed.  It could be configured like other bit-torrent clients for share ratio, upload speed, etc.

I feel this would really add to the community spirit!!!!

And during final releases, RC, etc, new users wouldn't shy away.  The initial impression can not be good for new users if it takes 24 hrs to do updates.  Just isn't good for Ubuntu or Linux or the community as a whole.

+1

;-)

---

### Post by KrazyPenguin on 2009-10-23
> **psyke83 said:**
> IMHO, using torrent sources for individual packages in a development release doesn't make much sense. Torrents require seeders - which means that users would need to have a torrent client running in the background, using their bandwidth.
Packages also change frequently during development.

Using torrents to distribute the actual .iso images makes plenty of sense, however.

To me it "does" make sense.
If the idea was to work, wouldn't the community want to test it in a "development cycle" before implementing it in the final release???

It sounds a little complicated, but possible, but to say "doesn't makes much sense" during development, means that it wouldn't have been tested.

I wouldn't suggest Ubuntu releases any sort of package this way.

Yes, sharing files in the backgrounds is possible.  The package manager already allows downloading and installing packaging in the background, but it isn't set by default.

Also running a bit-torrent client in the background is also possible.

This doesn't mean that the user "has" to share them.  
It is about choice, right??
And once a user shares a certain amount(ratio), the client can close, and the user can be notified.

Again this is just an idea, im not saying it is a good or a bad one.

Just something to think about.

Thanks ;-)

---

### Post by Giradman on 2009-10-24
> **ikt said:**
> system > admin > software sources > download from: and select other and then select your closest mirror, just remember to reload after (open terminal > sudo apt-get update)

Well, I had noticed 'snail-pace' slowness in my last attempts to update - :mad:

So, just took the advice above and switched to the Duke University server (about 90 mins from me in North Carolina) - did the updates in less than a minute!  Thanks for the suggestion - :)

---

### Post by Regenweald on 2009-10-24
> **KrazyPenguin said:**
> Looks like the Ubuntu Repositories are very slow.  
I'm upgrading by terminal, since the Update Manager isn't quite working properly.

Wouldn't an Update Torrent Manager be better for the community??  
Or would this lead to major security issues??
And couldn't those issues be addressed by some sort of checksum code??

I'm not a programmer so i'm sorry if it is a stupid question.
Thanks 
:guitar:

Coming down to release time, the repositories are always slow. About a week before and a week after. I think for obvious reasons.

---

