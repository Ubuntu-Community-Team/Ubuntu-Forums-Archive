---
title: "Fresh install after perfectly good Ubuntu and oh my"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2010-06-14
The other day I somehow messed up my kernel after uninstalling a kernel I  shouldn't have been messing with anyway. 
It was a development kernel from a Meerkat thread and I thought I did  everything OK, but all I got upon boot was 
"need to load the kernel first". So, rather than asking a bunch of dumb  questions, I just thought I would download 
a new install iso and go from there. I had done it several times before  and thought "what the heck",

(I jumped in on Lucid in development around beta and was very happy with  the way it worked. I had it setup 
exactly the way I wanted it. And I LOVED IT!)

So, now no matter what I do I cannot get the Min. Max. Close buttons to  appear on either side right or left!
And I know more than one way to do it including the gfconfig wrong way. I  cannot use Alt-Tab to switch between 
apps and I have tried System > Preferences > Keyboard shortcuts,  but to no avail. 
I cannot move windows by clicking on the top and holding the mouse  button down or anything! :confused:

I had a very nice Lucid Lynx setup and if I had not seen that and was  starting out with this, I would definitely 
have serious thoughts about whether to continue using Ubuntu...

I just cannot understand why and where the HUGE difference between what I  had and what I now have has occurred!
I felt like I had learned a lot about Ubuntu and could figure out a lot  and now I feel like an ignorant moron.

I dual boot w7 and this and I had spent very little time on w7 in the  last month or so, but right about now, it is looking pretty good... 
And I hate to even hear myself say that...

---

### Post by Cavsfan on 2010-06-14
Wait a minute. I think I may have something figured out here...
Be right back...

---

### Post by fallenshadow on 2010-06-14
Try this!

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

It includes an easy way to move the buttons to the right hand side.

---

### Post by Cavsfan on 2010-06-14
> **fallenshadow said:**
> Try this!

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

It includes an easy way to move the buttons to the right hand side.

Thanks, but I had already tried that about a dozen times. That's what I did initially to move them to the right.
Then everything just went to heck! I do not know why, but now everything is just peachy!!!

I had a custom grub2 screen that I didn't have to maintain that a very knowledgeable guy named Ranch Hand helped me set up.
I think I made the mistake of not letting the system see all of the grub files before I made them unexecutable
via the chmod command.
That may have been the downfall or at least part of it.

A few minutes ago I set the attributes of /etc/grub.d/10_linux (the ones that pulls in the kernels to display on the grub2 splash screen) 
to executable and rebooted and viola life was back to normal.
I had to try a couple other things before I could say it was fixed, but that apparently did it.

I wish I could ask a Mod. to just delete this thread! I hate when I start a thread and then figure out the error myself!

But, everything is back to normal in never never land!:lolflag:  Or should I say Far Far Away!
I just wish I had saved my firefox bookmarks in HTML as firefox 3.6 does not read JSON files anymore.
What a mess that was!

---

