---
title: "Migrating vista, merging 2 drives"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2007-11-10
[IMG]http://img260.imageshack.us/img260/613/computernk3.png[/IMG]

This is what I want to do:

Merge drives E: and D: as a JBOD. Question - does the D975XBX2 support making a JBOD? And where can I find the drivers for it? And how do I do it?

Migrate Vista from C: to D: (which would be both drives E and D). How do I do this?

Rename D: to C:, and C: to D:

Install Ubuntu on D:

Thanks in advance.

---

### Post by TV-VCR on 2007-11-10
Still need help.

---

### Post by Nano Geek on 2007-11-10
That's kind of tricky. Why not just install Ubuntu on the merged D: and E: drives?

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> That's kind of tricky. Why not just install Ubuntu on the merged D: and E: drives?

Windows is my main OS. You still have to say 465 GB is pretty generous for Ubuntu. :)

---

### Post by Nano Geek on 2007-11-10
> **TV-VCR said:**
> Windows is my main OS. You still have to say 465 GB is pretty generous for Ubuntu. :)Yes, it is more than enough. But I was wondering why you want to move Vista from one drive to another. Couldn't Ubuntu use that second drive? It would sure make things easier for you.

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> Yes, it is more than enough. But I was wondering why you want to move Vista from one drive to another. Couldn't Ubuntu use that second drive? It would sure make things easier for you.

I want Vista to have the most space. The 2nd 465 GB drive added to the 698 GB drive makes over a TB of space. And I have a lot of stuff to put on the windows section. That image is sort of outdated (space taken up only).

---

### Post by Nano Geek on 2007-11-10
> **TV-VCR said:**
> I want Vista to have the most space. The 2nd 465 GB drive added to the 698 GB drive makes over a TB of space. And I have a lot of stuff to put on the windows section. That image is sort of outdated (space taken up only).Wow! I though that said MB not GB. Well, you could also just resize the Windows partition to take up the extra space. If that would work for you I'll post the instructions.

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> Wow! I though that said MB not GB. Well, you could also just resize the Windows partition to take up the extra space. If that would work for you I'll post the instructions.

Would doing that make Windows recognize both E: and C: as one drive? And use both as one (like in a JBOD)? If so then please do post the instructions!

And I apologize for about wanting it to see both as one, I'm a real bad neat-freak.

---

### Post by Nano Geek on 2007-11-10
> **TV-VCR said:**
> Would doing that make Windows recognize both E: and C: as one drive? And use both as one (like in a JBOD)? If so then please do post the instructions!

And I apologize for about wanting it to see both as one, I'm a real bad neat-freak.No, do apologize. It's great that you want to learn. 

However, what you are saying sounds a little hard to do. What if you kept Vista on the drive you want now, installed Ubuntu on the D: drive, and then used the E: drive as a data drive for both Windows and Ubuntu? It wouldn't be quite as fancy as want you want, but it should work fine. Does that sound good to you? Please say if it doesn't.

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> No, do apologize. It's great that you want to learn. 

However, what you are saying sounds a little hard to do. What if you kept Vista on the drive you want now, installed Ubuntu on the D: drive, and then used the E: drive as a data drive for both Windows and Ubuntu? It wouldn't be quite as fancy as want you want, but it should work fine. Does that sound good to you? Please say if it doesn't.

Not really hehe :razz:, Ubuntu would have enough space, but Windows doesn't... it's starting to run out of space!

---

### Post by Nano Geek on 2007-11-10
> **TV-VCR said:**
> Not really hehe :razz:, Ubuntu would have enough space, but Windows doesn't... it's starting to run out of space!But with this you would move all of your personal data out of the Vista drive and into the current E: drive. Would that still not be enough space?

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> But with this you would move all of your personal data out of the Vista drive and into the current E: drive. Would that still not be enough space?

No.

---

### Post by Nano Geek on 2007-11-10
I'm sorry to say that it looks like to do what you want to do, you would have to buy something [like this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115001").

I'm afraid that I don't know much about RAID though. 
Sorry I couldn't fix your problem.

---

### Post by TV-VCR on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> I'm sorry to say that it looks like to do what you want to do, you would have to buy something [like this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115001").

I'm afraid that I don't know much about RAID though. 
Sorry I couldn't fix your problem.

Well what were the original instructions you were considering posting? Can I please just look at them? :(

Or at least, how do I move all of C: to E: for the time being?

---

### Post by Nano Geek on 2007-11-10
> **TV-VCR said:**
> Well what were the original instructions you were considering posting? Can I please just look at them? :(

Or at least, how do I move all of C: to E: for the time being?I'm afraid that I misread you question at first. I thought that each drive was actually a partition on one drive, but I see now that I am wrong. So I actually do not know how to make two hard drive look like one in Vista.

But if you want to move the content from one drive to another, then you can just boot the Ubuntu live cd and copy it over. You might have to reinstall the Windows boot loader afterwards though.

---

