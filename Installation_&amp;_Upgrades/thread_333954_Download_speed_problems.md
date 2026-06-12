---
title: "Download speed problems"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-01-08
Yesterday, I was installing Dapper 6.06.1 on two different machines.  On both machines I had problems with the speed at which the downloads of the available updates were taking place.  I am using DSL and the speed would start off at about 90kb/s and then would eventually go down to as little as 200b/s (please notice that there is NO K in that second number).  The speed would vary fairly greatly during the download process but once it went downward it never went back up to a fairly high speed.

Has anyone else been experiencing any download problems and has there been any report of problems with the Ubuntu/Conicial servers ?

Thanks.

---

### Post by Pobega on 2007-01-08
Yeah, I've been experiencing slow speeds with the repository downloads. I guess just give it time, whenever it gets slow it usually takes a day or so for it to go back to normal speed.

---

### Post by wpshooter on 2007-01-09
I am still experiencing the same problems trying to download updates as described in my original post.

Is the download speed problem something that Ubuntu is aware of ?  And if, not is there some way to report this to them ?

Thanks.

---

### Post by Pobega on 2007-01-10
Bump, because my speeds are still at 5000 B/s, and I'd like to know if I'm just going crazy or if other people are experiencing this too?

---

### Post by wpshooter on 2007-01-10
> **Pobega said:**
> Bump, because my speeds are still at 5000 B/s, and I'd like to know if I'm just going crazy or if other people are experiencing this too?


Pobega:

I know the two of can not be the only ones experiencing this !!! If we are, I wonder what we have done wrong ?  Have we been black-listed ???

Let me know if you find anything out about this.  I will be monitoring this post.  In the mean time I am going to try the update on one of my Dapper systems for the third time tonight.

---

### Post by Stephen47 on 2007-01-10
I am also having download problems and no one seems to want to address the problem

---

### Post by Pobega on 2007-01-10
Well that's the weird thing. Upgrade servers seem to work fine (I updated my kernel pretty quickly, but then again I'm not exactly sure on it's size), but when downloading apps it goes sluggishly slow.

---

### Post by wpshooter on 2007-01-10
I have just attempted the installation again and what I discovered is that the drastic slow down occurs on the 64th download file out of the 71 files available, that 64th file being "LANGUAGE-PACK-EN".

         Also, all files that come after #64 are also downloaded at this dramatically reduced speed.

        Can you tell me if this is something that needs to be looked into or do I just need to uncheck that particular file and all those that follow it and do NOT download and install them ?

        Thanks for your assistance.

---

### Post by wpshooter on 2007-01-10
Followup - On this last attempt, the download of all files finally actually completed (where as before, a time-out would occur and the update would ask me if I wanted to abort).

Also, I had reported to the Canonical yesterday via e-mail and I did get a response from them earlier today letting me know that they had received my e-mail.  Perhaps they are working on the problem.  I also just reported to them my findings as I just described in the above post.

Maybe we are making some progress.

Thanks.

---

### Post by Pobega on 2007-01-10
I wonder if it's just our connection with the server or something, because no one else is complaining about speed problems. Seems kind of weird actually, at first I thought it was a bandwith issue but then I realized it's still the first third of the month so that's not possible.

---

### Post by wpshooter on 2007-01-10
Actually, if you do some searches on the forum, I think that we are not the only ones experiencing this problem.  Do an advanced search on Download speed for about the last 2 weeks, title only.

---

### Post by Pobega on 2007-01-10
I found one other thread, [ here](http://ubuntuforums.org/showthread.php?t=334252&highlight=download+speed) and editing the "us." out of my sources.list file actually did speed up my downloads. But now for some reason it's refusing to download prboom, which is getting me angry D:

---

### Post by K.Mandla on 2007-01-10
Sounds like you tried this already, but if you switch to a repository elsewhere on the globe, you can sometimes get faster update speeds. 

I hear the servers in Belgium are quite quick. ;)

---

### Post by Pobega on 2007-01-11
> **K.Mandla said:**
> Sounds like you tried this already, but if you switch to a repository elsewhere on the globe, you can sometimes get faster update speeds. 

I hear the servers in Belgium are quite quick. ;)

Yeah, it seems that way. I get the us repositories get so many hits that it sucks  up their bandwith pretty quickly.

By the way, what is the name for Belgium servers? .bl?

---

