---
title: "[n00b] Installing.. (specifically perforce)"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by TheHitcher on 2011-06-11
Hi all

I'm an absolute new guy to this after giving it another go, and so far the whole OS is perfect and really come on in leaps and bounds since last I tried!!! Just installed 11.04 (natty), kernel LINUX 2.6.38-8 generic

My problem is with installing anything not in the usual repositories; I can download perforce, but aside from extracting them I've just tried running the executables a few different ways and I'm not getting any results. I could probably list everything I've tried but that'll probably be a waste of time since it was just trial-and-error of everything.

so my questions are:
-When I extract the executables, where should I put them? does it matter or will they just install to the right place and leave me to delete what I've extracted? I want to install p4d and p4v from the official perforce site.
-HOW do i run them? I've tried chmod +x p4v then ./p4v but that's just not running or giving junk text

Again, because I've no real idea of what to do formally, I don't just want to list everything I've tried, errors etc. as it'll undoubtedly be wrong anyway. Also I mightn't even be asking the right questions, so if you think there's anything else I should know that'd be great too.

All this is to a view of using this old laptop as a dedicated p4 server (p4d)(Which I already do under it's winxp partition, but when I upgrade all my Os's  I think it'd be a lot more efficient to have my ~£40 laptop running as much open source as I can to keep costs down as I don't like software piracy) so if anyone has any further information specific to that, that'd be awesome.

All-in-all I'm still learning the whole thing (installed < a day but so far everything else I need it for is up and running) but if I can get past this fundamental problem I think it'd benefit my learning in more than just this area..

Thanks everyone!

---

### Post by ccanning on 2011-06-29
Here are the steps to installing the Perforce command line and P4V tools.

[LIST=1]
[*]Goto Perforce Downloads
[*]Download Perforce Command-Line Client (P4) for Linux Kernel 2.6 for 64-bit Intel
[*]Move file to /usr/local/bin as root
[*][INDENT][/INDENT]sudo mv p4 /usr/local/bin
[*]Change owner and group to root
[INDENT]cd /usr/local/bin[/INDENT]
[INDENT]sudo chown root p4[/INDENT]
[INDENT]sudo chgrp root p4[/INDENT]
[*]Make executable
[INDENT]sudo chmod 755 p4[/INDENT]
[*]Download perforce Visual Client (P4V) for Linux Kernel 2.6 64-bit Intel
[*]Untar and unzip the file
[INDENT]tar -zxvf p4v.tgz[/INDENT]
[*]Move directory to /usr/local (replace p4v with your directory name)
[INDENT]sudo mv p4v/ /usr/local[/INDENT]
[*]Change owner and group to root
[INDENT]cd /usr/local[/INDENT]
[INDENT]sudo chown -R root p4v[/INDENT]
[INDENT]sudo chgrp -R root p4v[/INDENT]
[*]Link directory to p4v.latest
[INDENT]sudo ln -s p4v-2010.2.317255 p4v.latest[/INDENT]
[*]Add p4v.latest to your path
[/LIST]

You can just add the original p4v directory to your path if you don't want to link or you can rename the p4v directory. The above allows you to easily install newer versions and to switch between them.

---

