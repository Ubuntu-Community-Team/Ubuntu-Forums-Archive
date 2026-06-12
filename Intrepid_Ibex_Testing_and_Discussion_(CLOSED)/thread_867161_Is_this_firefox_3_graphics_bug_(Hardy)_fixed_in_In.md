---
title: "Is this firefox 3 graphics bug (Hardy) fixed in Intrepid?"
date: 2008-07-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sancho panza on 2008-07-22
Theres a bug in xorg graphics that affects firefox3 (running on Hardy), which needs to be fixed. The bug is discussed on [forums]("http://ubuntuforums.org/showthread.php?t=841739") and [launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908").
To fix this bug in Hardy, we wish to know if this bug has been fixed in Intrepid. Could anyone who has Intrepid running Firefox3 confirm if this bug exists/has been fixed in Intrepid?

Thanks,

---

### Post by mattduckman on 2008-07-22
i think i understand this bug correctly.

on this page if i go to View > Zoom > Zoom In , then the Ubuntu logo looks crappy.

if i'm reproducing this bug right, then, yes, it's still broken

---

### Post by sancho panza on 2008-07-23
Thanks matt, thats the bug im talking about. Has anyone else noticed it?

Cheers!

---

### Post by andrek on 2008-07-23
Yep, I can see the same problem with ubuntu logo here.

---

### Post by Jeffery Mewtamer on 2008-07-23
After doing a quick test, I do not think this is a glitch. Apparently, Firefox 3 can zoom both text and images, causing raster images to become distorted at zoom levels other than zero. View -> Zoom -> Zoom Text Only will toggle whether zoom effects images. I have Zoom Text Only turned on and have no graphical issues.

Note: I am running Hardy.

---

### Post by psyke83 on 2008-07-23
> **Jeffery Mewtamer said:**
> After doing a quick test, I do not think this is a glitch. Apparently, Firefox 3 can zoom both text and images, causing raster images to become distorted at zoom levels other than zero. View -> Zoom -> Zoom Text Only will toggle whether zoom effects images. I have Zoom Text Only turned on and have no graphical issues.

Note: I am running Hardy.

Ignoring that you run Hardy and there are several ways that your experience can differ (the OP implied that it's an Xserver bug, and Hardy uses an older version than Intrepid), you're missing the point.

The problem *is* the distorted images, not text. Disabling the image zoom is hardly a fix. Either way, to my eyes it looks as though the Windows version applies some kind of filtering (bilinear?) before displaying the zoomed images, and the Linux version is not doing the same.

Possibly released, if you select a block of text and drag, the block of text gets visually "pasted", following the mouse cursor. On the Windows version of Firefox, there seems to be some kind of filtering, whereas on Linux the text completely ignores the system's fontconfig settings (i.e. there's no antialiasing/filtering/hinting).

---

### Post by sancho panza on 2008-07-23
> **Jeffery Mewtamer said:**
> After doing a quick test, I do not think this is a glitch. Apparently, Firefox 3 can zoom both text and images, causing raster images to become distorted at zoom levels other than zero. View -> Zoom -> Zoom Text Only will toggle whether zoom effects images. I have Zoom Text Only turned on and have no graphical issues.

Note: I am running Hardy.

Zoom text is a very poor alternative to full page zoom on many websites. So using text zoom is not a solution. The reason why it IS an obvious glitch is that the same feature works waaaay better on firefox3 running on Windows. Go thru the links mentioned in the first post to know more about this.

Cheers!

---

### Post by NullHead on 2008-07-23
As a matter of fact, I get this in hardy too.

---

### Post by Gina on 2008-07-23
Same in Intrepid as Hardy.  Just done a new install and update of Intrepid on my laptop and have it beside my desktop which is running Hardy.  The Ubuntu logo is a bitmap image and zooming in shows the pixels - same on both.

---

### Post by tuxxy on 2008-07-23
Yes same here too, I use the Compiz enlarge plugin instead and runs fine.

---

### Post by klange on 2008-07-23
I get what you're saying, and as this is a bug in X.org / Cairo / Pixman, I wouldn't expect a fix for Intrepid as it doesn't exist in the release they're using.


And since no one seems to understand the bug: It happens in any Linux distro using the bugged cairo/pixman/X (which ever has the real bug in it) and involves not setting the proper filter mode for resizing textures. Yes, it'll happen in Hardy, that's even in the thread title. It still happens in Intrepid.

On Windows, FF3 zooms fine, as evidenced by the following attachment (Note: Despite the clearlooks theme and universal use of Tango, this is Windows XP, running FF3)

---

### Post by NullHead on 2008-07-23
> **WindowsSucks said:**
> I get what you're saying, and as this is a bug in X.org / Cairo / Pixman, I wouldn't expect a fix for Intrepid as it doesn't exist in the release they're using.


And since no one seems to understand the bug: It happens in any Linux distro using the bugged cairo/pixman/X (which ever has the real bug in it) and involves not setting the proper filter mode for resizing textures. Yes, it'll happen in Hardy, that's even in the thread title. It still happens in Intrepid.

On Windows, FF3 zooms fine, as evidenced by the following attachment (Note: Despite the clearlooks theme and universal use of Tango, this is Windows XP, running FF3)

Wow, that's one really customized desktop! 

Does anyone know how to fix this bug?

---

### Post by sancho panza on 2008-07-23
Apparently, the bug has been fixed, but it needs to be ported to Ubuntu. Thats what I understand from the links in the first post.
So the better question is if anyone knows how to get the patched version on ubuntu. As might be expected, upgrading to the patched pixman library alone doesnt fix the issue.

---

### Post by sancho panza on 2008-08-01
This bug really bothers me and if there's anything anyone can suggest to fix this issue, please advise.
[Bug report here.]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908")
[Related thread here.]("http://ubuntuforums.org/showthread.php?t=841739")

Cheers!

---

### Post by phenest on 2008-08-02
Hang on a minute. How can you call this a bug? Just because it doesn't do what you want it to do, that doesn't make it a bug.

'Bug' is a programmers term and can only be confirmed as a bug by the programmer. A 'bug' implies that the source code has an error. If FF3 was never meant to give smooth images on zooming, then it's not a bug. It's just something it doesn't do.

---

### Post by sancho panza on 2008-08-02
Please go thru the discussions in the other related threads and bug reports linked to in earlier posts. This post is not about if its a bug or not, but if its in Intrepid and about how it can be fixed in Hardy/Intrepid...Help

Cheers!

---

### Post by klange on 2008-08-02
> **phenest said:**
> Hang on a minute. How can you call this a bug? Just because it doesn't do what you want it to do, that doesn't make it a bug.

'Bug' is a programmers term and can only be confirmed as a bug by the programmer. A 'bug' implies that the source code has an error. If FF3 was never meant to give smooth images on zooming, then it's not a bug. It's just something it doesn't do.
It's a bug because it's an unexpected and unwanted result that occurs in a special case scenario.

If it works on Windows ands look like **** on Linux, it's a bug.

---

### Post by sancho panza on 2008-09-17
Is this bug going to ever get fixed? Why is there no response (positive/negative) on launchpad? Looks like its unlikely to be fixed on Intrepid...I'm not an expert, but from the looks of it, fixing this bug involves updating the relevant libraries etc. The actual bug has been fixed apparently...Is it really hard to do this?

---

### Post by phenest on 2008-09-17
> **WindowsSucks said:**
> If it works on Windows ands look like **** on Linux, it's a bug.

That's hardly the criteria for a bug.

This is not a bug, as nothing has gone wrong. That is to say, this is by design. What you should asking for is a feature request. Quite different.

---

### Post by sancho panza on 2008-09-17
@phenest: Its been agreed on these forums and launchpad that this is a bug. For you, I'll try wording it differently...When page-zoom feature on firefox is executed, the zoomed images are distorted/jagged/choppy. In short, the image-zoom is not working the way any functional image-zoom should. I'm not requesting image-zoom to be added(which would be a feature request), but am saying that its functioning is flawed beyond reasonable doubt.

Hope someone has the time/expertise to update the packages/libraries and introduce the bug patch to ubuntu...

---

### Post by klange on 2008-09-17
> **phenest said:**
> That's hardly the criteria for a bug.

This is not a bug, as nothing has gone wrong. That is to say, this is by design. What you should asking for is a feature request. Quite different.

It's not by design. It was not explicitly made to look horrible and pixelated. If it's a problem that needs to be fixed then it's a bug.

---

### Post by Sand &amp; Mercury on 2008-09-17
The problem is that Firefox's renderer in Linux builds don't apply a filter to graphics that are enlarged, I guess. I'm not sure if that would be a bug per se or just laziness on the part of the developers.

---

### Post by Gina on 2008-09-17
The logo is a bitmap image and becomes pixellated when you zoom in.  It's rather like the difference between bitmap and true-type fonts.  The Windows version uses a different logo (some form of vector graphics) for some reason.  I haven't checked the source code so can't add anything more.  Anyway, it's a Mozilla matter rather than Ubuntu and would need to be persued with Mozilla AFAIK.

---

### Post by phenest on 2008-09-17
If this really bothers you so, then here is the bug report an Launchpad: [bug 217908]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908")

---

### Post by Gina on 2008-09-17
As it only shows at high zooms I find it hard to see why it's a problem.  If someone uses a high zoom due to poor eyesight I doubt they'd notice. OTOH if some find it a problem I uphold their right to send the developers feedback - but I doubt anything will happen.

---

### Post by phenest on 2008-09-17
> **Gina said:**
> ... send the developers feedback - but I doubt anything will happen.

Judging by the bug report at Launchpad and at Mozilla, I agree.

---

### Post by sancho panza on 2008-09-17
The problem is not with mozilla, but with ubuntu. The reason for this is detailed in the various links in the first few posts of this thread. I'm aware of the bugreport and have made a few posts and am trying to push it for a while now.

@Gina: The problem has nothing to do with fonts/logos. It affects any graphic zoomed on Opera/Firefox.
Also, this happens at ANY zoom level, not just high zooms. I use it not bcos of eyesight, but bcos I have a high-ppi (126, i guess) display. This is a sharper display, but it causes text and images to be physically smaller than on regular displays (usually 96ppi). So I'd like most pages to be a bit bigger to read without squinting.

More information/links on this are here:
[http://brainstorm.ubuntu.com/idea/12125/]("http://brainstorm.ubuntu.com/idea/12125/")
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908")

---

### Post by sancho panza on 2008-09-23
I have to admit, in my more than one year (over 3 releases) of Ubuntu use, this is the first time I feel truly frustrated with Ubuntu. I have been trying to push this confirmed bug on these forums, launchpad and even on brainstorm for many months, and despite the fix being already available upstream for quite a few months(as I understand it), there has been absolutely no progress on this issue.

The browser is a fundamental piece of software and I fail to see why fixing the graphics issue affecting Opera and Firefox exclusively on Linux is utterly neglected. For the love of god, please help me.

---

### Post by chris-at on 2008-09-24
> **sancho panza said:**
> I have to admit, in my more than one year (over 3 releases) of Ubuntu use, this is the first time I feel truly frustrated with Ubuntu.

I completely agree. 

I find it ironic that even though this is open source and 'anybody' could fix the problem, nobody is actually willing to do so.

Are there any other browsers available on Linux that have a page zoom feature (besides Opera)? Unfortunately Konqueror can only zoom text.

---

### Post by sancho panza on 2008-09-24
> **chris-at said:**
> 
I find it ironic that even though this is open source and 'anybody' could fix the problem, nobody is actually willing to do so.


Its not that nobody's willing to do it. I just think that the people who can do it are just not aware of the problem, or they dont think that most people actually use the page zoom feature. What I have been trying is to get their attention...till date.

---

### Post by FuturePilot on 2008-09-24
Well it's not specific to Ubuntu for one thing. I can confirm this on many other distros as well such as OpenSuse and Fedora.

---

### Post by sancho panza on 2008-09-24
> **FuturePilot said:**
> Well it's not specific to Ubuntu for one thing. I can confirm this on many other distros as well such as OpenSuse and Fedora.

Yes I agree. Thats bcos the bug existed in xorg till a few months ago. But now I the bug has been fixed on xorg (if I understand correctly). So at least on intrepid and other future linux releases should have the bugfix included.

---

### Post by chris-at on 2008-09-25
> **sancho panza said:**
> Yes I agree. Thats bcos the bug existed in xorg till a few months ago. But now I the bug has been fixed on xorg (if I understand correctly). So at least on intrepid and other future linux releases should have the bugfix included.

Ah so that means that the bug has been fixed for Ubuntu 8.10?

Then I don't understand what you are complaining about - 8.10 will be released in a month anyways.

---

### Post by sancho panza on 2008-09-25
> **chris-at said:**
> Ah so that means that the bug has been fixed for Ubuntu 8.10?

Then I don't understand what you are complaining about - 8.10 will be released in a month anyways.

Sorry I should have elaborated. Although I said the bug should have been fixed in intrepid (8.10), but unfortunately it has not till date. And thats what the poll on this thread indicates. I checked the latest alpha release and the bug still exists.

---

### Post by crjackson on 2008-09-25
> **WindowsSucks said:**
> It's not by design. It was not explicitly made to look horrible and pixelated. If it's a problem that needs to be fixed then it's a bug.

Yup! No doubt about it.  It's a bug.

---

