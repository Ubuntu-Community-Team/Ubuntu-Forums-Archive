---
title: "Checksums after burning."
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by matelot on 2006-04-23
I download the ISO and validate the checksum. OK. Theoretically that is an uncorrupted download. Then when the CD is burned I find a checksum error reported in one of hundreds of files after trying to install.

How do you check a burned CD for non-corruption without having to check each individual file (assuming each individual file has a checksum somewhere)?

There's no point trying to run the CD otherwise, because sure as hell it won't install properly (as has often been the case judging by numerous other threads here), and it's all been a waste of time.

So how is it done? And why is Linux so tender when it comes to installing?

Thanks for advice.

---

### Post by Toon81 on 2006-04-23
I am very interested in this as well since I have no way of verifying whether or not the CD I burned is exactly like the ISO specifies it. I know it downloaded OK because the checksum checks out but how do I see whether the CD turned out right?

I was thinking making a .nrg image of my CD with Nero, and making a .nrg out of the ISO with Nero. and comparing their checksums (I seem to have no way of making a .iso out of a CD). Is that doable, or will a burned-and-ripped-again .nrg image provide a different MD5 checksum?

As for the delicacy involved, here's what I know about things like this: the system consists of packages that are usually compressed. So any redundant data has been eliminated from them and their bits have been re-arranged to make the data smaller. This means that every single bit is important so if one bit in a package isn't right, chances are very high that the package will turn out corrupted. Add to that that the packages consist partly of program code. If a bit in a text file isn't right, that's one thing but if a bit in an executable file isn't, the program won't do what it's supposed to anymore.

Hope I explained that right; I may well be wrong but I assume I will be corrected by smarter people if that turns out to be the case. :)

---

### Post by Herman on 2006-04-23
Hello, toon81, and matelot,
I really like your explanation there, toon81, it sounds reasonable to me I'd agree with that, very well put. 
Now I wouldn't be what you'd call an 'expert' either, but another fellow user trying to be as helpful as possible.
Bartender, another Ubuntu Forum member and I, went over this a little while ago and gathered some info from these forums and did some experiments ourselves for my web-site. [Here's a link]("http://www.users.bigpond.net.au/hermanzone/p17.htm") to the web-page containing the info we gathered on this. We felt that it was pretty important too. Here's where it has info about [checking the CD after it has been burned.]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Check_The_Burned_CDs_Integrity_optional")
There is only information there for the 'Breezy Badger i386 install CD' so far though.  There is room for someone to do more work on the subject and find out what checksums all the different available Ubuntu CDs should return after they have been burned. If you feel like  contributing some additional information it will be greatly appreciated. (Like for Kubuntu or other install CDs) Potentially it might save someone else quite a lot of trouble and frustrations if they take the time to check theirs and it's wrong.
A Ubuntu CD has a lot more stuff packed onto a single CD than other operating systems, how many CDs does it take before we get all our stuff installed in our 'other' system? I have a pile of them...ten or a dozen maybe?
Plus there's the potential for someone to burn to poor quality media using faulty equipment.
I installed 'Dapper' flight 6 the other day and it already has a self-testing feature in it. Obviously more knowledgeable people than us also think it's important.  I have read that the final release will also have a more advanced installer too. I'm waiting to see.
Regards, Herman.:D

---

### Post by Sef on 2006-04-23
If you download with bittorrent, it automatically md5sums.

> (I seem to have no way of making a .iso out of a CD)

Here is a free iso burner for Windows.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

Also don't burn at more than 4x.  That can cause corruption of the iso.

---

### Post by Bartender on 2006-04-23
Hi, guys - 
Oh, goodie, more md5 talk.  You've figured out that md5 gets complicated after converting the .iso file to the bootable install CD.  Hundreds of md5's instead of one.  MD5Summer, the Windows based utility Herman and I spent our time with, made a shorter list of md5's when I asked it to check a bootable install CD.  I don't know why.  
My rambling discourse is in this post 
[http://www.ubuntuforums.org/showthread.php?t=128673](http://www.ubuntuforums.org/showthread.php?t=128673)
You'll find an attached file in that thread...it's the list of MD5Summer results from a stamped Ubuntu i-386 install CD.  I used that CD to install to a test PC so 99.9% sure it's good.  
If you want to use MD5Summer, you should be able to figure out how to copy/paste the attachment so that MD5Summer can use it to compare your CD using the "Verify" mode.  Comparing long-hand would be a pain and too easy to miss a number.
I'm a little bit amazed that there isn't an established procedure for verifying the finished CD.  It'd be great to have a sticky with all the md5's from all the different versions.  As Herman mentioned, it sounds like with Dapper this problem will be no more.

---

