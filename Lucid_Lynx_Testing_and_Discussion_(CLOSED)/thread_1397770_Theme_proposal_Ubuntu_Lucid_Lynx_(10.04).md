---
title: "Theme proposal Ubuntu Lucid Lynx (10.04)"
date: 2010-02-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Reason NL on 2010-02-03
Hi all,

I've been a ubuntu user for quite some time now, but I think the looks of ubuntu are beginning to lag behind.
I'm not against the brown/orange theme, in fact I like it, but it just misses the final touches.
The login screen needs the be revamped and needs a complementary lock screen as well.
I took the liberty of redrawing the dusk theme, which I use daily, and was wondering if you guys could give me some directions and tell me if you like my approach!
Should I continue to put my effort into this?
I'm not even sure if my ideas are possible to achieve with the skinning possibilities of metacity.
So please enlighten me!

Thanks and I hope you'll enjoy my screens ;-)

[[IMG]http://img43.imageshack.us/img43/6659/humanmenuwindows.th.png[/IMG]]("http://img43.imageshack.us/i/humanmenuwindows.png/")

[[IMG]http://img641.imageshack.us/img641/7360/leavesmenuwindows.th.png[/IMG]]("http://img641.imageshack.us/i/leavesmenuwindows.png/")

[[IMG]http://img94.imageshack.us/img94/8886/sandmenuwindows.th.png[/IMG]]("http://img94.imageshack.us/i/sandmenuwindows.png/")

---

### Post by snkiz on 2010-02-03
Everybody says that every release. Check the wiki for artdrop, you'll see. besides you should really post this in the lucid testing forum.

---

### Post by Reason NL on 2010-02-07
Thanks for the reply. I've posted my ideas here because I was interested in what people think about the approach and I wasn't aware of any Lucid testing forum, so sorry about that.
I will search the wiki for more information in trying to get involved in making Ubuntu look better, but for now I'm still requesting all you Ubuntu users out there to check my screens and make suggestions on how Ubuntu should look like.

I will continue working on this concept on the Ubuntu wiki and named it the Unity theme:
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme)

---

### Post by Yezumg on 2010-02-25
I love your theme, you should continue with it. He looks a lot like Wasp. But I much prefer yours.

You could put some preliminary version to test?

Thanks and do not abandon the project.

---

### Post by Reason NL on 2010-03-22
New Update!
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme)

Made some preliminary versions of the login en lock screen.
Please comment!

@ Yezumg:
Thanks for your post! But I don't have any real skinning done yet.
Still just drawing pictures..

---

### Post by timosha on 2010-03-22
Excellent ! keep up the good work ;)

---

### Post by Reason NL on 2010-03-23
New Update!
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme)

Updated login and lock screens. Splash screen added.

---

### Post by solidsnakest on 2010-03-29
EXELENT!!!!!, that's the way it has to be, nice "loading bar" and windows. I hope something as cool as this is finally being used by canonical.

---

### Post by Jeremy23 on 2010-03-31
> **Reason NL said:**
> New Update!
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme)

Updated login and lock screens. Splash screen added.

The mockups showcase functionality that is quite clearly not available in GNOME, and won't be possible without a lot of work. For example, the "leave a message" buttons in GDM, and the blurred screensaver.

The blurred screensaver idea is just unreasonable — most computers have enough trouble running Compiz smoothly as it is without any blurring, not to mention a 3D screensaver running in the background.

