---
title: "GNOME 2.30 New Module Decisions"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-11-11
At the same time as [announcing]("http://mail.gnome.org/archives/devel-announce-list/2009-November/msg00001.html") that GNOME 3 will be released in September 2010, the GNOME Release Team also [announced]("http://mail.gnome.org/archives/devel-announce-list/2009-November/msg00002.html")  the new modules to be included in the next release, GNOME 2.30. There are some notable new modules, such as gnome-packagekit, Tracker and Vala, the last two being external dependencies. Vincent Untz has [a blog post]("http://www.vuntz.net/journal/post/2009/11/10/3.0%2C-2.30%2C-2.28%2C-11.2..")  giving his own take on the rationale behing the new modules.

---

### Post by gnomeuser on 2009-11-11
Tracker I would like to see this do something useful before including it as a standard component of the desktop. So far there has been a chicken and egg problem in the indexer area but I think now they are in a position to fix that. On the other hand to get people to use it developers need to be able to count on it being there. Maybe this is a case of adopting the technology now and hoping it will turn out well. I really want this stuff on the desktop I think it can make it better in ways we have a hard time doing otherwise. Another problem they need to address is that is that traditionally indexers have uncovered a lot of bugs that cause 100% cpu load and other nastiness, what is their plan to avoid this and gather data and fix this types of issues (this I think is PulseAudios major failing, they did not work hard enough to communicate the exact nature of any problem and people naturally assume that PA is to blame when in 99% of cases it is not).

I am excited to see PackageKit bring improvements to the desktop as an official component, one of the first places I would love to see this would be in fileroller to search for uncompressing support for unsupported files thus eliminating an ugly and unneeded error message. PackageKit already tells a compelling story and has proven to be solid technology. There are other areas that would benefit as well but this one is my obvious first case - added benefit providing more leverage to ending Ubuntu's aptdeamon adventure and join upstream.

Vala is interesting but before the language spec is at a stable 1.0 with assurance that the syntax is stable I would be concerned about adding it as a blessed language. I would like to see a major user pull this in rather than blessing before it's useful. Like the way Tomboy showed the maturity and completeness of the Mono+GNOME stack and thus proved useful to the community.

dconf looks to be a solid upgrade to gconf that increases performance and brings about something that is actually maintained. One lingering question seems to be migration of existing data, if it is done then who is responsible dconf itself or the application upon first launch. I do not believe anyone should seriously consider just dumping a whole bunch of user settings so migration is the obvious choice. No good story is told here yet and a plan really does need to form.

Outside of that I am happy to see globalmenu being proposed. It is hugely popular but the current implementation seems to lack a properly defined standard in the fdo realm. The configuration tool needs polish and there is no good GNOME 3 story to tell. It's one of these things I would love to include but it probably needs to happen as part of a desktop rethinking such as the gnome-shell.

Finally Clutter, I love that this supposedly great technology is now being kept out because of copyright assignment policies. This highlights how universally disliked this tactic is and why companies that enforce them on contributors need to evaluate their stance carefully if they want to gain adoption (Like a certain company that makes a popular Linux desktop distribution named.. Ubuntu). Added benefit till this situation is resolved the world is safe from gnome-shell.

---

### Post by Sashin on 2009-11-11
Global menu isn't that great it just moves the file, system etc to the menu at the top. If anything it means I'll have to move my mouse more...

---

### Post by Joe_Bishop on 2009-11-11
> **gnomeuser said:**
> Outside of that I am happy to see globalmenu being proposed. It is hugely popular but the current implementation seems to lack a properly defined standard in the fdo realm. The configuration tool needs polish and there is no good GNOME 3 story to tell. It's one of these things I would love to include but it probably needs to happen as part of a desktop rethinking such as the gnome-shell.

Disagree. There are several usecases when a global menu is a pain. It also is a pain all the time on large monitors. It doesn't become any great if the apple co uses it.

---

### Post by zekopeko on 2009-11-11
> **Sashin said:**
> Global menu isn't that great it just moves the file, system etc to the menu at the top. If anything it means I'll have to move my mouse more...

