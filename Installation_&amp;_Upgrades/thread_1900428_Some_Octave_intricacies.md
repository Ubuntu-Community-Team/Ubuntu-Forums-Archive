---
title: "Some Octave intricacies"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by areeda on 2011-12-26
I'm about to start a new job where MatLab is big and I want to get a head start using Octave until they pay for the $1k+ MatLab license.  It took some work to get my environment up and running so I thought I'd post my installation notes here for the next guy.

I tried using the Software Center to install octave and qtoctave then use the Install Packages from the Config menu.  This resulted in a few gotchas.

The big one is that the Install Packages GUI doesn't report errors so you can't tell if the package installs at all (they don't).  The octave command 'pkg list' is helpful.

The issues I've found so far:

[LIST]
[*]/usr/share/octave and /usr/lib/octave are owned by root:root and rwxr-xr-x so you have a couple of options:
[LIST]
[*]I chose to put them in my group and make them group writeable with 
sudo chown -R root:joe /usr/share/octave /usr/lib/octave
sudo chmod -R g+w /usr/share/octave /usr/lib/octave
[*]I think you could sudo qtoctave for the package installs, but haven't tried it.
[/LIST]
 
[*]The java package is a bit weird in that it seems to want JAVA_HOME pointing to the jdk and the jvm.so in a client directory.  Plus it seems to only work with the sun java package and not open jdk. I haven't bothered to see if it works with Java 7. So if you want this package try:
[LIST]
[*]unset JAVA_HOME JDK_HOME
[*]make sure /usr/lib/jvm/default-java is linked to jkd1.6.0_xx
[*]cd /usr/lib/jvm/default-java/jre/lib/amd64; ln -s server client
[/LIST]
 
[/LIST]
If the package installer GUI doesn't result in adding that package (verified with pkg list) then from the command prompt try: "pkg install -verbose <path-to-tar.gz-file>"  that will produce an error message that at least points you in the right direction if not tell you what's wrong.

This seems to work well.  So far I've been able to run all the .m files in my first project except the GUIDE related ones.

The boss seems to have little interest in moving the MatLab development to octave but it seems like a good alternative if you can't afford the expensive license and don't need the MatLab GUI builder.  Using a Java Swing GUI may be an alternative, we'll see.

Joe

---

