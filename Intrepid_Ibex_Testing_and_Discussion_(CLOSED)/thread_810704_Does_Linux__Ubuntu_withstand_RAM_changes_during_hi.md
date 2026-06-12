---
title: "Does Linux / Ubuntu withstand RAM changes during hibernate?"
date: 2008-05-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2008-05-28
Just recently, I bumped into an interesting issue. Somebody had installed memory into his Windows XP laptop, and when he started up the computer he was given a very cryptic prompt:
(Going by memory)> 
An inconsistency has been detected

[Option 1] Delete restore files and restart the system
[Option 2] Continue starting Windows normally
I think we can all agree, that first option sounds a bit creepy and could be anything, so it turns out that he never tried it. The second option led to a BSOD. (Coincidentally, a BSOD about our best friend, acpi. I didn't know Windows had trouble with the thing, too. Who does it work for?!).

Turns out that this person had put his computer into *hibernate mode* before installing the new memory. Evidently, Windows had some handling for the failure, but it was not user friendly and caused quite a bit of confusion. The options were cryptic enough that they sounded destructive, such as that the first option would be killing off the system restore partition or something along those lines.

Anyway, this got me thinking about Ubuntu. Installing it in a VM right now to find out, but do we have anyone daring enough to test this scenario, or who has encountered a problem like this? Worst case scenario, it doesn't boot. Ideally, it just wouldn't mind the change.

---

### Post by cariboo on 2008-05-28
It is my understanding that there is always a bit of voltage running through the motherboard whenever the computer is plugged in, so the chance of destroying the ram chip is quite high. The other thing is most operating system detect ram at boot up so even if you replace the ram without destroying it, the operating system is not going to detect it properly which could lead to a probable crash of the operating system.

Just my opinion.

Jim

---

### Post by Mr. Picklesworth on 2008-05-28
I think you are mixing up hibernate and suspend. That, or I am :)
Hibernate mode dumps memory to disk and shuts down completely, then when the computer is restarted reads it back into memory. This is why hibernate mode takes a while to do its thing, whereas suspend is nearly instant. (That's also how the mentioned person managed to install memory without blowing up his computer).

---

### Post by Gina on 2008-05-28
Yes, hibernate saves memory contents to HD then shuts down completely.  So there might not have been any power on the mobo and the memory modules might be OK.  It is best to disconnect from the mains and remove the laptop battery to replace or add to memory plus take anti-static precautions.

Anyway, the memory could well be fine - you will get an error if the memory at hibernate does not match that at resume (power up).  Firstly try Option 1 above - the restore file referred to is the hibernate file of the contents of memory (that can't be restored if the memory size has changed) if there are still errors, I suggest disconnecting the mains power and removing the battery to completely remove all power and reset things.  Windows can very easily get upset and this is often the only way to reset it.

See if that works - if not come back and we'll have a rethink.

---

### Post by Mr. Picklesworth on 2008-05-28
This isn't a support request, but pondering about whether Ubuntu handles this type of error in a decent way ;)

Thanks anyway for the large ammount of information, though. Could be of use to somebody!

---

### Post by Gina on 2008-05-28
In that case I'm not of much help I'm afraid - I have a fair bit of hardware experience but only just over a year of Ubuntu and just a little more of Linux in general.

---

### Post by ssam on 2008-05-28
only one way to find out :-)

The linux kernel has support for adding and removing RAM from a running system
[http://lhms.sourceforge.net/](http://lhms.sourceforge.net/)
[http://kerneltrap.org/node/14009](http://kerneltrap.org/node/14009)

For it to work you would need the hardware to support it. I think it mostly useful for virtual machines.

---

### Post by Mr. Picklesworth on 2008-05-28
Okay, just did some fiddling. In VirtualBox, it appears that we fall back to a horrible sight as soon as bootup begins. Lots and lots of text, presumably for debugging the fatal error that has occurred... but no actual mention of there having been an error or any attempt by the system to decipher it. The dump just goes on and on for eternity.

On the bright side, it stops trying to restore after that; next time the system is restarted, we have a fresh session, so the error only happens once.

I think it is a real risk that the system's available memory can change between shutting down and starting up, even without the user's immediate control, so tidy handling of this type of issue could work well. Is anyone able to confirm this, or do you have different (or more detailed) results to share?

I imagine killing the swap partition is similar to removing RAM from a running system, and yes that is quite a cool little operation.

---

### Post by scorpion-kde on 2008-06-10
It depends on how you do it, but removing the swap file isn't quite like removing physical RAM.  I would imagine that (perhaps with a kernel patch to force the matter), Linux could withstand an increase in RAM during hibernate.  A decrease, on the other hand, could definitely mess things up quite badly.  What do you think a good way to handle RAM changes over suspend would be?  I think spitting out a bunch of error messages and refusing to resume from hibernation (instead starting up normally next boot) is quite reasonable, as you really shouldn't do something like that.  Also, how, precisely, could RAM size change during hibernation without action on the user's part?

---

### Post by MaX on 2008-06-11
I have to say that if you intend to INSTALL more memory into your system you should do a proper Shutdown first. IMHO you have yourself to blame if this happens.

---

### Post by lithorus on 2008-06-13
> **MaX said:**
> I have to say that if you intend to INSTALL more memory into your system you should do a proper Shutdown first. IMHO you have yourself to blame if this happens.

Even better :
Remove the battery if it's a laptop...

---

### Post by Mr. Picklesworth on 2008-06-13
The reason I am asking this is because there is the possibility of this action leading over to an unbootable system, which would be completely stupid. *Whether the action itself is stupid or not*, it should be supported in the sense that the system continues to work. Consider this: User puts computer in hibernate for 2 months, then remembers he wanted to upgrade memory. Does that... "oops, it was in hibernate!" -- boom, the OS is unbootable. Wouldn't that just be plain stupid on the system's end?

Launchpad currently lacks a system to organize testing of certain aspects of the system, so I think that's where the forums come in handy.

Thankfully, the system appears to be working around the problem silently, which is good.

---

### Post by MaX on 2008-06-14
No I'd say that it's just what he/she was asking for :)

Sure it's stupid of the system. But it's sort of like changing the engine of a parked car that is still running and complain that it stopped. Would you try that?

---

