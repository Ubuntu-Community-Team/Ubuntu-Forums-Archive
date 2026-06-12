---
title: "Ok to download an O/S"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by DaleFarrell on 2007-10-11
I am not confident downloading something like an operating system. If just a bit or two are lost then the whole program could be unstable, or worse. I have ordered the Gutsy disk, but I would really like some experienced opinions.

---

### Post by floke on 2007-10-11
Check the mdsum of the download to verify it.
You can also run a verification check as it boots up - just select verify cd from the menu.

---

### Post by santy_kushwaha on 2007-10-11
ya thats for sure that if u had not download the whole OS it wont work properly but what kind of help u need can u specify

---

### Post by oilchangeguy on 2007-10-11
> **DaleFarrell said:**
> I am not confident downloading something like an operating system. If just a bit or two are lost then the whole program could be unstable, or worse. I have ordered the Gutsy disk, but I would really like some experienced opinions.

as long as you're not using dial-up you should be fine. and a wired highspeed connection is better than wireless for this as well. and read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by oilchangeguy on 2007-10-11
> **santy_kushwaha said:**
> ya thats for sure that if u had not download the whole OS it wont work properly but what kind of help u need can u specify

in this forum there are many whose first language is NOT english. so leave the text/im spelling elsewhere. in here spell correctly.

---

### Post by trak87 on 2007-10-11
It is possible to know that you've downloaded the *exact* operating system iso file by checking the downloaded file's MD5 value. To do this you run *md5sum <filename>* and it will produce a long number. Compare this number to the one posted at the Ubuntu download site for your particular iso file and you can be sure you've received the exact file.

I always suggest people download the iso with Bittorrent because it apparently does better error checking than http or ftp, which both have error checking capabilities but aren't as reliable for large files, especially http.

Here's one tip: even if you've downloaded a good portion of the iso file with http or ftp and the md5sum doesn't match, fire up Azureus or some other bittorrent client. Tell it where your broken iso file is and starting downloading the iso file. It will read the broken iso, find the errors and fill in the missing pieces and you'll end up with a complete, bit for bit, copy of the iso. And you'll have saved a lot of time by not starting over from the beginning. As long as that md5 value matches what it should be, you've got an exact copy.

---

### Post by DaleFarrell on 2007-10-11
Wow, that's what I needed. In a few minutes the force was with me! Can do all the above. Did not know about the disk verification tho. Thanks all. Dale in Seattle.

---

### Post by phr0ze on 2007-10-11
As someone who's been downloading for 15 years, the built in error checking in the protocol has never failed me. The only problematic downlaod I've had is when the download completes early. Which is obvious anyways because the file size is different. 

Finally, the MD5 sum is your friend.

---

### Post by DaleFarrell on 2007-10-11
Now I can't wait for 7.1, I'll try the beta on this emachine 5312 laptop. The hardware testing forums indicate they are happy campers. Now if FlightSim would work I'd bag Vista on the big machine. thanks everyone.

---

### Post by ryanVickers on 2007-10-11
I was always very reluctant to get gutsy because of everyone having problems, but now I think that the 'real' release will be better than the beta, and people have said it's fine ;) (signature)

---

### Post by oldos2er on 2007-10-11
That's why there are checks for the downloaded file(s); md5sum, and the 'check integrity' option on the LiveCD. I've downloaded and installed several distros and never had a problem.

---

### Post by Qinjuehang on 2007-10-11
Its ok to download, I downloaded my copy of Feisty. You just have you check the md5sum after downloading

---

