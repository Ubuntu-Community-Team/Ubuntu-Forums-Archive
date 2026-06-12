---
title: "Desktop icon placement"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-08-29
Does anybody know when the Karmic desktop will regain the ability to place icons consistently and reliably as I want them? At the moment mounted drives go in one arrangement, odd links to data folders go somewhere else, and actual files are scattered haphazardly. I would like them all to re-appear at each start, where I left them.

Works perfectly in jaunty, intrepid,....,XP, ME, W98,...W3.1.....

Is it coming soon? Please tell me yes!

---

### Post by hugmenot on 2009-08-30
I think icon position of symlinks isn&#8217;t stored in new nautilus file metadata system. Which sounds like a bug. I have no problems besides that one.

---

### Post by scradock on 2009-08-30
> **hugmenot said:**
> I think icon position of symlinks isn&#8217;t stored in new nautilus file metadata system. Which sounds like a bug. I have no problems besides that one.
That sounds plausible - I couldn't figure out what was supposed to be in charge of the placement, and hoped someone would have a clue. I'll try a bug against nautilus, unless the new version solves the problem when it arrives.

Thanks

---

### Post by scradock on 2009-08-30
> **hugmenot said:**
> I think icon position of symlinks isn&#8217;t stored in new nautilus file metadata system. Which sounds like a bug. I have no problems besides that one.
That sounds plausible - I couldn't figure out what was supposed to be in charge of the placement, and hoped someone would have a clue. I'll try a bug against nautilus, unless the new version solves the problem when it arrives.

Thanks

---

### Post by scradock on 2009-08-30
> **hugmenot said:**
> I think icon position of symlinks isn&#8217;t stored in new nautilus file metadata system. Which sounds like a bug. I have no problems besides that one.
OK, you're right, it's just the symlinks that have abberant behavior, which can push other icons around or even overlay them. A major problem for me is that the symlinks are laid out according to some default that sets them vertically down from a start point, whereas I like to read from left to right in a "category".

There are already several launchpad bugs on this topic; two got confused and written off as incomplete a month ago, and the latest one was stomped on as (Oh, someone who has this send it to GNOME bugzilla).

Searching bugzilla shows nothing that looks like this one, with hundreds of other bugs that seem unrelated.

This leaves two major possibilities: 

1) This is indeed a major regression in Nautilus that no-one else has noticed, and we can't do anything about it because that's GNOME; or

2) Something in the Ubuntu package isn't handing symlink positions correctly, so only Ubuntu users are affected anyway, and we're all too busy dealing with the awesome innovations in KK to worry about how our desktops look.

Does anyone except hugmenot and me have the same problem?

---

### Post by psyke83 on 2009-08-30
Just to let you know, Firefox's default download location will be changing to ~/Downloads as a result of the 100papercuts effort.

Although this isn't the fix you're asking for (and I also wish Nautilus had more sane icon placement), it'll reduce the problem.

[https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs/+bug/204567](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs/+bug/204567)

---

### Post by scradock on 2009-08-30
> **psyke83 said:**
> Just to let you know, Firefox's default download location will be changing to ~/Downloads as a result of the 100papercuts effort.

Although this isn't the fix you're asking for (and I also wish Nautilus had more sane icon placement), it'll reduce the problem.

[https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs/+bug/204567](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs/+bug/204567)
Great! Now I'll need to put a symlink to ~/Downloads on my Desktop......

Seriously, the point of a Desktop is to be a central "hub" for everything you want to access, at least for me. A sane Desktop would have links to Downloads, Documents, Pictures, Music..... - even better, these would BE folders within the folder that is portrayed as the Desktop. Why would I even want to go up one step to $HOME and then back down to Documents to get to my documents? It's crazy!

---

### Post by steeleyuk on 2009-08-30
> **scradock said:**
> Great! Now I'll need to put a symlink to ~/Downloads on my Desktop......

Seriously, the point of a Desktop is to be a central "hub" for everything you want to access, at least for me. A sane Desktop would have links to Downloads, Documents, Pictures, Music..... - even better, these would BE folders within the folder that is portrayed as the Desktop. Why would I even want to go up one step to $HOME and then back down to Documents to get to my documents? It's crazy!

