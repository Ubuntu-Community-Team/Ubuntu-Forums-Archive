---
title: "automatically remove old kernels"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Buggin on 2007-09-19
Although I've never read it in a news article or blog I feel like the biggest problem for linux new-comers is that no matter what you almost have to have some basic understanding of the way the OS works. 
For instance: somebody makes the switch. Ubuntu gets them going with a nice dual boot setup (just in case). They like what they see and decide to stick with it. They can get on the internet, their music works, they are happy. Over time they figure out updates and even go through a couple dist-upgrades via update manager. But now they have a humongous list in GRUB every time they boot up and have no idea why.  (Case and point lies in this post right here: [COLOR="Blue"][Best way to remove old kernels?]("http://ubuntuforums.org/showthread.php?t=137601")[/COLOR] )
> "What's a kernel?"

So why is that necessary? It seems that it would be simple enough to write a program that detects a new kernel has been installed. Then, it could monitor the next say 5 reboots to make sure the system seems to be stable. For instance, no failed modules, no bulletproof X on every boot, etc. If the reboots have all been successful it could then prompt the user asking if old, unnecessary kernels should be removed at that time. Then, through the magic of apt, it could  remove the old ones by itself, without the user ever knowing what a kernel is.
For the advanced user it could have options to keep more than one old kernel. Maybe even remove the new kernel if it detects the user going back to the old one multiple times.

It's just a thought that hit me driving to work from lunch today. I'm not sure if this is even the right place for it but I do know that I'm no programmer (bash scripter maybe, but definitely not a programmer).  Any thoughts?

---

### Post by Pumalite on 2007-09-19
It's good to keep old kernels around in case you end up with nothing else to boot from. Unless you have space problems or it exceeds the limits of Grub.

---

### Post by Buggin on 2007-09-19
Well like I said. Options to keep a certain number of old kernels. But keeping all of them definitely isn't necessary. And only prompting to remove old kernels after 5 (or however many) successful reboots and logins. 
I started one box on hoary and have upgraded it all the way to feisty and will be gutsy soon. The GRUB list with two entries for each kernel, let's not forget recovery mode, would be a bit long.

Not to mention, the oldest of the kernels no longer boot successfully on my system anyway. So why should I bother keeping them around. 
This is meant more for the people who don't even know what a kernel is, why they have it, and why they have so many of them now.

---

### Post by Lord Illidan on 2007-09-19
I think the best method would be to just leave them there, and just hide the menu, where it can be launched by pressing escape, of course. Old kernels can be useful.

---

### Post by Pumalite on 2007-09-19
You can remove them from Synaptic.

---

### Post by Buggin on 2007-09-19
I know how to remove them. You people are missing the point entirely and I will not bother replying until you actually read (and understand) my whole post.

---

### Post by Shazaam on 2007-09-19
nm, not an answer for the OP.

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> I think the best method would be to just leave them there, and just hide the menu, where it can be launched by pressing escape, of course. Old kernels can be useful.

I'm referring to newcomers switching from windows. They don't know how to hide their menu and may like to boot the old OS every now and again. READ... then reply

---

### Post by Lord Illidan on 2007-09-19
> **Buggin said:**
> I know how to remove them. You people are missing the point entirely and I will not bother replying until you actually read (and understand) my whole post.

I do get your point, and you make several valid points in fact, but the fact is, that is it true that users are that intimidated by it?

---

### Post by Buggin on 2007-09-19
> **Shazaam said:**
> I agree with Pumalite. Keep at least one old working kernel around so you can at least boot up if an update or an install trashes your current one.
You can open menu.lst and comment out the ones that you dont use to clean up grub as a temporary workaround.

Thank you for at least partially understanding what I'm talking about. That would work temporarily, but if you get a new kernel and GRUB rebuilds it's menu list for any reason you will get the whole old list back again.

And I do agree, definitely keep at least one old kernel in case an update goes haywire.

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> I do get your point, and you make several valid points in fact, but the fact is, that is it true that users are that intimidated by it?

