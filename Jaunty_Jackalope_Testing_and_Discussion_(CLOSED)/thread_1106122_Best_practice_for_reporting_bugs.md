---
title: "Best practice for reporting bugs"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-03-25
This is a great e-mail posted to the ubuntu-devel mailing list about best practices for reporting bugs in Ubuntu by Matt Zimmerman (CTO of Canonical, Head of Ubuntu Tech Board). 

Please consider the suggestions given in this e-mail before making bug reports in Jaunty Beta.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027868.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027868.html)

[QUOTE=MDZ]I've noticed that, even among Ubuntu devleopers, not everyone is applying our best practices for reporting bugs.  In particular, reporting bugs directly to Launchpad is usually *NOT* the best approach. This should only be done if there is no better option.

In almost all cases, it is preferable to report the bug using Apport. This can be done in one of the following ways:

1. If the bug is a crash, apport should automatically generate a report and guide you in filing it.  Copies of the crash reports are stored in /var/crash in case you need to refer to them directly.

2. The "Help" menu in many applications includes an entry "Report a problem..." which will invoke Apport manually.

3. On the command line, you can run "ubuntu-bug <package>" (or "ubuntu-bug <PID>") to invoke Apport manually.  Kernel bugs should be reported with "ubuntu-bug linux".

Using this method will automatically attach the relevant version information, log files, etc. where available.  This saves you time in filing the bug, and saves others time in analyzing it.  For example, filing a bug on the kernel will automatically include dmesg, lspci and so on.

We're about to get flooded with bug reports from the beta, so please start using this method immediately, and encourage everyone else who reports bugs to do the same.

More instructions for filing bugs can be found in the community documentation at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Note that if someone files a bug without using apport, you can still take
advantage of it to add the information later (assuming it's still relevant), by using apport-collect(1).  See [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000535.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000535.html) for details.

If you'd like to enhance your packages to take better advantage of apport by attaching relevant data, please ask for help.  It's very simple once you know how to do it.  The basics can be found at [https://wiki.ubuntu.com/Apport/DeveloperHowTo](https://wiki.ubuntu.com/Apport/DeveloperHowTo)

 - mdz
[/QUOTE]

Some graphical examples of this can be found on Jonathan Carter's blog.
[http://jonathancarter.co.za/2009/03/25/the-correct-way-to-file-bugs-in-ubuntu/](http://jonathancarter.co.za/2009/03/25/the-correct-way-to-file-bugs-in-ubuntu/)

Rocket2DMn also has a great beginners guide for bug reporting:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by taavikko on 2009-03-25
I must argue Matt's idea,
> reporting bugs directly to Launchpad is usually *NOT* the best approach. This should only be done if there is no better option.


While searching every apps right place to report bugs, LP offers great change to report them and/or triagers to send it upstream, if needed.

I only wish that LP could be adopted by more and more communities to used as "bugzilla"


Just my 2&#8364; ...

But, thanks for forwarding this from devel-mailing list :)

---

### Post by Technoviking on 2009-03-25
I'm locking the thread to keep this a informational thread and not a debate on bug reporting practices. Please feel free to create a separate thread for discussion of this topic.

T-V

---

### Post by Technoviking on 2009-03-25
> **Technoviking said:**
> This is a great e-mail posted to the ubuntu-devel mailing list about best practices for reporting bugs in Ubuntu by Matt Zimmerman (CTO of Canonical, Head of Ubuntu Tech Board). 

Please consider the suggestion given in this e-mail before making bug reports in Jaunty Beta.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027868.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027868.html)



Some graphical examples of this can be found on Jonathan Carter's blog:
[http://jonathancarter.co.za/2009/03/25/the-correct-way-to-file-bugs-in-ubuntu/](http://jonathancarter.co.za/2009/03/25/the-correct-way-to-file-bugs-in-ubuntu/)

Rocket2DMn also has a great beginners guide for bug reporting:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