Surely it would be easier for you just to get rid of the Desktop folder and have GNOME mark the Home folder as the desktop, using gconf.

A sane desktop in my eyes is to have nothing on it at all... :)

---

### Post by psyke83 on 2009-08-30
> **scradock said:**
> Great! Now I'll need to put a symlink to ~/Downloads on my Desktop......

Seriously, the point of a Desktop is to be a central "hub" for everything you want to access, at least for me. A sane Desktop would have links to Downloads, Documents, Pictures, Music..... - even better, these would BE folders within the folder that is portrayed as the Desktop. Why would I even want to go up one step to $HOME and then back down to Documents to get to my documents? It's crazy!

No operating system that I've ever seen uses the Desktop in the way you describe it should. Windows uses the Desktop to store shortcuts and the Recycle Bin (My Documents and My Computer have been removed since Vista), and Mac OS X seems only to display drives (not counting the dashboard or whatever it's called).

In addition, Firefox 3.5 on Windows platform now defaults to saving in the operating system's Downloads folder (it even creates this folder in XP, since it doesn't exist by default). 

Windows Explorer uses a "Favourites" system embedded into the sidebar of Explorer, and has quick-access links on the Start menu. Ubuntu (and presumably other GNOME based distributions) achieve the same effect with the Places menu.

---

### Post by scradock on 2009-08-30
> **steeleyuk said:**
> Surely it would be easier for you just to get rid of the Desktop folder and have GNOME mark the Home folder as the desktop, using gconf.

A sane desktop in my eyes is to have nothing on it at all... :)
That's a serious possibility; does anyone have any experience of disadvantages? For instance, are there apps that don't respect the gconf setting and insist that there HAS to be a Desktop folder? Does the Desktop folder have special attributes/paradigms that would not be available if I used $HOME?

Anyway, thanks for the suggestion...

---

### Post by scradock on 2009-08-30
> **psyke83 said:**
> No operating system that I've ever seen uses the Desktop in the way you describe it should. Windows uses the Desktop to store shortcuts and the Recycle Bin (My Documents and My Computer have been removed since Vista), and Mac OS X seems only to display drives (not counting the dashboard or whatever it's called).

In addition, Firefox 3.5 on Windows platform now defaults to saving in the operating system's Downloads folder (it even creates this folder in XP, since it doesn't exist by default). 

Windows Explorer uses a "Favourites" system embedded into the sidebar of Explorer, and has quick-access links on the Start menu. Ubuntu (and presumably other GNOME based distributions) achieve the same effect with the Places menu.
Yes, we all use Desktops differently - my wife stores all her working files on hers, for instance. 

I find the Ubuntu Desktop workable, because we can use symlinks to give immediate access to important destinations, even if I disagree with the default choices. The same is true for Vista, of course.

BUT when Nautilus doesn't handle symlinks properly I find that my carefully laid-out Desktop gets mangled at every restart. And I don't like it! Has anyone actually drawn the attention of the GNOME developers to this regression? I have zero confidence that a bugzilla filing from me would have any effect......

---

### Post by psyke83 on 2009-08-30
> **scradock said:**
> Yes, we all use Desktops differently - my wife stores all her working files on hers, for instance. 

I find the Ubuntu Desktop workable, because we can use symlinks to give immediate access to important destinations, even if I disagree with the default choices. The same is true for Vista, of course.

BUT when Nautilus doesn't handle symlinks properly I find that my carefully laid-out Desktop gets mangled at every restart. And I don't like it! Has anyone actually drawn the attention of the GNOME developers to this regression? I have zero confidence that a bugzilla filing from me would have any effect......

Ok. My point was that your files, drives and symlinks already present on the Desktop (i.e. in the Desktop folder) won't find themselves constantly re-arranged due to downloads from Firefox.

---

### Post by VMC on 2009-08-30
> **scradock said:**
> ...I have zero confidence that a bugzilla filing from me would have any effect......

Why so? Have you had bad experiences in the past. I find this is the reason we even have alpha and betas. So we can file bug reports to let developers know what system or app is failing among other things.

