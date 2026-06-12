---
title: "Inconsistent system after do-release-upgrade 16.04-&gt;18.04 (LTS)"
date: 2018-06-22
forum: Installation &amp; Upgrades
---

### Post by pivert2 on 2018-06-22
Hi,

On 1st of June, I initiated an upgrade from LTS 16.04 to LTS 18.04.
The system broke, since it uninstalled LVM2 that was necessary to run my KVM.
I fixed it by re-installing lvm2. However now, my system is inconsistent:
- I have packages of the 16.04
- But the /etc/issue and lsb_release tells I have a 18.04 LTS (bionic).
- the do-release-upgrade tells me that I'm on the latest release ("No new release found.")

I need help to:
- Understand what went wrong, so the problem does not occur for other users.
- Effectively upgrade the system to a 18.04. (Since it's blocked in a 18.04 with 16.04 packages installed).

More details:
Since it's an LTS release, the 18.04 upgrade was not available, as it waits for the 18.04.1 for proposing it. 
As I'm comfortable with Linux administration, I decided to proceed to the upgrade knowing the risks, but I had to explicitly ask for it. (I think by using the "do-release-upgrade -d" option.)

I can provide all the logs (dpkg.log or apt/history.log or apt/terrm.log). But did nto find any relevant information there.

Thanks for your help.

---

### Post by cruzer001 on 2018-06-22
Hello

Please post the output of
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

Also run
```
sudo apt -f install
```
Any errors?

---

### Post by pivert2 on 2018-06-23
Hi,

Sure, here it is (Just removed useless lines with grep):

```

root@homer:~# cat /etc/apt/sources.list | grep '^[^$#]' && ls /etc/apt/sources.list.d/*.list
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates universe
deb http://archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
/etc/apt/sources.list.d/google-chrome.list                  /etc/apt/sources.list.d/team-xbmc-ubuntu-kodi-old-xenial.list
/etc/apt/sources.list.d/landscape-ubuntu-16_06-xenial.list  /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/runner_gitlab-runner.list

```
```

root@homer:~# apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@homer:~# 

```

---

### Post by cruzer001 on 2018-06-24
Hello

I have seen this once before here in the forums.  In that case the poster manually updated the sources list from xenial 16.04 to bionic 18.04.  This did not work and just created more problems.  A reinstall of 18.04 was the final solution in that case.

Have you tried purging and reinstalling update-manager-core?

---

### Post by pivert2 on 2018-06-25
Ok,

So I'm probably not alone. 
I can't affort to take risks with this server, and reinstalling will take several hours because of the many services and complex network setup.

I did purge & re-install the "update-manager-core (1:16.04.13)".
Surprisingly, the update-manager and some other packages were in 18.04:

```

root@homer:~# apt install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies.
[COLOR=#ff0000] update-manager-core : Depends: python3-update-manager (= 1:16.04.13) but 1:18.04.11 is to be installed[/COLOR]
E: Unable to correct problems, you have held broken packages.
root@homer:~# apt install python3-update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]python3-update-manager is already the newest version (1:18.04.11).[/COLOR]
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@homer:~# apt remove python3-update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  plasma-discover-common
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED
  muon-discover plasma-discover python3-distupgrade python3-update-manager
  ubuntu-release-upgrader-core ubuntu-release-upgrader-qt
0 to upgrade, 0 to newly install, 6 to remove and 0 not to upgrade.
After this operation, 1,648 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 252047 files and directories currently installed.)
Removing muon-discover (4:5.6.2-1ubuntu1.1) ...
Removing plasma-discover (5.6.2-1ubuntu1.1) ...
[COLOR=#ff0000]Removing ubuntu-release-upgrader-qt (1:18.04.18) ...
Removing ubuntu-release-upgrader-core (1:18.04.18) ...
Removing python3-update-manager (1:18.04.11) ...
Removing python3-distupgrade (1:18.04.18) ...[/COLOR]
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for man-db (2.7.5-1) ...
root@homer:~# 
root@homer:~# 
root@homer:~# apt install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  plasma-discover-common
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  python3-distupgrade python3-update-manager ubuntu-release-upgrader-core
The following NEW packages will be installed
  python3-distupgrade python3-update-manager ubuntu-release-upgrader-core
  update-manager-core
0 to upgrade, 4 to newly install, 0 to remove and 0 not to upgrade.
Need to get 172 kB of archives.
After this operation, 1,368 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
[COLOR=#ff0000]Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-update-manager all 1:16.04.13 [32.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-distupgrade all 1:16.04.25 [104 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-release-upgrader-core all 1:16.04.25 [29.6 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-manager-core all 1:16.04.13 [5,496 B][/COLOR]
Fetched 172 kB in 0s (1,190 kB/s)              
Selecting previously unselected package python3-update-manager.
(Reading database ... 251930 files and directories currently installed.)
Preparing to unpack .../python3-update-manager_1%3a16.04.13_all.deb ...
Unpacking python3-update-manager (1:16.04.13) ...
Selecting previously unselected package python3-distupgrade.
Preparing to unpack .../python3-distupgrade_1%3a16.04.25_all.deb ...
Unpacking python3-distupgrade (1:16.04.25) ...
Selecting previously unselected package ubuntu-release-upgrader-core.
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a16.04.25_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:16.04.25) ...
Selecting previously unselected package update-manager-core.
Preparing to unpack .../update-manager-core_1%3a16.04.13_all.deb ...
Unpacking update-manager-core (1:16.04.13) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up python3-update-manager (1:16.04.13) ...
Setting up python3-distupgrade (1:16.04.25) ...
Setting up ubuntu-release-upgrader-core (1:16.04.25) ...
Installing new version of config file /etc/update-manager/meta-release ...
Setting up update-manager-core (1:16.04.13) ...

```

But it did not help:
```

root@homer:~# do-release-upgrade 
Checking for a new Ubuntu release
No new release found.

```

How can I say to update-manager that I'm in 16.04 instead ? Updating the /etc/issue & lsb_release ?

---

### Post by number-one on 2018-07-31
Actually, the 'do-release-upgrade' command won't show an update for 16.04 LTS until 18.04.1 comes out (as noted in the [release notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes")).  While version 18.04.1 was released several days ago, as of today (7/31/18) they still haven't done whatever is necessary to tag that release to show up in the do-release-upgrade command.

I guess the general idea for LTS server systems is to provide some time to work out any kinks in the latest OS release (and upgrade process) between the date of the main release and the point upgrade before offering the automatic do-release-upgrade method.  Hopefully they'll be activating the release any day now.  For your type of system (one with important services, etc) it would probably be better to wait until the .1 update of any new release, and that might have saved you trouble this time around.

---

### Post by jjv on 2019-01-12
I ran into the same issue.

As you discovered all the "normal" remedies did not work.

After removing the update manager I replaced the sources.list file with one from a recently upgraded system that upgraded from and to the same version.

Once I did this I was able to do an update, upgrade, autoremove, dist-upgrade and then reinstall the update manager.

All was right with the world and the system behaved as expected.

---

