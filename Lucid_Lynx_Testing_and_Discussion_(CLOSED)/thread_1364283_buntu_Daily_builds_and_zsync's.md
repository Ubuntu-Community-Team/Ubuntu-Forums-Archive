---
title: "*buntu Daily builds and zsync's"
date: 2009-12-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-12-25
I doadloaded Kubuntu daily build from [here]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/").

I noticed the daily build and the zsync have the same date. Is the zsync for the previous daily or the current one? I'm guessing the previous, because I zcynced the current one and the *old and the rebuilt iso has the exact same md5sum totals.

I've never tried zsync before so I thought I would try it on Kubuntu, sense that is where I started Kubuntu 10.04.

Next questions is. If I download todays daily and come back in say three days, will that zsync make my three day old iso current? Or how does that work. Do I need to zsync each and everyday?

thanks.

---

### Post by descendent87 on 2009-12-26
I had an old daily image from before alpha 1 and zysnced it a few days ago and it all seemed to update fine and the m5dsum matched the current daily build so looks like you don't have to do it everyday

---

### Post by VMC on 2009-12-26
> **descendent87 said:**
> I had an old daily image from before alpha 1 and zysnced it a few days ago and it all seemed to update fine and the m5dsum matched the current daily build so looks like you don't have to do it everyday

Thanks for your reply. So it looks like they just keep the one zsync file updated. If that's the case then it should "grow" in size. I'll have to watch that.

---

### Post by ranch hand on 2009-12-26
In my experience it really didn't.  I used it last testing round.  It just updates the ISO replacing stuff no longer needed for the CD.  The size stayed pretty stable, and more importantly, well within usable range of a CD.

---

### Post by VMC on 2009-12-26
> **ranch hand said:**
> In my experience it really didn't.  I used it last testing round.  It just updates the ISO replacing stuff no longer needed for the CD.  The size stayed pretty stable, and more importantly, well within usable range of a CD.

Here what I found by comparing two different dates of zsync files. I open and the first 7 lines gives you some info into the zsync file:

```
   zsync file dated: 12/25/2009
zsync: 0.5
Filename: lucid-desktop-i386.iso
Blocksize: 4096
Length: 746627072
Hash-Lengths: 2,3,5
URL: lucid-desktop-i386.iso
SHA-1: 7759fba2ccc27940c2cf708ad17d66118fadaaf6
=====
    zsync file dated: 12/26/2009
zsync: 0.5
Filename: lucid-desktop-i386.iso
Blocksize: 4096
Length: 746631168
Hash-Lengths: 2,3,5
URL: lucid-desktop-i386.iso
SHA-1: 91e1e4f3a994490b049908887be2d39fa9b95429

```
You will notice that the size of the "lucid-desktop-i386.iso" file increases each day.

---

### Post by ranch hand on 2009-12-26
Neat.  I never did that.  I just kept checking the properties.

---

### Post by VMC on 2010-01-01
I just zsync isn't that effective. I tried again today and it estamated over 120 minutes when I started. I stopped at after 15 minutes. 

Interesting that from 12/25 to 12/28 it took zsync only 17 minutes. From 12/25 to 01/01 it was going to take over **2 hours**!

There was very little updates from the dates. I could download the entire daily in the time that zsync was going to take.

```
=======12/25/09 to 12/28/09====
 $ cd /media/DOWNLOADS/sync
 $ time zsync http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso.zsync
#################### 100.0% 80.1 kBps DONE      

reading seed file lucid-desktop-i386.iso: ************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read lucid-desktop-i386.iso. Target 94.9% complete.      
downloading from http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso:
#################### 100.0% 90.4 kBps DONE      

verifying download...checksum matches OK
used 708861952 local, fetched 38333889

real	[COLOR="red"]**16m52.115s**[/COLOR]
user	0m27.250s
sys	0m8.265s

======12/25/09 to 01/01/10=====
 $ time zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso.zsync
#################### 100.0% 71.7 kBps DONE     

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso:
-------------------- 0.0% 8.7 kBps         
#------------------- 9.6% 89.8 kBps **[COLOR="Red"]120:06 ETA[/COLOR]**  ^C

```

Anyone here use zsync and have the same results?

---

### Post by Gina on 2010-01-01
I haven't got round to trying it yet - I'm still using rsync.

---

### Post by VMC on 2010-01-01
> **Gina said:**
> I haven't got round to trying it yet - I'm still using rsync.rsync may be a better approach. I was looking at it today. Reading several howto's, but it appears to be for syncing more than one computer. I have one computer. 

How do you use it?

---

### Post by xebian on 2010-01-01
> **VMC said:**
> rsync may be a better approach. I was looking at it today. Reading several howto's, but it appears to be for syncing more than one computer. I have one computer. 

How do you use it?