---

### Post by scradock on 2009-08-31
> **VMC said:**
> Why so? Have you had bad experiences in the past. I find this is the reason we even have alpha and betas. So we can file bug reports to let developers know what system or app is failing among other things.
Well, having tried to be a helpful "ubuntu testing team" member since, oh, maybe Hardy, I have had some brush-offs from Ubuntu devs over launchpad bug reports - but who hasn't. When said Ubuntu devs simply tell a reporting tester (not me) "Send it to GNOME" rather than taking this on themselves it makes me feel that they don't expect to be given any more respect than any other user. Makes me feel that I don't want to report anything if it's so scary that Ubuntu devs would rather not do it....

THIS IS A MAJOR REGRESSION!!!! The entire Ubuntu Desktop team should be crashing down on the Nautilus developers like a ton of hot bricks telling them it has to be fixed yesterday! Nautilus is NOT some minor app that we can live with misbehaving - it has core functions in any GNOME-based distro. If it doesn't do what it has always done, it should be fixed!!!

I don't know why I'm shouting - maybe this seems to me to be too important to be left to me to report to GNOME bugzilla on the off-chance that someone there may notice and think about looking at it when they have a moment.

---

### Post by psyke83 on 2009-08-31
> **scradock said:**
> Well, having tried to be a helpful "ubuntu testing team" member since, oh, maybe Hardy, I have had some brush-offs from Ubuntu devs over launchpad bug reports - but who hasn't. When said Ubuntu devs simply tell a reporting tester (not me) "Send it to GNOME" rather than taking this on themselves it makes me feel that they don't expect to be given any more respect than any other user. Makes me feel that I don't want to report anything if it's so scary that Ubuntu devs would rather not do it....

THIS IS A MAJOR REGRESSION!!!! The entire Ubuntu Desktop team should be crashing down on the Nautilus developers like a ton of hot bricks telling them it has to be fixed yesterday! Nautilus is NOT some minor app that we can live with misbehaving - it has core functions in any GNOME-based distro. If it doesn't do what it has always done, it should be fixed!!!

I don't know why I'm shouting - maybe this seems to me to be too important to be left to me to report to GNOME bugzilla on the off-chance that someone there may notice and think about looking at it when they have a moment.

I think you've been around long enough to understand Ubuntu's place in the food chain. We take upstream's code, tweak it slightly and build (you can even consider Debian as an intermediary upstream source in some cases).

Making significant code changes in Ubuntu's version of GNOME applications will cause duplication of effort. Additionally, if the resulting patches are submitted upstream and rejected for whatever reason (such as not building against the latest GNOME SVN code), the Ubuntu developers will be forced to perpetually maintain the patches against the latest GNOME SVN, maintain a seperate codebase, or drop the modifications entirely. None of these options seem favourable.

Can't you see that it's better to interact directly with upstream on some issues?

---

### Post by hugmenot on 2009-08-31
A couple points:

[LIST=1][*][This is the blog post]("http://blogs.gnome.org/alexl/2009/06/24/data-about-data/") that explains the new approach of icon meta-data, which, I think, led to the regression.[*]Myself I use the desktop a a transient storage place for things I&#8217;m working on. Things will get filed away when they aren&#8217;t of interest anymore. It&#8217;s a desk&#8217;s top, right? It&#8217;s meant as a surface for things you work with, right?[*]Try this: [FONT="Monospace"]gconftool --toggle /apps/nautilus/preferences/desktop_is_home_dir[/FONT]. It will just display your $HOME as the desktop. Nothing else will change. You can keep the "Desktop" folder.
[/LIST]

---

### Post by hugmenot on 2009-08-31
Re 1.: It might be a gvfs bug, not nautilus, then.

---

### Post by aamukahvi on 2009-08-31
> **scradock said:**
> That's a serious possibility; does anyone have any experience of disadvantages? For instance, are there apps that don't respect the gconf setting and insist that there HAS to be a Desktop folder? Does the Desktop folder have special attributes/paradigms that would not be available if I used $HOME?
The gconf setting only changes the folder that is shown on the Desktop. Normally this is ~/Desktop, but the gconf setting in question changes this so your ~/ is shown on the desktop. Presumably at least every application that uses the gnome file picker dialog should work nicely. Maybe you could also symlink ~/Desktop to ~/ ?

