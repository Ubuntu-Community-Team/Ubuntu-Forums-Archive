---
title: "Removing &quot;quiet splash&quot; still leaves &quot;Cylon warrior&quot; before login"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-06
Deleting the words and just leaving the quotes, or #'ing out the entire line still leaves the (or is that the KITT Lamp?) moving indicator for a bit before going to the login screen - the pre "X" stuff is still obscured.

Is this the intended action and how to eliminate the Wagging Tail completely?

/etc/default/grub

---

### Post by Longinus00 on 2009-10-06
Removing splash would stop usplash from displaying, but usplash is already disabled on bootup. Removing xsplash is currently not supported but there is a wish list item on the xsplash bug list. Replacing the xsplash trobber/logo images with a transparent png will work as a stopgap measure if you really don't want to see it.

---

### Post by emarkay on 2009-10-07
Thanks - actually I (and others I am sure) want to see the boot process code as long as possible without having to look at logs and all that later.

IMHO this should be much more than a "wishlist" - I'd almost say it's a "bug", since the intended action is not as it was in Jaunty, nor what I consider the intent!.

---

### Post by jocko on 2009-10-07
> **emarkay said:**
> Thanks - actually I (and others I am sure) want to see the boot process code as long as possible without having to look at logs and all that later.

IMHO this should be much more than a "wishlist" - I'd almost say it's a "bug", since the intended action is not as it was in Jaunty, nor what I consider the intent!.

But xsplash starts with x, so even if you would remove xsplash you still don't get any more text mode output (I've tried. You'll just get a grey screen until gdm loads, then the same grey screen again until you see the desktop). The only thing you can do if you want to stay in text mode longer is to change the init/upstart scripts to start x later in the boot process.

---

### Post by emarkay on 2009-10-07
Was going to mark this "Solved" but then I figured I would ask, then why was Jaunty different - is this something that had to be done or is this a "feature" that someone decided we wanted?

It's just sort of lame to have the "Throbber" (I think that is the correct term) either show for a while, then the Login Screen appears, or  show boot text, THEN the throbber, than the Login Screen. :confused:

---

### Post by jocko on 2009-10-07
> **emarkay said:**
> Was going to mark this "Solved" but then I figured I would ask, then why was Jaunty different - is this something that had to be done or is this a "feature" that someone decided we wanted?

It's just sort of lame to have the "Throbber" (I think that is the correct term) either show for a while, then the Login Screen appears, or  show boot text, THEN the throbber, than the Login Screen. :confused:

So when they finally meet the goal of a ten second boot, do you still want to see the text flashing by too fast to read (THAT would be lame), or do you suggest that there should be an option to slow down boot because you want to be able to read the text that flashes by (that would be pretty lame too)?

---

### Post by Ichtyandr on 2009-10-07
Hello fellows,

What do you mean not supported? I removed xsplash (from synaptic) and get a normal text boot right till the gdm loads (to automatic login in my case). 
And using this guy's howto you can also change the background of your gdm easily (usually its my desktop background)

[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

otherwise there will be an orange intermezzo between your boot and your desktop wallpaper:

---

### Post by scaine on 2009-10-07
Not really sure if it's in the spirit of "testing" to be making all these changes during the alpha/beta process.  You'll be reporting bugs about a system you've deliberately hacked to be different from the one they're trying to roll out the door.

But fire on, I suppose.  Everyone has different tastes.

---

### Post by emarkay on 2009-10-08
Filed a Bug on this:

[https://bugs.launchpad.net/ubuntu/+bug/446483](https://bugs.launchpad.net/ubuntu/+bug/446483)

---

### Post by Longinus00 on 2009-10-08
> **emarkay said:**
> Filed a Bug on this:

[https://bugs.launchpad.net/ubuntu/+bug/446483](https://bugs.launchpad.net/ubuntu/+bug/446483)

I already told you in my reply that there is a wishlist item for this already.

[https://bugs.launchpad.net/xsplash/+bug/439284](https://bugs.launchpad.net/xsplash/+bug/439284)

---

### Post by emarkay on 2009-10-08
> **Longinus00 said:**
> I already told you in my reply that there is a wishlist item for this already.
[https://bugs.launchpad.net/xsplash/+bug/439284](https://bugs.launchpad.net/xsplash/+bug/439284)

D'oh!  Sorry, been busy today - marked mine as a dupe.  :)

---

### Post by mr_skater99 on 2009-10-28
I just wanted to add a plus 1 to a text boot.

The new graphics are quite slick - but i prefer a text boot for a bunch of reasons.

Be great to be able to text boot at the native full 1080p res on these screens.

---

