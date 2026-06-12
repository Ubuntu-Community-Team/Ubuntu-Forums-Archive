---
title: "Installing Ubuntu on Sony Vaio VGN-AR41E"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by cyberkilla on 2008-08-12
Hello, I sincerely hope that I've posted this in the correct section of the forum;)

My problem is this: I have experimented with various versions of Ubuntu and other distributions before, and I've never been able to get everything working without excessive effort.

I have a Sony Vaio VGN-AR41E laptop, and I would really like to get Ubuntu running 100%. I would like to untie myself from Windows Vista, which uses 45% of my RAM with no open applications!

I ran the Hardy Live CD and checked it's RAM usage - 9% of 2GB. Fantastic! I want it;)
I realise that Vista treats RAM differently, but the memory usage cited above is with the likes of Superfetch disabled.

I'm flying off at a tangent here, let me get to the point...


I intend to make some room on the drive and install Ubuntu. However, even before I do so I have noticed issues.

- Sound comes out of speakers even if I have headphones plugged in(possible fix found already).
- No Fn keys appear to work in the live CD(Mute/Volume Up&Down work fine, however).
- No 3D acceleration. Okay, it's live CD but since it's NVidia I was expecting some kind of auto-support to show off Compiz).
- Choosing 'Sleep' on the Exit menu gives me a wonderful black screen with a flashing cursor and no choice but to force shutdown.

I have NEVER been able to get linux to suspend or hibernate properly and reliably. I am not pointing fingers, but you have to admit that it is a deal breaker for most users.

If at all possible, could somebody help me out? I never usually post for support but I really want to get it working flawlessly this time.

Here are my basic specs:
- Sony Vaio VGN-AR41E
- Intel Core 2 Duo @ 1.8GHz(T7100, Speedstep)
- 2GB DDR2 SDRAM @ 667MHz
- 120GB HDD(5400RPM)
- WLAN 802.11a/b/g(Intel, I believe)
- DVD+-RW/+-R DL/RAM
- NVidia GeForce 8400M GT @ 1440x900
- Current OS: Windows Vista Home Premium

Ah, one more thing(pushing my luck;))...
I had an HP Pavilion Tower that died with linux running a flash video in Firefox. It appeared to die of heat. The problem was either the motherboard or the cpu - everything else was okay.

I have heard many horror stories about overheating with linux running. My old laptop used to get incredibly hot too. It was warm in Windows XP, but too hot to hold in Ubuntu Feisty. Seemed to be related to the Wifi card.

In addition, there are tales of linux wearing out hard drives faster too. I am very concerned, but I really want to use Ubuntu for various development tasks(proper rsync, ssh without putty, etc).

Is there any chance that you could lay some of my fears to rest, or at least explain them?

I apologise for the ridiculously long post:).
Any suggestions or warnings or potential issues would be greatly appreciated if you have the time.

---

### Post by Partyboi2 on 2008-08-12
Here are a few links that discuss some of the issues you are having and some suggestions.
[http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E](http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E)
[http://ubuntuforums.org/showthread.php?t=465491](http://ubuntuforums.org/showthread.php?t=465491)

---

### Post by cyberkilla on 2008-08-12
> **Partyboi2 said:**
> Here are a few links that discuss some of the issues you are having and some suggestions.
[http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E](http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E)
[http://ubuntuforums.org/showthread.php?t=465491](http://ubuntuforums.org/showthread.php?t=465491)

Thanks for posting:)
I am afraid that I've already seen those threads, however.

The first link has a few solutions, but does not speak of a fix for the Sleep/Hibernate issue.

The second link makes it sound like a battle in vain. I am more than ready to fiddle around until a solution is found, but I don't have the time to reverse engineer things.

---

### Post by cyberkilla on 2008-08-13
Does anybody else own a similar laptop? Have you found any solutions to the sleep/hibernate issue?

EDIT:
I decided to use the Live CD for a few hours today. I noticed a somewhat warmer region on the laptop, just above the top-right of the touch pad.

After I noticed this, I rebooted into Windows Vista and used that for a few hours - the warmth disappeared within a few minutes.

I do not know for sure what lies below the warm region, but I suspect it's the hard drive(or possibly wifi). In addition, there was a slight vibration that is not present in Vista. I suspect that the hard disk is spinning excessively.

Does nobody else own one of these laptops?:)

