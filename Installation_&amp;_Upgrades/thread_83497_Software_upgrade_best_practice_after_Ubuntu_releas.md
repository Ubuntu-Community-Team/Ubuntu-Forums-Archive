---
title: "Software upgrade best practice after Ubuntu release"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by mloskot on 2005-10-28
Hi,

AFAIK and if I understand it correctly, after Ubuntu release is published then it is frozen so no software upgrades are expected.
In example, Ubuntu 5.10 includes FOX Toolkit 1.2 currently 1.4 is available, so according to the policy users should not expect to have FOX upgraded to 1.4 in Ubuntu 5.10. Am I right?

So, let's assume I am :-)
Then could you explain me your best practice of upgrading software on, let's say, frozen release of Ubuntu?

I use 5.10 but I would like to install i.e. FOX Toolkit 1.4, so please tell me
is it recommended to do upgrade?
Here I give an example of FOX Toolking, but my question is more general.
Certainly, there are very complex dependencies, so if I upgrade i.s. FOX to 1.4 then some of packages expecting 1.2 may stop to work or something like that. Simply, there are many traps :-)

Another subject is that I can build build my own package for my Ubuntu with software of newer version.

I'm really curious your best practice.

Regards

---

### Post by aysiu on 2005-10-28
Your assumption's incorrect. Packages get updated more frequently than releases do. For example, Firefox will probably update to 1.5 when 1.5 is officially released in December (or a week later), whereas the next Ubuntu release will be in April of 2006.

---

### Post by mloskot on 2005-10-28
[QUOTE=aysiu]Your assumption's incorrect. Packages get updated more frequently than releases do. For example, Firefox will probably update to 1.5 when 1.5 is officially released in December (or a week later), whereas the next Ubuntu release will be in April of 2006.[/QUOTE]

Hm, I think I've not expressed my question clearly.
I know that packages are updated frequently, in general.
But my quoestion is about packages in released Ubuntu.
In example, will Firefox be updated to 1.5 in Ubuntu 5.10 Breezy or in the Dapper Drake repositories?

Cheers

---

### Post by aysiu on 2005-10-28
[QUOTE=mloskot]Hm, I think I've not expressed my question clearly.
I know that packages are updated frequently, in general.
But my quoestion is about packages in released Ubuntu.
In example, will Firefox be updated to 1.5 in Ubuntu 5.10 Breezy or in the Dapper Drake repositories?

Cheers[/QUOTE] Breezy... or whenever 1.5 is released. Let me give you a little calendar (if Mozilla stays on target for its release date):

October 2005 - Breezy released
December 2005 - Firefox 1.5 released
December 2005 - Firefox 1.5 available in Breezy repositories
April 2006 - Dapper released, probably with the latest Firefox version

Does that help?

---

### Post by mloskot on 2005-10-28
[QUOTE=aysiu]Does that help?[/QUOTE]

Definitely, yes, but to be sure for 100%, please let me ask one more question.

This is my post form about 4 days ago
[[REQUEST] FOX Toolkit 1.4 packages]("http://ubuntuforums.org/showthread.php?t=81639")

and as you can read there, I was told that new FOX Toolking 1.4 can not be included to Breezy. So, by analogy, this is the same example as yours with Firefox, isn't it? That's why I misunerstood that policy.
So, is this possible to update FOX Toolkit to for Breezy?

Thanks for your patience

---

### Post by aysiu on 2005-10-28
I don't know if what that person told you was true, but as I understand it, it means that there will be no *new* packages included in Breezy after release, not that the packages already included won't be updated. As far as I can tell, there is no fox-toolkit in the repositories at all. There is, however, Firefox in the repositories.

All I'm saying is the stuff that's already in there (say, Firefox or gcc or Blender or Wine) will continue to be updated to newer versions. 

I don't know if other programs that are *not* currently in there will show up in there later.

---

### Post by AgenT on 2005-10-28
For new programs, you can request a backport (and use the backport repositories). Notice that your package would have to be first available in the next release of Ubuntu (now Dapper). If it is not in the next release, you can request it to be included, especially if it is available in Debian. Notice, this means requesting it into Dapper, not Breezy. Then after it makes in into the next release of Ubuntu (Dapper), you can request a backport into Breezy.

---

### Post by mloskot on 2005-10-29
[QUOTE=aysiu]I don't know if what that person told you was true, but as I understand it, it means that there will be no *new* packages included in Breezy after release, not that the packages already included won't be updated. As far as I can tell, there is no fox-toolkit in the repositories at all. There is, however, Firefox in the repositories.[/QUOTE]

Hm, are you saying no FOX Toolkit in Ubuntu repositories?
What is this?
[http://packages.ubuntu.com/breezy/libs/libfox1.2c2](http://packages.ubuntu.com/breezy/libs/libfox1.2c2)

About my understanding of what I was told.
Please, note how I confirmed it in the thread [[REQUEST] FOX Toolkit 1.4 packages]("http://ubuntuforums.org/showthread.php?t=81639"):

mloskot confirmed:
[I]Thank you for clarification.
I understand it, so newer FOX Toolkit may be included in nex RC and stable release, right?[/I]

and RAOF replayed:
*Yup, certainly. Expecially if you ask for them in the appropriate forum, the Dapper Drake developers forum*

I think that's clear I understand the Ubuntu repos update policy in the way that new version of FOX can not be included.

Cheers

---

### Post by aysiu on 2005-10-29
I don't know about Fox Toolkit, but I do know that programs get updated more than every six months--I've seen it happen. I started using Ubuntu only a few weeks after 5.04 was released, and a lot of software has been updated between then and 5.10. Take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=83535](http://www.ubuntuforums.org/showthread.php?t=83535)

People seem pretty confident that OpenOffice will be updated. Stuff just doesn't get updated to the newest version the very same week the newest version comes out (this will change when Breezy backports become available). When Firefox 1.0.7 came out this forum was flooded with threads about "When will 1.0.7 be in the repositories? When can we upgrade?" It took a little over a week, but it happened. We did **not** have to wait until October 13 to upgrade to 1.0.7 in Hoary.

---

### Post by mloskot on 2005-10-29
[QUOTE=aysiu]I don't know about Fox Toolkit, but I do know that programs get updated more than every six months--I've seen it happen.[/QUOTE]

All what you are saying is very clear for me.
I think that I was told wrong information in the second thread about FOX Toolkit. I believed you will confir that I was misinformed :-)

So, to summarize the discussion.
Can I expect (in some future) that FOX Toolkit - which version 1.2 is present in the Breezy - will be updated?

Thanks

---

