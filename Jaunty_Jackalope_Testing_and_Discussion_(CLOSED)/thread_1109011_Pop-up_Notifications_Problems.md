---
title: "Pop-up Notifications Problems"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Toadinator on 2009-03-28
As much as I like the new notifications, there's a few problems I've ran into and before I report them as bugs I'd like to see if others have these problems as well.

1) I had to edit my menus for the settings launcher to appear in Preferences... shouldn't it be there by default?

2) After I clicked it, I tried changing the theme and corner they appear in, but nothing changes. That, and the default location was the bottom-right corner, but they appeared in the top-right corner.

---

### Post by ktp on 2009-03-28
The new notification is not customizable.  There are no options to configure it and this is by design.  

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095)

---

### Post by Toadinator on 2009-03-28
> Included in Jaunty is a simple menu which can be used to set preferences for notification icons, such as where they pop up on the taskbar. Ubuntu 9.04 beta also includes a whole new notification system, as shown in the Flash movie here:

[http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf](http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf) 

Then whats this about?

---

### Post by ktp on 2009-03-28
That's what I thought until I read the bug:

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095/comments/3](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095/comments/3)

> We are sorry that Jaunty alpha 5 accidentally shipped with the "Notification Settings" utility that applied only to notification-daemon, when 9.04 is not going to ship with notification-daemon. But this mistake has been fixed since before alpha 6 (bug 332014).

---

### Post by Polygon on 2009-03-28
i agree with the argument there. why are forcing users to have the notify bubble in a certain spot with no ability to customize it? it seems stupid.

i mean, at least make it a gconf key or something, but i really hate the mentality that 'we know better then you therefore we shall make it impossible to change it"

---

### Post by phenest on 2009-03-28
> **Polygon said:**
> ... i really hate the mentality that 'we know better then you therefore we shall make it impossible to change it"

What makes you think that's what devs are like? Behave.

They are currently only interested in making it work, without making it customizable. I'm sure they'll add something eventually. One step at a time.

---

### Post by Polygon on 2009-03-28
> **phenest said:**
> What makes you think that's what devs are like? Behave.

They are currently only interested in making it work, without making it customizable. I'm sure they'll add something eventually. One step at a time.

you didn't fully read the bug report then.

> 
ktp420, you're quite correct to point out that the average user is not going to want to recompile software. **But that's fine, because they are not going to want to configure the bubble placement either.** We could be wrong about that; the beauty of Free Software is that if we are wrong, you can make your own variant and it will be wildly popular.

> 
So this is not a regression: **the bubble position wasn't graphically customizable in 8.10, and it won't be graphically customizable in 9.04 either. **It's not reasonable to say that Notify OSD doesn't "bother to see if I had settings from previously", where "previously" means "a bug in an alpha release".


they don't even give you a gconf key, its just 'its not customizable and you will NOT want to customize it anyway"

well what if i want to?

---

### Post by phenest on 2009-03-28
> **Polygon said:**
> they don't even give you a gconf key, its just 'its not customizable and you will NOT want to customize it anyway"
It does say "We could be wrong"
> **Polygon said:**
> well what if i want to?
You answered your own question (or they did for you). Write your own.

---

### Post by Polygon on 2009-03-28
and again, like in the argument, that is not an answer. Normal average joe users that ubuntu appeals to are not going to know how to do edit source code, or compile anything, or do any of that. 

saying 'this is the way its done or else you can rewrite it' is exactly the attitude i was talking about, 'we know better then you therefore we shall make it impossible to change it'. Try explaining to an average joe that he must write his own notification system if he wants to have the bubble moved, and see how fast he just gives up on ubuntu. This kind of attitude is not needed here =/

its not drastically changing anything about the notification system at all, its just changing the x,y coordinates of the bubble. I can't believe something as trivial as that is getting everyone worked up about usability.

---

### Post by phenest on 2009-03-28
> **Polygon said:**
> and again, like in the argument, that is not an answer. Normal average joe users that ubuntu appeals to are not going to know how to do edit source code, or compile anything, or do any of that. 
No noe expects you to.
> **Polygon said:**
> saying 'this is the way its done or else you can rewrite it' is exactly the attitude i was talking about, 'we know better then you therefore we shall make it impossible to change it'. Try explaining to an average joe that he must write his own notification system if he wants to have the bubble moved, and see how fast he just gives up on ubuntu. This kind of attitude is not needed here =/
This is the Linux way. No one is trying to make it impossible.
> **Polygon said:**
> its not drastically changing anything about the notification system at all, its just changing the x,y coordinates of the bubble. I can't believe something as trivial as that is getting everyone worked up about usability.
This is probably why you're not a programmer. It's not necessarily as trivial as you think.

---

### Post by ktp on 2009-03-28
> **phenest said:**
> This is the Linux way. No one is trying to make it impossible.

So lets close this bug:

[https://bugs.launchpad.net/bugs/1](https://bugs.launchpad.net/bugs/1)

---

### Post by TrueTom on 2009-03-28
> **Polygon said:**
> well what if i want to?

Fedora will release the beta version of their next release on Tuesday, including a sane notification system...

---

### Post by Polygon on 2009-03-29
> **phenest said:**
> 

This is probably why you're not a programmer. It's not necessarily as trivial as you think.

i meant functionality wise. I said nothing about how hard it would be to implement (as a pre-cs major, i would imagine that it is actually not that hard.) but rather how it does nothing to damage the functionality of the bubble if it just appears on...the top left or...the bottom right as opposed to the top right of the screen. 

and honestly, that is not the linux way. If it is, we might as well close bug #1 as invalid like the above poster said because we will never get anywhere with attitudes like these. Remember what they say about assuming things......

---

### Post by olskar on 2009-03-29
> **Toadinator said:**
> Then whats this about?

Yes that is kind of bad, seriosly there is very few things that changed from alpha 6 to Beta (mentioned in the releasenotes). It wouldn't be that hard to keep them updated?

---

### Post by ktp on 2009-03-29
> **olskar said:**
> Yes that is kind of bad, seriosly there is very few things that changed from alpha 6 to Beta (mentioned in the releasenotes). It wouldn't be that hard to keep them updated?

Maybe they are working on something...or didn't want to make more people mad.

---

