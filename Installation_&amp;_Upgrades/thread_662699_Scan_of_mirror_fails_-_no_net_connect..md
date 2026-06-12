---
title: "Scan of mirror fails - no net connect."
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by RainKing on 2008-01-09
Two issues here, really.

1. The install should allow for static IP setup. That would solve the second issue.

2. How can I disable the mirror scan during gutsy install? It doesn't get the net settings right,
 so there's no connection and the install just hangs. I found the following [post](http://ubuntuforums.org/showpost.php?p=3559320&postcount=1), which had
 an unacceptable answer about slow mirrors on release day. Well, my friends,
 this isn't release day anymore. ;-)

I can fix the net settings after install, if it finishes, but that's not the point.
 Please don't tell me I have to accept dumbed-down installation defaults because
that sounds too much like Redmond.

Thanks.

---

### Post by taurus on 2008-01-09
If it cannot connect to the net to check for security updates, it will move on to the next step after a certain amount time.  So, just wait for a few minutes and it should continue with the rest of the installing process.

---

### Post by RainKing on 2008-01-10
Thanks for the reply. As you said, after awhile, it continued with the install. However, it should be possible to prevent it from trying to access the net during the install. I would like this addressed. What is the proper way to proceed? File a bug or a wishlist item? Thanks, again.

---

### Post by Partyboi2 on 2008-01-10
Here is a related bug
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095)
Or you might find something closer by doing a search.
Or if you believe it is a bug that has not been reported you can file out a bug report
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

