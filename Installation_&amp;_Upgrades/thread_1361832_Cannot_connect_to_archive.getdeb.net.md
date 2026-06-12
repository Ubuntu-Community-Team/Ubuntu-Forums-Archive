---
title: "Cannot connect to archive.getdeb.net"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2009-12-22
Starting yesterday (21-Dec), I am unable to connect to or even successfully ping archive.getdeb.net. I need it for Karmic application updates. All of my other software sources seem to be working just fine. It is resolving to 94.126.144.44

I thought I would see lots of posts on this problem, but it looks like no one else is having it. Any ideas about what is going on?

Thanks,
Tim

---

### Post by blackSP on 2009-12-22
Similar problem here with karmic, tried various servers (US, Main, NL, France etc.)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (94.126.144.44). - connect (113: No route to host)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/i18n/Translation-en_US.bz2)  Could not connect to archive.getdeb.net:80 (94.126.144.44), connection timed out

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release)  

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/binary-amd64/Packages.gz)  Unable to connect to archive.getdeb.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by blackSP on 2009-12-22
Update: this effects my 64-bit Karmic (PC). My 32-bit Karmic (Laptop) updates fine!

---

### Post by lamego on 2009-12-22
> **blackSP said:**
> Update: this effects my 64-bit Karmic (PC). My 32-bit Karmic (Laptop) updates fine!

Our main server is down, if you are getting updates is not from the getdeb archive.

---

### Post by raccoonone on 2009-12-22
not working for me either, and their website seems to be down too.

---

### Post by houseworkshy on 2009-12-22
There was a problem connecting to getdeb.net which was happening to customers of 02.  It was fixed but now I have just checked and it is back again. Last time onehad to go through a web proxy to get there. I'm looking for one now.  Not sure if the problems are related but if you are on o2 is seems probable.

---

### Post by houseworkshy on 2009-12-22
Well couldn't find one that worked so used this [http://downforeveryoneorjustme.com/getdeb.net](http://downforeveryoneorjustme.com/getdeb.net) which says that the site is actually down.  Sorry o2, Not you this time.

---

### Post by ratcheer on 2009-12-22
Thanks, everyone. I will just keep checking to see when it is back up.

Tim

---

### Post by ratcheer on 2009-12-23
It was up again, late last evening. Very slow, though.

Tim

---

### Post by Buddlespit on 2010-01-12
I just found that if I add the repo's per PlayDeb's instructions, I can see, but not download packages:
[HTML]deb http://archive.getdeb.net/ubuntu karmic-getdeb games[/HTML]

But if I change their repo to :
[HTML]deb http://archive.getdeb.net/getdeb/ubuntu karmic-getdeb games[/HTML]
everything works fine

---

### Post by leopards on 2010-02-28
Seems they are down again! Can't get to getdeb or playdeb! Update Manager and Synaptic aren't getting thru and neither can I with the browser and the downforeverorisitjust me link above says it is down also!

---

### Post by choupiwen on 2010-03-01
the same happend since 3 days before,no able to connect to getdeb.net (without ping reply)

---

### Post by mogwai on 2010-03-01
That's funny. I did a who.is and it said the IP was 188.40.136.109
But if I try to ping the domain, it tries to resolve to 94.126.144.44

Both time out though.

> **ratcheer said:**
> Starting yesterday (21-Dec), I am unable to connect to or even successfully ping archive.getdeb.net. I need it for Karmic application updates. All of my other software sources seem to be working just fine. It is resolving to 94.126.144.44

I thought I would see lots of posts on this problem, but it looks like no one else is having it. Any ideas about what is going on?

Thanks,
Tim

---

### Post by mogwai on 2010-03-01
Hang on - getting a message now:

We are working to get our services online soon. - The GetDeb Team

---

### Post by mkvnmtr on 2010-03-01
Yesterday when I ran update manager I had two getdeb repositories that did not load. Just now I only had one that did not load. Maybe they are making progress.

---

### Post by ricardisimo on 2010-03-03
Are there any getdeb mirrors we can try in the meantime?

---

### Post by FauZt on 2010-03-04
From [http://blog.getdeb.net/](http://blog.getdeb.net/)
> Sunday, February 28, 2010
**Web services down**
Hello,
as you may have notice this weekend both the www. and archive. services have been unavailable.
We are working on the problem and expect to provide more information soon.

Thanks for your patience.

---

### Post by Vined Adobo on 2010-06-11
> **FauZt said:**
> From [http://blog.getdeb.net/](http://blog.getdeb.net/)


It seems getdeb.net is back up.  I got an adobe update today from archive.getdeb.net and I can ping getdeb.net now.

Dave

---

### Post by xtracool_protik on 2010-06-11
playdeb is still down can't ping archive.pleydeb.net However both sites shows
 Recovering services...
 Thanks for your patience. 

So I hope I'll wait for a day or 2

---