[http://www.asktog.com/basics/firstPrinciples.html#fittsLaw](http://www.asktog.com/basics/firstPrinciples.html#fittsLaw)

---

### Post by Merk42 on 2009-11-11
The whole copyright thing is hilarious.
Isn't that why GNOME started in the first place? Because they were scared of the copyright to Qt?

---

### Post by gnomeuser on 2009-11-11
> **Merk42 said:**
> The whole copyright thing is hilarious.
Isn't that why GNOME started in the first place? Because they were scared of the copyright to Qt?

No, because QT at that time was under a proprietary license. Then it became GPL which was also problematic (for ISVs and platform building). Only recently has QT become licensed under the more suitable LGPL license.

---

### Post by Merk42 on 2009-11-11
> **gnomeuser said:**
> No, because QT at that time was under a proprietary license. Then it became GPL which was also problematic (for ISVs and platform building). Only recently has QT become licensed under the more suitable LGPL license.

Oh well licensing either way.
I mean they didn't want to use Qt due to Nokia and now don't want to use Clutter due to Intel

---

### Post by 23meg on 2009-11-11
> **Merk42 said:**
> The whole copyright thing is hilarious.
Isn't that why GNOME started in the first place? Because they were scared of the copyright to Qt?

No. It had to do with QT being under a restrictive license at that time.

---

### Post by directhex on 2009-11-11
> **Merk42 said:**
> Oh well licensing either way.
I mean they didn't want to use Qt due to Nokia and now don't want to use Clutter due to Intel

They didn't want to use Qt because it was closed-source software owned by Trolltech. Then, subsequently, either closed-source or GPL-only (forcing EVERY app to be GPL too, regardless of developer wishes)

Copyright and licensing are related, but very different topics

---

### Post by shafin on 2009-11-11
Nokia bought QT just recently, it had nothing to do with gnome's adoption of gtk.

---

### Post by Merk42 on 2009-11-11
Oh trolltech, couldn't think of who it was.

> **directhex said:**
> Copyright and licensing are related, but very different topics

So I'm half right? :p

Still the point of touting a feature like clutter (and subsequently mutter) without checking if they actually can use it is odd.

---

### Post by 23meg on 2009-11-11
> **Merk42 said:**
> 
Still the point of touting a feature like clutter (and subsequently mutter) without checking if they actually can use it is odd.

It *would have been* odd, had it actually been the case. Clutter is already an external dependency.

```
 + clutter-core (desktop)
   - already adopted by the GNOME community
   - already an external dependency
   - not hosted on GNOME infrastructure, but tarballs and API docs are
     now there (missing: git and bugzilla)
   - copyright waiver possibly limits contributions:
     [http://bugzilla.openedhand.com/waiver.html](http://bugzilla.openedhand.com/waiver.html)
   - copyright assignment is also an issue
   => the release team is working with the Foundation to investigate the
      copyright waiver and copyright assignment, and with Intel to find
      an appropriate solution.
   => feedback from the community at large on what solution would be
      appropriate is welcome.
   => at least bugzilla should be moved to the GNOME infrastructure.
   => rejected, until those (non-technical) issues are solved. We still
      support the project as we believe it's really essential for GNOME,
      especially in the GNOME 3 context.

```

---

### Post by Merk42 on 2009-11-11
I thought GNOME Shell's window manager was Mutter which is a combo of Metacity and Clutter?

---

### Post by 23meg on 2009-11-11
> **Merk42 said:**
> I thought GNOME Shell's window manager was Mutter which is a combo of Metacity and Clutter?

And?

*(Trivia: Rather, GNOME Shell is a plugin to Mutter, probably to be separated soon.)*

---

### Post by Merk42 on 2009-11-11
and... doesn't the Intel thing mean they're reluctant to use something that's a core functionality of GNOME Shell?

Whatever, all that is more GNOME Shell and less 2.30.

So back on topic I hope whatever can get included in 2.30 shows up for Lucid as it's supposed to be "The pinnacle of GNOME 2.0"

---

### Post by gnomeuser on 2009-11-11
> **Merk42 said:**
> Oh trolltech, couldn't think of who it was.


Then research prior to posting

> 
So I'm half right? :p


no, wholly wrong also apparently willfully uninformed and proud of it it seems

> 
Still the point of touting a feature like clutter (and subsequently mutter) without checking if they actually can use it is odd.

It's not that they can't use it but all copyrights need to be wholly assigned to Intel which is not desirable. It means that Intel may take code that you wrote and relicense it pretty much any way they desire (now they may "promise" to keep the licensing OSI compliant but that is hardly the point). Aside that you also grant Intel ownership over all the technology you create. 

We are free to use Clutter but it is definitely not a good idea for us to do so before this has been cleared out somehow. Till then Clutter is contributor hostile and not a good dependency for us to endorse. The same problem exists with any "community" project Canonical undertakes, you have to assign copyright to them.

Evolution used to have this requirement as well, after they removed this, Evolution became a much more vibrant community project. I think the same will happen with Clutter.

---

