---
title: "Mono 2.0 released 3 days ago on October 6th!"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by irrdev on 2008-10-10
Although it seems to have gone unnoticed, Mono 2.0 was released 3 days ago on October 6th. You can [read the announcement here]("http://www.mono-project.com/news/archive/2008/Oct-06.html"). Mono 2.0 includes some major new features over Mono 1.9. From the [Mono 2.0 release notes]("http://www.mono-project.com/Release_Notes_Mono_2.0"), here are a few things which jumped out at me:

***** Many speed improvements - runtime compilations are 30% faster
***** Complete C# 3.0 support
***** LINQ support complete
***** System.Diagnostics partially implemented
***** Better 64 bit support
***** Monodoc programs have been streamlined into mdoc
***** ASP.NET now supports virtual paths

Ubuntu Hardy has Mono 1.2.6 in the repos, while **Itrepid currently only has Mono 1.9.1**. I find this extremely disappointing, as both beta releases of openSUSE and Fedora are already packaged with Mono 2.0. The actual installation differences between Mono 1.9 and 2.0 are extremely small, it is really just a matter of uploading the updated packages to the repositories. I really would like to see this pushed through in time for the final release date.

---

### Post by directhex on 2008-10-10
> **irrdev said:**
> The actual installation differences between Mono 1.9 and 2.0 are extremely small

No, they're not.

---

### Post by RAOF on 2008-10-10
You can look at it this way if you want: if the differences are small, we probably don't need them.  If the differences are big, we don't want them :).

---

### Post by fd0man on 2008-10-10
Perhaps the biggest change of import is the ability to use MonoDevelop's SVN version, which has support for integrated debugging.

In any event, I suspect that there will be some sort of unofficial backports of the packages springing up relatively soon.  I'd tried to use prevu to do this, actually, prevu in intrepid appears to be broken, giving all sorts of errors before it even gets to the point of starting the Mono 2.0 build.  Will try it using pbuilder and a different setup that I have instead, and see what happens... I suspect that'll go quite a lot easier.

---

### Post by irrdev on 2008-10-10
> **RAOF said:**
> You can look at it this way if you want: if the differences are small, we probably don't need them.  If the differences are big, we don't want them :).
While this may hold true with many libraries and projects, Mono is slightly different. Each release builds upon the previous version to better implement the .NET api. As a result, each release for the most part simply extends the previous version's api, and it doesn't break backward compatibility in any way. Any changes to previous code are simply made for performance/handling increases - the actual api in no way changes. Therefore, "big differences" are really just further additions to Mono to better implement the .NET api in a proficient manner. How can we not want them? :)

---

### Post by directhex on 2008-10-10
> **irrdev said:**
> While this may hold true with many libraries and projects, Mono is slightly different. Each release builds upon the previous version to better implement the .NET api. As a result, each release for the most part simply extends the previous version's api, and it doesn't break backward compatibility in any way. Any changes to previous code are simply made for performance/handling increases - the actual api in no way changes. Therefore, "big differences" are really just further additions to Mono to better implement the .NET api in a proficient manner. How can we not want them? :)

Because the risk of regressions is incredibly high, especial... Know what? I've answered this too many times.

Just pretend you're the one who posted [https://bugs.launchpad.net/ubuntu/+source/mono/+bug/278946](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/278946) or [https://answers.launchpad.net/ubuntu/+source/mono/+question/44628](https://answers.launchpad.net/ubuntu/+source/mono/+question/44628)

No core-dev would back putting Mono 2.0 into Intrepid this late in the release process, especially considering they would need to do all the repackaging and QA (which is significant work, believe it or not) themselves, rather than letting the pkg-mono team take care of it.

