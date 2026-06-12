---
title: "Can't upgrade Business Desktop Remix to Ubuntu 12.10"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by llemar97 on 2012-10-24
I encountered the following error message when attempting an upgrade from Ubuntu 12.04 BDR to Ubuntu 12.10:

[HTML]
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop-business' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.
[/HTML]

Upon running the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal, the following "Invalid Problem Report" error appears:

[HTML]
Package ubuntu-release-upgrader-core does not exist
[/HTML]

So I am lost.  How do I effectively upgrade Ubuntu BDR from 12.04 to 12.10?

---

### Post by grahammechanical on 2012-10-24
How did you try to upgrade to 12.10? what did you do?

Notice this:

> while removing social networking software, file sharing apps, games and development/sysadmin tools.

[http://www.ubuntu.com/business/desktop/remix]("http://www.ubuntu.com/business/desktop/remix")

My guess is that it is not possible to upgrade Ubuntu Business Desktop Remix 12.04 to standard Ubuntu desktop 12.10 because, first of all, some system administration tools are missing, such as ubuntu-release-upgrader-core.

After all an employer would not want to give his employees so much power to change the operating system.

Secondly, there may not be a 12.10 Business Desktop Remix available to upgrade to. With a system such as that you may only the able to upgrade from one LTS release to another.

Again, this would be a sensible business requirement and could only take place with the necessary authentication. As far as I can understand the intention of this business remix is to strictly limit what a user can do to and with the OS.

Regards.

---

