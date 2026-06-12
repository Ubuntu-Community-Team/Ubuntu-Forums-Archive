---
title: "Linux insists I have a floppy drive"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gt24 on 2010-04-20
Ok, Compaq Armada M700 laptop here.  It seems like Ubuntu, while it does work on this laptop, tends to have a new bug with every version.  Pity too since I'm not exactly sure how to report bugs so they get fixed.  So, I apologize in advance if this is in the "bug tracker" or otherwise was posted and if the bug doesn't get fixed because I only posted about it... well...

Anyways, here is the problem.  My laptop has a modular bay that can take a floppy drive but I don't have one.  The bay has a CD drive shoved in it and that will always be the case.  However, in a prior release of Ubuntu (not sure which one) the kernel insisted the floppy drive was in and delayed the boot process by a good 20 minutes as it tried over and over to read from the non-existent floppy drive.  There was no solution...

Ok, this Ubuntu version has a new one.  The "light that never turns on" is on, the floppy drive access light.  Interesting being that I still have no floppy drive.  So, what does the kern.log have to say about this?

> Apr 20 08:08:43 sparkie-zombie kernel: [  114.216736] end_request: I/O error, dev fd0, sector 0
Apr 20 08:09:16 sparkie-zombie kernel: [  148.150627] end_request: I/O error, dev fd0, sector 0
Apr 20 08:09:50 sparkie-zombie kernel: [  182.078125] end_request: I/O error, dev fd0, sector 0
Apr 20 08:09:50 sparkie-zombie kernel: [  182.078145] __ratelimit: 9 callbacks suppressed
Apr 20 08:09:50 sparkie-zombie kernel: [  182.078155] Buffer I/O error on device fd0, logical block 0
Apr 20 08:10:24 sparkie-zombie kernel: [  216.010698] end_request: I/O error, dev fd0, sector 0
Apr 20 08:10:24 sparkie-zombie kernel: [  216.010721] Buffer I/O error on device fd0, logical block 0
Apr 20 08:10:58 sparkie-zombie kernel: [  249.942320] end_request: I/O error, dev fd0, sector 0
Apr 20 08:10:58 sparkie-zombie kernel: [  249.942345] Buffer I/O error on device fd0, logical block 0
Apr 20 08:11:32 sparkie-zombie kernel: [  283.882134] end_request: I/O error, dev fd0, sector 0
Apr 20 08:11:32 sparkie-zombie kernel: [  283.882159] Buffer I/O error on device fd0, logical block 0
Apr 20 08:12:06 sparkie-zombie kernel: [  317.810694] end_request: I/O error, dev fd0, sector 0
Apr 20 08:12:06 sparkie-zombie kernel: [  317.810719] Buffer I/O error on device fd0, logical block 0
Apr 20 08:12:40 sparkie-zombie kernel: [  351.742313] end_request: I/O error, dev fd0, sector 0
Apr 20 08:12:40 sparkie-zombie kernel: [  351.742337] Buffer I/O error on device fd0, logical block 0
Apr 20 08:13:14 sparkie-zombie kernel: [  385.666761] end_request: I/O error, dev fd0, sector 0
Apr 20 08:13:14 sparkie-zombie kernel: [  385.666786] Buffer I/O error on device fd0, logical block 0
Apr 20 08:13:48 sparkie-zombie kernel: [  419.597873] end_request: I/O error, dev fd0, sector 0
Apr 20 08:13:48 sparkie-zombie kernel: [  419.597897] Buffer I/O error on device fd0, logical block 0
Apr 20 08:14:22 sparkie-zombie kernel: [  453.522157] end_request: I/O error, dev fd0, sector 0
Apr 20 08:14:22 sparkie-zombie kernel: [  453.522183] Buffer I/O error on device fd0, logical block 0
Apr 20 08:14:56 sparkie-zombie kernel: [  487.450646] end_request: I/O error, dev fd0, sector 0
Apr 20 08:14:56 sparkie-zombie kernel: [  487.450670] Buffer I/O error on device fd0, logical block 0
Apr 20 08:15:30 sparkie-zombie kernel: [  521.378171] end_request: I/O error, dev fd0, sector 0
Apr 20 08:15:30 sparkie-zombie kernel: [  521.378196] Buffer I/O error on device fd0, logical block 0
Apr 20 08:16:04 sparkie-zombie kernel: [  555.302623] end_request: I/O error, dev fd0, sector 0
Apr 20 08:16:04 sparkie-zombie kernel: [  555.302647] Buffer I/O error on device fd0, logical block 0
Apr 20 08:16:38 sparkie-zombie kernel: [  589.234722] end_request: I/O error, dev fd0, sector 0
Apr 20 08:16:38 sparkie-zombie kernel: [  589.234746] Buffer I/O error on device fd0, logical block 0
It's going to be one of those things again.  ](*,)

