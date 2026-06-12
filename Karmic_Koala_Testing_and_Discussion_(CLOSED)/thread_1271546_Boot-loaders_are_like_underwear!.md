---
title: "Boot-loaders are like underwear!"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-09-21
I can remember a year or more ago having arguments about whether or not to use EasyBCD. I sometimes found it to be a darn good option.

Lilo generally makes me crazy, but it seems to work well for non-persitent usb drives.

For every day use I tend to love grub legacy! I'm familiar with it! It just works in 95% of the situations I encounter!

Now comes the underwear comparison:P

In some situations briefs are the thing, other times it's best to go "commando", but for the most part I'm a boxer short kind of guy.

So, if I were buying undies for everyone I'd buy boxers!

Canonical provided everyone with GRUB 2!

But if you don't like it you don't have to wear it!

You can use whatever boot-loader you wish! You can choose to install no boot-loader at all and then configure your existing boot-loader to boot your new Karmic.

I've twice removed Grub 2 from Karmic and made it "bootable" from an existing grub legacy:

[http://ubuntuforums.org/showthread.php?t=1269856](http://ubuntuforums.org/showthread.php?t=1269856)

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

So if you don't like that new thong just toss it!

---

### Post by talkingwires on 2009-09-21
Well... that was an interesting comparison.

I'm not really sold on GRUB2. I can understand some the reasoning behind it (it supports more architectures natively, graphical boot if the Ubuntu developers would ever get off their *** and utilize it) but it seems to be causing a lot of problems for people and the GRUB2 developers seemed to go out of their way to make it hard for people familiar with the original GRUB to configure the thing.

---

### Post by talkingwires on 2009-09-21
Oh, and to clarify my remark about the Ubuntu developers:

I've been using Ubuntu since the very beginning. The boot experience is something they've been working on for a long time, but they've never done much to the actual bootloader. Every other distro I can think of as customized bootloader, but the Ubuntu developers have never bothered making their own. It's a little strange, considering how little work would be required to make a custom bootloader splashscreen, but then again, you only see it for a few seconds. I guess they're busy disabling touchpads and shortcuts to restart the X server.

---

### Post by kansasnoob on 2009-09-21
> **talkingwires said:**
> Well... that was an interesting comparison.

I'm not really sold on GRUB2. I can understand some the reasoning behind it (it supports more architectures natively, graphical boot if the Ubuntu developers would ever get off their *** and utilize it) but it seems to be causing a lot of problems for people and the GRUB2 developers seemed to go out of their way to make it hard for people familiar with the original GRUB to configure the thing.

Well, what I'm trying to do is introduce a certain degree of levity into this "I hate" environment.

Not one single change to Karmic is so "hard-wired" that anyone "must" do anything!

That's absolutely true regarding Grub 2!

The beauty of Linux is you can make it your own.

The transition to pulseaudio was the same. This may be worse since it effects actually booting the OS, but it's still the "change" thing.

Change is always hard.

---

### Post by kansasnoob on 2009-09-21
> **talkingwires said:**
> Oh, and to clarify my remark about the Ubuntu developers:

I've been using Ubuntu since the very beginning. The boot experience is something they've been working on for a long time, but they've never done much to the actual bootloader. Every other distro I can think of as customized bootloader, but the Ubuntu developers have never bothered making their own. It's a little strange, considering how little work would be required to make a custom bootloader splashscreen, but then again, you only see it for a few seconds. I guess they're busy disabling touchpads and shortcuts to restart the X server.


Well, I think I've tried every **nux out there and they all have their strong points and their weak points. And here I am!

And here I'll stay!

---

### Post by jocko on 2009-09-21
> **kansasnoob said:**
> Change is always hard.
Yep, but you need to change your underwear now and then...

---

### Post by dinxter on 2009-09-21
> Now comes the underwear comparison:P
grub2 with gfxmenu is like having pictures of bunny rabbits on your underwear i suppose :)

---

### Post by dinxter on 2009-09-21
> **jocko said:**
> Yep, but you need to change your underwear now and then...
  but if you turn grub2 inside out you can get a few more days surely?...

---

### Post by Squonk07 on 2009-09-21
This has to be one of the more creative ways of looking at an issue I have come across in a while. :P

As far as GRUB2, I haven't had any real problems, with the possible exception being the slight annoyance of having to regenerate the list after every Alpha so far (I dual boot with XP). On the other hand, I've been using from-scratch installations, so I guess I'm in a different boat than some people. I still need to learn how to manually update the list (if the need ever arises), but for now GRUB2 does what I need it to do.

---

### Post by MacUntu on 2009-09-21
Don't forget that EasyBCD is a third-party application (that doesn't work if your system is already borked) - plain bcdedit.exe is a pain and you cannot just edit the BCD file to add an entry like you can with GRUB2.

> Not one single change to Karmic is so "hard-wired" that anyone "must" do anything!

