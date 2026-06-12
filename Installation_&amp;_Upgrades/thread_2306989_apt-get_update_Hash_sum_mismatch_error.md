---
title: "apt-get update Hash sum mismatch error"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by dewdrop_world on 2015-12-21
I've looked around at a number of the threads about the "Hash sum mismatch" error, but so far, nothing is solving my problem.

I'm located in mainland China. At first I was using the Hong Kong mirror. I saw advice to try different mirrors, so I also tried "Server for United States" and "Main server." Same result every time.

Before trying the US and Main servers, I did this:

```
$ sudo apt-get clean
$ sudo rm -rf /var/lib/apt/lists/partial/*
$ sudo rm -rf /var/lib/apt/lists/*
$ sudo apt-get clean
$ sudo apt-get update
```

In all cases, the failure is the same:

```
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F8599E482BD84BD9
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG F141B5F0C7122F9B Launchpad PPA for Ubuntu SDK team
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/cassou/emacs/ubuntu/dists/precise/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/dists/precise/main/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

This, appearing in the middle of the "sudo apt-get update" process, also seems relevant:

```
Get:39 http://ppa.launchpad.net precise/main Sources [2,108 B]
58% [39 Sources bzip2 0 B] [37 Sources 1,369 kB/5,019 kB 27%] [Waiting for head
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
```

I'm aware this is a nuisance rather than a major problem. However, the update manager insists on displaying a warning in the notification bar, which is disturbing to see, and I can't get rid of the notification without a successful apt-get update. (If it's not a critical notification, then *why can't I dismiss it*???)

I also see in the other threads that this problem is either very easy to solve with a couple of common tricks, or it's spectacularly difficult. So my hopes are not very high. Still, there must be a way to get it to work, right? I've been using Ubuntu daily for five years and never had an impossible package problem before.

Thanks in advance,
hjh

---

