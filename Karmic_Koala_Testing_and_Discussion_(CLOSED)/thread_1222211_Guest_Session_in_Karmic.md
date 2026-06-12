---
title: "Guest Session in Karmic?"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marat89 on 2009-07-24
Hi,

In Jaunty there was an option in the Fast User Switch Applet to start a Guest Session.

Any info about this feature in Karmic? I cant find this Option.:(

---

### Post by BCurtisWX on 2009-07-24
> **Marat89 said:**
> Hi,

In Jaunty there was an option in the Fast User Switch Applet to start a Guest Session.

Any info about this feature in Karmic? I cant find this Option.:(

right now the FUSA applet isn't configured with the new Gnome, i believe it will be there before Karmic is released.

---

### Post by Marat89 on 2009-07-24
I hope so ;-)
And do you know about any plans to integrate the Guest Session option in the new GDM?

---

### Post by BCurtisWX on 2009-07-24
> **Marat89 said:**
> I hope so ;-)
And do you know about any plans to integrate the Guest Session option in the new GDM?

The option was there before, i don't see why it wouldn't

---

### Post by Marat89 on 2009-07-24
Are you sure?
In Jauntys GDM Facebrowser i had never a default option "Guest", which i could start.

You can do it manually I know, but thats not the issue.

---

### Post by Starks on 2009-07-24
gdm-guest-session does nothing for now...

---

### Post by wayne_cat on 2009-07-24
> **Starks said:**
> gdm-guest-session does nothing for now...

true :(


```
rschmitt@macbook:~$ /usr/share/gdm/guest-session/guest-session-launch

** (gdmflexiserver:4696): WARNING **: No longer supported
rschmitt@macbook:~$

```

---

### Post by Marat89 on 2009-07-24
hope for a fast integration
sadly there many parts now in Ubuntu Karmic with a step backwards like missing guest session or the "new" volume applet ...

---

### Post by | MM | on 2009-07-24
> **Marat89 said:**
> hope for a fast integration
sadly there many parts now in Ubuntu Karmic with a step backwards like missing guest session or the "new" volume applet ...

Do remember this is alpha software.

---

### Post by ranch hand on 2009-07-24
We are still in early days with this 9.10 release.

> 
August 2009
August 6th - Developer Sprint (tentative)
August 13th - Alpha 4 & Partner Upload Deadline
August 27th - Feature Freeze & Artwork First Drop

September 2009
September 3rd - Alpha 5
September 10th - User Interface Freeze & Artwork Second Drop
September 17th - Alpha 6
September 24th - Beta Freeze & Artwork Dead line

October 2009
October 1st - Ubuntu Karmic Beta & Documentation String Freeze
October 15th - Kernel Freeze & Final Freeze
October 22nd - Ubuntu Karmic Release Candidate
October 29th - Ubuntu 9.10 

Let's relax a bit and see what comes down the line when they start putting in the really new stuff that needs the completion of the new GDM and kernal.

---

### Post by wayne_cat on 2009-07-24
> **ranch hand said:**
> We are still in early days with this 9.10 release.


Let's relax a bit and see what comes down the line when they start putting in the really new stuff that needs the completion of the new GDM and kernal.

+1

the first new gdm version was a mess ... but it is getting getter every day.

---

### Post by Marat89 on 2009-07-25
No problem you are right. I was only saying that some parts due to the early stage are not feature complete and we all hope for a great Karmic release ;-)

---

### Post by n3had on 2009-09-26
any updates on guest sessions?

---

### Post by nanomad on 2009-09-26
I have it, see the attached screenshot.

---

### Post by taavikko on 2009-09-26
> **nanomad said:**
> I have it, see the attached screenshot.

Then click it and what happens...
Does it start the guest-session, or does it do nothing, or will it kill kittens...

---

### Post by nanomad on 2009-09-26
> **taavikko said:**
> Then click it and what happens...
Does it start the guest-session, or does it do nothing, or will it kill kittens...

I know I should have written it.

It works well.

---

### Post by n3had on 2009-09-26
> **nanomad said:**
> I know I should have written it.

It works well.

Do you know the command line mode to logon to guest session?

---

### Post by nanomad on 2009-09-27
Here you go:
```

sudo /usr/share/gdm/guest-session/guest-session-launch 

```

---

### Post by taavikko on 2009-09-27
The bugger won't play ball with me: [https://bugs.edge.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/437563](https://bugs.edge.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/437563)

Previously it ate my kittens (month ago) (hard locked the system)

---

### Post by philinux on 2009-09-27
I just tried the guest session and it worked flawlessly.

---

### Post by n3had on 2009-09-27
> **nanomad said:**
> Here you go:
```

sudo /usr/share/gdm/guest-session/guest-session-launch 

```

```
sudo: /usr/share/gdm/guest-session/guest-session-launch: command not found

``` this is what i got

EDIT: i don't have that package installed installing it right away

EDIT 2: Got it thanks

---

### Post by taavikko on 2009-09-27
> **n3had said:**
> ```
sudo: /usr/share/gdm/guest-session/guest-session-launch: command not found

``` this is what i got

Then reinstall "gdm-guest-session" package, or check the command.

---