Well, GRUB2 is default for new installations. New (unexperienced) users with broken boot loaders are a problem.

---

### Post by Funnnny on 2009-09-21
No one force you to use an Alpha version, no one force you to install Grub2, no one force you to use Ubuntu.
good luck for your complaining

---

### Post by xebian on 2009-09-21
Grub2 is a no-brainer.  My only complaint is why use root=/dev/sdxx instead of the modern root=UUID in the other OS section?  Maybe this is what causing boot problems because depending on the attached devices where you would expect sdb might be sdc or something else.  This happened to me one time when I forgot to unplug an eSata.  That's why I strongly suggest they use UUID for the root params.  It should be easy as the UUID is already known on the search line before the kernel line entry.  Just a 1 line hack on the other-os prober.

---

### Post by talkingwires on 2009-09-22
> **Funnnny said:**
> No one force you to use an Alpha version, no one force you to install Grub2, no one force you to use Ubuntu.
good luck for your complainingThat's great, really interesting. We're lucky you posted, actually. Are you the new DON'T USE ALPHA RELEASES BOT 2.0?

---

### Post by Funnnny on 2009-09-22
Oh yeah, no one force you to use Alpha, you choose to use it YOURSELF, so why do you complaining ?
Actually you called it ALPHA

---

### Post by 23meg on 2009-09-22
> **talkingwires said:**
> Oh, and to clarify my remark about the Ubuntu developers:

Right, because apparently, in the alternate reality you live in, every little decision about Ubuntu is taken by the initiative of a homogeneous, always-in-agreement collective entity called "the Ubuntu developers", not by different teams or individuals who work on different areas of the system, and in every decision you don't like, it's fair to blame the whole. 

> **talkingwires said:**
> I've been using Ubuntu since the very beginning. The boot experience is something they've been working on for a long time, but they've never done much to the actual bootloader. Every other distro I can think of as customized bootloader, but the Ubuntu developers have never bothered making their own. It's a little strange, considering how little work would be required to make a custom bootloader splashscreen, but then again, you only see it for a few seconds.

That's only correct if by "never bothered" you mean "[were aware of compatibility issues with graphical boot and didn't deem the risk worth the gain]("http://archives.free.net.ph/message/20050314.131030.33c9d4a6.en.html")".

> **talkingwires said:**
> I guess they're busy disabling touchpads

Disabling *tap-to-click*, on *touchpads that have buttons*, *in a development branch*, and stating that the change can be discussed further; and yet "the Ubuntu users&#8482;", who, being pre-release testers, are supposed to be early adopters, after a week of furious complaining in a user forum, haven't yet bothered to post to a mailing list to object to that change.

> **talkingwires said:**
> and shortcuts to restart the X server.

Shortcuts, as in Alt + SysReq + K?

---

### Post by col48 on 2009-09-22
Personally I'm grateful for all those folk who have contributed to the development of Ubuntu.  Yes, there are a few things I'd like done differently/as well but on the whole the problem is more likely choosing between the many options for doing X than frustration that X cant be done.

I think 23Meg's response is well put and very moderate.  Let's remember that Ubuntu Developers are not slave labourers or working unwillingly according to someone else's agenda or building developments in order to maximise the profits by inventing bells and whistles of minimal use.

I am not someone with the time, energy or interest to build an OS myself, so I'm grateful to those who have, who can, and who have made it freely available.

---

### Post by kansasnoob on 2009-09-22
Just to clarify: I'm **not** complaining.

I've just seen a trend lately where people "hate" feature x,y or z in Karmic, and I find that foolish.

Bootloaders, desktop environments, etc. are easily changed. It's **your** Ubuntu, customize to your hearts content!

---

### Post by bornagainpenguin on 2009-09-22
> **Funnnny said:**
> Oh yeah, no one force you to use Alpha, you choose to use it YOURSELF, so why do you complaining ?

Simple: So that the developers can find work-arounds or fixes for these issues in time for the Beta releases.  That's the whole point of having so many Alpha releases, isn't it?

Personally I don't mind the Ubuntu developers making the decision to update the boot-loader, as others have commented, Ubuntu is about the only one left now that hasn't made some form or another of boot-loader customization.  It's about time.  What I do have issues with is when the new version of something is deliberately difficult to edit with what you knew from the previous version.  This is because there are many HOWTOs that can take awhile to get updated for the newer version of something and making people get lost during or after a new install of Linux is never a good thing if it can be prevented.

For most people the new boot-loader might not be an issue, ut what about those like ourselves with a dual boot system set up?  The new grub didn't even add WinXP to the list, let alone my OSX86 install of Tiger, which I have always had to manually add to the menu.lst--now what do I do?  Since Karmic is in Alpha I'm reinstalling Jaunty, but how many people will simply give up on Ubuntu if this is still an issue on the final release?

This is why we have Alphas--so that people *can* complain and hopefully as many issues as possible can be ironed out before the final release!

--bornagainpenguin

---

