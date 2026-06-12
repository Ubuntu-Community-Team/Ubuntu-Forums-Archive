---
title: "Help with Installation (CD Verification Failure)"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by ev500cburke on 2007-08-30
OK… I’ve got 4 older (3 – 5 years) Dell PowerEdge Servers (a 4400, two 2400’s, and a 2500).  Xubuntu Command-Line Server Feisty Fawn has been installed on all of them except the 2500, and I was hoping to describe the symptoms publicly in hopes of getting assistance from the community (this is the final step prior to launching the server over Niagara Falls).

Installation on the 2500 has failed in seemingly in random locations, and I’ve tried 4 different CD’s:

[LIST]
[*]Feisty Fawn [Normal Installation CD]
[*]Xubuntu [Alt. Install CD] v. 6.06 Server Install
[*]Xubuntu [Alt. Install CD] v. 7.04 Command-Line System Install
[*]Xubuntu [Alt. Install CD] v. 7.04 Command-Line System Install (Slower Burn Speed)
[/LIST]

But rather than posting the various installation errors, I thought I’d isolate this request to solving the fact that all 4 CD’s fail verification on the 2500.  Each fails in a different location, and all failures are associated with the repeated message “Buffer I/O error on device sr0, logical block <contiguous numbers>”.  The excitement ends with a red screen explaining that the CD failed MD5 verification.

Conversely, ALL 3 CD’s have been successfully verified on one of the other servers, and all 3 have been successfully installed on OTHER servers.

As I said, though, I am just trying to get Ubuntu installed on this fourth and final server, but would have to assume that solving the verification failure would lead to a firm diagnosis and (ultimately) success.  My assumption, of course, is that some device on the 2500 is causing the problem, but I just don’t know how to get to the bottom of it.  So my questions are as follows:

[LIST=1]
[*]**What would cause a failure in the MD5 verification other than a defective CD?**
[*]**What is going on during the verification test that would cause it to consistently succeed on one machine while failing on another?**
[*]**I used InfraRecorder to burn all the CD’s, all with the default options selected.  Has anyone ever come across hardware (e.g. the CD device, etc.) that simply requires different settings when burning the image?  And if so, what other settings are relevant?**
[/LIST]
Any help would be greatly appreciated.  While I am only 30 minutes away from the Falls, the authorities really frown upon tossing computing equipment into the river.


-------------------------------------------------------------------------------------------------------------------

So.... I just wanted to close the loop on this should anyone else run into similar installation problems.

Essentially, I never did figure out what was causing the failure.  The memory tests were successful, which left the CD drive as the only logical point of failure.  Rather than going through the trouble of ordering a new drive, or trying to swap in a different drive from one of the other PowerEdges (as there were no spare connectors available on the motherboard), I proceeded with a PXE installation using another Ubuntu server.  Worked like a charm.  In fact, I like this approach better because it doesn't ask me to insert the "feisty" CD when trying to install a package.

In any case, I followed the instructions here:

[http://wiki.koeln.ccc.de/index.php?title=Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php?title=Ubuntu_PXE_Install)

Chris

---

### Post by Pumalite on 2007-08-30
Try different sofware: ImgBurn: [http://imgburn.com/](http://imgburn.com/) (free). Install. Go to Mode>ISO>Burn

---

### Post by wolfen69 on 2007-08-30
k3b is another burning app.(awesome) also, it could be that your cd drive (on the machine you are trying to install on) is defective in some way.

---

### Post by Wim Sturkenboom on 2007-08-30
My guess: bad CD drive or memory issue.

---