---

### Post by scradock on 2009-08-31
> **psyke83 said:**
> I think you've been around long enough to understand Ubuntu's place in the food chain. We take upstream's code, tweak it slightly and build (you can even consider Debian as an intermediary upstream source in some cases).

Making significant code changes in Ubuntu's version of GNOME applications will cause duplication of effort. Additionally, if the resulting patches are submitted upstream and rejected for whatever reason (such as not building against the latest GNOME SVN code), the Ubuntu developers will be forced to perpetually maintain the patches against the latest GNOME SVN, maintain a seperate codebase, or drop the modifications entirely. None of these options seem favourable.

Can't you see that it's better to interact directly with upstream on some issues?
Yes, I agree - I certainly wasn't suggesting the Ubuntu team take on fixing the issue.

But reporting it? Isn't a report from knowledgable, respected devs more likely to be taken seriously than one from an unknown user?

---

### Post by scradock on 2009-08-31
> **hugmenot said:**
> A couple points:

[LIST=1][*][This is the blog post]("http://blogs.gnome.org/alexl/2009/06/24/data-about-data/") that explains the new approach of icon meta-data, which, I think, led to the regression.[*]Myself I use the desktop a a transient storage place for things I&#8217;m working on. Things will get filed away when they aren&#8217;t of interest anymore. It&#8217;s a desk&#8217;s top, right? It&#8217;s meant as a surface for things you work with, right?[*]Try this: [FONT="Monospace"]gconftool --toggle /apps/nautilus/preferences/desktop_is_home_dir[/FONT]. It will just display your $HOME as the desktop. Nothing else will change. You can keep the "Desktop" folder.
[/LIST]
Thanks for the link - I womdered why you knew what was going on! Myself, I have no basis for assuming that this is even a Nautilus fault, which is one reason I'm reluctant to file e GNOME bug. As you say, it could also be a gvfs problem. My initial post was simply asking if anyone knew anything - and you did.

Having read the blog, and the learned comments that followed, I didn't see anywhere a mention of not storing icon-placement metadata for symlinks. I could see that being forgotten initially, but surely it should have been obvious that it needed to be included?

---

### Post by scradock on 2009-08-31
> **aamukahvi said:**
> The gconf setting only changes the folder that is shown on the Desktop. Normally this is ~/Desktop, but the gconf setting in question changes this so your ~/ is shown on the desktop. Presumably at least every application that uses the gnome file picker dialog should work nicely. Maybe you could also symlink ~/Desktop to ~/ ?
Thanks - that makes it clear. I might try that, but it seems to me I would still need at least some symlinks, and while Nautilus isn't re-positioning them as I want it would still annoy me.

---

### Post by 23meg on 2009-08-31
> **scradock said:**
> 
But reporting it? Isn't a report from knowledgable, respected devs more likely to be taken seriously than one from an unknown user?

No. Most bugs are reported by "unknown users".

---

### Post by scradock on 2009-08-31
> **23meg said:**
> No. Most bugs are reported by "unknown users".
That's true. Doesn't mean that my feeling is wrong!

I have tried submitting a follow-up question about this to the blog article by the developer who introduced the new metadata-storage paradigm at the end of June. Let's see if that has the desired effect.

---

### Post by 23meg on 2009-08-31
[QUOTE=scradock]That's true. Doesn't mean that my feeling is wrong![/QUOTE]

Doesn't mean it's true either.

[QUOTE=scradock]I have tried submitting a follow-up question about this to the blog article by the developer who introduced the new metadata-storage paradigm at the end of June. Let's see if that has the desired effect.[/QUOTE]

It's much less likely to produce an effect than filing a good bug report or adding information to an existing one, and if it does produce an effect, and a bug hasn't already been filed, it will be "Yes, that's an issue, please file a bug report so that we can track it".

---

