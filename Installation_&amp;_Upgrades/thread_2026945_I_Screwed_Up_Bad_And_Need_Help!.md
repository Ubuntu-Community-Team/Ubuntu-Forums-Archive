---
title: "I Screwed Up Bad And Need Help!"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by naathyn on 2012-07-16
I knew this would happen!  I was trying to run Ubuntu along-side Win7.

Basically, what happened is I allocated my hard drive.. I didn't reformat it, I only changed the allocation space...   It was a section of the "do not use" and the do not use section was larger than my used section.. so I don't understand what happened next... 

I did that, went back and Ubuntu can't find my original Windows 7 OS!  It is still showing my used space on the sda2/ but I can't boot into windows.  This was all during my Ubuntu installation.

Is there ANY way to get into windows or locate my files ???

*** EDIT*** I ran system diagnostic check and it is saying that it can not locate the bootable device.  Any suggestions?

***FINAL EDIT****

After mounds of research, I found the solution.  Perhaps database this link, because I found alot of people who had the same problem as me, but with no answers.

Here's how I did it.  [http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/Pavilion-dv7-3160us-will-not-boot/td-p/1428009](http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/Pavilion-dv7-3160us-will-not-boot/td-p/1428009)

Thanks,
-Nathan

---

### Post by na5h on 2012-07-16
What is your output of the following command?```
sudo fdisk -l
```

---

### Post by darkod on 2012-07-16
I don't understand what you did (allocate my drive, changed do not use????), you should be more precise when explaining. It sounds like you tried to resize your windows partition using the manual partitioning. But your post doesn't really explain anything.

Also, I see nothing in that link related to what you try to say was your problem. That thread you linked is talking about the computer not turning on at all, not simply about missing bootloader.

I hope that link posting is not some spam and will not get people confused.

If you really think your problem solution can help others, explain better:
1. What the problem was exactly? Resizing of the windows partition that went wrong?
2. What the solution was.

---

### Post by claracc on 2012-07-16
> After mounds of research, I found the solution. Perhaps database this link, because I found alot of people who had the same problem as me, but with no answers.

Please, mark the thread as solved with "thread tools" in the upper right part of the page, in order other people can find easily the information.

---

