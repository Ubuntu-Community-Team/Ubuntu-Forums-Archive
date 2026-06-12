---
title: "Some installed programs missing after LiveCD upgrade"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by Riothamus on 2012-06-12
So I recently had a crash in the middle of an upgrade to 12.04 over the Internet, and it said the installed packages were still downloaded, but it couldn't establish a connection. After trying a few more times and getting the same error, and then restarting, I found that Update Manager no longer displayed a "Upgrade to New Version" button, and I could no longer install new programs using apt-get because it said a connection couldn't be established (although other Internet-using programs still worked).

After posting for help here, I got no responses, so I eventually burned a LiveCD and did a full upgrade that way. Now, everything is working fine, except that I see a number of programs that were installed before now cannot be found anywhere. And I'm positive I did an upgrade, and not another install. Other files I had are still there as normal, it's just that for some reason, many of the programs I had installed are gone.

So my question is, is this a known problem? And is there anything I can do to get back the installed programs, other than installing them again from scratch? If this had happened on Windows, my impulse would be to look into programs to recover accidentally deleted files or run chkdsk to get rid of lost chunks, but because I know Linux's filesystem handles a lot of that stuff automatically, I'm not really sure if there's anything I should run to at least make sure disk space isn't being used up by missing chunks from those lost programs.

---

### Post by wilee-nilee on 2012-06-12
It would be hard to use your experiences here and set up as a marker, it stopped in the middle of a regular upgrade, then you used a disc to finish.

The disc upgrade should leave anything installed from the ubuntu repos in place basically.

Your upgrade fails the double blind test lol.

---

