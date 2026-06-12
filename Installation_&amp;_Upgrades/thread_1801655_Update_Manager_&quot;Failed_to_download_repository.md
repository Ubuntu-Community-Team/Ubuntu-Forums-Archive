---
title: "Update Manager &quot;Failed to download repository information&quot;."
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by jamynn on 2011-07-10
I keep getting a red triangle at the top right corner of my screen that says I need to update my software, but when I run update manager, I get an error window with the title of this post saying the following in its details:

"W:Failed to fetch [http://ppa.launchpad.net/plippo/t10lmt/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/plippo/t10lmt/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/plippo/t10lmt/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/plippo/t10lmt/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

I tried following the instructions in this post [http://ubuntuforums.org/showthread.php?t=1787167](http://ubuntuforums.org/showthread.php?t=1787167), but even though I successfully switch servers, I still get the same update manager failure.

---

### Post by wojox on 2011-07-10
That's because your using a ppa. The location has changed. Look at [http://ppa.launchpad.net/plippo/t101mt/ubuntu/dists/natty/main/binary-i386/](http://ppa.launchpad.net/plippo/t101mt/ubuntu/dists/natty/main/binary-i386/)

---

### Post by jamynn on 2011-07-10
Hey Wojox-

thanks for the help.  Whats a ppa?  And what am I looking for in that folder?

Thanks.

---

### Post by wojox on 2011-07-10
> **jamynn said:**
> Hey Wojox-

thanks for the help.  Whats a ppa?  And what am I looking for in that folder?

Thanks.

Open Update Manager > Settings > Other Software and delete any reference to 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197198&stc=1&d=1310354350[/IMG]

```
plippo/t101mt
```

Then add to:

```
ppa:plippo/t101mt 
```

Close and let it update.

---

### Post by jamynn on 2011-07-11
So doing that didnt help, but it turned out that instead of t10[COLOR="red"]**1**[/COLOR]mt, my path had t10[COLOR="Red"]****l[/COLOR]mt - no idea how the 1 got mixed with an l since i never edited it manually ... but it did.

So just changing the l to an 1 fixed the first two errors, but now I still get this error when reloading the package manager:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C3745BE8983882DF

---

### Post by jamynn on 2011-07-11
OK, so I used the link below as an example to deal with the missing key error.

[http://www.rebelzero.com/fixes/apt-get-gpg-error-public-key-not-available/88](http://www.rebelzero.com/fixes/apt-get-gpg-error-public-key-not-available/88)

---

