---
title: "GPG error"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by ProPilot on 2005-10-19
I get the following after a synatic reload and after executing 'sudo apt-get update'

""GPG error: [http://archive.unbuntu.com](http://archive.unbuntu.com) breezy updates Release: The following signatures were invalid: BADSIG 40976EA437DO5B5 Ubuntu Archive Automatic Signing Key <ftpmaster@unbuntu.com>
W: You may want to run apt-get update to correct these problems.""

Is this a problem on my machine or a problem with the repositories?

Thanks

---

### Post by skoal on 2005-10-19
man, that's good stuff.  People were saying before they got this occasional warning when running from the .us mirrors, me included. It doesn't for me anymore, but now you say it does on a mirror people were saying to switch to.

I guess do as others have suggested: change to another mirror in your sources.list.  Prefix a .us before your mirrors and see if that fixes it.

* I don't know what the source of these GPG errors randomly occuring across different mirrors are, but I guess it's just package maintainers dropping all sorts of updates constantly within the last few days without signing them first, and it takes awhile for other mirrors to sync with 'em.  It seems like every day for the past 3 days, there's been upgrade options ready for me too.  I don't remember this GPG error keeping me from using the repos though.  You should still be able to pull in the package and get a warning first about the GPG uncertainty...

\\//_

---

### Post by kaktusztea on 2005-10-20
[QUOTE=ProPilot]""GPG error: [http://archive.**[SIZE="3"]unbuntu[/SIZE]**.com](http://archive.**[SIZE="3"]unbuntu[/SIZE]**.com) breezy updates Release: The following signatures were invalid: BADSIG 40976EA437DO5B5 Ubuntu Archive Automatic Signing Key <ftpmaster@unbuntu.com>
W: You may want to run apt-get update to correct these problems.""
[/QUOTE]

You typed "unbuntu" istead of "ubuntu".

---

### Post by ProPilot on 2005-10-20
You are right - just a typo (two) on my part - it did say Ubuntu.

Must have been repositories because I did not change my sources.list and today all works ok - no errors.

Tom

---

