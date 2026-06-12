---
title: "The Me Menu"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kazade on 2010-03-04
So I've finally made the jump from Karmic to Lucid (I was trying to hold out this time, but the new branding changed my mind), anyway, I thought I'd try out the status updates via the Me Menu...

Firstly, is it just me that thinks it's totally non-obvious what that text field is supposed to do? It's just a text box dumped in the middle of the menu, there is no indication that it updates status. Is this something that is going to change? Worth filing a bug report over?

Secondly, it updated my status fine, but I had no notification that it did! I just sat there thinking, "did it work?" I had to open Gwibber to check... is this the intended behaviour?

I'm tempted to file bugs for both of these things, but I wanna make sure I'm not missing something obvious first (i.e. "it's on the to-do list", or "that's by design" :) )

---

### Post by FrancoNero on 2010-03-04
what bugs me is that it doesn't use my picture that i've set already.... where is it getting its picture from? where do i customize the me menu's behavior etc?

---

### Post by Kazade on 2010-03-04
Apparently that bug is already fixed ([https://bugs.launchpad.net/indicator-me/+bug/525951](https://bugs.launchpad.net/indicator-me/+bug/525951))

---

### Post by Mr. Picklesworth on 2010-03-04
> **Kazade said:**
> Firstly, is it just me that thinks it's totally non-obvious what that text field is supposed to do? It's just a text box dumped in the middle of the menu, there is no indication that it updates status. Is this something that is going to change? Worth filing a bug report over?

Secondly, it updated my status fine, but I had no notification that it did! I just sat there thinking, "did it work?" I had to open Gwibber to check... is this the intended behaviour?

I'm tempted to file bugs for both of these things, but I wanna make sure I'm not missing something obvious first (i.e. "it's on the to-do list", or "that's by design" :) )

You are not alone! That text box is not only unmarked, but illogical. It has no Post button yet doesn't apply unless you know to hit Enter. It doesn't show its current state. It is right above controls for instant messaging status. It is too small. It doesn't express the character limit. It encourages completely mundane and useless microblog messages like "having shower."

This thing, logically, should be setting your IM status message. I, for one, think it would be way more useful and fun that way, and to more people.

Now that I'm ranting about it, I'm tempted to make a branch that does it my way. Telepathy is easy to work with, so could be easy. Lots of other stuff for me to do, though, and I *am* already in my pajamas...

---

### Post by Keyper7 on 2010-03-04
> **Kazade said:**
> Firstly, is it just me that thinks it's totally non-obvious what that text field is supposed to do? It's just a text box dumped in the middle of the menu, there is no indication that it updates status. Is this something that is going to change? Worth filing a bug report over?

According to the [specification](https://wiki.edubuntu.org/MeMenu), the complete version is supposed to show microblogging icons, thus making the usage of the text field more clear.

> **Kazade said:**
> Secondly, it updated my status fine, but I had no notification that it did! I just sat there thinking, "did it work?" I had to open Gwibber to check... is this the intended behaviour?

The specification also says that notifications are only sent if something goes wrong.

> **FrancoNero said:**
> what bugs me is that it doesn't use my picture that i've set already.... where is it getting its picture from? where do i customize the me menu's behavior etc?

[Bug reported, fix commited.](https://bugs.launchpad.net/ubuntu/+source/indicator-me/+bug/525951)

---

### Post by Kazade on 2010-03-04
I've posted a bug report here: [https://bugs.launchpad.net/indicator-me/+bug/532230](https://bugs.launchpad.net/indicator-me/+bug/532230)

I also knocked up a mock up of how I think it could look to make it more obvious: 

[IMG]http://launchpadlibrarian.net/40201893/me_menu.png[/IMG]

---

### Post by VMC on 2010-03-04
At least this topic solved the mystery that I wondered about.
Since I don't have any social accounts outside of email & Skype, I just brushed it off as an oddity. 

I did type text in the box but they vanished into thin air somewhere.

I'm not sure what use this holds for me , but at least the mystery is solved.

---

### Post by Keyper7 on 2010-03-04
> **Mr. Picklesworth said:**
> This thing, logically, should be setting your IM status message. I, for one, think it would be way more useful and fun that way, and to more people.

The specification says the MeMenu will have this functionality in the future.

> **Kazade said:**
> I've posted a bug report here: [https://bugs.launchpad.net/indicator-me/+bug/532230](https://bugs.launchpad.net/indicator-me/+bug/532230)

I think your bug report is not very useful in its current state. First, your mockup is based on the current, incomplete version and thus does not truly show what your suggestion offers over the complete design. Second, your suggestion of the text field having the last update has been part of the specification for a long time now:

> The default contents of the field depends on what your last posting was to each of the set up broadcast accounts.

---

### Post by Kazade on 2010-03-05
> **Keyper7 said:**
> 
I think your bug report is not very useful in its current state. First, your mockup is based on the current, incomplete version and thus does not truly show what your suggestion offers over the complete design. 


Sure, I've stated that this was in Alpha 3, and I know it's incomplete...

> 
Second, your suggestion of the text field having the last update has been part of the specification for a long time now:

No, that's not quite the same as my suggestion. The mockup shows the greyed text in the box simply says "Update your social status..." regardless of what has been typed previously. When the status is changed the status appears *above* the text field - giving instant feedback that hitting enter actually did something.

---

### Post by Keyper7 on 2010-03-05
> **Kazade said:**
> Sure, I've stated that this was in Alpha 3, and I know it's incomplete...

Thus, your mockup should include the icons, because as it is know people cannot know if they supposed to go below your text or under it, for example, and, more importantly, how well they will complement the icons in terms of information.

Usability is a complex thing, and the line between "helpful" and "too helpful to the point of clutter" is blurry. Your mockups must be as precise as possible if you want to be heard.

> **Kazade said:**
> No, that's not quite the same as my suggestion. The mockup shows the greyed text in the box simply says "Update your social status..." regardless of what has been typed previously. When the status is changed the status appears *above* the text field - giving instant feedback that hitting enter actually did something.

That doesn't change the fact that the current specification *does* have success feedback. You need to update your bug report with more detailed info on why your proposal is better.

Frankly, in my opinion the whole thing is more suited to a mailing list than a bug report, as there's nothing obvious in the issue.

---

### Post by Kazade on 2010-03-05
> **Keyper7 said:**
> Thus, your mockup should include the icons, because as it is know people cannot know if they supposed to go below your text or under it, for example, and, more importantly, how well they will complement the icons in terms of information.

Usability is a complex thing, and the line between "helpful" and "too helpful to the point of clutter" is blurry. Your mockups must be as precise as possible if you want to be heard.


Good point.

> 
That doesn't change the fact that the current specification *does* have success feedback. You need to update your bug report with more detailed info on why your proposal is better.

Frankly, in my opinion the whole thing is more suited to a mailing list than a bug report, as there's nothing obvious in the issue.

Yeah, you're right, I didn't think about approaching a mailing list. :(

---

### Post by DeadSuperHero on 2010-03-05
I would really dig it if the MeMenu somehow would set your IM avatar on all of the IM networks you're using. (Within reason, I don't think it would be able to change Facebook IM)

---