If you want to propose ideas such as this, don't forget to put in hundreds of hours of C coding to actually patch the software to support the features too. Otherwise just re-style what's already there, and what's possible today. Pretty sure usplash or Plymouth won't support animated progress bars either (though I don't know them well enough to say definitively), but I agree that the animation in and of itself would be good.

The visuals need to be *way* more subtle. These mockups are just "in-your-face".

---

### Post by Reason NL on 2010-04-01
Thanks Jeremy for you're critic look at these mock-ups.
This is exactly what kind of reaction I was hoping to receive!

The blurred screen saver was just a test case and wake-up call for anyone willing to participate in making Ubuntu (gnome) look better and compete with / supersede what Apple and Microsoft are doing.
So yes my direction is to introduce things I haven't seen before, not bothered by the amount of work it will cost to realize.  It's to let people see the potential, rethink existing paradigms and show possible innovation in the product without completely revamp the complete desktop experience, like gnome 3 does for example (Evolution vs. revolution).

The leave message feature was deliberately put on both screens to make the login and lock screens more consistent. You should be able to use this feature for all logged-in users not just the one who locked the screen.
Both screens basically do the same thing, but are in all Ubuntu releases to date completely different, the lock screen is just completely out of sync with the rest of the look.

The progress bar should be able to be made with Plymouth, The default text base loading bar already show a progressive loading like I described. It may be even cool to have some more animations in the background to show off the possibilities from Plymouth.

And finally, can you elaborate a bit on what you mean with "in-your-face"?
What would you like to see changed?

Thanks again! I really appreciate your input..

---

### Post by KdotJ on 2010-04-01
Very nice theme indeed! Well done its a fantastic job

---

### Post by sandys1 on 2010-04-01
> **Jeremy23 said:**
> The mockups showcase functionality that is quite clearly not available in GNOME, and won't be possible without a lot of work. For example, the "leave a message" buttons in GDM, and the blurred screensaver.


Umm.. I have a "leave a message" button when my screen is locked. Are you talking specifically about the login screen ?

---

### Post by Jeremy23 on 2010-04-02
> **sandys1 said:**
> Umm.. I have a "leave a message" button when my screen is locked. Are you talking specifically about the login screen ?

I was referring to the login screen.

> **Reason NL said:**
> The leave message feature was deliberately put on both screens to make the login and lock screens more consistent. You should be able to use this feature for all logged-in users not just the one who locked the screen.
Both screens basically do the same thing, but are in all Ubuntu releases to date completely different, the lock screen is just completely out of sync with the rest of the look.

Agreed. This is the behaviour of Windows since Windows XP (the "lock" screen is the welcome screen &#8212; at least, when you're not on a domain), and would be better. However, I don't see that as being technically feasible within Linux, if only because switching X servers is slow, and on buggy video setups, even fatal. And because it's not supported in any code.

> **Reason NL said:**
> And finally, can you elaborate a bit on what you mean with "in-your-face"?

It's just too "apparent". It's too big. I like a little bit of subtlety. If I were to open my laptop on the train with one of those massive logos, a passenger sitting next to me would think I'm quite vain. ;)

---

### Post by blwegrzyn on 2010-04-06
nice , do u have tarbars to test?

---

### Post by snkiz on 2010-04-07
Its a little to glossy in some areas, but I like it. When you get to working on a gtk theme keep that in mind, because its what you see the most of. 
I think you could pull off a static blured image of the screensaver with existing code and a bit of scripting, but not animated... yet.
getting gdm and lock screen to play nice is an awesome idea. A unified solution in a noble goal but in the short term its probably simpler to just make the lock screen "look" like gdm, I could get you half way there with existing GTK.
And from what I've seen of Plymouth what you have pictured is doable.

---

### Post by Reason NL on 2010-04-22
Another Update!
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme]("https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme")

Made a new update to the existing screens and added controls to the panel. Notice I placed it on top of the screen instead of the default bottom location. This will also make it more consistent with the experience when you're logged in.


> **snkiz said:**
> Its a little to glossy in some areas, but I like  it....

I made the gloss a little less apparent, but added a button effect the images to incorporate it more in the rest of the design.

> **Jeremy23 said:**
> 
It's just too "apparent". It's too big. I like a little bit of subtlety. If I were to open my laptop on the train with one of those massive logos, a passenger sitting next to me would think I'm quite vain. ;)

I've scaled and toned down the logo's a bit, hope that suits you and your co-travelers better. ;)

To any one wanting to try this theme, you should be patience. My goal is to draw everything upfront and I'll guess I'll be asking all you guys to help me to realize the full blown experience when I'm done. ;-)

Thanks all, for the uplifting comments! Keeps me motivated..

I'll be throwing myself on the desktop from now on..


May 14, Yet another update:
[https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme](https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Unity%20Theme)

---

