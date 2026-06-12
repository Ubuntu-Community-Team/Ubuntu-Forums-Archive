---
title: "Is Karmic really supposed to be this buggy?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jon.reeve on 2009-10-27
This is the short list of the problems I've been having, that I didn't have with jaunty:

• the brightness on my laptop is completely screwed. It flickers, spontaneously switches to minimum brightness (while I'm working, not while I'm idle), and any attempt to manually set the brightness causes it to enter an infinite loop of brightness freak-out. 
* I can't plug in an external display without it freezing, requiring me to hard-reboot the machine
• when I play anything with audio, the speakers (even when I have headphones plugged in) will give a loud pop
• epiphany doesn't display more than 20% of favicons
• gnome-do starts off using 180% (yes, 180%) of the CPU half the time, and I have to manually kill it
• using GIMP will crash Compiz after awhile
* while writing this post, karmic has decided to adjust my brightness level to 20% four times. I'm in a brightness war with karmic. 

I mean, are all these problems going to be fixed in time for release?

---

### Post by 23meg on 2009-10-27
[QUOTE=jon.reeve]I mean, are all these problems going to be fixed in time for release?[/QUOTE]

Since we're in final freeze, don't expect fixes for any bugs other than [these]("https://launchpad.net/ubuntu/+milestone/ubuntu-9.10") and maybe some of [these]("https://bugs.launchpad.net/ubuntu/karmic/+bugs"), and possible bugs found during ISO testing, past this point.

---

### Post by psyke83 on 2009-10-27
First of all, nothing will be solved by posting about your problems on this - or any - forum. If you haven't checked for bug reports against your issues (and filed new reports if they don't exist), you have no right to complain about bugs not getting fixed.

> **jon.reeve said:**
> 
&#8226; when I play anything with audio, the speakers (even when I have headphones plugged in) will give a loud pop

This is because all HDA chipsets now have power-saving enabled, and certain codecs need to be tweaked slightly to remove the popping sound each time the codec is powered down. In order to do this, the specifications for each individual chipset/codec needs to be checked.

Daniel Chen [requested help]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html") from the community back in May. You should file a bug according to those guidelines if you ever expect the popping to stop on your machine. Since we're in freeze for release, this isn't going to be fixed in time, but there is a slight chance of getting the fix in a SRU, or Lucid at worst.

---

### Post by uschxc on 2009-10-27
are we at a point to where _only_ the LTR releases should be used by the general user?  was that the original intention all along?  

i personally only have a two or three problems that i've noticed, none of which are show stoppers.  i think everyone likes to stay up to date with whats out there, but i really feel for those with bugs equivalent to the original poster as i think it makes linux very frustrating.

i would like to see the release cycle have some flexibility to allow more tweaking if needed before release so that the integrity of the distro is maintained.

---

### Post by mesmith on 2009-10-27
You know, if you don't describe the problem you don't get a description of the work, e.g. codec tweaks, etc. which you kindly provided.  You can still describe a problem even after submitting a bug report to see if there has been an independent fix.

When I loaded xubuntu 8.10 I discovered the abiword help system was broken.  I submitted a bug report, it was accepted, and a fix promised for 9.04.  This is after contacting abiword and being told it was a distro error, not theirs.  So, I fired up the live cd for 9.10, launched abiword, hit insert, then page number, then help and bang.  Still broken a year later.

I too believe that some flexibility should be shown for these launches.  Another few weeks might do wonders for the acceptance of ubuntu in the general community.

---

### Post by exploder on 2009-10-27
Looking at the bug lists 23meg provided, the largest part of the serious issues have been resolved or are in the process of being fixed. I really appreciate the fact that the Developer's fixed the Intel issues and I see a lot of other things working that were not in the last release. For me, if all of the major things are fixed anything else can come in the form of updates.

---

