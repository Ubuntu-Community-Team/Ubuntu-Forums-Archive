---
title: "What to backup before upgrade (Transmission)?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by papibe on 2010-05-13
Hi all,

  I have a downloading server running transmission-daemon (Karmic server). I want to upgrade to Lucid, but I am concerned that I may loose the files are being downloaded right now (30Gb approx). 

Although I have configured the download directory on a safe partition (/home), I don't see there the information about how much is already downloaded (equivalent to utorrent's .dat files). My guess is that info is stored in the .resume files in /var/lib/transmission-daemon/info (again, just a guess).

I've never been a fun of distro-upgrade (now 'do-release-upgrade'), so if I were to do clean install, my question would be:

What do I have to backup before a clean install to avoid (or minimize) the recheck process and torrent away happily?

or,

Do you think 'do-release-upgrade' got better and will also preserve my transmission-daemon info?

Thanks in advance :).

---

### Post by lemming465 on 2010-05-14
I've had pretty good luck with release upgrades, and I would expect transmission state to survive across it.  However, it would be very risky to try to keep it running during the upgrade, so I'd shut it down during the upgrade.

If you have backup space, e.g. on an external USB drive or something, doing backups before upgrading is always safest.

If you have a spare PC or spare partition somewhere, you could try doing a test install of karmic followed by a test upgrade to lucid with just a small torrent involved, and see what kind of results you got.

According to packages.ubuntu.com, the version jump from karmic to lucid is 1.75 -> 1.92.  According to the [release notes]("http://trac.transmissionbt.com/wiki/Changes"), this includes some significant changes around 1.80 in January.  "dpkg-query -L" for packages transmission-common and transmission-gtk doesn't show any directories under /var, so I think you might be OK.

---

### Post by papibe on 2010-05-16
> **lemming465 said:**
> 
"dpkg-query -L" for packages transmission-common and transmission-gtk doesn't show any directories under /var, so I think you might be OK.

Thanks lemming :KS, but as you can see, transmission-daemon uses the /var/lib directory.
```

$ dpkg-query -L transmission-daemon | grep info
/var/lib/transmission-daemon/info
```
I have continued researching, and I believe I came across the right information. According to this help page: [http://trac.transmissionbt.com/wiki/ConfigFiles]("http://trac.transmissionbt.com/wiki/ConfigFiles") the .resume files are what I thought they were:
> resume/

This subfolder holds .resume files that hold information about a particular torrent, such as which parts have been downloaded, the folder the downloaded data was stored in, and so on.

Their format can be found here: [http://trac.transmissionbt.com/wiki/ResumeFile]("http://trac.transmissionbt.com/wiki/ResumeFile"). To be extra sure, I opened one the files using a bencode editor. There is a field called 'progress->bitfield' that seems to map what pieces have been already downloaded.

I feel pretty confident now that besides the actual content, you also need to backup /var/lib/transmission-daemon/info. In this directory are located both the .torrent and the .resume files. Note that these files have been renamed with a particular scheme, so you need them both.

**Nevertheless**, I going to follow lemming advice. I do have an spare old laptop, so I'll test it before upgrading my server.

I will post my results.

---

### Post by papibe on 2010-06-03
It worked: if you backup and restore the info dir, it reduces the checking time enormously (even some of them started downloading inmidiately).

Nevertheless, there are significantly changes between versions. I would advice to consider these warnings:
[LIST=1]
[*]The main config file is no longer /etc/transmission-daemon/settings.json. Even if the man, transmission website and READMEs said so. Look for /var/lib/transmission-daemon/info/settings.json now.
[*]Version 1.92 changes the way it reserves space for a download. Be prepared for transmission to reserve all space required for the torrent (very much like utorrent works).
[/LIST]

Regards.

---

