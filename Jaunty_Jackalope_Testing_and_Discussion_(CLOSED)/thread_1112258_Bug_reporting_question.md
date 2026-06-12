---
title: "Bug reporting question"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jackocleebrown on 2009-03-31
Hi,

I am seeing a bug in Evolution which appears to be recently known upstream ([http://bugzilla.gnome.org/show_bug.cgi?id=574522](http://bugzilla.gnome.org/show_bug.cgi?id=574522)).
Should I still add a bug report on launchpad and include this link or will the bug fix automatically filter through to jaunty?

Thanks for your help, Jack.

---

### Post by ghindo on 2009-03-31
I'm curious about this as well.  It definitely won't hurt, but I'm not sure of protocol here.

---

### Post by jackocleebrown on 2009-03-31
I've reported it here [https://bugs.launchpad.net/bugs/352660](https://bugs.launchpad.net/bugs/352660), we'll see what happens.

Are there any guidelines for Launchpad Ubuntu bug reporting? I have not seen anything and to be honest I find it quite confusing to know report things under source or distribution packaging.

---

### Post by ghindo on 2009-03-31
I asked around on some IRC channels and got an answer on #ubuntu-bugs:> <ghindo> Hi, if I know of a bug which has already been reported upstream, should I still report it through Launchpad?
<bdmurray> ghindo: It depends on its importance / severity
<bdmurray> Is it something that needs to be fixed in Jaunty?
<ghindo> bdmurray: I'm not sure
 bdmurray: I'm mostly asking on behalf of this thread:  [http://ubuntuforums.org/showthread.php?t=1112258](http://ubuntuforums.org/showthread.php?t=1112258)
<bdmurray> ghindo: Yes, that would be good to open in Launchpad since its a crash and something we'd like to fix in Jaunty
<ghindo> bdmurray: Cool, thank you.
<bdmurray> Some low priority ones it might make more sense just to open upstream, and the fixes will be pulled in during development of the next release.Sounds like you did the right thing by reporting it through Launchpad.

---

### Post by midtown on 2009-03-31
> **jackocleebrown said:**
> I've reported it here [https://bugs.launchpad.net/bugs/352660](https://bugs.launchpad.net/bugs/352660), we'll see what happens.

Are there any guidelines for Launchpad Ubuntu bug reporting? I have not seen anything and to be honest I find it quite confusing to know report things under source or distribution packaging.

Well, if you just google "bug reporting ubuntu" you will get many relevant things! The first of which is [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) . Following that you could have reported the bug directly from Evolution and then Launchpad would have your Ubuntu version, Evolution version, and other relevant information useful to triagers and developers.

If you happen to know of an upstream bug (which is really helpful, especially if you file one if one doesn't exist) such as you did in this case then you can link it by clicking "Also affects project" as was done for that report.

Is that resource what you were looking for?

---

### Post by jackocleebrown on 2009-04-02
Thanks for the link, I'll take a look at that. I should use Apport more, it does lots of the hard work for you.

Thanks, Jack.

---

