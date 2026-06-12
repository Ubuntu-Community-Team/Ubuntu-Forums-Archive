---
title: "upgrading ubuntu-server-20.04.2-lts --&gt; &quot; &quot; 21.10 impish daily build via an iso"
date: 2021-07-23
forum: Installation &amp; Upgrades
---

### Post by YQ002lc2 on 2021-07-23
Questions:

1. Does "do-release-upgrade -d" get me the daily build or just the latest development release?

2.     [https://superuser.com/questions/73624/how-do-you-upgrade-ubuntu-from-an-iso-image-by-mounting-as-loopback-without-bur](https://superuser.com/questions/73624/how-do-you-upgrade-ubuntu-from-an-iso-image-by-mounting-as-loopback-without-bur) 
indicates I should:

sudo mount -o loop ~/path/to/impish-live-server-amd64.iso /media/username/cdrom/

& gksu "sh /cdrom/cdromupgrade"

Has anyone tried that?

3. Is there another better way to do this?

I'm trying to avoid having to reinstall & setup everything again.

Thanks

---

### Post by ActionParsnip on 2021-07-23
You will need to upgrade to 20.10 first. You can only leapfrog versions when you are upgrading LTS to LTS. The packages will install but you are not following the advised upgrade path.

Once you upgrade to 20.10 you can then upgrade to 21.04.

Alternatively, if you wait until April next year then a new LTS release will be available and you can upgrade directly to it from Focal (Ubuntu 20.04). If you do as you are doing then you will need to upgrade to 21.10 in order to then upgrade to the new LTS released the following year.

---

### Post by YQ002lc2 on 2021-07-23
Thanks for your reply! 

So essentially, I need to go:
A, B, C, D in the "do-release-upgrade"
And can't skip from A to D, right?

Have you ever tried the upgrade using an ISO?

---

### Post by guiverc on 2021-07-23
Question also asked at [https://askubuntu.com/questions/1353550/upgrading-ubuntu-server-20-04-2-focal-lts-21-10-impish-daily-build-using-iso](https://askubuntu.com/questions/1353550/upgrading-ubuntu-server-20-04-2-focal-lts-21-10-impish-daily-build-using-iso)

Following is my response there (*very like* **ActionParsnip's**)

> The use of `do-release-upgrade is bump` you to the next release (*or next LTS if available*); so currently that's *groovy* or 20.10 for you, not 21.04 or *impish* (though any time now *groovy* will disappear due EOL)...   You can only upgrade to *impish* if you're on the *lastest stable* release, ie. currently you need to be on 21.04 which you are not.

Many of us upgrade to the *development* release, however you become off-topic at many support sites (you need to use #ubuntu+1 sites) so yes it works; I'm on *impish* myself - but you get there from the prior release; ie. I was on *hirsute* or 21.04 before I *bumped* to *impish*.   You cannot skip releases; except from one LTS to the next LTS **after** the .1 has been released; ie. you'll be able to go from 20.04 to 22.04 after 22.04.1 has been released; that's the only *fully* & QA-tested release path outside of all releases.


There can be *problems* when using the *development* release, so be prepared to deal with it.  If you call out for help, as already stated, you have fewer support sites open to you, and then only a smaller subset of the Ubuntu user base that actually uses *development* releases.

My system (*impish*) is a desktop; my server(s) are all *stable* releases, and I stick to LTS releases to avoid upgrading rather regularly.  I see little benefit having a server on a *development* release.

Upgrading via ISO - I do it very regularly with *desktops*.

I'm on the Lubuntu team, and it's a QA-testcase for our system, so I test for it rather regularly there, and use it myself for desktop systems. Sorry I only *release-upgrade* servers.

---

### Post by ActionParsnip on 2021-07-23
> **YQ002lc2 said:**
> Thanks for your reply! 

So essentially, I need to go:
A, B, C, D in the "do-release-upgrade"
And can't skip from A to D, right?

Have you ever tried the upgrade using an ISO?

Yes you need the intermediates. If you run:
```

sudo vi /etc/update-manager/release-upgrades

```

and change:
```

Prompt=lts

```

to:
```

Prompt=normal

```

Save and exit vi (feel free to use any text editor you like) then you can run:
```

sudo do-release-upgrade

```

and you will upgrade to 20.10. Once 20.10 boots up, you can rerun the same upgrade command to get to 21.04. You'll probably have a weird system as the old fluff from the old releases will still be around. Personally I prefer to do side-by-side upgrades and switch IPs under change rather than upgrading live servers in place. Alternatively, just wait for April next year and upgrade in one jump from LTS to LTS.

What is in the latest release that you want so badly?

---

### Post by YQ002lc2 on 2021-07-23
Thanks for all the replies! 
I was successful in upgrading to 21.10 using 
sudo do-release-upgrade
and 
sudo do-release-upgrade -d
. 

Thanks again!
This thread can be closed as far as I'm concerned.

---

### Post by deadflowr on 2021-07-24
For what it's worth,
the release channel from 20.04 has been moved up to 21.04.
So no more 20.10 to deal with.
Though this comment is mostly moot for the OP.
[ATTACH=CONFIG]288868[/ATTACH]

---

