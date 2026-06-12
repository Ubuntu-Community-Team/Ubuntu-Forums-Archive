---
title: "How do you file a bug specifically for Karmic Koala (9.10)?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zefew on 2009-10-16
I tried to file a bug that happens specifically for karmic, but
clicking on "Report a bug" link of [https://bugs.launchpad.net/ubuntu/karmic/+bugs](https://bugs.launchpad.net/ubuntu/karmic/+bugs)
only redirects me to a wiki page.

The problem is that the page only explains the way to file a bug for
packages in general, but not under certain ubuntu distribution.
I want my bug to appear on [https://bugs.launchpad.net/ubuntu/karmic/+bugs](https://bugs.launchpad.net/ubuntu/karmic/+bugs)
How do I do it? Why is it so hard to do so?

---

### Post by Rocket2DMn on 2009-10-16
You just file a bug normally and say that it is for Karmic (there is a link about filing bug reports in my profile if you need help).  If the bug needs to be specifically targeted for a release, it can be nominated for it, though it usually isn't necessary for development release bugs.  This late in the game, most problems won't get fixed unless they meet exception requirements since the repositories are (more or less) frozen.

---

### Post by zefew on 2009-10-16
> **Rocket2DMn said:**
> You just file a bug normally and say that it is for Karmic (there is a link about filing bug reports in my profile if you need help).  If the bug needs to be specifically targeted for a release, it can be nominated for it, though it usually isn't necessary for development release bugs.  This late in the game, most problems won't get fixed unless they meet exception requirements since the repositories are (more or less) frozen.

Thanks for your comment.
I do know how to file a bug "normally" (through "Report a problem" feature), 
but how do you "say that it is for Karmic"?

---

### Post by zefew on 2009-10-17
Just to simplify my question: 
How do I make my bug appear under [https://bugs.launchpad.net/ubuntu/karmic/+bugs](https://bugs.launchpad.net/ubuntu/karmic/+bugs) list?

---

### Post by 23meg on 2009-10-17
> **zefew said:**
> Thanks for your comment.
I do know how to file a bug "normally" (through "Report a problem" feature), 
but how do you "say that it is for Karmic"?

You don't have to. Simply file your bug report with ubuntu-bug and it will provide the required information.

> **zefew said:**
> Just to simplify my question: 
How do I make my bug appear under [https://bugs.launchpad.net/ubuntu/karmic/+bugs](https://bugs.launchpad.net/ubuntu/karmic/+bugs) list?

Technically, there are two ways for a bug to appear under that list: 

[list][*] If the bug is milestoned to be fixed in time for one of the milestones within the Karmic release cycle, it will appear there.

[*] If you nominate a report to be fixed for a specific release with the "Nominate for release" function, and it's approved to be fixed for that release by the release team, it will appear there.[/list]
But if all you're trying to convey is "This is a bug in Karmic and not some other release", you don't have to make it appear there. You do that by using ubuntu-bug, which will automatically attach package version information, thus let developers and bug triagers know which release you're using.

---

### Post by zefew on 2009-10-17
> **23meg said:**
> 
Technically, there are two ways for a bug to appear under that list: 

[list][*] If the bug is milestoned to be fixed in time for one of the milestones within the Karmic release cycle, it will appear there.

[*] If you nominate a report to be fixed for a specific release with the "Nominate for release" function, and it's approved to be fixed for that release by the release team, it will appear there.[/list]


Thanks for your comment. It was informative yet succinct.

Just to be perfectly clear though, would a milestone be added by
anyone in the release team and by no one else? Also, who are on
the list and how one could be able to join the team?

---

### Post by 23meg on 2009-10-17
> **zefew said:**
> Thanks for your comment. It was informative yet succinct.

You're welcome.

> **zefew said:**
> Just to be perfectly clear though, would a milestone be added by anyone in the release team and by no one else? 

Milestones can technically be added by anyone who is part of the Ubuntu Bug Control team, but in practice, we don't milesone bugs without consulting to release team members, or unless a developer whom we trust to have acknowledgement from the release team says "Please assign it to me and milestone it to [some milestone]".

> **zefew said:**
> Also, who are on the list and how one could be able to join the team?

This is the release team:

[https://launchpad.net/~ubuntu-release](https://launchpad.net/~ubuntu-release)

This is the Bug Control team:

[https://launchpad.net/~ubuntu-bugcontrol](https://launchpad.net/~ubuntu-bugcontrol)

Joining the release team would take a great amount of commitment and technical ability. You'd have to be part of [the core development team]("https://launchpad.net/~ubuntu-core-dev") (which by itself is a large undertaking), and demonstrate an interest and ability in managing releases. 

As for joining Ubuntu Bug Control, details are listed here:

[https://wiki.ubuntu.com/UbuntuBugControl](https://wiki.ubuntu.com/UbuntuBugControl)

---

### Post by zefew on 2009-10-17
> **23meg said:**
> Milestones can technically be added by anyone who is part of the Ubuntu Bug Control team, but in practice, we don't milesone bugs without consulting to release team members, or unless a developer whom we trust to have acknowledgement from the release team says "Please assign it to me and milestone it to [some milestone]".

Great. I'm perfectly clear now. Thank you again.

The amount of Ubuntu bugs seems to grow so fast that I was
anxious that bugs I report would go completely unnoticed if they
were not reported under a specific release.

I'm not sure how Ubuntu release teams control incoming bugs or
demarcate bugs for certain releases. It just seems to be a lot of
work without some kind of a release tagging or classification.

---

### Post by 23meg on 2009-10-17
[QUOTE=zefew]The amount of Ubuntu bugs seems to grow so fast that I was
anxious that bugs I report would go completely unnoticed if they
were not reported under a specific release.[/QUOTE]

That's the rationale behind the current experiment that leads people to use ubuntu-bug instead of reporting directly at Launchpad: so many bug reports get filed without basic information such as what release the reporter is using, and asking for that information takes a lot of triager effort.

---

