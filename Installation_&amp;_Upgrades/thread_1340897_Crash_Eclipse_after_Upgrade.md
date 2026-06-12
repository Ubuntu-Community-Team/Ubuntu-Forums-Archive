---
title: "Crash Eclipse after Upgrade"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2009-11-29
I have been using Eclipse for a while and it was working well until I upgraded to Karmic Koala. I have uninstalled clean eclipse, sun-java; cleaned out configuration files and reinstalled them without success.

Help

If I have posted this in the wrong forum or not provided enough info that would be helpful to know too.

In the latest round, there have been several, I uninstalled clean the following: **eclipse-jdt, eclipse-platform, eclipse-platform-data, eclipse-plugin-cvs and eclipse-rcp**.

Though I noticed that when I went to reinstall it, it did not download eclipse it just installed. Is there a way to tell the Koala to clear it's cache of eclipse and download a fresh copy? I may be grasping but I'm assuming that corruption is a possibility. Also in the log file I saw references to equinox even though I was upgraded to Galileo when I upgraded to Karmic Koala. Well at least the splash screen for eclipse says Galileo and the reinstalled version is listed as 3.5.1+repack~1-0ubuntu3 in synaptic.

After install I deleted my old ~/workspace directory and used a new ~/dev/workspace directory. Then I ran eclipse and created a new "Test" project and went to import a MyTest.java I saved from a preveous iteration. After choosing to import the file I received the following on the terminal window I ran eclipse from:

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x007c4856, pid=17656, tid=3078538944
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Client VM (14.1-b02 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libpango-1.0.so.0+0x23856]  pango_layout_new+0x36
#
# An error report file with more information is saved as:
# /home/sadwrn/hs_err_pid17656.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted

```

Please see attached hs_err_pid17656.log.

I would appreciate a clue as I'm dead in the water until I solve this.

---

### Post by TennTux on 2009-12-04
I have tried to work through this issue as time permits, but, have not made any progress.

I was able to not only remove the installed package and clean the config files but remove the install packages from the cache. Something that was not happening before. This did not help.

I currently have sun-java6-jdk and sun-java6-jre installed but not gnu java. Does anybody know if eclipse requires gnu jre for the environment to run, eventhough it's not listed as a dependancy? I'm not sure why I'm crashing in native code while running eclipse.

I'm reasonably sure it's not my code as I'm able to start with a new workspace and crash it before I even get to create my first source file. I should note that it is crashing in native code so I believe it's either eclipse's or something it depends on.

---

### Post by TennTux on 2009-12-06
Was helped with the solution my **the_king_men** in a programming/talk forum. The solution was that Assistive Technologies needed to be disabled (System -> Preferences -> Assistive Technologies). Once I did this I no longer crashed.

---