---

### Post by cyberkilla on 2008-08-13
Posted more information in the post above. Didn't realise I wouldn't be bumped if I edited the last post:)

---

### Post by cyberkilla on 2008-08-19
Is anybody out there? Am I not asking specific enough questions?

Why is the laptop running hotter under Ubuntu than in Vista?
Is there a general problem with laptops that Ubuntu can't handle?


Does anybody know of any recent news about the state of APCI/Fn key support for Sony Vaio Laptops?

---

### Post by dstew on 2008-08-19
My advice would be go ahead and install Ubuntu on a hard disk partition, get the updates, and see where you are. Probably you will have to fiddle to get things working, a usual problem with laptops. If you get everything working, write a HowTo! If you can't get it to work satisfactorily, just delete Ubuntu, and you are back to where you were to start with. Despite what people say, I don't think Ubuntu will physically damage your laptop while you try it out.

Another suggestion is to send an email or personal message to anyone who posted that has this laptop. Often, they have fixed things, but did not bother to post back to say what they did.

---

### Post by cyberkilla on 2008-08-20
> **dstew said:**
> My advice would be go ahead and install Ubuntu on a hard disk partition, get the updates, and see where you are. Probably you will have to fiddle to get things working, a usual problem with laptops. If you get everything working, write a HowTo! If you can't get it to work satisfactorily, just delete Ubuntu, and you are back to where you were to start with. Despite what people say, I don't think Ubuntu will physically damage your laptop while you try it out.

Another suggestion is to send an email or personal message to anyone who posted that has this laptop. Often, they have fixed things, but did not bother to post back to say what they did.

Thanks for the response.

I'll make a bit of room over the weekend and install it.
I know there are a lot of rumours about the damage it can cause, and the vast majority of them are uneducated opinions or just plain wrong.

However, I am somewhat concerned about the heat coming from the wifi card. I suppose I will just have to install it before I ask for any more help.
The live cd is probably not as fine tuned to my hardware as an installation would be.
For instance, I have a well known graphics card but no acceleration on the live cd.

Thanks again, I'll update this thread with my progress.

---

### Post by cyberkilla on 2009-02-13
Well, I've finally installed it.

The hard disk killing 'read cycles' issue has been resolved by Ubuntu, as the problem ceased after installing updates.

The hard drive was one of the affected Seagate models.


The only remaining problems that are apparent to me are:
- Vaio Fn keys not being trapped, so they can't be mapped to anything.
- Sound only comes out of main speakers(ignores headphones when plugged in and no sound is emitted through them).
- Sound volume level is silent at 50%, so I have to move the volume to about 80% to get a decent sound level.
- Brightness works with smartdimmer(which I installed from nvclock). However, the Fn brightness doesn't work(because of previous problem) and the gnome brightness applet doesn't support using smartdimmer afaik.

Other than that, I'm incredibly happy. It hasn't been a difficult install this time. When I tried it early last year, it was hell. Hardly anything worked. At least progress with Ubuntu has been made.

Does anyone have any solutions to these problems?

Ubuntu 8.10, Sony Vaio VGN-AR41E.

EDIT:

[http://www.alsa-project.org/db/?f=db8c91a0f1b2a9c7d666eab87d43918aee481375](http://www.alsa-project.org/db/?f=db8c91a0f1b2a9c7d666eab87d43918aee481375)

Above, is the information about my sound card.

Does anyone have any solutions?

---

### Post by cyberkilla on 2009-02-14
I have managed to fix the sound by entering:

"options snd-hda-intel model=vaio enable=1 index=0 position_fix=1"

Don't ask me what it does, because I really don't know. However, after appending it to &#8220;/etc/modprobe.d/alsa-base&#8221;, I found that the headphones worked! What's more, the damned things muted the main speakers.

Only remaining sound issues are, I can't get the mic to work and the 'optical out' isn't working either.

EDIT:
There is a new alsa driver available but Ubuntu doesn't have it in the repository. I'd rather not install it manually if it is scheduled to update on it's own in the future.

Is there somewhere I can go to find out when/what is being added to the updates for Intrepid?

It's a bit of an echo chamber here, lately;)

---