There are also several exciting developments happening in the realm of Mono packaging, including a drastic (20-40%) reduction in disk space required for apps like Tomboy. If you want to stay informed, then keep an eye on [http://wiki.debian.org/Teams/DebianMonoGroup/Mono20](http://wiki.debian.org/Teams/DebianMonoGroup/Mono20) and [http://wiki.debian.org/Teams/DebianMonoGroup/Mono20Transition](http://wiki.debian.org/Teams/DebianMonoGroup/Mono20Transition) - and on my PPA for packages, once they're ready for human consumption.

---

### Post by ajackson on 2008-10-10
As much as I would like Mono 2.0 in intrepid I have to agree with directhex, the potential for regressions is too high to risk, even for official backporting.

Someone will eventually release an unofficial backport, failing that there is always the source to compile yourself.

But by the time Ibex+1 is due out most of the major bugs should have been fixed.

---

### Post by gnomeuser on 2008-10-10
> **ajackson said:**
> As much as I would like Mono 2.0 in intrepid I have to agree with directhex, the potential for regressions is too high to risk, even for official backporting.


It could be considered relatively low. Unlike most projects Mono has their own dedicated QA team working full-time paid to do nothing but this process. You also will notice that 2.0 was branched a while ago and all the effort of testing for a long time has been on regressions from previous releases. Additionally Mono implements a standard, they run a wide set of tests to ensure compliance. Novell have many customers who rely on Mono being regression free, customers who do much testing of the codebase against large and complex existing programs, none of this testing seems to hav prompted problems that made Novell delay the release.

All that taken into consideration, it would be a fairly low risk freeze break.

I would be greatly saddened if upstreams efforts on QA were completely disregarded as they have been extensive and well organized. Mono 2.0 truly is, provably so, a much improved product and it would be a great candidate for a freeze exception.

---

### Post by gnomeuser on 2008-10-10
> **irrdev said:**
> 
Ubuntu Hardy has Mono 1.2.6 in the repos, while **Itrepid currently only has Mono 1.9.1**. I find this extremely disappointing, as both beta releases of openSUSE and Fedora are already packaged with Mono 2.0. The actual installation differences between Mono 1.9 and 2.0 are extremely small, it is really just a matter of uploading the updated packages to the repositories. I really would like to see this pushed through in time for the final release date.

Slightly related tidbit: The Fedora Mono SIG' confidence in Mono 2.0 is so great that it was just announced that the entire 2.0 stack will be pushed back to Fedora 9 making 2.0 available to everyone and being the only stack supported by Fedora post release of Fedora 10 (which will likely also be around the time said packages will start trickling into F9 testing).

---

### Post by directhex on 2008-10-10
> **gnomeuser said:**
> It could be considered relatively low. Unlike most projects Mono has their own dedicated QA team working full-time paid to do nothing but this process. You also will notice that 2.0 was branched a while ago and all the effort of testing for a long time has been on regressions from previous releases. Additionally Mono implements a standard, they run a wide set of tests to ensure compliance. Novell have many customers who rely on Mono being regression free, customers who do much testing of the codebase against large and complex existing programs, none of this testing seems to hav prompted problems that made Novell delay the release.

All that taken into consideration, it would be a fairly low risk freeze break.

I would be greatly saddened if upstreams efforts on QA were completely disregarded as they have been extensive and well organized. Mono 2.0 truly is, provably so, a much improved product and it would be a great candidate for a freeze exception.

```
2008-09/#mono.15.log:15-09-2008 22:33:28 < ajorg!~ajorg@137.65.133.4: debian WAS our QA team
```

I'm not going to disparage recent efforts by upstream, who have now provided us not only with a mailing list to discuss packaging issues but a hard line to QA when filing issues with bugzilla.

But Mono is still a package in need of careful tender care (I'm adding 3 new patches into the Lenny/Intrepid package as we speak). Compare today's date to [https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule) and consider that there would only be one week (!) for testing, between ReleaseCandidate and FinalFreeze. Assuming someone were to make 2.0 packages - which nobody within Ubuntu is going to want to do, and nobody within pkg-mono is sufficiently happy with yet.

Track the two Debian Wiki links above if you want to monitor progress on 2.0, but it won't make an official stable release until Jaunty.

---

### Post by fd0man on 2008-10-13
I've created a script that will install a parallel Mono (Mono 2.0) in ${HOME}/opt.  It also installs MonoDevelop 2.0 Alpha 1 current from SVN.  See [the post on my blog]("http://www.trausch.us/2008/10/13/want-to-play-with-mono-20-so-do-i/") which talks about it and provides many, many more details.

Just to make sure it's well-known and understood, I'll repeat part of what I said there, here:  A few words about the script: ***This script is released under the terms of the GNU General Public License, Version 3. It is version 3 ONLY. There is NO SUPPORT for this software; I wrote it for myself, and it may change or it may stagnate. I provide it in the hope that it is useful to someone out there other than myself, but it is AS-IS, WITHOUT WARRANTY, UNSUPPORTED software. If it changes your dog’s gender, bursts your house into flames, destroys your whatchamacallermicroflobbermajag, do not come and yell at me.*** That having been said, I welcome any modifications (at least to view them). You can modify it for your own use, you can share it (in fact I expect you to!) and you can tinker with and tweak it. Suggestions? Welcome! Comments? Welcome! Flames? Hey, free speech is your right…

---

