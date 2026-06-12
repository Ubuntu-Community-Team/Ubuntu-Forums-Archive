---
title: "2 boot splashes?"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by magneze on 2009-10-18
I've just upgraded to the 9.10 Beta. All seems fine apart from a few missing icons in Places and System. Also it generally seems a bit snappier than 9.04.

However, the boot sequence seems kinda worse. Do we really need 2 splashes? 1 with the ubuntu logo alone and then one with the logo, the text "ubuntu" and a status bar that doesn't quite update smoothly.

Can we just have one splash? Two looks really weird, especially after being used to 9.04's single boot splash screen.

Good work otherwise. :)

---

### Post by QwUo173Hy on 2009-10-18
The boot experience will change further between now and 10.04. This is just the first phase. When the boot reaches the 10 second goal, I imagine it will look a lot better, regardless of whether or not they drop one of the boot splashes.

It's good to see this progress so far though. As the Beatles once said (sang acutally) 'it's getting better all the time'.

---

### Post by joey-elijah on 2009-10-18
> **magneze said:**
> I've just upgraded to the 9.10 Beta.** All seems fine apart from a few missing icons in Places and System.** Also it generally seems a bit snappier than 9.04.

Good work otherwise. :)

They're supposed to be missing :p

---

### Post by magneze on 2009-10-18
> **joey-elijah said:**
> They're supposed to be missing :pI found the "show icons in menus setting and they're back. Odd that this didn't seem to affect all the menus tho.

---

### Post by magneze on 2009-10-18
> **jarlath said:**
> The boot experience will change further between now and 10.04. This is just the first phase. When the boot reaches the 10 second goal, I imagine it will look a lot better, regardless of whether or not they drop one of the boot splashes.

