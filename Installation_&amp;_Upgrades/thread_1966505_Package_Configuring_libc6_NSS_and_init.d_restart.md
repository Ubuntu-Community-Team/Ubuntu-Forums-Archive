---
title: "Package Configuring libc6 NSS and init.d restart"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2012-04-27
1. I'm running XFCE

2. After d/l'ing upgrade to Precise Pangolin (v. 12.04), a terminal window opened with the Title bar: "Package configuration". and below that: Configuring libc6

3. This window issues a scary warning "otherwise they might not be able to do lookup or authentication any more ..." and then says "Services to restart for GNU libc library upgrade:" and then lists rsync cups cron atd and others. While I was trying to copy & paste that list, I did something to the running terminal script and had to CTRL-C. Now the option to lookup or authenticate are stopped or blown up and 

what do I do to stop the upgrade or to fix this problem.

4. I'm leaving the computer powered up in hopes someone can walk me through this.

===

6 hours later, I tried running the Update Manager and was told only a partial upgrade was available. I closed that. The next screen msg. said use: sudo apt-get install -f. Here is the terminal output.

mark@Lexington-19:~$ sudo apt-get install -f
[sudo] password for mark: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can you help me kill the process that is running if that will help in this situation?

==

So I held my breath and re-booted. A-OK. Panel has red circle icon with white bar. Following the rule to run Package Manager, gave the following error:

dpkg: dependency problems prevent configuration of libnih-dbus1:
 libnih-dbus1 depends on libnih1 (= 1.0.3-4ubuntu9); however:
  Version of libnih1 on system is 1.0.3-4ubuntu2.
 libnih-dbus1 depends on libc6 (>= 2.3.4); however:
  Package libc6 is not installed.
dpkg: error processing libnih-dbus1 (--configure):
 dependency problems - leaving unconfigured

Can I restart the Upgrade or should I delete what is there and do a clean upgrade by d/l'ing the entire package(s)?

---

### Post by Mark_in_Hollywood on 2012-04-27
After the aforementioned restart, I ran Synaptic Pkg. Mgr. and saw the 12.04 upgrade available. I ran it. All seems to have gone well as on re-boot I entered an XFCE session. I have the internet and believe whatever happened with the init.d and restarting apt, cups, and the others is OK.

Thanks for reading all the way to here.

---

