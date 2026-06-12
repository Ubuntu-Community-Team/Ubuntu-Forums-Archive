---
title: "Help configuring Apache + Svn"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by lucacerone on 2010-11-09
Dear all,
I've Apache2 installed on my computer (I host a Drupal site
for me and my colleagues), and I would like to configure it 
to work properly with Subversion.
I followed the guide in here [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion) 
But whenever I try to make a commit I receive this error:
> Server sent unexpected return value (403 Forbidden) in response to PROPFIND
There are a few strange things (or at least to me)
Submitting files locally using the svn cli file:///repository works,
but I had to change the permissions of the repository folder
so that everyone can write in it. This is strange because I'm in the group subversion that owns the directories.

I'm not an expert so I have no idea where to start to check what is wrong.
I'd like to configure Apache2,SVN so that:
I use SSL (possibly ONLY SSL) for svn,
Assign checking out and committing permission to each repository,
so that only the authorized people can access it.

Any idea how I can do?
Thanks a lot in advance,
Cheers, -Luca

---