It's good to see this progress so far though. As the Beatles once said (sang acutally) 'it's getting better all the time'.Yes, Karmic is definitely better generally. IMO, the boot sequence at the moment appears worse, which is a bit of a shame. Hope it gets cleaned up for release at the end of the month. [-o<

I think just having one splash would improve it. What was the logic behind two?

---

### Post by qamelian on 2009-10-18
> **magneze said:**
> Yes, Karmic is definitely better generally. IMO, the boot sequence at the moment appears worse, which is a bit of a shame. Hope it gets cleaned up for release at the end of the month. [-o<

I think just having one splash would improve it. What was the logic behind two?

The first is usplash which is needed until X gets loaded. Once X is running, xsplash kicks in.

---

### Post by magneze on 2009-10-18
> **qamelian said:**
> The first is usplash which is needed until X gets loaded. Once X is running, xsplash kicks in.Jaunty only needed one splash and as a result looked much smoother IMO.

---

### Post by Starks on 2009-10-18
Why is the new usplash a static image? Shouldn't it show progress or reassure the user that the system hasn't locked up?

---

### Post by Guruji on 2009-10-18
it's static on the installed system, if you look on the livecd you'll see it's glowing in&out. Maybe they'll change this for final release.

---

### Post by FuturePilot on 2009-10-18
> **magneze said:**
> Jaunty only needed one splash and as a result looked much smoother IMO.

That's because in Jaunty and previous releases, X was one of the last things to start on bootup. Now X is starting much earlier as part of the 10 second boot time goal for 10.04

---

### Post by magneze on 2009-10-18
> **FuturePilot said:**
> That's because in Jaunty and previous releases, X was one of the last things to start on bootup. Now X is starting much earlier as part of the 10 second boot time goal for 10.04That doesn't quite explain why Jaunty has one and Karmic has two. If Karmic is starting X earlier then isn't xsplash enough?

---

### Post by NCLI on 2009-10-18
Because X doesn't start early enough(yet). For X to start, it needs a mounted disk, and mounting a disk requires other things to be done first, etc. 

So, for now, Usplash is still neccesary.

---

### Post by rockin_goliath on 2009-10-18
I understand why Usplash might still be necessary, but the display of two logos (splashes) is rather strange. In my opinion, the Usplash image should just be replaced with a black image. That way we can maintain the boot process that we have now while maintaining a consistent look throughout the boot process.

---

### Post by NCLI on 2009-10-18
> **rockin_goliath said:**
> I understand why Usplash might still be necessary, but the display of two logos (splashes) is rather strange. In my opinion, the Usplash image should just be replaced with a black image. That way we can maintain the boot process that we have now while maintaining a consistent look throughout the boot process.
Agreed, but that's not up to us :(

If possible, I'd like it to simply be the image already used for xsplash, with the Ubuntu logo + throbber fading in smoothly as soon as the transition the Xsplash takes place.

---

### Post by magneze on 2009-10-18
> **rockin_goliath said:**
> I understand why Usplash might still be necessary, but the display of two logos (splashes) is rather strange. In my opinion, the Usplash image should just be replaced with a black image. That way we can maintain the boot process that we have now while maintaining a consistent look throughout the boot process.=D> Amen to that.

---

### Post by aamukahvi on 2009-10-18
And now the real question... Could this be achieved with Plymouth?

---

### Post by Starks on 2009-10-18
> **Guruji said:**
> it's static on the installed system, if you look on the livecd you'll see it's glowing in&out. Maybe they'll change this for final release.
Keybuk, the boot dev, says he isn't going to change it.

---

### Post by FrancoNero on 2009-10-18
I hope I live long enough to exprience this: I power on the computer, and I start working. no booting, nothing

---

### Post by lswb on 2009-10-18
If and when boot time goes below 10 seconds, why do we need any aplash screen at all?

---

### Post by qamelian on 2009-10-18
> **FrancoNero said:**
> I hope I live long enough to exprience this: I power on the computer, and I start working. no booting, nothing

You mean like we did in the old days of the Commodore Vic 20 & the C64? :)

---

### Post by kklimonda on 2009-10-18
> **aamukahvi said:**
> And now the real question... Could this be achieved with Plymouth?

In short: no
For the longer answer check this post about xsplash: [http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

---

### Post by Ric_NYC on 2009-10-18
> **magneze said:**
> Jaunty only needed one splash and as a result looked much smoother IMO.

I agree completely.

---

### Post by VMC on 2009-10-18
> **FrancoNero said:**
> I hope I live long enough to exprience this: I power on the computer, and I start working. no booting, nothing

[Welcome to coreboot]("http://www.coreboot.org/Welcome_to_coreboot")

---

### Post by hanzomon4 on 2009-10-18
What we have now is basically what winxp has... and OS X has the same thing come to think of it...

---

### Post by rajeev1204 on 2009-10-19
> **hanzomon4 said:**
> What we have now is basically what winxp has... and OS X has the same thing come to think of it...


The keyword here is 'uniform boot splash' , and this definitely aint it.And maybe technically xp has the same boot concept but it definitely is much nicer.And in no way does it look like the current ubuntu boot.In fact i just reinstalled xp first time in 3 years and couldnt help smiling.Its a pretty neat installation and boot progress also.

Windows xp figured it out 8 years ago and we still cant? No point in explaining the technical details of a or b or u or x splash when people prefer a uniform splash .

I hate it. No offence.

Ill wait for the day coreboot arrives and we just switch on the PC and get to work :)

---

### Post by NCLI on 2009-10-19
> **lswb said:**
> If and when boot time goes below 10 seconds, why do we need any aplash screen at all?
Even 5 seconds is still a long time to be staring at a black, unresponsive screen.

---

### Post by Borjs85 on 2009-10-19
If usplash and xsplash had a coherent design I think there will be no complaints. Why one of them is black and the other is brown? 

Boot experience in Mandriva is beautiful: grub, usplash, xplash and default wallpaper, all whith the same image.

---

### Post by inportb on 2009-10-19
Well then, make it 5 seconds of black screen with round throbber in the center?

---

### Post by edujose on 2009-10-19
> **Borjs85 said:**
> If usplash and xsplash had a coherent design I think there will be no complaints. Why one of them is black and the other is brown? 

Boot experience in Mandriva is beautiful: grub, usplash, xplash and default wallpaper, all whith the same image.

I think the art team thought the same. But the current sequence is quite ugly: from a mostly black usplash (though a bit elegant) to a scene suggesting some dungeons-at-Frankenstein-castle (or something) :-)

