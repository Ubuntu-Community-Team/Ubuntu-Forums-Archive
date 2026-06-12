---
title: "Installing 12.04 LTS on Athlon XP 2200+"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by espoo on 2012-08-19
Every time at the end of installation after I enter new user data i get message "Installation failed: This installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again." I'm almost sure it's a processor issue. It's i386 but AMD. So I just tried and other X64 version but then I get an error "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU."
More informations about an error: "Crash report: Sorry, the application plugininstall.py has closed unexpectedly. If you notice further problems, try restarting the computer."
Uname: Linux 3.2.0-17-generic-pae i686
Casper version: 1.305
Apport version: 1.94-0ubuntu1
Architecture: i386
Package: ubiquity 2.9.24
ProblemType: Crash
Title: plugininstall.py crashed with IOError in command (): [Errno 32] Broken pipe

What is the best solution to this problem?
Thank you in advance. I love Ubuntu.

---

### Post by efflandt on 2012-08-19
I believe the Athlon XP is a 32-bit cpu, because I have an early Athlon64 3200+ (2 GHz) from 2004 which I think was one of the first AMD 64-bit cpus (Sempron cpus at that time were similar, but were crippled with 64-bit disabled).

For some reason I had trouble installing 64-bit 12.04 to a Intel Core 2 Duo laptop (w/Intel integrated graphics) from 2006, which really is 64-bit cpu (hung more than 2 hours at 90% of "Installing System" with no errors).  But the alternate text based installer worked.

So you might try the "alternate" 32-bit installer
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by espoo on 2012-08-22
A great post, in the meantime I downloaded alternate i386 version and it worked like a charm. Then I read your answer. Thanks for that, it was helpful. My processor is 32-bitand it's 1.8 GHz. Have a nice day!

---