If you search you'll find plenty of questions about this long list. And inside those threads the people reading them ask the question "What is a kernel?"
Which means to understand this list they have to have some basic understanding of the OS.. and why should they need to really? Just to surf the internet and check e-mail

Either way.. it's just a thought. Seemed like it should be easy enough to do but I can't program GUI anything.

---

### Post by Pumalite on 2007-09-19
People that use Linux tend to like to learn the OS.

---

### Post by Lord Illidan on 2007-09-19
> **Buggin said:**
> If you search you'll find plenty of questions about this long list. And inside those threads the people reading them ask the question "What is a kernel?"
Which means to understand this list they have to have some basic understanding of the OS.. and why should they need to really? Just to surf the internet and check e-mail

Either way.. it's just a thought. Seemed like it should be easy enough to do but I can't program GUI anything.

In hindsight, your argument is quite powerful. Yep, you're right about that. But the problem is that if you give them a prompt, will they understand it?

---

### Post by Buggin on 2007-09-19
> **Pumalite said:**
> People that use Linux tend to like to learn the OS.

Thee you go... I think that is exactly the problem. People who CURRENTLY use Linux like to learn the OS. I LIKE to learn the OS.

But some people don't. And if we really want main stream support and true open source drivers (Nvidia, broadcom, etc.) we also have to cater to those that NEVER want to learn the OS. That's what I'm talking about.

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> In hindsight, your argument is quite powerful. Yep, you're right about that. But the problem is that if you give them a prompt, will they understand it?

My reply is probably not what you expect... but if they can't click a simple yes or no (it's up to us to set the proper, SAFE, default values) then they need more help than I'm trying to give today.

---

### Post by Pumalite on 2007-09-19
That support is coming anyway. Linux is the future.

---

### Post by Buggin on 2007-09-19
but why not hurry it along by making things that could easily be simple.. be simple

---

### Post by Lord Illidan on 2007-09-19
> **Buggin said:**
> My reply is probably not what you expect... but if they can't click a simple yes or no (it's up to us to set the proper, SAFE, default values) then they need more help than I'm trying to give today.

Sure, but will they actually read the prompt? And understand what it means? Or will they just press Yes/No automatically?
Also, instead of removing the kernels, how about just commenting the entries in grub? That way they are still available...

Perhaps a sample prompt might be like this :

You currently have more than 2 kernels installed on your computer.

<listing of the kernels>

Would you like to trim the bootup menu in order to remove references to your older kernels?

Perhaps the word kernels could be a hyperlink to a help-page..so that users can find out what a kernel is.

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> Sure, but will they actually read the prompt? And understand what it means? Or will they just press Yes/No automatically?