They could have chosen one of [Mr doob's colorful variations]("https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot#Mr.doob%20boot"), it would have made the second splash a happier one.

---

### Post by Starks on 2009-10-19
Canonical is always quick to say "if it wasn't developed here, we don't like it", but we really do need to take a hard look at how suse and mandriver handle bootup from GRUB to desktop. It's really beautiful and efficient.

---

### Post by mrboojive on 2009-10-19
> **Borjs85 said:**
> If usplash and xsplash had a coherent design I think there will be no complaints. Why one of them is black and the other is brown? 

Boot experience in Mandriva is beautiful: grub, usplash, xplash and default wallpaper, all whith the same image.

+1. If there have to be two boot splashes, they should at least have the same image.

---

### Post by froggyswamp on 2009-10-19
Jaunty source:
```

..boot start
usplash start
..login

```Karmic source: new stuff!!
```

..boot start
usplash start
xsplash start
..login

```Lucid Lynx source: even more new stuff!!
```

..boot start
usplash start
xsplash start
plymouth start
..login

```

---

### Post by inportb on 2009-10-20
If anything, the next version of Ubuntu would drop usplash from the default boot process. Plymouth is just a polished usplash, anyway.

---

### Post by MadsRH on 2009-10-20
> **aamukahvi said:**
> And now the real question... Could this be achieved with Plymouth?

Yes, but remember this is still work in progress and the smooth experience (without U-splash) will not land until 10.04. Althougt U-splash will still show up on slower systems that cannot start X as fast as we want.

Anyway, I agree; it's pretty, but looks strange.

---

### Post by magneze on 2009-10-22
So, 7 days to go, wonder if we'll get 1 boot splash or 2 consistent ones. \\:D/

---

### Post by kkkkdddd on 2009-10-22
I have upgraded (downgraded?) from Jaunty to Karmic.
Can I somehow revert the boot procedure to the previous behaviour?

There are two reasons for which I want to do that:
-now boot sequence looks ugly
-it takes 90 seconds to boot, Jaunty needed only 60

Btw. is this "10 seconds boot" a joke?
Now Ubuntu boots almost as slow as Vista.

---

### Post by Ric_NYC on 2009-10-22
> **kkkkdddd said:**
> I have upgraded (downgraded?) from Jaunty to Karmic.
Can I somehow revert the boot procedure to the previous behaviour?

There are two reasons I want to do that:
-now boot sequence looks ugly
-it takes 90 seconds to boot, Jaunty needed only 60

Btw. is this "10 seconds boot" a joke?
Now Ubuntu boots almost as slow as Vista.

That's right.
Now we have 2 boot splashes... slowing the boot.

What's the point?
I don't get it.

---

### Post by PatrickVogeli on 2009-10-22
I've installed Karmic today and I find the new booting looks horrible. Really disapointing. Not that it's a critical component of the OS but the fact is that, the first impression, is really bad.

Hope it improves, but I don't count too much on it. It's sad since the rest seems to be awesome.

---

### Post by Ric_NYC on 2009-10-22
> **PatrickVogeli said:**
> I've installed Karmic today and I find the new booting looks horrible. **Really disapointing**. Not that it's a critical component of the OS but the fact is that, the first impression, is really bad.

Hope it improves, but I don't count too much on it. It's sad since the rest seems to be awesome.


It is disappointing. 
Where's the common sense?

---

### Post by cyberkilla on 2009-10-22
It is a bit choppy, I agree.

At the moment, there is no improvement for me at all; Booting takes over a minute and once I get to my desktop in Karmic, it isn't even ready for me! The panel isn't loaded, my icons are yet to appear and the wallpaper hasn't changed to my own yet.

---

