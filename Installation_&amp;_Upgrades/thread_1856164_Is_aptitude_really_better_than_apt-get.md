---
title: "Is aptitude really better than apt-get?"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by sonnet on 2011-10-07
I read over the net many times, that aptitude is better than apt-get for installing software. The reason is that apparently it resolves dependencies in a more clever way and so it's more unlikely to have problem  and break software in the future by using aptitude.

So for that reason I use aptitude rather than apt-get.
But on every guide over about program's installations, writers always use apt-get.


Now , I never minded before as I never noticed any difference in using one of the 2.
But now, using Oneiric 64 bit I found some odd (I guess  due to my ignorance) difference among the 2.

Basically installing 32bit proprietary software I found 2 odd problems with aptitude that apt-get seems to not give to me.

First one is with skype. Skype is already in 'partner repository', and indeed synaptic confirms that.
But if I run *'sudo aptitude install skype'* I get this message:
*Couldn't find package "skype".*

If I run the same command with apt-get, I get no problem.


Other issue is with acroread, wine or any other 32bit program.
Basically with aptitude I get warning messages about unresolved dependencies:
[I] Leave the following dependencies unresolved:                                                    
89)     ia32-libs recommends ia32-libs-multiarch                                                      
90)     libqt4-sql recommends libqt4-sql-mysql | libqt4-sql-odbc | libqt4-sql-psql | libqt4-sql-sqlite[/I]


Again apt-get, doesn't show any warning about those supposed conflicts.



What's you experience with apt-get and aptitude?

---

### Post by haqking on 2011-10-07
no difference really they both use dpkg underneath

see this similar thread [http://ubuntuforums.org/showthread.php?t=1854074](http://ubuntuforums.org/showthread.php?t=1854074)

---