### Post by hugmenot on 2009-08-31
> **scradock said:**
> Thanks for the link - I womdered why you knew what was going on! Myself, I have no basis for assuming that this is even a Nautilus fault, which is one reason I'm reluctant to file e GNOME bug.

The same for me. I wondered about this, and when I saw your thread I clicked it and chipped in with the little morsel of info I had up to that point.

Now, experiment:

[LIST=1]
[*]create a folder on the Desktop, e.g., «Test».
[*]```
$ gvfs-info -a "metadata::nautilus-icon-position" Test
  metadata::nautilus-icon-position: 64,42
```
[*] create a symlink to this folder «Link to Test»
[*] ```
gvfs-info -a "metadata::nautilus-icon-position" Link\ to\ Test
attributes:
  metadata::nautilus-icon-position: 64,42
```
[/LIST]

When you move the original icon, the icon position attribute is changed for both. When you move the link, nothing changes. This means, the symlink just inherits the attributes of the original.

Sounds like a bug, or a feature request. Depends on the mood of the developer, I guess.

---

### Post by scradock on 2009-08-31
> **hugmenot said:**
> The same for me. I wondered about this, and when I saw your thread I clicked it and chipped in with the little morsel of info I had up to that point.

Now, experiment:

[LIST=1]
[*]create a folder on the Desktop, e.g., «Test».
[*]```
$ gvfs-info -a "metadata::nautilus-icon-position" Test
  metadata::nautilus-icon-position: 64,42
```
[*] create a symlink to this folder «Link to Test»
[*] ```
gvfs-info -a "metadata::nautilus-icon-position" Link\ to\ Test
attributes:
  metadata::nautilus-icon-position: 64,42
```
[/LIST]

When you move the original icon, the icon position attribute is changed for both. When you move the link, nothing changes. This means, the symlink just inherits the attributes of the original.

Sounds like a bug, or a feature request. Depends on the mood of the developer, I guess.
Well, that's clear enough! Will you file a bugzilla bug? I know so little about these deep matters that I'm reluctant. You at least have extracted the details of what is missing in action.t I do agree with others that a bug needs to be filed.....by someone who knows a little bit about what's happening and what isn't.

---

### Post by scradock on 2009-09-01
> **hugmenot said:**
> The same for me. I wondered about this, and when I saw your thread I clicked it and chipped in with the little morsel of info I had up to that point.

Now, experiment:

[LIST=1]
[*]create a folder on the Desktop, e.g., «Test».
[*]```
$ gvfs-info -a "metadata::nautilus-icon-position" Test
  metadata::nautilus-icon-position: 64,42
```
[*] create a symlink to this folder «Link to Test»
[*] ```
gvfs-info -a "metadata::nautilus-icon-position" Link\ to\ Test
attributes:
  metadata::nautilus-icon-position: 64,42
```
[/LIST]

When you move the original icon, the icon position attribute is changed for both. When you move the link, nothing changes. This means, the symlink just inherits the attributes of the original.

Sounds like a bug, or a feature request. Depends on the mood of the developer, I guess.
Some more experiments: files and folders actually on the Desktop (i.e. listed by "ls -la" in the Deskto directory, have values for "metadata::nautilus-icon-position".

As you showed, symlinks TO items in the Desktop directory have the attribute of the original.

Symlinks to items that are actually in another folder have no value for the nautilus-icon-position metadata attribute.

Logically, I would expect the nautilus-icon-position to refer to the symlink itself, not whatever it is linked to.

---

### Post by hugmenot on 2009-09-01
No, go ahead and file a bug against gvfs in Launchpad and include the info we gathered.
You have more impetus to follow through, I think.

---

### Post by scradock on 2009-09-01
> **hugmenot said:**
> No, go ahead and file a bug against gvfs in Launchpad and include the info we gathered.
You have more impetus to follow through, I think.
As it happens, someone has done the deed- the Launchpad bug #411322 has been re-activated, and the same report has been made in GNOME bugzilla. Both against Nautilus.

Any reason you suspect gvfs might be responsible? Even if it's involved,  the fact that the nautilus-icon-position metadata is not assigned in some cases would make it impossible for gvfs or anything else to re-position icons, wouldn't it?

---