Well that's kind of what I'm getting at.
If we set the default values to delete all except one old kernel, again assuming there have been successful reboots and logins, and they just click Yes (because that's what their Windows background tells them to do in their gut) then they will still have one backup kernel, a cleaner system, and be none the wiser.
If they click No, because they are scared or don't understand, no harm no foul. Nothing was done. If they are curious they will come to the forums and ask. That's when you get to use the favorite reply. "You can remove the old kernels in Synaptic"

---

### Post by Buggin on 2007-09-19
For past present and future reference, don't let my argumentative nature throw you off. I just like a good discussion and like getting new ideas out in the wild to bloom or die. I appreciate all of your (thought out) comments.

---

### Post by Lord Illidan on 2007-09-19
> **Buggin said:**
> Well that's kind of what I'm getting at.
If we set the default values to delete all except one old kernel, again assuming there have been successful reboots and logins, and they just click Yes (because that's what their Windows background tells them to do in their gut) then they will still have one backup kernel, a cleaner system, and be none the wiser.
If they click No, because they are scared or don't understand, no harm no foul. Nothing was done. If they are curious they will come to the forums and ask. That's when you get to use the favorite reply. "You can remove the old kernels in Synaptic"

I like that..especially if checking has been done to ensure that the new kernel works 100%.

But, are you in favour of removing the kernels entirely or just commenting them out?

Don't worry about your argumentative nature, I love a good argument!

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> Perhaps a sample prompt might be like this :

You currently have more than 2 kernels installed on your computer.

<listing of the kernels>

Would you like to trim the bootup menu in order to remove references to your older kernels?

Perhaps the word kernels could be a hyperlink to a help-page..so that users can find out what a kernel is.


That's what I'm talking about. Give them an option, nether answer will kill them. Give them access to the information if they want it. And give the Advanced users a way to turn it of because we love a never show me this again button.

---

### Post by Buggin on 2007-09-19
> **Lord Illidan said:**
> But, are you in favour of removing the kernels entirely or just commenting them out?

That's kind of where I leave it up in the air. I personally, remove my old kernels completely (purged). Sometimes after a couple reboots... sometimes months later... but when I do it I usually get rid of it completely.
If there is a way to comment it out and keep it from being added back to the menu list again later that seems like a good option as well. My main goal was just to shorten the list for those users.

---

### Post by VMan on 2007-09-19
This would be a nice option for my wife's computer.  She likes Linux (I knew there was a reason I married her), but doesn't want to mess with the underlying stuff.  Currently I do everything except the auto updates.  She went from Vista, to dual boot Vista & Ubuntu, to Ubuntu only.

---

### Post by Buggin on 2007-09-19
I knew I had a fan base somewhere.. hehe

---

### Post by mocoloco on 2007-09-19
Absolutely, get those old kernels out of there!  I usually give a kernel upgrade two weeks to be sure it's stable, then search in synaptic and remove the old one.  It frees up about 200 MB every time.  That's a decent chuck of space that would add up if I didn't.  I imagine someone running Xubuntu on an older system with an 8GB HD wondering where all her space went.
Buggin, I think you should add this to launchpad as a wishlist item.  Let's keep working to make Ubuntu easier.

---

### Post by Lord Illidan on 2007-09-19
> **mocoloco said:**
> Absolutely, get those old kernels out of there!  I usually give a kernel upgrade two weeks to be sure it's stable, then search in synaptic and remove the old one.  It frees up about 200 MB every time.  That's a decent chuck of space that would add up if I didn't.  I imagine someone running Xubuntu on an older system with an 8GB HD wondering where all her space went.
Buggin, I think you should add this to launchpad as a wishlist item.  Let's keep working to make Ubuntu easier.

I've tried it, and yes, it's true...I second this then.

---

### Post by Buggin on 2007-09-19
launchpad is not user friendly either... i see that the wishlist and bug reports are in the same place.. but i can't see any way to mark a bug report as a wishlist item...

---

### Post by Buggin on 2007-09-19
thanks for your feedback... i added it to launchpad.. i think i put it in the right place.. i'm sure someone will tell me if i didn't

if there are any developers that would like to take a stab at it feel free... i'll gladly help test it. I'm running several gutsy boxes that i'm sure will get another kernel update soon. I've got one waiting to upgrade as well so plenty of test boxes.

---

### Post by mocoloco on 2007-09-19
I would suggest not to have it prompt the user with anything.  That's not really the Gnome way, which is to have good default settings and not bug the user with too many choices.  So maybe have it default to 
a) remove any but the current kernel after a time period/number of boots or a combination of the two
or
b) leave one prior kernel version indefinitely, and remove any previous.

The setting to change it's behavior could be in synaptic, along with one of the other "cleanup" settings about whether to keep downloaded package files after installing.

---

### Post by Lord Illidan on 2007-09-20
> **mocoloco said:**
> I would suggest not to have it prompt the user with anything.  That's not really the Gnome way, which is to have good default settings and not bug the user with too many choices.  So maybe have it default to 
a) remove any but the current kernel after a time period/number of boots or a combination of the two
or
b) leave one prior kernel version indefinitely, and remove any previous.