I'm not sure why Ubuntu is once again insisting I need a floppy drive... and in respect to massively bloating log files amongst other things, I would like to know how to kill the floppy drive thingy.  In respect to bug reporting, I would like to report this so it can be fixed but I'm not sure how to proceed.

So, advice?

---

### Post by SteveHillier on 2010-04-20
Just a thought and please don't shoot me if you have already checked but does your BIOS think you have a floppy disk and if so have you tried disabling it?

---

### Post by kansasnoob on 2010-04-20
I'm thinking much the same as Steve Hillier. Have you ever explored your BIOS settings?

If you need some general instructions regarding BIOS settings this isn't bad:

[http://www.tomshardware.com/reviews/bios-a-z,1200.html](http://www.tomshardware.com/reviews/bios-a-z,1200.html)

Specifically "5. Establish Boot Priority Order":

[http://www.tomshardware.com/reviews/bios-a-z,1200-4.html](http://www.tomshardware.com/reviews/bios-a-z,1200-4.html)

I usually set my BIOS boot priority to boot CD first, USB second, and HD next.

Remember to look for "Boot Up Floppy Seek" and/or "warn if no floppy found" type things.

By memory I think Compaq depends on the F10 key to enter the BIOS.

---

### Post by psusi on 2010-04-20
Yep, your bios thinks you have a floppy.  You need to fix your bios.

---

### Post by VMC on 2010-04-20
> **psusi said:**
> Yep, your bios thinks you have a floppy.  You need to fix your bios.

Yes, we had a similar [floppy topic]("http://ubuntuforums.org/showthread.php?t=1442950&highlight=floppy") a couple of weeks ago that turned out to be BIOS settings.

---

### Post by cascade9 on 2010-04-20
Agreed, its not a 'bug', its a BIOS setting.

---

### Post by Seq on 2010-04-20
> **gt24 said:**
> I'm not sure why Ubuntu is once again insisting I need a floppy drive... and in respect to massively bloating log files amongst other things

It isn't insisting you *need* a floppy drive, it is trying to access a floppy drive your laptop insists you have. There is a difference.

Your bios is likely reporting you have a floppy drive as they are not hot-swappable, even though your bay likely is. So it just reports you always have one so incase you swap one in, it works. The problem is Linux is checking it out to see some capabilities (Do I have a disk, etc). Since there isn't *actually* a drive there, you get some problems.

> **gt24 said:**
> I would like to know how to kill the floppy drive thingy.  In respect to bug reporting, I would like to report this so it can be fixed but I'm not sure how to proceed.

Sometimes laptops don't have the best BIOS configurability. If you can't disable the floppy controller there, you can check out [Comment Seven]("https://bugs.edge.launchpad.net/linux/+bug/384579/comments/7") in [bug 384579]("https://bugs.edge.launchpad.net/linux/+bug/384579") for a workaround (blacklisting floppy module).

It looks like that bug pretty much covers your issue. Assuming you have a launchpad account, click where it asks "Does this bug affect you" at the top, and confirm it does. Avoid posting a "Me too" comment as that just clutters up the bug history.

---

### Post by gt24 on 2010-04-20
I will double check, but the problem with the Armada M700 is that they don't give me an option to say if I have a floppy drive attached or not in the BIOS (the BIOS on the laptop is best described as bare minimum).  So, I guess the better description is that the computer believes it has a floppy drive.  Generally, in some versions of Ubuntu this wasn't a huge deal because the drive would be checked and then would "fail out" I guess because I wouldn't get many errors.  However, in this version of Ubuntu, it constantly checks the floppy drive even if every check comes back as an error.

Thanks for pointing out the bug report number.  I will do some double checking when I get home to make sure everything is in order (for instance, I didn't try the CD drive... and I'm only 99% sure that it sees it as a CD drive as opposed to seeing it as a floppy drive) and do a "me too" on the bug.  I did make a launchpad account a while ago to follow a bug that was really annoying.

---

### Post by cariboo on 2010-04-20
> Ok, Compaq Armada M700 laptop here. It seems like Ubuntu, while it does work on this laptop, tends to have a new bug with every version. Pity too since I'm not exactly sure how to report bugs so they get fixed. So, I apologize in advance if this is in the "bug tracker" or otherwise was posted and if the bug doesn't get fixed because I only posted about it... well...


Check out [this]("https://help.ubuntu.com/community/ReportingBugs") page for a bug reporting howto.

---

