---
title: "Upgrade - from 14.04 to 15.04?"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by sgtrobo on 2016-09-09
I have 2 questions:

1. Is it possible to upgrade from 14.04 to 15.04? (actually, I know it's possible, since it happened on a few of my servers)
2. Is there a way to see a do-release-upgrade list similar to the apt list to show last command entered to get to 15.04?

I know 15.04 is end of life
I know 16.04.1 is latest LTS

I know I am asking a strange few questions, but is it even possible?  Somehow a few of my servers went from 14.04 to 15.04 and I want to know how the heck it happened.  I am trying to reproduce this in a test environment, but I can't even get 14.04 to upgrade to 15.04.

I set Prompt=normal in /etc/update-manager/release-upgrades

If I do
# apt update && apt upgrade -y

I go to 14.04.5

If I do
# do-release-upgrade

I go to 15.10

I have a few 15.04 systems and I'd love to know how this could've happened.

I know apt has a place like /var/log/apt/history.log where you can see the last official command entered.  Does do-release-upgrade have this?  The /var/log/dist-upgrade/history.log doesn't seem to show the last command.

Any help greatly appreciated. Thanks.

---

### Post by TheFu on 2016-09-10
I suppose of the repos were manually modified for APT, then it could happen. Without manual intervention (or a devops screw up), I don't see it happening.  Is this a desktop install that you are calling a "server" or a real "ubuntu server" install?

OTOH, I'm an LTS-only guy and never deal with non-LTS releases.  Actually, I don't deal with the .0 LTS either.  Loaded my first 16.04.1 server yesterday for a few hours of testing.  Love the new option to have a minimal server installed (1.3G).

I'm interested in this, since about 25 of my "servers" here are still on 14.04.x today.

---

### Post by sgtrobo on 2016-09-11
hey, thanks a lot for your response!

yes, these are actual 'servers', not just desktop installs.  True, goshdarnit, real servers.  :)

---

### Post by deadflowr on 2016-09-11
> I set Prompt=normal in /etc/update-manager/release-upgrades
This sets you to go to the next release available.

In olden days that would have been the release directly after the LTS you were on.
(In 14.04's case the next release was 14.10)

But as they have shorter release duration for the non-LTS releases now. It currently directs to the next non-LTS version still active.
(In this case the next release after 14.10 was 15.04, so for a little while that was considered the next release after 14.04. Then it went to sleep and 15.10 became the next release)

So depending on when the release upgrade happened, that may help determine what release version it might get.


That make any sense?

---

### Post by TheFu on 2016-09-11
Well, the only guess I have is that the systems hadn't been maintained with all the patches - specifically, the do-release-upgrade version was probably out of date.  I do understand that the upgrade process after 14.04 did change so that going from 14.04 to any later release was supposed to work - don't think "supported" is the correct term for odd transitions.

In the old days, upgrades could be from 
a) LTS to LTS (12.04 --> 14.04 --> 16.04) 
or
b) to the very next release (12.04 --> 12.10 --> 13.04 -->13.10 --> 14.04 --> 14.10 --> 15.04 --> 15.10 .... ) without skipping.

But I don't think that is the requirement anymore.  I suspect the installed version of do-release-upgrade is what determines which release gets installed when that is run, but don't quote me. It is likely I'm completely wrong.

---

### Post by sgtrobo on 2016-09-16
figured out what it was.  One of my guys had added a repo to sources.list that points to Vivid.  It was the last entry, despite everything else pointing to Xenial

go figure.

---

### Post by TheFu on 2016-09-16
> **sgtrobo said:**
> figured out what it was.  One of my guys had added a repo to sources.list that points to Vivid.  It was the last entry, despite everything else pointing to Xenial

go figure.

Could happen to anyone trying to multi-task in a dynamic environment. Manual APT sources changed as suspected. Please mark thread as [solved].

---