The setting to change it's behavior could be in synaptic, along with one of the other "cleanup" settings about whether to keep downloaded package files after installing.

Which is easier, changing it's behaviour in synaptic, or reading a prompt and pressing Yes/No?

I dislike the way of not offering any configuration settings and then leaving a bunch of options in gconf-editor...

---

### Post by Buggin on 2007-09-20
Well it's not like it's something that happens all that often so a popup dialog wouldn't be that bad... 
As far as making this a synaptic feature... well I guess we'd have to talk to the developers of synaptic to see what they think
but this could almost be a small, stand-alone program that, through the power of apt, purges this stuff on it's own without synaptic being involved at all

I am personally for a dialog box with a details dropdown for more advanced options. But that is personal preference.. I can't code it so I'm not going to be a stickle on specifics... I just think old kernels should be gotten out of there without any user intervention... except for maybe clicking a Yes

---

### Post by NT4usB on 2007-09-20
Tangentially related...
I'm running Edgy on one of my boxes.
Used Envy to install/update Nvidia drivers. Never worked 'automatically' but manual install worked.
Near as I can tell, the reason auto didn't work was because the newest kernel was installed but it wasn't booting to it.
During one boot, I happen to notice which kernel was booting and it wasn't the current one. Apparently, the latest kernel was installed but some setting in the boot info wasn't automatically switching to the newest kernel.
I googled, found, and fixed the boot deal so whenever a new kernel is installed, it boots to it.
I don't know how, or why that bit got changed. I assume it is supposed to boot to the newest by default.
I manually remove older kernels every now and then, just to tidy up.
I'd have been hating life if I had removed the one that was booting...

---

### Post by Buggin on 2007-09-26
It should auto boot the new one. After a new kernel is installed it regenerates the boot menu based on the existing kernel and boots the top of the list (newest kernel). Either the update crashed mid stream (count yourself lucky it worked at all) or some seting got changed that locked it to that old kernel.

---

### Post by davec64 on 2007-09-26
I've got to add my 2 penneth!

Great idea, applying the old favorite KISS (Keep It Simple Stupid) anything that makes life easier for somebody coming to Ubuntu can't be a bad thing.

To expand the User base of the OS we have to take the leap and make things just happen under the hood for new users. As previously said, many users just want to surf the internet, write a few emails and use a couple of office apps. Not everyone is like us, they don't want to tinker with things that work, and as long as it does what they want when they want, they'll never look at a terminal or even delve into Synaptic. So as long as there's a way for us sad and lonely individuals to switch it off and tinker with as many kernels as we want, everyone should be happy!

Dave

---

### Post by Buggin on 2007-09-26
here here

> **davec64 said:**
> I've got to add my 2 penneth!

Great idea, applying the old favorite KISS (Keep It Simple Stupid) anything that makes life easier for somebody coming to Ubuntu can't be a bad thing.

To expand the User base of the OS we have to take the leap and make things just happen under the hood for new users. As previously said, many users just want to surf the internet, write a few emails and use a couple of office apps. Not everyone is like us, they don't want to tinker with things that work, and as long as it does what they want when they want, they'll never look at a terminal or even delve into Synaptic. So as long as there's a way for us sad and lonely individuals to switch it off and tinker with as many kernels as we want, everyone should be happy!

Dave

---

### Post by NT4usB on 2007-09-26
> **Buggin said:**
> It should auto boot the new one. After a new kernel is installed it regenerates the boot menu based on the existing kernel and boots the top of the list (newest kernel). Either the update crashed mid stream (count yourself lucky it worked at all) or some seting got changed that locked it to that old kernel.
It *should*,  but it wasn't.
Evidently, there is a setting in (menu.lst?) that can be configured to not update the list/boot to the newly installed kernel.
I googled around, found the fix, and changed the setting. Now it boots to the newly installed kernel.

---

### Post by diafygi on 2008-06-19
I created a bug for this problem: [Bug #241368]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/241368")

---

