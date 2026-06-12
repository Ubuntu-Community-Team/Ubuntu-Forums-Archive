---
title: "Software Updater not showing all the updates"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by boruno on 2019-04-18
Hello.
Sometimes, when I open the Software Updater program, it looks for updates, and then says that is everything up to date, but if I go to the terminal and run a "apt update", it shows some packages.
This has occurred more than once, and I would like to ask if this is a normal thing (if those updates showing in terminal are "special" and don't show at the Software Updater), or if Software Updater is not recognizing all it needs.
thanks in advance
PS.: the Software Updater still shows updates most of the time, for things like my browser, and even for the OS in general. i'm just intrigued for those packages that don't appear in it

---

### Post by Dennis N on 2019-04-18
Software Updater and apt (in terminal) are on different schedules as to what updates are made available. There can be a few days difference in availability. Software Updater may take slightly longer to offer some updates, but you will end up (after a few days) with the same updates regardless of what tool you use.

---

### Post by boruno on 2019-04-18
thanks for the info!

---

### Post by TheFu on 2019-04-18
Running **sudo apt update** is one of the processes which updates the list of packages and which version is available.  There is also an daily update which runs once a day based on when anacron thinks daily tasks should run on your machine.  Most of my systems run this at 6:25am, but 3 run it at 7:35am instead.  I don't know why.

I don't want patches daily due to the disruption that can cause to normal work-day efforts, so I've disabled the daily "package update" task.

I've never used "Software Updater", but rest assured that all the different GUIs/TUIs into APT use the same back-end database and that when updates happen, regardless of which updater does it, these are shared. It would be crazy NOT to do that from a design standpoint.

If you want more details, you can check out the manpages for each of the different tools.  apt, apt-get, aptitude, synaptic, each have a nice manpage which explains the options and what each does.  I don't use GUI tools very often, they don't work on servers, so my knowledge of any GUI tool will be limited. Sorry.

---

### Post by deadflowr on 2019-04-18
Software Updater has phased-updates support:
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

(Software Updater = update manager, fwiw)

---

### Post by TheFu on 2019-04-19
Very good info.  From the blog link:
> Who is participating?

Users of Ubuntu 13.04 who install updates with update-manager are automatically participating in this process. For every package, in -updates, update-manager will generate a random number and if that number is less than the Phased-Update-Percentage the package will be installed. One can opt out of the Phased Update process by adding &#8216;Update-Manager::Never-Include-Phased-Updates &#8220;True&#8221;;&#8217; to the configuration file &#8220;/etc/apt/apt.conf&#8221;.
 
The update-manager config files are in /etc/cron.daily, some in /etc/apt/apt/apt.conf.d/ and some in /var/lib/update-notifier/ . The list of files in the package are here:
 /var/lib/dpkg/info/update-notifier-common.list  Wish that blog post was included in a README for the package.

---

### Post by boruno on 2019-04-19
this is so cool, and answers all my questions! thanks!

---