rsync is the older one which uses more power of the server.

zsync is the newer one which uses more of the client side.

zsync is by default will look for a similar file name on the current directory and compare it againts the file-name.iso.zsync

In your case it could not find one so it's 0% complete. Look for your *386.iso file and run it from there, or you can pass the output file like this

zsync [http://cdimages....*386.iso.zsync](http://cdimages....*386.iso.zsync) -o <dir/file.iso>

Also, it makes a backup so you will find *386.iso.old later when it's done.

---

### Post by VMC on 2010-01-02
> **xebian said:**
> rsync is the older one which uses more power of the server.

zsync is the newer one which uses more of the client side.

zsync is by default will look for a similar file name on the current directory and compare it againts the file-name.iso.zsync

In your case it could not find one so it's 0% complete. Look for your *386.iso file and run it from there, or you can pass the output file like this

zsync [http://cdimages....*386.iso.zsync](http://cdimages....*386.iso.zsync) -o <dir/file.iso>

Also, it makes a backup so you will find *386.iso.old later when it's done.

Wait a minute. Now I see the problem. Look at my second zsync url. It's not kubuntu! that's the problem. Thanks for making me review my inputs.

Edit: Ok, this is much better. I was using the Ubuntu zsync to update my Kubuntu iso. A note to everyone, both Ubuntu and Kubuntu iso names are identical, but different URL's.
 I did keep them separate in different folders, but some cockpit errors proved otherwise :)
```
$ time zsync http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso.zsync
#################### 100.0% 81.3 kBps DONE

reading seed file lucid-desktop-i386.iso: 
**********************...*********************Read lucid-desktop-i386.iso. Target 92.0% complete.      
downloading from http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso:
#################### 100.0% 85.5 kBps DONE      

verifying download...checksum matches OK
used 686678016 local, fetched 60556672

real	[COLOR="Red"]**20m26.645s**[/COLOR]
user	0m28.422s
sys	0m8.613s

The sha's match for todays daily ISO's:
$ sha1sum lucid-desktop-i386.iso
4d0832db94dd4bc7937ca2e4361479de780c3f1e  lucid-desktop-i386.iso

```

---

### Post by xebian on 2010-01-03
> **VMC said:**
> Wait a minute. Now I see the problem. Look at my second zsync url. It's not kubuntu! that's the problem. Thanks for making me review my inputs.

Edit: Ok, this is much better. I was using the Ubuntu zsync to update my Kubuntu iso. A note to everyone, both Ubuntu and Kubuntu iso names are identical, but different URL's.
 I did keep them separate in different folders, but some cockpit errors proved otherwise :)
```
$ time zsync http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso.zsync
#################### 100.0% 81.3 kBps DONE

reading seed file lucid-desktop-i386.iso: 
**********************...*********************Read lucid-desktop-i386.iso. Target 92.0% complete.      
downloading from http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso:
#################### 100.0% 85.5 kBps DONE      

verifying download...checksum matches OK
used 686678016 local, fetched 60556672

real	[COLOR="Red"]**20m26.645s**[/COLOR]
user	0m28.422s
sys	0m8.613s

The sha's match for todays daily ISO's:
$ sha1sum lucid-desktop-i386.iso
4d0832db94dd4bc7937ca2e4361479de780c3f1e  lucid-desktop-i386.iso

```

It doesn't matter whether you use the ubuntu or kubuntu zsync file to update a kubuntu or ubuntu iso.  At least it will say "..reading seed file.." if it's there.  Otherwise, it would say "..no relevant data.." if it could not find it.

Besides the kubuntu iso has at least 50% same content as the ubuntu iso so at least you will have 50% complete instead of 0%.  It saves you a lot of time if at least you have one *buntu iso to get either kubuntu or xubuntu or ubuntu, etc.

---

### Post by VMC on 2010-01-04
> **xebian said:**
> It doesn't matter whether you use the ubuntu or kubuntu zsync file to update a kubuntu or ubuntu iso.  At least it will say "..reading seed file.." if it's there.  Otherwise, it would say "..no relevant data.." if it could not find it.

Besides the kubuntu iso has at least 50% same content as the ubuntu iso so at least you will have 50% complete instead of 0%.  It saves you a lot of time if at least you have one *buntu iso to get either kubuntu or xubuntu or ubuntu, etc.

I did have one ISO. The one from 12/25. What I was saying is I have both Ubuntu and Kubuntu ISO. I use the kubuntu URL to try to zsync my ISO. What I didn't know at the first try was I was using Ubuntu ISO and not Kubuntu ISO. They have the exact same name. I knew that but was in the wrong folder. 

Once I had the correct Kubuntu ISO , then using zsync from Kubuntu's URL, I was able to sync in 20 minutes instead of the 2 hours.

---

