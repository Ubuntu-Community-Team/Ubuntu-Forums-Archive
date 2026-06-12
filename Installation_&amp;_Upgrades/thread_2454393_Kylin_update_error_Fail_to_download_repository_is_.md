---
title: "Kylin update error: Fail to download repository is not the It's FOSS &quot;usual suspect&quot;"
date: 2020-11-28
forum: Installation &amp; Upgrades
---

### Post by davepool on 2020-11-28
According to It's FOSS, getting the notification that an update "failed to download repository information" is a very common error.  However, once entering "sudo apt update" in terminal (per their suggestion), the last few lines that I see are not the ones they report.  Instead, what I get is:

E: Repository '[http://archive.ubuntukylin.com/ukui](http://archive.ubuntukylin.com/ukui) focal InRelease' changed its 'Origin' value from 'LP-PPA-ubuntukylin-members-ukui3.0' to 'LP-PPA-ubuntukylin-members-ukui'
E: Repository '[http://archive.ubuntukylin.com/ukui](http://archive.ubuntukylin.com/ukui) focal InRelease' changed its 'Label' value from 'UKUI 3.0' to 'UKUI'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.

If that last instruction is meant to be a terminal command, the result I get is:

bash: syntax error near unexpected token "8"

Even if I add sudo to that command I get:

bash: syntax error near unexpected token "("

When I try to copy those URLs, they convert to something else. When I click on Open Link, I get taken to a directory where I have no idea what's what.

The good news here (I guess) is that so far whenever I have simply pressed OK in response to the repository fail, Kylin still downloads a walking ton of updates and manages to process them without additional drama. So I'm not sure of what, exactly, I'm missing with the new labels on those particular repositories.  

What should I be doing?

---

### Post by Bashing-om on 2020-11-28
davepool; Well --

The advisory:
> 
See apt-secure(8) manpage for details.

Translates to terminal as"
```

man 8 apt-secure

```

Wherein you direct the search for apt-secure docs in section 8 of the manual.

As to how ubuntukylin expects the sources.list to be formatted - no idea as I do not use that distro. However, as the package manager is "apt" we can take a poke at it and see if:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
the displayed syntax makes sense for your current release.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by davepool on 2020-11-28
Thanks, @Bashing-om, for your reply and your explanation. I've checked out the information that all 3 of those produce and....

Jeebus, that's crazy! About the only thing I can begin to grasp are what *appear* to be all the warnings about the software being ENTIRELY UNSUPPORTED by the Ubuntu team and also how it won't receive a security review, etc.  I don't know if that's just standard boilerplate CYA stuff that always appears but, net-net, I still have no clue what to do to respond to the Fail to Download Repository notification. 

At this point, it appears that since (as I reported in the IP) it actually DOES upgrade with lots of stuff and everything works and nothing seems wrong....OR....for as little as I've put into this installation in terms of adding packages, I could just re-install with the newest .iso (on the assumption that Labels and Origins are all corrected in same).

Thoughts, anyone?

---

